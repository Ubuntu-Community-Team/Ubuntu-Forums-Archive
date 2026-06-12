---
title: "changing bootsplash"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by pavel_kbc on 2006-12-18
hello i want to change my bootsplash... please tell me the tips and trick

( i use gfx grub so please dont tell me to use DUM)

---

### Post by pavel_kbc on 2006-12-19
anyone ?

---

### Post by boralyl on 2006-12-19
There are several different options if you look in your system settings -> Splash Screen...not sure if this is what you are looking for or not.

---

### Post by unarmedninja on 2006-12-19
are you trying to get a background image on grub? if so then just add this line to your menu.lst file
```
splashimage (hd0,0)/grub/images/debian_cooleye-dither.xpm.gz
```
where (hd0,0) is your boot partition and the image is in a xpm.gz format.
you can check this site out for more details:
[http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)

---

