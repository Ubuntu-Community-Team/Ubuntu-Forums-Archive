---
title: "GParted Crashed"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-08-03
Gnome crashed while I was using Gparted to resize a partition on a storage drive.  I walked away and came back a few hours later in the hopes that Gparted would finish its work even if the screen was frozen.  I then did ctrl+alt+backspace to restart x.  I then rebooted the computer.  Everything seems to be workign on the drive (files are accessible).  Gparted also shows that the partition is as it should be.  However, I don't want trouble down the road.  What test utilities should/can I run to check the integrity of this partition?

---

### Post by Inxsible on 2007-08-03
Boot up with a Livd CD. Open a terminal and run

```
fsck
```

---

### Post by l951b951 on 2007-08-21
> **Inxsible said:**
> Boot up with a Livd CD. Open a terminal and run

```
fsck
```

OK, this is a toy computer, so work got in the way of me exploring this issue.  After running fsck on the offending drive, HDD, my results were:

> check aborted.
e2fsck 1.38 (30-Jun-2005)
/dev/hdd1: clean, 8975/17596416 files, 13077995/35164269 blocks
e2fsck 1.38 (30-Jun-2005)


I can only assume that means good news, right?

---

