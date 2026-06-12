---
title: "PPPOE no longer working - how to diagnose?"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Adam590 on 2007-09-24
I've always been able to get online by running pppoeconf after each reboot, disconnection, etc. The last several days, this no longer works for me, and I can't figure out the problem (I've tried searching the forums).

[Here]("http://ubuntuforums.org/showthread.php?t=470174&highlight=pppoe") is a thread where I describe my usual connection process. 

I do think that my ISP may be going through a transition phase (big ad campaign, lots of new customers, new services), so there might be some changes on their end, but there are two other computers here running Windows that haven't had any problems connecting with the usual username/password. 

Any advice?

---

### Post by Arwen on 2007-09-24
Why don't you call your internet provider before starting looking for problems with your installation?You have router for connecting right?

---

### Post by Adam590 on 2007-09-24
Customer service is basically nonexistent here, and I'm not sure what I'd ask them anyway. I feel like the problem is on my end since the other computers can connect with M$.

Following advice from [this thread]("http://ubuntuforums.org/showthread.php?t=448389"), I added the two DNS addresses provided by one of the working Windows connections to my /etc/resolv.conf file, but that didn't seem to help. 

I can post the outputs of different commands here, but I'm not sure which ones are relevant. Any advice as to what other settings and configurations I should check/alter?

EDIT: To answer your question, we have an ADSL modem made by D-Link.

---

### Post by Adam590 on 2007-09-24
Um...specifically, are there other addresses or settings that I could snag from one of the (working, online) computers to put in my various configuration files?

---

### Post by Adam590 on 2007-09-25
Here's some more info, if it helps:

the internet setup:

telephone line -> "ADSL splitter" (splits to phone and modem) -> D-LINK ADSL modem -> 8-port Nway switch (ethernet splitter) -> three computers (two with Windows and my HP ZD7000 with Ubuntu)

So...I plug in the ethernet cable. The network connection icon swirls, then says "Connection Established - You are now connected to the wired network"

I open a terminal and type "sudo pppoeconf".

The gui says it has found two devices: eth0 and eth1

I enter "Yes", then it searches for the concentrator and seems to find it.

I enter "Yes" that the /etc/ppp/peers/dsl-provider file can be modified.

I enter "Yes" about the 'noauth', 'defaultroute', and 'nodetach' options.

I enter my username and password (which work on the Windows machines and used to work on mine).

I enter "Yes" that the DNS address(es) can be added automatically to my /etc/resolv.conf file.

I enter "Yes" about pppoe clamping MSS at 1452 bytes.

I enter "Yes" about starting the connection at boot time. (Not that it has ever worked.)

I enter "Yes" that I would like to start the connection now.

I enter "OK" and leave the gui.

But I'm not connected. At this point I used to have to go through several other steps, outlined [here]("http://ubuntuforums.org/showthread.php?t=470174") to connect, but those don't work any more, either.



So here's the output of as many relevant things as I've been able to find during hours of searching these forums. If there's anything else helpful I could add, please let me know:



Adam590@ub-laptop:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:37:54:11  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::2c0:9fff:fe37:5411/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:32587 (31.8 KiB)  TX bytes:20103 (19.6 KiB) 
          Interrupt:21 Base address:0xc800 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:4F:52:A4  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:10 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1412 (1.3 KiB)  TX bytes:1412 (1.3 KiB) 

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:79.125.132.190  P-t-P:79.125.128.1  Mask:255.255.255.255 
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1 
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:3 
          RX bytes:1770 (1.7 KiB)  TX bytes:54 (54.0 b) 




Adam590@ub-laptop:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
79.125.128.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0 
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0 

(that one should have a "UG" somewhere, right?) 




Adam590@ub-laptop:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02) 
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02) 
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02) 
00:1f.6 Modem [0703]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller [8086:24d6] (rev 02) 
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34M [GeForce FX Go5200] [10de:0324] (rev a1) 
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10) 
02:01.0 CardBus bridge [0607]: ENE Technology Inc CB-710/2/4 Cardbus Controller [1524:1411] (rev 02) 
02:01.1 FLASH memory [0501]: ENE Technology Inc CB710 Memory Card Reader Controller [1524:0510] 
02:02.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026] 
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03) 




Adam590@ub-laptop:~$ sudo lshw -C network 
  *-network:0             
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@02:00.0 
       logical name: eth0 
       version: 10 
       serial: 00:c0:9f:37:54:11 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.4 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s 
       resources: ioport:3000-30ff iomemory:d2007800-d20078ff irq:21 
  *-network:1 DISABLED 
       description: Wireless interface 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 3 
       bus info: pci@02:03.0 
       logical name: eth1 
       version: 03 
       serial: 00:90:4b:4f:52:a4 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master ethernet physical wireless 
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=32 link=no multicast=yes wireless=IEEE 802.11b/g 
       resources: iomemory:d2004000-d2005fff irq:22 




Adam590@ub-laptop:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 

auto eth0 
iface eth0 inet dhcp 

auto eth1 
iface eth1 inet dhcp 

auto eth2 
iface eth2 inet dhcp 

auto ath0 
iface ath0 inet dhcp 

auto wlan0 
iface wlan0 inet dhcp 


pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf 
auto dsl-provider 
iface dsl-provider inet ppp 
provider dsl-provider 



Okay, that's about all I've got, so far. Lots of Greek, to me. 
Anybody? :)

---

