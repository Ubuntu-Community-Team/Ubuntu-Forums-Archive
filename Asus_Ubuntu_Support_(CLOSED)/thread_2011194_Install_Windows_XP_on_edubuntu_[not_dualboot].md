---
title: "Install Windows XP on edubuntu [not dualboot]"
date: 2012-06-26
forum: Asus Ubuntu Support (CLOSED)
---

### Post by toolm on 2012-06-26
I'm using edubuntu 12.04 on my Asus Eee PC 900HA laptop. Now I want to delete the edubuntu OS and install XP instead. I don't need edubuntu and XP both [not dual boot]. The laptop doesn't have a CD ROM and I'm using a flash drive for booting and instaling.

I've already made my flash drive bootable with XP following [this tutorial]("http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html#.T-pTQZHpVs5"). Do I have to make any changes before I install XP? Change the partition to NTFS maybe or does the installation does that automaticaly?
When I tried booting from USB to go to edubuntu live mode it gave me a grub error menu. 

BTW I was using edubuntu with no problems at all. It bootet itself etc... And please check the tutorial that I was following and does it make any differences how I make the flash drive XP bootable? Some time ago I also tried with some other applications and I don't know if there's any difference.

---

### Post by oldfred on 2012-06-26
Windows installers will not see Linux partitions. You either have to erase drive or reformat with gparted to NTFS. If formated to NTFS you also have to add the boot flag (active partition in Windows) for Windows to install.

---

### Post by ddarsow on 2012-06-26
use Gparted to remove all partitions.
start with unpartitioned speace.
let Win create its own NTFS partition.
I can not imagone doing that, but to each is own...
some folks just like Windows.
Xp is end of life in early 2014 by the way...
just FYI

---

### Post by toolm on 2012-06-26
> **oldfred said:**
> Windows installers will not see Linux partitions. You either have to erase drive or reformat with gparted to NTFS. If formated to NTFS you also have to add the boot flag (active partition in Windows) for Windows to install.
If I erase the partition do I need to add the boot flag? If so, how do I do that?

And which is the best way to create a linux live usb (so I can go in live mode and erase the partition)

---

### Post by exodus_ on 2012-06-26
Windows will have it's own way of dealing with the disk, so as long as it's clean there should be no reason to add the boot flag.  Simply allow the windows installer to partition your disk, and install like normal.  Sometimes this has not fully worked and I have had to boot from recovery media and manually fix a few things, but this has been rare.

---

### Post by toolm on 2012-06-27
I installed it, loaded it via usb and it was ok (some drivers were missing). Later I tried to boot it without usb and it gave me the "Windows could not start because of a computer disk hardware configuration problem"

I changed the boot priorities to HDD. 
I tried doing some alternatives and in one (I can't remember which one) it gave me the hal.dll file missing error

---

