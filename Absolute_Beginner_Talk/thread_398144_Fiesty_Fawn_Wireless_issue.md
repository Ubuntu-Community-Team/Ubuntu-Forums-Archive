---
title: "Fiesty Fawn Wireless issue"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by prgsdw on 2007-03-31
Hello all, 

I have a Thinkpad R40 with a Cisco Aironet mini-pci wireless card installed. I have been running Ubuntu 6.10 for a month or so with no issues. This afternoon, I ran an upgrade to check out fiesty fawn beta. I did the upgrade via the instructions from the FiestyUgrades page here at Ubuntu forums (i.e., update-manager -d from a command prompt and followed instructions). 

I think the issue may be that I did this over my wireless connection. Since the upgrade, I can no longer connect to my wireless router. I've removed the WEP key and also set the router to broadcast it's SSID till I get this to work. 

If I run lspci, I can see the wireless card was detected (highlighted below).

[INDENT]$ sudo lspci

Password:

00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)

00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

[B]02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b

[/B]02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
[/INDENT]

Also, iwconfig seems to show the eth1 associated with the proper access point (WIRELESS_NET) - there is also a wifi0 which I believe was there under edgy as well:

[INDENT]$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



irda0     no wireless extensions.



eth1      IEEE 802.11-DS  ESSID:"WIRELESS_NET"  

          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:4D:52:83:A8   

          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  

          Retry limit:16   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality=100/100  Signal level=-37 dBm  Noise level=-97 dBm

          Rx invalid nwid:184  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:3017   Missed beacon:0



wifi0     IEEE 802.11-DS  ESSID:"WIRELESS_NET"  

          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:4D:52:83:A8   

          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  

          Retry limit:16   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality=100/100  Signal level=-37 dBm  Noise level=-97 dBm

          Rx invalid nwid:184  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:3017   Missed beacon:0



$ 

[/INDENT]

This is the way things look when I boot, I can't ping anything or access the web via a browser. It looks like the airo kernel module is loaded fine as it was under edgy:

[INDENT]$ sudo lsmod | grep -i airo
airo                   74400  0 
$ [/INDENT]

So, I think the issue is dhcp related, but not sure why...I can get on the net (and that is how I am typing this post) by manually running a dhclient and associating it with eth1 like this:

[INDENT]$ sudo dhclient eth1

There is already a pid file /var/run/dhclient.pid with pid 5919

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.0.4

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



wifi0: unknown hardware address type 801

wifi0: unknown hardware address type 801

Listening on LPF/eth1/00:02:8a:df:6d:82

Sending on   LPF/eth1/00:02:8a:df:6d:82

Sending on   Socket/fallback

DHCPREQUEST on eth1 to 255.255.255.255 port 67

ip length 314 disagrees with bytes received 534.

accepting packet with data after udp payload.

DHCPACK from 192.168.1.1

bound to 192.168.1.2 -- renewal in 34496 seconds.

$ 

[/INDENT]


I'm concerned about the wifi0: unknown hardware address type 801, but it seems to fall back to the eth1 connection. Not sure why this same thing isn't happening when the system boots? Here is the contents of my /etc/network/interfaces file:

[INDENT]$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface eth1 inet dhcp
wireless-essid WIRELESS_NET
auto eth1

iface wifi0 inet dhcp
wireless-essid WIRELESS_NET
$ 

[/INDENT]

I'd very much appreciate any ideas on how to resolve this...it was working sweet under edgy. Thanks a lot!

Steve

---

### Post by prgsdw on 2007-04-01
Well, I removed the network-manager via:

asudo apt-get remove network-manager

rebooted the machine and wireless connected fine. I've gone ahead and reconfigured my router to not broadcast the SSID and to turn WEP back on, so all is back to the way it was under edgy - there must be some issues with network-manager and my config at a minimum. 

Steve

---

