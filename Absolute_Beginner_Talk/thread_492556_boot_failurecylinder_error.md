---
title: "boot failure/cylinder error"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Sjohnson009 on 2007-07-04
Ubuntu boots ok from cd, but will not boot from hard drive.  An error message comes up something to the effect that "the cylinder selected is larger than is supported by bios".  The hard drive used has only the ubuntu OS installed and motherboard is brand new, dual core intel.  Hard drive install of Kubuntu booted ok. I re-formatted the drive and re-installed Ubuntu and still have the same error message. Where do I go from here?

SWJ

---

### Post by freebird54 on 2007-07-04
First thing that occurs to me is that you have an oddball setting in your BIOS that doesn't correctly describe your drive.  Is it a large drive?  Do you have extra-large partitions?  Is the drive set for LBA access?  What have you had running on this system before?  Are you perhaps having the boot partition WAY at the end of the disk?

Just some possibilities...

---

### Post by Sjohnson009 on 2007-07-04
The drive is only 30gb, it is partitioned for 15gb.  Note that drive and partition was set up by the program and the same drive had Kubuntu on it and it worked ok. Re-formatted the drive using W/D's drive software before installing Ubuntu after Kubunto. The downloaded install copied to CD ok with no checksum errors.

---

### Post by freebird54 on 2007-07-04
It is possible to get errors of this type on a drive as small as 8Gb if the system thinks it is an (e)ide drive.  In this case, I wonder if the WD format did something strange to the recognition of the drive by the BIOS.

Are you attempting the install on the first 15, or the last?  Is there an error number associated with the message? (what stage, etc).  Did you go for 'use empty space' option when installing?

Not too sure what is happening here!

---

### Post by Sjohnson009 on 2007-07-11
I let the install program use the entire drive. I downloaded 6.06 and tried this version and it does the same thing.  I think I will use another drive and see what happens.  The current drive was working ok, but maybe it has some errors developing.

SWJ

---

### Post by AverySimonsen on 2007-10-22
I too have this problem. I upgraded my feisty to gutsy and so I now have two kernels installed: 2.6.20 and 2.6.22. I can boot the 2.6.20 without problems, but when trying to boot the 2.6.22, I get the same error message as mentioned above.

The verbatim error message is: 

error 18: selected cylinder exceeds maximum supported by bios

My setup is a standard thinkpad T41p with all HDD space dedicated to my ubuntu installation. The BIOS on these machines is a bit of a pain as I have been unable to find any way to view the information held by the BIOS on my HDD.

[Here]("http://ubuntuforums.org/showthread.php?t=585453")  I saw somebody saying that the way to solve this problem is to make a boot partition. Could anybody point me towards a howto on this or perhaps give a few pointers?

---

### Post by Sjohnson009 on 2007-10-22
I did manage to get Ubuntu to install and I think what I did was format the hard drive as a FAT32 rather than NTFS.  Does this make any sense?

Steve Johnson

---

### Post by AverySimonsen on 2007-10-24
I found the solution to my problem [here]("http://ubuntuforums.org/showthread.php?t=33811"). Turns out my problem was caused by my thinkpad bios giving wrong hd-information to the OS on purpose in an attempt to protect the special area on my hdd where an XP installer used to reside (now long gone). Removing the protection of that area in the bios did the trick!

---

