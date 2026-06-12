---
title: "Distro's burned with a PC don't work?"
date: 2008-10-22
forum: Apple Hardware Users
---

### Post by CyyberSpaceCowboy on 2008-10-22
I have a few retired academic PPC Mac's and I'd like to try a Linux distro on one.  My test system is a G3 iMac with 512Mb SD-RAM.  I've tried every single CD Live PPC distro on PeguinPPC.org and if they boot at all (Ubuntu for PPC was not recognized as a boot disk), they lock on file read errors before I get to the desktop or before the installation completes. 

Do I need to burn my images on a Mac rather than a PC?  I know there are differences between the firmware in Mac and PC optical drives because while you can replace a dead Mac optical drive with an IDE drive from a PC, you can't boot an OS X install disk from one and PC burners are not recognized as such.  I've also found I can't make a working backup of an OS X CD on a Windows machine.

I've tried burning my Linux install CD's with both an XP machine and an Intel PC running KB3 under Hardy.  I've also tried installing Linux on a G3 tower with similar results, so I don't think it is hardware on the target machine.

If it turns out ISO's burned under a different architecture should work, I can  go back and post the errors I get for a particular distro, if someone wan't to help me troubleshoot.

---

### Post by tiresia on 2008-10-22
- If you still have a MacOS (9 or X) use Apple Disk Utility to burn your iso images
- Reset the PRAM/VRAM (cmd+opt+P+R) at boot up. Remove extra cards (usb, grafic cards)

How are you burning the iso images on Ubuntu? Are you doing it as root?
You say, you can't boot. Do you get to yaboot, or what do you see at booting?

---

### Post by mfox on 2008-10-22
I don't think the issue is the machine you are burning the CD in.  Awhile back I tried installing Ubuntu on a PowerMac G3 minitower and I had a lot of difficulty with it.  In the end, I got it to work with Ubuntu 6.06 LTS that was downloaded and burnt on a PC running winxp pro.  However, you may be having issues with either an old CD burner or your method of installation.  Remembering that I did this a long time ago, I recall having to use the program BootX 1.2 to get everything to work.  I may have had to install this program first and then use it to boot the installation CD.  Sorry if I can't be more definite.

---

### Post by tiresia on 2008-10-22
> **mfox said:**
>  I recall having to use the program BootX 1.2 to get everything to work.  I may have had to install this program first and then use it to boot the installation CD.  Sorry if I can't be more definite.

You need BootX to boot the kernel in OldWorld Rom Mac. An iMac is NewWorld Rom Mac (Yaboot is the bootloader for it). 
The Beige G3 is OldWorld, a B&W G3 is NewWorld

---

### Post by CyyberSpaceCowboy on 2008-10-22
Tiresia,

Thanks for suggesting clearing the NV RAM (I remember seeing that before).  I retried my distros and Ubuntu 6.10 PPC Alternate made it all the way through, but after i reboot I get past Yaboot, then I get "failed to start the xserver".  I'll try to troubleshoot this myself before asking for more help.  Thanks

---

### Post by tiresia on 2008-10-22
If you have problems with X, maybe this thread can help you
[http://ubuntuforums.org/showthread.php?t=190131](http://ubuntuforums.org/showthread.php?t=190131)

---

### Post by stream303 on 2008-10-27
Remember to burn release images very slowly for those older Macs - even if you are using a pc to burn it with.  Ridiculously slow 1X or 2X are sometimes needed.

---

