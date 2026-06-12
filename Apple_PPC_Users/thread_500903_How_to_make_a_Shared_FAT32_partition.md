---
title: "How to make a Shared FAT32 partition?"
date: 2007-07-14
forum: Apple PPC Users
---

### Post by kingcrowing on 2007-07-14
Hey, I've got an iMac G4 (800MHz, 17" widescreen) with a 120GB hard drive and I've got 3 ~40GB partitions on it, the first has Ubuntu 7.04, the 2nd is FAT32 (I formated it with the Gnome Partition editor on the live CD) and the 3rd is OS X (there is also the swap, newworld, and a few apple partitions on there as well), I've got the dual boot all set up perfectly fine without any hitches, I've got a drive titles Disc-1 or something in Ubuntu that is my FAT32 drive and I'd like to use that as a shared drive for both OS X and Ubuntu, however In OS X it just shows up in the disk utility as a greyed out "disk0s9" and I can't mount it or erase it or do anything with it and in the partition type it says "Apple_UNIX_SRV2" so what do I need to do to make a shared FAT partition?? And I'd also like to be able to name it something like Shared Space or something other than just Untitled, thanks!

---

### Post by earobinson on 2007-07-14
you should be able to use the live cd then fire up gnomeparted to partition your computer to add in a fat32 drive, then for linux check this out [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by kingcrowing on 2007-07-14
Well the issue is that I can do all the totally fine, I get the FAT going fine in ubuntu and I can see it on start up and read/write to it, however when I go back into OS X, I can't do anythign with the drive

---

### Post by earobinson on 2007-07-14
hum, I dont know much about os X and how they mount drives, sorry :(

---

### Post by kingcrowing on 2007-07-14
well I booted from the OS X CD and I've made the partition OS X Extended, so now i need to find an OS X tool that will let me convert it from that to FAT32 and I'm golden...

---

