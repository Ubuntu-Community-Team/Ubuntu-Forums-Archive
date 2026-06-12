---
title: "No DHCPOFFERS received. Wireless."
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-10-25
```

erin@erin-desktop:/etc/rc2.d$ sudo dhclient3 ra0 
There is already a pid file /var/run/dhclient.pid with pid 6666 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

Listening on LPF/ra0/00:0f:ea:68:d3:e9 
Sending on   LPF/ra0/00:0f:ea:68:d3:e9 
Sending on   Socket/fallback 
DHCPREQUEST on ra0 to 255.255.255.255 port 67 
DHCPREQUEST on ra0 to 255.255.255.255 port 67 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14 
No DHCPOFFERS received. 
Trying recorded lease 192.168.2.3 
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data. 

--- 192.168.2.1 ping statistics --- 
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms 

No working leases in persistent database - sleeping. 
erin@erin-desktop:/etc/rc2.d$ 

```

I have a gigabyte GN-WPKG. with the rt2500 chipset.  I've uninstalled gnome network manager.  DHCP server is enabled on the router.

This is what I've done: 

```

cd /etc/init.d/
gksudo gedit wireless-up

```

```

#!/bin/dash
ifconfig ra0 down
iwconfig ra0 essid "your essid"
iwconfig ra0 key "your wep key if you have one"
ifconfig ra0 up
dhclient3 ra0

```
Pasted his is inside the file "wireless-up".  This file is set to run on startup.

```

sudo chmod o+x ./wireless-up
cd /etc/rc2.d/
sudo ln -s /etc/init.d/wireless-up ./S14wireless-up

```

I noticed that when I started, it did not connect.  So I tried typing each of the commands in the text file individually.  And that's how I got the no DHCP offers recieved problem.

I think it might be the wrong wep key.  I disabled the WEP key and I just left it as 

iwconfig ra0 key s:

inside the text file.


Any help would be greatly appreciated, This is getting really annoying.

---

### Post by chili555 on 2007-10-25
The s: preceding the key implies it's an ASCII key. I haven't seen ASCII keys used in wireless routers for many years. That doesn't mean you don't have it; just that it's rare. 

Did you disable the key in the router? If you have administrative access to the router, then you should be able to verify you have the correct key. I would simply remove the key wording from your wireless-up file.

If it works, I would try the verified WEP key again, without s:.

---

