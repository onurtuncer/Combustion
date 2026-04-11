# Governing Equations of Fluid Flow with Chemistry — Beamer

Beamer conversion of the original PowerPoint lecture deck (112 slides).

## Contents

- `main.tex` — Beamer source (single file, 112 frames)
- `main.pdf` — compiled PDF (also 112 pages)
- `fig/` — figure assets
  - `itu_logo.png` — ITU seal used on the title slide
  - `slideNN.png` — original-slide PNG fallbacks for figure-heavy slides
    (CFD contour plots, ramjet schematics, GRI-Mech reaction tables, mechanism
    validation plots, reaction-path diagrams, etc.)

## How to compile

```
pdflatex main.tex
pdflatex main.tex
```

Two passes are needed for the page-counter in the infolines footer to settle.

The preamble uses only stock TeX Live packages: `beamer` (Madrid theme,
seahorse colour theme), `amsmath`, `mathtools`, `bm`, `graphicx`, `booktabs`,
`array`, `xcolor`, `caption`. No custom fonts.

## What was retypeset vs. embedded

About 65 of the 112 slides — every derivation slide from the continuum
assumption through the Navier–Stokes equations, the integral energy
equation, the chemical-kinetics formalism, and the SST k-ω turbulence
model — are typeset natively in LaTeX. Equations use proper math mode and
custom shortcuts (`\Dt`, `\pd{·}{·}`, `\divg`, etc.) defined in the
preamble, so they can be edited and restyled directly.

The remaining ~47 slides (microflow regime plot, atmospheric reentry CFD,
the four GRI-Mech 3.0 reaction-list pages, the CHEMKIN/NASA polynomial
listings, the Shomate equation table, mechanism-validation plots, the two
reaction-path diagrams, the laminar flame speed and NO emission plots, the
ramjet/scramjet schematic, the cavity simulation pressure/Mach/temperature/
OH/velocity contour fields, etc.) reference rendered PNGs of the original
PowerPoint slides under `fig/`. Each is `\includegraphics`-d with a `trim`
that crops away the original PowerPoint title bar and the bottom ITU
footer, so the Beamer frame title and infolines footer take their place
cleanly.

If you later want any of the embedded figure slides retypeset natively
(e.g. redrawing a schematic in TikZ, or reproducing a plot from raw data),
let me know which ones.

## Custom math shortcuts in the preamble

```latex
\newcommand{\dd}{\mathrm{d}}
\newcommand{\D}{\mathrm{D}}
\newcommand{\Dt}{\frac{\D}{\D t}}
\newcommand{\pd}[2]{\frac{\partial #1}{\partial #2}}
\newcommand{\bu}{\mathbf{u}}
\newcommand{\bF}{\mathbf{F}}
\newcommand{\bx}{\mathbf{x}}
\newcommand{\bn}{\mathbf{n}}
\newcommand{\bg}{\mathbf{g}}
\newcommand{\divg}{\nabla\!\cdot}
\newcommand{\Vol}{\mathcal{V}}
```
