# Valley of Grace — Static Site

Simple static HTML/CSS site. This document explains how to run locally and deploy to Netlify.

## Project layout
- `index.html` — main page
- `style.css` — styles
- `images/` — header.png, side.png, bg images etc
- `README.md` — this file

## Prerequisites
- Git (optional, for repo deploy)
- (Optional) Node.js + npm if you want to use Netlify CLI or a local static server

## Local preview
Option A — open in browser:
- Open `index.html` directly in your browser.

Option B — simple static server (recommended to avoid file:// path issues):
- Using Node (no install):
  - npx serve: `npx serve .`
- Using Python:
  - Python 3: `python -m http.server 8000`
- Open `http://localhost:5000` (or the port shown) in browser.

## Netlify — quick deploy (no build)
1. Create a Netlify account.
2. In Netlify dashboard choose "Sites" → "Add new site" → "Deploy manually" → drag-and-drop your project folder (drop the folder contents).
3. Netlify will deploy; publish directory = project root (no build command).

## Netlify — via Git (recommended for continuous deploy)
1. Push your project to GitHub / GitLab / Bitbucket.
2. In Netlify dashboard: "New site from Git" → connect your repo.
3. Build settings:
   - Build command: (leave blank for pure static)
   - Publish directory: `/` (root) or the folder that contains `index.html`
4. Save and deploy.

## Netlify CLI (optional)
Install CLI:
```
npm i -g netlify-cli
```
Login and deploy:
```
netlify login
netlify init       # link to a site or create new
netlify deploy --dir=.      # for draft deploy
netlify deploy --prod --dir=.  # production deploy
```

## Notes / gotchas
- Keep image paths relative (e.g. `images/header.png`) so Netlify serves them correctly.
- If you use client-side routing, add `_redirects` or `netlify.toml` to serve `index.html` for all routes.
- If your CSS or images are not updating, clear cache (Ctrl+F5) or increment file names.
