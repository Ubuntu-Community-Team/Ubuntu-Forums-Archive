---
title: "Network usage question"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by arijarot on 2007-06-29
I just installed a new wireless pcmcia network card. The system now shows two network connections. The one that I use, that is, ath0, and wifi0. 
My iwconfig ```
 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ...

``` doesn't have wifi0 enabled/configured, yet for some reason there is a constant ~2.2KB/s network usage (Received). I checked wireshark and there are no packets being sent across this network nor are there any established connections. 
My question is, why is there constant network activity [EDIT:] on the wifi0 interface?

---

### Post by arijarot on 2007-06-29
Can wifi0 be stopped?

---

### Post by arijarot on 2007-07-02
(bump)

---

### Post by arijarot on 2007-07-07
sorry, bump.

---

### Post by Swab on 2007-07-07
Perhaps there is some lower layer network activity going on.   Stuff that wireshark wouldn't pick up on.  Just a guess.  

Either that or the network usage meter is borked :)

---

