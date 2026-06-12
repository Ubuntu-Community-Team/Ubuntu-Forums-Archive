---
title: "Hours and hours to resize and partition"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by JerseyDevil1111 on 2008-01-25
Someone should explain to new users that it can take hours and hours to resize and partition a disc for Ubuntu. :mad:

---

### Post by LaRoza on 2008-01-25
It shouldn't.

The exact time it takes depends on several things.

* Size of the disk
* Contents of the partition
* State of the existing file system
* Condition of the hardware

Larger disks take longer.

If one attempts to resize a partition, the partitioning tool (should) move any files in the way to a different part of the partition. If the file system is corrupted, or is greatly fragmented, this can take a while and may lead to data loss. Defrag Windows partitions first several times.

If one attempts to alter the NTFS filesystem of Vista with an older tool, it will do it but will destroy the file system because of the changes of NTFS in that release. Newer tools do not have this problem. (Ubuntu 7.10 and the latest GParted are OK to use)

---

### Post by JerseyDevil1111 on 2008-01-25
But it does.:(

---

### Post by LaRoza on 2008-01-25
> **JerseyDevil1111 said:**
> But it does.:(

The problem you experience is a problem, not what is supposed to happen. Don't assume it happens al the time to everyone.

If you want help with the issue:

* Post what you are using and the version number
* Give the hardware you are using
* Give the outcome of the operations

---

### Post by dcstar on 2008-01-25
> **JerseyDevil1111 said:**
> Someone should explain to new users that it can take hours and hours to resize and partition a disc for Ubuntu. :mad:

Using what?

---

### Post by mivo on 2008-01-25
Well, like LaRoza wrote, it depends on a number of things. It may take ages, but it doesn't necessarily will. Personally, I would always just backup data and re-partition, since that's faster, cleaner and there is no risk of failure.

---

### Post by LaRoza on 2008-01-25
> **mivo said:**
> Well, like LaRoza wrote, it depends on a number of things. It may take ages, but it doesn't necessarily will. Personally, I would always just backup data and re-partition, since that's faster, cleaner and there is no risk of failure.

Resizing Vista and creating partitions and formating them takes about 15 minutes on my end.

---

