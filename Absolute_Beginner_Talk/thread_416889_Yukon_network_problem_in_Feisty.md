---
title: "Yukon network problem in Feisty"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by kingy on 2007-04-21
Hi,

I've got a problem with my network card, and I have very little Linux experience so could do with some help! When I boot up Feisty (64bit), the internet connection always cuts out within the 1st 10 seconds of using it. I'm connecting to the internet (cable broadband) via a router. The other people using the router all use XP and have no problems. I myself run a dual boot with Vista being the other OS, and networking and the internet connection are fine in Vista. The network card is a Marvell Yukon 88E8056 PCI-E Gigabit ethernet controller. I have previously tried to install Edgy but had no luck getting the network card working there. I've searched the forums and it seems a lot of people have been having issues with the Yukon, but I had read that the new kernal in Feisty should solve them. From looking at other posts, you'll be needing to know somethings about my system, hopefully I've covered the basics, if I've missed anything let me know.

ifconfig

eth0      
Link encap:Ethernet  
HWaddr 00:16:E6:DF:35:41           
inet addr:192.168.2.100  Bcast:255.255.255.255  Mask:255.255.255.0
inet6 addr: fe80::216:e6ff:fedf:3541/64 Scope:Link
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:1050 (1.0 KiB)  TX bytes:2372 (2.3 KiB)
Interrupt:16 
lo        
Link encap:Local Loopback         
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host          
UP LOOPBACK RUNNING  MTU:16436  Metric:1          
RX packets:2 errors:0 dropped:0 overruns:0 frame:0          
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:0           
RX bytes:100 (100.0 b)  
TX bytes:100 (100.0 b)

lshw -C network

WARNING: you should run this program as super-user.
*-network               
description: Ethernet interface
product: Marvell Technology Group Ltd.
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@03:00.0
logical name: eth0
version: 12      
serial: 00:16:e6:df:35:41       
width: 64 bits       
clock: 33MHz       
capabilities: bus_master cap_list ethernet physical       
configuration: broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A ip=192.168.2.100 latency=0 multicast=yes       
resources: iomemory:f7000000-f7003fff ioport:8000-80ff irq:16

lspci

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7280
01:00.1 Display controller: ATI Technologies Inc Unknown device 72a0
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4364 (rev 12)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
05:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
05:00.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
05:00.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

dmesg | grep sky2

[   44.468363] sky2 0000:03:00.0: v1.13 addr 0xf7000000 irq 16 Yukon-EC Ultra (0xb4) rev 2
[   44.468446] sky2 eth0: addr 00:16:e6:df:35:41
[   44.483202] sky2 eth0: enabling interface
[   44.485431] sky2 eth0: ram buffer 0K
[   46.167573] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   60.823580] sky2 eth0: transmit descriptor error (hardware problem)
[   60.823712] sky2 eth0: Link is down.
[   62.481793] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   62.481798] sky2 eth0: transmit descriptor error (hardware problem)
[   62.481931] sky2 eth0: Link is down.
[   64.073106] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   64.073111] sky2 eth0: transmit descriptor error (hardware problem)
[   64.073245] sky2 eth0: Link is down.
etc...

Any ideas? Thanks in advance for any help. Cheers.

---

### Post by ctothej on 2007-10-05
Bump.

Im having issues with transfering files over my network using smb. My network connection just drops during outbound transfer (it seems I can transfer from the shares without problems). I've tried smbfs and fusesmb. I changed the frame sizes from my NAS server. I have another machine with feisty that works perfectly using smbfs. I think it might be the network driver for my network card on this computer.

Network card: Marvell 88E8056 

Could it have anything to do with the AI NET2 feature?

---

### Post by ctothej on 2007-10-07
Fixed using the noapic and nolapic boot parameters in conjunction with the marvel drivers on their website.

---

