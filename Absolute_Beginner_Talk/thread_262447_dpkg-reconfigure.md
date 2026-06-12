---
title: "dpkg-reconfigure"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by mistywindow on 2006-09-21
I've just installed ubuntu 6.06 64bit server on my PC. Installed on an unformatted 120GB IDE drive.
During initial boot it halts on the command line.
I've tried entering dpkg-reconfigure xserver-xorg.
I get a message to the effect that xserver-xorg is not installed.

When booting initially, grub does not load. I installed Acronis OS Selector which picked up Linux and grub runs after selecting Linux in the Selector.

Grub was loaded on the windows boot disc (SATA).

I've wiped the whole installation and reinstalled with the same result.

Help!

System:
AMD Athlon 64bit 3200 CPU
2 x SATA 250GB NTFS drives
1 x 120GB IDE drive (configured automatically during ubuntu installation)
512MB NVidea graphics card.
2GB RAM

---

### Post by linear on 2006-09-21
I think the server install doesn't supply a gui. You can add it via apt-get.

---

### Post by chuckyp on 2006-09-21
Exactly a server install does not install xserver-xorg.  It sounds like you want a gui interface in which case your best bet is apt-get install ubuntu-desktop

---

### Post by mistywindow on 2006-09-21
Thanks people. I misunderstood the differences between images. I assumed that the Desktop download didn't permanently install ubuntu.

---

