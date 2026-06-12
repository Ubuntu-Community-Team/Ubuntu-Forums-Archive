---
title: "Can't Install Ubuntu 7.04"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Holy Knight on 2007-08-06
Hello to you Ubuntu users,I have a huge problem.

You see I ordered a cd of Ubuntu 7.04 and tried to install it through Graphical Installer on a FAT32 partition.Everything went well,but after rebooting the PC a message "Error loading Operating System"occurred.Upon investigation I discovered that the installer was able to resize the selected partition but didn't install a single file.Strange,I was able to install 6.06LTS flawlessly.

Please somebody help me,I really want to use the latest version of Ubuntu badly :(.

---

### Post by hessiess on 2007-08-06
sistem specs?

---

### Post by Holy Knight on 2007-08-06
> **hessiess said:**
> sistem specs?

Lets see

Intel Celeron D processor 2.4 GHZ
384 MB DDR RAM
ATI Radeon 9250
Asus P4GE MX Motherboard
Buitin Sound Card(AC 97)
RealTek LAN Card

enough?

---

### Post by splintercellguy on 2007-08-06
I don't believe you can install Ubuntu on a FAT32 partition, what reason did you decide to not just do it on an ext3 partition?

---

### Post by Holy Knight on 2007-08-06
> **splintercellguy said:**
> I don't believe you can install Ubuntu on a FAT32 partition, what reason did you decide to not just do it on an ext3 partition?

You are saying that Ubuntu cannot be installed on FAT32 partition?Weird....I was to install 6.06 normally.
And the reason why i am not using ext3 is that i want a dual system in my PC...WinXp and Ubuntu(WinXp for temporary period until i setup Ubuntu completely) adn i heard that WinXp cannot read/write on ext3 filesystem.

---

### Post by hessiess on 2007-08-06
^dident notice that
reinstall it on an ext3 partition
also the ati card may be problomatic

> adn i heard that WinXp cannot read/write on ext3 filesystem.
it cannot normaly, you ether need the ext3 win driver or make a 3rd partition as ntfs/ install ntfs3g on linux, or a fat32 partition

---

### Post by Ek0nomik on 2007-08-06
You can't install Ubuntu onto a FAT32 partition.  You need to install it on an EXT3 partition.

You can have Windows read the EXT3 partition, but it will take third party software to do so.  Just as you can have Linux read the NTFS file system (the one Windows uses), but it again will take third party software.

You need to install Ubuntu onto an EXT3 partition with another partition of Swap.  You can create a third partition as FAT32 if you want to use it as a "sharing" partition for both Windows and Linux.  You could dump any file you want onto it and than both O/S's will be able to read and write to files off of it without any third party software.

---

### Post by Holy Knight on 2007-08-06
> **hessiess said:**
> ^dident notice that
reinstall it on an ext3 partition
also the ati card may be problomatic

That reminds me...During Installation..in step 4 there is a choice of resizing a partition with the largest space(Automatic).I once tried to do Manual partitioning (by choosing Manual option) but came a problem....How can i define a root file system in the partition of my choice?(It is sda7)

---

### Post by Ek0nomik on 2007-08-06
> **Holy Knight said:**
> That reminds me...During Installation..in step 4 there is a choice of resizing a partition with the largest space(Automatic).I once tried to do Manual partitioning (by choosing Manual option) but came a problem....How can i define a root file system in the partition of my choice?(It is sda7)

You are doing this with the Live CD?

You should be able to right click on the partition and assign it to "/".

---

### Post by Holy Knight on 2007-08-06
> **Ek0nomik said:**
> You can't install Ubuntu onto a FAT32 partition.  You need to install it on an EXT3 partition.

You can have Windows read the EXT3 partition, but it will take third party software to do so.  Just as you can have Linux read the NTFS file system (the one Windows uses), but it again will take third party software.

You need to install Ubuntu onto an EXT3 partition with another partition of Swap.  You can create a third partition as FAT32 if you want to use it as a "sharing" partition for both Windows and Linux.  You could dump any file you want onto it and than both O/S's will be able to read and write to files off of it without any third party software.

Now that you told me...what is the name of that third party software and where will I get it?

---

### Post by stchman on 2007-08-06
> **Holy Knight said:**
> Hello to you Ubuntu users,I have a huge problem.

You see I ordered a cd of Ubuntu 7.04 and tried to install it through Graphical Installer on a FAT32 partition.Everything went well,but after rebooting the PC a message "Error loading Operating System"occurred.Upon investigation I discovered that the installer was able to resize the selected partition but didn't install a single file.Strange,I was able to install 6.06LTS flawlessly.

Please somebody help me,I really want to use the latest version of Ubuntu badly :(.

Create some free space (~20GB) and install Ubuntu to the free space.

---

### Post by Holy Knight on 2007-08-06
> **Ek0nomik said:**
> You are doing this with the Live CD?

You should be able to right click on the partition and assign it to "/".

Assign what?The mount Point of the partition?This is getting a bit confusing :S?

---

### Post by Holy Knight on 2007-08-06
> **stchman said:**
> Create some free space (~20GB) and install Ubuntu to the free space.

20 GB????The cover says 2GB!

---

### Post by Ek0nomik on 2007-08-06
> **Holy Knight said:**
> Assign what?The mount Point of the partition?This is getting a bit confusing :S?

If you want to assign a partition to be root, then yes, the mount point.  Sorry if I wasn't clear enough.  :)

If you want to read NTFS file systems in Linux, you will want to use NTFS-3G - [https://wiki.ubuntu.com/ntfs-3g](https://wiki.ubuntu.com/ntfs-3g).

If you want to read EXT3 file systems in Windows, you will want to look at [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Ek0nomik on 2007-08-06
> **Holy Knight said:**
> 20 GB????The cover says 2GB!

Correct, a fresh Ubuntu install should entail about 2.5GB of hard disk space.  Give or take.

However, you will be installing new software as time progresses (or so one would assume).  For that reason, you will want to give it a little buffer so you don't run out of space.  It really depends on what you will be doing and how tight for space you are.  You need to think it through for yourself.  :)

If it were me, I'd give it another 3-5GB for software installation.

---

### Post by Holy Knight on 2007-08-07
And Oh Yeah,one more thing...
since i don't know much about manual partitioning,can you tell me how to resize a partition in order to create a new partition for Linux swap.And also how many swap type partition should I create?

P.S:Sorry for the late reply,my internet was down.

---

### Post by stchman on 2007-08-07
> **Holy Knight said:**
> 20 GB????The cover says 2GB!

What cover????  A fully installed Ubuntu takes abour 3GB and the swap about another 1.5GB.  I don't know where you got that info.

If you are that short on hdd space then make it 10GB.

---

### Post by Holy Knight on 2007-08-07
> **stchman said:**
> What cover????  A fully installed Ubuntu takes abour 3GB and the swap about another 1.5GB.  I don't know where you got that info.

If you are that short on hdd space then make it 10GB.

Ok,but can you tell me how to resize a partition in order to create a swap partition for Linux?And how many swap partition should I create?

---

### Post by stchman on 2007-08-07
> **Holy Knight said:**
> Ok,but can you tell me how to resize a partition in order to create a swap partition for Linux?And how many swap partition should I create?

Ok, if you are going to install Ubuntu for the first time on a PC I will assume a few things.

1.  Windows NTFS
2.  You need to run a chkdsk and defrag

First thing run a chkdsk /f on all NTFS partitions followed by a defrag.  When that is done boot up to the LiveCD and fire up gparted.  Select the partition you want and then select resize.  What is left over will be free space.  Leave it that way.  Install ubuntu and tell it to use the largest available free space.

There you go.

---

### Post by maccawolf on 2007-08-07
I"m gonna "second" the request for the name of the 3rd party software that enables you to "see" Llinux form fat32.

BTW, I have no problem accessing fat32 FROM Linux.

---

### Post by stchman on 2007-08-07
> **maccawolf said:**
> I"m gonna "second" the request for the name of the 3rd party software that enables you to "see" Llinux form fat32.

BTW, I have no problem accessing fat32 FROM Linux.

The only OS I know of that uses FAT32 is WinME or older.  Win2K, WinXP and such are native NTFS.

There might be a piece of software that enables a FAT32 based OS to see EXT3, I am just not aware of it.

---

### Post by Holy Knight on 2007-08-08
> **maccawolf said:**
> BTW, I have no problem accessing fat32 FROM Linux.

I didn't say accessing FAT32 through Linux,Ubuntu LiveCD can do that but my problem is installing Linux on FAT32 partition.

---

### Post by Holy Knight on 2007-08-09
YAY!!!! I got Ubuntu INSTALLED!!!! \\:D/
But now i have to mount two partitions out of four (sda1 mounted,sda5 mounted but sda6 my personal partition and sda7 the Ubuntu partition with ext3 filesystem)

and configure Network settings(LAN,DynamicDNS with static IP) to make Internet browsing and file sharing possible.

And Wine to play games like Counter-Strike 1.6(not a hardcore gamer but I still like to change weapon models using Half-Life Model Viewer or HLMV) and few other games like BF2,MOHPA etc...still commercial games are pretty dang boring.

Can I obtain all these requirements?If so tell me where to go for help.Last request.

And Thank You all for helping me install Ubuntu by the way :)

---

