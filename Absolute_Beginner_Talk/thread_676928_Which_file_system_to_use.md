---
title: "Which file system to use"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by kudos1uk on 2008-01-24
Hi all, I am just setting up a fresh install on my laptop of dual windows xp & Ubuntu.
 
Which is the best file system to use for Windows in this setup, I got the installation disk in now and don't know if I should go with fat32 or NTFS.
 
Thanks Tony

---

### Post by macogw on 2008-01-24
Windows and Ubuntu 7.10 (Gutsy) can both handle NTFS just fine.  FAT32 is not recommended since it handles permissions poorly (only 32 bits within which to put that information), has limits on file size (no files over 4GB), and has limits on partition size (32GB, I think).  NTFS, however, does need to be defragmented from time to time.  Ext3 doesn't need to be defragmented, but Windows can't, by default, use it.  To make Windows XP able to understand ext3, install the driver from [http://fs-driver.org](http://fs-driver.org)

---

### Post by PmDematagoda on 2008-01-24
NTFS works on Linux but it does have a few problems on Linux whereas FAT32 works much better with Linux. But since NTFS is a better FileSystem than FAT32, I think you should go for NTFS.

---

### Post by kudos1uk on 2008-01-24
Thanks for that, I did not know Ubuntu can now handle NTFS, that was the only reason I was considering fat32.

NTFS it is then. Thanks again.

---

