---
title: "internet connection problem (wireless)"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by skywalkrNCSU on 2008-02-28
I have ubuntu vs. 6.something installed on my laptop which i havent used much in the past year.  the wireless used to work fine and dandy but now i cant get it to make a connection.  it works through the wired connection but when i go to connect wirelessly i get nothing.

when i click on the network icon in the upper right corner it just says connection is "lo"

i am a complete noob at this so sorry if i dont know what you are talking about right at first.  i tried searching but there are so many wireless threads that are different i didnt know what to look for.

---

### Post by rasmus91 on 2008-02-28
I can't tell you what the problem is, but identify your wireless card, (or wireless hardware) and search for the name of the card/(what ever you're using)

---

### Post by skywalkrNCSU on 2008-02-28
i have a laptop that is about 4 years old with centrino on it...is that the wireless or what should i search for?

---

### Post by dstew on 2008-02-28
Post the output of **lspci**, **ifconfig** and **iwconfig**

---

### Post by skywalkrNCSU on 2008-02-28
lspci:

0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller ( rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EH CI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridg e (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller ( rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97  Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Rad eon 9600 M10]
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01 )
0000:02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controlle r (rev 02)
0000:02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controlle r
0000:02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)



ifconfig:



eth0      Link encap:Ethernet  HWaddr 00:0F:1F:12:64:E5
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe12:64e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1033 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:800345 (781.5 KiB)  TX bytes:229689 (224.3 KiB)
          Interrupt:11

eth1      Link encap:Ethernet  HWaddr 00:0E:35:14:01:00
          inet6 addr: fe80::20e:35ff:fe14:100/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:3154 (3.0 KiB)  TX bytes:3456 (3.3 KiB)
          Interrupt:7 Base address:0x2000 Memory:faffc000-faffcfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)




iwconfig:



lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"NETGEAR"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by jan quark on 2008-02-28
please post also the output from 
```

sudo lshw -C network
```

---

### Post by skywalkrNCSU on 2008-02-28
*-network:0
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:12:64:e5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=full ip=192.168.0.12 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:faffe000-faffffff irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:14:01:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.1 firmware=ABG:9.0.2.6 (Mar 22 2005) link=no multicast=yes wireless=unassociated
       resources: iomemory:faffc000-faffcfff irq:7

---

### Post by mrsteveman1 on 2008-02-28
Seems like the driver is loaded just fine, but the card isn't associated with an access point.

---

