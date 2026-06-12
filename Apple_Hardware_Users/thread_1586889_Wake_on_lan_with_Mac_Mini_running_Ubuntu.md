---
title: "Wake on lan with Mac Mini running Ubuntu"
date: 2010-10-02
forum: Apple Hardware Users
---

### Post by apoth on 2010-10-02
My Mac Mini running Ubuntu won't wake up to a wakeonlan magic packet (sent either from a wakeonlan app on my android phone or wakeonlan client on another Ubuntu PC). The lights on the ethernet port aren't on after powering down.

I shutdown using the halt command, I've tried with the p flag too. I've also tried setting NETDOWN=no in /etc/init.d/halt.

Some more details are below. Any suggestions would be appreciated. Thanks in advance.

```
$ sudo ethtool eth0
[sudo] password for rich: 
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: g
	Current message level: 0x000000ff (255)
	Link detected: yes
```

```
$ lspci|grep Eth
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
```

---

### Post by apoth on 2010-10-03
So, it seems to work if I suspend the machine, but not if I halt it.

Is there a way around this?

---

### Post by apoth on 2012-06-05
And in the last 6 months it's stopped working even for a suspended machine? Any ideas?

---

