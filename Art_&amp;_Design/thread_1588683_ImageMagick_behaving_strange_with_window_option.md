---
title: "ImageMagick behaving strange with window option?"
date: 2010-10-05
forum: Art &amp; Design
---

### Post by tripmix on 2010-10-05
Could someone explain why this command works perfectly ```
DISPLAY=:0.1 animate -background "#000000" -backdrop -geometry 1000x1000+460-100 anonglobetest2.gif
``` while this ```
DISPLAY=:0.1 animate -background "#000000" -backdrop -window root -geometry 1000x1000+460-100 anonglobetest2.gif
``` sets the background surrounding the image (the root window) to cyan color? 

Another post I read had the same problem but there it defaulted to black (like I want) and they wanted another background color. They fixed it by using xsetbg but that doesn't work for an animation.

---

