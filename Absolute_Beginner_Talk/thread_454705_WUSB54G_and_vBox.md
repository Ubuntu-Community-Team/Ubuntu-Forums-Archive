---
title: "WUSB54G and vBox"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by b_chris on 2007-05-25
Hello,

I am running Feisty on my T20 with the WUSB54G, all works fine, however when I run windows in VirtualBox I cannot get on the internet through the WUSB54G only when connected via the ethernet.

I have the following in my rc.local file

[COLOR="DarkRed"]# For Network Bridging/TAP to enable Virtual Box

# Set permissions of tun device
chown root:vboxusers /dev/net/tun

#Add a bridge, add rausb0
brctl addbr br0
ifconfig br0 rausb0 0.0.0.0 promisc
brctl addif br0 rausb0
dhclient br0

# Create tap1
tunctl -t tap1 -u user_name #Be sure to change user_name to your user name

# Enable tap1
brctl addif br0 tap1
ifconfig tap1 up

chmod 0666 /dev/net/tun[/COLOR]


When I sudo bash rc.local I get the following:

[COLOR="DarkRed"]device br0 already exists; can't create bridge with the same name
rausb0: Unknown host
ifconfig: `--help' gives usage information.
device rausb0 is already a member of a bridge; can't enslave it to bridge br0.
There is already a pid file /var/run/dhclient.pid with pid 5590
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/br0/00:18:f8:ac:4c:fd
Sending on   LPF/br0/00:18:f8:ac:4c:fd
Sending on   Socket/fallback
DHCPREQUEST on br0 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.1
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on br0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.103 -- renewal in 34348 seconds.
Set 'tap1' persistent and owned by uid 1000
device tap1 is already a member of a bridge; can't enslave it to bridge br0.
[/COLOR]

What concerns me is the rausb0:unknown host line.


Does anyone have any ideas?

Regards.

---

