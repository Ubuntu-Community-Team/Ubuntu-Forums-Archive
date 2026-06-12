---
title: "trying to combine two seperatly patritioned harddrives"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2008-03-23
Is there any way I can repartition a harddrive to merge two previously seperate partitions? Thanks

---

### Post by RealPSL on 2008-03-23
Vague question. Are you trying to preserve the data and that drive post merge? Are the partitions adjacent? Can we see the output of fdisk -l /dev/sda? Assuming the drive is /dev/sda.

---

### Post by smoker on 2008-03-23
> **woodsonoversoul said:**
> Is there any way I can repartition a harddrive to merge two previously seperate partitions? Thanks

as you should back up any essential data before partitioning operations, just delete both partitions with something like 'gparted', and create one large new partition.

if you have an operating system on one partition you want to keep, then delete the other partition, and enlarge the os partition to take up the vacant space,

best of luck

---

