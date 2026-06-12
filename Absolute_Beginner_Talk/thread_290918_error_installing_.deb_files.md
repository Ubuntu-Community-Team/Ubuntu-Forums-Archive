---
title: "error installing .deb files"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by T-AA on 2006-11-01
when i try to install with konsole


>                 :~$ sudo dpkg -i mandvd_2.2-1_i386.deb
dpkg: fout bij afhandelen van mandvd_2.2-1_i386.deb (--install):
 kon archief niet benaderen: Onbekend bestand of map
Fouten gevonden tijdens behandelen van:
 mandvd_2.2-1_i386.deb


and when i use ark it sais something about a program ar but can't find that in the rep

thx in advance

---

### Post by David Corrales on 2006-11-01
Translate your error to get more help. ar? I think you're talking about RAR compression. The package is called unrar (be sure to enable all repositories).

---

### Post by T-AA on 2006-11-01
it sais support progam ar is not found in path

---

### Post by DirtDawg on 2006-11-01
It says on this [download page]("http://kde-apps.org/content/show.php?content=38347") you need these dependancies. Are you sure you have them all?
```
DVD Slideshow >= 0.7.5
mencoder
mplayer
MKISOFS >= 2.01
xine > 0.99.4
lame >= 3.97
dvdauthor >= 0.6.11
mjpegtools >= 1.8.0
netpbm >= 10.29
ImagMagick >= 6.2.4
transcode >= 1.0.2
dvd+rw-tools >= 5.21.4
```

---

### Post by T-AA on 2006-11-01
well i got man dvd runnig but not outta the .deb needed to download the tar

---

### Post by DirtDawg on 2006-11-01
> **T-AA said:**
> well i got man dvd runnig but not outta the .deb needed to download the tar

Nice work. Usually compiling is way more complicated. Too bad that deb isn't too hot.

---

