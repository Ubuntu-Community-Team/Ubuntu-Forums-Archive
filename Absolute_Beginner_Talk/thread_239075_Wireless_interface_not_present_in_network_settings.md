---
title: "Wireless interface not present in network settings"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by rgates on 2006-08-18
Everyone,

Ubunto 6.06 on IBM T41. The wireless interface is present in /etc/network/interfaces, however it does not show up in the network settings gui or in the network device list in network tools - Devices.

How can I get this to show up so that I can configure it and start the wireless network.

Thanks in advance,

---

### Post by LadyDoor on 2006-08-18
Are you using ndiswrapper?

---

### Post by rgates on 2006-08-18
Not using ndis wrapper...

---

### Post by rgates on 2006-08-18
The interface does not show up when doing ifconfig either.

---

### Post by LadyDoor on 2006-08-18
I'm sorry...I honestly don't know how to help you. All I know in wireless is ndiswrapper. Good luck!

--Door

---

### Post by gils0040 on 2006-08-18
looks like your laptops uses the Intel PRO/Wireless LAN 2100 3B Mini PCI Adapter. this is supported under linux using the ipw2100 driver. it may be included in the kernel and a simple 'modprobe ipw2100' could solve the problem. if not it can be downloaded and compiled manually from [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/)

---

### Post by jensoko on 2006-11-03
> **gils0040 said:**
> looks like your laptops uses the Intel PRO/Wireless LAN 2100 3B Mini PCI Adapter. this is supported under linux using the ipw2100 driver. it may be included in the kernel and a simple 'modprobe ipw2100' could solve the problem. if not it can be downloaded and compiled manually from [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/)
I'm having this same problem.  I'm using an IBM T40p with Dapper and Kubuntu desktop.  My wireless card worked fine for two weeks, then suddenly failed and is completely unrecognized.  So far I've discovered that it's an IPW2100 (I think I was using 3650 or 3950 drivers) and it doesn't seem to be loading in the boot. 

I'm a rank, rank n00b at Linux and would appreciate any help or direction--the simpler, the better.

---

### Post by RockabyeRy87 on 2006-11-04
I'm having this issue as well.  I am using ndiswrapper however, and "sudo modprobe ndiswrapper" results in "FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument"

---

