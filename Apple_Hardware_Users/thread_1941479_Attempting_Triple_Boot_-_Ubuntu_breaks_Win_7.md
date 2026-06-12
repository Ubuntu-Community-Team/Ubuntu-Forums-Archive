---
title: "Attempting Triple Boot - Ubuntu breaks Win 7"
date: 2012-03-15
forum: Apple Hardware Users
---

### Post by Mezentine on 2012-03-15
Alright, so this has been driving me crazy for about six hours now. I've got a 2008 Macbook and I've been trying to get three operating systems running: Lion, Ubuntu, and Windows 7(I've been using reFit as a bootloader). Installing Lion and Windows 7 works perfectly, but then after I install Ubuntu it all goes to hell. 

Here is my exact procedure: 
-Start with a hard drive that's been erased using the Mac DiskUtility
-Create three partitions in the sizes that I want. Both the Linux and the Windows partitions start out as FAT-32.
-At this point running "diskutil list" reveals four partitions: an EFI partition and the three new partitions numbered disk0s1 through 0s4
-Install Lion on the one partition
-Install reFit
-Install Windows 7 on another partition, which includes a step in which the partition is formatted to NTFS

At this point everything works fine. Then
-I go through the Ubuntu installation procedure, in which I manually select disk0s3 for installation with ext4 filesystem. I also make sure that the Linux specific loader is set to install on sda3
-Now when I reboot my computer I get reFit as usual. If I select Mac I boot into Mac. If I select Linux I get GRUB and then I can boot to Linux. If I select windows I *also* get GRUB. In both of the latter cases if I select Windows 7 inside GRUB I get an error of "Windows failed to start. A recent hardware or software change may be the cause" along with advice to run the utility from the Win 7 disc (which, if I do, says that it can't fix the current problem)
-If I now go to the Windows 7 installer on the disk and examine my partitions the previous partition for Windows 7 is now designated as "free space" 

I've done this entire procedure about three times now, with the same results. Does anyone have any advice?

EDIT: Further examination of the partitions listed under Windows 7 reveals a 0.00 MB sized partition at the top that wasn't there before and is designated as "primary". Since Mac only supports four primary partitions and the other three are EFI, Mac, and Ubuntu, it seems that the creation of this new one "kicks" the Windows partition into being designated as free space. Does this sound familiar to *anyone?*

Oh, and this  new mystery partition doesn't show up under diskutil list at all. At this point I'd probably settle for some Terminal commands to manually set the partition to primary

---

### Post by Mezentine on 2012-03-15
The problem is definitely related to this small partition. If I delete it in the Windows 7 installer (it doesn't show up in Mac) and then re-install Win 7 over the Windows partition I can then boot into Windows just fine, but then I can no longer boot into Ubuntu, because I get a "error: no such partition" error with the GRUB rescue prompt. 

So, to summarize: **when installing Ubuntu I get a minuscule partition created at the top of my partition list that apparently contains GRUB, which wouldn't be a problem except that its also designated as Primary. That, EFI, Mac and Ubuntu proper is four Primary partitions, so the Windows partition becomes invalidated.** Does that specifically sound like anything anyone can help me with?

---

