---
title: "Gutsy dual monitors + compiz"
date: 2007-11-07
forum: Apple Intel Users
---

### Post by ward83 on 2007-11-07
I'm having some trouble getting dual monitors working in gutsy, using xinerama and compiz. I'm on a 20" Intel iMac, which has a radeon mobility X1600 video card. I can get both monitors working if I uninstall xserver-xgl and disable compiz, or I can get compiz working on only one monitor. If I leave compiz enabled and enable the second monitor, gnome just crashes back to the login screen, no errors or anything. Any ideas?

---

### Post by cyberdork33 on 2007-11-07
[https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes](https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes)

Read the section about multimonitor setups. Xinerama is not supported any longer

---

### Post by luis.alves@lafaspot.com on 2007-12-16
Here is an example
 xrandr --output VGA --mode 1920x1200 --pos 0x0 --output TMDS-1  --mode 1280x720 --pos 0x1200

this a good tutorial 
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

---

### Post by Levo75 on 2007-12-16
Take a picture of the results if you succeed. :D

---

