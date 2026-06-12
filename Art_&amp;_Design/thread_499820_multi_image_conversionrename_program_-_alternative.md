---
title: "multi image conversion/rename program - alternative for Irfran view ?"
date: 2007-07-13
forum: Art &amp; Design
---

### Post by digitalis_vulgaris on 2007-07-13
I'm profesional software designer and I'm making transition from Windows to Ubuntu. I have two major problem:

1. When making animations and animated buttons, I work with image sequence - large numbers of pictures which I need to convert or rename in number listed sequence. In Windows I use Irfran's batch conversion option for this job. What is alternative for this tool in Linux ?

2. When making catalogs and posters, I need to work with photos in CMYK mode. In Windows I use Photoshop. I can't find good alternative.

---

### Post by yabbadabbadont on 2007-07-13
1) You could call imagemagick from a shell script to process them in the correct order.

2) Cinepaint supports CMYK (I think).  I know it supports 16bit images unlike Gimp.  I believe there are CMYK plugins available for Gimp, but it may be that they are not good enough for your purposes.  (You didn't list what you have tried)

---

### Post by digitalis_vulgaris on 2007-07-13
Yes, I know for Gimp plugin, but it isn't good solution. I tried Krita - program have CMYK color mod but don't have color mixer in CMYK.

I will try imagemagic, thanks...

---

### Post by digitalis_vulgaris on 2007-07-13
I tried ImageMagick. It's very powerfull tool, but not very much user frendly. I found couple articles about developing new GUI for this aplication. There is a way to lunch his GUI with **sudo display *ls***, but in this way user can't do with sequence of pictures. Looks like to me that linux still have no match for Irfan's batch conversion tool.

---

### Post by digitalis_vulgaris on 2007-07-13
I just tested Cinepaint. Noup... no CMYK...

Heeeeelp!?

---

### Post by digitalis_vulgaris on 2007-07-13
I found good solution for my problem - **gthumb 2.10.** This program can easy rename and convert images. Still I have no solution for photo editor in CMYK mode...

---

### Post by stani on 2007-07-14
> **digitalis_vulgaris said:**
> Still I have no solution for photo editor in CMYK mode...I have read in the past that Krita has CMYK support, but it is of course a KDE application.

[http://www.koffice.org/krita/](http://www.koffice.org/krita/)

---

### Post by Hairy_Palms on 2007-07-15
well if you cant find anything else, you can always run a version of photoshop under wine, 7.0 runs perfect and CS2 portable edition runs fine.

---

### Post by digitalis_vulgaris on 2007-07-15
Thanks. Something like that was on my mine too. It's my plan B... But I still looking for alternative...

---

### Post by Martje_001 on 2007-07-17
You can use 'bulk rename' included with the thunar package (sudo aptitude install thunar).

---

