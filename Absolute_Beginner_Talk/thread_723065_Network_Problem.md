---
title: "Network Problem"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by salmaansharif on 2008-03-13
Hi,
I am new user of Ubuntu/linux system. I am facing problem to set network connection. I ping it with ip address its perfect but the internet is not working on firefox or any other application
NEED YOUR HELP PLZ

---

### Post by jan quark on 2008-03-13
please post the results of these terminal commands:

```
sudo lshw -C network
iwconfig
sudo iwlist scan
cat /etc/network/interfaces
```

---

### Post by salmaansharif on 2008-03-15
Thanks for your reply please find below the the description of commands
salmaan@Salmaan:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:eb:dd:29
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 firmware=5705-v3.11 latency=32 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
  *-network
       description: 3CCFE575BT
       product: LAN Cardbus Card
       vendor: 3Com Corporation
       physical id: 0
       version: 001
       slot: Socket 0
       resources: irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth2
       version: 04
       serial: 00:0c:f1:17:ce:e0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
  *-network
       description: Ethernet interface
       product: 3cCFE575BT Megahertz 10/100 LAN CardBus [Cyclone]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:50:04:b5:2b:f2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half ip=192.168.0.231 latency=64 link=yes maxlatency=5 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
salmaan@Salmaan:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

salmaan@Salmaan:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      No scan results

eth1      Interface doesn't support scanning.

salmaan@Salmaan:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth2 inet dhcp
wpa-psk d210d6fb48b89a920ece93fbc09f6993b972e9638bc2d939a5e25a087e6c51cb
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Micronet




auto eth2

iface eth1 inet dhcp

auto eth1
salmaan@Salmaan:~$

---

