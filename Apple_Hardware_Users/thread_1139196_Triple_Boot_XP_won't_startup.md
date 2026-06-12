---
title: "Triple Boot XP won't startup"
date: 2009-04-26
forum: Apple Hardware Users
---

### Post by doublepedaldylan on 2009-04-26
I've googled and searched the Ubuntu Forums, and still can't find anything related close enough.
I currently have this config for my triple boot system:

>disk0s1
efi
>disk0s2
Mac OSX 10.5.6
HFS+ journaled
>disk0s3
Ubuntu 9.04
ext3 journaled
>disk0s4
Windows XP professional
NTFS

Although I enabled rEFIt, it will not boot into it.  The main problem is however, XP will not boot.
It gets to the loading screen, and about 3 seconds in, it flashes what looks like the blue screen of death, and then restarts the computer.

I installed OSX > used bootcamp to create XP partition > installed XP w/ bootcamp tools > created ext partition with gparted > installed Ubuntu 9.04 and ran updates.

I figure I need to do some terminal commands, but I don't know what.  If you could link to the proper thread, or just put the answer here.

Thanks!

---

### Post by cyberdork33 on 2009-04-27
I can't address your problem specifically, but you might have a read through the installation documentation:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by doublepedaldylan on 2009-04-29
> **cyberdork33 said:**
> I can't address your problem specifically, but you might have a read through the installation documentation:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Thanks! Just to provide info for anyone else that had this problem.  
My error was occurring in boot.ini on the WindowsXP C drive.
What was here there was

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

Because my XP partition was on the last partition, it SHOULD have been 4's not 3's:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

Hope that helps someone :)

---

### Post by cyberdork33 on 2009-04-30
Yes, Windows often complains if you change the partition layout after it has been installed.

---

### Post by cruizbugs on 2009-06-08
Hi, is there anyone knows how to modify the boot.ini file ?? 
I have the same problem in triple boot here. my windows XP just wont restart

---

