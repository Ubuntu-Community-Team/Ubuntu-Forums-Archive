---
title: "Um...Internet stopped working"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Cath0de on 2006-07-27
Ok, this is a pretty bizarre problem.

I came home from today and my network connection on my linux machine stopped working. I mean, it still works on every other computer I have, it says my ethernet connection is active on my machine (connected DHCP), but I can't connect through firefox, gaim, the shell, anything.

I use wireless internet and it has just always worked until I turned my machine on today. I didn't make any changes yesterday except installing the newest libpcap.

I honestly have no idea what the problem could be.

---

### Post by Cath0de on 2006-07-27
I think my laptop stopped detecting my wireless network and somehow became configured to ethernet even though I use wireless. How can I get it to recognize my wifi?

---

### Post by nalmeth on 2006-07-27
Start at

SYSTEM > ADMNISTRATION > NETWORKING

You should be able to activate/deactivate devices from there

---

### Post by Cath0de on 2006-07-27
Like I said, when I go into that menu, I'm shown that my ethernet connection (interface eth0) is active. Yet I'm still not connecting to my wireless network. I mean, this has always worked, it's not like the right drivers aren't installed or something.

---

### Post by nalmeth on 2006-07-27
Hmm, I didn't see you mention that before.

Regardless, can't you deactivate eth0 and activate eth1 or wlan0, whichever is your wireless?

---

### Post by Cath0de on 2006-07-27
when I look at that list of possible connections, I get the eth0 connection, a modem connection (I have a dual modem/ethernet card), and that's it.

 There was a wlan connection there yesterday, so it stopped detecting that. So, er, uh, how can I get it back? :-(

---

### Post by dad_e_man on 2006-07-28
let me know when you figure this one out...   I have had the same problem with three different distros....   I was hoping today when my disc got here that it was gonna work...  but no luck with Ubuntu either  So I figure since none of the distros can help me with this problem, its hardware related....   so you might want to pull the network card and try a different one if you happen to have an extra...   see I don't but would like to hear how that goes. Sorry...  total newb here...   my first post even...

---

### Post by nalmeth on 2006-07-28
Here is a good walkthru for wireless.
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

It's been a while since I've had to deal with it, so I can't seem to think of anything directly ATM. :(

It's a little long and detailed, but I'm sure you'll pick something useful out of it.

---

### Post by Papa-san on 2006-07-28
need to post, as I cannot find my own links...:rolleyes:
EDIT:

I got the network settings to show wlan0 now... I had previously installed something called " Network tools 2.14.2" this had what I needed to exchange the eth1 for my old wlan0. Not sure how it did it, but it did... I got it through the repositories... uni, I think?

---

### Post by Cath0de on 2006-07-31
I'm still not picking up the wireless network, though that tutorial helped me narrow down the problem: my computer stopped detecting my wireless card.

Can anyone help me figure out how to get it to start recognizing it again?

---

### Post by Cath0de on 2006-08-01
Ok, the output of
```
sudo lshw -C network
```

was (relating to my wireless card):
```
*-network: 1 UNCLAIMED
description: Network controller
product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
vendor: Intel Corporation
physical id: 2
bus info: pci@02:02.0
version: 04
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
resources: iomemory:d0220000-d0220fff irq:11
```

I'm no genius, but I think that unclaimed flag might have something to do with it since my network: 0 (ethernet, which works) doesn't have that.

Any ideas?

---

### Post by Cath0de on 2006-08-01
I think I've narrowed it down...I remember twiddling with my drivers last week and all signs point to my drivers not interfacing with the device, so perhaps I should install the default drivers for my particular card.

What is the code for installing drivers for this card (model type in above post)?

---

### Post by Cath0de on 2006-08-01
okay, really homing in on it now, this last part I really need help on.

I figured out which drivers I need (w70n51.inf and w70n51.sys both obtainable through ndiswrapper) but when I do ndiswrapper -i w70n51.inf or ndiswrapper -i w70n51.sys, I get:

```
couldn't copy w70n51.whatever at /usr/sbin/ndiswrapper line 135
```

Those drivers are listed as appropriate for the Intel PRO/Wireless LAN 2100 3A Mini PCI adapter, and my card as listed by lshw is a 2100 3B. I figured it would run on the same drivers, but just throwing that out there if that is the problem. The article ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#I](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#I)) that I pulled those drivers from notes that 2100 3A cards are detected as 2100 3B using linux diagnostics but the drivers work either way.

---

### Post by gils0040 on 2006-08-01
i quick search found that this card uses the ipw2100 driver. in terminal do lsmod and look for that module. if you dont find it, i think that a simple sudo modprobe ipw2100 should do the trick.

---

### Post by Cath0de on 2006-08-01
ipw2100 was not picked up in the lsmod output.

Here the web of confusions gets woven a bit thicker: 
```
root@ubuntulaptop1:/home/cath0de# modprobe ipw2100
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/net/ieee80211/ieee80211_crypt.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-23-386/kernel/net/ieee80211/ieee80211.ko': No such file or directory
FATAL: Error inserting ipw2100 (/lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/ipw2100.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Anyone care to untangle this mess?

---

### Post by gils0040 on 2006-08-01
im not sure, but it looks to me like you are missing some of the modules needed. i would suggest trying to compile the driver from source. [http://prdownloads.sourceforge.net/ipw2100/ipw2100-1.2.1.tgz?download](http://prdownloads.sourceforge.net/ipw2100/ipw2100-1.2.1.tgz?download)

---

### Post by leoscuro on 2006-08-29
My wirelles was working, I used this method:
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

but now my computer is not seeing the wirelles card

I ran this:
sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:48:11:f3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.134 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:7000-70ff iomemory:e0108800-e01088ff irq:185
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       resources: iomemory:e0104000-e0105fff irq:11
I got the UNCLAIMED warning...I am completely lost on this...

---

