---
title: "Unallocated space on a brand new built External Hard drive"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-11-28
Hi, I just recently put together a Sata External 2.5" drive.
I can feel the hard drive spinning inside of the drive, but when I plug it into ubuntu to format it,it says that all 80 gigs of it are unallocated and it won't let me format it

and on a side note, I have another 320gb hard drive that works fine, I was wondering what the best file system to format it to is?

---

### Post by master_kernel on 2007-11-28
You have to unmount the HD to be able to format it. Just right click the icon on the desktop (if any) and click unmount. Then go into gParted and format it as fat32 if you want it to be compatible with most computers (Mac, Windows, Linux) or choose ext3 if you primarily use Linux. If I'm wrong, could you attach a screenshot of the error window?

master_kernel

---

