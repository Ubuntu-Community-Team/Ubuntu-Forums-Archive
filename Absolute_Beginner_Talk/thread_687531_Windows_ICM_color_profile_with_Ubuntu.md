---
title: "Windows ICM color profile with Ubuntu?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by maduranga on 2008-02-04
Hello. I'm using a LCD monitor with manually calibrated color profile in windows. Default colors of the monitor I use isn't good.

 Is it possiable to use the *.icm color profile with ubuntu too? 

sorry for tha bad english

---

### Post by rax_m on 2008-02-06
Hi there, 

I believe that it is possible to use the colour profile, the only difference is in Ubuntu you need to apply it to each application that you want to use the profile. 

I haven't really tried it myself unfortunately, so this might be a good read:

[http://en.wikipedia.org/wiki/Linux_color_management](http://en.wikipedia.org/wiki/Linux_color_management)
especially this bit : 

> Color-managed applications

In ICC-aware applications, it is important to make sure the correct profiles are assigned to devices, mainly to the monitor and the printer. Linux applications are currently unable to automatically detect display profiles, so the profiles must be applied manually in each program.

Although there is no designated place to store device profiles on Linux, /usr/share/color/icc/ has become a de facto standard, used by several applications.

Most applications running under WINE have not been fully tested for color accuracy. While 8-bpp programs can have some color resolution difficulties due to depth conversion errors, colors in higher-depth applications should be accurate, as long as those programs perform their gamut conversions based on the same monitor profile as that used for loading the LUT. The corresponding LUT adjustments do need to be loaded though.

---

