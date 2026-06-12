---
title: "Help the new guy with his WiFi"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Howxat on 2007-01-30
I have ubuntu running nice and smooth on a tablet pc, and want to get wifi working on it. I am a complete newbie when it comes to linux, can anyone please help me out?

---

### Post by deadgobby on 2007-01-30
What is your WIFI card???

---

### Post by Howxat on 2007-01-30
It's a BT brand one (not sure if they were made by someone else originally or not)

---

### Post by dexter on 2007-01-30
Is the card listed in System, Administration, Networking ?

---

### Post by Howxat on 2007-01-30
I can't find anyone mention of my wireless card anywhere :( , except that the wireless card is getting power from the port.

---

### Post by JamieC on 2007-01-30
Can you please open a new terminal window (Applications -> Accessories -> Terminal) and post the output of the following command:-

If it is a PCI card:
```

lspci

```

If it is a USB adapter:
```

lsusb

```

---

### Post by Howxat on 2007-01-30
I used Lspci, and got a large steaming mound of data, which bit do you need to know :confused:

---

### Post by JamieC on 2007-01-30
> **Howxat said:**
> I used Lspci, and got a large steaming mound of data, which bit do you need to know :confused:

All of it, please. Attach it as a file or just paste it straight into a new post.

---

### Post by Howxat on 2007-01-30
Took a while to transfer it across to my other computer (this one) but here it is:

howard@trousers-laptop:~$ lspci
0000:00:00.0 Host bridge: Transmeta Corporation LongRun Northbridge (rev 03)
0000:00:00.1 RAM memory: Transmeta Corporation SDRAM controller
0000:00:00.2 RAM memory: Transmeta Corporation BIOS scratchpad
0000:00:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (r ev b2)
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (r ev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (re v 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 A udio Controller (rev 50)
0000:00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Contro ller (rev 30)
0000:00:08.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
0000:00:0a.0 Ethernet controller: Atmel Corporation at76c506 802.11b Wireless Ne twork Adaptor (rev 11)
0000:00:0b.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controlle r (rev 01)
0000:00:0b.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controlle r (rev 01)
0000:00:0c.0 USB Controller: NEC Corporation USB (rev 41)
0000:00:0c.1 USB Controller: NEC Corporation USB (rev 41)
0000:00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 02)

---

### Post by Howxat on 2007-01-30
Okay, so anyone know what I can do?

---

### Post by deadgobby on 2007-01-30
Please try this link.
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking?highlight=%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking?highlight=%28wireless%29)


Gobby

---

### Post by Howxat on 2007-01-30
I followed the guide and looking in network settings. I have two wireless connections right now, eth1 and eth 2. I put the details of my wireless network into eth1 and activated it, but still no internet connection,

---

### Post by deadgobby on 2007-01-30
Please open up the Terminal and copy and paste this command. Then post back the results.

lspci -v | less

Gobby

---

### Post by Howxat on 2007-01-30
howard@trousers-laptop:~$ lspci -v
0000:00:00.0 Host bridge: Transmeta Corporation LongRun Northbridge (rev 03)
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, medium devsel, latency 64
        Memory at e8100000 (32-bit, non-prefetchable) [size=1M]

0000:00:00.1 RAM memory: Transmeta Corporation SDRAM controller
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: fast devsel

0000:00:00.2 RAM memory: Transmeta Corporation BIOS scratchpad
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: fast devsel

0000:00:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (r ev b2) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 11
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at 18000000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (r ev 40)
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at 1040 [size=16]
        Capabilities: <available only to root>

0000:00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (re v 40)
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: medium devsel, IRQ 10
        Capabilities: <available only to root>

0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 A udio Controller (rev 50)
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: medium devsel, IRQ 7
        I/O ports at 1400 [size=256]
        I/O ports at 1054 [size=4]
        I/O ports at 1050 [size=4]
        Capabilities: <available only to root>

0000:00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Contro ller (rev 30)
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: medium devsel, IRQ 7
        I/O ports at 1800 [size=256]
        Capabilities: <available only to root>

0000:00:08.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, medium devsel, latency 66, IRQ 9
        Memory at e8020000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1000 [size=64]
        Memory at e8000000 (32-bit, non-prefetchable) [size=128K]
        Expansion ROM at 18010000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:00:0a.0 Ethernet controller: Atmel Corporation at76c506 802.11b Wireless Ne twork Adaptor (rev 11)
        Subsystem: Compaq Computer Corporation: Unknown device 00d3
        Flags: bus master, fast devsel, latency 99, IRQ 15
        Memory at e8030000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at 1c00 [size=256]
        Capabilities: <available only to root>

0000:00:0b.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controlle r (rev 01)
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, medium devsel, latency 168, IRQ 9
        Memory at 18020000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
        Memory window 0: 10000000-11fff000 (prefetchable)
        Memory window 1: 12000000-13fff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

0000:00:0b.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controlle r (rev 01)
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 18021000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 14000000-15fff000 (prefetchable)
        Memory window 1: 16000000-17fff000
        I/O window 0: 00002800-000028ff
        I/O window 1: 00002c00-00002cff
        16-bit legacy interface ports at 0001

