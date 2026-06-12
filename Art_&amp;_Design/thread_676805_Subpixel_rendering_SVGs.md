---
title: "Subpixel rendering SVGs?"
date: 2008-01-24
forum: Art &amp; Design
---

### Post by Schalken on 2008-01-24
SVGs are by default resterized is Inkscape with full anti aliasing, but is there a way to have them subpixel rendered as well?

---

### Post by hugmenot on 2008-01-26
Theoretically this is possible, but they have to move their rendering to Cairo first. Currently they have a custom renderer.
The thing is, where is your SVG rendered? If you generate a PNG, then maybe in the future, but if the SVG is published it always depends on the renderer in the viewer.

---

