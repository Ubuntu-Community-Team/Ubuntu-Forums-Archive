---
title: "[SOLVED] Can't install Gutsy from CD's"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by coolbrook on 2007-11-29
I've tried to install using the mailed CD and both burned (4x) Live and Alternate CD's to no avail.

The LiveCD freezes with the orange progress bar.  The Alternate CD it stops at 21% "Retrieving libc6-udeb."  Load installer components from CD fails.

The hashes match in the MD5SUM so the images are OK.

Is there anything else I can try?

---

### Post by irish_flu on 2007-11-29
That's weird.  Consider this a shot in the dark, but is there any chance it's running out of memory?

---

### Post by philinux on 2007-11-29
Can you post your system specs?

---

### Post by coolbrook on 2007-11-29
I have a Gig of RAM so I don't think that's what's happening.  I'm willing to bet it's my hardware.  I'm trying to install it using a Benq DQ60.  I have Feisty installed on the system but I was hoping to do a clean install of Gutsy so I can get it working on my network.

> Can you post your system specs?

Tyan Thunder S2518 LE-T (latest BIOS)
Onboard video (4 or 8 MB)
P3 1.4GHz, 1 GB SDRAM
Benq DQ 60
120GB Seagate Barracuda IDE

---

### Post by erginemr on 2007-11-29
Hello,

Please refer to the following threads and bug report:
[http://ubuntuforums.org/showthread.php?t=52451](http://ubuntuforums.org/showthread.php?t=52451)
[http://ubuntuforums.org/showthread.php?t=82017](http://ubuntuforums.org/showthread.php?t=82017)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/23085](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/23085)

Apparently, the problem originates from some CD/DVD drives, where DMA is not enabled. In one of the threads:
> "The trick was to type the following at the livecd boot prompt
    live cdrom-detect/cdrom_hdparm=-d1"

has been suggested. And in the bug report:
> "Short version: If DMA is disabled (like in ubuntu) it will fail, if DMA is
enabled it will work.
I just bootet rc1 in expert mode and played around a bit and if I do
hdparm -d 1 /dev/hda
after "Check and mount CD drives" when it scans the contents of the disc but
before it starts loading the udeb files it works."

I hope this will help you correct the issue and carry on the installation.

---

### Post by coolbrook on 2007-11-29
> **erginemr said:**
> "The trick was to type the following at the livecd boot prompt
live cdrom-detect/cdrom_hdparm=-d1"

I pressed ESC from the menu and tried this at athe boot: prompt but it didn't work.

---

### Post by ptn107 on 2007-11-29
Upon booting the CDs have you tried the 'Check CD for defects' option from the menu?

---

### Post by coolbrook on 2007-11-29
The CD isn't the problem.  I have 3 Live and 2 Alternates here.  I think the Benq DQ60 is a cousin or new badge for the Benq DW 1640 discussed here... [http://ubuntuforums.org/showthread.php?p=460479](http://ubuntuforums.org/showthread.php?p=460479)

If I get another drive that uses a different chipset then I'm sure that it will work.  I think I understand why people were giving this drive poor reviews a couple of years ago.  I'm not too keen on getting another drive but it's the sacrifice to make.  I could throw it into my Windows machine and try to update the firmware and then put it back in the target machine and try again.  That's the best solution that I can come up with.

---

### Post by coolbrook on 2007-11-29
Well I picked up a new drive and that didn't solve the problem.  Seems my hardware's pretty fussy. Earlier out of frustration I wiped my Feisty installation.  Since then, much to my surprise, I can't install that version either.  I was about to give up for the night just before I found an Edgy Eft CD that I burned and never used.  It's in the process of installing right now.  My fingers are crossed that I can get the wireless to work and perhaps I can upgrade one after another.  I'll post my results.

---

