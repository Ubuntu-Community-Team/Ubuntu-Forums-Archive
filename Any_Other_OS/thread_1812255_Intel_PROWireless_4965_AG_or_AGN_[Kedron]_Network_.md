---
title: "Intel PRO/Wireless 4965 AG or AGN [Kedron] Network Connection wifi problem"
date: 2011-07-26
forum: Any Other OS
---

### Post by edeetjen on 2011-07-26
[QUOTE=ugm6hr;5024425]There are plenty of people who have this as their first question regarding Ubuntu?  Why?  It is a primary role for computers in the modern day.

Unfortunately, merely telling people that it doesn't work won't help them to resolve the issue.  So - in the words of Tom Cruise, "Help me, help you."

This guide is useful reading regarding getting generic help: [https://help.ubuntu.com/community/GettingAnswers](https://help.ubuntu.com/community/GettingAnswers)

For internet-related help, make sure you include the following details:

1. How were you trying to get online?  e.g. dial-up, USB-wired ADSL modem, ethernet-wired ADSL modem, ethernet-wired ADSL modem-router, wireless router / modem-router, 3G-mobile internet etc.
wireless router

2. What hardware are you using?  The brand & model number (perhaps with a link to an online manual) for your adapters, modems, routers etc.  You can generally identify external components from their labelling, and internal components from within an Operating System already installed (e.g. Windows or Ubuntu).
```
lspci
lsusb
lshw -class network
```3. Who is your Internet Service Provider (and in which country)?
v
```
mint@mint ~ $ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
0e:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0e:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0e:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0e:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
mint@mint ~ $ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 5986:0200 Acer, Inc OrbiCam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mint@mint ~ $ lshw -class network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0a:e4:ca:9a:74
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb v3.04 ip=10.0.1.21 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:52 memory:f4100000-f410ffff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:47:64:6d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=228.61.2.24 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:51 memory:f4200000-f4201fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
lmint@mint ~ $ 
mint@mint ~ $ sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0a:e4:ca:9a:74
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb v3.04 ip=10.0.1.21 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:52 memory:f4100000-f410ffff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:47:64:6d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:51 memory:f4200000-f4201fff
mint@mint ~ $ uname -a
Linux mint 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

4. Which version of Ubuntu are you using?  e.g. Ubuntu 8.04, Xubuntu 7.10 etc and 32- vs 64-bit.
[CODE]uname -a
lsb_release -a
```5. Can you get online with any other method?  e.g. if you have a wifi problem, can you connect with ethernet?
mint@mint ~ $ lsb-release -a
No command 'lsb-release' found, did you mean:
 Command 'lsb_release' from package 'lsb-release' (main)
lsb-release: command not found
mint@mint ~ $ lsb_release -a
No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 11 Katya
Release:    11
Codename:    katya
mint@mint ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:ca:9a:74  
          inet addr:10.0.1.21  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:feca:9a74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168350 (168.3 KB)  TX bytes:38534 (38.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13680 (13.6 KB)  TX bytes:13680 (13.6 KB)

6. How are you getting online to post on this forum?
ethernet

7. Include the **output** from the following commands from Terminal (all **case sensitive**).  They help identify your hardware, so provide further detail to potential helpers.  If necessary, just copy and paste the text into a text file and upload from a different computer.

```
ifconfig
iwconfig
route -n
ping -c 3 208.67.219.101
ping -c 3 www.opendns.com
```8. For wifi - what encryption are you using? Have you tried an open network?  What wifi channel do you use?


 mint@mint ~ $ iwconfig
 lo        no wireless extensions.
 
 eth0      no wireless extensions.
 
 wlan0     IEEE 802.11abgn  ESSID:off/any  
           Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
           Retry  long limit:7   RTS thr:off   Fragment thr:off
           Power Management:off
           
 mint@mint ~ $ route -n
 Kernel IP routing table
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
 10.0.1.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
 169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
 0.0.0.0         10.0.1.1        0.0.0.0         UG    0      0        0 eth0
 mint@mint ~ $ ping -c 3 208.67.219.101
 PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.
 pint 
 --- 208.67.219.101 ping statistics ---
 3 packets transmitted, 0 received, 100% packet loss, time 2002ms
 
 mint@mint ~ $ ping -c 3 [www.opendns.com](www.opendns.com)
 PING [www.opendns.com](www.opendns.com) (208.69.38.150) 56(84) bytes of data.
 64 bytes from 208.69.38.150: icmp_req=1 ttl=52 time=39.1 ms
 64 bytes from 208.69.38.150: icmp_req=2 ttl=52 time=27.3 ms
 64 bytes from 208.69.38.150: icmp_req=3 ttl=52 time=31.0 ms
 
 --- [www.opendns.com](www.opendns.com) ping statistics ---
 3 packets transmitted, 3 received, 0% packet loss, time 10112ms
 rtt min/avg/max/mdev = 27.300/32.481/39.130/4.939 ms

9. Do you dual-boot with Windows?  If yes - read this:
No[/CODE]

---

### Post by ugm6hr on 2011-07-26
It looks like this might not be so straightforward to fix - except by using an older version:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/779159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/779159)

---

