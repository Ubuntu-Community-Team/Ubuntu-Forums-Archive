---
title: "Re: ubuntu 17.10 - no wi-fi adapter found"
date: 2017-12-15
forum: Apple Hardware Users
---

### Post by itachiniko on 2017-12-15
Came across this thread while looking for a solution to the same problem on my mid 2009 macbook pro.

lspci -nnk | grep -iA3 net

returns :

00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
	Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth
--
03:00.0 Network controller [0280]: Broadcom Limited BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
	Subsystem: Apple Inc. AirPort Extreme [106b:008d]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb



can you help?

---

### Post by QIII on 2017-12-19
Moved to its own thread in Apple Hardware Users from [https://ubuntuforums.org/showthread.php?t=2375901](https://ubuntuforums.org/showthread.php?t=2375901)

Please do not horn in on the threads of other users.  That becomes confusing for the OP,  you and those trying to help.

Cheers.

---

