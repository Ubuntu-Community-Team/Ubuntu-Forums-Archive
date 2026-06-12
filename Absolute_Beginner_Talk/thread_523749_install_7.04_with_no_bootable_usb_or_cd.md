---
title: "install 7.04 with no bootable usb or cd"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by The BB on 2007-08-12
**Question**

With only a hard disk and floppy that can be booted from how do I install UBUNTU from the live CD? (Newbie and can't find a Simon Says guide)

**Enviromment**

Have an old IBM 240 laptop, with a virgin DOS partitioned hard disk, and can only boot from floppy disk or the hard disk - no CD or USB support.  Have a USB CD but need to use a boot floppy to load USB support using the following on the floppy:

[Config.sys]
DEVICE=HIMEM.SYS
DEVICE=USBASPI1.SYS
DEVICE=USBCD1.SYS /D:MSCD001

[Autoexec.bat]
LH MSCDEX /D:MSCD001 /L:

Have Ubuntu installed as a dual boot with Windows on a desktop.

Rgds

Bob :(

---

### Post by MenZa on 2007-08-12
Umm, having looked at the Wikipedia page for the ThinkPad series, your laptop seems, really, really, really old ([link](http://en.wikipedia.org/wiki/ThinkPad#Model-specific_information)). Do you recall how old your laptop is, and do you have the specifications of it?

---

### Post by The BB on 2007-08-12
It's not that old - it's state of the arc (well maybe 6/7 years old)

But tiny and ideal to back up the pictures from my camera on until W2K blew up and rather than reinstall that - by copying everything onto the hard drive in an i386 directory and running from there would like to install Ubuntu (or maybe Xubuntu if that is what is needed - though trying Ubuntu first as have donwloaded and installed that on this machine so I know the CD is good).

192MB RAM / 400MHz Celeron / 12GB HDD, external floppy (bootable) / one USB 1.1 connector (non-bootable)

---

### Post by jgrabham on 2007-08-12
Erm, somebody correct me if Im wrong, but cant you take out the Hard drice, and get something which will plug it into the IDE plug of a desktop motherboard.

---

### Post by MenZa on 2007-08-12
> **jgrabham said:**
> Erm, somebody correct me if Im wrong, but cant you take out the Hard drice, and get something which will plug it into the IDE plug of a desktop motherboard.

Possibly, but that sounds like overkill.

Isn't there an Ubuntu netinstaller somewhere? I can't find one in the official download locations, nor can I find any info about it on the Wiki. Can this be true?

---

### Post by The BB on 2007-08-12
jgrabham

Not sure, but I don't want to go down the hardware route; I'd rather find a nice software configurationsolution than buy some kit for a one off, on what is after all an antique and a dabble into Ubuntu - but thanks for the thought.

If I try to run the START.EXE manually I get "This program cannot be run in DOS mode." (boot floppy indicates Windows 95) - likewise with the other .EXE files on the CD

Bob

---

### Post by The BB on 2007-08-12
MenZa

I do have an Ethernet PCMCIA card too (sorry missed that off the antiques list) but no drivers to hand so would have to find and make a boot floppy to support that and then be talked through how to share the Ubuntu desktop sitting beside it - and I though on a cloudy Sunday afternoon this would be a doddle!

---

### Post by klytu on 2007-08-12
> **The BB said:**
> **Question**

With only a hard disk and floppy that can be booted from how do I install UBUNTU from the live CD? (Newbie and can't find a Simon Says guide)

**Enviromment**

Have an old IBM 240 laptop, with a virgin DOS partitioned hard disk, and can only boot from floppy disk or the hard disk - no CD or USB support.  Have a USB CD but need to use a boot floppy to load USB support using the following on the floppy:

[Config.sys]
DEVICE=HIMEM.SYS
DEVICE=USBASPI1.SYS
DEVICE=USBCD1.SYS /D:MSCD001

[Autoexec.bat]
LH MSCDEX /D:MSCD001 /L:

Have Ubuntu installed as a dual boot with Windows on a desktop.

Rgds

Bob :(

Have you looked at [[COLOR="Red"]**_this guide_**[/COLOR]]("https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd")? And, in particular, [[COLOR="Red"]**_this_**[/COLOR]]("https://help.ubuntu.com/community/BootFromUSB")?

---

### Post by fickendichdu on 2007-08-12
Your best solution at this point is to get your USB cd-rom started at the boot section and install that way.  The transfer rates are going to be really slow though since you have 1.1.  With your laptop that old I dont think you have the ability to boot off of a USB stick if you had one.

---

### Post by MenZa on 2007-08-12
> **fickendichdu said:**
> Your best solution at this point is to get your USB cd-rom started at the boot section and install that way.  The transfer rates are going to be really slow though since you have 1.1.  With your laptop that old I dont think you have the ability to boot off of a USB stick if you had one.

Well, the problem here, is that a laptop this old has no optical drives (CD, DVD), but it doesn't have USB support either.

---

### Post by The BB on 2007-08-12
fickendichdu

Sadly yes, and the SBM does not see the CD drive as the USB support is not there for it and the SBM image is not readable...

the thought of fdisking an extra partition and installing Debian bootstrao and then another partition to put 7.04 ISO image on and running that seems very messy and something for another weekend ... just wanted a DOS bootstrap loader!

Bob

---

