---
title: "Almost there...need help on last step of wireless configuration"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-05-30
My usb wireless adapter (linksys wusb54gv1) is not supported, so I have to use ndiswrapper. I followed the instructions under system -> help and support  and almost have my wireless working. 

I copied by /etc/network/interfaces file from 6.06, and actually managed to get online briefly (without wpa enabled). However, it doesn't work with wpa. I'm not sure why

Here is what I get when I run /etc/init.d/networking restart

```

user@box:~$ sudo /etc/init.d/networking restart
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0c:41:fb:87:80
Sending on   LPF/wlan0/00:0c:41:fb:87:80
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0c:41:fb:87:80
Sending on   LPF/wlan0/00:0c:41:fb:87:80
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

So it sees the router, but for some reason don't connect...

here is the interfaces file

```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
#wpa-conf managed (commented out after reading sticky in networking forum)
wpa-ssid ubuntu
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 7825aec1be9f0...and so on
wireless-essid ubuntu

```

---

