---
title: "? on fstab and fsck"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-02-14
Should fsck be run on FAT32 partitions?

The reason I ask is, I found a 1gb file with the extension .rec, IIRC, on a fat32 drive. Apparently, this was created when fsck check the partition. Fortunately, nothing of value was in it. However, I question letting Linux check the Windows file system.  

Looking at my fstab, I see that all the vfat partition entries end with "1" (save one I edited previously). If I understand the man page on fsck and fstab, the "1" sets the drive to be checked with fsck. Should these be changes to "0"?

---

### Post by housam on 2007-02-14
Yes, if you change it to " 0 " , It'll not be checked by fsck.

---

### Post by Patrick K on 2007-02-14
is it best to not allow fsck to check vfat partitions?

---

### Post by housam on 2007-02-14
Unless you have a problem in the partition.

---

