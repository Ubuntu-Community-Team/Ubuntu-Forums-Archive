---
title: "can't get ipaddress"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by stu2004 on 2006-06-09
hi,

I have installed 606. In the networking settings i have an active ethernet card, dns servers are set and i can see the network.

I can't seem to get a dhcp ipaddress. I assume my lack of knowledge here is the problem what have i failed to do?

---

### Post by oscar on 2006-06-09
Firstly check in your System > Administration > Networking , Select your ethernet card and go properties, Make sure that it is enabled and the configuration is set to DHCP. If that doesn't work then try:
```
sudo dhclient eth0
```
in a terminal and see what happens.

---

### Post by stu2004 on 2006-06-09
thanks that worked.

---

