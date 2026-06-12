---
title: "Install to new 80GB HD in an iMac 266"
date: 2006-04-21
forum: Apple PPC Users
---

### Post by iMacUser on 2006-04-21
I have an iMac 266 with the original 6GB HD partitioned with both Mac OS 8.6 and Kubuntu 5.10 installed and successfully dual booting.  The iMac has 288MB of RAM installed.
As this HD is getting rather full, what I would like to do is replace the HD with a new 80GB HD, then install both Mac OS 8.6 and Kubuntu to partitions on the drive.
So far, I have been able to install the 80GB HD into the iMac (jumpers set to Master) and then install Mac OS 8.6 from CD-ROM, including partitioning the drive:
8GB Mac OS
32GB for Mac files storage (formatted as HFS+)
40GB Free Space

Then I attempted to install Kubuntu from the same CD that I used successfully before for the installation to the 6GB HD.  I used guided partitioning to ensure that the 40GB free space was partitioned to give a NewWorld boot partition, 31GB ext3 partition and a 578MB swap partition.
Installation then went fine through "base installation", copying packages to the HD and creation of a user.  When the CD was ejected and the computer rebooted, I got a white screen only.

I have tried the installation several times, even removing all partitions and then trying to install just Kubuntu (no Mac OS), still with the same problem after reboot for the second stage of installation.

Any thoughts...?

---

### Post by Ptero-4 on 2006-04-21
First. Ensure that the boot partition, the MacOS "Startup" partition and the linux root partitions are within the first 8 GB of your new drive.
Second. Ensure that you have manually fixed the video resolution (the earlier iMac G3's had ATI Rage VR or somesuch video card which is quite broken on linux).

---

### Post by Rxke on 2006-04-23
IIRC, that has something to do with max-size on the older machines... As Ptero points out, it would be good to make your (first) Mac partition <8 Gb; (say 7, or even 7.5...)  then following partition 40G Free space, and *then* the 32 GB for the Mac.
During install it will then re-divide that 40 Gb into boot, etc partitions, making sure it is in the first 8GB.

---

### Post by iMacUser on 2006-04-26
Success.  Thanks for your pointer about the partition sizes.  

During installation, I found that the guided partitioning didn't size the Linux and boot partitions within the first 8Gb.  So I manually edited the partition table to ensure that the Mac OS, boot and Linux partitions took <8Gb.

Re: video resolution, luckily the install process correctly identified resolutions that worked (anyway, I checked other threads in this forum for information, incase it didn't work).

---

