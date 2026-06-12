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

### Post by fl1pper on 2005-10-05
[QUOTE=anechoic]
- I am assuming that when making a backup of the OS X (HFS) partition you need to use something that doesn't try to take over the whole drive -- and possibly clobber the yaboot.conf file in the process...any tips, suggestions, URL's? this would be appreciated...
***my questions are as follows:
- was it OS X Disk Utilities that clobbered the yaboot?
- and how does one fix this running a Live Linux distro...
- how do I fix this?
- is there a Unix util that can fix this? I have Fink and Darwinports so I can DL it from them...[/QUOTE]
Well, for starters, when have you ever been able to copy a disk image to an external drive and have it be bootable? Where do you think utilities like BootCD come in handy? I'll tell you: They copy the tiny partition (invisible) that the bootstrap, or OpenFirmware sees first, that's how.
So, No, OS X didn't clobber your yaboot, but when you just copied the internal drive to the external, without using a utility to include all the other invisible partitions (especially the boot partition) you basically "yanked" everything from the drive except what you actually needed to boot from it. And when OS X 'wrote' to the external, it did exactly what you asked it to do, whether you knew it or not, It wrote all of the 'yanked' data, and nothing more.
The easiest way to fix the external and make it bootable is to launch Linux from the internal partition to verify that the external drive even shows up on the desktop, then relaunch from the Linux installer, just as if you were going to write a new OS to the external drive, and follow the installer right through to the area where you do a "manual partition", pick a tiny partition near the top of the free spaces and occupied spaces, and ID that little space as the /boot.
Write the changes to the partition, and then just back your way out of the rest of the install. Shut down. Start up with the Option key down, and you get your graphical representationof all the systems available. You shoould see two penguin icons and the X icon. Choose the penguin from the external, hit <return> and there you go.

---

