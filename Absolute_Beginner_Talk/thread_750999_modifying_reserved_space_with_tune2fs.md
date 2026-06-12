---
title: "modifying reserved space with tune2fs"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by mikespike2 on 2008-04-10
I was trying to removed the reserved space for root on my 2nd hard drive, since it's just for media, etc I don't need reserved space for root.

I tried:
sudo -s
sudo tune2fs -m 1 /dev/sdb

and it says:
tune2fs 1.40.8
tune2fs: Bad magic number in super-block while trying to open /dev/sdb
Couldn't find valid file system superblock.


Any ideas?  Or how should I be doing it?  Not sure I am using the right switches.

---

### Post by ajgreeny on 2008-04-10
I think you may need to use /dev/sdb1 and not just leave it as sdb in the device notation.  Just out of interest try ```
sudo tune2fs -l /dev/sdb
``` and see what happens.  If that doesn't work try sdb1 and see if it helps.

---

