---
title: "mdadm question..."
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by ehourigan on 2008-01-26
I have a quick question:
I have a 3 disk RAID5 array using mdadm
I wanted to add 2 new disks, so I ran
mdadm --add /dev/md0 /dev/sdd
mdadm --add /dev/md0 /dev/sde
mdadm --grow --raid-devices=5

I forgot about the partitions, sdd1 and sde1, I'm wondering if this is going to be a problem, or if sdd and sde will work?
It is currently reshaping the array.  Please advise if possible.
A response would be much appreciated!
Thanks,
Ed Hourigan

---

### Post by ehourigan on 2008-01-26
i decided to remove the drives one at a time, re-format them, and then re-add them with the partition. However, I would like to know what would have happened, if I  had stayed with just sdd and sde. 
Here's what I did incase anyone would like to know:
mdadm -f /dev/md0 /dev/sdd
mdadm --remove /dev/md0 /dev/sdd
mdadm --zero-superblock /dev/sdd
mdadm --add /dev/md0 /dev/sdd1

then repeated the same for sde.

---

