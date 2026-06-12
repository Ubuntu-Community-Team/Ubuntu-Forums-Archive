---
title: "After unbuntu installs, Windows still boots (no grub menu)"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by beatmasterbee on 2006-08-13
Hi,

I am dual-booting Windows and Ubuntu.  I have just installed Unbuntu and after a reboot my pc just goes straight to the Windows startup screen...there is no grub menu.

I tried booting the live cd and reinstalling grub as suggested here: [http://ubuntuforums.org/showthread.php?t=224351&highlight=howto+install+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=howto+install+grub)

but to no avail?

Im a bit of a linux noob so be gentle.  

I have a few HDD's in a SATA RAID if that helps?

Thanks for any suggestions in advance.

btw..Ive already installed Ubuntu on my laptop and Im a convert.  Im getting off Windows as fast as I can.

---

### Post by catlett on 2006-08-13
If I had to guess, grub is probably installed but not to the mbr of the booting hard drive. Grub in Ubuntu has been having alot of issues with sata. With sata's the issue has been grub installing to a partition or slave drive instead of to the mbr of the master.
I do not hAve a sata setup so I do not have any experience.
You could install the ext2 driver for windows and look at your linux partitions to see if grub is installed somewhere. [http://www.fs-driver.org/](http://www.fs-driver.org/)
You could use the grub super disk [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html) That page is written by Herman (he is the one who wrote the definitive ubuntu dual boot guide [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) ) I haven't used the disk but if Herman is touting it then it must be good tool.
There is also one more thing. GAG [http://gag.sourceforge.net/](http://gag.sourceforge.net/) this is another bootloader. It is a small download. After download burn the iso to cd. It boots to a menu with options to boot to whatever OSs it sees. You might get lucky with GAG and it sees both.
Sorry I do not have more info.

---

### Post by beatmasterbee on 2006-08-13
"Sorry I do not have more info."

Mate...thats a lot of info and I really appreciate it.  I'll give them a try and let you know.

Thanks again.

---

### Post by thoffland on 2006-08-13
I would like to know if you were successfull getting it to work. I've just installed Ubuntu on a 2nd Sata drive but have to keep one unplugged in order to boot. I am going to try GAG too, but would like to know how you made out.

---

### Post by beatmasterbee on 2006-08-13
Well after using SGD, the Grub loader came up, but when I chose Ubuntu, I got an error saying root (hd1,1) Error 22: No such partition and now my Windows NTLDR is also corrupted.  I have to load Windows now using SGD to boot up.

I can fix NTLDR easily but I'm still stuck with the same issue of not being able to load into Ubuntu at all.

Im thinking of just installing Unbuntu on a different SATA drive.

If you have Unbuntu and Windows on different SATA drives, how do you tell your PC which OS to load on startup?

---

### Post by sean_ on 2006-08-13
Lol, you just destroyed your PC, nice. Reinstall Windows, then install Ubuntu

---

### Post by catlett on 2006-08-13
Your pc is not destroyed. Sata is very "buggy" in Ubuntu. I just want to clarify, you have 2 sata drives correct? No ide drives.

Did you try GAG?

Did you use the ext2 driver and check your linux partitions for a boot folder with a grub folder in it?
If you get into the linux partition and /bbot/grub is there, post the contents of device.map. This is the list of devices grub sees. Just curious if both your drives are detected. 

Do you know what partition ubuntu is on? Right now grub thinks it is on (hd1,1) which means the second hard drive's second partition. Is that where  ubuntu is?
To check where it is you can use windows to search the drive or you can get to the grub menu and enter C. This gives you the grub shell. Enter find /boot/grub/stage1  Is that partition (hd1,1) ?


You might want to browse this thread just for reference [http://www.ubuntuforums.org/showthread.php?t=229909&highlight=sata+dual+boot](http://www.ubuntuforums.org/showthread.php?t=229909&highlight=sata+dual+boot)

This is a how to for using ntdlr for booting ubuntu but it needs grub to be installed. [http://www.ubuntuforums.org/showthread.php?t=208951](http://www.ubuntuforums.org/showthread.php?t=208951)
n?

---

### Post by beatmasterbee on 2006-08-13
Yeah I know its not destroyed.  If worse comes to worse, I'll just repair windows and reinstall Ubuntu.

Ill try the GAG and get back to you.

Cheers

---

### Post by thoffland on 2006-08-14
I have 2 sata drives, one with Windows XP already loaded onto it. I tried loading Ubuntu on the other one without any luck getting a dual boot to run properly. I tried with both drives connected, and without the XP drive connected. 

No matter how I install Ubuntu Grub overwrites my MBR for Windows and I cant boot to either system but if I unplug the Windows drive, then I can boot Ubuntu. I can format /mbr the windows disk and get back into it, but after doing that, then I cannot boot Ubuntu at all. 

I'll keep trying but I'm thinking about just trying a RAID 0 with Ubuntu and running Windows with VM Server inside it.

---

### Post by catlett on 2006-08-14
> **thoffland said:**
> I have 2 sata drives, one with Windows XP already loaded onto it. I tried loading Ubuntu on the other one without any luck getting a dual boot to run properly. I tried with both drives connected, and without the XP drive connected. 

No matter how I install Ubuntu Grub overwrites my MBR for Windows and I cant boot to either system but if I unplug the Windows drive, then I can boot Ubuntu. I can format /mbr the windows disk and get back into it, but after doing that, then I cannot boot Ubuntu at all. 

I'll keep trying but I'm thinking about just trying a RAID 0 with Ubuntu and running Windows with VM Server inside it.

There is a way to boot linux with ntdlr but I have never done it. Just in case your interested here are 2  HowTos [http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why](http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why)
[http://www.ubuntuforums.org/showthread.php?t=208951](http://www.ubuntuforums.org/showthread.php?t=208951)

This is an in depth page on ntdlr [http://www.tburke.net/info/ntldr/ntldr_hacking_guide.htm](http://www.tburke.net/info/ntldr/ntldr_hacking_guide.htm)

---

