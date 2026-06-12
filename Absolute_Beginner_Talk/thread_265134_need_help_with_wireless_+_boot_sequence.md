---
title: "need help with wireless + boot sequence"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by musab on 2006-09-25
[COLOR="RoyalBlue"][SIZE="4"]Hi every one

I just downloaded Ubuntu on my laptop. I have two questions so I get to go with Ubuntu

1. I have 0 idea how to connect the laptop (Gateway) to my wireless

2. I looked at the grub , menue.list file to change the time in the booting screen between windows and linux.. but I want windows to start fist cause I use it alot for school, any advice how to do that because I don't wanna miss with this file :mrgreen: 

Thank u..[/SIZE][/COLOR]

---

### Post by NetworkGuy on 2006-09-25
I'll start with the easiest.

#2 - You need to change the default number from 0 to the number that corresponds to your Windows entry.   Remember that the first line in your menu is 0  If Windows is the third entry in your menu, then you need to make your default 2.

#1 - We need more information to help you with your wireless router.  You need open a terminal (Accessories --> Terminal) and reply to this with the output of the following commands you type at the terminal
```
lspci
```
```
iwconfig
```
```
ifconfig
```

---

### Post by musab on 2006-09-25
Hi, This is what I got

[COLOR="Red"]musab@musab-laptop:~$ lspci[/COLOR]
```

0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE C ontroller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 A udio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev  02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 2 00M 5955 (PCIE)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 Fast Eth ernet Controller (rev 10)
0000:08:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 0 1)
0000:08:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g]  802.11g Wireless LAN Controller (rev 02)
0000:08:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control ler (rev 80)

```

[COLOR="Red"]musab@musab-laptop:~$ iwconfig[/COLOR]
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"CoMpUtErPiRaTeS"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

[COLOR="Red"]musab@musab-laptop:~$ ifconfig[/COLOR]

```

eth0      Link encap:Ethernet  HWaddr 00:03:25:33:23:D2
          inet addr:24.243.36.232  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::203:25ff:fe33:23d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:297647 (290.6 KiB)  TX bytes:17560 (17.1 KiB)
          Interrupt:50

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

```

hopefully this is what you need

Thank u..

---

### Post by musab on 2006-09-26
No idea :(

---

### Post by inkybutton on 2006-09-26
> **musab said:**
> No idea :(

eth1      IEEE 802.11b/g  ESSID:"CoMpUtErPiRaTeS"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



It's great that Ubuntu has recognised your wireless card and has attempted to connect. Now does your wireless network have a password (WEP,WPA etc.)?

If it's WEP, then enter this:

> sudo iwconfig eth1 key *[your password here]*

Hopefully it should work. 

If it's WPA, check out this Wiki [article]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") 

If the above don't work, enter:
> sudo iwevent
And post the output here.

If it does work, then post and let me know, because I can't be bother posting about making the Wireless LAN stay.
**EDIT**:I noticed the ESSID(or SSID in Windows world) might not be the one you need. To change it:
> sudo iwconfig eth1 essid *[enter your ESSID/SSID here]*

---

### Post by musab on 2006-09-27
Hi..

 I only have MAC Adress filter, I didn't put any password

I will try those commands and post the results here

thaaanks

---

### Post by musab on 2006-10-14
I'm not getting any thing on any of the command except the first one, I get this

```

musab@musab-laptop:~$ sudo iwevent
Waiting for Wireless Events from interfaces...

musab@musab-laptop:~$ sudo iwconfig eth1 essid NETGEAR
musab@musab-laptop:~$ sudo iwconfig eth1
eth1      IEEE 802.11b/g  ESSID:"NETGEAR"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

