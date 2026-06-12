---
title: "[SOLVED] How to connect to a wireless network"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-04-24
I have an unsecured wireless network which only allows connections based on the MAC addresses. I put in the MAC address of my computer in the router settings and I can connect via Vista. But when I create a new wireless profile in Ubuntu, it tries to connect, but never actually does.
 
Am I missing something?

---

### Post by bukwirm on 2007-04-25
What happens if you enter the following commands:

sudo ifdown **interface**
sudo iwconfig **interface** essid **essid**
sudo ifup **interface**

Replace the stuff in bold with the appropriate items.

---

### Post by Inxsible on 2007-04-25
> **bukwirm said:**
> What happens if you enter the following commands:
 
sudo ifdown **interface**
sudo iwconfig **interface** essid **essid**
sudo ifup **interface**
 
Replace the stuff in bold with the appropriate items.
 
 
or some reason, I am now able to connect via the same network !!
 
Maybe i just wasnt patient enough earlier !
 
Thanks for you help, Bukwirm

---

### Post by bukwirm on 2007-04-27
You're welcome!

---

