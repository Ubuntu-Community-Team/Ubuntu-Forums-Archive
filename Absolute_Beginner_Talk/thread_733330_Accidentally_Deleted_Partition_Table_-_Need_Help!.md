---
title: "Accidentally Deleted Partition Table - Need Help!"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by AegisTalons on 2008-03-23
So I had Vista installed on my laptop in addition to Ubuntu. I wanted to delete Vista and switch to XP because its less resource intensive and I need it for SolidWorks. Well I went to my bios, and switched my HD from SATA to ATA because XP didn't see SATA. Then I went to XP install and deleted Vista partition. XP couldn't install cause "too many partitions". I wanted to go back into Ubuntu and use gparted to fix things up. Well, looks like I deleted the partition table and now I can't boot into anything. I popped in the Ubuntu Alternative Install cd to go into recovery mode and try to recover my partitions. Looks like there are no more partitions left, hence partition table is gone.

Please help, any ideas will be beneficial.

---

### Post by bumanie on 2008-03-24
Test disk is your best chance of recovering your data. Use the live cd version. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) However, having played around with xp and gparted since the original mishap, may reduce your chances of recovery.

---

### Post by AegisTalons on 2008-03-24
So a quick update and lessons learned: Vista on getting deleted from the disk, deletes the MBR. Using Super GRUB disk, you can rebuild the GRUB but make sure that you check where your grub is pointing to because Vista made Ubuntu point to where Vista was.

Additionally, I was having issues with GParted not being able to see partitions on the hard drive, I think an issue with gparted (I was using the liveCD). Either way, I got into Ubuntu with Super Grub, backed up my files and just reformated and now in the process of rebuilding.

Installed XP, not many drivers installed yet. Looking into Ubuntu and install time hard disk encryption.

Moral of Story: Vista (M$) will try to screw you if you don't like their OS and really mess your system up for having the gumption of deleting the Vista partitions.

---

