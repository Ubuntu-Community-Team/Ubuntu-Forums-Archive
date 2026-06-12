---
title: "Confusion installing Ubuntu on a USB external HD"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by arcooke on 2007-06-23
Hi guys.. I finally got my liveCD up and running for the first time ever (I'm excited!)

I'm trying to install Ubuntu on a new external USB2.0 hard drive but I'm having some trouble.  I attached a screenshot of where I'm at right now.

I just don't know what to do from here.  In the screenshot, I highlighted the drive I intend to install Ubuntu to.  It keep saying "no root file system is defined". It has something to do with the "mount point" thing, but I'm not sure what to do there and don't want to screw anything up.

Ideas?

Thanks :popcorn:

---

### Post by eentonig on 2007-06-23
It's quite simple.

During the installation, your external HD is known as the second (or later) disk, since the IDE bus was scanned before the USB devices were added.

After install and while you reboot, you'll need to adapt this as now the USB HD will be known as the first HD in the system.

---

### Post by arcooke on 2007-06-23
Thanks for the quick reply.

If I set the external drive to be the first drive, then set it back after I install ubuntu, will anything break? My windows installation is the primary on this computer (need it for work software)

---

### Post by confused57 on 2007-06-23
> **arcooke said:**
> Thanks for the quick reply.

If I set the external drive to be the first drive, then set it back after I install ubuntu, will anything break? My windows installation is the primary on this computer (need it for work software)
Yes, make sure to set your external hard drive in bios to boot before your internal hard drive...when you are prompted where to install grub, there should be an "Advanced" button that you can type in or select where you want it installed...if /dev/sdb is your external drive, you can enter this, and grub will be installed to the external drive's mbr.

I would recommend that you burn a copy of the Super Grub Disk, before you install Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it might come in handy if you have trouble booting, or need to restore your mbr.

---

### Post by arcooke on 2007-06-23
Thanks again.  Actually.. I just went back a screen (screenshot attached).

If I use the setting in that screenshot, will it just install Ubuntu to my external drive properly? The external drive is the Samsung 40gig which Is selected in the screenshot.

I feel really stupid asking these questions but I don't want to screw anything up as this is my first time to ever use Linux.

---

### Post by confused57 on 2007-06-23
> **arcooke said:**
> Thanks again.  Actually.. I just went back a screen (screenshot attached).

If I use the setting in that screenshot, will it just install Ubuntu to my external drive properly? The external drive is the Samsung 40gig which Is selected in the screenshot.

I feel really stupid asking these questions but I don't want to screw anything up as this is my first time to ever use Linux.
Yes, that should install Ubuntu to your external hard drive...your main concern is not to install grub to your internal hard drive's mbr, you wouldn't be able to boot your internal hard drive with the external drive disconnected.
That's why I'm stressing to set your external hard drive in bios  to boot before your internal hard drive and just to be sure select "/dev/sdb"(or whatever you external hard drive is recognized as by the partitioner) as the location you want grub installed.

Many people make the mistake of installing to an external drive and don't realize that grub is installed to (hd0) by default...this would be the internal hard drive, if it is set to boot before the external hard drive.

If you don't have a Window's install cd(not a recovery cd), you really should burn a copy of the SGD...it's only a 5-7 Mb download & it can restore your Window's IPL to the mbr, if you ever need to.

---

### Post by arcooke on 2007-06-23
Oh, I think I see what you're saying now.. thanks.  I was just a bit confused about what grub was at first.  So grub is something built into the installer?

These are the steps I'm interpreting here:
1. Set my external hard drive to the first boot device in the bios.
2. Start the live CD
3. Start the installation
4. Somewhere along the lines, the installation will ask me about grub?  At which point I make sure it is set to the external drive, which would probably be /dev/sba now.
5. Installation is complete.. set my internal drive back to first boot device to get back into windows, or keep it as is to get into Ubuntu.. until I set up the dual boot stuff.


Is this correct?

---

### Post by confused57 on 2007-06-23
> **arcooke said:**
> Oh, I think I see what you're saying now.. thanks.  I was just a bit confused about what grub was at first.  So grub is something built into the installer?

These are the steps I'm interpreting here:
1. Set my external hard drive to the first boot device in the bios.
2. Start the live CD
3. Start the installation
4. Somewhere along the lines, the installation will ask me about grub?  At which point I make sure it is set to the external drive, which would probably be /dev/sba now.
5. Installation is complete.. set my internal drive back to first boot device to get back into windows, or keep it as is to get into Ubuntu.. until I set up the dual boot stuff.


Is this correct?
You might want to glance over the Mbr & Grub pages on this site:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

It looks like your internal drive is /dev/sda and you external hard drive is /dev/sdb...grub would recognize the drive that it's IPL is installed to the mbr as hard drive (hd0), if you set up your external hard drive to boot first, then your external hd "should" be (hd0) and you internal hd would be (hd1) to grub.
Your plan sounds good, just make a note of how your external hard drive is designated in the partitioner, i.e. /dev/sdb...this is the hard drive that you want to install Grub's IPL to the mbr.

---

