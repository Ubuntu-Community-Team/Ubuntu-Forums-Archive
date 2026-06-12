---
title: "xubuntu and no ethernet card detected"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by mikeblob on 2006-08-26
i have an old pc, 200mmx- 96MB ram.

its working with win2000, but sluggish.

Due to hard to find display drivers for win, i wanted to try linux.

Installed xubuntu on a spare 4G drive, but it cant detect the ethernet card, cnet cn650eplus.

ifconfig in console gives only:

lo  link encap:local loopback
    inet addr:127.0.0.1 mask:255.0.0.0
    UP LOOPBACK RUNNING MTU:16436 Metric:1
    RX packets:3 errors:0 dropped:0 overruns:0 frame:0
    TX packets:3 errors:0 dropped:0 overruns:0 carrier:0

    collisions:0 txqueelen:0
    RX bytes:172 (172.0 b) TX bytes:172 (172.0 b)

Edit: typed dmesg in console, and on one line it said:

[41.136052] isapnp: card `CNet 650Eplus PoerNIC


seems it doesnt find any card or eth0, im on broadband and modem.

any chance to get it online?

---

