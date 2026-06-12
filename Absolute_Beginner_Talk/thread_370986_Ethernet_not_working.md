---
title: "Ethernet not working"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by graha on 2007-02-26
am completely new to ubuntu i just installed it today at first the ethernet works fine but then when i boot my computer it didnt work, even in live cd it didn't. can someone help me

---

### Post by ukripper on 2007-02-26
> **graha said:**
> am completely new to ubuntu i just installed it today at first the ethernet works fine but then when i boot my computer it didnt work, even in live cd it didn't. can someone help me

Run follwoing commands :

$ sudo ifconfig -a


and paste output here.

just a temperory solution if your ethernet doesn't start type following in terminal:

$ sudo ifdown eth0
$ sudo ifup eth0

---

### Post by zvacet on 2007-02-28
[http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe]("http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe")

---

