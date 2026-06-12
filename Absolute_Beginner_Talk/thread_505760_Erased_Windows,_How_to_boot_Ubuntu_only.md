---
title: "Erased Windows, How to boot Ubuntu only?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by rainontin on 2007-07-20
Hi i got some problems with windows this made me to erase it and got into this: [http://ubuntuforums.org/showthread.php?t=505611](http://ubuntuforums.org/showthread.php?t=505611) but now, i just want to boot ubuntu only, but i tried with supergrub and grub only, and says Error 17: Cannot mount selected partition,
How did i restore my old ext3 to boot.
with fdisk this appears:
```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15861   127403451    7  HPFS/NTFS
/dev/sda2           15862       18171    18555075   83  Linux
/dev/sda3           18172       30515    99153180    f  W95 Ext'd (LBA)
/dev/sda5           18172       18428     2064321   82  Linux swap / Solaris
/dev/sda6           18429       30515    97088796    7  HPFS/NTFS

```

---

### Post by AlexenderReez on 2007-07-20
i have similar problem before but this post help me ---->

> [http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+problem](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+problem)

---

