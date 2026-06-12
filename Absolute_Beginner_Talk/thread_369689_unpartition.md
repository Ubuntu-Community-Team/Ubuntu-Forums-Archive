---
title: "unpartition?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by windfer on 2007-02-24
thank you so much for yoour help in advance
i installed ubuntu and love it i partitioned it so my system is duel boot but now i no longer want windows i want my computer to be strickly ubuntu how do i do this

---

### Post by houstonbofh on 2007-02-24
Well...  One way is to boot the livecd, run gpartd and delete the partition.  Next expand your linux partitions.  Then you need to reinstall grub.

Another option is to clean up your Windows partition as much as possible.  Then boot the Live CD and run gpartd to shrink your Windows partition as small as possible. (with some room to work)  Expand the Linux partitions, and juet keep Windows around for emergencies.

---

