---
title: "How to boot the Ubuntu partition of a dual boot (Windows XP) machine?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by bendm on 2007-12-30
Hi all,

I have an old Sony running Windows XP. The XP install is very slow, too slow to be useful anymore. I decided to see if I could turn this into a dual-boot machine rather than wipe XP off, just to be certain I could successfully install before losing the old OS.

I believe I have successfully installed Ubuntu 7.10 on a non-bootable partition.

There are four partitions of a single hard drive.
C: NTFS
D: NTFS
/ ext3
/swap

The C: drive is the XP boot drive. It came with the D: drive partitioned by the OEM / Sony.

If I use GPartition to set the "/" drive with a boot flag, the boot flag disappears from the C: drive and the machine refuses to boot anything from the hard drives. The screen is black and the words, "Press any key to reboot" appear. 

If I then use GPartition (from the Live CD) reset the boot flag onto the C: drive, Windows XP loads at boot. There is no opportunity during the boot process to select Ubuntu.

If I use the Ubuntu i386 CD that installed the system, I can't find the boot options to mount the "/" drive instead of the CD.

Any suggestions how I can verify that the hard drive's Ubuntu installation works without compromising the Windows XP install?

Thank you very much for your assistance.

Ben

---

### Post by bone2006 on 2007-12-30
You either supergrub or I believe the ubuntu liveCD can get you into the ubuntu by selecting boot from the first HD.  You need to repair grub (the bootloader), grub allows you to boot both your windows and XP.  Ubuntu takes care of all of this for you, you really didn't even need to use gparted unless you wanted another partition, but ubuntu during installation allows you to do a non-destructive repartition and the grub bootloader would have worked just fine.  Messing with the flag is probably want did it and then you want back to microsoft's mbr system which doesn't play with Linux well.

---

### Post by bendm on 2007-12-30
Thanks Bone2006,

I'm not sure I know how to fix the grub. During install the automatic / guided partition didn't work so I had to partition manually. Upon install, the system booted straight to XP and not Ubuntu, so I found some documentation that recommended changing the boot flag in GPartition. Hence I found myself monkeying with boot flags, and not with grub.

"Boot from the first HD" also boots to XP.

Is there a manual on Supergrub or how to repair grub? I'd be happy to read up on the web if possible.

Ben

---

### Post by ericlusk on 2007-12-30
Have you checked in windows xp? there is an option to choose how long before xp boots for multiple operating systems. It is under system properties, advanced, and then startup and recovery settings.

---

### Post by bendm on 2007-12-30
Hi Erik,

Thanks for the quick reply.

I looked in the Windows XP System Control Panel for Startup and recovery. The box "time to display multiple operating systems is checked, and lists 30 seconds as the time to display.

At boot time there is no 30-second wait before Windows XP boots itself. There is the standard multi-user login screen for Windows XP.

Here is the text of the boot file.

[INDENT] 
[boot loader]
timeout =30
default multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=OptIn
[/INDENT]

Is there online documentation for the boot file somewhere?

Ben

---

### Post by bone2006 on 2008-01-02
Supergrub has a liveCD that I would try it.  The documentation is here [http://supergrub.forjamari.linex.org/?section=documentation](http://supergrub.forjamari.linex.org/?section=documentation)

I think if you pop in the CD and just answer the questions you can probably figure out how to repair grub.

The "Windows XP System Control Panel for Startup and recovery." section has nothing to do with it.   The boot loader cannot be used by XP.  Microsoft does not give you the flexibility in Windows XP to boot Windows or Linux, you have to use another boot loader, therefore you  have to get grub installed.


If your still having a problem I'd try removing all the spare HDs in your system.  Then I would reinstall it, putting it back on the same place and see if grub plays alright.

---

### Post by bendm on 2008-01-02
Hi Bone2006,

Thanks for your help with this. I should have closed this out a couple of days ago. Turns out I had been too stingy with partition space and the installation had not completed properly. I gave Ubuntu 10GB plus 2GB swap and then reinstalled.

Smooth sailing from there--but I have a lot to learn about package management, configuration, and Linux software in general. I am learning slowly but the process has given me great respect for serious hackers. I hope I didn't waste your time on this Supergrub problem.

Happy new year.

Ben

---

### Post by jken146 on 2008-01-02
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by bone2006 on 2008-01-03
Just glad to hear you got it working.  I wouldn't have suspected that not having enough space would allow you to do a complete installation and have the boot loader not work.  Seems like a bug personally.  I think if the size isn't large enough for installation that you should be warned, instead of having to go through what you went through.   Maybe check to see if there's a bug issue if not, it would help to report one if you believe that something like this should be fixed so that others don't have to go through the same pain you went through

---

