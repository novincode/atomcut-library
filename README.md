# atomcut-library

The content behind AtomCut's Library — sounds today, presets and visuals next.

**Git is the source of truth. R2 only serves it.** Everything mechanical about a
file (duration, waveform peaks, the detected hit point, hash, byte size) is
DERIVED at build time and never committed by hand. The only hand-edited file is
each pack's `pack.json`, and it carries editorial facts alone.

    packs/<id>/pack.json      the one hand-edited file
    packs/<id>/audio/*.wav    the bytes
    dist/                     generated — do not commit

## Publishing

From the AtomCut repo:

    pnpm library:build     # decode, analyse, hash → dist/
    pnpm library:publish   # blobs first, manifests last

`library:build` fails the build if a file is undecodable or over budget, so a
broken pack never reaches the catalogue.

## Adding a pack

Create `packs/<id>/`, write `pack.json`, drop the files in, run the build.
A pack is homogeneous — one `kind` per pack, because a mixed pack is two packs
wearing one name.

## Licence

The seed packs are CC0-1.0, synthesized from DSP in
`scripts/library/seed.mjs` in the app repo. Anything added here must declare
its own `license` and `attribution` in `pack.json`.
