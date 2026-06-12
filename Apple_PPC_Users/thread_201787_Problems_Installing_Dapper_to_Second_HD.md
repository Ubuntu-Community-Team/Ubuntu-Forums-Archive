---
title: "Problems Installing Dapper to Second HD"
date: 2006-06-22
forum: Apple PPC Users
---

### Post by wolfdude96 on 2006-06-22
I have a PowerMac G5 (Early June 2004) and would like to install ubuntu (dapper) on to a second partition on a secondary internal drive. I am able to partition the drive but when it comes time to install I get a message that states that no NewWorld partition can be found. My goal is to dual boot this machine with OS X 10.4 (which is on the primary internal drive). 

Please Help This Linux NOOB!

---

### Post by tidris on 2006-06-22
If you are using the live desktop CD to install, that is a known problem. Either let the installer automatically create all the partitions needed using free space in the disk, or use the "alternate" CD to install.

Does your computer have serial ATA disks?

---

### Post by hotani on 2006-06-22
I did mine with the "install" disk, not the live CD. I remember I had to explicitly set the "New World" partition before it would proceed to the next step in the install process.

---

### Post by wolfdude96 on 2006-06-22
[QUOTE=tidris]If you are using the live desktop CD to install, that is a known problem. Either let the installer automatically create all the partitions needed using free space in the disk, or use the "alternate" CD to install.

Does your computer have serial ATA disks?[/QUOTE]

Yes (both of them)

---

### Post by wolfdude96 on 2006-06-22
I just installed ubuntu on the second hard dish without a bootloader, held option at startup, and my ubuntu disk did not show up.

How do u set a NewWorld partition on a disk without os x on it?

---

### Post by tidris on 2006-06-22
[QUOTE=wolfdude96]Yes (both of them)[/QUOTE]
In that case this thread will probably be of interest to you:

[http://www.ubuntuforums.org/showthread.php?t=189133](http://www.ubuntuforums.org/showthread.php?t=189133)

---

### Post by tidris on 2006-06-22
[QUOTE=wolfdude96]I just installed ubuntu on the second hard dish without a bootloader, held option at startup, and my ubuntu disk did not show up.

How do u set a NewWorld partition on a disk without os x on it?[/QUOTE]

The way I did it was to let the ubuntu installer automatically create all the partitions it needs using the free space in the disk. In that case it creates a newworld boostrap partition, a root partition and a swap partition. Even if you go that super easy way, do know that because you have a G5 with serial ATA disks you might have to tweak the yaboot.conf file as explained in that other thread I referenced above.

---

