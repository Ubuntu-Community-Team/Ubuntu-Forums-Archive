---
title: "immovable files"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by djen9999 on 2007-02-16
I burned the iso image and ran Ubuntu from the CD for a few days and felt comfortable enough to create a dual boot system.  First order of business was to defrag my hard drive.  When I finished defragmenting I was surprised to see two immovable files.  One at half way and another a third of the way beyond that.  I'm afraid of resizing any partitions with these two immovable files in the way.  

I am completely new and prior to a week ago, never even entertained the idea of a dual boot system.

I've attached a screen shot of my defrag window.

Any suggestions?

Dave

---

### Post by logos34 on 2007-02-16
Those are probably your swap/paging and hibernation files.  Or system restore.  Try going into control panel>system>advanced and disabling virtual memory.  Do the same for hibernation (in power managementt).  Go back and check to see they're gone.

I'd also run CHKDSK/error checking to fix any potential bad sectors, corrupt files.  

Hopefully you will be able shrink it during install without a problem.

---

### Post by old_geekster on 2007-02-16
These files are related to Windows.  Therefore, when you add a partition, they will stay with the Windows partition.

This is the reason for having Windows installed before installing Ubunu/Linux.  It is probably better if you allow Ubuntu to create the partitions.  It will assure that Windows is handled properly.

GRUB (GRand Unified Bootloader) will be installed on the first sector of your hard drive.  This is the program that allows you to pick the OS that you want to boot.

I have done dual-boot situations both on the same drive and separate drives.  When I was a complete newbie, I sat back and crossed my fingers that things would be done so I still had Windows.  I have never had a problem.

Go for it.  You will be pleasantly surprised!

p.s. Just do a backup of your important files.  This is always the best policy.

---

### Post by mcduck on 2007-02-16
you should boot windows into safe mode and run defrag again. Otherwise it's notable to move all files.

---

### Post by djen9999 on 2007-02-16
Thanks for the quick response and the great advice.  I turned off virtual memory which got rid of the file to the far right.  I'm sure that the file in the middle is my recovery.  I still have plenty of room for a second partition.  Now it's back-up time.

One more quick question. Is GRUB automatically added to the first sector or do I have get it there through some process that I am yet unfamiliar with?

Dave

---

### Post by Maestro23 on 2007-02-16
> **djen9999 said:**
> Thanks for the quick response and the great advice.  I turned off virtual memory which got rid of the file to the far right.  I'm sure that the file in the middle is my recovery.  I still have plenty of room for a second partition.  Now it's back-up time.

One more quick question. Is GRUB automatically added to the first sector or do I have get it there through some process that I am yet unfamiliar with?

Dave

It will automatically go into the MBR (Master Boot Record).

---

