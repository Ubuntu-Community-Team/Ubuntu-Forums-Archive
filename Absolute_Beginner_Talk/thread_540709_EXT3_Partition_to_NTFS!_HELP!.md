---
title: "EXT3 Partition to NTFS! HELP!"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by deucalion on 2007-09-01
So i have a laptop with 2 partitions. One is my Gibbon, the other is now empty (was feisty). both are EXT3. I need to get one of these partitions (the blano one) formatted from EXT3 to NTFS so that i can put Tablet PC back onto my tablet. I need it for school. i dont know how to format and i cant find a usable bootable partition editor.

---

### Post by Freddie.Ruddick on 2007-09-01
What you need to do is use a partition editor to delete the empty partition and create an NTFS partition of the same size. The easiest way to do this is with the [gParted LiveCD](http://gparted.sourceforge.net/livecd.php). Be aware, when you install windows, it will probably overwrite GRUB (The Ubuntu Bootloader) with a windows bootloader, so you will be unable to boot into ubuntu unless you install GRUB again (Windows Bootloader assumes that you only have windows installed, GRUB can handle booting from Linux AND Windows, and will give you a menu to choose one)

---

