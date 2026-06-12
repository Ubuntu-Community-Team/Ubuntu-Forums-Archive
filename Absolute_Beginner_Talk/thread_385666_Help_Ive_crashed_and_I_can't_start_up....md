---
title: "Help Ive crashed and I can't start up..."
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Swoop-LD on 2007-03-16
OK, I tried to enable my ATI Radeon 9600 to use the dual head /monitor. I reconfigured the xorg.conf file (following a Ubuntu book I got) but now it crashes on boot. (I get the grey/blue Xserver crash screen.):mad: 

I can boot in recovery mode. 
I can boot from a live cd.

I just can't figure out how to get into the /etc/X11/xorg.conf file to restore it the way it was.

If I use the recovery mode I tried $ sudo gedit /etc/x11/xorg.conf
Then I get a "display not found" error. "Use gedit --help"
I use gedit -- help & see that display syntax of --display=DISPLAY.
OK that is clear as mud... and I tried it different ways I thought was correct with no joy. :confused: 

How can get back into the xorg.conf file to restore it?

TIA,

-Swoop

---

### Post by ibanex22 on 2007-03-16
hey swoop,

if you have just edited a few lines, you can do
```
sudo vim /etc/X11/xorg.conf
```
from any command prompt and take them out.

if not and if you have made a backup of your working xorg.conf, you can copy it to /etc/X11/xorg.conf via the command prompt and startx.

if not, look for a swap file (such as xorg.conf~ in /etc/X11/) and copy that to /etc/X11/xorg.conf and startx.

if you have no backups, do
```
sudo dpkg-reconfigure xserver-xorg
```

and go through your settings and see if your xserver works by startx.

sorry if that is a lot of intormation/confusing.  i have broken my x server many times :D let me know if anything works.

-erik

---

