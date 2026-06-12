---
title: "new install-multiboot sys"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by leavingOS2 on 2007-01-03
Yesterday, after much planning, I completed my first install of Unbuntu (6.06).  All went very smoothly.  Because I have a legacy software application and a piece of legacy hardware that require it, I planned a multiboot system, with a primary partition for Win98 and an extended partition for OS/2.  Because of my familiarity with OS/2 and IBM's Boot Manager, I planned to use Boot Manager for booting.

First I partitioned (but not formatted) using an OS/2 liveCD.  I installed Ubuntu, /boot on a primary, swap and root on extended partitions.  After it was working, I installed Win98.  After it was working, I installed OS/2.  Finally, I added the three booting OSes to the Boot Manager menu (which identifies the Linux boot partition as a Type 83 partition).  OS/2 and Win98 boot from the Boot Manager menu, but when I choose Unbuntu, I get an error message stating that "The partition is not formatted" and it will not boot.

To determine whether the Windows install may have wiped out the /boot partition I figured I could boot from the Ubuntu live CD and see if I could view the partition.  However, I got a login screen that did not accept the ID and Password I used for my hard drive installation of Ubuntu; and since I was never prompted for an ID/Password before with the live CD boot, I'm not sure where it booted from.  I did get the usual live CD menu when the computer first started, so maybe it was some sort of hybrid boot between CD and HD?

Two questions:
1. Any idea on getting Ubuntu to load from Boot Manager?  (I can ask this in the OS/2 forums, too--they seem to have plenty of linux experience there, maybe the writing is on the wall).

2. If it is a meaningful diagnostic step to address question 1, can I still boot from the live CD after having Ubuntu installed on my HD, and how (what was the problem with the ID/Password prompt)?

Thanks,
LeavingOS2

---

