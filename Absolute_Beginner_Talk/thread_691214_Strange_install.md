---
title: "Strange install"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by nwcman on 2008-02-08
Hello, I have recently installed gutsy 7.10. The install itself went smoothly, however when actually in the OS the problems occur. First, unlike ubuntu on my laptop it doesn't check for the updates.  Second, my video card isn't being detected.  Even when I try to set the default nvidia drivers up.  Everything else seems to work ok. Any help would be greatly appreciated.

My system specs are ( in case anyone asks ):
Intel Q6600 quad core
Gigabyte p35-d3sl motherboard
Crucial Ballistix DDR2800
BFG NVIDIA 8800GT OC

---

### Post by taurus on 2008-02-08
Is your networking connection working?  Maybe your network is off so it couldn't check for update and couldn't install a driver for your graphic card.

Applications -> Accessories -> Terminal
```
/sbin/ifconfig
```

---

