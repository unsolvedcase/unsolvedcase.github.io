# Videos — file conventions (AAA builds)

Videos are hosted as **separate files** in this folder and referenced by
relative URL from `index.html` (e.g. `videos/trailer.mp4`). **Never**
base64-inline a video into the HTML — it would blow GitHub's 100 MB
per-file limit.

Naming for later batches (per-case intro videos, suspect videos):

- `trailer.mp4` — the game trailer, played from the home screen.
- `case-XX-intro.mp4` — cinematic intro video for case XX (01–32).
- `case-XX-suspect-<suspect-id>.mp4` — suspect interrogation video, the
  suspect speaking. Suspect IDs match the case data (e.g. `case-01-suspect-sofia-reyes.mp4`).

Player component: the reusable `aaaVideoPlayer(videoEl, playBtn, muteBtn, noteEl)`
helper in `index.html` wires play + mute for any video; reuse it for new
players instead of writing a second one. If a video file is missing, the
player hides its card (error handler) instead of breaking the page.

Keep each video small (720p, ~10s, a few MB). The whole repo tree must stay
well under GitHub's limits; the HTML file itself is already ~29 MB.

## Shipped

- **Batch 1 (2026-10-27):** `case-01-intro.mp4` (6.2 MB) through
  `case-06-intro.mp4` (4.5 MB) — 10s h264 1280x720 cinematic intros for
  Cases 1–6, title on screen, no dialogue. Wired into the briefing screens
  via the shared `aaaVideoPlayer()` helper (static cards for Cases 1–2,
  dynamic card for the generic view, Cases 3–6; hidden for Cases 7+ until
  their batch lands).
- Next: batch 2 = Cases 7–12 intro videos; later batches = suspect videos.
