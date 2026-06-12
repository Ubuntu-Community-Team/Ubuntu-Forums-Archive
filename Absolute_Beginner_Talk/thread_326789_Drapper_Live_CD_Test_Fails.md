---
title: "Drapper Live CD Test Fails"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Naturally on 2006-12-28
Hi,

I am trying out Drapper from the Live CD. I just bought a new SATA Harddisk and am planning on installing Windows XP SP2 + Drapper. The download I did was for the ISO of 6.06.1 LTS. Checksum verified to be correct. I then used Nero to burn the ISO image into my CD's using an LG DVD Writer. I have had no issues in the past, so I burned at 8X.

After booting from the CD, I tried to perform a CD verification to ensure integrity. The verification went fine for around 15 minutes and my PC suddenly rebooted. I then started the Live CD and it gave me lots of green lines. I then started it in SAFE graphical mode and it worked very well (a little slow to start though). I am now posting from within Drapper.

Is the re-start during the CD self check normal? I am worried that during the install the installer will freeze or cause me issues with the installation. Anything else I can do to ensure a smoother installation?


My PC configuration:
MSI 875p Motherboard
NVidia 6200 256MB RAM Video Card
3 GB RAM
Pentium 4 3.4 GHz
LG DVD Writer
~300 GB in hard disk space (all in NTFS)
Internet through Linksys ADSL Gateway connected through ethernet.


Any issues with my hardware?

---

### Post by OffHand on 2006-12-28
> **Naturally said:**
> Is the re-start during the CD self check normal? 
No this isn't normal.
> **Naturally said:**
> I am worried that during the install the installer will freeze or cause me issues with the installation. Anything else I can do to ensure a smoother installation?You should at least make a backup before install.
> **Naturally said:**
> 
My PC configuration:
MSI 875p Motherboard
NVidia 6200 256MB RAM Video Card
3 GB RAM
Pentium 4 3.4 GHz
LG DVD Writer
~300 GB in hard disk space (all in NTFS)
Internet through Linksys ADSL Gateway connected through ethernet.


Any issues with my hardware?Hard to tell. Best way is to try it. I do not think the issues you have, have anything to do with your hardware.

---

### Post by Naturally on 2006-12-28
Thanks for the quick responce my friend.

I will burn another copy in 4X speed just incase and try again.

Regarding the backup, I have made a backup of all important things to my external USB Hard Disk, so it is not an issue. I also have 3 hard disks at the moment 1 SATA and 2 PATA IDE. I bought a new SATA HD and was planning to unplug all HD out and leave only the new HD for a fresh install of windows XP and Ubuntu.

Will ubuntu have problems if 2 or 3 new hard disks appear after the full installation? will it be difficult to identify the new Hard disks to Ubuntu?

Sorry if the questions are too simple :cool:

---

### Post by OffHand on 2006-12-28
> **Naturally said:**
> Thanks for the quick responce my friend.

I will burn another copy in 4X speed just incase and try again.

Regarding the backup, I have made a backup of all important things to my external USB Hard Disk, so it is not an issue. I also have 3 hard disks at the moment 1 SATA and 2 PATA IDE. I bought a new SATA HD and was planning to unplug all HD out and leave only the new HD for a fresh install of windows XP and Ubuntu.

Will ubuntu have problems if 2 or 3 new hard disks appear after the full installation? will it be difficult to identify the new Hard disks to Ubuntu?

Sorry if the questions are too simple :cool:
Shouldn't be too hard. It's something I have never had to do myself though so I'm not sure. It should be a matter of adding some mount points to the fstab file.

---

### Post by Naturally on 2007-01-01
The CD failed when burned at 8X. I re-burned the same ISO file at 4X (which is the minimum for my drive) and the test suceeded.

Thanks for the help.

---

