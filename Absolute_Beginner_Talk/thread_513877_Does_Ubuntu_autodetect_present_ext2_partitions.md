---
title: "Does Ubuntu autodetect present ext2 partitions?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Lolicon on 2007-07-31
Just what my questions says...
Does Ubuntu autodetect present ext2 partitions, and if so does it enable writing to them by default? I had quite a few problems with LinuxMint on that note. Thanks

---

### Post by aquavitae on 2007-07-31
It depends exactly what you mean by autodetect.  It can read and write them, yes, and depending on your setup it may automatically mount them.  In general though, if the partition is on a hard drive, you have to manually mount it.  Your systemn should, however, automatically create a device node for it (e.g. /dev/hdb1).  Regarding the read/write, if will only allow writing if it has been mounted for read write, and if the user permissions allow it.  This is all really easy to set up, so if you can let us know exactly what you want to do we can probably help more.

---

### Post by Lolicon on 2007-07-31
Ah excelent. Thank you very much.

---

