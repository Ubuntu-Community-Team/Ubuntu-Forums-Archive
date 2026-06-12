---
title: "Trying to install RT2500 wireless card"
date: 2005-06-16
forum: Absolute Beginner Talk
---

### Post by halfpower on 2005-06-16
I've been trying to install a wireless adapter based on this chipset.  After a lot of frustration it started to work.  I then rebooted and it was no longer working.  :neutral:   So more frustration, and then it worked again.  Then I rebooted, and I'm at square one again.  ](*,)   I can't figure out where I'm screwing up.    The last time I tried to install, configure, and connect to  the WLAN, I got a message resembling the following:

> 
sit0: unknown hardware address type 776
sit0: unknown hardware........

DHCPDISCOVER on RA0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on RA0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on RA0 to 255.255.255.255 port 67 interval 13...

No DHCPOFFERS recieved
No working leases in persistent database - sleeping
 

Do you know what I'm doing wrong?

---

### Post by clarkburbidge on 2005-12-31
I am having the same problem. Anyone lend a hand?

> [COLOR="Red"]**Here is my run throught the list of troubleshooting ideas at [https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=(troubleshoot)](https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=(troubleshoot))**[/COLOR]

**clark@ubuntu:~$ sudo lshw -businfo**
Password:
Bus info     Device    Class       Description
==============================================
                       system      OptiPlex G1 400L+
                       bus         Motherboard
                       memory      BIOS
cpu@0                  processor   Celeron (Mendocino)
                       memory      L1 cache
                       memory      L2 cache
                       memory      System Memory
                       memory      DIMM DRAM Synchronous
                       memory      DIMM DRAM Synchronous
pci@00:00.0            bridge      440BX/ZX/DX - 82443BX/ZX/DX Host bridge
pci@00:01.0            bridge      440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
pci@01:00.0            display     3D Rage IIC AGP
pci@00:07.0            bridge      82371AB/EB/MB PIIX4 ISA
pci@00:07.1            storage     82371AB/EB/MB PIIX4 IDE
ide@0        ide0      bus         IDE Channel 0
ide@0.0      /dev/hda  disk        Maxtor 4W060H4
ide@1        ide1      bus         IDE Channel 1
ide@1.0      /dev/hdc  disk        ATAPI CD-ROM MAX 58X
pci@00:07.2            bus         82371AB/EB/MB PIIX4 USB
usb@1        usb1      bus         Intel Corporation 82371AB/EB/MB PIIX4 USB
pci@00:07.3            bridge      82371AB/EB/MB PIIX4 ACPI
pci@00:0d.0  ra0       network     Ralink RT2500 802.11 Cardbus Reference Card
pci@00:0e.0            multimedia  Vortex 1
pci@00:11.0  eth0      network     3c905B 100BaseTX [Cyclone]


**clark@ubuntu:~$ sudo lshw -C network**
  *-network:0
       description: Wireless interface
       product: Ralink RT2500 802.11 Cardbus Reference Card
       vendor: RaLink
       physical id: d
       bus info: pci@00:0d.0
       logical name: ra0
       version: 01
       serial: 00:12:17:82:32:99
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:ff020000-ff021fff irq:10
  *-network:1
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 11
       bus info: pci@00:11.0
       logical name: eth0
       version: 24
       serial: 00:c0:4f:47:e1:0b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=3c59x driverversion=LK1.1.19 duplex=full link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:dc00-dc7f iomemory:ff022000-ff02207f irq:11

**clark@ubuntu:~$ sudo lsmod | grep 2500**
rt2500                150372  1

**clark@ubuntu:~$ sudo iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"the_coop"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:12:17:A6:E1:0F
          Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=56/100  Signal level=-78 dBm  Noise level:-206 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

**clark@ubuntu:~$ sudo iwlist ra0 scan**
ra0       Scan completed :
          Cell 01 - Address: 00:12:17:A6:E1:0F
                    Mode:Managed
                    ESSID:"the_coop"
                    Encryption key:off
                    Channel:11
                    Quality:57/100  Signal level:-102 dBm  Noise level:-206 dBm


**clark@ubuntu:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:C0:4F:47:E1:0B
          inet6 addr: fe80::2c0:4fff:fe47:e10b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1210 errors:0 dropped:0 overruns:1 frame:0
          TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:209187 (204.2 KiB)  TX bytes:129996 (126.9 KiB)
          Interrupt:11 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:203110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:203110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14977780 (14.2 MiB)  TX bytes:14977780 (14.2 MiB)

ra0       Link encap:Ethernet  HWaddr 00:12:17:82:32:99
          inet6 addr: fe80::212:17ff:fe82:3299/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4324 errors:670 dropped:670 overruns:0 carrier:0
          collisions:793 txqueuelen:1000
          RX bytes:895127 (874.1 KiB)  TX bytes:292664 (285.8 KiB)
          Interrupt:10 Base address:0x4000

