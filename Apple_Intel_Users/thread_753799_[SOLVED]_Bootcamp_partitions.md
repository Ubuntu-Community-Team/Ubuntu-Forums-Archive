---
title: "[SOLVED] Bootcamp partitions"
date: 2008-04-13
forum: Apple Intel Users
---

### Post by m84 on 2008-04-13
I have installed Ubuntu via bootcamp, however when choosing the partition option, I went for the first option, which I believe partitioned my bootcamp partition again.

In Disk Utility it reads

Macintosh HD (visible)
Bootcamp (visible, 600MB)
disk0s4 (not visible, 55GB)
Linux Swap (not visible, 2.5GB)

The problem is that I have a 500MB partition that shows on my Mac os desktop that is annoying. I believe that I should reinstall ubuntu, deleting the disk0s4 and disk0s5 (Ubuntu + Swap) and then follow the macbook walkthrough properly. Is this the solution?

Thanks

---

### Post by m84 on 2008-04-13
Solved.

Used Gparted live CD to delete the two linux partitions and then grow the bootcamp one. Fantastic tool.

---

### Post by cyberdork33 on 2008-04-13
> **m84 said:**
> Solved.

Used Gparted live CD to delete the two linux partitions and then grow the bootcamp one. Fantastic tool.
Exactly what I would have suggested. 

Can you mark this as solved?

---

