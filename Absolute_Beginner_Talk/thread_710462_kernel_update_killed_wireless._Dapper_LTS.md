---
title: "kernel update killed wireless. Dapper LTS"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2008-02-28
Still trying to figure this out... Once I got frustrated with trying to get it working, I decided to upgrade to 7.10. Made it through the partitioning and formating part of installation, THEN discovered that my system won't run it, so there is no earlier kernel to revert to.

Re-installed 6.06 because it is LTS. ):P

I went through every 'bcm43xx' and 'ndiswrapper' thread and how to I could find, and can't make it work... 
One of them led me to a clue:

When I ran lshw, I got: ```
  *-isa UNCLAIMED
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
 
```
Nothing has changed in my hardware, this was caused by the latest kernel update.

I have never messed with "/etc/pcmcia/config.opts" before, except two years ago I looked at it to verify the proper inclusion of my wireless cards information in there. I previously ran "sudo pccardctl ident" and it showed me what it was supposed to. something like:```
 Socket 0:
    product info: " Broadcom Corporation.", "AR5001-0000-0000", "Wireless LAN Reference Card", "00"
    manfid: 0x0271, 0x0012
    function: 6 (network)
Socket 1:
  no product info available
```(The above data is from someone else's post, so we cannot use any of it for my system.) 
Now I get:```
 john@john-laptop:~$ sudo pccardctl ident
Socket 0:
  no product info available
Socket 1:
  no product info available
```Evidently the update made it so the memory on my wireless adapter cannot be read properly by a certain part of my system. (Whatever it may be.) Yet the card seems to be working in every other aspect.

I have no more ideas, so was hoping someone else might have a few!

---

### Post by igknighted on 2008-02-28
For broadcom chips, the newer releases are much better.  Bcm43xx actually works well in Gutsy.  I would start with a fresh install of that (not upgrade).  What failed when you tried before, and did you do a fresh install or an upgrade?

EDIT: If you were using bcm43xx, a kernel update will break it.  You need to move the firmware files from the old /lib/firmware/<kernel_version> folder to the new one.

---

### Post by Papa-san on 2008-02-28
The bcm43xx that came with Dapper didn't work, so I had to go through the 'blacklist' process, and install ndiswrapper. All was working fine until Update Manager prompted the latest kernel update. The moment it was installed and re-boot was complete, wireless quit working. I reverted to an older kernel and all was good until I figured out how to back up my  data so I could upgrade to Gutsy (Using a disk that was mailed to me from Canonical.)

Like I said, we got as far as the formatting step and then through to 15% of the new install process. Six times now, the install stopped at 15%. In another thread, we determined that my system doesn't have the resources needed to install Gutsy with the standard disk. I have ordered the alternate install CD, but it won't be here for several weeks. Until then, I need to get Dapper working again.

I am trying to work through this Guide:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
It has always worked before, but now, it isn't...

---

### Post by Papa-san on 2008-02-29
Wonderfulll...```
GRUB loading stage1.5

Grub loading, please wait...
Error 15
```

---

