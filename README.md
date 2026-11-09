# yogaudio.app

The landing page for Yogaudio: plain HTML and CSS, no build step, no JavaScript, no cookies or analytics.
It is served by GitHub Pages at https://yogaudio.app.

| File | What it is |
| --- | --- |
| `index.html` | Landing page: name, one-line description, App Store badge, beta / practitioner / instructor emails |
| `privacy.html` | Privacy policy |
| `accessibility.html` | Accessibility statement and how to report a problem |
| `404.html` | Page not found (GitHub Pages serves it automatically) |
| `styles.css` | All styles, light and dark mode |
| `CNAME` | Tells GitHub Pages the custom domain is `yogaudio.app` |
| `robots.txt`, `sitemap.xml` | For search engines |
| `.nojekyll` | Serves the files as they are, without Jekyll processing |
| `assets/` | App icon, favicon, Apple touch icon, social preview image (`og-image.png`, 1200 × 630), Apple's pre-order badge |

## App Store

The badge links to <https://apps.apple.com/app/id6832462412>. The same ID is in the structured data
(`"downloadUrl"`) and the Smart App Banner tag (`apple-itunes-app`) in the `<head>` of `index.html`.
`assets/pre-order-on-the-app-store.svg` is Apple's official badge, from the
[App Store marketing guidelines](https://developer.apple.com/app-store/marketing/guidelines/); do not edit it.

When the app launches, replace it with the **Download on the App Store** badge
(<https://developer.apple.com/assets/elements/badges/download-on-the-app-store.svg>), change the image's
`alt` to "Download on the App Store" (it must match the words on the badge), and change
"Coming soon, available to pre-order now." under it.

## Publish on GitHub Pages

In this repository: **Settings → Pages → Build and deployment**, Source **Deploy from a branch**,
branch **main**, folder **/ (root)**, Save. **Custom domain** should then read `yogaudio.app`
(from the `CNAME` file); if not, type it and Save. Every push to `main` republishes the site.

## Connect yogaudio.app (Namecheap)

1. **Verify the domain with GitHub first** (stops anyone else from claiming it on GitHub Pages):
   GitHub → your profile picture → **Settings → Pages → Add a domain** → `yogaudio.app`.
   GitHub shows a TXT record. In Namecheap → **Domain List → Manage** next to yogaudio.app →
   **Advanced DNS → Add new record**, add that TXT record (Host is the part before `.yogaudio.app`,
   for example `_github-pages-challenge-robinkanatzar`), then click **Verify** in GitHub.
2. In the same **Advanced DNS** page, delete Namecheap's default parking records
   (usually a `CNAME` for `www` pointing to `parkingpage.namecheap.com` and a `URL Redirect` for `@`).
3. Add these records:

   | Type | Host | Value |
   | --- | --- | --- |
   | A Record | `@` | `185.199.108.153` |
   | A Record | `@` | `185.199.109.153` |
   | A Record | `@` | `185.199.110.153` |
   | A Record | `@` | `185.199.111.153` |
   | AAAA Record | `@` | `2606:50c0:8000::153` |
   | AAAA Record | `@` | `2606:50c0:8001::153` |
   | AAAA Record | `@` | `2606:50c0:8002::153` |
   | AAAA Record | `@` | `2606:50c0:8003::153` |
   | CNAME Record | `www` | `robinkanatzar.github.io.` |

   With the `www` record, GitHub redirects www.yogaudio.app to yogaudio.app.
4. Wait for DNS (minutes, sometimes a few hours). The repository's **Settings → Pages** shows
   "DNS check successful" when it is ready.
5. Tick **Enforce HTTPS** there once it becomes available. `.app` domains only work over HTTPS
   (browsers require it for the whole `.app` top-level domain), so the site will not load until
   GitHub has issued the certificate, which it does automatically after the DNS check passes.

## After it is live: search engines

- **Google Search Console** (<https://search.google.com/search-console>): add the domain property
  `yogaudio.app`, verify with the TXT record it gives you (Namecheap Advanced DNS again),
  then submit `https://yogaudio.app/sitemap.xml` under Sitemaps.
- **Bing Webmaster Tools** (<https://www.bing.com/webmasters>): import from Search Console, which also covers DuckDuckGo.
- Link to `https://yogaudio.app` from the App Store listing (Marketing URL and Support URL fields),
  your own site and social profiles. Links from relevant sites are what helps most.
- Use `https://yogaudio.app/privacy.html` as the Privacy Policy URL in App Store Connect.

What is already in place for SEO: a descriptive `<title>` and meta description on every page, canonical
URLs, one `<h1>` and a clean heading outline, real text describing the app, `MobileApplication`
structured data, Open Graph and Twitter tags with a preview image, `sitemap.xml`, `robots.txt`,
a fast page with no scripts, and good accessibility (which search engines reward too).

## Accessibility

The site aims for WCAG 2.2 AA, with AAA contrast (at least 7:1) and AAA target sizes. Checked with
axe-core (WCAG 2.0 to 2.2 A, AA, AAA rules and best practices) in light and dark mode at 320 and
1280 pixels wide, with no violations; keyboard tab order; no sideways scrolling at 320 pixels wide
or with 200% text and WCAG 1.4.12 text spacing; and forced colors mode.

Please also try it yourself with VoiceOver on iPhone and Mac before launch: swipe through the page,
use the rotor to jump by headings and links, and check each email button opens Mail with the subject filled in.

When you change anything, keep:

- Every page's footer the same, in the same order (WCAG 3.2.6 Consistent Help).
- Link and button text that makes sense on its own ("Email to join the beta", not "Click here").
- Links opening in the same tab.
- Colors from the variables at the top of `styles.css`; they are all checked for contrast.
- The "Last updated" date on the privacy policy and the `lastmod` dates in `sitemap.xml` current.
