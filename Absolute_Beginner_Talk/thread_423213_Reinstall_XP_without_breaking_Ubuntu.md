---
title: "Reinstall XP without breaking Ubuntu"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-04-25
Is this possible?  I want to reinstall Windows XP, but I don't want it to touch Ubuntu.
(and I still want it to be able to boot into grub on startup)

---

### Post by ImpelGD on 2007-04-25
> **chris062689 said:**
> Is this possible?  I want to reinstall Windows XP, but I don't want it to touch Ubuntu.
(and I still want it to be able to boot into grub on startup)

I don't know if there's a way to install Windows without it touching the Master Boot Record, but if you went ahead as normal you could restore the MBR with [SystemRescueCD]("http://www.sysresccd.org/") (after having backed it up first). Run 'partimage' from the command line after booting with the CD.

---

### Post by annda on 2007-04-25
you can do it. be prepared for windows to erase GRUB (it won't touch ubuntu partitions). so you will have to reinstall it manually using the live CD. it's easy:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by zvacet on 2007-04-25
[http://ubuntuforums.org/showthread.php?t=358183&highlight=reinstall+windows]("http://ubuntuforums.org/showthread.php?t=358183&highlight=reinstall+windows")

---

