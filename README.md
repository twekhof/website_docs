# tobiaswekhof.com

Personal academic website of Tobias Wekhof. Plain HTML and CSS, no build step and no third-party requests (system fonts, no trackers).

## Files

- `index.html`: the home page, laid out like the old Google Site and kept short on purpose: the banner, the photo on the left, and on the right the name, a one-line welcome, the CV and email links, Topics, Methods, the job market paper, and round icons for LinkedIn, GitHub and Google Scholar. At the bottom, one entry for the practice report "Teaching with generative AI" (`files/Wekhof_Teaching_with_GenAI.pdf`, cover picture `files/media/teaching-with-genai.webp`).
- `research.html`: job market paper, publications, working papers and other publications. Titles are visible; each abstract is folded into a drop-down (`<details class="abs">`).
- `media.html`: policy briefs and articles, each with a small picture (`files/media/`).
- There is no teaching page on purpose: teaching is in the CV.
- Every page has the same menu (Home, Research, Media) and footer. The CV is linked from the home page only, not from the menu. When you add a page, copy the header and footer and mark the current page with `aria-current="page"`.
- `style.css`: layout and colours, with a dark mode that follows the visitor's system setting.
- `files/`: public files linked from the page. Keep the file names stable so old links keep working.
  - PDF links open in a new tab (`target="_blank" rel="noopener"`). GitHub Pages serves PDFs as `application/pdf`, so browsers show them directly; no nbviewer is needed. nbviewer caches files for up to an hour. Don't link to raw.githubusercontent.com, which makes browsers download the file.
  - PDFs: `CV_Wekhof.pdf`, `Wekhof_JMP.pdf`, `Wekhof_Teaching_with_GenAI.pdf` (the 9 Nov 2026 practice report; replace the file to update it, keep the name).
  - Images, as on the old Google Site: `panorama.webp` (1280 × 149), the thin mountain strip at the top of every page, and `mountains.webp` (1280 × 460), the larger view of the same valley at the bottom of every page, just above the footer. `portrait.jpg` and `photo.jpg` are described below.
- Design: colours come from the banner photo. Each research area has its own colour (gold: sustainable finance; slate: energy and environment; violet: AI and text as data). On the Research page, every paper title is followed by a small filled label with its area's name (`<span class="tag">…</span>` inside `<li class="s-fin|s-energy|s-text">`), and the legend at the top shows the same three labels.
- `.nojekyll`: tells GitHub Pages to serve the files as they are.

Only public material belongs in this repository. It is separate from the applications folder on purpose.

## Updating

- New CV: export from Overleaf and replace `files/CV_Wekhof.pdf`.
- New paper version: replace the PDF in `files/`, or update the link in `research.html` (and in `index.html` for the job market paper).
- Photo: `files/portrait.jpg` (720 × 900, 4:5) is the home-page photo, and `files/photo.jpg` (512 × 512) is the square crop used when the site is shared. Replace both files to change the photo.

## Publishing on GitHub Pages

The site lives in the repository `twekhof/website_docs`, branch `gh-pages`, at the root, next to the older PDFs that the Google Site linked to (`CV_Wekhof_main_academic.pdf` and the paper PDFs). Pages deploys from that branch, so a push to `gh-pages` updates the site within about a minute. Until the domain moves, the site is at https://twekhof.github.io/website_docs/. The links are relative, so they work there and on the domain.

To update: copy the changed files into a clone of `gh-pages`, commit and push.

## Moving tobiaswekhof.com from Google Sites

Do these steps in this order. If the `CNAME` file goes in while the domain still points to Google Sites, GitHub forwards the old `twekhof.github.io/website_docs/…pdf` links to tobiaswekhof.com, where Google Sites has no such files.

1. At the domain registrar:
   - point `www` to `twekhof.github.io` with a CNAME record;
   - point the bare domain to GitHub's four A records: 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153.

   Remove the old Google Sites records for the same names. Leave any email (MX) records alone.
2. Then add a file `CNAME` containing `www.tobiaswekhof.com` to `gh-pages`, or set the custom domain under Settings → Pages of `website_docs`.
3. When GitHub shows the domain as verified, tick "Enforce HTTPS". The old `twekhof.github.io/website_docs/…` links then forward to `www.tobiaswekhof.com/…`.
