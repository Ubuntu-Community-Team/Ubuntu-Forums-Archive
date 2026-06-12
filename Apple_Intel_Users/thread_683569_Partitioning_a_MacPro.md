---
title: "Partitioning a MacPro"
date: 2008-01-31
forum: Apple Intel Users
---

### Post by mert on 2008-01-31
I am installing Gutsy on a MacPro with 3 hard disks.  2 disks are being used for a Mac OS software RAID.  I'm planning to reformat the 3rd disk for use with Ubuntu.  When I run the installer, all three disks contain a fat32 partition mounted at /media/EFI System Partition.  The installer complains because all three disks have partitions being mounted at the same mount point.  My question is, are these partitions/mount points needed and which ones should I change to get ubuntu to install and boot?  Should I delete the mount points for the two mac disks that I'm not going to use with ubuntu?
thanks

---

### Post by cyberdork33 on 2008-01-31
> **mert said:**
> My question is, are these partitions/mount points needed and which ones should I change to get ubuntu to install and boot?  Should I delete the mount points for the two mac disks that I'm not going to use with ubuntu?
thanks
You should not mount the EFI partitions. There are some issues with installing on Mac Pros related to multiple hard drives. Be sure to check out the FAQ.

---

### Post by mert on 2008-02-01
Its alive!  finally I've installed ubuntu on this machine.  I just deleted the mount points for the EFI partitions and ignored the warnings about the mount points when they popped up.

Now I need to figure out what to do about the fan speed control and temp monitoring. 

cheers

---

