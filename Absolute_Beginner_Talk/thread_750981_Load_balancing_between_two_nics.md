---
title: "Load balancing between two nics"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by karthikbalaji on 2008-04-10
Hi All,

I have two NIC'S on my system (Broadcom and e1000) and both are connected to the network. Is there any tool or method to distribute the network traffic across the two NIC's ? Or is it taken care by ubuntu by default ?

However I could see from Network manager that only one NIC is active at a time.Also both nic's have roaming mode enabled.

Is there a way to effectively utilize both the NIC's?

Thanks,
Karthik

---

### Post by m_atif on 2008-04-10
Its not taken care of by default. By the looks of it, you should be looking for channel bonding (ethernet bonding). It can serve numerous purposes, IMHO and through experiments I have concluded that for extream high load on a cluster (high performance computing) channel bonding achieves less bandwidth and high latencey, especially for gigabit ethernet cards. 
A good tutorial is here for debian which should work for ubuntu as well.
[http://www.debianhelp.co.uk/bonding.htm](http://www.debianhelp.co.uk/bonding.htm)

Please let me know if you face problems.

---

