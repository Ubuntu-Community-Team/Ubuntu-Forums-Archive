---
title: "Problems connecting to internet with Speedstream 4100"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by peruisay on 2007-12-30
Hey, all. I'm having trouble getting my internet up and running on a fresh Ubuntu install. I've read and followed all the solutions I could find online, but I'm pretty green on Linux and couldn't get anything to work. I'm stumped at this point.

I'm dual-booting Windows XP Media Center Edition and Ubuntu 7.10. The modem is a Siemens Speedstrem 4100, and it connects by ethernet. It works perfectly in XP and uses DHCP.

My situation is probably *closest *to this thread: 

[http://ubuntuforums.org/showthread.php?t=352738&highlight=speedstream+4100](http://ubuntuforums.org/showthread.php?t=352738&highlight=speedstream+4100)

Here's my **ifconfig**:

eth0      Link encap:Ethernet  HWaddr 00:11:2F:CA:2C:35  
          inet6 addr: fe80::211:2fff:feca:2c35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1272 (1.2 KB)  TX bytes:1272 (1.2 KB)

And my **/etc/network/interfaces**.

auto lo
iface lo inet loopback

auto eth 0

iface eth0 inet dhcp

auto eth0

This is what my **lspci **looks like:

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:04.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:05.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)

And here's my **lshw -C network**.

*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: eth0
       version: 10
       serial: 00:11:2f:ca:2c:35
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

Just a few more! (I figure it's better to put it all out here up front, rather than restart my computer endless times.)

This is what **ifconfig -a** looks like.

eth0      Link encap:Ethernet  HWaddr 00:11:2F:CA:2C:35  
          inet6 addr: fe80::211:2fff:feca:2c35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xc400 

eth0:avah Link encap:Ethernet  HWaddr 00:11:2F:CA:2C:35  
          inet addr:169.254.4.135  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1456 (1.4 KB)  TX bytes:1456 (1.4 KB)

And this is the **more /var/log/messages grep dhcp**

::::::::::::::
/var/log/messages
::::::::::::::
Dec 29 23:03:50 renato-desktop syslogd 1.4.1#21ubuntu3: restart.
Dec 29 23:09:09 renato-desktop kernel: [  692.735105] PPP generic driver version
 2.4.2
Dec 29 23:09:09 renato-desktop kernel: [  692.738723] NET: Registered protocol f
amily 24
Dec 29 23:09:27 renato-desktop pppoe-discovery: Timeout waiting for PADO packets
Dec 29 23:09:27 renato-desktop kernel: [  710.760657] NETDEV WATCHDOG: eth0: tra
nsmit timed out
Dec 29 23:09:30 renato-desktop kernel: [  713.758793] eth0: link up, 100Mbps, fu
ll-duplex, lpa 0x41E1
Dec 29 23:09:42 renato-desktop pppoe-discovery: Timeout waiting for PADO packets
Dec 29 23:09:48 renato-desktop kernel: [  731.747274] NETDEV WATCHDOG: eth0: tra
nsmit timed out
Dec 29 23:09:51 renato-desktop kernel: [  734.745413] eth0: link up, 100Mbps, fu
ll-duplex, lpa 0x41E1
Dec 29 23:11:22 renato-desktop pppd[6716]: pppd 2.4.4 started by renato, uid 0
Dec 29 23:11:22 renato-desktop pppd[6716]: Using interface ppp0
Dec 29 23:11:22 renato-desktop pppd[6716]: Connect: ppp0 <--> /dev/pts/0
Dec 29 23:11:26 renato-desktop pppd[6716]: Hangup (SIGHUP)
Dec 29 23:11:26 renato-desktop pppd[6716]: Modem hangup

I'd really appreciate any help with this. If you need anything else, I'll be more than happy to provide it. I've been working on this all week!

---

### Post by ^rooker on 2007-12-30
I don't know the Speedstream DSL modem, but I assume the following:

1) your eth0 doesn't get *any* IP from the modem's DHCP.
Usually that would be "10.0.0.140" (and the modem itself is 10.0.0.138).
The quickest way to check that is to open a shell and type:

"sudo ifconfig eth0 inet 10.0.0.140 up"

and then:
"ping 10.0.0.138" - and see if you get an answer from the modem.


2) If your modem answers, you still need to configure the ADSL connection itself. I'm sorry, but I've never done that using a GUI, but from here you should be able to follow any ADSL howto (It'll probably include the use of "pptp")

-- IF your modem does *not* answer to the pings, it must be setup differently to what I know. Please tell me and I'll see if I can help you out.

---

