---
title: "Wired Network DHCP trouble"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by small_bird on 2007-07-08
Hi all!

I'm having a little trouble. I have ubuntu 7.04 on my laptop with an ethernet modem (seen as a wired connection). I'm getting my IP by DHCP. On my win XP it is done very quickly with no trouble. But on my Ubuntu it is not :(.

I can see the modem, I can ping and access my gateway(my modem) in firefox (so I can reset the modem from the laptop or do any settings). When I connect to my modem, in it's settings it is said that my MAC is 'Proprietary', so all seems good. 

Everything seems great, but after I try to connect, it says that 'You are connected to wired network', but I get almost all ip adresses equal to '0.0.0.0' in network manager. Seems like dhcp client does something wrong maybe.... Because the gateway itself is 100% working and I get my IP normally on winXP (just plug in the cable to my PC with XP and it's working. Plug in into my laptop with ubuntu - doesn't work :(  )... 

The dhcp server sends the IP addresses by the MAC addresses. The MAC address is registered by my ISP, so it must be known on the other side.

Here is some data, which is taken after I try to connect and get all IPs '0.0.0.0' in network manager:



[I]**$ ifconfig -a**
eth1      Link encap:Ethernet  HWaddr 00:16:36:4D:CF:3A  
          inet6 addr: fe80::216:36ff:fe4d:cf3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:447752 (437.2 KiB)  TX bytes:69316 (67.6 KiB)
          Interrupt:17 

eth1:avah Link encap:Ethernet  HWaddr 00:16:36:4D:CF:3A  
          inet addr:169.254.5.200  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15536 (15.1 KiB)  TX bytes:15536 (15.1 KiB)
**$ cat /etc/network/interfaces**
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


iface eth0 inet dhcp
address 87.237.115.100
netmask 255.0.0.0
gateway 87.237.115.1







auto eth0
**$ route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth1
default         *               0.0.0.0         U     1000   0        0 eth1
[/I]

---

### Post by small_bird on 2007-07-09
up...

---

