---
title: "how to unmute on alsamixer"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by nairod on 2007-04-13
It seems stupid to ask but by now anything goes...

I have no sound. It's a packard bell easynote, Ubuntu Edgy.

aplay -l results in

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC260 Digital [ALC260 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have uninstalled alsamixer and reinstalled as per the instructions on 
Comprehensive Sound Problem Solutions Guide v0.5e . 

Then I installed the most recent drivers.

I checked that the bios is not muted and could not figure anything because the bios setup does not refer to sound nor integrated peripherals.

So... as the installation and many threads refer to the sound channels being mutted I tried alsamixer and I get the information that the chip is Realtek ALC260. All channels are unmuted except I cannot alter IEC958 from OO. Should I? and how? To be honest I say they are unmutted but I am not sure, I don't think I know what I am talking about. Is there any place that explains how to alter the values on alsamixer? I absolutely don't get it.

Please help. No sound is unacceptable.

---

### Post by caffienefree on 2007-04-13
OO is unmuted. MM means muted. Is the volume itself raised?

---

### Post by nairod on 2007-04-13
as it stands the sound is

PCM - 100
Front - 81
Line - 69
Cd - 80
Mic - 75

and the IEC958 is on 00. I can change from MM to 00 but not raise the volume on this.

---

### Post by caffienefree on 2007-04-13
Try going step by step through this guide.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

EDIT: Wait, you already used that. Let me look around.

EDIT2: Try the guide with these drivers. [http://soundcard.free-driver-download.com/RealTek/17400/Realtek-ALC-ALC880-ALC260-ALC861-HD-Audio-CODECs-Driver-R1.0-Linux.html](http://soundcard.free-driver-download.com/RealTek/17400/Realtek-ALC-ALC880-ALC260-ALC861-HD-Audio-CODECs-Driver-R1.0-Linux.html)

---

### Post by nairod on 2007-04-13
no such file or directory... :( none of the download sites.

---

### Post by caffienefree on 2007-04-13
Oh. Try here.

[http://www.opendrivers.com/freedownload/217400/realtek-alc-alc880-alc260-alc861-hd-audio-codecs-driver-r1.0-linux-download.html](http://www.opendrivers.com/freedownload/217400/realtek-alc-alc880-alc260-alc861-hd-audio-codecs-driver-r1.0-linux-download.html)

---

### Post by nairod on 2007-04-14
I apologise, i feel I am being a pain... And I am very thankful for the help so far... still... I am as ignorant as can be so I need to ask ...

What am I doing? I downloaded the file... but I have no clue what to do with it. I checked the readme file... but I don't think whoever wrote that envisaged the level of ignorance of people like me. 

I assume I am supposed to install the drivers for the sound card so that would be the step where it's meant to say sudo modprobe snd- and the reference to the driver. 
Don't I need to declare where it is in my hard drive? How do I do that? I do I install these drivers and make alsa be aware of it. 

And by the way, why am I doing that? Should I not assume the drivers are installed? ok... this is just to learn, do I don't keep harassing and annoying everythime something silly happens... 

also... my computer... when told to lspci -v replies this:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Unknown device 1631:c017
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Unknown device 1631:c017
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at 4c280000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 70c0 [size=8]
        Memory at 30000000 (32-bit, prefetchable) [size=256M]
        Memory at 4c300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Unknown device 1631:c017
        Flags: bus master, fast devsel, latency 0
        Memory at 4c200000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Unknown device 1631:c017
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at 4c340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: 4b200000-4c1fffff
        Prefetchable memory behind bridge: 0000000044100000-0000000045000000
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: 4a100000-4b1fffff
        Prefetchable memory behind bridge: 0000000045100000-0000000046000000
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: 49100000-4a0fffff
        Prefetchable memory behind bridge: 0000000046100000-0000000047000000
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: 48100000-490fffff
        Prefetchable memory behind bridge: 0000000047100000-0000000048000000
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Unknown device 1631:c017
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at 7080 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Unknown device 1631:c017
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at 7060 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Unknown device 1631:c017
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at 7040 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Unknown device 1631:c017
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at 7020 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Unknown device 1631:c017
        Flags: bus master, medium devsel, latency 0, IRQ 169
        Memory at 4c344000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=06, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: 42000000-440fffff
        Prefetchable memory behind bridge: 0000000040000000-0000000041f00000
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Unknown device 1631:c017
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Unknown device 1631:c017
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 70a0 [size=16]

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Unknown device 1631:c017
        Flags: medium devsel, IRQ 11
        I/O ports at 7000 [size=32]

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1001
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at 4a100000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

05:02.0 FireWire (IEEE 1394): O2 Micro, Inc. Unknown device 00f7 (rev 02) (prog-if 10 [OHCI])
        Subsystem: Unknown device 1631:c017
        Flags: bus master, medium devsel, latency 64, IRQ 169
        Memory at 44003000 (32-bit, non-prefetchable) [size=4K]
        Memory at 44004000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

05:02.2 Class 0805: O2 Micro, Inc. Unknown device 7120 (rev 01)
        Subsystem: Unknown device 1631:c017
        Flags: slow devsel, IRQ 169
        Memory at 44004800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

05:02.3 Mass storage controller: O2 Micro, Inc. Unknown device 7130 (rev 01)
        Subsystem: Unknown device 1631:c017
        Flags: slow devsel, IRQ 11
        Memory at 44001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

05:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 02)
        Subsystem: Unknown device 1631:c017
        Flags: bus master, medium devsel, latency 64, IRQ 58
        Memory at 44000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 2200 [size=64]
        Capabilities: <access denied>


Very sorry for the silly level of ignorance. Also, if you have any sugestions of a good linux book that you recommend... because I bought Linux Bible... but it really is not helpful as a reference... and I will not go back to windows, I must figure this out... 

Thank you.

---

### Post by forrestcupp on 2007-04-14
I know this is a stupid question, but is it possible your speakers got unplugged from your computer or from the outlet?

---

### Post by nairod on 2007-04-16
:)  hehehe. A good question. It's a laptop. So I guess not, right? ... it worked fine in windows. thanks for asking though.

---

