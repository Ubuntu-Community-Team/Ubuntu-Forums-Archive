---
title: "Ubuntu 10.10 Fails to boot past startup screen, Mac G4"
date: 2011-05-18
forum: Apple Hardware Users
---

### Post by RandomNameRandom on 2011-05-18
Hey I just recently put Ubuntu 10.10 for ppc on a Cd-R and installed it onto an old Mac I had found.  The installation seemed perfectly fine I booted the computer and was presented to boot with two options "Linux" and "old" or to press enter and boot default.  I had decided to boot default and it reaches the splash screen where the loading bar advances two dots and then completely stops.
If there is any more info needed please say inform me.

EDIT: Oh also if it matters it appears to be using yaboot.

---

### Post by RandomNameRandom on 2011-05-18
So terminal spiuts this message at me 
fsck from util-linux-ng 2.17.2
/dev/hda3: clean 109686/3523856 files, <whatever out of whatever> blocks
*Starting AppArmor profiles
[    23.586498] fb: conflicting fb hw usage nouveaufb vd Offb NVDA NVMac - removin generic driver

Then it just completely freezes.

---

### Post by linuxopjemac on 2011-05-19
I guess you need to make an xorg.conf file and use the nv driver instead of the nouveau driver it seems to try. What is your exact MAc model anyway? Can you give a link in everymac.com ?

---

### Post by RandomNameRandom on 2011-05-19
[http://www.everymac.com/systems/apple/imac/stats/imac_700_fp.html](http://www.everymac.com/systems/apple/imac/stats/imac_700_fp.html)

here appears to be the correct model but I'm not nessecarily sure it could be any PPC G4 iMac, but it is an iMac not a powerbook etc...

---

### Post by RandomNameRandom on 2011-05-19
So how would we go about creating an xorg.conf for a system that cant even boot? 
Would we try to edit the iso? And in that instance how would we do it?

---

### Post by linuxopjemac on 2011-05-20
At the yaboot prompt try to boot into single user modus:
```
Linux 1 video=ofonly nosplash
```
then you are asked for your root password
then you do the following:
```
wget http://mac.linux.be/files/xorg/imac8.txt
mv imac8.txt /etc/X11/xorg.conf
```
CTRL-D to resume booting
good luck and let us know how it goes...

---

### Post by RandomNameRandom on 2011-05-20
Nope that boot command hasn't worked it still spits the same message out to me about removing generic driver and freezes. I haven't been able to access the computer at all past the boot prompt.

---

### Post by linuxopjemac on 2011-05-20
Install MintPPC.

---

