---
title: "general video lag"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by chick3n on 2007-04-09
When using firefox and browsing websites, or watching videos it is a little laggy in comparison to windows xp.

I can of course live with it, but i wanna know how do i know if my video drivers are set up and running properly? How do i know i have the latest drivers installed?

My video card is a NV34 [GeForce FX 5200] which is listed in the Device Manager.

---

### Post by overdrank on 2007-04-09
> **chick3n said:**
> When using firefox and browsing websites, or watching videos it is a little laggy in comparison to windows xp.

I can of course live with it, but i wanna know how do i know if my video drivers are set up and running properly? How do i know i have the latest drivers installed?

My video card is a NV34 [GeForce FX 5200] which is listed in the Device Manager.

Hi you can use one of two ways. one is _* lsmod*_ in the terminal and look at the drivers being used or
 Two  *_gksudo gedit /etc/X11/xorg.conf_* in the terminal and view the device drivers there.
Hope this helps good luck!

---

