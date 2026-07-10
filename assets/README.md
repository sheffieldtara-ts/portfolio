# Image exports needed from Figma

Note: `card-analytics.png` / `card-ai.png` / `card-app.png` (previously listed
here) are no longer used — the work page's 3-card gallery was replaced by the
tabbed panel layout, so those rows have been removed.

## AI Text to Chart panel (case-studies.html, `#panel-ttc`) — 4 slots

Source file: **AI Chart Builder**, fileKey `xWqJEPRL62w9cbeU82Ogy6`. Open it in
Figma and find the flow map (node `1:25944`) — it's a series of horizontal
rows on an orange background, each row a named flow ("Interaction leading to
previewing a chart", "Add to NEW dashboard", "Add to an EXISTING dashboard",
"Start a new chat", "View History of conversations"), each row a left-to-right
sequence of screens.

| File name            | Where in the row                                                                                      | Used on (slot)                              | Export |
|-----------------------|--------------------------------------------------------------------------------------------------------|----------------------------------------------|--------|
| `ttc-result.png`      | Row **"Interaction leading to previewing a chart"**, 3rd frame — the "463" chart with the follow-up/refine panel on the right | Top-right slot beside Overview/Problem       | PNG, 2x |
| `ttc-flow-strip.png`  | The whole **"Interaction leading to previewing a chart"** row — select all 4 frames together (landing search → generating → chart+refine → refined chart) and export as one wide image | Full-width slot below the problem section    | PNG, 2x |
| `ttc-followup.png`    | Row **"Interaction leading to previewing a chart"**, 4th frame — the compact chart card with the follow-up question chip | Small slot beside "How I got here"           | PNG, 2x |
| `ttc-outcome.png`     | Row **"Add to an EXISTING dashboard"**, last frame — "Inspection Dashboard QA" showing the new chart sitting alongside the existing dashboard charts | Slot beside Solution/Outcome                 | PNG, 2x |

**✅ Done (2026-07-10)** — all 4 exported and dropped in.

## KPI Visualisation panel (case-studies.html, `#panel-kpi`) — 4 slots

Source file: **Analytics KPI's**, fileKey `gMvOdGpXSuq2lBlP2bAbsZ`, node
`8:5553` ("01 Slice 1 - KPI Configuration", Approved). Sections on that page,
top to bottom: Components, **KPI selection** (5 frames), **Threshold and
Display configuration** (8 frames), **Timeline table configuration** (5
frames), **Colour-Code configuration** (single line/range examples, then
"Multiple line/range example").

| File name             | Where                                                                                          | Used on (slot)                          | Export |
|------------------------|--------------------------------------------------------------------------------------------------|-------------------------------------------|--------|
| `kpi-config.png` + `kpi-config-full.png` | The **whole page** — every section, exported as SVG and rasterized (see note below, this one didn't go as scoped — in a good way) | Top-right slot beside Overview/Problem    | see below |
| `kpi-flow-strip.png`   | The whole **Threshold and Display configuration** row — all 8 frames together, wide export      | Full-width slot below the problem section | PNG, 2x |
| `kpi-modes.png`        | **Colour-Code configuration** → **"Multiple line/range example"** — the 2 frames together (single-value lines vs. min/max range bands) | Small slot beside "How I got here"        | PNG, 2x |
| `kpi-final.png`        | **KPI selection** section, top-right **"Colour picker"** frame — finished colour-coded multi-KPI chart | Slot beside Solution/Outcome              | PNG, 2x |

**✅ 3 of 4 done (2026-07-10, updated).** `kpi-modes.png` was re-exported as a
tighter 2×2 grid (much better fit for the slot-sm layout — see styles.css
note below) and `kpi-flow-strip.png` / `kpi-final.png` were re-dropped too.

**✅ `kpi-config.png` resolved (2026-07-10) — via SVG, not a re-crop.** Tara
wanted to keep the whole-page "wall of screens" (all the exploration, not
just one frame) — re-exported the same full selection as `kpi-config.svg`
instead of PNG. Vector export sidestepped the raster memory problem entirely
(SVGs don't have a pixel grid until something rasterizes them), so Claude
could render it down to whatever size was actually needed:
`kpi-config.png` (1300px, ~225KB) for the slot, and `kpi-config-full.png`
(3200px, ~750KB) for the lightbox pop-out via a `data-full` attribute on the
`<img>`. The source `.svg` (16.5MB — Figma outlines all text to paths, so
vector didn't mean small here) and the original oversized `.png` were both
deleted after rendering; only the two derived PNGs remain in this folder.
This image uses `object-fit: contain` (class `fit-contain` in styles.css)
instead of the usual crop-to-fill, so nothing in the wall gets cut off.

## Mobile-editing UX panel (case-studies.html, `#panel-media`) — 4 slots

Source file: **Media-on-Mobile**, fileKey `hajSW0hsKtGOnLhSfQf9rW`. Only one
page ("✅ Ready for Dev") — it's a toolbar component/state spec, not a full
annotated-photo flow, but the **"Dark Mode Pattern"** and **"Light Mode
pattern"** sections (laid out side by side on the canvas) each contain a full
editor screen mockup plus toolbar state breakdowns.

| File name              | Where                                                                                     | Used on (slot)                          | Export |
|--------------------------|---------------------------------------------------------------------------------------------|-------------------------------------------|--------|
| `media-editor.png`      | **"Dark Mode Pattern"** section → the **"Dark"** frame — full editor screen (Cancel/Done, image, toolbar) | Top-right slot beside Overview/Problem    | PNG, 2x |
| `media-flow-strip.png`  | **Both** "Dark Mode Pattern" and "Light Mode pattern" sections together, wide export        | Full-width slot below the problem section | PNG, 2x |
| `media-states.png`      | The toolbar state comparison group (bottom right of the page) — Default / Selected / Disabled swatches | Small slot beside "How I got here"        | PNG, 2x |
| `media-outcome.png`     | **"Light Mode pattern"** section → the **"Light"** frame — full editor screen               | Slot beside Solution/Outcome              | PNG, 2x |

**✅ Done (2026-07-10) — all 4 exported as SVG and came back better than
scoped.** Tara's export actually included real annotation-tool screens (Draw
select / Text select / Shapes select / Rotate, on a real evidence photo of
building damage) rather than just the abstract state swatches described
above — a better match for the case study copy than what was originally
findable in the file. All 4 rasterized with cairosvg (see kpi-config note)
and compressed. `media-flow-strip.png` and `media-outcome.png` use
`class="fit-contain"` since their source aspect ratios don't match their
slots' shapes (near-square and wide-landscape respectively) — same fix as
kpi-config, prevents cropping.

The remaining 2 panels (Holistic Analytics, Project TARS — 8 slots) are still
empty — same process, one panel at a time.

**Reminder if any export comes back oversized:** re-export as SVG and ask
Claude to rasterize it — see the kpi-config note above for why that works
when a plain PNG doesn't. Tara now defaults to SVG for these exports since
it's worked twice — good habit to keep.

Optional: `avatar-ben.png`, `avatar-kael.png` (48px referral avatars on the
landing page — they fall back to a gradient if missing).

Already done: `venn.svg` (hero graphic). To update it, just re-export the
graphic from Figma over this file — no code changes needed.

How: select the layer(s) in Figma → Export panel (bottom right) → set 2x → Export.
