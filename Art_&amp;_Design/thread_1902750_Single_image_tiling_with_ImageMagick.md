---
title: "Single image tiling with ImageMagick"
date: 2011-12-31
forum: Art &amp; Design
---

### Post by shantiq on 2011-12-31
tried this   to make a Screensaver with a tiled single image
convinced there is a quicker more efficient route with ImageMagick;   also the final size does not match my request.....



here is the image in question


[IMG]http://img836.imageshack.us/img836/8471/aguilapretopeq.png[/IMG]


TILING

> convert file.png file.png file.png file.png file.png  -append  file44.png  &&  
convert file44.png file44.png file44.png file44.png file44.png   +append -geometry  1920x1200   filefinal24.png

---

### Post by shantiq on 2011-12-31
ok got the trick to force size


> convert file.png file.png file.png file.png file.png  -append  file44.png  &&  
convert file44.png file44.png file44.png file44.png file44.png   +append -geometry  1920x1200**[COLOR="DarkRed"]\![/COLOR]**   
 filefinal24.png 



but still need help on simplifying:KS

---

### Post by ofnuts on 2011-12-31
> **shantiq said:**
> ok got the trick to force size

but still need help on simplifying:KS
Try another IM Tool: combine with -tile option.

---

