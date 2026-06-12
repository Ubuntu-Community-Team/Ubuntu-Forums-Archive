---
title: "Ubuntu 9.04 ppc slow on iBook"
date: 2009-09-14
forum: Apple Hardware Users
---

### Post by rwrouns on 2009-09-14
I have installed Ubuntu 9.04 for ppc on a Mac iBook.  It seems to run slow with System Monitor showing CPU from 50% to 100% with no programs running.  The only process showing any activity is the Gnome-system-monitor.  Are there any tweaks to speed things up?

---

### Post by tgalati4 on 2009-09-14
How much RAM?

---

### Post by rjcalifornia on 2009-09-14
How much RAM?

Tweaks? Use Kubuntu :)

---

### Post by rwrouns on 2009-09-15
It has 384 mb of ram.  The installation was super...everything but the display worked at the beginning, and the display issue was resolved by putting in an xorg.conf used with an earlier version of Ubuntu.  The earlier version, 8.04, seemed even slower, which was one reason I was trying the upgrade.

---

### Post by tgalati4 on 2009-09-15
Is this a G3 or G4 processor and what megahertz?  You need at least 512 MB--1 GB will run comfortably.

What graphics driver are you using?  Most iBooks have some sort of ATI radeon.  If you are running 3D effects then its possible that direct rendering is turned off and compositing/shadowing is being done in software.  This would account for continuous CPU usage.

---

### Post by jml on 2009-09-15
Another suggestion is to turn off all of the "fancy" desktop effects.  Set it to none.  This may speed up the computer.  If you can not ultimately get the speed up to your liking, an alternative would be to remove Ubuntu and install Debian 5.0 for the PPC.  You can configure it with a less resource hungry windows/desktop manager (like XFCE.)Plus at least on Intel platforms, Debian always seemed to be a bit faster on my hardware than Ubuntu.  (No flames, please.  I still run Jaunty and like it a lot.)

Joe

---

### Post by tgalati4 on 2009-09-15
The ibooks have slower memory pathways, slower hard disks, and slower video chips than equivalent powerbooks.  I've run dapper on my 1 GHz powerbook with 1.25 GB of memory.  It ran OK, but a lot of stuff didn't work smoothly.

You might get better mileage by adding RAM (1 GB is good) and putting on Tiger and installing several open source programs that have been compiled/rewritten to work with Tiger.

Or as jml suggested, vanilla Debian for PPC and keeping things light as possible.

---

