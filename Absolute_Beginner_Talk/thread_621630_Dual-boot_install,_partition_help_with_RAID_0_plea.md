---
title: "Dual-boot install, partition help with RAID 0 please"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by tenpenny on 2007-11-23
Hi!

This is my first posting here.  I have a machine with XP on it and I want to create a dual-boot setup with Gutsy Gibbon.  The problem is when I get to the partitioning stage, I don't see the Windows partition at all.  I can't get to the point where I see the XP partition to adjust its size.  The only thing that shows up under devices in the installer is "/dev/sda" and "/dev/sdb."  There is no data in the Type, Mount Point, Format, Size, or Used columns.

After selecting one of the above devices anyway and choosing "new partition table,"  I get the message, "You have selected an entire device to partition.  If you proceed with creating a new partition table on the device, then all current partitions will be removed."

If I go the non-manual route, I get the message, "Warning--this will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted."

The drive type I have is a 320GB (160GB x 2) SATA in RAID 0 configuration.  I don't believe it is fakeraid, although I'm not sure.  My device manager shows it as an Intel 82801GHM SATA RAID Controller.  Do you think the RAID 0 is the reason I'm not seeing the Windows partition?  If it is, is there anything I can do about it?

Thanks for any advice you can provide!

-Eric

---

### Post by spiderbatdad on 2007-11-23
how are you partitioning with gparted or trying to use a windows partitioner?
after defragging windows you can go ahead and boot from the live cd and from the desktop select install. gparted should offer to resize the disk for you

---

### Post by tenpenny on 2007-11-23
I tried partitioning through the live cd after scanning and defragging.  I also tried using System Rescue, which I believe uses gparted as well.  Unforunately, in both cases I got the same result--no access to the Windows XP partition, which I want to, of course, resize.

I don't know if it's the RAID SATA setup that's the cause of this, but I've just read about hiccups when trying to dual-boot with this type of hard-drive.  However, I'm not sure if this would also be a problem in just getting the partitions ready..

---

