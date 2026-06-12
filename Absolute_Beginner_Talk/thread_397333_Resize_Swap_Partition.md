---
title: "Resize Swap Partition"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by infin?ty on 2007-03-30
By mistake, i made my swap partition as 5 GiB.
How can i reduce the size of my swap partition to 512 MB

---

### Post by raja on 2007-03-30
You can resize it with gparted. It may be best to do it with the live cd (so that the partitions will be unmounted). You can then add the free space created to the adjacent partition or create a new partition in that space.

---

