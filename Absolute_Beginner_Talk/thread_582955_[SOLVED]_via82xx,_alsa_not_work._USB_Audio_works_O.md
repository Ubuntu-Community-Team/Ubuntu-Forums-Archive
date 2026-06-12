---
title: "[SOLVED] via82xx, alsa not work. USB Audio works ONLY for totem, no login/logout snds"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by offline on 2007-10-20
FEISTY: can only hear sound with totem. Nothing else(no xine etc), even when either loging in/out there is no sound although these sounds are enabled(and I tested them from sound pregerences).

I used aplay -l, lspci -v | less, amixer | less and sudo asoundconf list and am presenting the output below.

I hear the above when "USB Audio" is enabled in "sound preferences" and NOTHING else will have a sound. I enabled all alsamixer options from the sound controller>edit but again nothing.

Can you help(I am not experienced in these)

~$ aplay -l


```
**** List of PLAYBACK Hardware Devices ****
card 0: rev50 [VIA 82C686A/B rev50], device 0: VIA 82C686A/B rev50 [VIA 82C686A/B rev50]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [YAMAHA YST-M45D USB Speaker  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v | less


```
0:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
        Subsystem: Elitegroup Computer Systems Unknown device 0a30
        Flags: bus master, medium devsel, latency 8
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: dc000000-ddffffff
        Prefetchable memory behind bridge: d0000000-d7ffffff
        Capabilities: <access denied>

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
        Subsystem: Elitegroup Computer Systems Unknown device 0a30
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [M
aster SecP PriP])
        Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at c000 [size=16]
        Capabilities: <access denied>

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at c400 [size=32]
        Capabilities: <access denied>

00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller

0:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at c800 [size=32]
        Capabilities: <access denied>

00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
        Subsystem: Elitegroup Computer Systems Unknown device 0a30
        Flags: medium devsel, IRQ 11
        Capabilities: <access denied>

00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
        Subsystem: Elitegroup Computer Systems Unknown device 0a30
        Flags: medium devsel, IRQ 11
        I/O ports at cc00 [size=256]
        I/O ports at d000 [size=4]
        I/O ports at d400 [size=4]
        Capabilities: <access denied>

00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at dc00 [size=256]
        Memory at df000000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 40000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:0c.0 Communication controller: Motorola Wildcard X100P
        Subsystem: Motorola Unknown device 0000
        Flags: bus master, medium devsel, latency 32, IRQ 9
        I/O ports at e000 [size=256]
        Memory at df001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0d.0 Multimedia audio controller: Fortemedia, Inc Xwave QS3000A [FM801] (rev b2)
```

amixer | less

```
imple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
 Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [on] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
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
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 14 [93%] [-3.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
 Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 14 [93%] [-3.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
(END) 
```

~$ sudo asoundconf list
```
Password:
Names of available sound cards:
rev50
default
```

[feisty, yamaha usb desktop speakers, VIA 82xx sound card(probably)]

---

### Post by offline on 2007-10-20
Since I couldn't find an answer I just pulled the usb out and connected the speakers with the soundcard and changed  sound preferences to alsa. Now the sound returned.

By the way, what an ugly login sound is that of feisty(I heard it now). How can I change it back to that of dapper?

---

