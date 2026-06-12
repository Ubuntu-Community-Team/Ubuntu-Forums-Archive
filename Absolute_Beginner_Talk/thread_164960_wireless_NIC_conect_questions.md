---
title: "wireless NIC conect questions"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Silver-revo on 2006-04-23
Ok new problem again.

Now I got the Bcom wifi NIC working properly, now I need to know how to conect to  a wireless router...

I can see the router via Kwifi manager now how do I connect to the router and get onto the internet?

---

### Post by Papa-san on 2006-04-23
System > administration > networking

This will open a box that shows the different connection options. You will prolly be looking for wlan0. The first thing tho, will be to de-activate eth0 (or eth1).
Then click on wlan0 and click on properties (side tab) You will need to enter your router info:

Default is usually 192.168.1.1 for gateway (bottom) Try typing this into a browser url line to see if it connects to the router. If you get into the settings, you will see what your submask # is, and the range you can use for your laptop IP. (192.168.1.101 or something)

Once you have this set, click OK. Then it should show as active. If not, activate it. Also, you will need to set it as default.

---

