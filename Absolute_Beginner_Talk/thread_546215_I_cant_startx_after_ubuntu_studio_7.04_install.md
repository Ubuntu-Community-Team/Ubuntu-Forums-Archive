---
title: "I cant startx after ubuntu studio 7.04 install"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by sluricanewallace on 2007-09-08
X server crashes after first boot on install.  I was running 6.10 fine previously.  I can't figure out how to reconfigure it?  no xfree86config...

---

### Post by gashcrumb on 2007-09-08
If you're running the low latency kernel try logging into the console and doing:

sudo apt-get install linux-restricted-modules-lowlatency

if you're running the realtime kernel:

sudo apt-get install linux-restricted-modules-realtime

This is assuming that you're running an nvidia card.  You should probably also post the contents of /var/log/Xorg.0.log which will give an idea of what's going wrong if the above commands don't fix anything.

---

### Post by schorsch on 2007-09-08
From the command line try:
```
dpkg-reconfigure -phigh xserver-xorg
```
And the file to edit (after you made a backup of it!) is /etc/X11/xorg.conf.

---

