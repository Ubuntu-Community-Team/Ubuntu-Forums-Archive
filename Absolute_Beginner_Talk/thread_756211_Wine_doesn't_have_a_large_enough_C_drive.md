---
title: "Wine doesn't have a large enough C drive"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by astoroth88 on 2008-04-15
I installed wine onto ubuntu, but it seems it only is using 600mb out of the 70gb i have, and i can't install games such as guild wars because they think there is only 600mb to install onto and it's not enough.  I tried searching google but i can't seem to find a guide to increase the size or anything, so does anyone know how to either bypass or actually increase my C drive size for Wine?

---

### Post by astoroth88 on 2008-04-15
Never mind, it seems that ubuntu itself only has 603mb, i don't understand why, i specified 70g for it's partition.

---

### Post by Tatty on 2008-04-15
can you post the output of ```
sudo fdisk -l
```

---

### Post by astoroth88 on 2008-04-16
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4984    40033948+   7  HPFS/NTFS
/dev/sda2            4985       19457   116254372+   5  Extended
/dev/sda5            4985       19080   113226088+  83  Linux
/dev/sda6           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdf: 999 MB, 999817216 bytes
21 heads, 20 sectors/track, 4649 cylinders
Units = cylinders of 420 * 512 = 215040 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        4650      976320    6  FAT16

I wiped my hard drive, dual partitioned and installed the new Ubuntu 8.04 beta today. this is the new output for that command.  It seems I still only have 600megs according to the shortcut on the desktop

---

