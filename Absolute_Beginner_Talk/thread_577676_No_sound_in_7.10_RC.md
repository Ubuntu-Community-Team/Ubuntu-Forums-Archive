---
title: "No sound in 7.10 RC"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Mileeta on 2007-10-16
Well, I had sound this morning before I upgraded to Gutsy.  I've tried all the things that I did originally to make it work in Feisty, but to no avail.  Here's some code:

```
chris@chris-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M5455 [ALi M5455], device 0: Intel ICH [ALi M5455]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: M5455 [ALi M5455], device 2: Intel ICH - IEC958 [ALi M5455 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SBLive! Platinum [CT4760P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Live [SBLive! Platinum [CT4760P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SBLive! Platinum [CT4760P]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chris@chris-desktop:~$ lspci -v
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
        Subsystem: Giga-byte Technology Unknown device 5000
        Flags: bus master, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: ALi Corporation AGP8X Controller (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: e0000000-efffffff

00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fa000000-fbffffff
        Prefetchable memory behind bridge: a8000000-a80fffff

00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
        Subsystem: Giga-byte Technology Unknown device 5001
        Flags: bus master, medium devsel, latency 32

00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Giga-byte Technology Unknown device 5003
        Flags: medium devsel

00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
        Subsystem: Giga-byte Technology Unknown device ae01
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at d000 [size=256]
        Memory at fc000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7) (prog-if fa)
        Subsystem: Giga-byte Technology Unknown device 5002
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f000 [size=16]

00:0e.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10) (prog-if 8f)
        Subsystem: Giga-byte Technology Unknown device b003
        Flags: bus master, 66MHz, medium devsel, latency 128, IRQ 16
        I/O ports at d400 [size=8]
        I/O ports at d800 [size=4]
        I/O ports at dc00 [size=8]
        I/O ports at e000 [size=4]
        I/O ports at e400 [size=16]

00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
        Memory at fc001000 (32-bit, non-prefetchable) [size=4K]

00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        Memory at fc002000 (32-bit, non-prefetchable) [size=4K]

00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 20
        Memory at fc003000 (32-bit, non-prefetchable) [size=4K]

00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 48, IRQ 21
        Memory at fc004000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation NV38 [GeForce FX 5950 Ultra] (rev a1) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 01c6
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 22
        Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        [virtual] Expansion ROM at f9000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
        Subsystem: Creative Labs CT4760 SBLive!
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at c000 [size=32]
        Capabilities: <access denied>

02:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at c400 [size=8]
        Capabilities: <access denied>

02:07.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) (prog-if 10 [OHCI])
        Subsystem: Agere Systems FW323
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at fb001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

02:08.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Subsystem: ADMtek Unknown device 0574
        Flags: bus master, medium devsel, latency 64, IRQ 17
        I/O ports at c800 [size=256]
        Memory at fb000000 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at a8000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Giga-byte Technology GA-7VM400M/7VT600 Motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at cc00 [size=256]
        Memory at fb002000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

chris@chris-desktop:~$ 

```

Thanks!

---

### Post by mrtrick on 2007-10-16
[This thread]("http://ubuntuforums.org/showthread.php?t=539595&highlight=gutsy+still+no+sound") helped me get sound back with my SBLive card and my dell precision workstation. 

Since I wasn't working on a laptop with an intel card I removed that flag when configuring the driver. Also the only thing I needed to add to the alsa-base file was 'model=3stack'. 

I posted my particular steps on my blog [here]("http://mrtrick.org/"), but as I said, it basically follows the thread minus the latptop specific stuff.

---

### Post by Mileeta on 2007-10-16
Well, that didn't work.  I just installed the 1.0.15 alsa drivers, but to no avail.
Strangely, when I run alsa-mixer, it defaults to a realtek card, which I didn't even know that I had.

```


gedit /etc/modprobe.d/alsa-base

# autoloader aliases
install sound-slot-1 /sbin/modprobe snd-card-0
install sound-slot-0 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

I'm annoyed.  Sound worked with 7.04 :((

---

### Post by Mileeta on 2007-10-16
Oh, and I switched the first line in my autoloader aliases intentionally to try and force load the sound blaster instead of the ALiM5455, but that didn't work either.

Also, I double checked, and Realtek is the manufacturer for that ALiM5455 card.

---

### Post by Mileeta on 2007-10-17
bump before bedtime.  Thanks in advance!

---

### Post by ZeBadger on 2007-10-19
I've got exactly the same problem.  Working in 7.04... fresh install for 7.10.  No sound.  I've tried changing the device for the mixer, but it's not fixed it.

I've also got onboard sound which I'm pretty much sure is disabled in the BIOS.

---

### Post by ZeBadger on 2007-10-19
I've had this problem.  I've done two things.

1) Double clicked the sound icon on the top right to bring up the Volume Control and gone to  File-> Change Device -> selected "SB Live".

2) On the same application underneath "Master" there is a box that had a red X on it.  I unchecked it.  Why oh why?!

Working now!

---

### Post by merlin114 on 2007-10-20
I have a similar problem.  I have an SB-Live card that was working under 7.04, but I upgraded to 7.10 and have problems getting sound from web videos.  The SB-Live card is recognized and comes up in ALSA, and it looks like the EMU10K1 driver is loaded.  I set all the volumes up except a couple and I've got CD's playing okay, and also audio MP3 files I download.  But I still can't get sound on web videos such as Youtube, even when I unmute everything and put all the volumes up.  Any ideas?

---

