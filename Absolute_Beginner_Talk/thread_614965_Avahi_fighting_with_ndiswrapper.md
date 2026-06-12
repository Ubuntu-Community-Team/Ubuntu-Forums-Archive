---
title: "Avahi fighting with ndiswrapper"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Tatterdemalian on 2007-11-16
I'm having a problem with wireless networking on my Ubunty 7.10 Gutsy 64-bit AMD system. Apparently one of the daemons in the avahi package that comes with Gutsy doesn't like ndiswrapper. For a while after every reboot, my wireless works just fine. However, eventually it stops working. When this happens, everything is reported as normal by ndiswrapper, lspci, iwconfig, etc., except ifconfig reports that a new interface, wlan0:avahi, has been created, that wlan0 (my usual wireless interface) no longer supports IPv4 communication, and the new interface is the only one that supports it.

Has anyone else had this problem? Apparently the interface management in Gutsy only supports the IPv4 network protocol through avahi; disabling or removing avahi eliminates all support for IPv4 in all my interfaces, including wlan0, and often makes Ubuntu crash so badly it has to be cold-booted, as I can't even switch to a getty session.

Does anyone know why avahi is doing this, and what I can do to make it stay the way it is when the system is first started up?

---

### Post by Tatterdemalian on 2007-11-16
Oh, and neither bcm43xx nor any fwcutter-created versions of it work on my system. Yes, I've tried every tutorial in the forums, and ndiswrapper is the only thing that works. Sort of.

---

### Post by Tatterdemalian on 2007-11-16
Here's a saved copy of my ifconfig report before and after I get disconnected:

Before:
```

eth0      Link encap:Ethernet  HWaddr 00:1B:24:84:40:E8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:24:84:40:E8  
          inet addr:169.254.7.120  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61722 (60.2 KB)  TX bytes:61722 (60.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1A:73:81:1D:C0  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe81:1dc0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33884669 (32.3 MB)  TX bytes:1998895 (1.9 MB)
          Interrupt:9 Memory:b8000000-b8004000 

```

After:
```

eth0      Link encap:Ethernet  HWaddr 00:1B:24:84:40:E8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:24:84:40:E8  
          inet addr:169.254.7.120  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61722 (60.2 KB)  TX bytes:61722 (60.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1A:73:81:1D:C0  
          inet6 addr: fe80::21a:73ff:fe81:1dc0/64 Scope:Link
          UP BROADCAST RUNNING MTU:1500  Metric:1
          RX packets:25168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33884669 (32.3 MB)  TX bytes:1998895 (1.9 MB)
          Interrupt:9 Memory:b8000000-b8004000 

wlan0:ava Link encap:Ethernet  HWaddr 00:1A:73:81:1D:C0  
          inet addr:169.254.6.184  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:9 Memory:b8000000-b8004000 

```

lspci:
```

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

```

lspci -n:
```

03:00.0 0280: 14e4:4311 (rev 02)

```

ndiswrapper -l:
```

bcmwl5 : driver installed device (14E4:4311) present (alternate driver: bcm43xx)

```

lshw -C network:
```

  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:81:1d:c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.49+Broadcom,10/12/2006, 4.100. ip=192.168.0.6 latency=0 link=yes module=ndiswrapper wireless=IEEE 802.11g

```

iwconfig -a:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Tatternet"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:90:4B:83:48:3C   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:644  Invalid misc:2158559   Missed beacon:0

```

ip addr:
```

1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:1b:24:84:40:e8 brd ff:ff:ff:ff:ff:ff
    inet 169.254.7.120/16 brd 169.254.255.255 scope link eth0:avahi
3: wlan0: <BROADCAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:1a:73:81:1d:c0 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.6/24 brd 192.168.0.255 scope global wlan0
    inet6 fe80::21a:73ff:fe81:1dc0/64 scope link 
       valid_lft forever preferred_lft forever

```

---

