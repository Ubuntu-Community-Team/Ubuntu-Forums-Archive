---
title: "Ubuntu fresh install and partitioning"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by carlyle_ny on 2007-07-25
[SIZE="4"]If one chooses the automatic install of Ubuntu, will it select the optimum partionin sizes for the necessary /, /home, and /swap partitions?  Or should one do this manually?  By the way, when I try to partition manually and try to mount a partition for /swap, I do not have this option.[/SIZE]

---

### Post by FleetAdmiral74 on 2007-07-25
Well if you do automatic it will automatically do the /home for you, although doing manual you can specify a seperate partition for home. I think automatic just uses all the available free space, either that or the whole drive, but it should say which.

Welcome to the Forums!

I prefer manual myself, just leave at least 8gigs for the /, then as much as you want for /home and /swap (you create partitions with those names)

---

### Post by stchman on 2007-07-25
> **carlyle_ny said:**
> If one chooses the automatic install of Ubuntu, will it select the optimum partionin sizes for the necessary /, /home, and /swap partitions?  Or should one do this manually?  By the way, when I try to partition manually and try to mount a partition for /swap, I do not have this option.

I recommend creating a say 20GB partition of free space.  During install tell Ubuntu to use the largest free space and an ext3 partition and swap partition will be created out of the 20GB partition.  Formate the other partitions to say FAT32 or EXT3 so Ubuntu does not see it as free space.

---

