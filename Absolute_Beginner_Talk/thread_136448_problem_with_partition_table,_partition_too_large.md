---
title: "problem with partition table, partition too large"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by ninjasmith on 2006-02-26
ok put this in new thread as I'm pretty sure this is what the problem is.

pc wont boot currently,
get grub error 17 (which I think is cannot mount partition)
if I boot from installation cd and try running 

parted /dev/sdb
rescue

I just get the following message

Error: Can't have partition outside the disk

if I run fdisk I get the following

device boot start end block id system
/dev/sdb1 1 2550 20482843+ 7 ntfs
/sdb2 * 2551 3768 9783585 83 linux
/sdb3 3769 14588 86911650 f w95 ext'd (lba)
***/sdb5 ? 18391 65645 379573761 81 Minix / old linux***
/sdb6 3826 6375 20482843 7 ntfs

sdb1,2 and 5 are my linux and two windows partitions. other than that there should be a 60 gig partition which I was trying to edit when caused the problem.

I think sdb6 is the problem as it is larger than the drive. shall I just delete this and then run parted?

---

### Post by ninjasmith on 2006-02-26
/bump

also if I choose manually edit partitions from the linux installer (as if I wanted to reinstall) it sees no partitions on the drive....

anyone got any opinions on the likely problems of just deleting my dodgy partition using fdisk?

and whether haveing the dodgy partition there is causing the grub error and the inability to see the partions from the installer?

---