0000:00:0c.0 USB Controller: NEC Corporation USB (rev 41) (prog-if 10 [OHCI])
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, medium devsel, latency 64, IRQ 9
        Memory at e8022000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:0c.1 USB Controller: NEC Corporation USB (rev 41) (prog-if 10 [OHCI])
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at e8023000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 02) (prog-if 20 [EHCI] )
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, medium devsel, latency 132, IRQ 7
        Memory at e8021000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

---

### Post by deadgobby on 2007-01-30
Wow that gave me every thing. Tee hee, but really it is this command

lspci -v | less

Just copy and paste that. I just want to see which card is active.:D :D :D 

Gobby

---

### Post by Howxat on 2007-01-30
I can't copy and paste between computers, so I was wondering what is the character between "v" and "less"? thanks

---

### Post by Duppy on 2007-01-30
Connection-Manager is the best wifi manager.

Search for it in google and it will lead you back to a forum on this site.

---

### Post by phossal on 2007-01-30
> **Howxat said:**
> I can't copy and paste between computers, so I was wondering what is the character between "v" and "less"? thanks

It's often above the \ key. It's a vertical bar. It may appear something like a colon, but the two shapes are lines rather than dots. It's the "pipe" command character.

---

### Post by Howxat on 2007-01-30
Found it, thanks a lot :) terminal code inc:

0000:00:00.0 Host bridge: Transmeta Corporation LongRun Northbridge (rev 03)
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, medium devsel, latency 64
        Memory at e8100000 (32-bit, non-prefetchable) [size=1M]

0000:00:00.1 RAM memory: Transmeta Corporation SDRAM controller
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: fast devsel

0000:00:00.2 RAM memory: Transmeta Corporation BIOS scratchpad
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: fast devsel

0000:00:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 11
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at 18000000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if
8a [Master SecP PriP])
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at 1040 [size=16]
        Capabilities: <available only to root>

0000:00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
        Subsystem: Compaq Computer Corporation: Unknown device 00b5
        Flags: medium devsel, IRQ 10
        Capabilities: <available only to root>
:

---

### Post by deadgobby on 2007-01-30
Ok I think I found the driver for it. Can you post the reply after this command

lspci

Gobby

---

### Post by Howxat on 2007-01-30
0000:00:00.0 Host bridge: Transmeta Corporation LongRun Northbridge (rev 03)
0000:00:00.1 RAM memory: Transmeta Corporation SDRAM controller
0000:00:00.2 RAM memory: Transmeta Corporation BIOS scratchpad
0000:00:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 30)
0000:00:08.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
0000:00:0a.0 Ethernet controller: Atmel Corporation at76c506 802.11b Wireless Network Adaptor (rev 11)
0000:00:0b.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:00:0b.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:00:0c.0 USB Controller: NEC Corporation USB (rev 41)
0000:00:0c.1 USB Controller: NEC Corporation USB (rev 41)
0000:00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 02)

---

### Post by deadgobby on 2007-01-30
If you have internet connection on the system we are working on. Do this......
Open up Synaptic. It will ask for a password. Should be the one you use at your splash screen login. After Synaptic opens up.
Synaptic can be found at System>Admin>Synaptic
When that open up click on search and type in 
firmware
After is does it seach. There should be atmel-firmware
  Firmware for Atmel at76c50x wireless networking chips.
The drivers for these chips in the Linux 2.6.x kernel do not include
the firmware; this firmware needs to be loaded by the host on most
cards using these chips. This package provides the firmware images
which should be automatically loaded as needed by the hotplug
system. It also provides a small loader utility which can be used to
accomplish the same thing when hotplug is not in use.

 Right click on it and scroll down to mark for install. After you check mark it. Click on the apply button and see if you can get connected.

Gobby

PS I have my fingures cross on this. After that I am dumbfounded...

---

### Post by Howxat on 2007-01-30
Sorry to waste your time, but I'm fairly sure I can't do that. This computer is an apple mac, running completely different hardware and software to the problem computer.

---

### Post by mdsmedia on 2007-01-30
Howxat, is it possible for you to get WIRED (ie. ethernet cable) access to the internet from your tablet, in order to load the firmware for wireless internet?

---

### Post by Howxat on 2007-01-30
I haven't tried a wired connection, but it would probably work. From reading various how-tos, I think the problem is lack of drivers for the wifi card.

---

### Post by mdsmedia on 2007-01-30
I'd suggest getting wired access for the tablet, so you can do what gobby suggested with internet access. Then see if your wireless will work after the firmware is installed.

I say that because Gobby seems to have found the solution, but you need internet access to install it.

---

### Post by Howxat on 2007-01-30
okay thanks a lot, I'll try that tomorrow and repoty back :D

---

### Post by deadgobby on 2007-01-30
With you comp specs you have a an Intel Eithernet card that may be hard wire in. After wired in reboot and see if you get the internet.
NOw you are going to keep my in limbo till tomorrow. Uggg :>)

Gobby

---

