---
title: "problems making my laptop work wirelessly &gt;.&lt;"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by Chii on 2005-09-30
I recently installed Ubuntu on my laptop which is a ze5400, and it has a built in wireless internet card and Ive been attempting to get it to work with ndiswrapper.

Ive installed the WPA supplicant as well, but when I try to do a sudo dhclient wlan0, this is what I get :/

There is already a pid file /var/run/dhclient.pid with pid 19096
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0b:cd:75:73:e6
Sending on   LPF/wlan0/00:0b:cd:75:73:e6
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Now apparantly something is not connecting :/  How would I remedy this?
Is it a probem with the hardware/software interacting or could it be something with my router?

This problem with connecting is only with my wireless card, as Im able to use the internet if my computer is connected to the router via an ethernet chord >.<

---

### Post by mlomker on 2005-09-30
Either you need to try a different driver with ndiswrapper or something's wrong with your encryption setup.

Post the output of:

```

ifconfig wlan0
iwconfig wlan0
ndiswrapper -l

```

---

### Post by Chii on 2005-12-10
I realize this post was made a while back but since I started it I want to finish it so that it can be closed so to say.  But I recently installed the non-beta version of breezy badger and downloaded the wireless tools, which made it a lot easier to configure my wireless card.  So now I am successfully connected to the network.  

Thank you for taking the time to help me, and sorry I disappeared :/ But I got very busy with school.

---

