---
title: "Macbook 2,1 with XP and Ubuntu - Trouble installing"
date: 2009-07-31
forum: Apple Hardware Users
---

### Post by voltage22 on 2009-07-31
I have a Macbook 2,1 with XP SP3 already installed via bootcamp on a partition and I created another partition with diskutility of my main Mac partition to format later for Ubuntu.

I followed these directions to a T:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Mac OSX, XP, and Ubuntu]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Mac OSX, XP, and Ubuntu")

And when I restarted my computer and loaded the CD I burned of rEFit, when I selected the penguin icon, it said "Load Linux from..." without a specification of where the installation was. For both XP and Mac OS it displayed the partition number. When I selected it, it just went to the grey screen with the penguin icon and sat there doing nothing.

I decided to try again with slight modification. I loaded up the Ubuntu CD again and formatted the same partition again but this time with the ext4 system instead of ext3 (Yes, on the last step I went to "Advanced" and installed the bootloader on the Linux partition with a "/" mount point) and it still doesn't work, except this time when I go to rEFit and choose the penguin icon, it displays "Load Linux on partition 3" as it should, but I get the same result when I try to load it from there.

Both times I've tried the Partition tool on rEFit and it has said there is "no need to sync." In the standard Apple menu for loading partitions and discs, the Linux partition is not displayed.

Any help would be appreciated, sorry if this is a repeat post!

---

### Post by voltage22 on 2009-08-03
edit

---

