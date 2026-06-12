---
title: "How to install with a non-bootable CD?"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by OldDogNewTricks on 2006-12-11
I have two PCs operating well using Edgy Eft.  Networked together, and working well with my Windows laptop.  Now I'm trying to expand my horizons a bit.

I have an old Windows 95 machine I want to use for experimenting with IP masquerading.  It has a CD drive, but the bios has no provision for booting from the CD drive.

My understanding of how to successfully load Ubuntu onto this machine is a bit fuzzy.  I think I need to boot in Windows 95, load the Ubuntu CD's contents into a folder on the HDD, and then somehow boot with a GRUB floppy that points to that folder.  As you can see, I really don't know how to go about loading Ubuntu without a bootable-CD option in the bios.

Can someone point me in the right direction?  I've googled the problem, but I get loads of howtos on making a bootable GRUB floppy, which doesn't tell me how to point GRUB to the CD drive -- or if that is even a viable option.

---

### Post by seshomaru samma on 2006-12-12
Did you try [this]("http://sourceforge.net/projects/btmgr/") or [this]("http://www.bcdwb.de/bcdw/index_e.htm")?

---

### Post by OldDogNewTricks on 2006-12-12
The first URL you referred me to presumes that the operating system is already installed on one's hard drive, and the floppy is used to repair a damaged GRUB.  This is not my situation, as I still need to get the OS installed to the HDD, but my bios will not allow the CD drive to be the boot drive.

The second URL describes how to make a multi-boot CD.  Since my bios does not support booting from a CD, this won't help me either.

What I need -- and I don't know if it is even possible -- is a boot floppy that starts enough of the boot process to make the CD drive active, and then directs the rest of the boot process to proceed on the (now active) CD.

---

### Post by donniebnyc on 2006-12-13
Use [MagicIso]("http://www.magiciso.com") to write the file sbm.bin to a clean floppy.  The file is on the cd in the install directory.  Boot with the floppy, then highlight the cd drive.  Press Tab to get the main menu select Boot It and press Enter.  I just did this and it works for Dapper Dan.  Good luck.

---

### Post by louieb on 2006-12-13
> **seshomaru samma said:**
> Did you try [this]("http://sourceforge.net/projects/btmgr/") or [this]("http://www.bcdwb.de/bcdw/index_e.htm")?
He has it right with the first one. You have to remember the OS is installed not on the hard drive but on the CD. and a Smart Boot Manager  will boot an OS on CD.
Here is my page on how to make the SBM floppy disk 
[Nuts n Boldt's on Smart Boot Manager]("http://louboldt.com/ilinuxsbm.htm")

---

### Post by OldDogNewTricks on 2006-12-13
I installed MagicIso, and it looks like it will do exactly what you say.  However, I run into the problem that smb.bin is 1.47 MB in size, and the 1.44 MB floppy won't accept it.  How did you get around this problem?  I checked back on earlier versions of Ubuntu, and the smb.bin file is still this large.

---

### Post by OldDogNewTricks on 2006-12-13
> **louieb said:**
> He has it right with the first one. You have to remember the OS is installed not on the hard drive but on the CD. and a Smart Boot Manager  will boot an OS on CD.
Here is my page on how to make the SBM floppy disk 
[Nuts n Boldt's on Smart Boot Manager]("http://louboldt.com/ilinuxsbm.htm")

It sure looked like smartboot manager would work, so I tried it.  I downloaded sbootmgr.dsk and rawwritewin.exe.  Then made the floppy.  Installed floppy and live CD in computer and rebooted.  Floppy came up with boot options, including booting from the CD.  I chose the boot from CD option and hit enter.  Immediately got the error message: (Disk Error: 0xAA)

I'm a really newbie at this stuff, so my guesses may be way out in left field.  Nonetheless, I need to try to understand what is happening.  I currently think that because the built in bios doesn't know how to initialize the CD, it isn't, and the smartboot manager is assuming that the CD is active when it isn't.  But what do I know?

Any more suggestions?

---

### Post by seshomaru samma on 2006-12-14
[This?]("https://help.ubuntu.com/community/Installation/FromWindows")

---

### Post by macogw on 2006-12-14
honestly, i'd just shove the hard drive into another computer, install the OS, and shove it back into the one you want it to be in.

---

### Post by dmizer on 2006-12-14
i'm with macogw.  you'll most likely have to reconfigure your xserver (dpkg-reconfigure xserver-xorg) but beyond that it should work.  and even if the 95 machine is a laptop, the hard drive is most likely very accessable.

much less headache, and much less potential for show stopping screw ups.

just make sure all  your other hard drives are disconnected.

---

### Post by louieb on 2006-12-14
> **OldDogNewTricks said:**
> Floppy came up with boot options, including booting from the CD.  I chose the boot from CD option and hit enter.  Immediately got the error message: (Disk Error: 0xAA)
Any more suggestions?
 
Yea SMB will do that. I just ignore it and press enter again. Sometimes I have to press enter 3 or 4 times before the PC boots to the CD. (one of my PC's is an old P1 that came  originally with  Win95 on it)
Try that and let me know.

---

