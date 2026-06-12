---
title: "Amiga Partition table corrupted at block 0"
date: 2007-11-27
forum: Apple PPC Users
---

### Post by iamdigitalman on 2007-11-27
I have decided to get back in to Ubuntu after my B&W got a revision 2 facelift. It has a 120gb seagate primary hard drive running Mac OS X 10.4.11, quite smoothly. I dug out an old 13.7gb IBM Deskstar with some windows OS on it (not important). I hooked it in to the double drive bracket and set it to slave. I formatted it as MS-DOS in OS X, and it formats fine and popped up on the desktop. I pulled out my 7.04 PPC CD I made some time ago. I booted, and installed ubuntu just fine.

Upon shutting down for a reboot, ubuntu got to the very end where it asks me to remove the disc, close the tray, and press enter. I do, but the machine does not respond. Odd, I thought. So, I give it the three finger salute (command-control-power). Upon booting, I get a very nice "ubuntu first stage bootstrap" screen with x for Mac OS X, l for Linux, and C for CD-ROM. Upon pressing l, or waiting for it to time out, I get the following screen (sorry for not knowing most of it, I took a pic of it on a poor camera and parts of it is unreadable):

Amiga partition table corrupted at block 0
block type is not partition but (some number)
block checksum is bad : (some number)
(boot path, unreadable, ending in yaboot.conf) unknown or corrupt filesystem
Can't open config file
Welcome to yaboot vesion (version number)
Enter 'help' to get some basic useage information
Amiga partition table corrupted at block 0
block type is not partition but (some number)
block checksum is bad : (some number)
boot: _

upon typing in the location of the kernel, it still says it can not boot.

I have tried installing twice now, both with the same result, and the hard drive still formats fine, and Mac OS X still boots fine, even from the first stage ubuntu bootstrap.

any thoughts? My next step is to grab the 7.10 image and try installing that, but I am low on blank CDs and don't want to burn another one until we are sure the CD is the problem.

---

### Post by iamdigitalman on 2008-01-14
Sorry to necro post, I had forgotten about this as well, moving and such means disconnecting the power for a bit, but now that everything is all set back up, and I have a bit of free time, I decided to try it again, and sure enough, I get the same thing after pulling out my 6.10 alternate CD and installing off that.

This is getting frustrating, it's not a bad CD if 2 versions give the same error. It can not be the hard drive, SMART status reads OK, and a surface scan finds no bad blocks.

Any thoughts?

-digital ;)

---

