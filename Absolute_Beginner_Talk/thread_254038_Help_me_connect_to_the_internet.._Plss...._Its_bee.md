---
title: "Help me connect to the internet.. Plss.... Its been 2 months"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by last_desp on 2006-09-09
Hi! I'm new to linux and I'm having trouble connecting to the internet.When I use the live cd I'm able to connect but after I installed it i could not connect. I use an ADSL connection that does need to login via PPPOE and has a dynamic IP. My connection goes like this:

ethernet[Cnet pro200]>Modem[Alcatel Home++500 ADSL modem]>internet.

I have tried the following and did not work:
-sudo PPPOE(just in case) it told me could not find access concentrator
-copy the configuration from etc folder

These are the following messages I get from:

**ifconfig**

eth0 Link encap:Ethernet HWaddr 00:08:A1:9A:07:F3
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:92 errors:219 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:6588 (6.4 KiB) TX bytes:2520 (2.4 KiB)
Interrupt:10 Base address:0xd000

**ifup**

^[[AListening on LPF/eth0/00:08:a1:9a:07:f3
Sending on LPF/eth0/00:08:a1:9a:07:f3
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

**ifdown**

Listening on LPF/eth0/00:08:a1:9a:07:f3
Sending on LPF/eth0/00:08:a1:9a:07:f3
Sending on Socket/fallback

---

