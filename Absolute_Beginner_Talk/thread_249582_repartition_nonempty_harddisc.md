---
title: "repartition nonempty harddisc"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-09-02
heho, i've got one ext3 (root), one fat32 (data), one empty partition and a swap on my physical drive. Is it possible to unify the empty space with the data disc without having to copy the data around and without loosing the data?

---

### Post by meng on 2006-09-02
If the partitions are in the order that you describe, e.g.
/dev/hda1 = / (ext3)
/dev/hda2 = [data] (fat32)
empty space
/dev/hda? = swap

then it should be a simple matter of resizing hda2. A LiveCD like GParted is probably the way to go.

If the order is different, then depending on what the order is, you may be able to get away with deleting the swap and recreating it somewhere else on the disk. Again GParted will be helpful here. If the name of the swap partition is different, you will need to change your /etc/fstab to reflect the change.

Let us know how you go.

---

