---
title: "Hardware rivelation trouble"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by S-4-N-D-M-4-N on 2006-01-01
Hi all,
I would like to become an Ubuntu user, but I have a little problem with hardware rilevation: while installing Ubuntu on my celeron 700 Mhz, it freezes during the hardware rilevation (86% exactly while loading the Linux ATAPI CD-ROM) and I cannot resolve it.
Do you know any solution?

TNX all :razz:

---

### Post by az on 2006-01-01
[QUOTE=S-4-N-D-M-4-N]Hi all,
I would like to become an Ubuntu user, but I have a little problem with hardware rilevation: while installing Ubuntu on my celeron 700 Mhz, it freezes during the hardware rilevation (86% exactly while loading the Linux ATAPI CD-ROM) and I cannot resolve it.
Do you know any solution?

TNX all :razz:[/QUOTE]
1.  Check the integrity of the cd by getting out of the menu when you first start the installation.
2.  Try to install again and go to the error console and see what errors are displayed when it freezes.  (CTRL-ALT-F3)

---

### Post by S-4-N-D-M-4-N on 2006-01-01
I did what you said.
The last entry is:
insmod /lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-cd.ko

What does it means?

I'm a linux newbie :???:

---

### Post by az on 2006-01-01
If the cd is not corrupt (you did not mention about checking the cd) you can try looking at the bios settings for the cdrom drive.  Perhaps setting them to the default value if they are not already so.  Depending on your bios, you may try several different settings (DMA on or off, PIO (older hardware) or check to see if there are other devies on that ide channel that are causing the trouble.

---

### Post by S-4-N-D-M-4-N on 2006-01-01
Sorry, the cd is new and not corrupt (the distribution is downloaded from the main site - italian mirror and it's 617 Mb).

I'm trying to install Ubuntu on my Acer Travelmate 210TEV which has a DVD-Rom  device integrated...maybe not supported? :confused:

---

### Post by S-4-N-D-M-4-N on 2006-01-01
Those are the specifications:

 Celeron 700Mhz Processor
13.3" TFT (XGA)Display
128Mb RAM
10Gb Hard Drive
Internal 8xDVD Drive
Internal 3.5" Floppy Disc Drive
Internal 56K V90 Modem
4Mb SGRAM(Video Memory)
2X ATI Rage Mobility-M1 Graphics Accelerator

---

### Post by Mustard on 2006-01-01
[QUOTE=S-4-N-D-M-4-N]Sorry, the cd is new and not corrupt (the distribution is downloaded from the main site - italian mirror and it's 617 Mb).

I'm trying to install Ubuntu on my Acer Travelmate 210TEV which has a DVD-Rom  device integrated...maybe not supported? :confused:[/QUOTE]

Have you done an md5sum check on the ISO you downloaded?  Thats the best way to confirm that the ISO wasn't corrupted during the download.

The md5 hash's for the ISO's should be somewhere on the download page you used.  A freeware md5sum checker can be acquired from a freeware site and then you would run the md5sum check on the ISO and compare the hash.  If they match then the ISO is not corrupted.

---

### Post by S-4-N-D-M-4-N on 2006-01-01
[QUOTE=Mustard]Have you done an md5sum check on the ISO you downloaded?  Thats the best way to confirm that the ISO wasn't corrupted during the download.[/QUOTE]

i tryed but it's not clear if it successed (i wrote md5sum -c ubuntu-5.10-install-i386.iso). I've a checksum, but i don't remember how to view the page with the real checksum (I use firefox last version))...

---

### Post by Mustard on 2006-01-01
[QUOTE=S-4-N-D-M-4-N]i tryed but it's not clear if it successed (i wrote md5sum -c ubuntu-5.10-install-i386.iso). I've a checksum, but i don't remember how to view the page with the real checksum (I use firefox last version))...[/QUOTE]

Does it look like this?

**126751a2dc5528c2f9044d9e4ee36d61**  ubuntu-5.10-install-i386.iso

That is from this site, which is a download mirror listed on the ubuntu download mirrors.
[http://cdn.mirror.garr.it/mirrors/ubuntu-releases/5.10/MD5SUMS](http://cdn.mirror.garr.it/mirrors/ubuntu-releases/5.10/MD5SUMS)

---

### Post by S-4-N-D-M-4-N on 2006-01-01
exactly the same #-o 

I hoped it was wrong...

---

### Post by Mustard on 2006-01-01
[QUOTE=S-4-N-D-M-4-N]exactly the same #-o 

I hoped it was wrong...[/QUOTE]

Ok..well at least you have eliminated that as a possible problem.  That's an important step in troubleshooting the issue, because its not worth going forward until its confirmed one way or the other.

---

### Post by Mustard on 2006-01-01
The next step is to check your BIOS settings as posted earlier I would say.  I would also mention that some of your hardware is going to be troublesome with regards to working with linux.  Internal modems are generally winmodems, which are difficult to impossible to get working on linux.  Also ATI graphics cards can be a problem too.  I would say that once you get it all working via the liveCD, you will find that your going to have to get some new hardware if you want to move on to the stage of actually installing linux on your machine.  Its possible you might get it all working, but its not going to be a straightforward process.

---

### Post by S-4-N-D-M-4-N on 2006-01-01
[QUOTE=Mustard]The next step is to check your BIOS settings as posted earlier I would say.  I would also mention that some of your hardware is going to be troublesome with regards to working with linux.  Internal modems are generally winmodems, which are difficult to impossible to get working on linux.  Also ATI graphics cards can be a problem too.  I would say that once you get it all working via the liveCD, you will find that your going to have to get some new hardware if you want to move on to the stage of actually installing linux on your machine.  Its possible you might get it all working, but its not going to be a straightforward process.[/QUOTE]

I changed the boot sequence so it boots from CD-ROM first and then from Floppy (it was viceversa). I agree that internal hardware "suck" in this case, but even if it doesn't matter for the modem, it's really important for the CD-ROM (which sucks very much :-?  ). 

I wanted to install Linux on that notebook, but it seems unuseless :(
However, TNX for help :)

---

### Post by S-4-N-D-M-4-N on 2006-01-01
New Update: after two hours it successfully completed the hardware detection. Now it's stuck in the CD-ROM Scan sequence (it's not really stuck, but it's very slow...about a 2% every 30 minutes). Is this a good sign or it doesn't mean anything?

---

### Post by Mustard on 2006-01-01
It sounds like its not working very smoothly.  It shouldn't take that long.

---

### Post by frufo on 2006-12-23
I need the boot-option "irqpoll" (without quotes) on startup. Just choose F6 on startup and add irqpoll. This worked fine for dapper drake. Ubuntu 6.10 could be installed as well using this options. Now i have troubles with my Ethernet PC-Card, the WLAN-Card still works fine. However, I am not sure if this is related. I get a lot of messages like:

Calling INT0x1A (F000:FE6E)
EAX is 0xB102

and:

IRQ 15 nobody cared (try booting with the irqpoll option)

although Iam using this option. The System freezes quite often. This did not happen just after the install. I suspect that a kernel-update caused this (currently 2.6.17-10). Thus you might be better off using Dapper Drake (even having long term support) for the 210TEV. Apart from the irqpoll boot options worked well. However the internal Win-Modem does not work and the  ACPI-implemtation of the bios seems to be broken (no suspend).

Frufo

---

### Post by LDRoamer on 2006-12-23
I recall reading  the live cd needs 256 mb of ram.  There is an alternate cd that doesn't require as much ram. I don't think it uses a graphical installer.  I have not used it so I don't know much about it.

> **S-4-N-D-M-4-N said:**
> Those are the specifications:

 Celeron 700Mhz Processor
13.3" TFT (XGA)Display
128Mb RAM
10Gb Hard Drive
Internal 8xDVD Drive
Internal 3.5" Floppy Disc Drive
Internal 56K V90 Modem
4Mb SGRAM(Video Memory)
2X ATI Rage Mobility-M1 Graphics Accelerator

---

