---
title: "network adapter values?"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by anemptygun on 2007-11-26
This seems like a silly question, but I have 3 network interfaces eth0, eth1, and ath0. How do I tell which is which?

---

### Post by PeterJS on 2007-11-26
> **anemptygun said:**
> This seems like a silly question, but I have 3 network interfaces eth0, eth1, and ath0. How do I tell which is which?

ifconfig will tell you the ip address associated with each one of those. I can tell you right now that ath0 is an Atheros wireless card, because they're cool, and like to be different with their naming scheme.

---

### Post by anemptygun on 2007-11-26
sweet! thx!

---

### Post by jamvegan on 2007-11-26
You can run
```
ifconfig
``` 
to determine the HWaddr associated with each of those interface names, then run 
```
sudo lshw -class network
```
and compare the serial number shown for each device to the HWaddr from ifconfig.

---

