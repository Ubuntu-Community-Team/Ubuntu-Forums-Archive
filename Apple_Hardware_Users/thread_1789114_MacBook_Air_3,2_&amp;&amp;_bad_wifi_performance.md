---
title: "MacBook Air 3,2 &amp;&amp; bad wifi performance"
date: 2011-06-23
forum: Apple Hardware Users
---

### Post by gwillem on 2011-06-23
Hi, running natty 64bit @ MBA3,2.

Wifi performance is *sometimes* abysmal (~200ms ping to AP, 10% packetloss) with my Linksys WRT54Gv2 AP. 

It is not the hardware, as there is no wifi problem while running MacOSX at the same location. 

It is not the location, as MacOSX works fine (~6ms), and so does another computer with wifi connection (~1ms) on the same desk. 

So I'm suspecting the driver: Broadcom BCM4353 802.11 Hybrid Wireless Controller 5.100.82.38. 

Did anyone experience the same issues and, hopefully, solve it somehow?

Tnx

---

### Post by gwillem on 2011-07-07
This is quite a killer :( have to resort to macosx because ubuntu gives me 80% packetloss, am sitting in major internet cafe right now.

---

### Post by starwed on 2011-09-07
I just installed natty on my Air and had the same issue -- notably synaptic would insta-kill the connection, which made it impossible to upgrade anything!

Disabling the (proprietary) Broadcom driver completely fixed it.

I just went into the interface for finding such special hardware drivers, removed it, and Ubuntu switched back to something that worked automatically.

---

### Post by Lusse on 2011-09-08
This might have something to do with the power saving "features" of this card. See if running the command below will temporarily fix the issue.

iwconfig eth0 power off

You might have to change eth0 to something else (e.g. eth1, wlan0, wlan1) but on my MacBook Air 3,2 it's eth0.

---

