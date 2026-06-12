---
title: "No sound anymore, spontaneously"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by gpaciga on 2006-11-29
I'm using Dapper with KDE. My sound worked fine for a few weeks but now nothing makes so much as a peep. I was using the computer when things stopped but wasn't installing packages or anything, just playing some movies with mplayer. Something similar happened before, but restarting the sound server (/etc/init.d/alsa-utils restart) had fixed it. I've tried that, as well as restarting the computer, and made sure that nothing was muted accidentally as far as I can tell. I'm at a loss now.

Since people always seem to ask for them on posts like these, here's some output from lspci to show that my sound card is there:

```
0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 01)
0000:02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
0000:02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
0000:02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller

```

and from amixer to check the levels:

```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 27 [87%] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 29 [94%] [on]
  Front Right: Playback 29 [94%] [on]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'AC-Link' 'A/D Converter'
  Item0: 'AC-Link'
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mic'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [on]
  Front Right: Capture 0 [0%] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

```

---

### Post by black hole sun on 2006-11-29
Well your sound might be muted. 

Run in a terminal,

alsamixer

---

### Post by gpaciga on 2006-11-29
> **black hole sun said:**
> Well your sound might be muted. 

Run in a terminal,

alsamixer

Yes, I've already done that to check that things aren't muted. In fact in alsamixer I can mute things and a little "mute" light on my keyboard turns on, but this is not the problem.

---

### Post by Ben Sprinkle on 2006-11-29
MP3 or WAV or.......?

---

### Post by gpaciga on 2006-11-29
> MP3 or WAV or.......?

Everything. mp3, wav, ogg, sound from any movies, not even so much as a system bell.

---

### Post by gpaciga on 2006-11-30
Someone suggested that I try running alsaconf, but that program doesn't exist on my computer. Since this is apparently strange I was told to try reinstalling alsa-base, however when doing this apt-get wants to uninstall ubuntu-base and ubuntu-minimal as well. Can this be safely done?

---

### Post by Ben Sprinkle on 2006-11-30
For mp3, install libmp3-mad and libmp3-ugly. It will fix your mp3 issues.

---

### Post by gpaciga on 2006-11-30
I don't have MP3 issues. I have all the libraries and codecs required to whatever sound formats I want. Sound had worked fine for two or three weeks. The sound card is still recognized, there are no errors when I try to play something, just nothing comes out of the speakers *as if* it was on mute (but it *is not* muted).

---

### Post by deadgobby on 2006-11-30
MMMM, that is odd. just a simple question. Do you have a sound card?

---

### Post by gpaciga on 2006-11-30
Yes, of course. Like I said, sound worked fine for weeks. My sound card couldn't have spontaneously disintegrated. I can't see how it can be a hardware probablem at all since it's still being recognized by the system and there are no 'no sound card' type errors.

---

### Post by deadgobby on 2006-11-30
When I was running Dapper on a old HD. My sound card work fine for months. Then all of the sudden. The sound was gone. I made sure that the BIOS setting was correct and all that jazz. I cannot put my thumb on it. It seem to happen after a update. I use Sound Blaster Live card. When I got a new HD and installed Dapper on it. Sound was there and proceeded to upgrade to Eft on the new HD. I not saying to reinstall Dapper, but trace your steps and think of what you have done to the puter before all sound was lost.

---

### Post by gpaciga on 2006-11-30
That's just the thing, I can't figure out what it might have been. I would glady uninstall whatever package was casuing a conflict, if that was the case. What I had been doing was surfing around on Firefox, and playing a series of short mpg movies in mplayer. One movie ended, and when I played the next one, it was without sound. I could imagine that there might have been some glitch in playing a movie that would make the sound server hang or something, but I would have expected restarting to fix it.

I want to reinstall alsa-base etc, but ubuntu-base and ubuntu-minimal would be uninstalled along with it. Can I actually do that? Or does that amount to reinstalling the whole OS?

---

### Post by Ben Sprinkle on 2006-11-30
Hmm, reinstall all your players, codecs, drivers etc. before you do the whole system.

---

### Post by black hole sun on 2006-11-30
That is so weird. Post your dmesg here, you will.

---

### Post by PriceChild on 2006-11-30
Firstly I advise you to pop a live cd in to see if that works for you....

