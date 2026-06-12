---
title: "New Monitor Not Working Correctly"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Tachions on 2008-01-29
Hey guys I just bought a brand new Samsung 24 inch monitor for my linux box, and yes i did check it works b4 i connected it to my linux comp, but my question is.... my monitor is not correctly displaying the proper resolution with my linux machine, only showing 1280 x 1080 i think, when i can get my 1900x1200 resolution easy. 

Yes my vidcard supports the resolution, but linux is not recognizing my monitor. I checked the display settings and my monitor is not there. my old monitor was but not this new 1....


any ideas, thanks a lot

---

### Post by benfindlay on 2008-01-29
Try typing ```
sudo dpkg-reconfigure xserver-xorg
``` into terminal and following the instructions through.

When you get to an option asking for simple, medium and advanced, choose medium and it will allow you to choose the range of resolutions you want available, as well as setting a preferred one

Hope this helps!

---

### Post by bcrom on 2008-01-29
Hey, I had this problem with my LG 24-inch.  I had to use nvidia-settings to get it to work.

---

### Post by Tachions on 2008-01-29
hey bcrom what do you mean you had to use nvidia settings???

---

### Post by bcrom on 2008-01-29
If you have an Nvidia card, then open a terminal and type ```
sudo apt-get install nvidia-settings
``` then type ```
 nvidia-settings
```  You may have to reboot after you install it and reboot again after you choose your settings.

---

### Post by bcrom on 2008-01-29
actually, try typing ```
nvidia-settings
``` into terminal first, then install them if you don't have them.  You might have the interface already but it interacts with different drivers.

---

### Post by Tachions on 2008-02-04
bump

---

