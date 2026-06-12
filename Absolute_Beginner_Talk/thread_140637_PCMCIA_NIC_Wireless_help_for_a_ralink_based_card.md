---
title: "PCMCIA NIC Wireless help for a ralink based card"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by Cedfelix on 2006-03-06
I have been all over the forums getting help installing my new wireless card (Zonet ZEW1501) to kubuntu. The problem is that when i activate my card from system settings/network settings, it says "Enabling interface **ra0**" for about 30 secs. to a minute. After it is done, it immideatly goes back to disable wireless network device. Also, i get no blinking lights on the card itself. 

Here are a list of links that i have tried. 

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide")
This was good, helped me get my machine to recognise the card.

I haven't used mdiswrapper because [this]("https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo") says it should use the supplied driver. Although it also [talks about installing the Raconifg]("https://wiki.ubuntu.com/WifiDocs/RalinkRT2500/DriverAndRaconfig"), but that seems scary and also, i have no internet access on that machine to do so. 

ifconfig shows this
```
link encap:ethernet HW addr 00:06:F4:0C:53:DE
inet6 addr: fe80::206:f4ff:fe0c:53de/64 Scope: Link
UP BROADCAST RUNNING MYLTICAST  MTU:1500 Metric:1
RX packets:0 errors0 dropped:0 overruns:0 frame:0
RX packets:2340 errors:0 dropped:0 overruns:0 carrier:0
collisions:4 txqueuelen:1000
RX bytes:0 (0,0 b) TX bytes:76085 (74.3 KiB)
Interrupt:11 Base address:0x4000
```

Anyone got any ideas? Please keep it relatively simple, I am just a poor newb.

---

### Post by Cedfelix on 2006-03-06
One more thing, when I run "sudo ifup ra0" to enable the card, it gives me this.
```
there is already a pid file /var/run/dhclient.ra0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
...(Copyright, rights, for infot, etc)...

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ra0/00:06:f4:0c:53:de
Sending on  LPF/ra0/00:06:f4:0c:53:de
Sending on  Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
no DHCPOFFERS recieved.
No working leases in persistent database - sleeping.
```

Does this mean since it cant find a network, it goes to sleep?

I also get the same message when i run "sudo dhclient ra0", but for intervals at 3,7,15,19,12, and 5.

---

### Post by essexman on 2006-03-19
[quote=Cedfelix]One more thing, when I run "sudo ifup ra0" to enable the card, it gives me this.
```
there is already a pid file /var/run/dhclient.ra0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
...(Copyright, rights, for infot, etc)...

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ra0/00:06:f4:0c:53:de
Sending on  LPF/ra0/00:06:f4:0c:53:de
Sending on  Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
no DHCPOFFERS recieved.
No working leases in persistent database - sleeping.
``` 
Does this mean since it cant find a network, it goes to sleep?

I also get the same message when i run "sudo dhclient ra0", but for intervals at 3,7,15,19,12, and 5.[/quote]

This is a bug please go to [https://launchpad.net/distros/ubuntu/+source/knetworkconf/+bug/35129]("https://launchpad.net/distros/ubuntu/+source/knetworkconf/+bug/35129")

and add a "me too" to get developers to fix it

---

