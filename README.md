# brightshield
For Middle Earth
# source.archive

A research dump for the history video channel. Every link, note, and file
in one searchable place — links, notes, and scans, filterable by topic and episode.

🔗 **Live site:** enable GitHub Pages (see below) and your archive will be browsable at
`https://<your-username>.github.io/<repo-name>/`

---

## How this is organized

```
.
├── index.html        ← the site itself (open this in a browser, or via GitHub Pages)
├── sources.json       ← the database — every source lives here as one entry
├── assets/             ← actual files: PDFs, scans, images
└── scripts/
    └── add_source.py   ← run this locally to add a new source
```

The site is plain HTML/CSS/JS — no build step, no dependencies. It just reads
`sources.json` and renders it. That means you can also just edit `sources.json`
by hand if you ever want to, but the script is easier for day-to-day use.

## Adding a new source

From the repo root, run:

```bash
python3 scripts/add_source.py
```

It'll ask you for:
- **Title** — what it's called
- **Type** — `link`, `note`, or `file`
- **URL** (for links) or a **file path on your computer** (for files — it gets
  copied into `assets/` automatically)
- **Topics** — comma-separated tags like `WWII, archive`
- **Episodes** — comma-separated tags like `ep01, ep02`
- **Note** — why this matters / how you'll use it

It appends to `sources.json` and asks if you want to add another, so you can
batch through a research session in one go.

Then commit and push:

```bash
git add .
git commit -m "add sources"
git push
```

## Setting up GitHub Pages (so you get a real browsable site)

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under "Build and deployment," set **Source** to `Deploy from a branch`.
4. Pick your main branch and `/ (root)` folder, then save.
5. GitHub gives you a URL in a minute or two — bookmark it.

Every time you push new sources, the site updates automatically.

## A few notes for future-you

- Keep file sizes in `assets/` reasonable — GitHub will complain above 100MB
  per file, and large PDFs slow down repo clones. Scans/photos are usually fine;
  full video files are not what this repo is for.
- `sources.json` is just an array of objects — if the site design ever needs
  a refresh, the data underneath doesn't have to change at all.
- Topic and episode filters populate automatically from whatever tags exist
  in `sources.json` — no need to maintain a separate tag list anywhere.
