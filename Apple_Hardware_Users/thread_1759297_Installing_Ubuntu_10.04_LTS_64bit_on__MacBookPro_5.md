---
title: "Installing Ubuntu 10.04 LTS 64bit on  MacBookPro 5,4"
date: 2011-05-15
forum: Apple Hardware Users
---

### Post by danradu on 2011-05-15
Hi,

I am trying to install Ubuntu 10.04LTS 64bit on a MacBookPro 5,4 running OS X 10.6 in a dual-boot configuration.
I am folowing the instructions at :
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#You%20have%20already%20installed%20Mac%20OSX%20and%20Windows%20Vista,%20now%20to%20install%20Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#You%20have%20already%20installed%20Mac%20OSX%20and%20Windows%20Vista,%20now%20to%20install%20Ubuntu).

I installed rEFIt and rebooted the machine (no Ubuntu installed yet).
I get a rEFIt boot menu with two options : 'Mac  OS X from Macintosh HD' and 'Boot Linux from HD' although no Linux installed yet.
Is this normal ?
If I start the Partitioning Tool I get the folowing info :

Current GPT partition table :
#  Start LBA        End LBA   Type
1            40         409639    Basic Data
2     409640    431294399    Mac OS X HFS+

Current MBR partition table :
# A  Start LBA        End LBA   Type
1               40         409639    0B  FAT32 (CHS)
2 *     409640    431294399    AF  Mac OS X HFS+

Status: Analysis inconclusive, will not touch this disk.
Error: Not Found returned from gptsync.efi

* Hit any key to continue *


What could be the problem ?

Thanks,
dan

---

