---
title: "windows can't detect a partition"
date: 2011-10-16
forum: Any Other OS
---

### Post by krizanand on 2011-10-16
[FONT=Arial][SIZE=2]Hi all,[/SIZE][/FONT][SIZE=2]

         [/SIZE][SIZE=2]This may sound odd as I'm posting it on a Ubuntu forum, reason I'm posting is to make myself sure that its not a problem with Ubuntu. My laptop(Acer4736Z) has 320Gb HDD and I've partitioned it as 45G(Ubuntu 11.10), 4gb(swap), 40Gb(Windows7), remaining 250Gb for storage. I'm not able to see that 250Gb partition in WIndows7, I'm searching on Windows forums as well, is there anything I could do from Ubuntu to make it visible on Windows or it is only a Windows thingy.

Thanks.
[/SIZE]

---

### Post by Quackers on 2011-10-16
What is the 250GB partition formatted as? NTFS/FAT32/EXT4?

---

### Post by krizanand on 2011-10-16
[SIZE=2][FONT=Arial]Partition is NTFS only. Still can't figure out what is wrong.

Thanks.
[/FONT][/SIZE]

---

### Post by Quackers on 2011-10-16
Windows should have no problem recognising a NTFS partition.
Can you post a screenshot of your Windows Disk Management screen please?

---

### Post by oldfred on 2011-10-16
Moved to otherOS since mostly Windows

Windows should see it as the d: drive.

I have heard of a few cases where a Linux formated NTFS partition was not seen, but many have done that and it works.

Post this:

sudo fdisk -lu

Have you tried chkdsk on d: or does Windows repair console not see it either? 

You might try ntfsfix from Ubuntu but that only does minor repairs and sets chkdsk flag for Windows to run chkdsk, but I do not think Windows automatically runs it on data partitions just system.

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdXY x- drive y - partition

---

### Post by krizanand on 2011-10-16
[SIZE=2][FONT=Arial]I need to login to Windows for that, I will be back in few minutes, haven't checked [/FONT]windows disk management yet :)




[/SIZE]

---

### Post by Quackers on 2011-10-16
> **krizanand said:**
> [SIZE=2][FONT=Arial]I need to login to Windows for that, I will be back in few minutes, haven't checked [/FONT]windows disk management yet :)




[/SIZE]

Or see oldfred's post above for Linux commands - sorry I thought you were in Windows!
If you haven't checked WDM yet, how do you know Windows doesn't recognise the partition?

---

### Post by dFlyer on 2011-10-16
Windows should be able to read an NTFS partition. Are you sure you didn't format it as ext2, 3, or 4 by mistake?

---

### Post by krizanand on 2011-10-16
[SIZE=2]@oldfred 
-------------------------------------------------------------------------------------------------------
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00048d82

   Device Boot      Start         End      Blocks          Id          System
/dev/sda1            2048    97656831    48827392     83      Linux
/dev/sda2        97658878   194562047    48451585    5     Extended
/dev/sda3   *   194562048   625139711   215288832    7    HPFS/NTFS/exFAT
/dev/sda5        97658880   105469951     3905536    82      Linux swap / Solaris
/dev/sda6       105472000   194562047    44545024    7     HPFS/NTFS/exFAT

Disk /dev/sdb: 8000 MB, 8000110592 bytes
255 heads, 63 sectors/track, 972 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15624191     7811072    7  HPFS/NTFS/exFAT
[/SIZE]--------------------------------------------------------------------------------------------------------------------
[SIZE=2]That is what I see after typing fdisk[/SIZE] [SIZE=2]-lu

@quackers start > computer > I couldn't see that partition :) only C: 

@dFlyer I have that partition all along, it was created when I first partitioned HDD on my laptop while installing windows. I kept it as such and have installed windows fewer times but this time when I installed Windows it is not visible :)
[/SIZE]

---

### Post by Quackers on 2011-10-16
Maybe Windows can't "see" the extended partition at all (which includes sda6).

---

### Post by krizanand on 2011-10-16
[SIZE=2]Got it sorted gentlemen, In windows disk management I was able to see the partition just gave it a drive letter E: and voila it got mounted. At times you miss out checking simple things first, apologies for that. Appreciate for your time Quackers, oldfred and dFlyer, thanks :)[/SIZE]

---

### Post by Quackers on 2011-10-16
Is this Vista? I should have remembered that. It sometimes needs a prod in the right direction :-)

---

### Post by krizanand on 2011-10-16
Windows 7 Ultimate :)

---

### Post by oldfred on 2011-10-16
If you use testdisk does it show it as a valid NTFS partition?

This primarily is for those who install grub's boot loader to a window partition, but you can use it just to see if PBR partition boot sector is a valid NTFS partition.  Your partition table shows it as type 7 so that is correct, but in Window partition boot sector also has to be valid.

Restore PBR boot sector for windows from linux using testdisk
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

