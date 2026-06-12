---
title: "Wireless PCMCIA Card Not Functioning"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by flowingfire on 2007-06-11
Hi Everybody,

My wireless PCMCIA card is not working in Ubuntu.  It is a Linksys WPC54GS v1.1.  Please help me get it working...  I just tried fruitlessly for hours and a helpful person on chat got frustrated and asked if I was completely new.

What I tried to do to fix the problem was this:
Step 1: Install PCMCIA stuff from Adept and Symantic.  I just clicked on whatever looked right and now I have it.
Step 2: I installed ndiswrapper and all its related stuff.
Step 3: I downloaded the correct .inf driver from a website with wrapper-compatible drivers, then used ndiswrapper on it.

It didn't work.

Step 4: I downloaded the correct driver from Linksys.com and installed it using the same method.

It didn't work.

What I have is the computer recognizing my wireless device as eth1.  When I click to enable it, it gives me an error or simply does not enable at all.  

(On a side note, why does EVERYTHING in Linux have to be hours and hours of work?  Like 10-20 hours to get the display working correctly?  Another 6-8 hours to get the wireless card working... And it doesn't work?!!!  Sigh.)


Anywho, I'd appreciate input from experience Ubuntuites who might know how to make this work...

---

### Post by ugm6hr on 2007-06-11
Worthwhile letting us know what type of wifi chipset you have:

In Terminal:
```
lspci
```
Let us know the Network / Ethernet controller outputs
```
ifconfig
```
```
iwconfig
```

Then someone will be able to help.

---

### Post by flowingfire on 2007-06-11
BELOW IS MY LSPCI:
```
david@Into-the-Future:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

--------------------
BELOW IS MY IFCONFIG:
```
david@Into-the-Future:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:9D:43:51:FC
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fe43:51fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:165594 (161.7 KiB)  TX bytes:6146 (6.0 KiB)
          Interrupt:11 Base address:0x6000

eth1      Link encap:Ethernet  HWaddr 00:13:10:47:F1:F5
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:10ff:fe47:f1f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1874 errors:0 dropped:414 overruns:0 frame:0
          TX packets:1176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1817434 (1.7 MiB)  TX bytes:113567 (110.9 KiB)
          Interrupt:11 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
-----------------------
BELOW IS MY IWCONFIG:
```
david@Into-the-Future:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Coleman Family LAN"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:11:95:77:62:64
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=80/100  Signal level=-47 dBm  Noise level=-61 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by flowingfire on 2007-06-11
Okay...All of a sudden my wireless card is working without any good reason.  Did one of you nice folks hack my computer and fix it?  LOL!

Nevermind.

---

