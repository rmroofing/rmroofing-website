# RM Roofing Website

A sleek, fast, static rebuild of rmroofing.co.uk — plain HTML/CSS/JS, no build tools required to host it.

## What's inside

```
index.html, about.html, services.html, gallery.html,
testimonials.html, faq.html, contact.html
+ 13 individual service pages (new-roof-installation.html, etc.)
css/style.css     — all design tokens, colors, type, layout
js/script.js      — mobile nav, FAQ accordion, contact form
assets/           — favicon
_build/           — Python templates used to generate the HTML (optional, see below)
```

## Editing content

Every page is a normal, readable HTML file — open any `.html` file in a text
editor and change the text directly. No build step is needed for simple edits.

For bigger changes (e.g. adding a new service to the whole site, changing the
nav on every page at once), it's easier to edit the templates in `_build/`
and regenerate:

```
python3 _build/build.sh
```

This rewrites all HTML pages from the shared header/footer/nav templates —
useful so you never have to hand-edit the same nav link in 20 files.

## Publishing on GitHub Pages (free hosting)

1. Create a new repository on GitHub (e.g. `rmroofing-website`).
2. Upload all these files to the repository (drag-and-drop on github.com
   works fine, or use `git push` if you're comfortable with git).
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment", set **Source** to "Deploy from a branch",
   branch `main`, folder `/ (root)`. Save.
5. GitHub gives you a live URL like `https://yourusername.github.io/rmroofing-website/`
   within a minute or two.

## Pointing rmroofing.co.uk at it later

When you're ready to replace the WordPress site:
1. In the repo, go to **Settings → Pages → Custom domain**, enter `rmroofing.co.uk`, save.
   This creates a `CNAME` file in the repo automatically.
2. Philip's team updates the DNS: an `A` record pointing to GitHub Pages' IPs
   (185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153) or a
   `CNAME` record for a `www` subdomain pointing to `yourusername.github.io`.
3. Wait for DNS to propagate, then tick "Enforce HTTPS" in the Pages settings.

Coordinate this step with Philip since he manages the DNS records, and don't
switch it over until Ross has approved the new site.

## Things to swap in before launch

- **Gallery photos**: the gallery page currently has labelled placeholder
  tiles instead of real project photos (no fake images were generated).
  Drop real photos in and update `gallery.html`.
- **Testimonials**: same approach — placeholder cards are marked clearly.
  Replace with real customer reviews (Google/Facebook).
- **Contact form**: currently opens the visitor's email client with the
  form details pre-filled (works with zero backend). Once the GHL "Roof
  Quotation Request Form" iframe is ready, that can replace the form in
  `contact.html` so submissions flow straight into the Roof Quotation
  Leads pipeline — there's a code comment marking exactly where.
