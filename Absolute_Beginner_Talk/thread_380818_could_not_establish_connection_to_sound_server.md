---
title: "could not establish connection to sound server"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by mad vixen on 2007-03-10
Hi

I am a total newbie to linux/ubuntu/dapper the lot so pls bear with me if i have to ask for help in very basic idiot proof terms.

I ran a dual boot of ubuntu dapper and windows for a while on my main pc and over time and lots of research and help from a friend i got it working lovely.

so feeling brave yesterday, i completly wiped this pc (not my main one) of everything and started installing ubuntu dapper.

got the internet working lovely
got the geforce fx5500 gfx card working and accelerating

got cedega installed and working and guildwars running on it *felt very chuffed at this point

then suddenly realised i hadnt turned the speakers on, so i did and nada no sound came from them.

my first check was to the volume icon that is in the top right of the screen, resulting in a box appearing and telling me this :-  The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu

so off i goes into the synaptic package manager to look up GStreamer plugins, well as im on a learning curve and nothing but many hours of hard work to loose i installed various plugins result: = no change

hmm, so i then starts to google the problem, finding many references to having no sound, and instructions on what to do, but all the ones im finding are refering to sound cards and not onboard mother board sound.

now here is where you gonna say, so what mother board is it - to be totally honest i have no idea, as atm i cant find the books that came with it and i cant remember

*keeps fingers crossed there is a typable sentance that will enlighten me

anyway, i have tried various things 

listed in no particular order:

tail -2 /proc/asound/oss/sndstat

tail: cannot open `/proc/asound/oss/sndstat' for reading: No such file or directory


lspci -v

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
        Subsystem: VIA Technologies, Inc.: Unknown device 0000
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: dde00000-dfefffff
        Prefetchable memory behind bridge: bdd00000-ddcfffff
        Capabilities: <available only to root>

0000:00:08.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at d400 [size=64]
        Expansion ROM at dffe0000 [disabled] [size=64K]

0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 5901
        Flags: bus master, medium devsel, latency 32, IRQ 169
        I/O ports at ec00 [size=8]
        I/O ports at e800 [size=4]
        I/O ports at e400 [size=8]
        I/O ports at e000 [size=4]
        I/O ports at dc00 [size=16]
        I/O ports at d800 [size=256]
        Capabilities: <available only to root>

0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 5901
        Flags: bus master, medium devsel, latency 32, IRQ 169
        I/O ports at fc00 [size=16]
        Capabilities: <available only to root>

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]        Subsystem: VIA Technologies, Inc.: Unknown device 0000
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 185
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Expansion ROM at dfee0000 [disabled] [size=128K]
        Capabilities: <available only to root>


 sudo lspci -v
Password:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
        Subsystem: VIA Technologies, Inc.: Unknown device 0000
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: [80] AGP version 3.5
        Capabilities: [c0] Power Management version 2

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: dde00000-dfefffff
        Prefetchable memory behind bridge: bdd00000-ddcfffff
        Capabilities: [80] Power Management version 2

0000:00:08.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at d400 [size=64]
        Expansion ROM at dffe0000 [disabled] [size=64K]

0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 5901
        Flags: bus master, medium devsel, latency 32, IRQ 169
        I/O ports at ec00 [size=8]
        I/O ports at e800 [size=4]
        I/O ports at e400 [size=8]
        I/O ports at e000 [size=4]
        I/O ports at dc00 [size=16]
        I/O ports at d800 [size=256]
        Capabilities: [c0] Power Management version 2

0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 5901
        Flags: bus master, medium devsel, latency 32, IRQ 169
        I/O ports at fc00 [size=16]
        Capabilities: [c0] Power Management version 2

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]        Subsystem: VIA Technologies, Inc.: Unknown device 0000
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: [c0] Power Management version 2

0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 185
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Expansion ROM at dfee0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 3.0

aplay -l

aplay: device_list:221: no soundcards found...



sorry if this has been a long winded post but ive tried to put as much information in as i can, no doubt to help more information will be required, if you can tell me how to get the information, then i can get it.


many many thanks

mv.


p.s. i tried putting an audio cd in the drive, clicking on its icon on the desktop opened sound juicer, i clicked on the play button and got this :-

Error playing CD.

Reason: Could not establish connection to sound server

---

### Post by Delvien on 2007-03-10
Wow thats a lengthy post, I appluad you for being so detailed.

As far as the sound goes, make sure sound works at all after  a new reboot.

I experienced nothing but problems with Cedega..

Make sure when running cedega NO OTHER APPS are open, linux has a problem acessing sound from more than one app at the same time. IMO WINE works much better for sound.

---

### Post by mad vixen on 2007-03-10
I'm not getting any sounds of any kind at all, from any application

as far as i can tell ubuntu is not recognising that the motherboard has on board sound and is therefore telling me no sound device is present.

im considering, doing another complete wipe and install to see then if i get any sounds or just buying a sound card that is linux/ubuntu friendly

so far this seems to be the only major problem that im having :(

hoping for a positive outcome tho :D

---

