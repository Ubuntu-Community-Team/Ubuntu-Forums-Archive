---
title: "Newbie trying to tri boot via grub."
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by krazbaty on 2007-07-23
Hello, I'm new to Linux/Ubuntu as of this past week. Loving Ubuntu! Have a question though.

I have an IDE HD with Ubuntu loaded. Loaded this OS last. I also have a SATA drive with XP (loaded first) and Vista. Ubuntu loads great via grub, but I keep getting an Error 17 file not found when I select the Windows boot loader option. 

Again, I'm very new to this stuff so any help is appreciated. Thanks!

_sudo fdisk -l_

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2570    20643493+   7  HPFS/NTFS
/dev/sdb2            2571        4865    18434587+   f  W95 Ext'd (LBA)
/dev/sdb5            2571        4865    18434556    7  HPFS/NTFS



_menu.lst_

title		Windows Vista or XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by goodfella on 2007-07-23
Sometimes grub's devices are not the same as ubuntu's.  On my system when I change the boot order grub changes its references to my drives but ubuntu does not.  I have pretty much the same setup as you do.  I have one IDE drive and two SATA drives, one with 160 gb the other with 250 gb.  My IDE drive shows up in ubuntu as /dev/hdb while my two SATA drives show up as /dev/sda and /dev/sdb.  For grub hd0 refers to my first bootable harddrive.  For example if my drives are set in the following boot order:

IDE
SATA 160
SATA 250

GRUB refers to them as hd0, hd1, hd2 respectively.  So hd0 is my IDE drive, hd1 is my SATA drive with 160 gb and hd2 is my SATA drive with 250 gb.

With that said it could be that your device mapping is incorrect.  I would check to see if your windows drive that is referred to as hd1 is actually the second boot drive set in your bios.

---

### Post by krazbaty on 2007-07-23
The SATA drive with the Windows OS's is set in the bios as the second HD to boot. When I change the SATA drive to boot first, yeah, Vista boot loader works fine... but no Ubuntu option. 

What adjustment would you suggest I make?

Thanks

---

### Post by goodfella on 2007-07-23
The reason why Vista boots fine is because it is not going through grub.  I run windows XP on my other drive and it boots fine.  My menu.lst is setup much like yours.  Everything in your menu.lst file looks good for booting windows as the second boot drive.  You may want to try removing the makeactive line and even the savedefault line.  Other than that I think this is a Windows Vista issue.  Try google to see if anyone has had any success.  Sorry I could'nt help you more.

---

### Post by MQMike on 2007-07-23
As Goodfella says, you will have to sort out your drives.  GRUB sees your drives the same way BIOS does.  Linux may see them differently.
Add to that that you have a triple-boot setup, not just a dual boot.
Nonetheless, I haven’t tried it (because I don’t have Vista), but the following will certainly fill you in on how Vista works with XP and with Linux.

***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)


-Mike
(who has a much simpler setup of XP on sda and several Linux distros on sdb,
and who wrote a * very * basic GRUB methods How-To at:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0) )
(read down a ways, to July 17,  to see a summary of that link apcmag)

---

### Post by goodfella on 2007-07-24
The error that you were getting (GRUB error 17) refers to GRUB not being able to mount a parition, so instead of using:

root (hd1,0)

use:

rootnoverify (hd1,0)


The rootnoverify command tells grub not to try and mount the partition.  Hope this helps

---

