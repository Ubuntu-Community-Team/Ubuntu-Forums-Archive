---
title: "wireless networ - what speed?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by roger_doger on 2006-10-11
How can I tell what speed my wireless adapter is working at? I can open the network manager, and see the signal strength, but that's it.

---

### Post by meng on 2006-10-11
You could drop down to terminal and:
sudo iwconfig eth0
(assuming eth0 is your wireless interface)

---

### Post by roger_doger on 2006-10-11
Will that allow me to change it to either an 802.11b or g?

---

### Post by meng on 2006-10-11
[http://www.die.net/doc/linux/man/man8/iwconfig.8.html](http://www.die.net/doc/linux/man/man8/iwconfig.8.html)

---

### Post by roger_doger on 2006-10-13
iwconfig allowed me to see what it is working at. Before I installed ubuntu, I was using XP, and I was able to connect at 54mb/s, now I only seem to connect at 36 mb/s. Signal level is good. Is the a gui for the wireless? any other suggestions?

---

