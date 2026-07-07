# Bloom

A single-file audio visualizer that turns any track you drop into it into a living, glowing radial bloom — no build step, no dependencies, just open it in a browser.

## What it does

- **Upload any audio file** (mp3, wav, m4a, etc.) straight from your browser — nothing leaves your machine, there's no server involved.
- **Radial frequency bloom** — a ring of petals grows and shrinks with the song's frequency bands, bass on the outer sweep through to treble on the inner, painted across a wide, slowly drifting color arc.
- **Pulsing core** that breathes with the bass.
- **Waveform halo** — a thin ring tracing the actual live waveform as it orbits.
- **Beat-reactive embers** — lightweight beat detection on the bass band throws off drifting particles on each hit and estimates a live BPM.
- **Minimal transport dock** — upload, play/pause, and scrub, tucked into a frosted glass bar.

## Usage

1. Open `bloom.html` (or `index.html`, if you've renamed it) in any modern browser.
2. Click the upload icon in the bottom dock and choose a song.
3. It starts playing automatically — sit back, or scrub around with the seek bar.

That's it. No installation, no npm, no API keys.

## Running it locally

Since it's a single HTML file, you can just double-click it to open it in your browser. If your browser blocks local file audio for any reason, serve it instead:

```bash
python3 -m http.server 8000
```

then visit `http://localhost:8000/bloom.html`.

## Hosting it on GitHub Pages

1. Push this file to a repo.
2. In the repo, go to **Settings → Pages**, set source to your default branch, root folder.
3. Rename the file to `index.html` if you want it served at the clean root URL; otherwise it'll be available at `/bloom.html`.

## How it works

Built with the Web Audio API (`AnalyserNode`) and a single `<canvas>`. Frequency data drives the radial petals (grouped logarithmically so bass and treble both read clearly), time-domain data draws the waveform ring, and a simple running-average check on the bass band triggers the beat particles and BPM estimate. Colors are computed live from a curated hue arc rather than fixed values, so the palette evolves over the course of a track.

No external libraries — just HTML, CSS, and vanilla JavaScript.

## Browser support

Works in any modern browser with Web Audio API support (Chrome, Firefox, Safari, Edge). Mobile browsers work too, though the layout is tuned primarily for larger screens.

## License

MIT — do whatever you'd like with it.
