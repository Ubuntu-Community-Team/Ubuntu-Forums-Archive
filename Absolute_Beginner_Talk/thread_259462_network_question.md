---
title: "network question"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by deltad on 2006-09-17
Hello. I've just installed Ubuntu 5.10 for the first time.  I'm excited to check it out but I'm having some trouble accessing the internet.  I've connected through my router and configured my network settings for DHCP.  I can access the router setup page through Firefox but the web.  The eth0 connection status seems to vaccilate between "idle" and "receiving."  (btw: no trouble connecting to the web with my windows PC which is on the same network).  I don't know much about anything so I'm guessing I've just overlooked something fairly straightforward.  Any suggestions?

Thanks

---

### Post by Garyu on 2006-09-17
hmm, why did you install breezy instead of dapper? dapper has a lot of added functionality.

did you reboot your machine? sometimes it takes a couple of reboots before anything happens. 

you could also try from the menu System -> Administration -> Network. There you will find eth0 and possibly a modem that is deactivated. Choose eth0 and the deactivate. Wait a few seconds and then activate it again. That might fix you up. At least this works for ADSL dhcp that isn't working properly.

---

