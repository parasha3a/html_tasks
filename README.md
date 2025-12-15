# Практическое занятие №10 - Деплой сайта

Проект готов к деплою на различные платформы. Сайт оптимизирован, минифицирован и протестирован.

## Структура проекта

```
html_tasks/
├── index.html          # Главная страница
├── style.css           # Исходные стили
├── style.min.css       # Минифицированные стили (для статического деплоя)
├── script.js           # Исходный JavaScript
├── script.min.js       # Минифицированный JavaScript (для статического деплоя)
├── images/             # Папка с изображениями
├── package.json        # Конфигурация npm и Vite
├── vite.config.js      # Конфигурация Vite
├── dist/               # Собранный проект (создается после npm run build)
└── README.md           # Документация
```

## Быстрый старт с Vite

### Установка зависимостей

```bash
npm install
```

### Запуск локального сервера разработки

```bash
npm run dev
```

Сайт откроется автоматически в браузере на `http://localhost:3000`

### Сборка проекта для продакшена

```bash
npm run build
```

Собранный проект будет в папке `dist/`. Vite автоматически минифицирует CSS и JS.

### Просмотр собранного проекта

```bash
npm run preview
```

## Оптимизация

- ✅ CSS и JS минифицированы (автоматически при сборке через Vite)
- ✅ Изображения используют формат WebP с lazy loading
- ✅ Мета-теги для SEO и социальных сетей
- ✅ Адаптивный дизайн для всех устройств
- ✅ Валидный HTML5

## Деплой на GitHub Pages

### Шаг 1: Создание репозитория

1. Перейдите на [GitHub](https://github.com/new)
2. Создайте новый репозиторий (например, `my-website`)
3. Инициализируйте git в папке проекта:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/ваш-username/my-website.git
git push -u origin main
```

### Шаг 2: Настройка GitHub Pages

1. Откройте репозиторий на GitHub
2. Перейдите в **Settings** → **Pages**
3. В разделе **Source** выберите:
   - Branch: `main`
   - Folder: `/ (root)`
4. Нажмите **Save**
5. Ваш сайт будет доступен по адресу: `https://ваш-username.github.io/my-website/`

### Шаг 3: Обновление сайта

После каждого изменения:

```bash
git add .
git commit -m "Описание изменений"
git push
```

Сайт автоматически обновится через несколько минут.

## Деплой на Netlify

### Вариант 1: Drag & Drop

1. Перейдите на [Netlify](https://www.netlify.com/)
2. Зарегистрируйтесь или войдите
3. Перетащите папку проекта в область **Deploy**
4. Сайт будет автоматически опубликован

### Вариант 2: Через Git

1. Войдите в Netlify
2. Нажмите **New site from Git**
3. Выберите ваш репозиторий GitHub
4. Настройки сборки:
   - Build command: (оставьте пустым)
   - Publish directory: `/` (root)
5. Нажмите **Deploy site**
6. Сайт будет доступен по адресу: `https://project-name.netlify.app`

**Автодеплой**: При каждом push в репозиторий сайт автоматически обновится.

## Деплой на Vercel

1. Перейдите на [Vercel](https://vercel.com/)
2. Зарегистрируйтесь через GitHub
3. Нажмите **Import Project**
4. Выберите ваш репозиторий
5. Настройки:
   - Framework Preset: Other
   - Root Directory: `./`
6. Нажмите **Deploy**
7. Сайт будет доступен по адресу: `https://project-name.vercel.app`

**Автодеплой**: При каждом push в репозиторий сайт автоматически обновится.

## Проверка сайта

### 1. Chrome DevTools

- Откройте сайт в Chrome
- Нажмите `F12` или `Ctrl+Shift+I`
- Проверьте **Console** на наличие ошибок JavaScript
- Используйте **Toggle Device Toolbar** (`Ctrl+Shift+M`) для проверки адаптивности

### 2. Lighthouse

1. Откройте DevTools → вкладка **Lighthouse**
2. Выберите категории: Performance, Accessibility, SEO, Best Practices
3. Нажмите **Generate report**
4. Стремитесь к оценке ≥ 80 по всем категориям
5. Исправьте рекомендации

### 3. W3C Validator

1. Перейдите на [W3C Validator](https://validator.w3.org/)
2. Выберите способ проверки:
   - **Validate by URL** - вставьте ссылку на опубликованный сайт
   - **Validate by File Upload** - загрузите локальный `index.html`
   - **Validate by Direct Input** - вставьте код напрямую
3. Нажмите **Check**
4. Исправьте все **Errors** (красные)
5. Исправьте **Warnings** (желтые) по возможности

### 4. Оптимизация изображений

1. Используйте [TinyPNG](https://tinypng.com/) для сжатия PNG/JPG
2. Конвертируйте в WebP через [Convertio](https://convertio.co/ru/webp-converter/)
3. Убедитесь, что все изображения имеют атрибут `alt`
4. Используйте `loading="lazy"` для изображений ниже сгиба

### 5. Кроссбраузерность

Проверьте сайт в:
- Chrome
- Firefox
- Edge
- Safari (если возможно)

## Деплой собранного проекта (Vite)

После выполнения `npm run build` папка `dist/` содержит оптимизированную версию сайта.

### GitHub Pages (из папки dist/)

1. Соберите проект: `npm run build`
2. Загрузите содержимое папки `dist/` в репозиторий
3. В настройках GitHub Pages укажите папку `dist/`

Или используйте GitHub Actions для автоматической сборки.

### Netlify (с автодеплоем)

1. Подключите репозиторий к Netlify
2. Настройки сборки:
   - Build command: `npm run build`
   - Publish directory: `dist`
3. Netlify автоматически соберет и задеплоит проект

### Vercel (с автодеплоем)

1. Подключите репозиторий к Vercel
2. Vercel автоматически определит Vite
3. Build command: `npm run build`
4. Output directory: `dist`

## Чек-лист перед деплоем

- [ ] Все пути к файлам корректны
- [ ] CSS и JS минифицированы
- [ ] Изображения оптимизированы и имеют alt
- [ ] Мета-теги заполнены
- [ ] Сайт адаптивен (проверено через DevTools)
- [ ] Нет ошибок в Console
- [ ] HTML валиден (проверено через W3C Validator)
- [ ] Lighthouse показывает хорошие оценки
- [ ] Все ссылки работают
- [ ] Формы работают корректно
- [ ] Модальные окна открываются/закрываются

## Полезные ссылки

- [GitHub Pages](https://pages.github.com/)
- [Netlify](https://www.netlify.com/)
- [Vercel](https://vercel.com/)
- [W3C Validator](https://validator.w3.org/)
- [TinyPNG](https://tinypng.com/)
- [WebP Converter](https://convertio.co/ru/webp-converter/)
- [Vite](https://vitejs.dev/)

## Поддержка

При возникновении проблем проверьте:
1. Консоль браузера на наличие ошибок
2. Валидность HTML через W3C Validator
3. Корректность путей к файлам
4. Настройки деплоя на выбранной платформе

