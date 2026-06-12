---
title: "External HD not recognized"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by FonqueJumang on 2006-11-12
I'm using 6.10 for the past few weeks. Had an external Iomega hooked up and all was fine. Was changing themes and all of a sudden desktop HD icon is gone. After a disconnect and reboot same thing. Thinking the HD may be dying I connected a Maxtor One Touch only to get the same results. Nada. All suggestions appreciated. These drives contain all my Tucky Buzzard, SRV, und Megadeth. Okay Nickel Creek too. If you know who these people are... you know how desperate I am.

---

### Post by joshsherman on 2006-11-14
I'd do a `dmesg` to see if the drive(s) are being recognized while booting.  You may also want to check the mount points (under /media).  Perhaps the drives are there and being mounted, but Gnome isn't adding the icons to the desktop (or are you in KDE?)

-j

---

