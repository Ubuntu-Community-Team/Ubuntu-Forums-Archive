---
title: "Dual boot with XP"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by hazash on 2006-08-04
Hi, I just reinstalled Windows XP on a 40GB Large partition and got 200GB left unpatitioned space that I want to install ubuntu on about 30GB and the rest for a secondary windows partition. When I try to install ubuntu I get an error on Drive 0. Do I have to partition a part of my unpartitioned space for linux before I can install ubuntu or something?

---

### Post by Frank Golden on 2006-08-04
> **hazash said:**
> Hi, I just reinstalled Windows XP on a 40GB Large partition and got 200GB left unpatitioned space that I want to install ubuntu on about 30GB and the rest for a secondary windows partition. When I try to install ubuntu I get an error on Drive 0. Do I have to partition a part of my unpartitioned space for linux before I can install ubuntu or something?
In windows partition all but 30GB of the unpartitioned space to
Fat32 you will probably need to use Partition Magic or something like that. Leave the 30GB unallocated. When you install Ubuntu
and I am assuming you are using the DesktopCD, when the install
gets to the partitioning phase choose the option to install to
the largest free space available. This will be the 30GB unallocated space. Ubuntu will create a large ext3 partition
for itself and a small swap partition and install itself.
Grub will automatically detect XP and prepare a dualboot
setup with Ubuntu the default. You can edit /boot/grub/menu.lst
later if you want XP to boot first. 
See the following link for much more info. Great read.
[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

This scheme gives you your XP partition and a large Fat32
partition that you can share between OS's. Ubuntu will be on
a separate ext3 partition with it's swap. 
The above link includes info on making the shared partition mount at bootup so you can read/write to it. You can not write
to the XP partition if XP is NTFS because writing to NTFS is
generally not possible from Linux.

---

