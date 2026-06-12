---
title: "Install failed"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by mb_8466 on 2008-02-22
V.7.10 failed at step 4. The partitioner either did not load or failed to detect the two installed Seagates in the system. The dialog remained blank.
Downloaded and burned an ISO image to CD.
Thoughts?

---

### Post by Linux_Man on 2008-02-22
How are your HDs connected?

---

### Post by mb_8466 on 2008-02-22
Both are PATA on the MB controller.
HP Vectra VL 420

---

### Post by mb_8466 on 2008-02-25
Gave this a little thought. Blew the partition away with FDisk.
     Ubuntu STILL could not see it (nekkid drive). Rebooted.

Partitioned with FDISK. Rebooted.
     Ubuntu still unable to detect the drive

Formatted the drive FAT32. Rebooted.
     Ubuntu STILL unable to see the drive

This is not a cosmic config. It's a CPQ EVO D510 with an IDE (PATA) motherboard controller. The disk is a Seagate 160 GB. 

Win98 boot disk (w/FDISK and FORMAT) sees and manipulates the drive just fine. CHKDSK sees it and reports correctly on it. Windows installer CD has no problems at all with it. But Ubuntu partitioner cannot see the drive.

Conclusion: Ununtu (and linux in general) still not ready for prime time. That's a shame. I have no love for MS.

---

