---
title: "Wireless prob - no IP"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by timebomb on 2007-03-10
Greetings all-

Totally new to Ubuntu and linux (3 weeks). Common refrain on these boards, but I cannot connect to my wireless router.  All seems to work but the router is not offering an IP.  I've trawled through the docs and boards and saw similar requests.  I can scan area and see all local networks, suggesting the driver (IPW2200) is operational.  I'm running 6.10.

Onwards - Interfaces: 
> auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid WIRELESS
wireless-key restricted WIRELESS_KEY

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0

iface wlan0 inet dhcp
auto eth0

Output of iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"WIRELESS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:09:5B:27:28:8C   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=-28 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:282  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Output of eth1 on ifconfig (no IP address here):
> eth1      Link encap:Ethernet  HWaddr 00:0E:35:74:94:96  
          inet6 addr: fe80::20e:35ff:fe74:9496/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:516 errors:297 dropped:297 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:6144 (6.0 KiB)
          Interrupt:5 Base address:0xc000 Memory:fafef000-fafeffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

Output to sudo dhclient eth1:
> There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:74:94:96
Sending on   LPF/eth1/00:0e:35:74:94:96
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any advice appreciated.

---

### Post by oilchangeguy on 2007-03-10
do you have wep or wpa enabled?

---

### Post by timebomb on 2007-03-10
> do you have wep or wpa enabled?

WEP is enabled.

---

### Post by oilchangeguy on 2007-03-10
not sure about 6.10, but in 6.06 a double screened icon shows next to the clock. open this and select wlan0 and from there you'll need to enter your security code. re-start the computer and just to make sure the router also, and see what happens.

---

### Post by timebomb on 2007-03-10
Thanks for the quick responses.  

The network connection icon only gives me the options of eth0 or lo (never eth1).  I thought this might be an issue - maybe it is? - but I can see and configure my wireless connection through the System | Administration | Networking GUI.  These remain the same through various re-boots, whether restarting the OS or the router.

---

### Post by eljalill on 2007-03-10
The double screen icon always only shows you the active connections... no idea why.
I had a smililar problem and switching to NetworkManager helped... again no idea why.
.... miraculous things these wireless networks... ;)

---

### Post by timebomb on 2007-03-10
I installed network manager, but it doesn't seem to do much (other than tell me when I am unplugging or plugging in my ethernet cable).  I also tried some of the other managers like Wi-Fi radar and Wireless assistant.  They can also scan and see local networks but cannot connect.  I've uninstalled each thinking it may be best to strip the system down and avoid conflicts.

---

### Post by timebomb on 2007-03-11
Resolution to this problem on:
[http://www.ubuntuforums.org/showthread.php?t=381327](http://www.ubuntuforums.org/showthread.php?t=381327)

Thanks to all for the help.

---

