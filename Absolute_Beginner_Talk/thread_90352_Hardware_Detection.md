---
title: "Hardware Detection"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by Major Matt Mason on 2005-11-14
Real newbie here.

Does Ubuntu detect hardware the same as Windows, like in a 'plug and play' kind of a way?

I have a Linksys Wireless-B notebook adapter (2.4 GHz, 802.11b) that I'm trying to get to work on a Tecra 8000 with Ubuntu installed. I haven't got a clue where to start. In the Device Manager it sees something because when I remove the card a device disappears from the list.

Am really just getting to grips with things, so answers in non-technical speak would be appreciated (I've only just discovered the terminal). Although I did manage to fix a bug on resolution thanks to you lovely people out there (which I was rather pleased about).

Cheers

Matt

---

### Post by Kapre on 2005-11-14
[QUOTE=Major Matt Mason]Real newbie here.

Does Ubuntu detect hardware the same as Windows, like in a 'plug and play' kind of a way?[/quote]

Partly yes. Meaning some hardware can be detected by Linux (in general) and can be "plug n play" and some they can not. In this case you'll need some drivers from the net.

> I have a Linksys Wireless-B notebook adapter (2.4 GHz, 802.11b) that I'm trying to get to work on a Tecra 8000 with Ubuntu installed. I haven't got a clue where to start. In the Device Manager it sees something because when I remove the card a device disappears from the list.

Am really just getting to grips with things, so answers in non-technical speak would be appreciated (I've only just discovered the terminal). Although I did manage to fix a bug on resolution thanks to you lovely people out there (which I was rather pleased about).

I'm not using a wireless adapter but I've been reading lots of post regarding some _minor_ difficulties encountered by other users regarding their adapters. I cannot help you on this one but would advise you to go through and search the forum because they have already fixed this.

Cheers

K

---

### Post by 010010110101 on 2005-11-14
Yes ,,I was wondering the same,,,about drivers for devices. I am going to be installing this weekend and will probably be all over these forums in the next few weeks,,,,so please be ready for a plethoria of questions. 

Thanks
F

---

### Post by Lambert on 2005-11-14
Type your exact model # in the search field for starters as you may find somebody else had the same problem/question as you and it's been solved already.

Searching though can be time consuming with many posts read and no answer found.

Open a terminal and type

```
sudo lshw -C network

here's part of  mine

*-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@03:00.0
       logical name: ath0
       version: 01
       serial: 00:11:95:50:be:62
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) ip=192.168.0.150 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:10800000-1080ffff irq:11
```

Because your device is shown it is plug and play, it just needs a driver set up so the os knows what to do with it.

In your search you may see what others are using. There may be a driver built into the the os, I use the madwifi driver. Or you may see ndiswraper which is a utility that makes the windows drivers work on a lot of cards but not all.

---

