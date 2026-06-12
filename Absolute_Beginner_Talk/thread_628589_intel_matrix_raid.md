---
title: "intel matrix raid"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by simons-photography on 2007-12-01
ok no I don't want to install ubuntu onto my raid I have a separate HDD for the OSes and the raid for data...

can ubuntu recognise an intel matrix raid and use it and not have issues ?

I have the gigabyte DS3 mobo so the system disks are on gigabytes own sata controller and the raid disks are on intels SB controller set up as raids

---

### Post by webjames on 2007-12-01
the easiest way to test this is to download the ubuntu live cd, and run it, click install, and when it comes to partitioning see if it picks it up correctly.

there is three different types of raid, hardware raid, software raid, and fakeraid. the latter is normally what you find embedded in motherboards. linux has very good software raid. i have an adaptec hardware raid card which you set up the partitions in a separate bios before the os is booted.

as is said go through the installer until you get to the partition setup and see if your raid gets picked up, or if it still looks like separate drives. however make sure you don't confirm any partition changes.

hope this helps

---

### Post by simons-photography on 2007-12-01
yea say that again I've already freeked it out by knoking out a raid partition in ubuntu but tell me more about the ubuntu software raid if I have three HDDs can I tell ubuntu to make a raid out of them ? without going thru the hardware raid ? would be handy as I'm not up to trusting raid that much just need some highspeed scratch disk space

---

### Post by webjames on 2007-12-01
> **simons-photography said:**
> yea say that again I've already freeked it out by knoking out a raid partition in ubuntu but tell me more about the ubuntu software raid if I have three HDDs can I tell ubuntu to make a raid out of them ? without going thru the hardware raid ? would be handy as I'm not up to trusting raid that much just need some highspeed scratch disk space

the only reason for going for hardware raid is that that you can multi boot windows as well. if you download the alternative cd then you can setup software raid from there. 

i think the basic steps is to set the hard drives you want to be included in the raid as 'linux raid' then you can setup the partitions once that is done in the next step. there is howto's around about doing this, but if you are fairly IT competent then just give it a go. a good idea is to have nothing plugged in that you don't want to loose when you testing then once you're sure of you setup plug in any other drives you don't want in the raid.

---

### Post by webjames on 2007-12-01
to get the alternative CD go here: [http://www.ubuntulinux.org/getubuntu/download](http://www.ubuntulinux.org/getubuntu/download)

and make sure you tick the box at the bottom:

> "Check here if you need the alternate desktop CD"

---

