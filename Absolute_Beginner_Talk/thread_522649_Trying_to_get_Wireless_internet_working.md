---
title: "Trying to get Wireless internet working"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by V3lier on 2007-08-10
Well I just installed Ubuntu yesterday and it's fantastic but I have some trouble getting the internet to work. I have been searching a lot and have found no solution to my problem. I have two computers. One with Windows XP with internet working and everything and the other with Ubuntu. My problem is that in Ubuntu it picks up Netgear and even another wireless connection which I don't own but it cant get a strong signal. I am using the router netgear WGR614 v6. Before when I didn't have Ubuntu installed I had Windows XP and I was using the wireless internet but I don't know what to do. I will keep searching and I will learn as much as possible but it would be great if someone would help. I will do anything possible to fix this problem. Thank you in advanced. :)

---

### Post by V3lier on 2007-08-10
Bump::Help would be greatly appreciated.

---

### Post by jimrz on 2007-08-10
> **V3lier said:**
> Well I just installed Ubuntu yesterday and it's fantastic but I have some trouble getting the internet to work. I have been searching a lot and have found no solution to my problem. I have two computers. One with Windows XP with internet working and everything and the other with Ubuntu. My problem is that in Ubuntu it picks up Netgear and even another wireless connection which I don't own but it cant get a strong signal. I am using the router netgear WGR614 v6. Before when I didn't have Ubuntu installed I had Windows XP and I was using the wireless internet but I don't know what to do. I will keep searching and I will learn as much as possible but it would be great if someone would help. I will do anything possible to fix this problem. Thank you in advanced. :)

since you are able to "see" the other AP's,the system is obviously "seeing" your card:

1- check your router and make sure that it is broadcasting it's ESSID. I used to not have mine do so, but the current version of network-manger would not "see" it, from either of my laptops, until I changed that setting.

2- are you able to connect to these other AP's from you xp box?

3- what wifi card are you trying to use? please post make/model/chipset

---

### Post by V3lier on 2007-08-10
> **jimrz said:**
> since you are able to "see" the other AP's,the system is obviously "seeing" your card:

1- check your router and make sure that it is broadcasting it's ESSID. I used to not have mine do so, but the current version of network-manger would not "see" it, from either of my laptops, until I changed that setting.

2- are you able to connect to these other AP's from you xp box?

3- what wifi card are you trying to use? please post make/model/chipset

1. Yup it's broadcasting
2. nope. I can see the other APs from Ubuntu too but I'm not able to connect because the signal bar is gray. It has no signal at all.
3. How can you figure out how to collect that data? I will google but an answer from you would be great.

---

### Post by V3lier on 2007-08-10
bump.

---

### Post by Paul133 on 2007-08-10
Open up a terminal and type ```
lspci -v
``` Post the output.

---

### Post by Talon2 on 2007-08-10
I can't from what you've said if you wireless is pci.  If so, type "lspci" in a terminal.

---

### Post by jimrz on 2007-08-10
from the terminal type
```
lspci
```
should the list the info you need 
copy and paste it into this thread.

---

### Post by V3lier on 2007-08-10
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
        Flags: bus master, fast devsel, latency 0
        Memory at 48000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: 41000000-421fffff
        Prefetchable memory behind bridge: 44000000-45ffffff

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 40000000-403fffff
        Prefetchable memory behind bridge: 30000000-300fffff

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05) (prog-if 80 [Master])
        Subsystem: Compaq Computer Corporation Unknown device 0083
        Flags: bus master, medium devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 2480 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation Unknown device 0083
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 2440 [size=32]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation Unknown device 0083
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 2460 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
        Subsystem: Compaq Computer Corporation Unknown device 008c
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 2000 [size=256]
        I/O ports at 2400 [size=64]

01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 0022
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
        Memory at 41000000 (32-bit, non-prefetchable) [size=16M]
        Memory at 44000000 (32-bit, prefetchable) [size=32M]
        [virtual] Expansion ROM at 42000000 [disabled] [size=64K]
        Capabilities: <access denied>

02:0b.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 6834
        Flags: bus master, slow devsel, latency 66, IRQ 19
        Memory at 40000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

02:0d.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 04 [Hayes/16750])
        Subsystem: PCTel Inc Unknown device 0001
        Flags: medium devsel, IRQ 16
        I/O ports at 1400 [size=64]
        Capabilities: <access denied>

