---
title: "How would I go about this?"
date: 2009-04-06
forum: Apple Hardware Users
---

### Post by computergeek6 on 2009-04-06
I need to remove my Ubuntu Linux partitions (1 for OS, 1 for swap) and turn it into a Time Machine volume. How would I do this without erasing my MacOS installation?

---

### Post by cyberdork33 on 2009-04-06
> **computergeek6 said:**
> I need to remove my Ubuntu Linux partitions (1 for OS, 1 for swap) and turn it into a Time Machine volume. How would I do this without erasing my MacOS installation?

Just a Note, keeping a backup on the same drive as what you are backing up is kinda pointeless... (if your hard drive fails, you still lose the backup).

If you want to continue, you can boot the Ubuntu LiveCD and start the partition editor (gparted). There you can unmount the swap partitition (the livecd uses it), then delete the Ubuntu root partition and the swap partition. After that, you should be able to boot into OS X and use DiskUtility to put a new HFS+ partition in the free space.

---

### Post by computergeek6 on 2009-04-06
So, I can do that in Disk Utility without erasing my Mac partition?

---

### Post by cyberdork33 on 2009-04-06
> **computergeek6 said:**
> So, I can do that in Disk Utility without erasing my Mac partition?
don't repartition... you are just reformatting the existing partition. ou don't even touch the Mac partition for that.

---

### Post by computergeek6 on 2009-04-06
Thanks. I'll try that

EDIT: Is there a way to do it in Disk Utility? The live CD won't boot.

---

### Post by cyberdork33 on 2009-04-07
Disk Utility won't let you delete all the old partitions.


Put in the LiveCD and hold Alt/Opt while you are booting up. A menu will let you choose to boot from the CD

---

