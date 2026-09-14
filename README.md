# Pitsamorn Ingkavara — Portfolio

Personal portfolio site for **Pitsamorn Ingkavara (พิศสมร อิงควระ)** — SAP S/4HANA Test Manager, Digital Transformation Programme Manager, and Data Governance & Management Specialist, Bangkok.

Two static pages — a landing page and an enterprise-console view of the same work. No build step, no dependencies, no framework. Open `index.html` and it works.

---

## Publish it on GitHub Pages

**1 — Create the repository**

On github.com, create a new repository. Name it `portfolio` for a URL like
`https://<your-username>.github.io/portfolio/`, or name it exactly
`<your-username>.github.io` for a URL with no sub-path at all.

Leave "Add a README" unticked — this package already has one.

**2 — Upload the files**

Easiest way, no command line:

1. Open the new empty repository on github.com
2. Click **uploading an existing file**
3. Drag in *the contents* of this folder — `index.html`, `console.html`, the `gal` folder, the `docs` folder, and the dot-files. Do **not** drag the outer folder itself, or every path gains an extra level and the images break.
4. Write a commit message (for example `Add portfolio site`) and click **Commit changes**

Or with Git:

```bash
cd ingkii-portfolio
git init
git add .
git commit -m "Add portfolio site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

**3 — Turn on Pages**

In the repository: **Settings → Pages**. Under *Build and deployment*, set
**Source: Deploy from a branch**, **Branch: `main`**, **Folder: `/ (root)`**, then **Save**.

Give it one to two minutes. The URL appears at the top of that same Settings → Pages screen.

**4 — Check it**

Open the URL and confirm the deliverable images load and the carousel advances. If images are missing, the upload nested the folders one level too deep — see step 2.

---

## What's in here

```
index.html      landing page — hero, projects, auto-advancing gallery
console.html    app-console view — sidebar nav, KPI tiles, tabs, tables
gal/            56 files: 26 deliverable images + 2 CV pages, each with a thumbnail
docs/           CV (PDF + Word) and the portfolio deck (PDF), linked from the page
.nojekyll       stops GitHub Pages running Jekyll, which it does not need
.gitignore      keeps OS junk out of the repository
```

## Two pages, two audiences

Both read from the same `gal/` images and tell the same story. Pick whichever suits
the person you are sending it to — or keep both, since they cross-link in the nav.

| | `index.html` | `console.html` |
|---|---|---|
| Reads like | A landing page — scroll top to bottom | An enterprise application — pick a screen |
| Best for | Recruiters, first contact, a link on LinkedIn | Hiring managers and delivery leads who want the numbers |
| Navigation | Sticky nav, dot rail, scroll | Left sidebar, tabs, no page scroll |
| Gallery | One image at a time, auto-advancing | Filterable tile grid with a viewer |
| CV | Download link | A **CV screen** showing both pages, plus downloads |
| Style | Navy / blue / yellow, Sora + Manrope | Indigo / electric blue gradient, Plus Jakarta Sans |

To make the console the front page instead, rename the files — `index.html` to
`landing.html`, `console.html` to `index.html` — and swap the two cross-links in
the navigation of each.

## Editing it

The landing page lives in `index.html`; the console lives in `console.html`. The
table below covers `index.html`; `console.html` follows the same shape — palette
in `:root`, content in `<section class="view">` blocks, gallery data in the `G`
array.

| To change | Look for |
|---|---|
| Colours | the `:root { }` block at the top of `<style>` — light theme first, dark theme below it |
| Fonts | the Google Fonts `<link>` in `<head>`, then the `font-family` rules |
| Headline, stats, bio | the `<header class="hero">` block |
| The three capability cards | `<section id="capability">` |
| Project cards | the three `<article class="proj">` blocks |
| Case-study panels | the `CASES` object in the `<script>` at the bottom |
| Gallery images and captions | the `G` array in the `<script>` — one line per image |
| Carousel speed | `DUR=7000` in the script (milliseconds) |
| Work history | `<section id="experience">` |

### Adding a gallery image

1. Put a full-size image in `gal/` as `my-image.jpg` (about 1500px wide)
2. Put a thumbnail beside it as `my-image-t.jpg` (about 640px wide)
3. Add one entry to the `G` array:

```js
{f:"my-image", t:"test", ti:"Short title", c:"One or two sentences on what this shows and why it matters."},
```

`t` is the filter track: `test` (test management), `dt` (transformation) or `dg` (data governance).

### Using a custom domain

Add a file named `CNAME` at the root containing just your domain (`portfolio.example.com`), then point a CNAME DNS record at `<your-username>.github.io`. GitHub's Pages settings will confirm once DNS resolves.

---

## Client anonymisation — what has been removed, and what has not

Client names have been removed from the **deliverables**:

- **Inside the images.** Every occurrence of the client group's name and its derived
  identifiers was located and covered — solid fills on the clean diagrams, pixelation
  on the screenshots. That includes the programme codename, the corporate mail
  domain and the Jira tenant URL, since each of those identifies the client just as
  directly as the name itself. An OCR sweep across all 28 images confirms none of the
  target strings survive.
- **In the page copy.** Programme and case-study text now reads "a leading Thai
  petrochemical group", "a Thai refinery group" and similar.

Client names have **not** been removed from:

- **The Profile / Experience section**, which is employment history — normal on a CV.
- **CV page 1**, which is the CV as issued and names each employer.

Be aware of what that combination means: anyone who reads the experience list and
then looks at the deliverables can join the two together. The anonymisation protects
the artefacts from casual scraping and from being indexed against a client's name —
it is not anonymity. If you need the stronger version, say so and the employer names
in the Profile section and on CV page 1 can be genericised too.

Whatever you choose, before making the repository public it is worth **confirming
with your current and former employers** that this material can be shown externally.
Note also that on a free GitHub account, Pages sites are public even when the
repository is private — the URL is unlisted, not protected.

---

## Credits and licence

Design and content © 2026 Pitsamorn Ingkavara. All rights reserved.

Typefaces via Google Fonts: [Sora](https://fonts.google.com/specimen/Sora), [Manrope](https://fonts.google.com/specimen/Manrope), [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono), [Plus Jakarta Sans](https://fonts.google.com/specimen/Plus+Jakarta+Sans), [Roboto Mono](https://fonts.google.com/specimen/Roboto+Mono) — all SIL Open Font License 1.1.

---

## Typos to fix in the source CV

Spotted while rendering `docs/Resume_Pitsamorn_Ingkavara_2026.pdf` — these are in the
original design file, so they need correcting there:

| Reads | Should read |
|---|---|
| PTT **Grobal** Chemical Public Company (twice) | PTT **Global** Chemical Public Company |
| CORE **COMPLETENCIES** | CORE **COMPETENCIES** |
| Team **Coachng** & Super Vision | Team **Coaching** & Supervision |
| Auto **Notificaton** | Auto **Notification** |
| MS **Project,Monday** | MS **Project, Monday** |
| UAT **Exist** Analyzer / UAT **Exist** Analysis | UAT **Exit** Analyzer / UAT **Exit** Analysis |
