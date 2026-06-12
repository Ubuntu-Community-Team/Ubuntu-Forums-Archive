---
title: "How to crop a square and make it a circle in GIMP"
date: 2012-02-15
forum: Art &amp; Design
---

### Post by Automat2 on 2012-02-15
Hi,

I've got a problem. I am trying to crop a square image to make it a circle, and using GIMP.

I can't. There always appear a black or white edge on the angles of the square, beyond the limits of the circle.

Is there any way I can get the image edited to a circle?

---

### Post by ofnuts on 2012-02-15
> **Automat2 said:**
> Hi,

I've got a problem. I am trying to crop a square image to make it a circle, and using GIMP.

I can't. There always appear a black or white edge on the angles of the square, beyond the limits of the circle.

Is there any way I can get the image edited to a circle?In the computer graphics world, a circle is a square with transparent corners. So 1) make sure your layer can be transparent: "Layers/Transparency/Add alpha channel" (if it is grayed, you already have the alpha channel) and 2) save your image in a format that supports transparency, such as PNG (JPEG doesn't)

---

### Post by Automat2 on 2012-02-19
Thanks ofnuts,

I tried it and it works. :p

---

