---
title: "Excessive Partitions"
date: 2007-11-29
forum: Apple PPC Users
---

### Post by Doctor J on 2007-11-29
Here's the story: PowerBook G4 dual-booting Ubuntu and Tiger.  I tried the Gutsy upgrade, but found no joy there.  I wiped the linux partition, re-installed Feisty from scratch.  Now, however, i have 2 Bootstrap partitions and 2 linux-swap partitions.  Here's the map:

hda1     Apple_partition_map
hda-1    free
hda2     Apple_Bootstrap
hda3     hfs+ [Tiger]
hda4     Apple_Bootstrap
hda5     linux_swap
hda6     ext3 [Feisty]
hda7     linux_swap

The kicker is, my edits to /etc/yaboot.conf are being ignored.  I suspect that the old Gutsy Bootstrap is the one actually running things.  Question is, which is it?  I could speculate that hda2 and hda5 are leftovers from Gutsy, but haven't been able to find any confirmation in PartEd nor DiskUtil.  Short of wiping all linux partitions and starting over, how do i straighten this out?

---

### Post by Doctor J on 2007-12-07
bump

---

### Post by stmiller on 2007-12-08
This is a somewhat sticky situation, but using a live ubuntu CD you can delete the unneeded partitions, and set the boot partition with fdisk to the correct boot partition. You would also have to resize the desired partitions to fill out that now free space... 

I would just back up my files and start over, making sure to delete the unneeded partitions during the install. :(

---

### Post by Doctor J on 2007-12-08
> **stmiller said:**
> I would just back up my files and start over, making sure to delete the unneeded partitions during the install. :(

Well that's more or less what i ended up doing.  GPartEd got rid of the Feisty partition, both Bootstraps and the swaps.  Installing again set everything aright.  Now i can actually change the boot menu, woohoo!

---

