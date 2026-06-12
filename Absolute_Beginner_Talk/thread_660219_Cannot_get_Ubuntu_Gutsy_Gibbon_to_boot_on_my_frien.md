---
title: "Cannot get Ubuntu Gutsy Gibbon to boot on my friend's laptop."
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-01-06
My friend has a Gateway MX6426. The stats are as follows:

===========================================================

Processor: 	AMD Turion™ 64 Mobile Technology ML-40

Operates at: 2.2 GHz | 1 MB L2 Cache

HyperTransport™ technology at up to 1600 MHz

LCD Screen: 	15.4-inch Ultrabright™ WXGA TFT (1280 × 800)

Chipset: 	ATI RS482M

Memory: 	1024 MB 333 MHz DDR (2 × 512) Expandable to 2 GB

Total slots: 2 DDR slots | Available slots: 0 DDR slots

Video: 	ATI™ Radeon® Xpress 200M graphics. Up to 128 MB of shared video memory

Audio: 	AC 97 2.3 compliant 2-channel audio

Hard drive: 	80 GB 4200 RPM PATA hard drive

Optical drive: 	DVD+/-RW Multi-Format Double Layer (up to 8.5 GB)

Write maximum: 8X DVD +/-R, 6X DVD-RW, 8X DVD+RW, 2X DVD-R DL, 2.4X DVD+R DL, 24X CD-R and 16X CD-RW

Read maximum: 24X CD-R/RW/ROM, 8X DVD-R/RW/ROM, 4X DVD+/-R DL, RAM

Media reader: 	4-in-1 Digital Media Manager

Secure Digital™ (SD), Memory Stick®, Memory Stick-Pro®, and Multimedia Card™ (MMC)

Modem: 	56K ITU V.92 ready fax/modem

Network: 	Integrated 802.11b/g wireless LAN

Integrated 10/100 Ethernet

Interfaces:

    * 4 - USB 2.0 ports
    * 1 - VGA external connector
    * 1 - IEEE 1394 connector
    * 1 - RJ11
    * 1 - RJ45
    * 1 - Microphone In
    * 1 - Headphone / Audio Out
    * 1 - Kensington lock slot
    * 1 - AC adapter connector 

Pointing device: 	Integrated Synaptics touchpad with vertical scroll zone
PCMCIA 	1 - Type I or Type II; Card Bus

Battery : 	6-cell Lithium-ion

Dimensions: 	1.31 to 1.40-inches H × 14.09-inches W × 10.39-inches D
Weight 	6.32 pounds

========================================================================

The live CD boots, and we created a root directory, swap directory, and installed Ubuntu Gutsy.I should also mention that he has another partition that contains Windows XP Media Center edition. Then when we boot his computer it gets to where you choose which operating system you would like to boot. Just like it does on my computer (which is a Dell Latitude D520, stats aren't really important). After pressing enter on Ubuntu it does the whole "KERNAL ALIVE" thing and then.... nothing. A black screen that just hangs forever. I mean forever. I sat and waited a good half hour just to be sure. If anyone has some suggestions I would greatly appreciate them. I'm trying to really get this operating system down as I am a Network Communication Management major.

---

### Post by adam.tropics on 2008-01-06
If you hit say <ctrl><alt>F2, are you able to at least login? (I am thinking that since we have the same video card you may be suffering from the fact that sometimes, with the current free drivers, it doesn't play nice)

edit:Failing that, can you boot to the root prompt in recovery mode?

---

### Post by philinux on 2008-01-06
Sounds like a graphics card problem.

when grub come up hit esc. then chose recovery mode.

When the command promt comes up use

```
dpkg-reconfigure xserver-xorg
```

maybe choose vesa for the graphics initially.

Obviously the live cd booted ok? As you installed :confused:

---

### Post by whoscheesemine on 2008-01-06
Hmmm... being as the graphics looked fine when we booted the live CD I figured it wasn't a graphics problem, however, I did expect to hear a lot of feedback about the graphics being as I've heard about a ton of issues between ATI and Ubuntu. He had to run downtown for an interview and brought his laptop. When he gets back I'll try what you suggested. Thanks everyone, still taking suggestion by the way.

EDIT: I thought I should also mention that I am a complete and total noob when it comes to Ubuntu as I've only used Windows operating systems my whole life.

EDIT2: He still isn't back yet, but I haven't tried booting in the recovery mode. I'll try both when he gets back.

---

