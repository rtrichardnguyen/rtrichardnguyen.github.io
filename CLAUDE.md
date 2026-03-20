# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-page birthday website for Sandra's 20th birthday ("Golden Birthday" — turning 20 on March 20). It's a self-contained `index.html` with inline CSS and JavaScript — no build system, no dependencies, no framework.

## Structure

- `index.html` — the entire application (HTML + CSS + JS)
- `photos/` — 20 JPEG images for the polaroid gallery (currently not wired up in the `photos` array)

## How to Run

Open `index.html` directly in a browser, or use any local server:

```
python3 -m http.server 8000
```

## Key Sections in index.html

The file is organized into clearly marked sections with comment banners:

1. **CSS** (lines 7–733) — all styles including animations, responsive breakpoints at 768px and 480px
2. **HTML** (lines 735–788) — hero, polaroid gallery, lightbox, iMessage-style chat, footer
3. **JS Configuration** (lines 805–842) — the two arrays to edit:
   - `photos[]` — 20 entries with `src` and `caption`; photos with empty `src` show a numbered placeholder
   - `textMessages[]` — chat bubble sequence with `type` (sent/received), `text`, and `delay` (ms)
4. **JS Engine** (lines 849–1175) — gallery rendering, lightbox, chat animation, sparkle canvas, balloon system, confetti system

## Configuration Pattern

All user-editable content is in the configuration block at the top of the `<script>` tag. The engine code below it reads these arrays and builds the DOM dynamically. To add a photo, set its `src` to a path in `photos/` (e.g., `"photos/IMG_1897.jpeg"`) and update the `caption`.

## Design System

CSS custom properties defined in `:root`: `--gold`, `--gold-light`, `--gold-dark`, `--gold-glow`, `--cream`, `--dark`, `--brown`. Three Google Fonts: Playfair Display, Poppins, Dancing Script.
