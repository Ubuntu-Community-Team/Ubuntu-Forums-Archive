---
title: "[SOLVED] Triple Boot Question"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2008-03-25
Hi all,

First off, this isn't really a Linux question... at all really.
I'm attempting to triple boot OSX86, Win XP, Xubuntu
I currently have Dual boot working fine with XP and Xubuntu

My partitioning is set up as follows
/dev/sda1: ~70 gigs for Xubuntu 7.10 (my main OS)
/dev/sda2&sda5: ~5 gigs for swap
/dev/sda3: ~40 gigs for Win XP
/dev/sda4: ~40 gigs for Mac OSX86 (tried both unallocated, and as FAT32 to be reformatted)

I have been trying to follow the following link for triple booting
[http://cybernet1.blogspot.com/2006/10/how-to-triple-boot-windows-mac-os-x.html](http://cybernet1.blogspot.com/2006/10/how-to-triple-boot-windows-mac-os-x.html)

When I go to install Mac OSX86 (JaS 10.4.8 Intel/AMD SSE2&3 with both patches)
I go into the Disk Utility to attempt to Erase that 40gig FAT32 or unallocated space, in order to make it Mac OS (with Journaling), i believe thats hfs+.  The Disk Utility seems to be unable to make this partition hfs+, it just keeps on erasing to MS-DOS (FAT32) filesystem.  Without being able to get this format correct, I can not procede with the installation.

After more research, after using the Disk Utility, going back into Xubuntu, I realized that the partition was infact allocated as hfs+ filesystem, and that the installer was still not recognizing that partition as being available to install OSX on.

Has anyone attempted this kind of triple boot?  I am currently downloading 2 more iso's to see if maybe one of them will work.

I apologize for anyone who reads this and was looking for answers, this has proven to be a real stumper for me.

thanks for any ideas, I posted this on the insanelymac forum as well, but have not received any responses thus far, and frankly, I know the ppl on this forum could probably help me out.

best regards,
kt

---

### Post by c-ron on 2008-03-25
Hi, FAT32 has a 32 Gig limitation. Start by making that partition smaller than 32 Gigs and follow the instructions you linked to.

---

### Post by kernel tom on 2008-03-25
no it doesn't, only if you are formating the drive with windows

---

### Post by s3a on 2008-03-25
You don't need a 5 gb swap...make it 1 gb...and just install the Mac and XP OSes as usual then install Xubuntu and grub should allow you to choose any of the three OSes and you will have a nice triple boot system. If you have high speed do this now, if not then; wait until Hardy Heron comes out (Xubuntu 8.04) and install that as the last OS.

---

### Post by kernel tom on 2008-03-25
My problem is I can not install Mac OSX, due to the Disk Utility not working, I can not create an hfs+ partition that is visible to the Mac OSX installer.

Sorry for the misunderstanding
-kt

---

### Post by Confuzius on 2008-03-25
Try Parted Magic boot disk
Format as HFS, not +, + is journaled and can cause trouble.
the parted magic site seems down now, but it's a custom build of gparted on a livecd, saved my *** while experimenting with hackintosh.

---

### Post by kernel tom on 2008-03-25
figured out u can use cfdisk from the live cd and that worked, now grubs a problem but this is pretty much solved.

thanks,
kt

---

