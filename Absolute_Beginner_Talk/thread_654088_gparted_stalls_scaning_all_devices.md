---
title: "gparted stalls scaning all devices"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by captlogic on 2007-12-30
I've got Gutsy, full install, and I wanted to take a look at my partition scheme.  So I loaded up gparted from the menu and the window opens and hangs at 'scanning all devices' without any result.

If I run gparted from the terminal with sudo gparted I get the following

======================
libparted : 1.7.1
======================
Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.

I'm always having problems with the floppy drive (I don't have one!) and even though it's disabled in the bios the OS (Windows XP included) always installs it.  But I don't think that's the problem.  It's always been this way and I've successfully used gparted before.

I've searched around but not really found anything about this particular problem.
Anybody have any ideas?

I've been using Ubuntu since Fiesty, but I don't know where to start the diagnoses.

Thanks in Advance
CaptLogic

---

### Post by taurus on 2007-12-30
How about just do the old fashion command?

```
sudo fdisk -l
```

---

### Post by jken146 on 2007-12-30
Hmm.  Are you running gparted with gksudo?
```
sudo fdisk -l
``` will display your partitions and ```
df -h
``` will display the amount of space used/left on the mounted ones.

---

