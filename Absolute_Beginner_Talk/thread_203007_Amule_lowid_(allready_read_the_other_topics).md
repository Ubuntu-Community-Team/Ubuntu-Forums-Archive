---
title: "Amule lowid (allready read the other topics)"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by falkenberg_cph on 2006-06-24
Hi
I get a low id in amule and it says KAD is firewalled.
I have forwarded port 4662, 4665 and 4672 on my linksys wrt54g router.
I have also allowed inbound traffic from port 4662-4672 in firestarter. which also have permissive outbound traffic.

strange thing is. typing route -n i get this:
Destination_____Gateway_____Genmask_______Flags Metric Ref_____Use Iface
xxx.xx.x.0______0.0.0.0_______255.255.255.0__U____0_____0______0___eth0
0.0.0.0_________xxx.xx.100____0.0.0.0_______UG____0____0_______0___eth0

The gateway is correct. but i have set up my network like this:
DHCP:
IP._______xxx.xx.x.130
subnet.___255.255.255.0
gateway._xxx.xx.x.100

Shouldnt the first destination equal my static ip, that is: xxx.xx.x.130?

What else could cause my low id - i think i have setup everything correct.

Thank you
Carsten

PS: sorry for the confusing layout

---

### Post by cacharreo on 2006-06-24
For this purpose you should visit the amule forum:
[http://forum.amule.org/](http://forum.amule.org/)

---

### Post by falkenberg_cph on 2006-06-24
ok. thanks.

---

### Post by falkenberg_cph on 2006-06-24
Well. Someone in the amule forum says its not an amule problem, but a problem with my router/firewall. Please re-read my topic (and perhaps also take a look at my new thread, which could be related to this one - maybe)
[http://www.ubuntuforums.org/showthread.php?t=203127](http://www.ubuntuforums.org/showthread.php?t=203127)

Carsten

---

