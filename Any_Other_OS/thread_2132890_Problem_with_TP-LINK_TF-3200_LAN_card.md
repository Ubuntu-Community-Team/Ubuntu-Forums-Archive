---
title: "Problem with TP-LINK TF-3200 LAN card"
date: 2013-04-06
forum: Any Other OS
---

### Post by MOraleSs on 2013-04-06
I have a system with a onboard LAN (Realtek RTL8101E/RTL8102E) and bought recently a TP-LINK TF-3200 card. I've done this because I have 2 ISP's in my location. 
On my linux mint install based on ubuntu 12.04 the network manager marks the TP-LINK card as unavailable. Note that it shows it as Sundance Technology / IC Plus IP100A. I can't get the TP-LINK card to work in any way. I also have a dual boot with Windows 7 and I don't have any problem with it over there.

Here are some outputs:

> # dmesg | grep eth
[    0.176236] i2c-core: driver [aat2870] using legacy suspend method
[    0.176237] i2c-core: driver [aat2870] using legacy resume method
[    1.072947] r8169 0000:01:00.0: eth0: RTL8102e at 0xf8020000, 00:25:22:ef:d8:3f, XID 04c00000 IRQ 42
[    1.074928] eth1: IC Plus Corporation IP100A FAST Ethernet Adapter at 0001ec00, 64:70:02:11:f6:79, IRQ 23.
[    1.075452] eth1: MII PHY found at address 0, status 0x7849 advertising 01e1.
[   11.905034] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.905041] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   14.545640] r8169 0000:01:00.0: eth0: link down
[   14.545647] r8169 0000:01:00.0: eth0: link down
[   14.545808] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.546321] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.146639] r8169 0000:01:00.0: eth0: link up
[   16.146764] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.128007] eth0: no IPv6 routers present

> # lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:25:22:ef:d8:3f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=172.16.200.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:d800(size=256) memory:fdeff000-fdefffff memory:fdee0000-fdeeffff memory:feae0000-feafffff
  *-network
       description: Ethernet interface
       product: IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY
       vendor: Sundance Technology Inc / IC Plus Corp
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: eth1
       version: 31
       serial: 64:70:02:11:f6:79
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sundance driverversion=1.2 duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10Mbit/s
       resources: irq:23 ioport:ec00(size=128) memory:febffc00-febffdff memory:febe0000-febeffff

> ethtool eth1
Settings for eth1:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Current message level: 0x00000001 (1)
                   drv
    Link detected: no


> # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:22:ef:d8:3f  
          inet addr:172.16.200.5  Bcast:172.16.200.255  Mask:255.255.255.0
          inet6 addr: fe80::225:22ff:feef:d83f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27595 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68915390 (68.9 MB)  TX bytes:2312455 (2.3 MB)
          Interrupt:42 

eth1      Link encap:Ethernet  HWaddr 64:70:02:11:f6:79  
          inet6 addr: fe80::6670:2ff:fe11:f679/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:49
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:12704 (12.7 KB)
          Interrupt:23 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8936 (8.9 KB)  TX bytes:8936 (8.9 KB)

modprobe sundance shows nothing

A little help will be appreciated.

Thanks!

---

### Post by Perfect Storm on 2013-04-06
Moved to Other OS/Distro Support.

---

