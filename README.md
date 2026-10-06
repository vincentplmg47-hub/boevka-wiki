# Вики проекта — источник (Quartz)

Исходник вики-сайта «Боёвка Stellaris» — фан-проекта по реинжинирингу боёвки для Stellaris.
Движок: [Quartz 5](https://quartz.jzhao.xyz) — бесплатный open-source «Obsidian Publish»:
граф связей, обратные ссылки, полнотекстовый поиск, список статей, теги, тёмная тема.

## Что здесь

- `content/` — заметки в формате Obsidian (Markdown + `[[вики-ссылки]]` + YAML-frontmatter).
  Этот же каталог можно открыть как Obsidian-vault.
- `quartz.config.yaml` — настройки сайта (тема, шрифты, локаль ru-RU).

## Как пересобрать сайт

1. `git clone -b v5 https://github.com/jackyzha0/quartz.git`
2. `cd quartz && npm install --include=dev`
3. Скопировать сюда `content/` и настройки:
   `rsync -a --delete <этот-репозиторий>/content/ content/ && cp <этот-репозиторий>/quartz.config.yaml . && cp <этот-репозиторий>/custom.scss quartz/styles/custom.scss`
4. `npx quartz build` → готовый статический сайт в `quartz/public/`

## Публикация

`public/` — полностью статический сайт: его можно отдать на любой бесплатный
статический хостинг (GitVerse Pages, GitHub Pages и т.п.). Никакой сервер не нужен.

Важно: перед публикацией убедиться, что в `quartz.config.yaml` прописан реальный
адрес сайта в `baseUrl` (иначе canonical-ссылки и sitemap будут с превью-адресом).
