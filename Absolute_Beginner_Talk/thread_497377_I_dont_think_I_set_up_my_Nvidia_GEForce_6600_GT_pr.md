---
title: "I dont think I set up my Nvidia GEForce 6600 GT properly, Please help"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-07-10
I recently installed 7.04 on my comp and all I have done is gone to system ->administration->restricted drivers and enable nvidia accelerated graphics driver and stopped and restarted the x-server. But it's acting the same as before I did these steps. While I am playing a dvd the cpu usage hangs around 7 - 17% on occasion but as soon as I try to move a window around on the screen it shoots up towards 80 - 90% usage. Even without a dvd playing and I just try to move this window around its going from 0 - 5% to 50% usage. Do I need to edit the Xorg.conf file? or download anything else to set up my graphics card? Thanks

---

### Post by AlexenderReez on 2007-07-10
in terminal

> sudo nvidia-xconfig --add-argb-glx-visuals -d 24

restart

---

