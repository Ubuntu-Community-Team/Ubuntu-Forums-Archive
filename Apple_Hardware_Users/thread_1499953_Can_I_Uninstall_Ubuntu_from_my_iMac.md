---
title: "Can I Uninstall Ubuntu from my iMac?"
date: 2010-06-02
forum: Apple Hardware Users
---

### Post by TechnoEagle on 2010-06-02
I installed both Ubuntu Linux 10.04 and Linux Mint 9 on my iMac (10.6.3) through Bootcamp. Now, if it is possible, I would like to uninstall Ubuntu, but keep Linux Mint. For this reason, I cannot simply restore my hard drive to a single partition. :(

When I open up disk utility, it says I have 7 partitions as follows: Macintosh HD (248.03 GB), DISK0S3 (1.00 MB), DISK0S4 (34.49 GB), Linux Swap (2.97 GB), disk0s6 (1.00 MB), DISK0S7 (32.90 GB), and Linux Swap (1.46 GB). There is also 34.36 GB of free space. Based on the sizes of the partitions, I am pretty sure that DISK0S4 and DISK0S7 are the two Linux partitions. I have absolutely no idea what any of the other partitions are for (aside from Macintosh HD). :confused:

I was thinking that it might be possible to simply erase all of the partitions other than the DISK0S7 and the Macintosh HD, but I don't want to delete anything important. If anyone could help me, I would appreciate it! :KS

---

### Post by linuxopjemac on 2010-06-02
I would delete the Ubuntu partition with gparted and make it space for Linux Mint. You have to update grub though.

---

