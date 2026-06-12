---
title: "Hard Drive not found - !please read more than just the title!"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Otisgoad on 2007-10-25
The drive is detected by both the Motherboard BIOS and the SCSI card BIOS. It is formated in NTFS. Windows sees it and i am able to use it in windows with no problem. Now that that is said i am trying to install Ubuntu 7.10 on the mentioned hard drive but Ubuntu does not detect it. it detects the other drive on the card and all the rest of the drives in the computer. I am new to Linux and do not know the terminal commands. i typed in "sudo lshw | less" and this is the output for the scsi device i am using for the drive in question:

*-scsi
description: SCSI storage controller
product: AIC-7892B U160/m
vendor: Adaptec
physical id: c
bus info: pci@0000:02:0c.0
logical name: scsi4
version: 02
width: 64 bits
clock: 66MHz
capabilities: scsi pm bus_master cap_list scsi-host
configuration: driver=aic7xxx latency=64 maxlatency=25 mingnt=40 module=aic7xxx
*-disk
description: SCSI Disk
product: ATLAS10K3_18_WLS
vendor: QUANTUM
physical id: 0.1.0
bus info: scsi@4:0.1.0
logical name: /dev/sde
version: 020K
serial: 342124551905
size: 17GB
capacity: 17GB
capabilities: 10000rpm partitioned partitioned:dos
configuration: ansiversion=3
*-volume
description: HPFS/NTFS partition
physical id: 1
bus info: scsi@4:0.1.0,1
logical name: /dev/sde1
capacity: 17GB
capabilities: primary bootable


the drive listed is the one that the windows OS is on but the one i want to use is not there. it is the same brand and similar model but a 9 gig.
the rest of the drives are listed too but i didnt think it was important. please help. Thanks for telling me more than "Make sure is recognized by BIOS first. (and make sure is formatted)" like the last guy to offer up his wisdom...

---

### Post by H3retic on 2007-10-25
Places > Computer > whatever hard drive you want

That's what I do anyway.  I don't know how to mount it from logon.

---

### Post by ed-koala on 2007-10-25
A couple of questions ... you say Linux doesn't see the drive .. have you already installed Ubuntu or are you using the live CD?

Is the 9 gig drive Windows formatted already?

Just trying to get a bit more specific info to see what's what  :)

---

### Post by MegaJim on 2007-10-25
Searching for that scsi chip reveals a few linux problems both on this forum and the net.  I would post this to the hardware forum where you're more likely to get the help you need.

As a stop-gap measure, you could try removing the rest of your hard drives to see if ubuntu will detect them in a less complicated situation.

You could also try using [http://kmuto.jp/debian/hcl/index.cgi](http://kmuto.jp/debian/hcl/index.cgi)

---

### Post by Otisgoad on 2007-10-25
Hello,
Thanks for the reply!
i am running it from the live CD so far because i want to install it onto the drive in question. and it is formatted in NTFS by windows XP.
Otis

---

### Post by Otisgoad on 2007-10-25
Good idea! Thanks. i will try it
Otis

---

