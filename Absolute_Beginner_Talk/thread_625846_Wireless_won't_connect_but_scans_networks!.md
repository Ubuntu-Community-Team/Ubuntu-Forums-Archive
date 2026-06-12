---
title: "Wireless won't connect but scans networks!"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-11-28
Hey all =]
I've just upgraded to gusty and I'm trying to get my wireless working but it's just problem after problem after problem. I'm up to the stage where I can scan networks and it picks all the ones in my area up (including the one I want to connect to) but I can't actually connect to them! Here is hopefully every command I thought you'd need to look at:

lsusb
```

Bus 002 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 08ec:0020 M-Systems Flash Disk Pioneers
Bus 001 Device 002: ID 046d:c50a Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

```

ndiswrapper -l
```

rt2500usb : driver installed
device (050D:7050) present (alternate driver: rt73usb)

```

lshw (*network and usb entries*)
```

*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:4c:37:c8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
*-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 13
             bus info: pci@0000:00:13.0
             logical name: eth0
             version: 10
             serial: 00:20:ed:19:a6:09
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd       autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

*-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.3
             bus info: pci@0000:00:11.3
             version: 23
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
*-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.2
             bus info: pci@0000:00:11.2
             version: 23
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd

```
 
iwconfig
```


lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:20:ED:19:A6:09
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x8f00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:4C:37:C8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-4C-37-C8-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Sorry about all the code!!!
At a total random stab in the dark, I'm going with that wmaster0 being the problem. It doesn't show up in /etc/network/interfaces, has a ridiculously long hardware address and 'dhclient' gives the error'wmaster0: unknown hardware address type 801'.
But that is a stab in the dark!
Thanks for any help :)

---

### Post by Casual Fan on 2007-11-28
This is a stupid question, but you can get to the point where it asks you for your wireless key and IP address, right? And it just won't connect after that is entered?

---

### Post by tartarian on 2007-11-28
Nah its not a stupid question, I should have made it clear. I'm trying to connect through the command line because Knetworkmanager scans my network, then tries to connect (gets to 57%) and then says, Unable to connect to WANADOO-3EB4
So I've tried setting it all using sudo iwconfig but that doesn't work either. 
So I'm kinda stuck :(

---

### Post by tartarian on 2007-11-28
sorry....
but *bump*

---

