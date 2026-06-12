---
title: "Sorry, help on wireless network ona laptop please?"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by shutterpunk on 2007-06-30
Hi guys and gals, first of all thanks for haing such a great site, i have been searching around and looking for answers to my questions for a couple of days now and the wealth of knowledge you have is great! However, i seem to be a bit of a dunce!
Im a life long MS sheep and am used to their way of thinking so Ubuntu is taking some getting used to on my part im sad to say :-(
Anyway, i have read through a lot of info on wireless networking but im afraid my tech knowledge needs some help, 
I have installed version 6.06, i tried the latest version but the cd took forever and kept stalling at the last hurdle so i gave up, is it possible to upgrade now i have 6.06 installed or is it a fresh install? Presumably with a fresh download too?
Sorry im rambling, 
I have 6.06 installed and i have a belkin wireless pcmcia card installed, i looked it up on the compatablity list and it is a F5D7010 which should apprently work out of the box... Anyway i dont think it is. I found some code that i was told to type into
/etc/network/interfaces 
to get it working with a WPA preshared key setup and still nothing, i was wondering if anyone could talk me through it and just explain any diagnostic steps to me so that i dont ever have to ask again, i dont jus want it fixed, i want to understand a little about how and why it is working.
Sorry to be such a pain, im sure you are all fed up of questions like this but any help would really be appreciated.
thanks once again!
Rob

---

### Post by mlentink on 2007-06-30
What version of that card do you have Rob? 

Googling around I found at least four different versions of that card:

 802.11g 	 F5D7010 	 man: 1799 dev: 7010 	 Cardbus 	 Broadcom 	 bcm43xx 	 yellow  	 [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)
802.11g 	F5D7010 revision 3000ef 	man:1814 dev:0201 	Cardbus 	Ralink 	rt2x00 	green 	Driver available from manufacturer: [http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html) , or [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
802.11g 	F5D7010 revision 3001 	man:1814 dev:0201 	Cardbus 	Ralink 	rt2x00 	green 	Driver available from manufacturer: [http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html) , or [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
802.11g 	F5D7010 v.5100 	man: 168c dev: 001a 	Cardbus 	Atheros 	Mad WiFi 	green 	driver available at: [http://madwifi.org](http://madwifi.org)

Since my desktop uses an Atheros based card as well, I know that version should work with WPA, but I' m not sure about the others.
Have you tried it with WEP already?

---

### Post by shifty_powers on 2007-06-30
Have you thought about using something such as ndiswrapper? (in the repo's). Allows you to use the windows drivers, (hopefully), for your card....

---

### Post by shutterpunk on 2007-06-30
I have found it on this list, [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin")
I believe it is the RT2500 version and i believe version 6.06 is breezy? I get confused! 
Is there anything i can do/type to find out if the card is being seen by the system and therefor determine if its the driver thats the problem or the WPA/network settings? I could switch to WEP i guess but is that any easier?
Rob

---

### Post by mlentink on 2007-06-30
> **shutterpunk said:**
> I have found it on this list, [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin")
I believe it is the RT2500 version and i believe version 6.06 is breezy? I get confused!No woriies, well get you there. If not through me then through some of the more knowledgeable guys. There seem to be even more versions than I thought.  btw Ubuntu 6.06 is 'Dapper Drake', 
> **shutterpunk said:**
> Is there anything i can do/type to find out if the card is being seen by the system and therefor determine if its the driver thats the problem or the WPA/network settings? I could switch to WEP i guess but is that any easier?
Rob
Yes, 's matter of fact you could! Open up a terminal and type
```
lspci -v

```That'll give us detailed info on the installed devices, including that Belkin. And yes, switching your AP to WEP might temporarily decrease your security, but many driver simply do not support WPA. If it works under WEP, then we could always try to figure a way to make it work with WPA as well...

---

### Post by shutterpunk on 2007-06-30
Here is the output from lspci -v

rob@rob-laptop:~$ lspci -v
0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Memory at f4400000 (32-bit, prefetchable) [size=4K]
        I/O ports at 8090 [disabled] [size=4]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: f4100000-f41fffff
        Prefetchable memory behind bridge: f6000000-f7ffffff

0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ALi Corporation USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f4010000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
        Subsystem: ALi Corporation ALI M1533 Aladdin IV ISA Bridge
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
        Subsystem: Compaq Computer Corporation: Unknown device 00b0
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 8400 [size=256]
        Memory at f4011000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
        Subsystem: Compaq Computer Corporation: Unknown device 00b0
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at ffbfe000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 10000000-11fff000 (prefetchable)
        Memory window 1: 12000000-13fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
        Subsystem: Compaq Computer Corporation: Unknown device 00b0
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 8800 [size=256]
        Memory at f4013000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:0c.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
        Subsystem: Compaq Computer Corporation: Unknown device 8d89
        Flags: medium devsel, IRQ 10
        Memory at f4000000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at 8098 [size=8]
        Capabilities: <available only to root>

0000:00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ALi Corporation USB 1.1 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f4012000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if fa)
        Subsystem: ALi Corporation M5229 IDE
        Flags: bus master, medium devsel, latency 32
        I/O ports at 8080 [size=16]
        Capabilities: <available only to root>

0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: ALi Corporation M7101 Power Management Controller [PMU]
        Flags: medium devsel

0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1 (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation: Unknown device 00b0
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at f6000000 (32-bit, prefetchable) [size=32M]
        I/O ports at 9000 [size=256]
        Memory at f4100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at f4120000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:00.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
        Subsystem: Belkin: Unknown device 701a
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at 12000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

rob@rob-laptop:~$

---

### Post by shutterpunk on 2007-06-30
just to update, im poking around in the network tools section, i have tried to ping my router, 192.168.1.1 and i get 100% packet loss, however, under network name (ESSID) i am picking up my wireless network and another, presumably a neighbour..This i have confirmed on the windows laptop i am typing to you from now. The thing that is confusing me is that although the Ubuntu machine is picking up a network in range, none of the status lights are illuminated on the card? Is this normal?
Sorry to be such a noob!
Rob

---

### Post by mlentink on 2007-06-30
OK, we've defintely established you've got the Ralink RT2500 version, which many have gotten to work. So we'll get yours to work as well.
It's pretty late here, so I'm signing off for a few hours, but I'd like to point you to this [thread]("http://ubuntuforums.org/showthread.php?t=78250")
I'll be back as soon as I can, but there's likely to be someone in more convenient time zones to correct/augment me...

---

### Post by smo0th on 2007-06-30
I also have RT2500, there's a lot of help in other threads, you should take a good look at them and I'd recommend you install the RutilT WLAN Manager to quickly set the configuration.

You should have something like this in your /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
pre-up ifconfig eth0 down
pre-up ifconfig eth0 up

auto eth1 inet dhcp

auto ra0
iface ra0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "NETWORK"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="your key here"
pre-up ifconfig ra0 up

then in your /etc/resolv.conf you put your dns servers, ip addresses only

I recommend you use sudo nano /path/file to edit.

use sudo /etc/init.d/networking restart to restart your network interfaces.

:popcorn:

---

### Post by shutterpunk on 2007-07-01
ok i understand some of that, ill have a go and see how i do, please bare in mind that as a new user im only just getting the hang of commands and stuff! i find a lot of this confusing! 
As a matter of interest should the WPA passcode be in ascii or hex?

---

### Post by smo0th on 2007-07-03
oh yup, the passcode is hex coded, if you don't know how to hex code it post again and i'll take a look, right now i can't remember and i'm too sleepy hehehe, c ya later

---

