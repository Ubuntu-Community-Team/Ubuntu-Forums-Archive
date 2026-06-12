---
title: "Have a new iMac? Post issues here. Installation instructions."
date: 2007-09-05
forum: Apple Intel Users
---

### Post by seanieb64 on 2007-09-05
Here are all the problems I've faced with the new aluminum iMacs

No sound,

You must use the Gutsy Gibbon Tribe Five beta release to use Ubuntu on your mac.

Installing:

[http://cdimage.ubuntu.com/releases/gutsy/tribe-5/gutsy-desktop-i386.iso](http://cdimage.ubuntu.com/releases/gutsy/tribe-5/gutsy-desktop-i386.iso)

Download this and burn the image with OS X Disk Utility (Applications -> Utilities -> Disk Utility.)

Install Apple BootCamp, Have it partition a bit of your disk for you, Insert the Gutsy disk in the drive when it prompts for the Windows disk, let it reboot, It will boot to the LiveCD normally, but slowly, Be patient with it. Run the installer. When you reach the partitioner, select the fat32 or ntfs partition the BootCamp wzard made, Delete it, and make a new partition that's at least 2042 MB (2 GB) less than he amount of free space. Make this mount point "/" no quotes and format it as ext3  and make the 2024 MB partition swap.

Install normally.

---

