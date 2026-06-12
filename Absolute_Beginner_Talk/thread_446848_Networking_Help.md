---
title: "Networking Help"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by swatF1RESTORM on 2007-05-17
I need some help getting things set up on my network. First I'll say what I'm trying to accomplish. I have wifi access at home and at work. Ubuntu is running on my laptop (which I bring to work everyday) All other computers on the network are windows machines (with the exception of a co-workers Mac that also connects through wifi).

Anyways I want to be able to switch back and forth between the wifi network (both at home and work) and the LAN (at work) on my laptop. I have tried entering the information for my network through the 'Manual configuration' option. I have saved 2 different locations under my network manager; Wired & Wireless. I can't seem to disable Roaming Mode under Wireless connection-->Properties. Every time I uncheck the box that says 'Enable roaming mode' and click 'Ok' the wireless connection still seems to be active and roaming. After repeating these steps a couple of times the icon in the upper right panel (taskbar, sorry X-windows user ><) changes to an icon that looks like 2 PCs connected. I can access most of the places on the network but I'm not sure which connection I am using. 

I have a network desklet on my desktop and no matter what location I use, either Wired or Wireless, it still lists the network device at eth0. Shouldn't that read wlan0 when in Wireless and eth0 when in Wired? That makes the most sense to me and that's how I would like to have it setup.

Things are workable now so I am hesitant to make any changes but I would like to have my network setup correctly and logically. I figured I would ask for help FIRST this time BEFORE screwing up what I have now.

Here is what's in /etc/network/interfaces:
_______________________________________________________________________________________
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface eth0 inet static
address <address>
netmask <netmask>
gateway <gateway>

auth eth0
_______________________________________________________________________________________

This is what I get when I try to reconfigure the network interfaces:

"sudo /etc/init.d/networking restart" (minus quotes) --> produces the following:
_______________________________________________________________________________________

  * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:11:d8:e1:c8:d1
Sending on   LPF/eth1/00:11:d8:e1:c8:d1
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:11:d8:e1:c8:d1
Sending on   LPF/eth1/00:11:d8:e1:c8:d1
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
SIOCADDRT: File exists
Failed to bring up eth0.
_______________________________________________________________________________________

Not sure what a lot of that means but I see a lot of ERRORs and that usually isn't a good thing. This is under the 'Wired' location I setup and the ethernet cable is plugged in. What I don't get though is the last thing it said was 'Failed to bring up eth0' and yet I am still able to browse the web.

Any ideas?

swatF1RESTORM

---

### Post by swatF1RESTORM on 2007-05-17
bump

---

### Post by swatF1RESTORM on 2007-05-17
Anyone?

swatF1RESTORM

---

### Post by swatF1RESTORM on 2007-05-18
Any luck this morning?

---

### Post by Kurt-A on 2007-05-25
What i can see, is that eth1 gets ip 192.168.1.1 at the top. All the other errors are simply missing network devices. 

If you add :    
auto my-network-card
iface my-network-card inet dhcp

to the /etc/network/interfaces file, you would get an error message saying my-network-card is not present.

Hopefully that will answer why you get those error messages.

---

