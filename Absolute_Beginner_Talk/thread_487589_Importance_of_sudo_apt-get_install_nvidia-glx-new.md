---
title: "Importance of sudo apt-get install nvidia-glx-new"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by lazyart on 2007-06-29
Update Manager just notified me of a kernel update.  We all know what this could lead to-  "X server failed to start" when you reboot.

Some time ago I did```
sudo apt-get install nvidia-glx-new
```This handy package then gets updated when the new kernel comes down and ta-da!  No X server issues.

If you use the nvidia driver, be sure to grab that package before you update your kernel.  Just makes things easier for you down the road.

---

### Post by confused57 on 2007-06-29
I just installed nvidia drivers in Feisty  for my GEForce FX5500, using this guide:
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

I  installed  the "nvidia-glx", because the instructions mentioned to install this for my particular card...hope this gets updated when there's a kernel update.  At least I have my /etc/X11/xorg.conf backed up with the "nv" driver, before I installed the nvidia driver.

---

### Post by lazyart on 2007-06-29
Mine is a 5200, so not much difference there.  My card shows up on both lists.  Given a choice, I like new. :)

---

### Post by confused57 on 2007-06-29
> **lazyart said:**
> Mine is a 5200, so not much difference there.  My card shows up on both lists.  Given a choice, I like new. :)
Thanks, mine is also on both lists...missed it the first time(AADD?), new sounds even better.

---

