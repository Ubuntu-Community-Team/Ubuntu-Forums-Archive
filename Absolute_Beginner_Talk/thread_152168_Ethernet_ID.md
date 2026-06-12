---
title: "Ethernet ID"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by phenix on 2006-03-29
anybody knows how I can find my ethernet card ID in ubuntu

THAN YOU!!!!

---

### Post by rmjokers on 2006-03-29
If you are talking about the hardware (MAC) address,  you can get that by opening a terminal and typing:

ifconfig -a

You should see something like this:

eth0      Link encap:Ethernet  HWaddr 00:11:43:BB:AE:AA

indicating that the address is 00:11:43:BB:AE:AA

---

### Post by phenix on 2006-03-29
man that was fast!!!!
thanks rmjokers!!!

---