02:0f.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
        Subsystem: Accton Technology Corporation EN-1207D Fast Ethernet Adapter
        Flags: bus master, medium devsel, latency 66, IRQ 17
        I/O ports at 1000 [size=256]
        Memory at 40100000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: <access denied>

That is what I got. Sorry for taking so long.

---

### Post by V3lier on 2007-08-10
Bump.

---

### Post by V3lier on 2007-08-10
Bump. Please help. :)

---

### Post by V3lier on 2007-08-10
I'm am EXTREMELY sorry for being a nag but...bump.

---

### Post by V3lier on 2007-08-10
Help please.

---

### Post by Paul133 on 2007-08-10
You have the RaLink RT2500, which I'm pretty sure is extremely well-supported. Since you can see other networks, wireless is definitely working. The problem seems to be that you can't find your network.  Try ```
sudo iwlist scanning
``` and post the output, OK? The problem seems to be that your router is not broadcasting its ESSID. I don't think I can help you with that, but hopefully someone else can. FInally, as frustrating as it is, don't bump every 5 minutes.

---

### Post by V3lier on 2007-08-10
l0 Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
ra0 scan completed:
      Cell 01 - Address : 00:14:6c:94:04:9A
      Mode: Managed
      Essid:"NETGEAR"
      Encryption key: on
      Channel:11
      Quality: 0/100 signal level: -52dBm Noise level:-211 dBm
     
     Cell 02 - Address: 00:14:6C:89: DE
     Mode: Managed
     Essid:"jill"
     Encryption key: off
     Channel:11
     Quality: 0/100 Signal level: -97 dBm Noise level: -212 dBm

---

### Post by Paul133 on 2007-08-10
So you can only see those two networks. What is the name of your network? And do you know what router you have?

---

### Post by V3lier on 2007-08-10
> **Paul133 said:**
> So you can only see those two networks. What is the name of your network? And do you know what router you have?

Yeh. One is the netgear one which is mine. The other one is just one that I've picked up. My router is Netgear WGR614 v6. I think the name of my network is NETGEAR. The two networks visible are "NETGEAR"(mine) and "jill"(random.).

---

### Post by Paul133 on 2007-08-10
OK, so you can see your network. Can you connect to your network, but you don't have a strong signal or are you unable to connect. What's the problem?

---

### Post by V3lier on 2007-08-10
> **Paul133 said:**
> OK, so you can see your network. Can you connect to your network, but you don't have a strong signal or are you unable to connect. What's the problem?
Well. I can't seem to connect. I know the password but it keeps searching but doesn't connect. I connected once and no signal and when I tried again it didn't work. Even right now I have no signal. Like; theres a bar which when it has a strong signal it fills up with red but its in gray with no signal at all.

---

### Post by Paul133 on 2007-08-10
So you see an icon for the network manager at the top right?

---

### Post by V3lier on 2007-08-10
> **Paul133 said:**
> So you see an icon for the network manager at the top right?
Yes. I click it and it shows the two networks.

---

### Post by medley on 2007-08-10
> **V3lier said:**
> Yes. I click it and it shows the two networks.

In your network manager, check and see what the default gateway address is. It should show the IP address of your router (192.168.X.1) I don't know what model router you have so the X could be a 0 or 1. You need to make sure that the default gateway points to your router. Also ensure that the device is the same name as your wireless interface. I had a hard time with this recently.

Network manger doesn't seem to save what you type in here. Apparently your driver is working and your card can see your router, but you can't connect to the router. 

If you type 'ifconfig', what do you get?

---

### Post by V3lier on 2007-08-10
> **medley said:**
> In your network manager, check and see what the default gateway address is. It should show the IP address of your router (192.168.X.1) I don't know what model router you have so the X could be a 0 or 1. You need to make sure that the default gateway points to your router. Also ensure that the device is the same name as your wireless interface. I had a hard time with this recently.

Network manger doesn't seem to save what you type in here. Apparently your driver is working and your card can see your router, but you can't connect to the router. 

If you type 'ifconfig', what do you get?
I don't see anything telling me about the default gateway address I just my IP address and netmask. I checked the wireless connection on WIndows XP and the Default Gateway IP is 192.168.1.1. I will post what I get from ifconfig soon.

---

### Post by V3lier on 2007-08-10
> **V3lier said:**
> I don't see anything telling me about the default gateway address I just my IP address and netmask. I checked the wireless connection on WIndows XP and the Default Gateway IP is 192.168.1.1. I will post what I get from ifconfig soon.
eth0      Link encap:Ethernet  HWaddr 00:30:F1:26:3E:5D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2504 (2.4 KiB)  TX bytes:2504 (2.4 KiB)

