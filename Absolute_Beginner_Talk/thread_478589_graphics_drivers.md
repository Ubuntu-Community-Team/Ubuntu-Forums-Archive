---
title: "graphics drivers"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by jeff00z28 on 2007-06-19
someone installed some graphics drivers on a computer running kubuntu which did not work. Is there a way to like enter something like safemode and do something similar to rolling back the driver? Thanks.

---

### Post by Sparkster185 on 2007-06-19
You need to make sure you back up your /etc/X11/xorg.conf file before you make significant (changing drivers, for example) changes.  I always copy mine to my home directory with a .OLD extension (xorg.conf.OLD).

What graphics card do you have?  There are numerous posts here about how to install nVidia/ATI drivers.  Either way, I would use Envy.  It downloads the restricted drivers for you and configures all the files automatically.  Worked great for me on my desktop with an NVidia GeForce 5200 series.

---

