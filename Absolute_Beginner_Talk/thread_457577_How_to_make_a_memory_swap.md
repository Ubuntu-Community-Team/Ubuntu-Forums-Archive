---
title: "How to make a memory swap"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-05-28
I just partitioned my computer to dual boot and i forgot to make a memory swap.

---

### Post by yabbadabbadont on 2007-05-28
If there is still free, unpartitioned space on the drive, you should be able to use it to create a swap partition.  If not, resize the last partition on the disk to make it smaller.  One gigabyte smaller should be plenty.  Now create a swap partition using the space you just freed up.  Of course, the easiest solution would be to just start over if you haven't already make a lot of customizations and don't have a lot of files to backup.

---

### Post by st33med on 2007-05-28
If I may ask, when I make a linux-swap partition using parted, will Ubuntu recognize it and use it on reboot?

If it doesn't, how do I make it? Reason why I ask is because Ubuntu crashes on me and I think it is because of having no swap and too high memory usage (usually crashes when running Firefox, the memory hogger)

---

