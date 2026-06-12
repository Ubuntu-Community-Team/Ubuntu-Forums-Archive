---
title: "Getting my Comcast connection back."
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Patrick Moore on 2008-03-07
My Comcast cable/wireless router connection worked fine until Wednesday evening, then kaput. The modem works fine with a borrowed MS laptop. Of course the CC techs can't help me with Ubuntu.

What do I do to get (1) the modem talking to the Ubuntu laptop via ethernet cable, and (2) the router talking to the Ubuntu laptop via the wireless card?

Thanks.

---

### Post by spiderbatdad on 2008-03-07
To find out if the problem is in your router, plug the network cable directly from the modem into your laptop. You will now have to reboot the modem. Remove the coax and power cables. Often they say 30 seconds is good. Often this is not true. Let the lease try to expire...wait at least five minutes, then power on the modem. Run ifconfig and sudo ifup eth0 on your linux terminal, if you dont see a connection.

To reconnect to the router, the modem will need to reboot again after reconnected to the router. You should also leave the router unplugged for awhile and reset it.

---

