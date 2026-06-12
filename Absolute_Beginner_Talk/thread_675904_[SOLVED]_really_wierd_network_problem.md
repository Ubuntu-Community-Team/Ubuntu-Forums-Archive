---
title: "[SOLVED] really wierd network problem"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by arjayes on 2008-01-23
so i've just installed ubuntu gutsy on  a friends laptop .
and i'm unable to connect to the internet.
ping gives me 
>  Unable to detect a network 
the output of 
lspci:
> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

of lshw -C network
> 
 *-network DISABLED
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:00:00:1a:73:92
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:94:8a:6c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

and ifconfig:
> 
eth0      Link encap:Ethernet  HWaddr 00:1B:24:94:8A:6C  
          inet6 addr: fe80::21b:24ff:fe94:8a6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1957 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:239192 (233.5 KB)  TX bytes:6895 (6.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1688 (1.6 KB)  TX bytes:1688 (1.6 KB)




the contents of the /etc/network/interfaces file is 
> 
auto lo
iface lo inet loopback


iface eth0 inet static
address 10.117.143.27
netmask 255.255.255.0
gateway 10.117.143.2

auto eth0


the network referred to is the LAN at my college which connects to the net through a proxy
any idea what the problem is

---

### Post by bumanie on 2008-01-23
Early on with gutsy there were many problems with people getting connected to the internet. Posts about this issue have greatly decreased - not sure whether this is due to updates improving things or not. However, a common problem had been ipv6. Many got the internet to work by blacklisting ipv6. You could try that. You can reverse it if it doesn't work, by later removing what you've added.
In terminal type
gksudo gedit /etc/modprobe.d/blacklist and hit enter
at the end of the list type
blacklist ipv6. Save and reboot.
I hope this is your issue and that this helps.

---

### Post by arjayes on 2008-01-23
thanks worked perfectly

---

