---
title: "Help - newbie has destroyed the gnome-terminal"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by ran_ma on 2007-04-30
Hello All , 

This is my first post here , and I'm also a fresh rockie in ubuntu and linux , so I'm happy there is a place  can ask all sorts of stupid questions like this one... . 

I tried to change the setting of the terminal (the one you open from the accesories menu) and now it crashes when I start it . 
How do I restore he original settings?
I tried reinstalling it from the packet manager but that doesn't help . 
I think I know what I did worng , if I could get the setings menu back I'd fix it but I can't because it doesn't start ! 
the option of the CTRL+ALT+F1 works but I like the terminal emulator. 
Please help ! 


Ran.

---

### Post by jpatton on 2007-04-30
I'm not 100% certain of this, but I would image if you open this location:

.gconf/apps/gnome-terminal/profiles

and delete everything in there except the.xml file, that might fix your problem. Others more knowledgeable than I may wish to chime in as well.

---

### Post by annda on 2007-04-30
are you per chance using nvidia drivers and xinerama? if so, it's an old bug. take a look here:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232)

especially the "AddARGBGLXVisuals" solution at the bottom.

---

### Post by ran_ma on 2007-05-08
No . this doesn't help . 

I don't use nvidia (I have an ATI) graphics card .

---

