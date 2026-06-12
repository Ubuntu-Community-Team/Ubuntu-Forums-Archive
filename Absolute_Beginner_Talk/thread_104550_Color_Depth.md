---
title: "Color Depth"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Brainless on 2005-12-16
How do I reduce the color depth? :confused:

---

### Post by Gustav on 2005-12-16
In the file /etc/X11/xorg.conf there is a value called DefaultDepth in the "Screen" section.

Open xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```
Change the line that sais "    DefaultDepth     24" to "     DefaultDepth     16" (or the depth you want) 
save and exit

---

### Post by roblinux on 2007-09-03
> **Gustav said:**
> In the file /etc/X11/xorg.conf there is a value called DefaultDepth in the "Screen" section.

Open xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```
Change the line that sais "    DefaultDepth     24" to "     DefaultDepth     16" (or the depth you want) 
save and exit

Thanks for that info. I now have direct rendering=YES instead of NO by going from 24 to 16.

In other words....3D in now working !! Useful for Pinball and Foobillards(why did they spell that wrong?)

I don't see any difference in picture quality !!

Rob

---

