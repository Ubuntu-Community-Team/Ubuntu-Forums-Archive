---
title: "OS X Disk Image backup clobbers yaboot file"
date: 2005-09-25
forum: Apple PPC Users
---

### Post by anechoic on 2005-09-25
- I partitioned my sons G3 iMac into three parts: [OS X (HFS): 50G], [Ubuntu PPC (ext3): 5G], and [New World part/boot (HFS): 250M]...
- everything installed fine, I was able to dual boot without a problem and everything was working nicely together...yaboot came up and showed three devices to boot from MacOSX, Linux and cdrom
- then I decided to back up the OS X partition onto an external 300G (HFS formatted) drive
- I made a disc image of the OS X partition (at least I thought it was the OS X part and not the entire drive) and stored it onto the 300G external drive using Apple's Disk Utilities...
- I shut down and didn't test anything since it was late and I planned on testing the backup in the morning when...
- my son went to boot into Linux that morning and the yaboot didn't come up at all...i.e., it booted straight into OS X; no yaboot
- I poked around online and found:
- [http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch9.en.shtml](http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch9.en.shtml)
- I read the info on yaboot and did the following:
- I reset NVRAM
- I booted into Open Firmware and tried to boot from the yaboot manually but...
- still no luck
- so I loaded up the live disc of Ubuntu, installed the 'gparted' package and looked at the iMac's drive (cause OS X disc utils UI sucks) and I didn't want to read the unix man on disc utils at that point...
but 'gparted' let me see the entire drive and Linux (ext3) and New World (HFS+) parts as well as the OS X HFS parts were all still there...

by now I am pretty certain that the yaboot got hosed when backing up by making a disk image in OS X...
- I am assuming that when making a backup of the OS X (HFS) partition you need to use something that doesn't try to take over the whole drive -- and possibly clobber the yaboot.conf file in the process...any tips, suggestions, URL's? this would be appreciated...

***my questions are as follows:
- was it OS X Disk Utilities that clobbered the yaboot?
- and how does one fix this running a Live Linux distro...
	- side note: I tried booting using OpenFirmware and none of the parts I entered seemed to work per the instructions on the penguinlinux.org yaboot page

***Conversely, when I rebooted into Linux with the HFS+ formatted backup drive hanging off the iMac the drive came up and I could see all the .dmg backups on it...but when I rebooted into OS X the HFS drive came up as unrecognized...WTF?! 
my next questions are:
- how do I fix this?
- is there a Unix util that can fix this? I have Fink and Darwinports so I can DL it from them...

---

### Post by interrupt on 2005-09-29
Are all your linux files undamaged apart from the boot-loader? (I didn't wade through the whole of your post ;) ) If so, and it's just the boot-loader that has been overwritten, you can use ybin to write another one to the disk's boot partitition. 
Best way to back-up OS X is to clone it to another disk. That way you have a bootable back-up should the unthinkable happen...
check out 
[http://www.bombich.com/software/ccc.html](http://www.bombich.com/software/ccc.html)
here you can download a free utility callled Carbon Copy Cloner – which pretty much does what it says on the tin.
cheers.

---

