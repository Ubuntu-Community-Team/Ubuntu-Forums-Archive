---
title: "(Noob Dual Install) Can I safely use Boot Repair to convert to EFI mode?"
date: 2014-06-08
forum: Apple Hardware Users
---

### Post by NurpDev on 2014-06-08
[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]Noob question here but I want to make sure I don't nuke my dual install. I'm following [these directions]("http://cberner.com/2014/04/20/installing-ubuntu-14-04-on-macbook-pro-retina/") to install an Ubuntu partition on my OS X MBP Retina.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I'm at the part where it says I should use Boot Repair to convert to EFI mode, but if I tick "Separate /boot/efi partition" the option it gives is "sda1." However, to the best of my knowledge that's where I have OS X files. I have Ubuntu files on sda4 (boot loader), sda5 (main partition), and sda6 (swap). However partitions and file systems on mac/linux systems are pretty new to me. I'm a programmer but come from a Windows background...
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I'm worried that proceeding with these instructions is going to do something bad to my OS X partition. Can someone please tell me if this is safe, and ideally help me to understand a bit more what's going on here? I'm new to Linux and would very much appreciate the guidance. Thanks![/FONT][/COLOR][/SIZE]

---

### Post by NurpDev on 2014-06-10
Just bumping this. Would really appreciate any insights here. Thanks all.

---

### Post by oldfred on 2014-06-10
I will move your thread to the Apple sub forum. Those that know Mac may be able to help.

But in general with UEFI, each hard drive has one efi partition for every systems efi boot files. 
Issues with Mac are related to Apple using an old version of UEFI and Windows & Ubuntu using a newer version of UEFI.

Always a good idea to backup. So if concerned make a full backup of your efi partition.

Some links that may be helpful, but I do not know much about a Mac.
 [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

---

