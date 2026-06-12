---
title: "Internet ARGH!"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by tori192 on 2007-04-26
Hi,
So I've got a problem with the internet on Ubuntu...
Im booting with the live CD (I don't want to install until I'm entirely sure about my choisce of Linux distro) and the pc can find my windows network fine and the internet works works fine with xp but zilch on Ubuntu. I'm using a linksys BEFSR41 connected to my pc with a linksys WRT54G connecting the router for my oc with the rest if the network in my house (ie. mum's laptop,dad's pc etc) I can ping my router and can access files on other computers in the network fine.
I've had a look through the forums and tried some people's advise (turning everything off etc) and ive ran some commands which people have suggested... here are my results:
> ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:92:02:A9:63  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe02:a963/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5149 (5.0 KiB)  TX bytes:9320 (9.1 KiB)
          Interrupt:58 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)


> ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1A:92:02:A9:63  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe02:a963/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12018 (11.7 KiB)  TX bytes:18467 (18.0 KiB)
          Interrupt:58 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


> ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


> ubuntu@ubuntu:~$ nslookup [www.google.com](www.google.com)
;; connection timed out; no servers could be reached

> ubuntu@ubuntu:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:92:02:a9:63
Sending on   LPF/eth0/00:1a:92:02:a9:63
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.100 -- renewal in 81728 seconds.

If you could help it would be much appreciated

Vicki

---

### Post by annda on 2007-04-26
hmm, your network looks fine. whaty exactly is your pronlem? can you rephrase the question? that would be great.

---

### Post by Seisen on 2007-04-26
Have you changed the settings in the System>Administration>Network and did you set put in the right dns numbers.

---

### Post by tori192 on 2007-04-26
Which are the dns numbers?
...
actually i think i tried that a bit back but couldn't be bothered to use the forum lol

---

### Post by Seisen on 2007-04-26
Like my dns # is 192.168.1.1 which is the same way that i access my router. Do you have it set to give you a IP address via DHCP or is it set not to do that on your router.

---

### Post by tori192 on 2007-04-26
My internet & router are set to DHCP so is ubuntu...

---

### Post by Seisen on 2007-04-26
What is the name of your network card?

---

### Post by tori192 on 2007-04-26
I don't have a clue... how do I find that out?

---

### Post by Seisen on 2007-04-26
```
lspci
``` in the terminal

---

### Post by tori192 on 2007-04-26
> ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. Unknown device 0327
00:00.1 Host bridge: VIA Technologies, Inc. Unknown device 1327
00:00.2 Host bridge: VIA Technologies, Inc. Unknown device 2327
00:00.3 Host bridge: VIA Technologies, Inc. Unknown device 3327
00:00.4 Host bridge: VIA Technologies, Inc. Unknown device 4327
00:00.5 PIC: VIA Technologies, Inc. Unknown device 5327
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6327
00:00.7 Host bridge: VIA Technologies, Inc. Unknown device 7327
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. Unknown device a327
00:03.0 PCI bridge: VIA Technologies, Inc. Unknown device c327
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A PCI to PCIE Bridge
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0393 (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
Well at least I'm getting some exercise - running up and down stairs lol

---

### Post by Seisen on 2007-04-26
I have the same one too and it works fine. If you can eliminate the second router and try to see if it works.

---

### Post by tori192 on 2007-04-26
I can't because the ethernet wires run through the loft and round the outside of my house just to get from downstairs to my bed room...  I had the same problem with a distri called slax (My dad found it).  I guess I'm just going to have to try a different distro...

---

### Post by Seisen on 2007-04-26
Can you ping both of the routers or just one.

---

### Post by tori192 on 2007-04-26
My computer can access it because it can access the network so it must go through the router...

---

### Post by tori192 on 2007-04-26
do you think it could be to do with ntl/virgin media? because they are my internet providers

---

### Post by srt4play on 2007-04-26
Run this in a terminal and post the output:

```
cat /etc/resolv.conf
```

---

### Post by Seisen on 2007-04-26
It it works in windows that it should work in ubuntu.

---

### Post by tori192 on 2007-04-26
Right I can ping this computer (its on xp and a different pc) but i can't trace the route to it the command thing crashes after reaching my router

---

