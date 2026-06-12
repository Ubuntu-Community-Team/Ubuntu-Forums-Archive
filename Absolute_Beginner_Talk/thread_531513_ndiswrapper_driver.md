---
title: "ndiswrapper driver"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by kcirtap on 2007-08-21
I'm reading a guide in the Ubuntuwiki about how to install ndiswrapper to use my wireless card. Everything is going well so far except that the driver from the driverlist, this site to be exact: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/) isn't working. The problem is that the driver I need is removed from the server.

**Wireless card:**
**00:0b.0** Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I've been searching a bit and found out that ndiswrapper is the best attempt to get wireless working with my card. I need to get the Windows driver though, thankful for help..

---

### Post by ddrichardson on 2007-08-21
Do you still have your windows driver or restore partition?

---

### Post by kcirtap on 2007-08-21
> **ddrichardson said:**
> Do you still have your windows driver or restore partition?

Well, I still have Windows installed on another partition so maybe I can get the driver from there? Where is it located, I don't know which files it is.

---

### Post by ddrichardson on 2007-08-21
If you have a recovery partition it'll be in \i386\drv\net. If not then it'll be in the Windows directory somewhere. it'll probably be bcm4318.inf.

---

### Post by kcirtap on 2007-08-22
> **ddrichardson said:**
> If you have a recovery partition it'll be in \i386\drv\net. If not then it'll be in the Windows directory somewhere. it'll probably be bcm4318.inf.

Alright I searched the Windows folder and found: **BCMWL5.INF** and **BCMWL5A.INF**. I have also installed those drivers but it still doesn't work. I can find all the networks available but I cannot connect to any of them.

edit: When I type ndiswrapper -l the following appears:
[I]
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
bcmwl5a : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
drivername : invalid driver![/I]

---

### Post by splintercellguy on 2007-08-22
You need to blacklist the native driver:

gksudo gedit /etc/modprobe.d/blacklist

And add to the end of the file:

blacklist bcm43xx

Then save and reboot.

---

### Post by kcirtap on 2007-08-22
That's already done. I did that yesterday.

---

### Post by kevdog on 2007-08-22
Can install multiple drivers

cd /etc/ndiswrapper
sudo rm -rf *

---

### Post by ddrichardson on 2007-08-22
If you can find networks but not connect it isn't neccessarily the driver at fault. Broadcom cards are notoriously awkward to get setup.

Finding networks indicates that the card is identified and powered on, how is the wireless network configured?

---

### Post by kcirtap on 2007-08-23
> **ddrichardson said:**
> If you can find networks but not connect it isn't neccessarily the driver at fault. Broadcom cards are notoriously awkward to get setup.

Finding networks indicates that the card is identified and powered on, how is the wireless network configured?

I'm not sure, I haven't really configured it except activating it and typed the right password. I've only followed the following tutorial on ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

