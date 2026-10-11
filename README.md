# seamcraft.dev

The "coming soon" page for Seamcraft, hosted on GitHub Pages at https://seamcraft.dev.

| File | Purpose |
|---|---|
| `index.html` | The coming-soon page. No scripts, no cookies, no external requests. |
| `privacy.html` | The privacy policy. Change its effective date when its content changes. |
| `styles.css` | Shared styles for both pages, with light and dark themes. |
| `favicon.svg` | The two-panel stitched-seam mark. |
| `CNAME` | Tells GitHub Pages to serve this site at `seamcraft.dev`. |
| `.well-known/microsoft-identity-association.json` | Proves to Microsoft Entra that the Seamcraft app registration owns seamcraft.dev (its publisher domain). |
| `.nojekyll` | Stops GitHub Pages skipping folders that start with a dot, such as `.well-known`. |

## Publish

1. Create the GitHub org `seamcraft-dev` and a public repo in it named `seamcraft.dev`. Push this folder to it.
2. In the repo, go to **Settings → Pages**. Set the source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
   The custom domain should fill in as `seamcraft.dev` from the `CNAME` file.
3. Recommended: in the org, go to **Settings → Pages → Add a domain** and verify `seamcraft.dev`. GitHub gives you a TXT record to add.
   Verifying stops anyone else from using the domain on GitHub Pages.
4. In GoDaddy, go to **seamcraft.dev → DNS**:
   - Delete GoDaddy's default `A @` record (the parked page) and any `CNAME www` it created.
   - Add these records:

     | Type | Name | Value |
     |---|---|---|
     | A | @ | 185.199.108.153 |
     | A | @ | 185.199.109.153 |
     | A | @ | 185.199.110.153 |
     | A | @ | 185.199.111.153 |
     | AAAA | @ | 2606:50c0:8000::153 |
     | AAAA | @ | 2606:50c0:8001::153 |
     | AAAA | @ | 2606:50c0:8002::153 |
     | AAAA | @ | 2606:50c0:8003::153 |
     | CNAME | www | seamcraft-dev.github.io |
     | TXT | (from step 3) | (from step 3) |

5. Wait for DNS to update (usually under an hour) and for GitHub to issue the HTTPS certificate. Then tick **Enforce HTTPS** in **Settings → Pages**.
   Browsers only load `.dev` sites over HTTPS, so the site won't open until the certificate has been issued.

## seamcraft.app

To send `seamcraft.app` to the same page, use **seamcraft.app → Forwarding** in GoDaddy and set up a permanent (301) forward to `https://seamcraft.dev`.
Browsers also only load `.app` over HTTPS, so check that GoDaddy's forward works on `https://seamcraft.app`. If it doesn't, add `seamcraft.app` as a second GitHub Pages site later.
