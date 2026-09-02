# jetlag-legal

The public privacy policy and support pages for the **Jet Lag** app, served by
GitHub Pages.

This repo exists for one reason: the App Store and Google Play both require a
publicly reachable **privacy policy URL** and a **support URL**, and the app's
own repository is private. Rather than make the app source public, the two
documents the stores need live here on their own.

**No app source, keys, or build config belong in this repo. It is public.**

## Pages

| Path | Purpose |
|---|---|
| `/` | Landing page, links to both |
| `/privacy/` | Privacy policy — the URL given to both stores |
| `/support/` | Support page — the App Store support URL |

## Editing the privacy policy

`privacy/index.md` is **generated**. Do not hand-edit it.

The source of truth is `PRIVACY.md` in the app repo, which sits next to the
code it describes so it gets updated in the same commit as the behaviour it
describes. To publish a change:

```sh
./sync-privacy.sh ../jetlag-rn/PRIVACY.md
git commit -am "Sync privacy policy"
git push
```

If the two ever disagree, the app repo wins.

## Editing support

`support/index.md` is hand-written and lives only here — it is about how to
get help, not about what the app does, so it has no counterpart in the app
repo.

## Notes

- The layout is a single self-contained file (`_layouts/default.html`) with
  inline CSS. No remote theme, no webfont, no CDN — a store reviewer opening
  a required URL should never see a broken page because something upstream
  moved.
- Jekyll is what renders the Markdown here, so there is deliberately **no**
  `.nojekyll` file. Adding one would serve raw Markdown to a reviewer.
- Both URLs are load-bearing during review. If Pages is disabled or the repo
  is made private, both store listings break.
