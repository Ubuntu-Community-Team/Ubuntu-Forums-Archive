---
title: "Noob needing install help"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Lord_Pyro on 2007-11-29
I just found kubuntu recently and decided to install.  I am currently running a very customized version of XP.   i know what i am doing in widows more than the average user but am no leet, however when it comes to linux i am a complete noob.

I have not been able to get the live cd to load to a desk top.  After passing the Kubuntu loading screen all i get is a series of codes that I don't understand.  I have yet to see the desktop from install or live boot.

**my system: (custom built)**
AMD Athlon 1ghz
2gb pc 3200 ram
30gb western digital hd w 11gb free (am planning on partitioning 8gb for linux)
wireless pci card (dlink 802.11b)
nvidea 128mb graphics card
soundcard on motherboard

**some of the error codes i'm getting:**
Buffer I/O error on device sda Logical block 0

ata1.00: exception Emask 0xosAct 0x0 Serr action 0x2 frozen

ata1.00:cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag ag0cdb 0x0 data4096in

Buffer I/O error on device Fd0 Logical Clock 0

**What ive done so far:**
checksum my iso (Kubuntu 7.10) [from windows xp, can't get checksum on the disk to run]

 tried downloads from multiple mirrors

i have not tried an alternet install cd

**Question i have:**
Are these errors because i have not yet re-partitioned my harddrive?

if so, what programs do you recomend-i was under the impression that i could do that from kubuntu live boot.

should i try the alternet install cd - i didn't see anything that suggested this may work better?

thanks

---

### Post by jken146 on 2007-11-29
You can run the 'Check CD for Errors' or some such when you boot from the live CD.  If it does have errors try re-burning it at a slow speed.

The easiest thing to do though is probably to use the alternate CD to install.  The live CD doesn't seem to work for everyone (graphics issues) but such problems usually disappear when you install.

My other advice is to plan your partitions carefully (8GB for / should be ok, and you will need a swap partition too, usually RAM x 1.5).  You may also want to consider backing up your important files.

Welcome to Ubuntu!

---

### Post by Lord_Pyro on 2007-11-30
tried the alt cd and got a little bit farther when i used "boot: install noapic nolapic".  however in the hardware detection section the installer could not detect either of my optical drives.

one is a samsung cd-rw internal
other is a memorex dvd-rw dl internal
both are ide connected.

i do not at this time have a floppy disk drive in the system and have no idea how to do a network install.  i might be able to install a floppy drive but don't know where to find a driver for either of those drives (but also have not done any searches yet.  anyone have a suggestions?

---

