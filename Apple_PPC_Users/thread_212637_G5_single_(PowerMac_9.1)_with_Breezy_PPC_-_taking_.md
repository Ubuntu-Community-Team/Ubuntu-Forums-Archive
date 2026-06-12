---
title: "G5 single (PowerMac 9.1) with Breezy PPC - taking status."
date: 2006-07-10
forum: Apple PPC Users
---

### Post by RoadTripDK on 2006-07-10
I have been looking through the Ubuntu forums again of late and it seems like the problems that have dogged iMac G5 and G5 single users (thermal control and sound) are still there in Dapper. Debian has problems with the SATA drivers somehow blocking the CD drivers at install (Sarge PPC) and USB keyboards at install (Etch PPC). So my alternatives for getting a Debian based install on my G5 were to either try to create a vanilla Debian PPC (non 64 bit) memory stick install, or installing Ubuntu PPC Breezy, I opted for installing Breezy.

Having sorted the yaboot issue in Breezy, I have the following issues to consider:

1) Sound support. The solution seems to be to do the following:

mv /dir1/dir2/artsd /dir1dir2/backartsd

Unfortunately, I haven't been able to find artsd on my Breezy install, when booting from a Dapper desktop (live) CD. I have tried with the following:

sudo mkdir /mnt/linux
sudo mount -t ext3 /dev/sda3 /mnt/linux

Then, I have tried browsing though the install folders to find artsd, but no luck :-( Where does artsd reside?

2) Thermal control issue.

I was thinking of trying a Dapper kernel, but keeping the rest of the system in Breezy for now. Is that called backporting? How do I do that? If that wouldn't work I would try a kernel from [http://www.ppckernel.org/kernel.php?id=74](http://www.ppckernel.org/kernel.php?id=74) Interestingly, I see that there is no official 2.4 or 2.6 G5 kernel build using g5_defconfig available at:

[http://www.ppckernel.org/specialized.php?category=pmac](http://www.ppckernel.org/specialized.php?category=pmac)

Weird. Anyway, I would appreciate help with either of the two above issues, so I can actually get Ubuntu Breezy up and running. I will wait with doing a dist upgrade until I am sure that the sound issue is sorted in Dapper as the postings describe the problem as being more diffused and less straight forward to get sorted out then in Breezy.

---

