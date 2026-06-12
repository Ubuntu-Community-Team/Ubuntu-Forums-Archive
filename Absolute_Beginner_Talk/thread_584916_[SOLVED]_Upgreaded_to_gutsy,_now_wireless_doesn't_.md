---
title: "[SOLVED] Upgreaded to gutsy, now wireless doesn't work - where are restricted drivers"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Sporkman on 2007-10-21
I have an Acer Aspire 5100-3357 laptop. Wireless worked fine in 7.04, but after upgrade to 7.10 it did not. Note that I ran into "failed to fetch <repository>..." problems during installation (perhaps do to Automatix?), so I followed the suggestion made in a thread to turn off all but the canonical-main repositories in Synaptic->repositories. Installation then proceeded fine. Perhaps that causes new restricted drivers not to download...? How can I get those now?

FYI, when I go to System->Adminstration, there is no "restricted drivers manager"...

Here's the output of lshw -C network:

```

> lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:b6:88:26
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=80 maxlatency=28 mingnt=10

```

Thanks...

---

### Post by mistergq on 2007-10-21
Have you turned all the restricted repos back on?

---

### Post by Sporkman on 2007-10-21
> **mistergq said:**
> Have you turned all the restricted repos back on?

Yes, and when I search in synaptic for "atheros", I get two "linux-restricted"-type packages, but they show as installed, & the name says they's associated with linux 2.6.20 (as opposed to Gutsy's 2.6.22...)

---

### Post by Sporkman on 2007-10-21
Ah, I fixed it:

First I tried to simply modify the "linux-restricted..." module name to match that of the current kernel: 

sudo apt-get install linux-restricted-modules-2.6.22-14-generic

...no luck, it said it couldn't find the package. Then I ran:

sudo apt-get install update

..note that I have the restricted, etc, universe turned back on. Then tried to download the same module:

sudo apt-get install linux-restricted-modules-2.6.22-14-generic

...and it found it! 8)

Wireless now working fine. 8)

---

