---
title: "when can I trust the linux update system? network manager broke"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by clevin on 2007-04-17
every update of every distro always break something. 

this network manager 0.6.4 can not detect my static IP network card, all it gives me are wireless networks.

however, I can still connect my office LAN if I “disable wireless” from right click menu.

whats wrong?
> 
sudo ifdown -a; ifup -a did not help

why Linux auto upgrade sucks so much?

---

### Post by zvacet on 2007-04-17
If I understand you correctly,you don´t need wireless.If it is so 
> disabling network manager in the sessions/startup bit, and typing 

sudo ifup eth0
sudo ifdown eth0
sudo ifup etho

---

