---
title: "file system"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-03-21
hi there

i just want to know what the type of file system that ubuntu support ??

ntfs? fat , fat32 , ext2 ,ext3 ?

i know that it support ext 2,3 but what about ntfs and fat ??

---

### Post by taurus on 2007-03-21
Yes, Ubuntu can read ntfs and can read and write to fat32/vfat.  However, you need to use ext3 (default) filesystem when you install Ubuntu.  Don't even think about installing Ubuntu on a fat32 filesystem.

---

### Post by Redache on 2007-03-21
NTFS can only be read from Ubuntu, Fat32 can be read and written to.

If you mean will Ubuntu install onto a Fat 32 partition, I'm not 100% on this but I don't think it's possible due to the way any Linux Kernel works and the filesystems supported.

You can write to NTFS with the NTFS-3G Driver but it's considered experimental/dangerous and isn't to be taken as a simple solution.

---

