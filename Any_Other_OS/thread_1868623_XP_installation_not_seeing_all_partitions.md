---
title: "XP installation not seeing all partitions?"
date: 2011-10-24
forum: Any Other OS
---

### Post by Xtensity on 2011-10-24
I've played around with my partition tables for my primary drive a bit with Gparted, but no damage is caused.

Right now I have in the partition Table...
Unpartitioned Space - 10 GIG
/dev/sda2 - ntfs - 215/250gig - win 7
Unpartitioned Space - 30gig
/dev/sda4 - ext3 - 20/83gig - ubuntu


The only partition that the XP installation disc sees is the windows 7 one, the /dev/sda2... How come it doesn't see that other unpartitioned space? I did a bit of searching and some people said it may need sata drivers to be loaded at XP installation... but it's seeing this sata drive perfectly fine so I doubt that's the reason. It just wont see the partitions.

Any tips on what ubuntu could be doing to cause this?

---

### Post by oldfred on 2011-10-24
If you are trying to install XP, one of the defaults is to install to a NTFS partition with the boot flag (active partition). I would expect it to see the unallocated since you have an available primary but the combination of active partition already used and the ext4 partition that it really cannot see confuses it.

I would just create a NTFS partition and move boot flag to it. Then it will install to that partition. One advantage is then you can directly boot each windows. Otherwise windows combines boots into one and grub can only boot the windows partition with the boot flag.

To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by JRV on 2011-10-24
A long time ago I was dual booting Windows and OS2.  My first partition was Windows, the second partition was OS2, and the third FAT.

Windows could not see the FAT partition.  I believe that Windows can not see any partition after a non-Windows partition.

---

### Post by Xtensity on 2011-10-24
I created a NTFS partition and flagged it boot.

It created as sda1, the first partition on the drive so to speak. 

Rebooted with XP disc.. and it still was seeing that primary windows partition that I don't use anymore and can't have deleted since I need the files on it.

---

### Post by techvish81 on 2011-10-24
mods should change the name of this thread,  it's not "Ubuntu stopping", but its windows unable to see.

---

### Post by oldfred on 2011-10-24
I almost moved it before but it is really a Windows issue. Moved to other OS sub forum.

---

### Post by Xtensity on 2011-10-24
Actually it's an ubuntu issue because I didn't start having these problems until i started using ubuntu and gparted.

Ubuntu has done something disallowing windows to see these partitions. I have installed xp on this computer before, before I used ubuntu with multiple partitions present and had no problems.. now I use ubuntu and problem. mmm

---

### Post by Mark Phelps on 2011-10-24
It's more likely GParted, not Ubuntu.  I've tried to tell folks that the best approach is to use Windows utilities with Windows filesystems, and Linux utilities with Linux filesystems -- but keep getting thrashed by the GParted fans.

If you can't even see the partition from Windows, you can't run chkdsk on it -- which would most likely fix it.

You could Google for Hiren's CD, download the image, burn it to CD, and try that.  It has a host of filesystem utilities.

You could also use the free Partition Wizard.  This is an MS Windows partitioning app.  You may be able to diagnose and repair partition problems with that.

---

### Post by Xtensity on 2011-10-24
If I could get on my WIndows 7 partition, what do you suggest I do to the partition that I want to install xp on?

---

### Post by oldfred on 2011-10-24
You can boot directly to Windows by reinstalling the Windows boot loader(fixMBR)  and moving boot flag back to your Windows 7 partition. Or install lilo's boot loader which works just like Windows boot loader.
You can use Supergrub to boot most working systems or Boot Repair to fix minor booting issues and/or run the boot info script for analysis of issues.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

From Windows repairCD:
Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands

The NTFS partition that gparted creates may not be the newer boot sector that Windows 7 wants to see. There seem to be 3 versions of NTFS boot sectors. Non-bootable, XP, & Windows 7. Each may have slightly different structures. When I used a Windows 7 repair USB to run chkdsk on my XP partition it did more repairs and updated boot sector to Windows 7. XP still booted which surprised me. But I used the Windows 7 repair disk to convert it back to XP boot sector.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

