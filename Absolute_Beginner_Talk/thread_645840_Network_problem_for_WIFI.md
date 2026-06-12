---
title: "Network problem for WIFI"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Julian Lewis on 2007-12-20
A wireless problem on my COMPAL IFL91

I have no internet access on my daughters Laptop, but I can access my home network from it no problem, so there isnt a hardware problem.
I can ping 208.67.219.101 and I can ping my router, I can even play films off my network drive.
I can not use any application like Firefox, Skype, Miro etc, they do not find a server.
What is important is that it did work correctly when I gave it to my daughter, then something went wrong.
I am using a fixed IP address and have a good router connection.
If I run KwiFiManager it shows a good signal and reports no problem.
My router is able to support my other personnel Ubuntu laptop no problem with a fixed IP
It seems that there was an eth1 and eth0 before but I cant be sure.
This is what comes out of iwconfig ...
 
alexandra@alexandra-laptop:~$ iwconfig

lo        no wireless extensions.



eth2      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11g  ESSID:"JulianLewisLeaz"  

          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:4D:18:D9:68   

          Bit Rate=54 Mb/s   

          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   

          Link Quality=93/100  Signal level=-20 dBm  Noise level=-87 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


This is what comes out of ifconfig ...

alexandra@alexandra-laptop:~$ ifconfig

eth2      Link encap:Ethernet  HWaddr 00:1B:38:62:E7:78  

          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0

          inet6 addr: fe80::21b:38ff:fe62:e778/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:4639 errors:0 dropped:0 overruns:0 frame:0

          TX packets:3890 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:4492272 (4.2 MB)  TX bytes:787225 (768.7 KB)

          Interrupt:16 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



wlan0     Link encap:Ethernet  HWaddr 00:1D:E0:12:C1:71  

          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0

          inet6 addr: fe80::21d:e0ff:fe12:c171/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:6387 errors:0 dropped:0 overruns:0 frame:0

          TX packets:3395 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:6598589 (6.2 MB)  TX bytes:400549 (391.1 KB)



wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-12-C1-71-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


When I do an lsmod these are the wireless modules ...

iwl4965               101480  0 

iwlwifi_mac80211      175112  1 iwl4965


and finally this is what comes out of lshw -C network...

alexandra@alexandra-laptop:~$ sudo lshw -C network

  *-network               

       description: Ethernet interface

       product: NetLink BCM5906M Fast Ethernet PCI Express

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:04:00.0

       logical name: eth2

       version: 02

       serial: 00:1b:38:62:e7:78

       size: 100MB/s

       capacity: 100MB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full ip=192.168.0.2 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

  *-network

       description: Wireless interface

       product: PRO/Wireless 4965 AG or AGN Network Connection

       vendor: Intel Corporation

       physical id: 0

       bus info: pci@0000:0c:00.0

       logical name: wmaster0

       version: 61

       serial: 00:1d:e0:12:c1:71

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=iwl4965 ip=192.168.0.9 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g


Help !!!

---

### Post by jbt on 2007-12-20
Hi,

It sounds like one of two problems:

1) DNS
   Do you have the correct DNS server set on the machine ?

2) Routing
  Do you have a route set correctly ?

try route -v

you should only see the wireless interface, and there should be a default route in it.

if that works - try:
ping 91.189.94.158

if that works try:

ping ubuntu.com

if that works then maybe a firewall problem ?

Regards
JohnT

---

### Post by Julian Lewis on 2007-12-22
Thanks, that was exactly my problem.
In the network manager it fills in the sub mask automatically for you, and I assumed I didnt need to put anything in the gateway because the OK was green. In fact all the fields must be filled in correctly. Big thanks that sorted out my problem

---

