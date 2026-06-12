---
title: "[SOLVED] Resizing a partition"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2008-01-03
I need to resize a partition that is nearly filled to include neighboring unallocated space.  During the resizing process will I lose any data or will unallocated space merely be tacked onto the end of the old partition?

---

### Post by victorgreen on 2008-01-03
You shouldnt lose any data on the partition you're resizing unless it has more data on it than space you intend to leave for it. The best way to resize partitions Ive found is to boot off the gparted live cd. Ubuntu includes gparted itself, but to work correctly the drive has to be unmounted which is annoying to do in terminal and obviously wouldnt work if you're currently booting off that drive.

The gparted livecd gets you around that little hurdle. Its either a 70 or 90 something meg iso. Good luck!

---

### Post by dcstar on 2008-01-03
> **victorgreen said:**
> You shouldnt lose any data on the partition you're resizing unless it has more data on it than space you intend to leave for it. The best way to resize partitions Ive found is to boot off the gparted live cd. Ubuntu includes gparted itself, but to work correctly the drive has to be unmounted which is annoying to do in terminal and obviously wouldnt work if you're currently booting off that drive.

The gparted livecd gets you around that little hurdle. Its either a 70 or 90 something meg iso. Good luck!

Booting off the Ubuntu install CD will also allow you to resize disk partitions as it has gparted available in it.

---

### Post by sciencewhiz on 2008-01-03
while resizing is relatively safe, you should ALWAYS back up anything important, just in case.

---

