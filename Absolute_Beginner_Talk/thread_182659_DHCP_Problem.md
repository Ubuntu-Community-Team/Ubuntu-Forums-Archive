---
title: "DHCP Problem"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by alanphil on 2006-05-26
I'm running a current beta of Dapper Drake on a Thinkpad x30 laptop, and having some issues getting DHCP to work properly. I've run hardware diagnostics and the laptop hardware doesn't seem to be the problem. I've also tried multiple network cables and different networks. The only way I can get online with this machine is to assign a static IP. Then everything works fine.

I'm new to troubleshooting DHCP issues. Below is the output from dhclient at the command line. Please let me know what other details would be helpful to troubleshoot this -- and thanks in advance for any help! ](*,) 

sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:09:6b:60:d0:79
Sending on LPF/eth0/00:09:6b:60:d0:79
Sending on Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 140.220.250.35
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by clint1010 on 2006-05-26
Have you checked your router settings? it may be setup to supply a static address. were you using breezy before installing drake? and if so was it functioning ok?

it would seem that your pc is waiting to accept an IP, but isn't being supplied one by your router

---

### Post by Iowan on 2006-05-26
Along the same lines... What is *supposed* to be providing DHCP addresses?  If it's the router, does it have DHCP enabled?
> DHCPNAK from 140.220.250.35 :confused:

---

