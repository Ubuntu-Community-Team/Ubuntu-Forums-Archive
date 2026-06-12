---
title: "Condensed fonts are gone"
date: 2007-05-23
forum: Art &amp; Design
---

### Post by bruzzel on 2007-05-23
After upgrading from 6.06 (dapper) to 7.04 in two steps, I find that my Deja Vu Sans Condensed and Serif Condensed fonts have disappeared from the font lists in applications like OpenOffice, Abiword and Firefox. They are still in their font folder though (see below), only I can't access or use them. Has anyone experienced this? Can it be due to errors in the upgrade process?

bruzzel@D02746:~$ ls /usr/share/fonts/truetype/ttf-dejavu/
DejaVuSans-BoldOblique.ttf           DejaVuSans.ttf
DejaVuSans-Bold.ttf                  DejaVuSerif-BoldOblique.ttf
DejaVuSansCondensed-BoldOblique.ttf  DejaVuSerif-Bold.ttf
DejaVuSansCondensed-Bold.ttf         DejaVuSerifCondensed-BoldOblique.ttf
DejaVuSansCondensed-Oblique.ttf      DejaVuSerifCondensed-Bold.ttf
DejaVuSansCondensed.ttf              DejaVuSerifCondensed-Oblique.ttf
DejaVuSans-ExtraLight.ttf            DejaVuSerifCondensed.ttf
DejaVuSansMono-BoldOblique.ttf       DejaVuSerif-Oblique.ttf
DejaVuSansMono-Bold.ttf              DejaVuSerif.ttf
DejaVuSansMono-Oblique.ttf           fonts.dir
DejaVuSansMono.ttf                   fonts.scale
DejaVuSans-Oblique.ttf

---

### Post by Nakkis on 2007-05-23
Yeah, it's a bug. 

[https://bugs.launchpad.net/ubuntu/+bug/93155](https://bugs.launchpad.net/ubuntu/+bug/93155)

---

