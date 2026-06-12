---
title: "nVidia card not default display in ubuntu"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Domino3 on 2007-08-25
Ok so I have a nVidia Geforce FX5200 video card but when i boot the live cd i get a black screen. But when i use the onboard graphics it works. How do i use my geforce instead of my onboard graphics?

---

### Post by henriette_holm on 2007-08-25
Hi.
I don't have a nvidia graphics adapter but try looking at this page:

[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

/Henriette

---

### Post by immortals on 2007-08-25
So when you are using the live CD you see nothing? That's impossible. You must see some Ubuntu logo, or I can' imagine...

After you probably install the whole Ubuntu operating system, you can customise your video card easily with the automatically downloaded video card drivers.

I don't understand why you are using your live CD, or you are just meeting Ubuntu, I mean how it looks like or how it works?

Good luck

---

### Post by asmoore82 on 2007-08-25
is the nVidia card PCI?

---

### Post by Domino3 on 2007-08-25
The video card is pci

---

### Post by Domino3 on 2007-08-25
> **immortals said:**
> So when you are using the live CD you see nothing? That's impossible. You must see some Ubuntu logo, or I can' imagine...

After you probably install the whole Ubuntu operating system, you can customise your video card easily with the automatically downloaded video card drivers.

I don't understand why you are using your live CD, or you are just meeting Ubuntu, I mean how it looks like or how it works?

Good luck

I am going to install ubuntu to use beryl and stuff but I can't because since it doesn't pickup my video card. Well, it does in the hardware section but I have to use intergrated graphics to install.

---

### Post by henriette_holm on 2007-08-25
You can properly chance the settings after the installation. If the computer wont let you install try using the alternate cd. Then you'll end up in a terminal window and from thre you can install the needed drivers. I have the same sort of problem with my ATI and thats the way to sort it.

/Henriette

---

### Post by asmoore82 on 2007-08-25
> **Domino3 said:**
> The video card is pci

^^ like he said ...

the LiveCD will default to the first available card.
(An AGP card will "hide" your onboard video but a PCI card will co-exist with it)

It's not worth customizing setup and using the nVidia card until after the system is installed.

---

### Post by Domino3 on 2007-08-25
I can;t enable my card because I don't have internet. My wireless adapter works with ubuntu but I can't connect to the internet.

---

### Post by immortals on 2007-08-25
May I ask which distribution do you use?

I have tried Ubuntu 6.10 Edgy and now I am using 7.10 Feisty...
Normally at the first boot both of Ubuntu doesn't recognize my video card...

So don't be afraid, after a full install you can get the things fixed...

If you are using 6.10 I recommend that install Envy, than you can set your card working at the GUI.(But it needs internet connection)

Or if you use 7.04, it will recognize one half of your card, but it will show that you must use your internet once to get a proper driver. Besides it runs on a graphical interface, so it should be easy.

Let's try it, if you have stucked, drop me a line, and I will help.

P.S.: I have Nvidia card in my laptop, and at first it doesn't recognize it.But now it works!!!

Good luck

---

### Post by Domino3 on 2007-08-25
It won't use my PCI video card on first boot or any other. I have to use my Integrated graphics and it gets really annoying. I enable the one in restricted drivers but it won't enable it. I can't use my internet either for some reason. I think it's because My router has a Firewall. Might I ask, What port does ubuntu connect through? I am using Ubuntu 7.04

---

### Post by immortals on 2007-08-26
Well, to be honest I have no idea which port is used, but...

It would be easier if you try a normal wired internet connection to get the right packages.

Or you can use your live CD to browse with your Synaptic Package Manager to install the Graphical packages...
If it works, when you open a terminal and type "nvidia-settings" you should get your settings and customize them...

P.S.: Sorry I am a bit confused, but I know your problem, I had the same. But I solved myself. Can you give me your connection details? And the details of the whole problem once more?:confused:

---

### Post by Domino3 on 2007-08-26
The internet details. I have a WMP54G Linksys Wireless Network Adapter.
The ESSID I'm connecting to is 2Wire510.
It has WEP Encryptions. 64-bit.  And when I type Stuff I get:
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"2WIRE510"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:3F:A0:44:89   
          Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=82/100  Signal level=-65 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
        Subsystem: Trigem Computer Inc. Unknown device 7148
        Flags: bus master, fast devsel, latency 0

00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
        Subsystem: Trigem Computer Inc. Unknown device 7148
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 10
        Memory at ec000000 (32-bit, prefetchable) [size=64M]
        Memory at e8000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: e8100000-e9ffffff
        Prefetchable memory behind bridge: f0000000-f7ffffff

00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Intel Corporation 82801AA IDE
        Flags: bus master, medium devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 1080 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation 82801AA USB
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 10a0 [size=32]

00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
        Subsystem: Intel Corporation 82801AA SMBus
        Flags: medium devsel, IRQ 9
        I/O ports at 1100 [size=16]

00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
        Subsystem: Trigem Computer Inc. Unknown device 7148
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1200 [size=256]
        I/O ports at 1300 [size=64]

01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Trigem Computer Inc. Unknown device 7148
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at 2000 [size=256]
        Memory at e8100000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)
        Subsystem: Risq Modular Systems, Inc. Unknown device 044e
        Flags: medium devsel, IRQ 255
        Memory at e8100400 (32-bit, non-prefetchable) [disabled] [size=256]
        I/O ports at 2800 [disabled] [size=8]
        I/O ports at 2400 [disabled] [size=256]
        Capabilities: <access denied>

01:0d.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Linksys WMP54G 2.0 PCI Adapter
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at e8102000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

01:0e.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp. Unknown device b309
        Flags: 66MHz, medium devsel, IRQ 255
        Memory at e9000000 (32-bit, non-prefetchable) [disabled] [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [disabled] [size=128M]
        [virtual] Expansion ROM at e8120000 [disabled] [size=128K]
        Capabilities: <access denied>

ubuntu@ubuntu:~$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:12:17:83:81:dd
Sending on   LPF/ra0/00:12:17:83:81:dd
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by mysticmatrix on 2007-08-26
> **Domino3 said:**
> It won't use my PCI video card on first boot or any other. I have to use my Integrated graphics and it gets really annoying. I enable the one in restricted drivers but it won't enable it. I can't use my internet either for some reason. I think it's because My router has a Firewall. Might I ask, What port does ubuntu connect through? I am using Ubuntu 7.04

When you click on enable drivers, Ubuntu downloads the correct driver from Nvidia's website and installs them to your computer. If you don't have access to internet, you may download packages on some other computer and use a CD/USB key to install the drivers.

I don't know the correct packages, but some one else might help.

---

### Post by Domino3 on 2007-08-26
I don't get how I'm supposed to get internet because my computer is upstairs and my router is downstairs.
Just to add something, my videocard has dvi input but I have a DVI to VGA Adapter.

---

### Post by immortals on 2007-08-26
It's like mysticmatrix said:

The 7.04 would automatically download the driver, so you have to fix your internet connection.

Have you / Can you try wired connection? It would be the easiest way to get that nasty driver.

Good luck

---

### Post by Domino3 on 2007-08-27
No I can't because my router is downstairs and this computer is upstairs.

---

### Post by immortals on 2007-08-28
What else could I say for you?

pff... Sorry, C'est la vie...

:confused:

---

