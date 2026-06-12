---
title: "boot from floppy but can't get into Ubuntu"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-03-24
I'm trying to make a safety boot floppy that will get me back into Ubuntu if needed. 
I've followed a few instructions on making a boot floppy which worked fine. 
I also copied device.map & menu.lst to the floppy so my Grub menu comes up when I boot from the floppy. The problem is, I just get an error when I hit any of the boot options so the boot floppy is useless.  The same menu.lst & device.map work fine when I boot from the HD to XP or Feisty.
Anyone have any ideas what I'm missing?

---

### Post by garyed on 2008-03-24
Another thing I found is that if I choose the recovery option it will get me to the tty & from there I can do a "gdm restart".  That gets me into the desktop with some"Hal" error but it still solves the problem. Recovery has the same root (1,0) as the normal kernel which doesn't work & doesn't make sense either.

---

### Post by herbster on 2008-03-24
Floppy still exists? ;)

How many floppy disks have you tried, ensuring that isn't a physical issue?

---

### Post by garyed on 2008-03-24
> **herbster said:**
> Floppy still exists? ;)

How many floppy disks have you tried, ensuring that isn't a physical issue?

I just tried one, but it boots fine it's just a matter of getting to the HD through my menu.lst file. 
If I press "e" at the boot screen it shows the same (1,0) for the recovery kernel as it does for the generic kernel. Also (0,0) won't get me into my XP partition either but they both work right if I boot from the HD.

---

