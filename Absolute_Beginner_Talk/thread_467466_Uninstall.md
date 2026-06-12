---
title: "Uninstall"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by kevintp on 2007-06-07
How do you uninstall ubuntu with a dual windows xp pro boot. I have not installed it yet but would like to know going in before I do?

---

### Post by dstew on 2007-06-07
Usually, when you install Ubuntu, you shrink your XP partition to make room for Ubuntu, then create new partitions out of the new unallocated disk space, and install Ubuntu there. When Ubuntu installs, it puts its own boot loader named grub (Grand Unified Boot Loader) into the Master Boot Record of the disk, so you can boot either Windows or Ubuntu. Grub has to be used because the Windows boot loader can only boot Windows.

To uninstall Ubuntu, you just delete the partitions that you created earlier. Then, use the Windows Recovery console (on the Windows installation CD) to re-install the Windows boot loader, by using the **fixmbr** command. Finally, you can grow the XP partition to take up the space you freed up when you deleted the Ubuntu partitions.

The best tool for manipulating partitions is GParted (Gnome Partition Editor). It is on the Ubuntu LiveCD. You can also get a [Live CD that has GParted only]("http://gparted.sourceforge.net/livecd.php"), which is nice and small.

---

