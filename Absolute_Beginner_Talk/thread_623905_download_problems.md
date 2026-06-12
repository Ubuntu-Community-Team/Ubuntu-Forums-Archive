---
title: "download problems"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by rcdif on 2007-11-26
I am trying to install a dual boot  . When installing I select the manual option my hd is already formatted with two fat 32 and two ex 3 partitions. When selecting the partition for the root I used "/" but I am unable to get the swap partition to be recognized tried all the options in the drop down menu but keep getting the go back and choose a swap partition window. How do you designate a swap partition? Should it be a ex 3? Thanks

---

### Post by Sqwishy on 2007-11-26
A swap partition should be formatted as 'linux-swap' not ext

---

### Post by PeterJS on 2007-11-26
Swap actually has it's own separate format, delete the ext3 partition you're trying to use for swap, and create a new partition, when creating the new partition set it's mount point to swap, and I think the installer should take care of the rest for you.

---

### Post by rcdif on 2007-11-26
Thanks That worked I am now at the ready to install screen a warning says "This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted"
The fallowing partitions are going to be formatted
partition #3 of SCS 1 (000) (sda) as swap
partition #4 of SCS 1 (000) (sds) as ext3

Just want to double check before I install Will this affect my fat 32 ext? Would hate to inadvertently format those partitions.

---

### Post by PeterJS on 2007-11-26
Can't really tell from what you posted if there will be any damage, but if you go back a step it should list what the paritions will look like in their final state, if you see the fat32 partition listed there (and it's not 3 or 4) you should be fine.

---

