---
title: "Need help with Harddrive"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Tr0n on 2007-01-23
I have a Western Digital Caviar SE 120GB hard drive. However ever sense I've installed Ubuntu the hard drive is being recognized as only having roughly 33 GB, I tried googling this for solutions however all the solutions are for XP, however this problem didn't occur while I had XP. Thanks ahead for the help.

---

### Post by ucsdrake on 2007-01-23
can you be a bit more specific on the matter? which OS is only identifying it as 33GB Ubuntu or Windows and what setup did you use when installing Ubuntu (ie partitions used and please include file systems)

---

### Post by rabid emu on 2007-01-23
Do you have it dual-booted?  If so it'll show the size of the individual partitions you're using rather than the whole disk.  If you only have ubuntu installed on a single 100gb partition for your disk, then that's a different question.

---

### Post by bionnaki on 2007-01-23
perhaps you setup your partitions incorrectly and you are reading that your / partition is 33 gigs. 

post the output of *sudo fdisk -l*

---

### Post by Tr0n on 2007-01-23
Sorry for not being clear. I'm not dual-booting, I've installed Ubuntu recently. When I installed I formatted both HDD, so they're both empty, but after I mounted the drive it said it only has 33gb. So I only have Ubuntu and both HDD were formatted before the install.

---

### Post by Tr0n on 2007-01-23
> **bionnaki said:**
> perhaps you setup your partitions incorrectly and you are reading that your / partition is 33 gigs. 

post the output of *sudo fdisk -l*
Disk /dev/hda: 33.8 GB, 33820284928 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4111    33021576   83  Linux

Disk /dev/hdb: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2375    19077156   83  Linux
/dev/hdb2            2376        2480      843412+   5  Extended
/dev/hdb5            2376        2480      843381   82  Linux swap / Solaris

---

