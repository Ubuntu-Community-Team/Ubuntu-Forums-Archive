---
title: "[SOLVED] Stuck with old Swap"
date: 2009-01-02
forum: Apple Hardware Users
---

### Post by iAtari on 2009-01-02
Hi there, I had Ubuntu 8.10/OS X  booting on separate partitions on a 3,1 Macbook. I followed the guide on ubuntu help for installing.

However, after needing to triple-boot, I erased and removed my ubuntu (ext3) partition using Disc Utility, but i couldn't remove the swap partition. It wouldn't mount, nor reformat.

I went into gparted and removed the swap, then reformatted the free space as fat32. Booting back into OSX, Disc Utility still can't mount or do anything with this new partition. Bootcamp can't do anything, as its not formatted as HFS+. I also tried with NTFS.

I can't format it as HFS+ in gparted, it's grayed out. 

Any suggestions on how to get Disc Utility to mount the partition so I can restore it back into my Macintosh HD volume? (possibly via bootcamp)?

---

### Post by iAtari on 2009-01-02
Nevermind, I erased the partition, erased the free space and resized OSX. All is working, my mistake for overlooking that.

---

### Post by cyberdork33 on 2009-01-02
just for additional information onteh above problem, 

There is a bug in gparted that makes FAT32 partitions created with it incompatible with OSX, though it can still be mounted manually from the commandline. If a FAT32 partition is desired, just leave free, blank space and create an "msdos" partition with DiskUtility in OSX. This will make a FAT32 partition that is usable from both OSX and Ubuntu.

Also, DiskUtility does not know how to deal with Linux swap partitions, so you do have to use gparted to delete such partitions (as the above poster figured out).

iAtari,
Can you please mark this thread as solved from the thread tools menu at the top of the page?

---

