---
title: "Hard disk partitioning and GRUB errors"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by Hammock on 2006-07-23
Hi all,

I am very new to the Linux scene, and have been experimenting with Ubuntu on my Dell 700m (80GB HD and 512 MB RAM) using a dual-boot set-up with Windows XP-Home Edition.  Planning to try out the newest Ubuntu version, I deleted my existing Linux partitions using Norton Partition Magic.  I thought that GRUB would just kick me into Windows, and I would be able to install the new Ubuntu back where the old version had sat.

This is not the case.  When I boot up, after the splash screen, GRUB starts up, and gives me an "Error 22" message before hanging.  My BIOS is set up to boot from CD-ROM first, so I tried booting from the Ubuntu 6.06 live/install DVD, as well as the two other installation disks.  Nothing will get me past that GRUB screen.  Even if I take the hard drive out of the boot sequence in BIOS, I still cannot boot from the CD-ROM.

Does anyone have any ideas on how I can solve this problem?  I would like to just install the new Linux, but if there is another work-around I am happy to hear of it.

Thank you!

---

### Post by catlett on 2006-07-23
You have an issue with booting to the cd. Grub is on the mbr so if you get grub, then you are bypassing the cd drive and it is going to the hard drive. 2 things could cause this. 1 your bios has hard drive before your cd drive. 2 your cd's are not bootable.
Are you sure you "burned" the isos to disk?
There are 2 options that can get you into windows. One definate and one that should work.
The issue is, only a small part of grub is on the mbr. The rest is on your ubuntu partition...and you erased your ubuntu partition. Grub will not work.
There is GAG. That is a small iso that you burn to disk or it can be copied to a floppy. It should bet you past grub and into windows.[http://gag.sourceforge.net/](http://gag.sourceforge.net/)
If you have a windows installation disk, you can boot to that and select the recovery mode (you type r at the prompt) Eventually after a couple of prompts get to a command prompt i.e. C:\ enter ```
fixmbr
```

The easiest way for you to solve this, is for you to install ubuntu again. It will re-write grub and give you a dual boot setup like before.
I would double check your bios and double check the cd's you are using before I tries a different way into xp

---

### Post by Hammock on 2006-07-24
Thanks, Catlett.  It looks like your first suggestion has put me back in business.  It turns out that I had merely copied the iso to a DVD, rather than burned it properly.  D'oh!  I am not out of the woods yet, but at least I can get the Live CD working and install everything from here.

Take care!

---

### Post by catlett on 2006-07-24
Glad it was simple. The first time I tried to install linux it was with Mandriva. I couldn't get the install to work. I made copy after copy and even bought a copy for $7 from ebay.
The end result was my cd drive was bad. Go figure? Anyways it cost me a $75 cd/dvd writer and a $7 paypal payment to install a free OS :D 
So at least your error was cost free :-D 
Believe it or not, this error comes up all the time. XP doesn't come with the ability to burn isos. If you didn't get nero or a buring application bundled  with your computer,  "how would you know that it is even an option?"
Anyways, glad it was a simple fix. See you around the forum.

---

