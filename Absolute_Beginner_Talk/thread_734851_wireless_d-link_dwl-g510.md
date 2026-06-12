---
title: "wireless d-link dwl-g510"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by padeco on 2008-03-25
hi there,

installed wireless in my pc (amd 2.0ghz, 1.2 G ram) running ubuntu 7.10.

it only connects to the wireless router for about 10 -15 mins and then freezes / crashes. it is quit weird.

i tried many links and other posts however, it still crashing after a short period of time. would any one be able to assist, in quite simple terms, as to how i may be able to get out of this one. i have kicked windows away for over 4 yrs and do not want to go back at all!!!! so any help is much appreciated.

regards,
padeco

some outcome:
:~$sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: wmaster0
       version: 00
       serial: 00:1b:11:bb:a6:ed
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g


:~$iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:5B:55:E4:41   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 16331
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:11:bb:a6:ed
Sending on   LPF/wlan0/00:1b:11:bb:a6:ed
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
Trying recorded lease 192.168.0.100
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
Terminated

---

### Post by Helios38 on 2008-03-25
tried ndiswrapper with window drivers?

---

### Post by padeco on 2008-03-26
i cannot get ndiswrapper to work. i can get connected to the net, the only thing is that it crashes after 15 mins. if you have a nice easy step to follow to install the software i&#314;l have a go at it.
thanks, 
padeco

---

### Post by apothecaryaaron on 2008-03-26
There are 3 different Revisions of that card, and they all act differently, Revision C is supposed to take some work, I think.
 
I have revision B of that card, the Restricted drivers worked first try in gutsy. It created a wlan0 and an ath0 interface, which confused me for a while, but it worked with Network Manager. I had to install the newest madwifi with my feisty install.

---

### Post by jan quark on 2008-03-26
you can also try the network connection software WiCD
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

perhaps it is just a matter of the nm-applet

---

### Post by Marat Galiev on 2008-03-26
Hi guys!
I'm using D-Link DL-110 adapter.
and i'm trying windows drivers.
It fork fine for me.

---

### Post by padeco on 2008-03-27
many thanks!
i have tried wcid, no luck!

how can i enable restricted drivers? may be i'll try that option.

thanks,
padeco

---

