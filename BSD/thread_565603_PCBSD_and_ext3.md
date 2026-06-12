---
title: "PCBSD and ext3?"
date: 2007-10-02
forum: BSD
---

### Post by smah77 on 2007-10-02
Does anyone know if the new PCBSD 1.4/FreeBSD 6.2 can have read/write access for ext3 partitions?  I've got read access enabled, and the forums for PCBSD seem to be covering previous versions, but don't look promising...

Other than that problem and some weirdness with my keyboard sometimes locking up during the boot process (and that it uses KDE, and getting used to the package management system), PCBSD 1.4 is pretty awesome - it is fast, stable, comes with the NVIDIA drivers by default and has easy installation of compiz-fusion (and compiz-fusion is way fast on PCBSD for some reason - setting the cube transparent for some reason doesn't slow down my system at all).

---

### Post by Bachstelze on 2007-10-03
FreeBSD (and all the three major BSD-based OSes today, for that matter) have read-write support for ext2, and ext3 is just ext2 with a journaling and a few other minor enhancements.

Thus, your BSD system can read and write to your ext3 without problems but cannot make use of the journaling, which adds a small theoretical risk for data loss, especially after a "hard reboot". However, in several years of putting my BSD home folder on an ext3 partition and countless hard reboots, I've never run into any problem that a good *e2fsck* couldn't fix.

---

### Post by smah77 on 2007-10-03
> **HymnToLife said:**
> FreeBSD (and all the three major BSD-based OSes today, for that matter) have read-write support for ext2, and ext3 is just ext2 with a journaling and a few other minor enhancements.

Thus, your BSD system can read and write to your ext3 without problems but cannot make use of the journaling, which adds a small theoretical risk for data loss, especially after a "hard reboot". However, in several years of putting my BSD home folder on an ext3 partition and countless hard reboots, I've never run into any problem that a good *e2fsck* couldn't fix.

I've read that, and I've read that there's only read support.  When I tried to mount my ext3 drive, though, I got it read only - is there some specific step I needed to take?

---

### Post by Bachstelze on 2007-10-03
> **smah77 said:**
> I've read that, and I've read that there's only read support.  When I tried to mount my ext3 drive, though, I got it read only - is there some specific step I needed to take?

All the BSDs mount ext2/3 read-only by default, so you need to explicitly specify in the mount options that you want it mounted read-write, like :

```
sudo mount -t ext2fs -o rw /dev/something /somewhere
```

---

### Post by smah77 on 2007-10-03
> **HymnToLife said:**
> All the BSDs mount ext2/3 read-only by default, so you need to explicitly specify in the mount options that you want it mounted read-write, like :

```
sudo mount -t ext2fs -o rw /dev/something /somewhere
```

Okay cool, thanks!

---

