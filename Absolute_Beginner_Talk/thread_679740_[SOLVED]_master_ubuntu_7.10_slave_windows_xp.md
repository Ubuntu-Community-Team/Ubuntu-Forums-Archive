---
title: "[SOLVED] master ubuntu 7.10 slave windows xp"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by TMpBG on 2008-01-27
I have installed ubuntu 7.10 on my 80 gb master drive for some time.NO BIG problems with ubuntu...
The problem come when yesterday i put 10 gb slave and try to install windows xp.Xp installer say I need partition on my master drive to store some files.So i start ubuntu live cd and run partition editor.Then I resaize my mine drive and now there is fat32 partition.No problems here...I boot from hdd and ubunto works.And again restart boot from win xp CD install program copy some fils and restart.NOW i can't boot ubuntu or win setup...some error and if I boot from win xp CD install program start from the beginning and copy files and restart again.

Here is fdisk -l : 
> 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c000c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         111      891576    b  W95 FAT32
/dev/sda2             112        9634    76493497+  83  Linux
/dev/sda3            9635       10011     3028252+   5  Extended
/dev/sda5            9635       10011     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10aa10a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1215     9759456    7  HPFS/NTFS


...and pls try to write "easy" english is not my firs language...

---

### Post by ureckifix on 2008-01-27
Windows ......Proprietary
Linux.....not
partition HD 
install win 
install...Linux
Follow the prompts should be ok
Linux goes on partion 2 
install grub in boot sector

---

### Post by TMpBG on 2008-01-27
"install grub in boot sector"

how exactly(is grup the program to chose what OS to start?)...and is there problem if I install ubuntu before win xp?

---

### Post by insane_alien on 2008-01-27
grub will go to bootsector with the installer anyway. there are some problems if you install ubuntu first but they are due to windows not playing nice rather than ubuntu.

---

### Post by rkd on 2008-01-27
It is possible to install Windows after having installed Ubuntu, but it requires some extra work.

If it would not be bad for you to erase your disks, install Windows, then install Ubuntu, that would be the simplest, and maybe quickest way to solve your problem.

If you need to keep the Ubuntu installation you already have, you can find directions for reinstalling Grub here:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Another way to fix up Grub is to use the Super Grub disk. The short instructions are here (look for the heading "I reinstalled Windows and Linux no longer boots"):

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Boot_Master_Boot_Record](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Boot_Master_Boot_Record)

That section is in the middle of the Super Grub page. If you go up to the top of the page, it tells you how to download the Super Grub image.

I'm not sure which method you would find easier. The Super Grub pages are a bit hard to read, but the Super Grub program might be easier to use than following the manual steps.

---

### Post by TMpBG on 2008-01-27
Thank YOU ALL! 

I decide to format all and install first win xp... 
still I will take a look to this links tank you rkd.

---

### Post by rkd on 2008-01-27
You probably will not have any need for the information in those links I gave, because Grub will be set up properly when you install Ubuntu after Windows. If you want to learn about how to fix problems with Grub, in case you have such problems in the future, go ahead and look at those links.

---

### Post by TMpBG on 2008-01-27
Windows xp installed in little 10 gb slave hdd...I start ubuntu life CD install it in master hdd but when the installer restart OPSS I find myself in windows xp welcome screen?NO warning that  I am going in there nothing...
OK that was disturbing ...THEN I remember...restart...open bios and yes my first boot device was my slave hdd...change it to be my master hdd an now I have bootable UBUNTU/Win PC.

...so this is my story... end for now :)

---

