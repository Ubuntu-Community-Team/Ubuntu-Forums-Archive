---
title: "Problem with partitioning when installing 6.06LTS"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by cspivack on 2007-02-11
I was running the installation, when I got to the partitioning of my hard drive. It reduced the size of my main drive, and I created a new one for Ubuntu. It worked fine, but next there was the part with mounting drives (?). It looked fine, so I hit next, but it said that "/" was too small, only 8 MB when it needed 2253 MB. I was confused because free space had previously been 8 MB, so I went back to check on the partition. The drive was back to its original size (144 GB, back from 130), as if I hadn't done anything, except now it was "Unknown". I couldn't resize it, so I tried to reboot and go back to Windows to check the disk, hopefully to make it work again, but Windows wouldn't start up. I just got a message saying "Bad PBR". I downloaded Super Grub Disk, because a friend told me that it could recover it. I tried running it from a flash drive, no go, so I wanted to burn it to a disc, but I can't eject the Ubuntu boot disc. Is there anyway to recover Windows, or at least install Ubuntu without erasing my hard drive to do so?

---

### Post by housam on 2007-02-11
Insert windows installation cd and fix the MBR through the recovery console. OR
Boot from ubuntu live cd , then go for system >> admin. >> Gnome partition editor .
use this partitioning tool to resize the windows partition and create 2 new partitions : one for the root ( / ) ext3 format and the other is swap format ( 1 Gb ) for the swap partition.
then proceed installing ubuntu.

---

### Post by cspivack on 2007-02-11
I should have mentioned this before, I don't have the Windows installation cd, my computer was bought with Windows XP Media Center Edition pre-installed. Also, I can't resize the Windows partition, it won't allow me to, because the filesystem is unknown.

---

