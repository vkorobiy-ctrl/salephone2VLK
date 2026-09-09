# iPhone Store

Одностраничный магазин: каталог iPhone, выбор цвета и объёма памяти, корзина, оформление
с адресом и анимацией курьера. Без сборки и зависимостей — чистые HTML, CSS и JS.

## Структура

```
index.html          вся страница: разметка, стили, логика
images/             фотографии моделей и фургон курьера (WebP, ~30 КБ каждая)
.nojekyll           отключает обработку Jekyll на GitHub Pages
```

## Как выложить на GitHub Pages

1. Создайте репозиторий на github.com (например `iphone-store`), можно публичный без README.
2. Загрузите содержимое этой папки в **корень** репозитория — `index.html` и папка `images`
   должны лежать рядом, не внутри дополнительной папки.
   - Через сайт: **Add file → Upload files**, перетащите `index.html`, папку `images` и `.nojekyll`,
     затем **Commit changes**.
   - Через терминал:
     ```bash
     git init
     git add .
     git commit -m "iPhone Store"
     git branch -M main
     git remote add origin https://github.com/ВАШ_ЛОГИН/iphone-store.git
     git push -u origin main
     ```
3. В репозитории: **Settings → Pages**. В разделе *Build and deployment* выберите
   Source: **Deploy from a branch**, Branch: **main**, папка **/ (root)**. Нажмите **Save**.
4. Через 1–2 минуты страница откроется по адресу
   `https://ВАШ_ЛОГИН.github.io/iphone-store/`.

## Если картинки не видны

Пути к фото относительные (`images/...`), поэтому папка `images` должна лежать в том же
каталоге, что и `index.html`. Проверьте прямую ссылку `https://.../images/courier.webp`:
если 404 — файлы попали не в корень репозитория.

## Как менять каталог

Все модели описаны массивом `MODELS` внизу `index.html`. Одна модель — один объект:

```js
{ id:'18promax', name:'iPhone 18 Pro Max', series:'18', isNew:true,
  tagline:'6.9-inch display, 5x tetraprism zoom',
  storage:['256GB','512GB','1TB','2TB'],
  colors:[
    { name:'Deep Purple', hex:'#6b3b7a', img:'images/18-pro-max-purple.webp' }
  ] }
```

- `series` — по нему работают фильтры сверху (`18`, `17`, `16`).
- `isNew: true` — рисует бейдж New.
- `colors` — кружки-переключатели под фото; `hex` это цвет кружка, `img` — путь к файлу.
- Оценка одна для всех и задана в константе `RATING` строкой выше массива.

Новые фото лучше готовить так же, как текущие: обрезать пустые поля вокруг телефона
и поместить на прозрачный холст 700×875 (4:5), чтобы масштаб совпадал с остальными карточками.
