# torchvision · Transform Explorer

> **Live demo:** [https://sinadunk23.github.io/torchvision_explorer/](https://sinadunk23.github.io/torchvision_explorer/)

An interactive visual reference for `torchvision.transforms` — see exactly what each transform does and how parameter changes affect your images, before writing a single line of training code.

![screenshot placeholder](https://via.placeholder.com/900x400/0e1117/00e5b0?text=torchvision+Transform+Explorer)

---

## Features

- **17 transforms** visualized in a live grid: Geometric, Color, Blur/Sharpen, Crop/Erase, Normalize
- **Real-time sliders & selects** — tweak every parameter and see the canvas update instantly
- **Upload your own image** — replace the built-in scene with any photo from your disk
- **Hold SPACE on a card** — compare the transformed result against the original
- **Copy Python** button on every card — copies the exact `torchvision.transforms` snippet with your current parameter values
- **Category filter** — focus on just Geometric, Color, Blur, Crop, or Normalize transforms
- Zero server / zero dependencies — pure HTML + Canvas API, works offline

---

## Transforms Included

| Category | Transforms |
|---|---|
| Geometric | `RandomHorizontalFlip`, `RandomVerticalFlip`, `RandomRotation`, `RandomAffine` |
| Crop & Erase | `CenterCrop`, `Pad`, `RandomErasing` |
| Color | `ColorJitter`, `Grayscale`, `Solarize`, `Posterize`, `Invert` |
| Blur & Sharpen | `GaussianBlur`, `RandomAdjustSharpness` |
| Normalize | `AutoContrast`, `Equalize`, `Normalize` |

---

## Deploy to GitHub Pages

1. Fork or clone this repo
2. Go to **Settings → Pages**
3. Set source to **Deploy from a branch**, branch `main`, folder `/ (root)`
4. Visit `https://<your-username>.github.io/<repo-name>/`

That's it — `index.html` is fully self-contained.

---

## Local development

No build step needed:

```bash
# Any static server works
python -m http.server 8080
# or
npx serve .
```

Then open `http://localhost:8080`.

---

## Notes

- Transforms are **simulated in JavaScript** using Canvas 2D — they closely match torchvision behavior but are not pixel-perfect (especially `Normalize`, which maps into `[0,255]` for visibility rather than staying in float space).
- The "Copy Python" snippets use `torchvision.transforms` v2 API style.
- CORS-safe: the built-in scene is drawn entirely on `<canvas>`, and uploaded images come from `FileReader` — `getImageData` works without any server headers.

---

## Contributing

PRs welcome for additional transforms or accuracy improvements. The transform list is in the `TRANSFORMS` array near the top of `index.html`.
