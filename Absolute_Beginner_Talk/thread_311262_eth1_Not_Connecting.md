---
title: "eth1 Not Connecting"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-12-02
Earlier today I deactivated my connections. Well, now I'm trying to reactivate them but it seems to be giving me some trouble. I know that theres a Networking Forum, but I think that this is more of a beginners problem and I think I'm just overlooking something big here. But when I went in to deactivate everything it showed me my wireless connections along with the ethernet connections. I have no idea why there is an eth1 *and* an eth0, but it says that eth0 is my default. eth0 is also the one that I'm having trouble with.

It shows me the bars for my wireless connection to the router, so I know that's all good. But when I try to activate eth0, it takes about 2 minutes to activate and then I click OK and it stalls for about 3 or 4 minutes before finally closing. Even after all that though it still shows no connection next to the bars for the wireless signal and the internet will still not connect. 

Will somebody please guide me? Much appreciated.

---

### Post by mthakur2006 on 2006-12-02
Please post us the results of

iwconfig

and 

ifconfig

Then we might be able to help :)

---

### Post by voodoonirvana on 2006-12-02
> **mthakur2006 said:**
> Please post us the results of

iwconfig

and 

ifconfig

Then we might be able to help :)

Sure thing.


**iwconfig:**

lo           no wireless extensions

eth0         no wireless extensions

wifi0        no wireless extensions

eth1         IEEE 802.11-DS Mode:Managed
             Link Quality: 43/92  Signal Level:-65 dBm  Noise Level:-91 dBm
             Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
             Tx excessive retries:0  Invalid misc:0  Missed beacon:0





**ifconfig:**


Theres way too much to copy over to this computer by hand so Ill give you what I think is important.

All the variables for eth0 are zero.

eth1
     Rx Packets:487 errors:0 dropped:0 overruns:0 frame:0
     Tx packets:67  errors:0 dropped:0 overruns:0 frame:0
     collosions:0 txquelen:0
     Rx bytes:44817(43.7 kb)  TX bytes:6336 (6.1 kb)
     interrupt:3 base address:0x9100

lo   Link encap:local loopback
     inet addr:127.0.0.1  Mask:255.0.0.0
     inet6 addr: ::1/128 Scope:host
     The rest of the variables are zero except-
     RX bytes: 1768 (1.7 kb)  TX bytes:1768 (1.7 kb)


whew, hope you can help.

---

### Post by voodoonirvana on 2006-12-02
Anyone?

Also, if someone could tell me how to add a new connection then I might have it figured out. I was just told that we switched out our router a few days ago, but that still doesn't explain why it was working fine earlier today. But could that have anything to do with why I'm not able to reconnect to the network. It is a Windows network by the way.

---

### Post by voodoonirvana on 2006-12-02
Hahaha, wow...just wow. I wish computers could talk. I just rebooted and it's back up and running again! So weird. Thanks anyway.:rolleyes:

---

### Post by mthakur2006 on 2006-12-31
Apologies for not replying, my network went down :)
But good to know you are back up....
:-D

---

