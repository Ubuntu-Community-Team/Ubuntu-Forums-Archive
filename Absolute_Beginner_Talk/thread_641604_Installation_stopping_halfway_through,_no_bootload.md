---
title: "Installation stopping halfway through, no bootloader"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Betamaxx on 2007-12-15
Hi everybody- unfortunately I've had a number of problems with setting up my system for dual booting.

[LIST=1]
[*]partitions:
i've had to use the sysrescd to sucessfullly shrink my windows partition, but even after i did that, the partitions are showing up as different sizes in the sysrescd and the installer
[*]bootloader:
does not load when i try to boot from the hdd.
i can't even post; if i try to it asks me to flash the bios.
[*]installer:
this might be the root of my problems- at around 52%, (1.1 GB in my linux partition) through installing, it just closes itsself.  when this happens a /target file manager appears on the desktop.  after this happens, i have to start up the sysrescd utility again to delete the faulty linux partitions and start over
[/LIST]

anybody got any ideas what the problem might be with this?

---

### Post by jken146 on 2007-12-15
Do an integrity check on the CD (it's one of the options on the first screen you see).  If it fails, try re-downloading the iso and burning it at the slowest speed you can.

---

### Post by Sef on 2007-12-15
1) What Windows do you have?  XP, Vista, other?

2) Did you defrag at least twice before install?

---

