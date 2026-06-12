---
title: "[SOLVED] Printing with Inkscape"
date: 2008-03-29
forum: Art &amp; Design
---

### Post by miggols99 on 2008-03-29
I want to print some thing with Inkscape, but if I print it (or print it to a PDF) things I need like blur and transparency are removed. So I will need to export it as a bitmap. What DPI should I export it to? How can I get it to fit perfectly in the template without having to sacrifice blur and transparency? I need it to be **exact** measurements, and I did this with Inkscape's guidelines, but exporting to a bitmap and printing resulted in a blurry, off the page image...

(By the way, I'm printing out CD labels, inserts and the back of the case)

---

### Post by mcduck on 2008-03-30
> **miggols99 said:**
> I want to print some thing with Inkscape, but if I print it (or print it to a PDF) things I need like blur and transparency are removed. So I will need to export it as a bitmap. What DPI should I export it to? How can I get it to fit perfectly in the template without having to sacrifice blur and transparency? I need it to be **exact** measurements, and I did this with Inkscape's guidelines, but exporting to a bitmap and printing resulted in a blurry, off the page image...

(By the way, I'm printing out CD labels, inserts and the back of the case)

The resolution you need depends on what kind of print you are making. Generally something like 300DPI should be enough for printed material.

For exact measurement you'd better change the document size instead of using the guidelines to crop the image to correct size.

---

### Post by miggols99 on 2008-03-30
But it is printing on an A4 piece of paper. I need it to have guidelines otherwise it won't work...

---

### Post by mcduck on 2008-03-30
There should be no problem printing a smaller image into bigger paper, so even if your document is the size of a CD cover you should be able to print it to A4 ;)

Anyway, the easiest way (that should work, no matter what kind of printer you have ) should be to keep the Inkscape document at correct size, then export the final image to a PNG file with 300DPI resolution. Then import this image into any desktop publishing application, or into OpenOffice to put the image into A4-sized page. Then print it.

Printing straight from SVG probably doesn't work, so you'll need to create a bitmap image. And you need to make that image with high enough resolution. After that getting it printed at correct size is simply a question of having correct printer settings. (no scaling, for example). Actually you should be able to print the CD cover image correctly even without putting it into any a4-sized page.

---

### Post by miggols99 on 2008-03-30
That worked great! In fact, the one with the exact measurements worked as well. All I did was export the whole page at 300 DPI and use OpenOffice to do the rest. Thanks!

---

