---
title: "newbie needs wireless help and flash help!"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by michaelpagz on 2007-08-01
hi everyone. im new to linux alot. in fact, i just installed ubuntu 7.04 t for the first time on a built computer that was previously running xp. i really enjoy it so far but i have a couple problems. 

first problem: i can't get the wireless to work! i'm using a buffalo wireless card. im clicking on the 2 overlapping black screens and it isnt showing my wireless network. i think mabye somethings up with driver recognition, but then again i am clueless. please help! 

second problem: i can't get flash to work! it won't let me check the flash plugin package from the other category in the sound and video section to add it! i think i figured out that this has something to do with the fact that i am running x86 amd. help!!!

if you need more info please let me know. sorry if i am phrasing incorrectly. i hope these are common problems that can be fixed!

thanks in advance for your help,
mike

---

### Post by AlexenderReez on 2007-08-01
have you enable all repos ? (universal? ) in software sources ? 

terminal -->

> gksu gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

enable all...update...

for flash install flash-plugin nonfree package ...hm..about wireless...some card will give you automatically detect if you are using fesity(with network manager gnome installed)..if you are not using wireless line without no encryption then you should able to detect it easily ....i think you should check it in its website ---> use** ndiswrapper** if it required to install windows driver :) ...


you can try to install **Broadcom 43xx Firmware** :)

---

### Post by wolfen69 on 2007-08-01
this [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBuffalo](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBuffalo) is all i could find for buffalo wireless.  go here [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)  to add repositories. then: add/remove programs, search for flash.

---

### Post by ugm6hr on 2007-08-02
> first problem: i can't get the wireless to work! i'm using a buffalo wireless card. im clicking on the 2 overlapping black screens and it isnt showing my wireless network. i think mabye somethings up with driver recognition, but then again i am clueless. please help! 

You need to find the wifi chipset, and then which driver Ubuntu is using at the moment:
```
lspci -nn | grep Network
lspci -nn | grep Ethernet
lshw -C network
```

One of the first 2 will list the wifi chipset. The last one will list similar details, but one line will read something like:
>  configuration: broadcast=yes driver=ath_pci ip=192.xxx.x.xxx latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
You are interested in the driver=... bit.

Post the results here - and we'll get you started.
> 
second problem: i can't get flash to work! it won't let me check the flash plugin package from the other category in the sound and video section to add it! i think i figured out that this has something to do with the fact that i am running x86 amd. help!!!

If you are unable to update the Synaptic sources (click on reload in Synaptic), it will give errors re:x86 if you try and install flash-plugin-nonfree.  So you need to get online first!  There is another way - but it's much easier to get wifi sorted and then download that way (unless you can use an ethernet connection to internet).

---

### Post by michaelpagz on 2007-08-03
> **ugm6hr said:**
> You need to find the wifi chipset, and then which driver Ubuntu is using at the moment:
```
lspci -nn | grep Network
lspci -nn | grep Ethernet
lshw -C network
```

One of the first 2 will list the wifi chipset. The last one will list similar details, but one line will read something like:

You are interested in the driver=... bit.

Post the results here - and we'll get you started..

okay, here is what i got from those three command lines: driver=bcm43xx. what is the next step then?

```
:~$ lspci -nn | grep Network
01:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
:~$ lspci -nn | grep Ethernet
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a2)
:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth1
       version: 03
       serial: 00:16:01:56:56:3c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=32 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:fe9fc000-fe9fdfff irq:19
```

by the way thanks so much for everyones help! i love this stuff! i dont understand much but its so much more interesting than windows!!!

---

### Post by ugm6hr on 2007-08-03
> **michaelpagz said:**
> i dont understand much but its so much more interesting than windows!!!

This is the wifi chipset: *Broadcom Corporation BCM4306 *
And, as you spotted, this is your current wifi driver: *bcm43xx*
So that you can understand a bit about the commands: [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/) (although lshw isn't there)

To fix wifi - there are 2 main options (feel free to search for these terms in the forum to find out more):
1. fwcutter
2. ndiswrapper

If you are online with Ubuntu - then the easiest solution is here:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

If this doesn't work:
[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)

I think the second option can be made to work without internet on Ubuntu (with a USB-flash to transfer files).

---

### Post by michaelpagz on 2007-08-03
woohooo! it worked! thanks so much i used the first link and it worked very smoothly and efficiently. now i just need flash and then to get my desktop to do that cool 3d cube effect. heh!

---

### Post by ugm6hr on 2007-08-03
> **michaelpagz said:**
> second problem: i can't get flash to work! it won't let me check the flash plugin package from the other category in the sound and video section to add it! i think i figured out that this has something to do with the fact that i am running x86 amd. help!!!


If it's x64 you're running - you'll have to search these forums for an the solution (I believe there is one).  If it's i386 - it's very easy - just add it from repos.

---

