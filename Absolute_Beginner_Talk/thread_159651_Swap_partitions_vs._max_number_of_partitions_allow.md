---
title: "Swap partitions vs. max number of partitions allowed"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by BjornHaland on 2006-04-13
***Hi, I'm wondering about a few things relating to partitioning:***
* I want to triple-boot AMD64/32 + Windows.
* I need a FAT32 partition for easy communication between Windows and Linux.

***My challenge is:***
* Only four partitions allowed.
* Triple-booting+Swap drive+FAT32 drive= 5 partitions.

***I am wondering if:***
* I could let go of the swap drive (especially after installing the third OS, I'm at Win+AMD64 atm.)
* I could manually assign a swap drive at a later stage (and how) if I really need it that much.

***I know:***
* That I can share the swap partition between the two Linux partitions.

***A couple of specifications***:
AMD64 3400+
512 MB DDR 133
90 GB 7200 RPM

Any thoughts on this?

---

### Post by taurus on 2006-04-13
You can only have four primaries partitions on one drive but you can have as many extended partitions you want.  So, convert the last primary to logical and use that to create a few more extended partitions.  Then, you don't have to worry about limiting yourself to only four partitions...

---

### Post by BjornHaland on 2006-04-13
Ah, very nice. I take it this means I could assign the extra logical volumes from within the Dapper partitioner?

- I'll try and report back here in case someone does a search once and could use the information.

---

