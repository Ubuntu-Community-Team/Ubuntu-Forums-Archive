---
title: "resolution"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2007-04-25
my system is rather old but works great. p3 800mhz 512ram with a nvidia nv564 video card
the legacy driver is installed but when it is enabled by the driver manager i am only able to get 800x600 res.
how can i use the driver and get the higher resolutions 1600x1200 as when it is disabled. iam running feisty

---

### Post by lepz on 2007-04-25
open a terminal and type 

gksudo gedit /etc/X11/xorg.conf

go to monitor section and put in your  resolution at the beginning of each mode line. Save and exit. control alt backspace and log back on

---

### Post by abu-fatu on 2007-04-26
my xorg.conf file shows all resolutions 1600x1200 etc... still stuck at 800x600 unless i disable the legacy driver
in the retricted rivers manager.

---

### Post by lepz on 2007-04-26
Have you tried changing it through your nVidia settings?

---

### Post by Art_Redwood on 2007-04-26
Many thanks, I had a problem with my acer 1916w mointer, it only showed 1028*1024, i did what you suggested, now its running beautifully at 1400*900.

you killed two birds with the one stone many thanks, this forum rocks

---

