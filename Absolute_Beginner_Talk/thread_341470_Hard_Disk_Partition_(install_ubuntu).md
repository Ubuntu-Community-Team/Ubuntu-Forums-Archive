---
title: "Hard Disk Partition (install ubuntu)"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by eschmidt90 on 2007-01-18
Is there a way for me to partition my hard drive to install ubuntu, without erasing the bit of the disk that has my mac OS X stuff on it?

Also, my airport card, (Apple Airport Extreme, it comes built into the iBook G4) does not appear to be supported, is there a way for me to gain support, like, is there a driver I can install?

TIA

-Erik

---

### Post by xopher on 2007-01-18
Yes, just boot-up the LiveCD, and do a manual partitioning, leaving your Mac OS X partition intact. It'll probably show up as 'HSF+' or something, which is the filesystem OS X uses. And for the wifi card; you can probably get it running with ndiswrapper, search the forums for more information.

---

### Post by zerhacke on 2007-01-18
ndiswrapper only works for Windows based network cards.

---

