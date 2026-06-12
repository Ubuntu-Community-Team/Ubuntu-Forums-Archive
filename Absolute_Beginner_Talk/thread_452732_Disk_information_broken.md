---
title: "Disk information broken"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by transparent9 on 2007-05-23
This is related to my other thread about how I [[COLOR="DarkOrange"]overwrote the first bit of my NTFS partition with a 13mb vmware tools iso.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=451120")

Even though my Windows partition appears to work, it's still called "vmware tools" and identified as a joliet filesystem... **even after I completely reformatted and reinstalled ubuntu!**  This is after I overwrote the MBR with a new one (windows' fixmbr command).  

I have no idea where this information is coming from, why does ubuntu think that partition is still "vmware tools"?  I've since repaired the filesystem, repaired the MFT, repaired the boot sector, and boot loader, but somehow, ubuntu thinks it's the vmware iso.

Where else would this information be stored, if not in the MBR, MFT or boot sector of the partition?

thanks for any help

---

### Post by dstew on 2007-05-23
The fixmbr command only adds the boot loader to the MBR. It does nothing to the partition table. The only way I know of to change the partition table is to re-partition and/or reformat. I think you can also directly write an image there, but I do not know how to do that. I think you use the **dd** command.

---

