---
title: "Grub boot Cd"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by fake_punk on 2008-03-31
Hello,

I want to know if it is at all possible and how would i go about creating a GRUB boot CD to boot my linux partition (I couldnt install grub to the MBR on my pc as that would kill my T61 recovery options)?  I know it is (hd0,3).

---

### Post by Duck2006 on 2008-03-31
You can try super grub disk.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

For a grub boot cd this may help.

[http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD](http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD)

Any thing on grub you may find this a good read.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by maybeway36 on 2008-03-31
GRUB4DOS can boot from a CD. [https://gna.org/projects/grub4dos/]("https://gna.org/projects/grub4dos/")
GRLDR is the ISO boot sector (for mkisofs).
OR, if you have a floppy drive, you could always just run the live CD and type in a terminal:
```
sudo grub
root (hd0,3)
setup (fd0)
```
Then you get a quick boot floppy.

---

