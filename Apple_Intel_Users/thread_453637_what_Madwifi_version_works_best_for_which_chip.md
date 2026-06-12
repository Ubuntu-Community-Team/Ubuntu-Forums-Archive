---
title: "what Madwifi version works best for which chip?"
date: 2007-05-24
forum: Apple Intel Users
---

### Post by benanzo on 2007-05-24
I am trying to get an idea of people's success with different versions of Madwifi with the different wireless chips in the Macs.

I am using **0.9.3 (2007-03-19)** compiled for a 2.6.21.1 kernel with the 2.6.21 mactel patches.  This version works wonderfully on my first-gen MacBook Core Duo.

```
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

I've been testing the latest SVN snapshots, hoping for better range/power management, but all I've gotten was the module failing to unload cleanly on poweroff/suspend.  This is a regression bug that I have seen reported and have discussed with the Madwifi devs on IRC.

Anyone know which Madwifi version shipped with the stock Feisty kernel/restricted-modules?

---

### Post by ronocdh on 2007-05-29
> **benanzo said:**
> I am trying to get an idea of people's success with different versions of Madwifi with the different wireless chips in the Macs.

I am using **0.9.3 (2007-03-19)** compiled for a 2.6.21.1 kernel with the 2.6.21 mactel patches.  This version works wonderfully on my first-gen MacBook Core Duo.

```
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

I've been testing the latest SVN snapshots, hoping for better range/power management, but all I've gotten was the module failing to unload cleanly on poweroff/suspend.  This is a regression bug that I have seen reported and have discussed with the Madwifi devs on IRC.

Anyone know which Madwifi version shipped with the stock Feisty kernel/restricted-modules?
Hm, this post slipped under my radar. On my current installation of Ubuntu, I'm not sure whether I'm using ndiswrapper or madwifi, because I recall trying to configure both (I was installing fresh to show a friend how easy setup was). Can you give me some terminal commands to run so I can check this, and also call up my version numbers?

---

