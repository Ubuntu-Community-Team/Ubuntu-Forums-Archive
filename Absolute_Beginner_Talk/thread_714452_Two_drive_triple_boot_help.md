---
title: "Two drive triple boot help?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by commemoratives on 2008-03-03
I have been attempting to perform an install without much success.  Any ideas on how I can get this to work?

I have a primary drive with an XP NTFS boot/primary partiton and a second NTFS data partition and a third FAT32 partiton that I plan to share with my Linux install.

I would like to install Ubuntu and Kubuntu on the second drive using the windows boot manager to point to Grub (if necessary) on the second physical drive.

First, how do I get Ubuntu/Kubuntu to live on the second drive?  Can the swap partition be shared?  The second drive is 60 gigs and I would like to go 60%/40% Ubuntu/Kubuntu.

I have gotten an install to work, but I can't get the windows boot manager to point to the Linux dirve and successfully boot.  I did disable the primary drive and get a clean install, but when I put the primary back online my ubuntu.bin file just leaves the system hanging.

I know I am probably missing something simple here, but any assistance would be appreciated.  My goal is to leave the XP drive pretty much alone and get familiar with Linux before I completely migrate.

<<Edit>>  I forgot to mention that about the only thing I haven't tried is allowing Grub to write to my primary MBR.  I am reluctant to do that right now so i hope there is a solution which will allow me to leave my primary boot drive intact for the moment.

---

### Post by confused57 on 2008-03-03
You could install grub's IPL(Initial Program Loader) to the mbr of the 2nd hard drive:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

You could switch the positions of the hard drives, if they're both IDE or both SATA...or if you're able to boot first to the 2nd hard drive, you really wouldn't need to disconnect or switch drives...if so, set your 2nd hard drive to boot first in bios, before you boot the Ubuntu install cd.  If you really want to be sure grub's IPL is installed to the 2nd hard drive's mbr, click on the "Advanced" button in the lower right portion of the screen(near the end of the install), then type in /dev/sdb(or however your 2nd drive is recognized) instead of the default (hd0).

If you want to try using Windows to boot Ubuntu:
[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

Instead of installing Ubuntu/Kubuntu separately, you may want to just install Ubuntu, then install kubuntu-desktop:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

It would definitely be much easier to use grub to boot Windows, rather than vice-versa.

---

### Post by commemoratives on 2008-03-04
Thanks for the links and suggestions.  It looks like I will be back at it again tonight, but probably with greater success!

I like the ability to run both desktops on one install.  That should streamline my efforts, but how do you kep track of the "native" applications for each version... I guess the "K" nomenclature will cover 90% of that.

I appreciate the help and understanding.  I hope to be to the point soon where I trust Grub on my MBR, but the current install of XP has been on this machine for about 2 years and I am reluctant to wipe it completely right now.

---

### Post by confused57 on 2008-03-04
> **commemoratives said:**
> Thanks for the links and suggestions.  It looks like I will be back at it again tonight, but probably with greater success!

I like the ability to run both desktops on one install.  That should streamline my efforts, but how do you kep track of the "native" applications for each version... I guess the "K" nomenclature will cover 90% of that.

I appreciate the help and understanding.  I hope to be to the point soon where I trust Grub on my MBR, but the current install of XP has been on this machine for about 2 years and I am reluctant to wipe it completely right now.
Even if grub were to overwrite your Windows IPL,  there are various ways to restore your mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
might be a good idea to burn a copy of the Super Grub Disk, it's an excellent utility to have for booting problems

This pretty much explains the Mbr:
[http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)

---

### Post by commemoratives on 2008-03-07
Well, I bit the bullet and put Grub on my MBR and it all worked out fine.  I even installed Ubuntu to my primary drive and had it take up the partition I planned on sharing.  I figure I can resize and open up a shared partition later.

I think I was just getting too stubborn about the configuration I wanted to use and finally decided it was time to get on with it.

I did make an MBR backuo and did a backuo of my windows partition on the second drive though.

Thanks again!

---

### Post by confused57 on 2008-03-07
Glad to help....good job getting your system set up.

---

