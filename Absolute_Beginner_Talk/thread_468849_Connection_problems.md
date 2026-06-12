---
title: "Connection problems"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by gubata on 2007-06-09
i ve started eth0 and lo, i put my ip and gateway but cant ping even gateway.
ping say connction is unreachable!!!!

---

### Post by EndPerform on 2007-06-09
> **gubata said:**
> i ve started eth0 and lo, i put my ip and gateway but cant ping even gateway.
ping say connction is unreachable!!!!

What does the output of:

```
ifconfig
```

show?  Also, is there some reason you aren't using DHCP?  Most routers will deal out an IP address to you automatically.

---

### Post by matthewboh on 2007-06-09
Can you give a little more information?  Is this a NIC card or wireless, what version of Ubuntu are you running?

NetworkManager is getting pretty good, but you have to comment out the devices to let it do it's thing.  Try going into /etc/network/interfaces and comment out everything EXCEPT local (lo)

---

### Post by gubata on 2007-06-09
i ve Ubuntu 7.04 Feisty Fawn
i ve static ip that must be add manual, i allrdy add ip gateway and dns 
i ve wired connection not wareless
Network Adapter	Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC on epox mf4 ultra 3

---

### Post by matthewboh on 2007-06-09
Can you post the output of ifconfig?

---

