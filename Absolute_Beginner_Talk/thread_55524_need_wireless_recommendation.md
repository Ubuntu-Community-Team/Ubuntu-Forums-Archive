---
title: "need wireless recommendation"
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-08-09
right now, i'm on a USB wireless connection (netgear wg111). the router is also netgear. i have been advised to use ndiswrapper to get my wg111 going. (frankly, i just don't see me getting that done.) what i would like is something that is going to start up without me having to do anything but to install ubuntu. so, which wireless USB adapter would work with ubuntu, right from the start? can i use a different brand adapter from the router (router has to stay netgear. long story)?

---

### Post by costoa on 2005-08-09
[QUOTE=fuscia]right now, i'm on a USB wireless connection (netgear wg111). the router is also netgear. i have been advised to use ndiswrapper to get my wg111 going. (frankly, i just don't see me getting that done.) what i would like is something that is going to start up without me having to do anything but to install ubuntu. so, which wireless USB adapter would work with ubuntu, right from the start? can i use a different brand adapter from the router (router has to stay netgear. long story)?[/QUOTE]

Check out: [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards). It will tell you what cards work "out of the box".

As for mixing cards and routers, it's fine. The exception is Netgear's "Super G", which requires a wireless card with an Atheros chipset. Otherwise the standard 802.11g / 54Mbit works fine. I use a Linksys router and Orinoco, 3Com, ralink and whatever Apple uses chipsets on the same network.

---

### Post by fuscia on 2005-08-09
thanks. looks like i may be out of luck with USB adapters.

---

### Post by costoa on 2005-08-09
[QUOTE=fuscia]thanks. looks like i may be out of luck with USB adapters.[/QUOTE]

Is there a reason you need to use an USB adaptor?

---

### Post by fuscia on 2005-08-09
[QUOTE=costoa]Is there a reason you need to use an USB adaptor?[/QUOTE]

i have an old piece of crap that has no ethernet card and no PCI slots (whatever the hell they are). i'm on the second computer in the house, so i get the wireless connection.

---

### Post by costoa on 2005-08-09
[QUOTE=fuscia]i have an old piece of crap that has no ethernet card and no PCI slots (whatever the hell they are). i'm on the second computer in the house, so i get the wireless connection.[/QUOTE]

That's a good reason. =)   The Netgear MA111v1 (~$40USD) was on the list as supported and is USB. Good luck.

costoa

---