**clark@ubuntu:~$ sudo dhclient ra0**
There is already a pid file /var/run/dhclient.pid with pid 12228
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ra0/00:12:17:82:32:99
Sending on   LPF/ra0/00:12:17:82:32:99
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database – sleeping.

**[COLOR="Red"]After Using the Network Setting wizard:[/COLOR]**

**clark@ubuntu:~$ ifconfig **
eth0      Link encap:Ethernet  HWaddr 00:C0:4F:47:E1:0B
          inet6 addr: fe80::2c0:4fff:fe47:e10b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1250 errors:0 dropped:0 overruns:1 frame:0
          TX packets:390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:215820 (210.7 KiB)  TX bytes:132048 (128.9 KiB)
          Interrupt:11 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:207290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15289460 (14.5 MiB)  TX bytes:15289460 (14.5 MiB)

ra0       Link encap:Ethernet  HWaddr 00:12:17:82:32:99
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe82:3299/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4472 errors:678 dropped:678 overruns:0 carrier:0
          collisions:841 txqueuelen:1000
          RX bytes:923652 (902.0 KiB)  TX bytes:307762 (300.5 KiB)
          Interrupt:10 Base address:0x4000

**clark@ubuntu:~$ ping -c 4 192.168.1.1**
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=4.96 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=36.0 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.70 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=3.48 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 1.704/11.555/36.065/14.197 ms

**clark@ubuntu:~$ ping -c 4 192.168.1.3**
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
64 bytes from 192.168.1.3: icmp_seq=1 ttl=64 time=0.123 ms
64 bytes from 192.168.1.3: icmp_seq=2 ttl=64 time=0.093 ms
64 bytes from 192.168.1.3: icmp_seq=3 ttl=64 time=0.096 ms
64 bytes from 192.168.1.3: icmp_seq=4 ttl=64 time=0.099 ms

--- 192.168.1.3 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.093/0.102/0.123/0.017 ms

**[COLOR="Red"]Attempted Firefox click to Ubuntu failed[/COLOR]**

**clark@ubuntu:~$ ping -c 4 147.83.195.18**
connect: Network is unreachable

[B]clark@ubuntu:~$ sudo route add default gw 192.168.1.1
clark@ubuntu:~$ ping -c 4 147.83.195.18[/B]
PING 147.83.195.18 (147.83.195.18) 56(84) bytes of data.

--- 147.83.195.18 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms

**clark@ubuntu:~$ ping -c 4 [www.yahoo.com](www.yahoo.com)**
ping: unknown host [www.yahoo.com](www.yahoo.com)

---

### Post by Mustard on 2005-12-31
I have absolutely no idea about wireless, but in the absence of any other replies, I'll post this link just in case you haven't seen it before...

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by reckless2k2 on 2006-01-01
[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

that link will answer your questions about how to bring it up and such. 

good luck.

---

### Post by clarkburbidge on 2006-01-03
I went through the steps in the rt2500 install guide. Then I went through the troubleshooting steps in the troubleshooting guide. I did both before posting my initial request for help. I included the results of the test in my post. I am grateful for your suggestions, but as evidenced by my original post info, I've already gone through the troubleshooting guide, and i understand by my results (at least I think) that I correctly completed the install guide.

Anyone else have any hints, or will anyone go through my troubleshooting results to see if I should have picked up something important?

---

### Post by reckless2k2 on 2006-01-05
Have you done any editing in the /etc/network/interfaces file?

If not and you network is not changing, I'd suggest editing that file to include the ra0 interface. map the essid suing wireless_essid xxxxx and any key if enabled. make sure you assign it for a dhcp braodcast. I've included an example:

# sudo nano /etc/network/interfaces

---------------------------------------------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0
map ra0

# The primary network interface
iface eth0 inet dhcp

# The wireless network interface
iface ra0 inet dhcp
# wireless-* options are implemented by the wireless-tools package
wireless_mode managed
wireless_essid REPLACE WITH YOUR ESSID
# dns-* options are implemented by the resolvconf package, if installed
#dns-nameservers REPLACE WITH YOUR GATEWAY

auto ra0

auto eth0

-----------------------------------------------------------------------


simplify your essid to something like test and make sure dhcp server is running on the router. Let me know how that works for you. also, when bringing up your card from the terminal, you only need do the following:

# sudo iwconfig ra0 essid YOURESSID mode Managed
# sudo ifup ra0
# ping [www.google.com](www.google.com)

I'd just suggest using the interfaces file though cause that'll map it. reboot and it'll bring it up.

---

### Post by bionnaki on 2006-06-13
try my solution in this thread: [http://ubuntuforums.org/showthread.php?t=161376](http://ubuntuforums.org/showthread.php?t=161376)

should work with any rt2500 driver card

---

