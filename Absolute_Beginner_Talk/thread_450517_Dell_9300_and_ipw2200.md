---
title: "Dell 9300 and ipw2200"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Nxion on 2007-05-21
Can some one point me in the direction on how to upgrade the drivers for my wireless. I have the ipw2200. The driver version that is on the laptop now is 1.2.0. The reason why I want to do this is because some of the wireless audit tools wont work because it tells me that monitor mode isn't enabled. I looked around and it says that I need to upgrade my driver,

Any help ?

---

### Post by Kobalt on 2007-05-21
If you have Ubuntu 7.04 then your card should actually be working pretty well (it's one of the best working card of the moment). To me your problem doesn't come from your driver version, a configuration problem. Do you use Network-Manager for example ?

---

### Post by Nxion on 2007-05-21
Yes I do use network-manager, and yes I use Feisty. But how is that linked with the wifi audit tools ?

---

### Post by Kobalt on 2007-05-21
I'm not sure actually, I'm just trying to search where that could come from potentially.

---

### Post by Nxion on 2007-05-21
Got ya :)

---

### Post by gerrymoth on 2007-05-21
This might be a good starting point:
[http://www.thinkwiki.org/wiki/Ipw2200](http://www.thinkwiki.org/wiki/Ipw2200)

I've got the ipw2200 in a ACER 2428 laptop and I've had a few problems with it, seems to be the ETH0 and ETH1 switching. ETH0 was my cable connection and ETH1 my wireless, but for some reason the cable connection even thought not connected switches to ETH1 and screws thinks up. I've disabled the cabble connection via NETWORK, but it still enables itself every so often.

---

