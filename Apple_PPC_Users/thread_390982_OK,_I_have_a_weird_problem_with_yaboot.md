---
title: "OK, I have a weird problem with yaboot"
date: 2007-03-22
forum: Apple PPC Users
---

### Post by MJMullinII on 2007-03-22
Alright.

First, let me introduce myself, I'm MJMullinII.  Pleased to meet you all as well.

The problem I am having is with installing Ubuntu 6.10 on my modded Gigabit Ethernet G4 Macintosh.  The computer originally came with dual 450 ghz. G4 processors, but I have since upgraded it with Dual 1 ghz. G4 processors.  The computer, also, originally came with ATA/66 hard drive support for up to 2 hard drives.

In addition to the processor, I have also added a combination ATA133/SATA I PCI card, (information here: [http://www.macsense.com/product/storage/sua-100e.html](http://www.macsense.com/product/storage/sua-100e.html))

Attached to the original ATA/66 port is a single 6GB hard drive.  Attached to the Combo ATA/133/SATA I card are two 128 mb ATA/100 hard (NO SATA drives are currently installed).

When I boot from, either, the Ubuntu PPC Desktop OR Alternative 6.10 CD, the install goes perfectly, whether I'm installing to the 6GB drive (Which Ubuntu reads as /dev/hdb) or one of the 128GB drives (Which Ubuntu reads as /dev/sda(b)).  The Operating System installs fine, but always fails at the stage when it tries to install Yaboot.

Reading these forums, I've come to understand this is not an isolated incident.  However, I haven't heard of a report with a setup like mine, so I'm hopefully my setup is adding some wrinkly the Yaboot installer is becoming confused with an there's an easy fix.

HOWEVER, if there is no way to get yaboot to install correctly during the install, I have another question: How can I manually (again, while booted from the Desktop cd) install yaboot AFTER the install has completed (and the automatic yaboot installer has failed).

I have no problem following instructions, but I can't seem to find any on manually installing yaboot on another device than the one your booted from and, of course, I can't boot from my internal drive UNTIL I get yaboot installed.

Any help I can get would be greatly appreciated.  TIA! :)

---

### Post by grazie on 2007-03-22
Hi MJMullinII,

Welcome to the forum and the PPC Ubuntu World. The Ubuntu installer does have a known problem installing yaboot onto firewire and USB drives. As you have some drives on a PCI card this may be part of the same problem. However, I wouldn't have expected any problems with the 6G drive. Have you tried the installation with the PCI card/drives disconnected? Alternately, you can complete the installation by installing yaboot yourself. It's been described a few times on the forum threads including [here]("http://www.ubuntuforums.org/showthread.php?t=380424") using mkofboot instead of ybin, but I don't remember seeing it being described in the Ubuntu documentation. Also, unless you're completely comfortable with the way yaboot works, I suggest you post the output of 

```
$ sudo mac-fdisk -l
```
from the booted desktop cd and "to be sure to be sure", the contents of /etc/yaboot.conf and /etc/fstab on the hard drive you've installed on.

---

### Post by MJMullinII on 2007-03-24
OK!

I have tinkered and tinkered,...and then tinkered some more.  I have reinstalled AT LEAST 100 times, only to come to the same problem, with yaboot.

I have, however, made a little progress toward, at least, identifying the culprit.  I think my Combo ATA133/SATA I card is unable to be traversed by ofpath (which, BTW, it shows up in firmware as SerialATA+IDE-XRack)  I have tried to manually dictate the OpenFirmware path in yaboot and have also come up empty handed.

What really is throwing my off, however, is the fact the both hard drives attached to the card show up PERFECTLY!  The Live CD AND the Alternative CD, both, see both drives perfectly (the only oddity is that they see them as SCSI drives, but reading these boards leads me to believe that Linux pretty much identifies anything other than ATA drives as SCSI).  This is the bad news.

The good news (!) is that I WAS finally able to get Ubuntu installed on my old G4.  I dusted off an old Adaptec 29160N SCSI card I had laying around and an old Quantum SCSI160 drive and they worked perfectly!  I am a little disheartened at giving up on getting it installed on one of the ATA133 drives, but I figure I can try it again int he future, perhaps after the next Yaboot update.

I feel good having finally having it installed, AND can say already that I like it better than Yellow Dog Linux AND straight Debian (I say straight because I understand Ubuntu is based on Debian).

Well, I be in touch!
Good Day!

---

