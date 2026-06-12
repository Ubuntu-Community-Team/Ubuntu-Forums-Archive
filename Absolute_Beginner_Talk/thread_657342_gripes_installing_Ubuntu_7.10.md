---
title: "gripes installing Ubuntu 7.10"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by mrodent on 2008-01-03
I tried to install a dual boot on my laptop which already had WXP on it.  The partition configuration was approximately as follows: 

Primary partition
	C: 30 GB NTFS

Extended partition
D: 22 GB NTFS 
E: 22 GB FAT 32
20 GB Healthy
20 GB Healthy

The pimary partition had about 9 GB free.  I had previously installed Ubuntu in a WXP dual-boot on my "secondary" machine, letting Ubuntu install itself in a "guided" fashion.  So I did the same this time.

prob 1.
The first problem had to do with the monitor.  This computer is a Dell Inspiron 6400 laptop.  But I usually use it with a separate Iiyama 19" LCD monitor, which is more comfortable to use.  Ubuntu installation was unable to use it: messages flashed up on the monitor: "out of range H 75, V 60" and "try using a resolution of 1280 x 1024".  Eventually Ubuntu gave up, saying it had tried to get the "video server" working 6 times in the past 90 seconds.  So installation stopped.  But Dell/Iiyama is hardly an exotic combo, also couldn't it use some sort of default driver...?

prob 2.
After this I disconnected the monitor, not particulary happy: I much prefer to work with a separate, large monitor.  I tried installing again.  This time disaster struck.  I got as far as the partition arrangements, and trusting soul that I am, opted for "guided" installation.  Ubuntu chose to try to install to the primary partition.  But, I have since concluded, there wasn't enough space: only 9 GB.  So after a long time the installation ground to a halt with the message: "disk full".  This time, as you might have imagined, it had also messed up my WXP opsys!

reinstating WXP
Many many unsuccessful attempts later to "repair" the WXP installation I concluded I had to install a fresh WXP installation... which I duly did, followed by much reconfiguration and reinstallation of various programs and files.

Ubuntu installed
This time, I tried to install Ubuntu again, but manually: for the swap partition and the root partition I chose one of the unformatted 20 GB logical partitions above in the extended partition.  Not really knowing whether this would work: what exactly are primary and logical partitions anyway?  It seems you have can two primary partitions... should I set up a second one, etc. etc.?  Floundering in other words.  But this managed to get Ubuntu installed.  On starting up Ubuntu I also saw that I could, to my surprise, do things to the files in the WXP partitions, even those with NTFS formatting... which I was surprised by: I thought Linux couldn't read NTFS... sda1 seems to correspond to C:, sda5 to D: and sda6 to E:.

Things start to change worryingly
I have just logged on to Ubuntu again, and now it is impossible to access C: (sda1) or D: (sda5)... which makes sense because these are the two NTFS partitions.  I can now only access E: (sda6), which is FAT32 formatted.  But why the change?

Can anyone explain to me:
- how I can find and install a driver or sthg to use the monitor?
- why I should have been able initially to access the NTFS WXP partitions... but not now?
- how come the Ubuntu installer is not clever enough to spot that a partition is filling up and stop before it totally messes up an existing opsys?  Isn't this pretty basic stuff that you would want built in to the installer program?
- it also took me a long time to work out how I make WXP the default opsys in the grub loader... using gedit with "sudo" so you have administrator privileges, negotiating to the appropriate file, working out what to change, and how to change it.

In short, I have to say that my initial experience of Ubuntu/Linux is not much more user-friendly than it was a few years ago when I got totally confused and frazzled with another Linux distro.  These basic obstacles, particularly the fact that my WXP opsys was damaged beyond repair with no warning, and the extremely steep learning curve to accomplish the basic step of making WXP the default opsys at start-up, are pretty unforgiveable.  Can't these things be improved?

---

### Post by threetimes on 2008-01-03
1. try the vesa driver
2. ubuntu cant write to a ntfs partition anyway
3. 9GB is more than enough for 2 installations
4. read [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu) , the explain everything

"what exactly are primary and logical partitions anyway?"
A primary partition is a "normal" partition, you can have max 4 of them on 1 hdd.
A extended partition is a "container" for partitions, so you can have more than 4 partitions.
A logical partition is a partition inside a extended partition. You cannot boot from a logical partition afaik.

**Edit:** I ran an complete web server on a pc with just 6 gb space using ubuntu server 6.10, and i had plenty empty space.

---

### Post by kestrel1 on 2008-01-03
You can have up to four primary partitions on one HDD, but if you wanted four & a extended you couldn't do it. Three Primary & one extended, as many logical in the extended as you want etc.
ntfs support has been available in Linux for a while now.
To configure your two displays go to System - Administration - Screens & Graphics. You may get it sorted there.
As for the grub configuration install StartupManager:
```
sudo apt-get install startupmanager
```
Then you can configure your startup by going in to System - Administration - Startup-Manager

---

### Post by mrodent on 2008-01-04
thanks to you both!

---

