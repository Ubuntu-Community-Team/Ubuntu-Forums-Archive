---
title: "&quot;hdc: drive  not ready for command&quot;"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Shortspan on 2007-01-03
I'm new to Linux.  I just received a copy of Live/install Ubuntu 6.10 on DVD.  When I attempted to use the DVD as a live OP/SYS the DVD loaded but would hang and opened a window with the last line stating:  [I]some numbers[I] and " hdc: drive  not ready for command."  After looking over other peoples issues here I found that the bios does not recognize the DVD, itself, as a boot option.  The CDRW is the master and the DVD is the slave.  The DVD is listed in bios as a slave but it is not in the boot sequence (only the FLoppy, CDRW, and HD0).   Can Ubuntu be loaded onto this machine without too much hassle?  And, I know NOTHING about Linux.  I do not really need Linux, I just wanted to see if I would like it so I bought the live option version.  
AMD XP1800, MSI K7t266 Pro2, LiteOn DVD, TDK CDRW, 512MB Crucial

---

### Post by bodhi.zazen on 2007-01-03
Swap your CD and DVD drives. You will need to change the jumper on the back of the drives such that the DVD is master and the CD is slave.

---

### Post by Shortspan on 2007-01-03
Thanks.  I'll give it a shot.

---

### Post by Shortspan on 2007-01-03
It worked.  By making the DVD the master drive it took and loaded the live version of Ubuntu.  It won't recognize the CDRW now, but so be it.  This brand of Pheonix Bios only has boot recognition for floppy, CDROM and HD.   If I want to get serious about Linux I need an updated machine.

Thanks again.

---

### Post by vadania on 2007-09-02
> **Shortspan said:**
>   If I want to get serious about Linux I need an updated machine.  Thanks again.

I heard Ubuntu runs ok  on old machines like PIII 533 Mhz (slower, but still usable).

---

