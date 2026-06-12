---
title: "Ubunto on an iMac 1.8 GHz PowerPC G5"
date: 2009-03-25
forum: Apple Hardware Users
---

### Post by Colinwlu on 2009-03-25
Hi.
I have an iMac 1.8 GHz PowerPC G5 running Leopard 10.5.6.  I have a Maxtor firewire drive partitioned with Tiger, Tiger installer & Leopard installer and a large portion for Time Machine.

I cannot get Ubuntu to work.  I've tried re-partioning the internal hard drive (thank god for time machine) with a free space partition at the top, I've added a free space partition to the Maxtor drive but nothing works.  Kubuntu 6.0.6 ppc alternate iso  installs but when I try to run it it can't find the boot loader.  The live version ends up with a blue screen and a mouse pointer that doesn't move.
8.10 & the alternative iso can't find the cdrom and I haven't a clue how to tell it where to look.  It says press Alt f2 & enter ls /dev but that produces so much text it disappears off the top of the screen.
Any help appreciated.:confused:

---

### Post by pxwpxw on 2009-03-25
> **Colinwlu said:**
> Hi.
I have an iMac 1.8 GHz PowerPC G5 running Leopard 10.5.6.  I have a Maxtor firewire drive partitioned with Tiger, Tiger installer & Leopard installer and a large portion for Time Machine.

I cannot get Ubunto work.  I've tried re-partioning the internal hard drive (thank god for time machine) with a free space partition at the top, I've added a free space partition to the Maxtor drive but nothing works.  Kubuntu 6.0.6 ppc alternate iso  installs but when I try to run it it can't find the boot loader.  The live version ends up with a blue screen and a mouse pointer that doesn't move.
8.10 & the alternative iso can't find the cdrom and I haven't a clue how to tell it where to look.  It says press Alt f2 & enter ls /dev but that produces so much text it disappears off the top of the screen.
Any help appreciated.:confused:

Answer to the cdrom problem is at tail end of the ppc faq, top of this forum.
Once installed ubuntu 810 should find the bot loader.

---

### Post by Colinwlu on 2009-03-25
> **pxwpxw said:**
> Answer to the cdrom problem is at tail end of the ppc faq, top of this forum.
Once installed ubuntu 810 should find the bot loader.
I looked up the ppc faq and it said after pressing alt f2 enter modprobe ide-scsi which I did but it didn't like it.

I don't think a G5 has scsi. System profiler shows it as being on an ATA bus.  I tried entering ata but it didn't like that either.

---

### Post by tiresia on 2009-03-25
Your G5 has S-ATA HD's, that Linux detects as SCSI Drives.
You should be able to install Ubuntu on your machine.

---

### Post by Colinwlu on 2009-03-25
> **tiresia said:**
> Your G5 has S-ATA HD's, that Linux detects as SCSI Drives.
You should be able to install Ubuntu on your machine.
8.10 doesn't get as far looking for hard drives.  It's the CDROM it can't detect.  
6.06 installs but when trying to boot Ubuntu, it can't find the Root file system.
I agree I should be able to install, how do I tell my iMac that? :confused:

---

### Post by tiresia on 2009-03-25
The PPC g5 processor is a 64-bit computer. When you start the installer, did you choose a 64bit option? At boot up, hit TAB to see the different kernel you can choose.

---

### Post by Colinwlu on 2009-03-26
I've tried all '64' options available.  It's as though it installs but then doesn't know where to find it.
:confused:

---

### Post by tiresia on 2009-03-26
I don't know, what is wrong. Maybe you can try to install with the LiveCD 8.04 (Hardy). At the yaboot-prompt choose 'live-nosplash-powerpc64'

---

### Post by paul_mcl on 2009-03-26
OP, you need yaboot bootloader on 2-nd partition of your disk. Or a specially prepared kernel with mkvmlinuz. Yaboot is most common option. So, you have two ways: 1) to erase and to repartition; leave about 1 Mb for yaboot as second partition (when you do this, read 'man ybin', 'man yaboot.conf' and/or 'man yabootconfig'), 2) use some (unknown for me) third-party non-free utility designed to repartion disks without reformatting.

---

