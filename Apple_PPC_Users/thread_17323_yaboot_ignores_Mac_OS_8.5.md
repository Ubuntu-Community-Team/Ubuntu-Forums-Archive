---
title: "yaboot ignores Mac OS 8.5"
date: 2005-02-27
forum: Apple PPC Users
---

### Post by Aurora on 2005-02-27
Hello,

I made two partitions with the Mac disk utility, set the first one as Mac and the other as unassigned, and installed Mac on the first partition. Then I booted the Ubuntu install CD and set the Mac partition as the newworld boot partition and flagged it bootable, added a swap partition and a bootable ext 3 partition.  Installed Ubuntu to the ext 3 partition--runs beautifully :) However, the yaboot menu doesn't list a Mac OS, neither does /etc/yaboot.conf .  What must I do differently to dual boot, with Mac OS 8.5 as the default?

--Aurora

---

### Post by Aurora on 2005-02-28
After learning at [www.penguinppc.org](www.penguinppc.org) about the partitioning procedure, I resolved to create a separate 1MB bootstrap partition, only to find that the "partition free space automatically" option does exactly that. I reinstalled both OS's. The only difference is that now I don't see any config files when I try ~$ sudo pico /etc/yaboot.config  :confused: 

--A

---

