---
title: "PlaneShift Server keeps Failing"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-04-03
I can't connect to the planeshift server for some reason.  Has anyone else had this problem? [Here]("http://www.planeshift.it/quickstart.html") it says it needs port 7777 so i forwarded it on my router and i did iptables for it.  The command i used for iptables is
```
sudo iptables -A INPUT -p udp -d 0/0 -s 0/0 --dport 7777 -j ACCEPT
``` for TCP and UDP.  Did i do something wron with that, because i don't know anything about iptables.  Also i don't have a firewall.
found only 2 topics about this, 1 said don't use the updater and i havent.

---

