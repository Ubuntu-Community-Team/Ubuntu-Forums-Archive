---
title: "Downloads Cause System Freeze Up"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by TheFourElements on 2008-02-06
Whenever I download anything using bittorrent my whole computer freezes up. I have to cut the power and then start it back up again. I used to think that it was just bittornado that I was using but other bittorrent programs cause this as well. Does anybody know what is going on? Has this happened to anybody before? Any help is appreciated.

---

### Post by spiderbatdad on 2008-02-06
I recently saw a suggestion that linksys routers have trouble with torrents.

---

### Post by hyperair on 2008-02-06
It's not a router problem. Are you using ndiswrapper? If so type "ndiswrapper -v" in the command line and give us the output.

---

### Post by TheFourElements on 2008-02-06
I'm not using ndiswrapper

---

### Post by jan quark on 2008-02-06
whats your network device?

pls post the result of the terminal command:

```
lshw -C network
```

---

### Post by TheFourElements on 2008-02-06
```
 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@01:0b.0
       logical name: eth0
       version: 10
       serial: 00:0d:61:19:89:19
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:c400-c4ff iomemory:ee000000-ee0000ff irq:19
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:04:e2:98:e5:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=8.101.5-84 ip=192.168.2.169 wireless=IEEE 802.11b

```

---

