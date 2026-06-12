---
title: "Connecting to Internet (Another one)"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Sanchopinky on 2007-03-15
I was one of those windows xp users starry-eyed and eager to use linux.

So I installed Ubuntu (the latest) and I'm having issues connecting to the internet. I have the same problems as others (ethernet card detection) except I'm not trying to use wireless.

Following results:

When I tried to see if my Ethernet card  was detected I got a bunch of numbers. Sof I cant even see if it's compatible or detected or even running.

Modem [Westell 327w] gave me some IP addresses.

I checked "Configuring PPPoE with the command line", I was following the instructions, but when I got to the password part it won't even let me type it all in before it tells me it's wrong.

I know it's kind of generic but if you guys could help steer me in the right direction. I am most willing to give you any information you need. 

Please help.. I dont want to go back to XP

---

### Post by inCursorated on 2007-03-15
we're going to need some more details. what kind of NIC is it (lspci)? What does ifconfig -a return? is there a data link light? what kind of connection do you have? usually PPPoE is handled by a router...

---

### Post by Sanchopinky on 2007-03-15
I have a dsl connection but when I checked the guide I keep getting redirected to the PPOE configuration because I use an ethernet cable to connect to pc~


This is the lspci:

00.00.0 Host bridge:ATI Technologies inc unknown device 5a33
00:01:0 PCI bridge: ATI Technologies inc rs480 pci bridge
00:11:0 IDE Interface: ATI Technologies inc ATI 437a serial ata controller (rev80)
00:13:0 IDE Interface: ATI Technologies inc ATI 4379 Serial ATA Controller (rev80)
00:13:0 USB Controller: ATI Technologies inc IXP SB400 USB Host Controller(rev80)
00:13:1 USB Controller: ATI Technologies inc IXP SB400 USB Host Controller(rev80)
00:13:2 USB Controller: ATI Technologies inc IXP SB400 USB2 Host Controller(rev80)
00:14:0 SMBus : ATI technologies inc IXP SB400 SMBus Controller (rev 81)
IDE INTERFACE: ATI TECHNOLOGIES INC STANDARD DUAL CHANNEL PCI IDE CONTROLLER ATI (REV80)
AUDIO DEVICE: ATI TECHNOLOGIES INC UNKNOWN DEVICE 437B (REV 01)
ISA BRIDGE: ATI TECHNOLOGIES INC IXP SB400 PCI-ISA BRIDGE (REV 80)
 PCI BRIDGE: ATI TECHNOLOGIES INC IXP SB400 PCI-PCI BRIDGE (REV 80)
VGA COMPATIBLE CONTROLLER: ATI TECHNOLOGIES INC RC410 [RADEON XPRESS 200]
ETHERNET CONTROLLER: REALTEK SEMICONDUCTOR CO., LTD. RTL-8139/8139C/8139
C+ (REV 10)
COMMUNICATION CONTROLLER: CONEXANT HSF 56K DATA/FAX MODEM


This is what the ifconfig -a returns:

eth0     Link encap:Ethernet HWaddr 00:17:31: DB:16:54
            inet6 addr: fe80::217:31ff:fedb:1654/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
           RX packets:21 errors:0 dropped:0 overruns:0 frame:0
           TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:3024 (2.19 kiB) TX bytes:1188 (1.1 KiB)
           Interrupt:201 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1   Mask:255.0.0.0
          inet6 addr: ::1/28  Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)

sit0     Link encap:IPv6-in-IPv4
          NOARP   MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Sanchopinky on 2007-03-15
> **inCursorated said:**
> we're going to need some more details. what kind of NIC is it (lspci)? What does ifconfig -a return? is there a data link light? what kind of connection do you have? usually PPPoE is handled by a router...


I answered what I could, but could you please specify on the data link light? Do you mean on the modem?


Any help would be appreciated!

---

### Post by inCursorated on 2007-03-15
by data link light i mean the LED indicator on the NIC where you plug the ethernet cable in... not all NICs have them but most do

from the lspci output, it looks like your NIC was recognized properly...

eth0 (from ifconfig) is your ethernet network adapter. the fact that it's listed indicates it's probably working properly. if you can ping the loopback address (ping 127.0.0.1) then it's working. 

without knowing anything about your dsl router configuration, it's hard for me to say where to go from here. but PPPoE is definitely handled by the router, so you should only have to worry about IP settings... i'm not sure what u mean by getting redirected to the PPPoE config, what guide are you refering to? i assume it's on the dsl, provided by your ISP. every home dsl router that i've worked with was pre-configured with NAT and DHCP... but if that was the case for you it should have connected automatically (to be certain you can try: sudo ifconfig eth0 up; sudo dhclient eth0)

do you have any info on the router setup (IP addresss, NAT/no NAT, subnet, etc)? is there a switch in front of the router? are any other computers using the dsl connection now? that's about all i could think of... i'll be online for awhile and should be able to respond in a timely fashion...

---

### Post by inCursorated on 2007-03-16
i think maybe i got carried away and over-complicated things...

u made several references to modem and ethernet. to clarify, is there a cat5 (or similar; RJ-45) network cable connected from your pc to your router (or switch)? the pc's modem should not be involved here... 

also, is this the same machine that u were running xp on?

---

### Post by Sanchopinky on 2007-03-16
Yes this is the same machine I used to have XP on.

The only thing connected to my pc is the modem, (westell 327w) provided from verizon, and the only thing linking them is the ethernet cable. Yes, there is a on/off switch at the back. All the lights are lit up too. The only other thing using the internet connection is my  old laptop which I am using now. 

You mentioned something about eth0 yes it is being listed but it lists 'unkown' on some parts.. I don't know if that makes a difference. The PPPOE guide I was reffering to is the one on the Help guide that comes with Ubuntu.

---

### Post by oilchangeguy on 2007-03-16
just an idea. have you reset the modem (turned it off) since you install ubuntu on the computer? if not try that.

---

### Post by jhenager on 2007-03-16
In Administration>Networking, do you see eth0? If so, is it activated? Most of the time, you will use DHCP, which requests an IP address from your router. PPPoE stands for Point to Point Protocol over Ethernet, which means that you establish a direct connection between one computer and another over the net. This requires a username and password. Most home DSL/cable setups don't require that.

---

### Post by Sanchopinky on 2007-03-16
I went to administration and networking but I didnt see Eth0. The only thing that I saw was Wireless connection and Modem connection with a '-' sign. It says the modem connection has not been configured yet.. Would I need to contact my ISP to find out the details so I can fill in the blanks?

---

### Post by oilchangeguy on 2007-03-16
no, the modem connection is the computers internal phone modem. and since you use dsl, you connect to your isp's external modem via your computers network card. your computer does have a network card, right? does the dsl modem connect to a network card or a usb port?

---

### Post by fanny on 2007-03-16
listen i had the same problem . i will try to guide you step by step , my english isnt so good so try to understand. 
first you need to type in the terminal: "sudo pppoeconf" ( without" "). if you already did it o.k.
 if not ,say yes to all the questions , dont forget to type your user name and password correct.
 if you see under : system >administration>networking "eth0" its o.k. your modem isnt importent now.

---

### Post by Sanchopinky on 2007-03-16
I love you guys. :D (not in a weird way)

Thank you guys for the help! I finally got it working!!

---