I remember the same happening to me, eventually I figured out that the new tv card i had just installed was now selected as the default output for all sound.

A quick trip to System>Preferences>Sound and a change at the bottom and all was fine.

Pricey

---

### Post by gpaciga on 2006-11-30
I booted up in my windows partition and as greeting with a nice loud startup sound, having left my speaker volume at maximum from trying to listen for any hint of noise from Ubuntu :shock:

Ubuntu has a similar startup noise as well that, of course, can not be heard anymore. That seems to imply that the problem is more fundamental than what program I choose as a player... Is there a way at least of getting a chronological list of packages installed so I can try rolling back in the hopes that if it is some kind of software conflict I'll remove whatever package is causing it.

I thought I'd show that Ubuntu seems to believe sound is working perfectly. Here's some mplayer output, which clearly shows it accessing the sound card and loading the required codecs without issue:

```
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Banias (Family: 6, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Playing ubuntu Sax.ogg.
[Ogg] stream 0: audio (Vorbis), -aid 0
Ogg file format detected.
================================================================
Opening audio decoder: [libvorbis] Ogg/Vorbis audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 160.0 kbit/11.34% (ratio: 20000->176400)
Selected audio codec: [vorbis] afm: libvorbis (OggVorbis Audio Decoder)
================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/60208 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Video: no video
Starting playback...
A:  10.2 (10.2) of 26.0 (25.9)  3.3%


```

And for black hole sun, my dmesg:

