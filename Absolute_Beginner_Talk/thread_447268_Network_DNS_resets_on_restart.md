---
title: "Network DNS resets on restart"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-05-17
Ok, so my problem is ubuntu's network program wont work right with just dhcp, even though that is what my router is for. THe solution is to just put in 192.168.0.1 in the DNS server config window, and then it works fine. On system restart this gets cleared though, and I do not know why. How do I make this persist?

---

### Post by wormser on 2007-05-17
I am not sure on a resolution but here is something to try.  In your router there usually is a place for DNS servers.  Put it in your DNS there and if you do not have one use 4.2.2.2 and 4.2.2.1.  Then try running **sudo dhclient** to get an ip.  Let us know if that works.

---

