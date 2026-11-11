# Gym Log v10

Personal, offline-first PWA for beginner full-body strength training and 25m pistol sporting journal.

## Use

Host the repository root on any HTTPS static host (e.g. GitHub Pages, deploy `main` / root). Open `https://vanvietit-star.github.io/GymLog/` and use **Share → Add to Home Screen** on iPhone. The app is client-only; it does not send workouts, shooting scores, photos, or user data to GitHub.

## Features

- Full Body A/B/C flexible 3-day rotation, quick kg/reps tracking, workout draft recovery, optional exercise swapping, locally authored technique diagrams and tips.
- Workout history with edit/delete; progress/volume/estimated 1RM trend; weight tracking with 7-day rolling summary.
- 25m pistol journal with .22 default, quick scoring and 5-/10-shot series, consistent-condition scores, editing, optional misses and multiple per-session target photos.
- On-device photo resizing up to 1600px and WebP/JPEG quality compression, storing blobs in IndexedDB. No uncompressed originals kept.
- Import v9 `localStorage['ft']` on first run (leaves the original data untouched), migration of workout snapshots, shooting history, weights and in-progress draft.
- JSON export (excludes images) or *complete* ZIP (data + photos), merge/replace restore with confirmation.
- All functionality works offline after the first successful install. No third-party dependencies or backend.

## Important privacy and data facts

- GitHub Pages hosts source code **only**. Photos and diary entries are stored in the local browser IndexedDB on the device; they are not synced between devices.
- iOS may clear browser/PWA data due to user action or storage pressure. **Export ZIP backups** to iCloud Drive regularly. JSON exports do not include photographs.
- If old v9 data was saved under a different origin/path, it cannot be automatically detected by the new site. First export the v9 JSON backup and import it into v10.
- Illustrations are original **schematic SVG diagrams**, not full exercise video demonstrations; external YouTube search requires internet.
- ZIP restore is intentionally restricted to the store-only ZIP format produced by this app, with checksum verification.

## Project layout

- `index.html`: PWA entry point
- `styles.css`: mobile-first dark theme
- `legacy.js`: unchanged v9 workout templates and guidance for historical migration
- `storage.js`: IndexedDB, migration, standalone ZIP backup/restore
- `app.js`: gym, shooting, photo compression and UI
- `sw.js`: offline cache for static assets
- `manifest.json` + icons: PWA installation assets

## Manual smoke tests

1. Load with no data; start A; complete 1 set; reload; draft should persist.
2. Finish A and check B is suggested; edit history and read it back.
3. Add a 30-shot 25m pistol session, 250/300 points, attach one photo; reload to see the photo.
4. Try 301/300 points: must be rejected. Edit and delete a shooting entry.
5. Export ZIP, import with merge (no duplicates), and restore in a clean browser profile (including photo).
6. Prepopulate v9 `ft` localStorage and load v10; no old logs, shooting, weights or draft should be lost.
7. Go offline after first load; reopen, track exercise and shooting journal without network.

Version: 10.0 (2026-11-11).