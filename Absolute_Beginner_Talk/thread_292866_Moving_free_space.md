---
title: "Moving free space"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-11-04
I have been trying to move some of the 57.75 gigs of free space on my computer over to Linux.  I use Gnome partition editor.  For some reason, it wont let me do it.  Why do they even give you the option?

---

### Post by Kateikyoushi on 2006-11-04
It depends where is the free space which you want to move.
Could you post the output of this ?

```
sudo fdisk -l
```

---

### Post by CatKiller on 2006-11-04
> **OptimusPrime said:**
> I have been trying to move some of the 57.75 gigs of free space on my computer over to Linux.  I use Gnome partition editor.  For some reason, it wont let me do it.  Why do they even give you the option?

It depends on the filesystem you're trying to play with. The latest version, which you can use with the [GParted live cd]("http://gparted.sourceforge.net/livecd.php"), has full move support.

---

### Post by OptimusPrime on 2006-11-04
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            7546       12161    37078020    f  W95 Ext'd (LBA)
/dev/hda2   *           1           6       48163+   b  W95 FAT32
/dev/hda5            7546        8301     6072538+  83  Linux
/dev/hda6            8302        8365      514048+  82  Linux swap / Solaris
/dev/hda7            8366       12161    30491338+  83  Linux

Partition table entries are not in disk order

---

### Post by OptimusPrime on 2006-11-04
> **CatKiller said:**
> It depends on the filesystem you're trying to play with. The latest version, which you can use with the [GParted live cd]("http://gparted.sourceforge.net/livecd.php"), has full move support.

I just don't want to move the space if it is going to mess up anything.  By the way, I was wondering what type of partition a linux 32 would go on.  Also, Windows XP home.

---

