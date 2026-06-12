---
title: "Kubuntu and Ubuntu multiboot raid issue"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Maxymillion on 2008-01-16
Hello, was hoping to get some clarification on whats causing my problem.

My partitions are such

sda - Operating system

sd[bcde] - storage in a raid 0+1


Now I had the raid properly configured / well tested in Ubuntu using mdadm. Its a home PC so i decided to resize my OS drive and install KDE4 multiboot for a play.  Installed KDE4 into some free space on sda,  booted into Ubuntu and setup grub to multiboot. My raid at this stage was still fine.  First boot into KDE4 worked, didn't do anything. Reboot and i noticed it said "Synch'in disks" while it was beginning to reboot, getting scared I boot Ubuntu to make sure it hasn't touched my raid drives, and lo and behold they are no longer active.

During KDE4 install i made sure only sda had a "mount point" set. 
I did nothing in KDE4, just booted it once, and rebooted. 

Whether i get my data back or not i won't find out for 20-30 hours while mdadm does its thing. But obviously I can't use KDE4 until i figure out why this happened.

Any insight would be appreciated :P I'm kinda at a loss how KDE4 could possibly do something so...evil without consulting me, heck it had no raid software or anything whatsoever installed, my raid shouldn't have existed as far as KDE4 was concerned?!. 

If someone knows why it "sync'd" disk's during reboot that would be awesome 
Cheers for any help

---

