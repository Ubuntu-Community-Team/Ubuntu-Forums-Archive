---
title: "Emac and Ubuntu"
date: 2010-01-03
forum: Apple Hardware Users
---

### Post by Trogdor the burninator on 2010-01-03
I've been working on getting an old G4 emac to run ubuntu Dapper.  When I try and run sudo /etc/init.d/gdm restart I get an error and warning that states "Couldn't open RGB_DB ' /usr/share/X11/rgb' (WW) ****INVALID IO ALLOCATION**** b: 0xf0000400 e: 0xf00004ff correcting^G
(EE) end of black range 0xefffffff  < begin 0xf0000000

And so on. 

A little help???

---

### Post by Gen2ly on 2010-01-04
Not sure about '/usr/share/X11/rgb' but I do have a '/usr/share/X11/rgb.txt' which I'm pretty sure that it is what it is talking about.  It belongs to xorg-server-utils-7.5-3 which is probably newer than your version so if there was a bug it might be fixed.  Added file as attachment.

---

