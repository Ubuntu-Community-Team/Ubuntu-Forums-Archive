---
title: "wireless not functioning"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by maclif58 on 2008-01-30
hi
i use a hp zv6000 notebook and can not make my wifi to work
searching the forum i found this line 

configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g

now looking at my configuration i see this line

configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.0.0.3 latency=128 maxlatency=64 mingnt=32 multicast=yes

it looks as if i need ndiswrapper+lsbcmnds in order to use my wifi

can anyone help

maccabi

---

### Post by macogw on 2008-01-30
Uh...what?  I see the string "bcm" in there, so I'm guessing you're saying it's a Broadcom card?  Can you post the output of this?
```
lspci | grep -i broadcom
```

My roommate's says > 02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

Does yours say something similar about Broadcom and 802.11?

If it's a Broadcom wireless card, just install bcm43xx-fwcutter to get the firmware (the driver is already installed), like this:
```
sudo apt-get install bcm43xx-fwcutter
```

---

### Post by Crafty Kisses on 2008-01-30
You might have to use a NDISwrapper.

---

