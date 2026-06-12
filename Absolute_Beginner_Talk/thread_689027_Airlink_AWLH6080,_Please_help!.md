---
title: "Airlink AWLH6080, Please help!"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by ApatheticLoser on 2008-02-06
I need to get this wireless card to install on my ubuntu partition (I already use it for my vista and xp instalations) but for some reason it just doesn't want to work. I've tried installing it with ndiswrapper and the netr28.inf file that comes on the CD, and it seems to be correct because ndiswrapper tells me that the hardware is there, but when I goto the network manager I don't have a choice to configure a wireless connection and sudo lshw -C network & lspci doesn't list an airlink card (calls it RaLink and unknown(outputs listed below))

Would someone please help me with a solution? Thanks in advance.

lspci:
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0611 (rev a2)
07:00.0 Network controller: RaLink Unknown device 0601
07:01.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

sudo lshw -C network:
  *-network:0 UNCLAIMED   
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
  *-network:1
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 01
       serial: 00:19:d1:68:5d:0a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.1.6 latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

and just incase it helps,
lspci -n:
00:00.0 0600: 8086:2770 (rev 02)
00:01.0 0604: 8086:2771 (rev 02)
00:1b.0 0403: 8086:27d8 (rev 01)
00:1c.0 0604: 8086:27d0 (rev 01)
00:1c.2 0604: 8086:27d4 (rev 01)
00:1c.3 0604: 8086:27d6 (rev 01)
00:1c.4 0604: 8086:27e0 (rev 01)
00:1c.5 0604: 8086:27e2 (rev 01)
00:1d.0 0c03: 8086:27c8 (rev 01)
00:1d.1 0c03: 8086:27c9 (rev 01)
00:1d.2 0c03: 8086:27ca (rev 01)
00:1d.3 0c03: 8086:27cb (rev 01)
00:1d.7 0c03: 8086:27cc (rev 01)
00:1e.0 0604: 8086:244e (rev e1)
00:1f.0 0601: 8086:27b0 (rev 01)
00:1f.1 0101: 8086:27df (rev 01)
00:1f.2 0104: 8086:27c3 (rev 01)
00:1f.3 0c05: 8086:27da (rev 01)
01:00.0 0300: 10de:0611 (rev a2)
07:00.0 0280: 1814:0601
07:01.0 0401: 13f6:0111 (rev 10)
07:08.0 0200: 8086:1094 (rev 01)

---

### Post by ApatheticLoser on 2008-02-07
One day without a reply, so I'm bumping.

---

