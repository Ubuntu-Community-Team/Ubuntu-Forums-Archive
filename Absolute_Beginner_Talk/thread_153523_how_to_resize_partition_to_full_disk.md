---
title: "how to resize partition to full disk"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-04-01
I want to resize hda3 to full size of disk space


isk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda3            2810        4776    15799927+  83  Linux
/dev/hda4            4777        4864      706860    5  Extended
root@ubuntu:~#         

here is what qtpated shows the sofware is not inportant is how to do it

dev/hda1 FREE  21.52 GB STATUS HIDDEN
/dev/hda3 as above
/dev/hda4 as above
dev/hda1 FREE 690.25mb STATUS HIDDEN

lex1

---

### Post by Ramses de Norre on 2006-04-01
```
dev/hda1 FREE 21.52 GB STATUS HIDDEN
dev/hda1 FREE 690.25mb STATUS HIDDEN
```
You've got hda1 twice, typo?
To change the partition: you'll need to delete hda1 and hda2 (if existing) and move hda3 to the beginning of the disk, then you can enlarge it with the free space behind it.
You need to do it this way because you can't change the starting point of a partition by enlarging it, you need to move it first.

---

