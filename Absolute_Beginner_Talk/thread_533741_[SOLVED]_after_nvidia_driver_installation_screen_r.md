---
title: "[SOLVED] after nvidia driver installation screen remains black!"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Kenobi on 2007-08-24
What can I do?

I enabled desktop effects and Ubuntu Linux 7.04 aked me for the installation CD, which installed the nvidia drivers. After the requested reboot, and after the progress bar, linux boots normally, except for the screen remains black.

What can I do? Or how can I remove that driver?

Thanks alot!

---

### Post by jay4e on 2007-08-24
run 
```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```
and chose nv rather than nvidia  that should reset your drivers to the default nvidia.

then try envy to install the nvida drivers:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Kenobi on 2007-08-24
Thank you soo much!!
My Linux is now booting again. But there is no 3D graphics at all now. How do I "chose nv" again?

---

### Post by jay4e on 2007-08-24
envy should upgrade you to the proprietary nvidia drivers and get your 3d working.  the default nv drivers do not support 3d well if at all.

---

### Post by Hobo Joe on 2007-08-24
> **Kenobi said:**
> Thank you soo much!!
My Linux is now booting again. But there is no 3D graphics at all now. How do I "chose nv" again?

Did you use Envy? If you did, then it's already set to the nVidia drivers.

---

### Post by Kenobi on 2007-08-27
Hi,

you didn't understand my question: I was asking how to reenable "nv" in case I can't run envy.

However, I got envy running and it did everything absolutely beautifully. The only drawback is that there seems to be no way to set up these nvidia drivers without an internet connection. Why can't you just "download the whole bunch" on a stick and install it somewhere? Bad news for some people.

ok but thanks you very much for recommending envy - it did a quite awesome job - can't imagine doing all that by hand *uff*! Tell nvidia they should put that on their main download site!

---

