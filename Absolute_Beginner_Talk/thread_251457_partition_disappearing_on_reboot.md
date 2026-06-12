---
title: "partition disappearing on reboot"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by barry253 on 2006-09-05
Hi all -

New to Linux, so apologies in advance if this is an easy fix that I should have known:

I am setting up MythTV on Ubuntu 6.06.  I set up a 200gb ext3 partition, and in Disks Manager, I made the access path /pvr (after creating that directory and chmoding it to 777). I clicked "Enable," it became Accessible, and MythTV was happy.

For some reason, after a reboot (about 9/10 times), the partition is no longer linked to /pvr and MythTV obviously gets upset. When I look in Disks Manager, I see that the access path field is blank, and the status is now Inaccessible.  When I manually enter the info again, it works fine.

Why is this, and how do I fix it?  If there's any log you want me to post, please let me know (with exact place I can find it).

Thanks in advance!
--Barry

---

### Post by barry253 on 2006-09-05
Solved it on my own...didn't realize I had to manually edit fstab.

---

