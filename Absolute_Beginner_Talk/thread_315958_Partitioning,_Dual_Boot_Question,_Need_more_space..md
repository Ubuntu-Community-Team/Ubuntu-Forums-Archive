---
title: "Partitioning, Dual Boot Question, Need more space."
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by tempest152 on 2006-12-10
I installed Ubuntu 5.10 Breezy on a slave drive, with Lilo loading off the master drive which XP is installed.

My scenario is, I have ran out of space on the Ubuntu loaded drive, which ext3 formatted, I want to resize the XP NTFS partition on the master so that I can have some extra space for Ubuntu.

1. Is this possible?

2.  I seen a partioning tool in the ubuntu GUI but didnt want to jump into that,  does that work?

3. Any suggestions for getting the extra space without re-installing xp?


Thanks in advance

---

### Post by S1NGH on 2006-12-10
Indeed it is possible as i have resized my Windows XP NTFS partition before.
You will need to use GParted for this and resize your XP partition, hence you will get some unallocated free space. You may make it as a primary partition if you may want or use it as an extended partition inorder to add more partitions into it.
Remember:
You may only have 4 primary partitions.

---

