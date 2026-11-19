# SAKAS | Idea Box

A standalone idea page for Sakas: anyone can send an idea for what we film,
with an optional picture or voice message, no account needed.

Live: https://sakasidea.noiraunoir.com

This is deliberately **separate from the client portal** at noiraunoir.com/sakas/
(that one keeps its own request box). A GitHub Pages repo can only carry one
custom domain, so this page needs its own repo.

## How it works

- The form posts to the shared Cloudflare Worker relay (source lives in the
  mc-kresha-hub repo under `cloudflare-worker/`) with `site: "sakasidea"`.
- Each idea becomes a GitHub issue in this repo labeled `idea`.
- Pictures and voice messages are stored on the `uploads` branch, so an upload
  never rebuilds the site. Voice notes play back through the relay, because
  GitHub serves audio as `text/plain` with sniffing disabled.
- The wall is read through the relay too, which avoids GitHub's 60 requests per
  hour limit for anonymous visitors.

## Moderating

Open [`admin.html`](admin.html) directly (it is not linked from the page):
every idea has a Remove button, removed ideas can be restored. Needs a
fine-grained token with **Issues: read and write** on this repo, pasted once
into the page and kept in that browser only.

## Style

House style: pitch black background, plain white text, no colors, no shadows,
Playfair Display headings with Inter body text.