```
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001ffd0000 (usable)
[4294667.296000]  BIOS-e820: 000000001ffd0000 - 000000001fff0c00 (reserved)
[4294667.296000]  BIOS-e820: 000000001fff0c00 - 000000001fffc000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001fffc000 - 0000000020000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 511MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 131024
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126928 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 COMPAQ                                ) @ 0x000f6350
[4294667.296000] ACPI: RSDT (v001 HP     CPQ0860  0x30090320 CPQ  0x00000001) @ 0x1fff0c84
[4294667.296000] ACPI: FADT (v002 HP     CPQ0860  0x00000002 CPQ  0x00000001) @ 0x1fff0c00
[4294667.296000] ACPI: SSDT (v001 COMPAQ  CPQGysr 0x00001001 MSFT 0x0100000e) @ 0x1fff5bd7
[4294667.296000] ACPI: DSDT (v001 HP       nx7000 0x00010000 MSFT 0x0100000e) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:e0000000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda2 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01401000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1395.545 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294669.093000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294669.094000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.111000] Memory: 508724k/524096k available (1976k kernel code, 14792k reserved, 606k data, 288k init, 0k highmem)
[4294669.111000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294669.171000] Calibrating delay using timer specific routine.. 2792.51 BogoMIPS (lpj=1396257)
[4294669.171000] Security Framework v1.0.0 initialized
[4294669.171000] SELinux:  Disabled at boot.
[4294669.171000] Mount-cache hash table entries: 512
[4294669.171000] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[4294669.171000] CPU: After vendor identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[4294669.171000] CPU: L1 I cache: 32K, L1 D cache: 32K
[4294669.171000] CPU: L2 cache: 1024K
[4294669.171000] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00000040 00000180 00000000 00000000
[4294669.171000] mtrr: v2.0 (20020519)
[4294669.171000] CPU: Intel(R) Pentium(R) M processor 1400MHz stepping 05
[4294669.171000] Enabling fast FPU save and restore... done.
[4294669.171000] Enabling unmasked SIMD FPU exception support... done.
[4294669.171000] Checking 'hlt' instruction... OK.
[4294669.175000] checking if image is initramfs... it is
[4294670.235000] Freeing initrd memory: 6606k freed
[4294670.248000] ACPI: Looking for DSDT ... not found!
[4294670.251000] ACPI: setting ELCR to 0200 (from 0c20)
[4294670.313000] NET: Registered protocol family 16
[4294670.313000] EISA bus registered
[4294670.313000] ACPI: bus type pci registered
[4294670.314000] PCI: PCI BIOS revision 2.10 entry at 0xf031f, last bus=3
[4294670.314000] PCI: Using configuration type 1
[4294670.314000] ACPI: Subsystem revision 20051216
[4294670.323000] ACPI: Interpreter enabled
[4294670.323000] ACPI: Using PIC for interrupt routing
[4294670.323000] ACPI: PCI Root Bridge [C046] (0000:00)
[4294670.323000] PCI: Probing PCI hardware (bus 00)
[4294670.323000] ACPI: Assume root bridge [\_SB_.C046] bus is 0
[4294670.331000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[4294670.331000] PCI quirk: region 1100-113f claimed by ICH4 GPIO
[4294670.331000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294670.331000] Boot video device is 0000:01:00.0
[4294670.331000] PCI: Transparent bridge - 0000:00:1e.0
[4294670.331000] ACPI: PCI Interrupt Routing Table [\_SB_.C046._PRT]
[4294670.344000] ACPI: PCI Interrupt Routing Table [\_SB_.C046.C047._PRT]
[4294670.344000] ACPI: PCI Interrupt Routing Table [\_SB_.C046.C058._PRT]
[4294670.345000] ACPI: Embedded Controller [C0EA] (gpe 28) interrupt mode.
[4294670.367000] ACPI: Power Resource [C18D] (on)
[4294670.368000] ACPI: Power Resource [C195] (on)
[4294670.369000] ACPI: Power Resource [C19C] (on)
[4294670.369000] ACPI: Power Resource [C1A6] (on)
[4294670.370000] ACPI: PCI Interrupt Link [C0C2] (IRQs 5 *10)
[4294670.371000] ACPI: PCI Interrupt Link [C0C3] (IRQs 5 *10)
[4294670.371000] ACPI: PCI Interrupt Link [C0C4] (IRQs *5 10)
[4294670.372000] ACPI: PCI Interrupt Link [C0C5] (IRQs *5 10)
[4294670.372000] ACPI: PCI Interrupt Link [C0C6] (IRQs 5 10) *0, disabled.
[4294670.373000] ACPI: PCI Interrupt Link [C0C7] (IRQs 5 10) *11
[4294670.373000] ACPI: PCI Interrupt Link [C0C8] (IRQs 5 10) *0, disabled.
[4294670.374000] ACPI: PCI Interrupt Link [C0C9] (IRQs *5 10)
[4294670.375000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.375000] pnp: PnP ACPI init
[4294670.382000] pnp: PnP ACPI: found 15 devices
[4294670.382000] PnPBIOS: Disabled by ACPI PNP
[4294670.382000] PCI: Using ACPI for IRQ routing
[4294670.382000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.441000] pnp: 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[4294670.441000] pnp: 00:0d: ioport range 0x1000-0x107f could not be reserved
[4294670.441000] pnp: 00:0d: ioport range 0x1100-0x113f has been reserved
[4294670.441000] pnp: 00:0d: ioport range 0x1200-0x121f has been reserved
[4294670.441000] PCI: Bridge: 0000:00:01.0
[4294670.441000]   IO window: 3000-3fff
[4294670.441000]   MEM window: 90400000-904fffff
[4294670.441000]   PREFETCH window: 98000000-9fffffff
[4294670.441000] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[4294670.441000]   IO window: 00002800-000028ff
[4294670.441000]   IO window: 00002c00-00002cff
[4294670.441000]   PREFETCH window: 30000000-31ffffff
[4294670.441000]   MEM window: 34000000-35ffffff
[4294670.441000] PCI: Bridge: 0000:00:1e.0
[4294670.441000]   IO window: 2000-2fff
[4294670.441000]   MEM window: 90000000-903fffff
[4294670.441000]   PREFETCH window: 30000000-31ffffff
[4294670.441000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294670.441000] **** SET: Misaligned resource pointer: dfe985c2 Type 07 Len 0
[4294670.441000] ACPI: PCI Interrupt Link [C0C4] enabled at IRQ 5
[4294670.441000] PCI: setting IRQ 5 as level-triggered
[4294670.441000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [C0C4] -> GSI 5 (level, low) -> IRQ 5
[4294670.442000] audit: initializing netlink socket (disabled)
[4294670.442000] audit(1164893938.441:1): initialized
[4294670.442000] VFS: Disk quotas dquot_6.5.1
[4294670.442000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.442000] Initializing Cryptographic API
[4294670.442000] io scheduler noop registered
[4294670.442000] io scheduler anticipatory registered
[4294670.442000] io scheduler deadline registered
[4294670.442000] io scheduler cfq registered
[4294670.442000] isapnp: Scanning for PnP cards...
[4294670.799000] isapnp: No Plug & Play device found
[4294670.814000] PNP: PS/2 Controller [PNP0303:C1A3,PNP0f13:C1A4] at 0x60,0x64 irq 1,12
[4294670.822000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294670.827000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294670.827000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294670.832000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294670.833000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294670.834000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.834000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294670.834000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.834000] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[4294670.836000] 00:03: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.836000] **** SET: Misaligned resource pointer: dfc671c2 Type 07 Len 0
[4294670.837000] ACPI: PCI Interrupt Link [C0C3] enabled at IRQ 10
[4294670.837000] PCI: setting IRQ 10 as level-triggered
[4294670.837000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [C0C3] -> GSI 10 (level, low) -> IRQ 10
[4294670.837000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[4294670.837000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.837000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.837000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.837000] mice: PS/2 mouse device common for all mice
[4294670.838000] EISA: Probing bus 0 at eisa.0
[4294670.838000] Cannot allocate resource for EISA slot 1
[4294670.838000] Cannot allocate resource for EISA slot 2
[4294670.838000] Cannot allocate resource for EISA slot 3
[4294670.838000] Cannot allocate resource for EISA slot 4
[4294670.838000] EISA: Detected 0 cards.
[4294670.839000] NET: Registered protocol family 2
[4294670.849000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[4294670.849000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.850000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.850000] TCP: Hash tables configured (established 32768 bind 32768)
[4294670.850000] TCP reno registered
[4294670.850000] TCP bic registered
[4294670.850000] NET: Registered protocol family 1
[4294670.850000] NET: Registered protocol family 8
[4294670.850000] NET: Registered protocol family 20
[4294670.850000] Using IPI Shortcut mode
[4294670.850000] ACPI wakeup devices: 
[4294670.850000] C058 C1AD C1A3 C1A4 C0AC C0B3 C0B4 C0B5 C0E7 C136 
[4294670.850000] ACPI: (supports S0 S3 S4 S5)
[4294670.850000] Freeing unused kernel memory: 288k freed
[4294670.879000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294670.903000] vga16fb: initializing
[4294670.903000] vga16fb: mapped to 0xc00a0000
[4294671.019000] Console: switching to colour frame buffer device 80x25
[4294671.019000] fb0: VGA16 VGA frame buffer device
[4294672.163000] Capability LSM initialized
[4294672.196000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294672.196000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294672.648000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294672.648000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294672.648000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [C0C4] -> GSI 5 (level, low) -> IRQ 5
[4294672.648000] ICH4: chipset revision 1
[4294672.648000] ICH4: not 100% native mode: will probe irqs later
[4294672.648000]     ide0: BM-DMA at 0x4c40-0x4c47, BIOS settings: hda:DMA, hdb:pio
[4294672.648000]     ide1: BM-DMA at 0x4c48-0x4c4f, BIOS settings: hdc:DMA, hdd:pio
[4294672.648000] Probing IDE interface ide0...
[4294672.912000] hda: TOSHIBA MK8032GAX, ATA DISK drive
[4294673.524000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.549000] Probing IDE interface ide1...
[4294674.221000] hdc: DW-224E, ATAPI CD/DVD-ROM drive
[4294674.835000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.843000] hda: max request size: 1024KiB
[4294674.852000] hda: 156301488 sectors (80026 MB), CHS=16383/255/63, UDMA(100)
[4294674.852000] hda: cache flushes supported
[4294674.852000]  hda: hda1 hda2 hda3 hda4
[4294674.905000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 1658kB Cache, DMA
[4294674.905000] Uniform CD-ROM driver Revision: 3.20
[4294675.361000] usbcore: registered new driver usbfs
[4294675.361000] usbcore: registered new driver hub
[4294675.363000] USB Universal Host Controller Interface driver v2.3
[4294675.363000] **** SET: Misaligned resource pointer: dfd10502 Type 07 Len 0
[4294675.364000] ACPI: PCI Interrupt Link [C0C2] enabled at IRQ 10
[4294675.364000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [C0C2] -> GSI 10 (level, low) -> IRQ 10
[4294675.364000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294675.364000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294675.364000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294675.364000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000048c0
[4294675.364000] hub 1-0:1.0: USB hub found
[4294675.364000] hub 1-0:1.0: 2 ports detected
[4294675.438000] ieee1394: Initialized config rom entry `ip1394'
[4294675.465000] **** SET: Misaligned resource pointer: de827ec2 Type 07 Len 0
[4294675.465000] ACPI: PCI Interrupt Link [C0C5] enabled at IRQ 5
[4294675.465000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [C0C5] -> GSI 5 (level, low) -> IRQ 5
[4294675.465000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294675.465000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294675.465000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294675.465000] uhci_hcd 0000:00:1d.1: irq 5, io base 0x000048e0
[4294675.466000] hub 2-0:1.0: USB hub found
[4294675.466000] hub 2-0:1.0: 2 ports detected
[4294675.567000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [C0C4] -> GSI 5 (level, low) -> IRQ 5
[4294675.567000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294675.567000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294675.567000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294675.567000] uhci_hcd 0000:00:1d.2: irq 5, io base 0x00004c00
[4294675.567000] hub 3-0:1.0: USB hub found
[4294675.567000] hub 3-0:1.0: 2 ports detected
[4294675.669000] **** SET: Misaligned resource pointer: de8278c2 Type 07 Len 0
[4294675.670000] ACPI: PCI Interrupt Link [C0C9] enabled at IRQ 5
[4294675.670000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [C0C9] -> GSI 5 (level, low) -> IRQ 5
[4294675.670000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.670000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294675.670000] ehci_hcd 0000:00:1d.7: debug port 1
[4294675.670000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294675.670000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294675.670000] ehci_hcd 0000:00:1d.7: irq 5, io mem 0xa0000000
[4294675.671000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[4294675.674000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294675.674000] hub 4-0:1.0: USB hub found
[4294675.674000] hub 4-0:1.0: 6 ports detected
[4294675.775000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294675.775000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [C0C2] -> GSI 10 (level, low) -> IRQ 10
[4294675.829000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[90200000-902007ff]  Max Packet=[1024]
[4294675.931000] Attempting manual resume
[4294675.946000] kjournald starting.  Commit interval 5 seconds
[4294675.946000] EXT3-fs: mounted filesystem with ordered data mode.
[4294676.193000] usb 4-5: new high speed USB device using ehci_hcd and address 3
[4294676.515000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[4294677.106000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f3638003783]
[4294686.829000] Linux agpgart interface v0.101 (c) Dave Jones
[4294686.834000] agpgart: Detected an Intel 855PM Chipset.
[4294686.847000] agpgart: AGP aperture is 256M @ 0xb0000000
[4294686.858000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294686.862000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294687.510000] hw_random hardware driver 1.0.0 loaded
[4294687.514000] Real Time Clock Driver v1.12
[4294687.786000] input: PC Speaker as /class/input/input1
[4294688.263000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0C3] -> GSI 10 (level, low) -> IRQ 10
[4294688.263000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294688.297000] wbsd: Winbond W83L51xD SD/MMC card interface driver, 1.5
[4294688.297000] wbsd: Copyright(c) Pierre Ossman
[4294688.298000] **** SET: Misaligned resource pointer: dc366e42 Type 00 Len 42
[4294688.298000] **** SET: Misaligned resource pointer: dc366ec6 Type 07 Len 0
[4294688.298000] pnp: Device 00:01 activated.
[4294688.303000] mmc0: W83L51xD id 7112 at 0x248 irq 6 dma 2 PnP
[4294688.306000] parport: PnPBIOS parport detected.
[4294688.306000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294688.343000] 8139too Fast Ethernet driver 0.9.27
[4294688.563000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x2348b3, caps: 0x904713/0x10008
[4294688.618000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[4294688.653000] usbcore: registered new driver hiddev
[4294688.682000] input: Microsoft Microsoft Wheel Mouse Optical as /class/input/input3
[4294688.682000] input: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical] on usb-0000:00:1d.0-1
[4294688.682000] usbcore: registered new driver usbhid
[4294688.683000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294688.691000] SCSI subsystem initialized
[4294688.711000] Initializing USB Mass Storage driver...
[4294688.711000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294688.712000] usb-storage: device found at 3
[4294688.712000] usb-storage: waiting for device to settle before scanning
[4294688.712000] usbcore: registered new driver usb-storage
[4294688.712000] USB Mass Storage support registered.
[4294688.717000] ieee80211_crypt: registered algorithm 'NULL'
[4294688.729000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4294688.729000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294688.758000] ts: Compaq touchscreen protocol output
[4294688.920000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.4
[4294688.920000] ipw2100: Copyright(c) 2003-2005 Intel Corporation
[4294689.076000] intel8x0_measure_ac97_clock: measured 50394 usecs
[4294689.076000] intel8x0: clocking to 48000
[4294689.081000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [C0C4] -> GSI 5 (level, low) -> IRQ 5
[4294689.081000] Yenta: CardBus bridge found at 0000:02:04.0 [0e11:0860]
[4294689.081000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294689.081000] Yenta: Routing CardBus interrupts to PCI
[4294689.081000] Yenta TI: socket 0000:02:04.0, mfunc 0x001c1132, devctl 0x44
[4294689.081000] 8139too: pci dev 0000:02:01.0 (id 10ec:8139 rev 20) is an enhanced 8139C+ chip
[4294689.081000] 8139too: Use the "8139cp" driver for improved performance and stability.
[4294689.081000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [C0C3] -> GSI 10 (level, low) -> IRQ 10
[4294689.081000] 8139too: 0000:02:01.0: unknown chip version, assuming RTL-8139
[4294689.081000] 8139too: 0000:02:01.0: TxConfig = 0x74800000
[4294689.081000] eth0: RealTek RTL8139 at 0xe0aa0000, 00:02:3f:63:6c:6f, IRQ 10
[4294689.081000] eth0:  Identified 8139 chip type 'RTL-8139'
[4294689.081000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [C0C5] -> GSI 5 (level, low) -> IRQ 5
[4294689.082000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[4294689.304000] Yenta: ISA IRQ mask 0x0818, PCI irq 5
[4294689.304000] Socket status: 30000006
[4294689.304000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[4294689.304000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[4294689.304000] cs: IO port probe 0x2000-0x2fff: clean.
[4294689.304000] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x903fffff
[4294689.304000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[4294689.329000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294689.738000] eth1: Radio is disabled by RF switch.
[4294689.908000] cs: IO port probe 0x100-0x3af: excluding 0x140-0x14f 0x200-0x20f
[4294689.910000] cs: IO port probe 0x3e0-0x4ff: clean.
[4294689.911000] cs: IO port probe 0x820-0x8ff: clean.
[4294689.911000] cs: IO port probe 0xc00-0xcf7: clean.
[4294689.912000] cs: IO port probe 0xa00-0xaff: clean.
[4294690.359000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294690.461000] lp0: using parport0 (interrupt-driven).
[4294690.496000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294690.496000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[4294690.496000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294690.558000] Adding 2096472k swap on /dev/hda3.  Priority:-1 extents:1 across:2096472k
[4294690.722000] EXT3 FS on hda2, internal journal
[4294690.886000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294690.886000] md: bitmap version 4.39
[4294691.546000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294691.593000] NET: Registered protocol family 17
[4294692.238000] cdrom: open failed.
[4294693.714000]   Vendor: ST325082  Model: 4A                Rev: 0000
[4294693.714000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294693.716000] usb-storage: device scan complete
[4294693.773000] Driver 'sd' needs updating - please use bus_type methods
[4294693.774000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[4294693.774000] sda: assuming drive cache: write through
[4294693.777000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[4294693.777000] sda: assuming drive cache: write through
[4294693.777000]  sda: sda1
[4294693.781000] sd 0:0:0:0: Attached scsi disk sda
[4294693.792000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294698.726000] NET: Registered protocol family 10
[4294698.726000] lo: Disabled Privacy Extensions
[4294698.727000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[4294698.727000] IPv6 over IPv4 tunneling driver
[4294704.359000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294704.418000] NTFS volume version 3.1.
[4294709.561000] eth0: no IPv6 routers present
[4294709.981000] ACPI: AC Adapter [C134] (on-line)
[4294710.052000] ACPI: Battery Slot [C11F] (battery present)
[4294710.115000] ACPI: Power Button (FF) [PWRF]
[4294710.115000] ACPI: Power Button (CM) [C1BE]
[4294710.115000] ACPI: Lid Switch [C136]
[4294710.218000] ibm_acpi: ec object not found
[4294710.241000] pcc_acpi: loading...
[4294710.329000] ACPI: Video Device [C0D0] (multi-head: yes  rom: no  post: no)
[4294712.547000] ppdev: user-space parallel port driver
[4294712.933000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294712.933000] apm: overridden by ACPI.
[4294716.789000] Bluetooth: Core ver 2.8
[4294716.789000] NET: Registered protocol family 31
[4294716.789000] Bluetooth: HCI device and connection manager initialized
[4294716.789000] Bluetooth: HCI socket layer initialized
[4294716.819000] Bluetooth: L2CAP ver 2.8
[4294716.819000] Bluetooth: L2CAP socket layer initialized
[4294716.840000] Bluetooth: RFCOMM socket layer initialized
[4294716.840000] Bluetooth: RFCOMM TTY layer initialized
[4294716.840000] Bluetooth: RFCOMM ver 1.7
[4294718.478000] ip_tables: (C) 2000-2002 Netfilter core team
[4294718.738000] Netfilter messages via NETLINK v0.30.
[4294718.761000] ip_conntrack version 2.4 (4094 buckets, 32752 max) - 232 bytes per conntrack
[4294719.458000] [drm] Initialized drm 1.0.1 20051102
[4294719.469000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [C0C2] -> GSI 10 (level, low) -> IRQ 10
[4294719.470000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[4294720.746000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294720.746000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[4294720.746000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[4294720.992000] [drm] Setting GART location based on new memory map
[4294720.992000] [drm] Loading R200 Microcode
[4294720.992000] [drm] writeback test succeeded in 2 usecs
[4294753.222000] KMF: IN=eth0 OUT= MAC=00:02:3f:63:6c:6f:00:40:05:31:01:17:08:00 SRC=24.201.245.77 DST=192.168.0.142 LEN=183 TOS=0x00 PREC=0x00 TTL=58 ID=7621 DF PROTO=UDP SPT=53 DPT=32768 LEN=163 
[4294758.223000] KMF: IN=eth0 OUT= MAC=00:02:3f:63:6c:6f:00:40:05:31:01:17:08:00 SRC=24.201.245.77 DST=192.168.0.142 LEN=183 TOS=0x00 PREC=0x00 TTL=58 ID=10511 DF PROTO=UDP SPT=53 DPT=32768 LEN=163 

```

---

### Post by gpaciga on 2006-12-01
To update:
I've reinstalled the media players but with no luck.

I also reinstalled alsa-utils and alss-base with apt-get --purge -remove. (This also meant reinstalling ubuntu-base and ubuntu-minimal, but my system didn't seem to mind.) At first I didn't think it had any affect, still not being able to hear anything, but a few minutes later I was surfing around in the internet and some video clip started playing sound.

Though I still don't know why it happened, or how exactly I fixed it, it seems like my problem is solved.

---

### Post by Yuzem on 2006-12-02
I have a the same problem but it isn't permanent. Some times i boot and there is no sound (aplay -l gives me nothing) and some times everything works perfect.
Im using Edgy.
Any idea?

---

### Post by gpaciga on 2006-12-02
Once before it happened to me but restarting the sound server fixed it. 
sudo /etc/init.d/alsa-utils restart

But I don't know what caused it or how to fix it.

---

### Post by FastZ on 2006-12-03
I had a similar thing happen to me the other day on my computer, I run Edgy.  I was just casually surfing the internet and all of a sudden I had no sound whatsoever, not even a single system sound.  When I read PriceChild's post about how he had to go into System>Preferences>Sound and change the default sound output I went looking at my configuration and whadaya know!  Some weird setting was in there that was not my sound card so I changed that back to set my sound card as the output device and all works fine now.  I am like you, gpaciga, I have no idea what caused the problem.

---

### Post by gpaciga on 2006-12-03
The System>Preferences>Sound trick doesn't work for me though, I think since I'm using KDE and have no such thing. What I think is the equivalent, Settings>Sound & Multimedia>Sound System, didn't have anything illuminating for me.

---

### Post by Yuzem on 2006-12-03
> **gpaciga said:**
> Once before it happened to me but restarting the sound server fixed it. 
sudo /etc/init.d/alsa-utils restart

But I don't know what caused it or how to fix it.

Didn't work for me. Today i have sound but i dont know what will be the next boot... it is a random thing.

---

### Post by KA01 on 2006-12-03
i had the same, when i installed gstreamer xtra plugins.
and i did this:
sudo /etc/init.d/alsa-utils reset

and sound is working

---

