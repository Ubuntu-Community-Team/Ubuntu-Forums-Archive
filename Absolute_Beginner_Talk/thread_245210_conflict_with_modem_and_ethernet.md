---
title: "conflict with modem and ethernet"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by tobmeister on 2006-08-27
After installing Ubuntu 5.05, attempted to go online via external modem. The modem dialed in but I was unable transfer data.  I had this same problem with Mandriva 2006 and I knew that I had to disable the ethernet card to use the modem.  I found that I had the same problem with ubunto.  What can I do to utilize bot hte modem (For online use) and the ethernet (For home network)?

Thanks

Tobmeister](*,)

---

### Post by gborzi on 2006-08-27
The problem can be on how you configured your ethernet card. If your configuration specify a complete routing table this may conflict with the routing table activated by ppp. To avoid such a conflict I use something like this for my laptop:
> iface eth0 inet static
      address 192.168.1.2
      netmask 255.255.255.0
Note that there isn't a gateway, to avoid having a complete routing table. My ISP assigns address in the 192.168.100.[0-255] range so there is no conflict with eth0.

---

### Post by tobmeister on 2006-08-27
Hey thanks,

I think that worked.  So in the future, I should set a static IP address for my system that is also running a modem.  This is good info!

Cheers, 

Tobmeister

:)

---

### Post by gborzi on 2006-08-27
I think some explanation is needed here. Your computer connects to the internet using a routing table, i.e. a set of rules to communicate with other ip addresses. A typical (and very basic) routing table is as such
> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
where each rule is specified in one line. The first line (=rule) says that to connect to any IP address in the 192.168.0.[0-255] range a direct connection is used. There is no gateway to use in this range. The second rule states that to connect to any other IP address it must go through a gateway, in this case "192.168.0.1". Note that the gateway must be reachable in the first rule.
So if you configure your ethernet card with an ip address **and a gateway** every time you try to connect to an IP address your computer will try to contact the gateway, but if your ethernet is disconnected the communication fails. With such a configuration, when you activate a ppp connection other rules are added, but never used because the rules for eth0 "swallow" every attempt to connect. To avoid this problem, use an incomplete set of rules for eth0, i.e. restrict the range of IP address managed by this interface by not specifying a gateway.
I hope this explanation is clear enough.

---