ra0       Link encap:Ethernet  HWaddr 00:13: D3:6C:63:21  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:3580513 (3.4 MiB)
          Interrupt:19 Base address:0x8000 

That's what I got.

---

### Post by jimrz on 2007-08-11
> **V3lier said:**
> 00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
        Flags: bus master, fast devsel, latency 0
        Memory at 48000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: 41000000-421fffff
        Prefetchable memory behind bridge: 44000000-45ffffff

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 40000000-403fffff
        Prefetchable memory behind bridge: 30000000-300fffff

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05) (prog-if 80 [Master])
        Subsystem: Compaq Computer Corporation Unknown device 0083
        Flags: bus master, medium devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 2480 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation Unknown device 0083
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 2440 [size=32]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation Unknown device 0083
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 2460 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
        Subsystem: Compaq Computer Corporation Unknown device 008c
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 2000 [size=256]
        I/O ports at 2400 [size=64]

01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 0022
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
        Memory at 41000000 (32-bit, non-prefetchable) [size=16M]
        Memory at 44000000 (32-bit, prefetchable) [size=32M]
        [virtual] Expansion ROM at 42000000 [disabled] [size=64K]
        Capabilities: <access denied>

02:0b.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 6834
        Flags: bus master, slow devsel, latency 66, IRQ 19
        Memory at 40000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

02:0d.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 04 [Hayes/16750])
        Subsystem: PCTel Inc Unknown device 0001
        Flags: medium devsel, IRQ 16
        I/O ports at 1400 [size=64]
        Capabilities: <access denied>

02:0f.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
        Subsystem: Accton Technology Corporation EN-1207D Fast Ethernet Adapter
        Flags: bus master, medium devsel, latency 66, IRQ 17
        I/O ports at 1000 [size=256]
        Memory at 40100000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: <access denied>

That is what I got. Sorry for taking so long.

seems your RaLink RT2500 802.11g needs a bit of tweaking to get it running...check out [[COLOR="Sienna"]**_this_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=519280&highlight=rt2500") thread that seems to have worked for others with the same wifi chipset

---

### Post by V3lier on 2007-08-11
Uhm. I'm sorry to be a complete noob but what exactly do I do? Do I go [here]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads") and download the driver for RT2500? Also how would I install the driver? I don't have the internet working in Ubuntu so I can't go to the site to get it.

---

### Post by V3lier on 2007-08-11
*Bump*

---

### Post by V3lier on 2007-08-11
*Bump*

---

### Post by jimrz on 2007-08-11
> **V3lier said:**
> Uhm. I'm sorry to be a complete noob but what exactly do I do? Do I go [here]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads") and download the driver for RT2500? Also how would I install the driver? I don't have the internet working in Ubuntu so I can't go to the site to get it.

one would guess...I just searched the forums for "RT2500" found a thread marked "resolved" and pointed you to it, I do not have a card with that chipset so no actual experience of it

since you obviously have net access on at least 1 machine, you could d/l the driver to the one you are currently on, copy to thumb drive/cd/whatever and then from there to your ubuntu box in order to get it installed. a bit of a long way around, but it should work.

---

### Post by Talon2 on 2007-08-11
Based on your lspci post it appears your wireless is provided by a RaLink RT2500 mini pci card.  I don't have that card so won't be much help but here is what I would do if I were you:

Do a search of the forums here using these keywords:  "RaLink RT2500"

---

### Post by medley on 2007-08-11
> **V3lier said:**
> eth0      Link encap:Ethernet  HWaddr 00:30:F1:26:3E:5D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2504 (2.4 KiB)  TX bytes:2504 (2.4 KiB)

ra0       Link encap:Ethernet  HWaddr 00:13: D3:6C:63:21  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:3580513 (3.4 MiB)
          Interrupt:19 Base address:0x8000 

That's what I got.

Based on what I see here, I think your driver is working. It looks like your wireless interface has transmitted 3.4meg of stuff and hasn't heard anything back. That would suggest to me that the problem might not be the driver but that your wireless isn't able to communicate with the router. I would see if you can find out where to configure your default gateway.
In my network manager (I'm using KDE) it's under the 'routes' tab. It should specify the address of your router, and the name of your wireless interface (ra0 in your case, I think).

---

