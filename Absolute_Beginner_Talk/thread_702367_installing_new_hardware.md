---
title: "installing new hardware"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by abooks on 2008-02-20
I'm trying to install a wireless PC card. Ubuntu says it can't read the CD, nor any of the files on it.So far, I can't find any place that tells me, the rankest beginner, how to do that. I've gone to "absolute beginner talk" and I find things like this: 
a) If it continously fail regarding borked CD, mismath checksum, download the .iso from another mirror." Now I'm sorry, but I don't speak this language. Could somebody tell me where I should go to find something that says Step 1. turn on the computer. Step 2, click on the upper right hand thingy. You have to tell ubuntu this. . ." It looks like "Absolute Beginner talk" is not the place to start. Can someone tell me how to get to step one?

---

### Post by jan quark on 2008-02-20
welcome 

nobody speaks that weird language in the beginning so relax

it would be good to know what your network card is:

do this step by step, and only one step at a time:

go to

application > accessories > terminal

type in these commands, press enter after every command and post the output here
copy ctrl+C, and paste ctrl+v 

```
iwconfig
```

```
ifconfig
```

```
lspci
```

```
sudo lshw -C network
```

linux is case sensitive so the capital C is really a capital C.

---

### Post by abooks on 2008-02-20
I may haveto do this in two pieces: I have to go to work, and I'm using another computer, so I have to transcribe all the findings.

for iwconfig:

lo no wireless extensions
eth no wireless extensions

for ifconfig

eth link encap: ethernet  HW addr 00:00:86:4B:0A:BA
UP broadcast multicast  MTU 1500  Mteric :1
RX packets :0 error: 0 dropped 0 overruns 0 frame 0
TX pacfkets 0 errors 0 dropped 0 overruns 0 carrier 0
collisions 0 txquelen 1000
RX bytes 0 (0.) b) TX bytes 0 (9.) b)
Interrupt: 11 Base address: 0x6c00

OUt of time, do te rest later. Thanx

---

### Post by abooks on 2008-02-20
response to lspci

00:00.0 Host Bridge: Intel Corp 440 BX/ZX/DX- 82443 BX/ZX/DX Host Bridge (rev 03)

00:021.0 PCI Beridge: Intel Corp 440 BX/ZX/DX - 82443BX/ZX/DX Agp bridge (rev 03)

00:03.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus controller

00:03.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus controller

00:07.0 Bridge: Intel Corp  82371AB/EB/MB PIIX4 ISA (rev 02)

00:07.1 IDE Interface: Intel Corp 82371AB/EB/MB PIIX4 IDE (rev 01)

00:07.2 USB Controller: Intel Corp 82371AB/EB/MB PIIX4 USB (rev 01)

00:07.3 Bridge: Intel Corp 82371AB/EB/MB PIIX4 ACPI (rev 03)

00:08.0 Multimedia audio Controller: ESS technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)

00:10.0 Ethernet controller: 3Com Corp  3c556 Hurricane Cardbus  [cyclone] (rev 10)

00:10.1 Communication controller: 3Com Crop Mini PCI 56k Winmodem (rev 10)

01:00.0 VGA compatible Controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 2)


And the exact wording I got when I tried to run the autorun.exe file was "No application suitable for automatic installation available for handling this kind of file"

Thanks for your patience. I hope you can make something of this.

---

### Post by abooks on 2008-02-20
oops, you wanted me to run sudo lshw -C network, too

response was:

*-network

description: Ethernet interface
product: 3c556 Hurricane Cardbus [cyclone]
vendor: 3Com corporation
physical id: 10
bus info: pci@0000:00:10.0
logical name: eth0
version: 10
serial: 00:00:86:4b:0a:ba
size: 10 MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt-fd autonegotiation
Configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no max latency=5 mingnt=10 module=3c59x multicast=yes port MII speed=10MB/s

now I remember why I'm not a secretary or data inputter

---

### Post by jan quark on 2008-02-20
so you have already inserted the wireless card into the PC?

because if yes, then ubuntu has not detected it in the first place

only the wired connection is active and the drivers are enabled but only for the wired connection

what the type of your wlan card, brand ?

---

### Post by abooks on 2008-02-22
Actually I didn't insert the card. . .the instructions said to run the cd first, so I was trying to do that. Now I gather the cd only is used in windows devices? I got a Netgear Super G wireless card, which the ubuntu hardware site indicate would work on my machine. . .I think. So I should just insert the thing anyway? Don't I need a driver?

---

