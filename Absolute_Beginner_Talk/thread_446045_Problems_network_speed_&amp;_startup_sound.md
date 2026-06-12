---
title: "Problems: network speed &amp; startup sound"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by msfisher on 2007-05-16
I've posted previously regarding slow network and startup, specifically under Edgy and Feisty.  I broke down and tried installing Dapper using the Alternate install disk.  

One result is that the slow network problem is partially fixed.  I'm now maxing at about 30KBps with a sustained rate of more than 20 up from a max of 18, about 8 sustained.  BTW, these numbers come from the Update dialog window.  I'd still like to find out if there are additional tweaks to get this up further.

I also found that my ping times were faster, but VERY variable.  Usually they now run in the several hundred millisecond range, down from the 1500ms range.  However, I get slowdown "spikes" of up to 3000ms.  How can I get this down to the consistent 25 to 100ms range I see in Windows and Xandros?

Lastly, there's the slow startup.  That hasn't changed, BUT I've seen something new.  Sound.  I generally have my sound routed through a pair of headphones that I only wear when I'm specifically listening to music or playing a game.  I'd noticed under Edgy and Feisty a very faint, odd, repetitive noise after login during startup.  When I installed Dapper, I happened to have the sound routed through speakers.  Lo and behold, the sound was the standard startup sound, "pulsing" a few notes at a time.  Once the startup sound was finished, everything worked OK.  Although I used the obvious solution -- turning off the startup sound -- that didn't fix the sound itself.  ALL playback does the same thing -- pulse, pulse, pause, pulse, pulse, pause -- going through the sound file with painful slowness.

How do I fix this one???

Thanks again!

---

### Post by Pragmatist on 2007-05-18
Please tell us what hardware your using:

1.) Processor
2.) RAM (i.e. How much)
3.) Sound Card


Please use the scrip I'm attaching (called "sound_info.sh")  In the directory you downloaded to, type this (filename is any name you choose):

```
./sound_info.sh filename
```

Attach the resulting file to your next post.

---

### Post by msfisher on 2007-05-19
Processor is Sempron 2600
Motherboard is MSI, chipset NVidia Nforce 3 250, so
sound & NIC are on the board
RAM is 512
Video is NVidia Geforce 2

I'm enough of a Linux newbie that I couldn't troubleshoot things when the script wouldn't run. Yes, I tried sudo, Yes, I typed it in exactly as you wrote.  SO, I ran the script steps individually.

Kernel:
Linux mike 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686 GNU/Linux

Mixers:
0: Realtek ALC655 rev 0

Names of available sound cards:
CK8S

Names of available sound cards:
CK8S
mike@mike:~/downloads$ lsmod | grep snd
snd_intel8x0           33692  1
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm

Resource Assignment:
           CPU0
  0:     234394          XT-PIC  timer
  1:       1629    IO-APIC-edge  i8042
  2:          0          XT-PIC  cascade
  5:     100000   IO-APIC-level  ohci_hcd:usb2
  7:         12    IO-APIC-edge  parport0
  8:          3    IO-APIC-edge  rtc
  9:          0   IO-APIC-level  ohci_hcd:usb1
 12:      32782    IO-APIC-edge  i8042
 14:      23650    IO-APIC-edge  ide0
 15:       5503   IO-APIC-level  ide1, ehci_hcd:usb3, NVidia CK8S, eth0
NMI:          0
LOC:     234171
ERR:          0
MIS:          0

PCI IDs:
0000:00:00.0 0600: 10de:00e1 (rev a1)
        Subsystem: 1462:7030
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 0601: 10de:00e0 (rev a2)
        Subsystem: 1462:7030
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 0c05: 10de:00e4 (rev a1)
        Subsystem: 1462:7030
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at fc00 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <available only to root>

0000:00:02.0 0c03: 10de:00e7 (rev a1) (prog-if 10)
        Subsystem: 1462:7030
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 9
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 0c03: 10de:00e7 (rev a1) (prog-if 10)
        Subsystem: 1462:7030
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.2 0c03: 10de:00e8 (rev a2) (prog-if 20)
        Subsystem: 1462:7030
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 15
        Memory at fe02d000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:06.0 0401: 10de:00ea (rev a1)
        Subsystem: 1462:b010
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 15
        I/O ports at f000 [size=256]
        I/O ports at ec00 [size=128]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 0101: 10de:00e5 (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: 1462:7030
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at e000 [size=16]
        Capabilities: <available only to root>

0000:00:0b.0 0604: 10de:00e2 (rev a2)
        Flags: bus master, 66MHz, medium devsel, latency 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fb000000-fcffffff
        Prefetchable memory behind bridge: e8000000-efffffff

0000:00:0e.0 0604: 10de:00ed (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fdf00000-fdffffff
        Prefetchable memory behind bridge: fde00000-fdefffff

0000:00:18.0 0600: 1022:1100
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 0600: 1022:1101
        Flags: fast devsel

0000:00:18.2 0600: 1022:1102
        Flags: fast devsel

0000:00:18.3 0600: 1022:1103
        Flags: fast devsel

0000:01:00.0 0300: 10de:0110 (rev b2)
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at fc000000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:02:0d.0 0200: 10ec:8139 (rev 10)
        Subsystem: 1462:030c
        Flags: bus master, medium devsel, latency 32, IRQ 15
        I/O ports at cc00 [size=256]
        Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at fde00000 [disabled] [size=64K]
        Capabilities: <available only to root>

Mixer:
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
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
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined enum
  Items: 'PCM' 'Analog In' 'IEC958 In'
  Item0: 'PCM'
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
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
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
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

Hope this helps.  Also, I had the same problem with sound and startup in Mandriva 2006 & 2007 BUT NOT with Windows 98, XP Home or Xandros 3.  I also didn't have it when I first installed Ubuntu using the Alternate CD and and OEM install logging in as oem.

---

### Post by msfisher on 2007-05-19
I missed the last line of the script.  Here are the system messages:

[17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 512MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f4fa0
[17179569.184000] On node 0 totalpages: 131072
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126976 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: Unable to locate RSDP
[17179569.184000] Intel MultiProcessor Specification v1.4
[17179569.184000]     Virtual Wire compatibility mode.
[17179569.184000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
[17179569.184000] Processor #0 15:12 APIC version 17
[17179569.184000] I/O APIC #2 Version 17 at 0xFEC00000.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Processors: 1
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: BOOT_IMAGE=Ubuntu_6.06.1_LTS_on_hdb3 ro root=/dev/hdb3 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[    0.000000] Detected 1607.446 MHz processor.
[   31.856708] Using tsc for high-res timesource
[   31.858045] Console: colour VGA+ 80x25
[   31.858661] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   31.859610] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   31.869909] Memory: 509016k/524288k available (1977k kernel code, 14836k reserved, 605k data, 288k init, 0k highmem)
[   31.869913] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   31.946599] Calibrating delay using timer specific routine.. 3218.13 BogoMIPS (lpj=6436265)
[   31.946628] Security Framework v1.0.0 initialized
[   31.946634] SELinux:  Disabled at boot.
[   31.946645] Mount-cache hash table entries: 512
[   31.946730] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000000 00000000 00000001
[   31.946737] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000000 00000000 00000001
[   31.946743] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)[   31.946746] CPU: L2 Cache: 128K (64 bytes/line)
[   31.946748] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000000 00000000 00000001
[   31.946760] mtrr: v2.0 (20020519)
[   31.946763] CPU: AMD Sempron(tm) Processor 2600+ stepping 00
[   31.946767] Enabling fast FPU save and restore... done.
[   31.946769] Enabling unmasked SIMD FPU exception support... done.
[   31.946773] Checking 'hlt' instruction... OK.
[   31.962776] checking if image is initramfs... it is
[   32.567586] Freeing initrd memory: 6619k freed
[   32.575165] ExtINT not setup in hardware but reported by MP table
[   32.575257] ENABLING IO-APIC IRQs
[   32.575433] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   32.615160] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   32.615195] ...trying to set up timer (IRQ0) through the 8259A ...
[   32.615197] ..... (found pin 0) ... failed.
[   32.654925] ...trying to set up timer as Virtual Wire IRQ... failed.
[   32.694648] ...trying to set up timer as ExtINT IRQ... works.
[   32.938797] NET: Registered protocol family 16
[   32.938822] EISA bus registered
[   32.954880] PCI: PCI BIOS revision 2.10 entry at 0xfb7b0, last bus=2
[   32.954888] PCI: Using configuration type 1
[   32.955287] ACPI: Subsystem revision 20051216
[   32.955290] ACPI: Interpreter disabled.
[   32.955294] Linux Plug and Play Support v0.97 (c) Adam Belay
[   32.955302] pnp: PnP ACPI: disabled
[   32.955306] PnPBIOS: Scanning system for PnP BIOS support...
[   32.955563] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc230
[   32.955569] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc260, dseg 0xf0000[   32.956342] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   32.956355] PCI: Probing PCI hardware
[   32.956359] PCI: Probing PCI hardware (bus 00)
[   32.956710] Boot video device is 0000:01:00.0
[   32.957560] PCI->APIC IRQ transform: 0000:00:01.1[A] -> IRQ 11
[   32.957563] PCI->APIC IRQ transform: 0000:00:02.0[A] -> IRQ 9
[   32.957566] PCI->APIC IRQ transform: 0000:00:02.1[B] -> IRQ 5
[   32.957569] PCI->APIC IRQ transform: 0000:00:02.2[C] -> IRQ 15
[   32.957572] PCI->APIC IRQ transform: 0000:00:06.0[A] -> IRQ 15
[   32.957579] PCI->APIC IRQ transform: 0000:02:0d.0[A] -> IRQ 15
[   32.985449] PCI: Bridge: 0000:00:0b.0
[   32.985452]   IO window: d000-dfff
[   32.985456]   MEM window: fb000000-fcffffff
[   32.985460]   PREFETCH window: e8000000-efffffff
[   32.985465] PCI: Bridge: 0000:00:0e.0
[   32.985467]   IO window: c000-cfff
[   32.985470]   MEM window: fdf00000-fdffffff
[   32.985473]   PREFETCH window: fde00000-fdefffff
[   32.985484] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   32.985820] audit: initializing netlink socket (disabled)
[   32.985830] audit(1179565283.780:1): initialized
[   32.985924] VFS: Disk quotas dquot_6.5.1
[   32.985945] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   32.985998] Initializing Cryptographic API
[   32.986002] io scheduler noop registered
[   32.986009] io scheduler anticipatory registered
[   32.986016] io scheduler deadline registered
[   32.986032] io scheduler cfq registered
[   32.986196] isapnp: Scanning for PnP cards...
[   33.340024] isapnp: No Plug & Play device found
[   33.350307] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   33.888630] serio: i8042 AUX port at 0x60,0x64 irq 12
[   33.891094] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.891139] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   33.891233] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.891350] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.893697] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.893909] 00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.894260] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.894302] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.894305] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.894428] mice: PS/2 mouse device common for all mice
[   33.904129] EISA: Probing bus 0 at eisa.0
[   33.904147] Cannot allocate resource for EISA slot 4
[   33.904162] EISA: Detected 0 cards.
[   33.904212] NET: Registered protocol family 2
[   33.946656] input: AT Translated Set 2 keyboard as /class/input/input0
[   33.950510] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)[   33.950739] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[   33.951364] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   33.951692] TCP: Hash tables configured (established 131072 bind 65536)
[   33.951695] TCP reno registered
[   33.951781] TCP bic registered
[   33.951789] NET: Registered protocol family 1
[   33.951796] NET: Registered protocol family 8
[   33.951798] NET: Registered protocol family 20
[   33.951818] Using IPI Shortcut mode
[   33.951854] Freeing unused kernel memory: 288k freed
[   34.001520] vga16fb: initializing
[   34.001526] vga16fb: mapped to 0xc00a0000
[   34.158394] Console: switching to colour frame buffer device 80x25
[   34.158401] fb0: VGA16 VGA frame buffer device
[   35.174309] Capability LSM initialized
[   35.971555] SCSI subsystem initialized
[   35.973198] libata version 1.20 loaded.
[   35.976421] NFORCE3-250: IDE controller at PCI slot 0000:00:08.0
[   35.976438] NFORCE3-250: chipset revision 162
[   35.976440] NFORCE3-250: not 100% native mode: will probe irqs later
[   35.976444] NFORCE3-250: BIOS didn't set cable bits correctly. Enabling workaround.
[   35.976449] NFORCE3-250: 0000:00:08.0 (rev a2) UDMA133 controller
[   35.976460]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
[   35.976471]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
[   35.976479] Probing IDE interface ide0...
[   36.262377] hda: WDC WD800JB-00JJA0, ATA DISK drive
[   36.542355] hdb: WDC WD800JB-00CRA1, ATA DISK drive
[   36.600109] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   36.600319] Probing IDE interface ide1...
[   37.334299] hdc: LITE-ON CD-RW SOHR-5239S, ATAPI CD/DVD-ROM drive
[   38.006450] ide1 at 0x170-0x177,0x376 on irq 15
[   38.014714] hda: max request size: 128KiB
[   38.027327] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[   38.027406] hda: cache flushes supported
[   38.027553]  hda: hda1 hda2 < hda5 hda6 >
[   38.067525] hdb: max request size: 128KiB
[   38.074112] hdb: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[   38.074118] hdb: cache flushes not supported
[   38.074230]  hdb: hdb1 hdb2 hdb3 hdb4 < hdb5 hdb6 >
[   38.113587] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[   38.113597] Uniform CD-ROM driver Revision: 3.20
[   38.841405] usbcore: registered new driver usbfs
[   38.841697] usbcore: registered new driver hub
[   38.843020] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   38.843327] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   38.843331] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   38.874097] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   38.874124] ohci_hcd 0000:00:02.0: irq 9, io mem 0xfe02f000
[   38.932318] hub 1-0:1.0: USB hub found
[   38.932330] hub 1-0:1.0: 4 ports detected
[   39.034232] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   39.034236] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   39.050186] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   39.050197] ohci_hcd 0000:00:02.1: irq 5, io mem 0xfe02e000
[   39.108264] hub 2-0:1.0: USB hub found
[   39.108273] hub 2-0:1.0: 4 ports detected
[   39.211490] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   39.211495] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   39.211532] ehci_hcd 0000:00:02.2: debug port 1
[   39.211536] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   39.211723] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   39.211732] ehci_hcd 0000:00:02.2: irq 15, io mem 0xfe02d000
[   39.211740] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   39.211936] hub 3-0:1.0: USB hub found
[   39.211946] hub 3-0:1.0: 8 ports detected
[   39.377259] Attempting manual resume
[   39.396400] kjournald starting.  Commit interval 5 seconds
[   39.396412] EXT3-fs: mounted filesystem with ordered data mode.
[   48.372404] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   48.376586] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.386879] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   48.386905] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   48.673991] Linux agpgart interface v0.101 (c) Dave Jones
[   48.759892] input: PS2++ Logitech MX Mouse as /class/input/input1
[   48.780295] agpgart: Detected AGP bridge 0
[   48.780306] agpgart: Setting up Nforce3 AGP.
[   48.784854] agpgart: AGP aperture is 128M @ 0xf0000000
[   48.892273] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   48.978017] nvidia: module license 'NVIDIA' taints kernel.
[   49.160376] input: PC Speaker as /class/input/input2
[   49.162360] Real Time Clock Driver v1.12
[   49.170997] 8139too Fast Ethernet driver 0.9.27
[   49.209381] intel8x0_measure_ac97_clock: measured 54812 usecs
[   49.209386] intel8x0: clocking to 46982
[   49.210717] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[   49.225685] eth0: RealTek RTL8139 at 0xe09e8000, 00:13:d3:9e:28:0d, IRQ 15
[   49.225688] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   49.262047] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   49.642253] ts: Compaq touchscreen protocol output
[   49.854580] Floppy drive(s): fd0 is 1.44M
[   49.888683] FDC 0 is a post-1991 82077
[   49.920688] parport: PnPBIOS parport detected.
[   49.920737] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   49.941405] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   50.371635] lp0: using parport0 (interrupt-driven).
[   50.429052] Adding 2048248k swap on /dev/hdb6.  Priority:-1 extents:1 across:2048248k
[   50.590972] EXT3 FS on hdb3, internal journal
[   50.744873] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   50.744878] md: bitmap version 4.39
[   51.280819] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   51.978481] cdrom: hdc: mrw address space DMA selected
[   70.879452] ReiserFS: hdb2: found reiserfs format "3.6" with standard journal[   70.880880] ReiserFS: hdb2: using ordered data mode
[   70.880967] ReiserFS: hdb2: journal params: device hdb2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   70.882135] ReiserFS: hdb2: checking transaction log (hdb2)
[   70.912997] ReiserFS: hdb2: Using r5 hash to sort names
[   72.174868] powernow-k8: Power state transitions not supported
[   74.024047] NET: Registered protocol family 10
[   74.024152] lo: Disabled Privacy Extensions
[   74.024284] IPv6 over IPv4 tunneling driver
[   78.241884] ppdev: user-space parallel port driver
[   78.462591] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   78.809418] Bluetooth: Core ver 2.8
[   78.809424] NET: Registered protocol family 31
[   78.809427] Bluetooth: HCI device and connection manager initialized
[   78.809437] Bluetooth: HCI socket layer initialized
[   78.855810] Bluetooth: L2CAP ver 2.8
[   78.855816] Bluetooth: L2CAP socket layer initialized
[   78.899954] Bluetooth: RFCOMM socket layer initialized
[   78.899971] Bluetooth: RFCOMM TTY layer initialized
[   78.899974] Bluetooth: RFCOMM ver 1.7
[   79.160639] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[   79.160648] hdc: drive_cmd: error=0x04 { AbortedCommand }
[   79.160651] ide: failed opcode was: 0xec
[   81.970364] irq 5: nobody cared (try booting with the "irqpoll" option)
[   81.970391]  [<c013ee82>] __report_bad_irq+0x22/0x80
[   81.970402]  [<c013ef78>] note_interrupt+0x68/0xc0
[   81.970423]  [<c013e83c>] __do_IRQ+0xbc/0xe0
[   81.970455]  [<c010596a>] do_IRQ+0x1a/0x30
[   81.970460]  [<c01040aa>] common_interrupt+0x1a/0x20
[   81.970490]  [<c010106a>] default_idle+0x3a/0x70
[   81.970498]  [<c01010dc>] cpu_idle+0x1c/0x60
[   81.970504]  [<c03887c6>] start_kernel+0x176/0x1d0
[   81.970520] handlers:
[   81.970522] [<e0905730>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   81.970549] Disabling IRQ #5
[   84.402828] eth0: no IPv6 routers present
[   90.690322] cdrom: hdc: mrw address space DMA selected
[   90.747879] cdrom: hdc: mrw address space DMA selected
[   90.787858] ISO 9660 Extensions: Microsoft Joliet Level 1
[   90.802916] ISOFS: changing to secondary root

---

### Post by Pragmatist on 2007-05-19
My mistake about the script.  For future reference, you first need to make the script executable by typing:
```
chmod a+x sound_info.sh
```You got us the info anyway; good job!

I think both your problems may have to do with your "PREEMPT" kernel.  First, update your system, which is a good idea anyway:
First find the available changes:
```
sudo apt-get update
```Then upgrade the changes:
```
sudo apt-get upgrade
```

Now reboot your system. 

After reboot see if your kernel still has "PREEMPT" at the end of it:
```
uname -a
```

Another option, if you want to try something without upgrading, is to switch kernel's at startup.  When your machine boots, do you get a list of kernel's to choose from?  If so, pick a kernel without the "PREEMPT"

---

### Post by msfisher on 2007-05-20
I tried the update path.  I'm using Dapper from the Alternate CD (all of the live/install CD's have problems with my system -- keep reporting something wrong with my hdc which works fine).  Apt-get says everything is up to date, and no change was made to the kernel.

Remembering I'm new to this, how else do I recompile the kernel?  Or should I add some of the Edgy or Feisty update servers to my list?

---

### Post by Pragmatist on 2007-05-20
[quote=pragmatist]Another option, if you want to try something without upgrading, is to switch kernel's at startup. **When your machine boots, do you get a list of kernel's to choose from?** If so, pick a kernel without the "PREEMPT" [/quote]

Did you see the list of kernel's when you boot your machine???

One very simple test is to start your machine in safe mode, or using a different kernel.  When you boot your computer, there should be a list available.  Pick something other than your current kernel and/or one marked as "recovery mode".  The list probably has a timeout of 20 seconds or so.  Make sure you look for it while your machine boots.

Let us know what happens.

---

### Post by msfisher on 2007-05-20
Sorry, forgot to mention.  I boot with LILO, multiple to Xandros (LILO set by Xandros -- it won't boot (kernel panic) with the GRUB that Ubuntu installs) & Win98.  No option there for other kernels.

---

### Post by Pragmatist on 2007-05-21
please post contents of **/etc/apt/sources.lst**

---

### Post by Pragmatist on 2007-05-21
> **Pragmatist said:**
> please post contents of **/etc/apt/sources.lst**

Sorry!  The file is [B]/etc/apt/sources.list
[/B]

---

### Post by msfisher on 2007-05-23
Sorry to be so slow replying to you Pragmatist -- it's been very busy around here.  Here's the contents of /etc/apt/sources.list:

# 
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

Thanks again for your efforts!

---

### Post by msfisher on 2007-05-23
I missed the last few lines:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Like i said, things have been a bear here -- even affecting this!

---

### Post by Pragmatist on 2007-05-23
edit your sources.list and make sure any line with "cdrom" is commented out (put a  #   in front of the line)

You definitely want to put a # in front of this line:
>  deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restrictedThen try updating:
```
sudo apt-get update
```and upgrading:
```
sudo apt-get upgrade
```

---

### Post by msfisher on 2007-05-24
OK, I tried it and got the same result as before: after apt-get upgrade, lots of zeros.  I did manage to get the GUI update tool to work when I first installed Dapper.

---

### Post by Pragmatist on 2007-05-24
> **msfisher said:**
> OK, I tried it and got the same result as before: after apt-get upgrade, **lots of zeros**.  I did manage to get the GUI update tool to work when I first installed Dapper.

What do you mean by "lots of zeros"?

---

### Post by msfisher on 2007-05-25
Zero files downloaded, zero files updated.

---

### Post by Pragmatist on 2007-05-25
When you go into Synaptic, how many packages does it say are available?  (you can see the number in the status bar--bottom of the window)

---

### Post by msfisher on 2007-05-26
4463 Listed, 1111 installed.

---

### Post by Pragmatist on 2007-05-26
I have 21,487 packages!  You don't have all of the repositories enabled.  I can't tell you to do so, as some of these are "unofficial" and are not supported by Ubuntu.  However, if you are interested in enabling them, follow these instructions:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Also, I ran across this which may be helpful (again, this isn't official):

[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

---

### Post by msfisher on 2007-05-26
Some extra info from Synaptic:

I notice there are several Linux Kernel Images, including 2.6.15.23-k7 (I have a Duron processor), 2.6.15-23-server, 2.6.15.23-386 and the equivalent 2.6.15.25, 26, 27, and 28 images.  It shows the 26-386 (26.47), and 28-386 (28.55) images as being installed.  There are also some images just listed as "linux-image-" and the 386 (version 2.6.15.26) from them is listed as installed.

---

### Post by Pragmatist on 2007-05-26
Have you tried using a LiveCD ?   Do the speed/sound issues occur there too?

---

### Post by msfisher on 2007-05-26
The live cd's for Dapper, Edgy and Feisty all find apparently nonexistent errors with one of my hard drives during boot.  I've done all the Ubuntu installs from alternate cd's -- and the problems have existed since the first time I logged into Edgy as "oem" immediately after the first installation.  I've seen the exact same problems with installations of Mandriva 2006 & 2007 but NOT with Xandros 3.

---

### Post by Pragmatist on 2007-05-26
Interesting.  I would try using Knoppix.  They are one of the first LiveCDs and are known for their ability to correctly recognize hardware.

If you don't want to try that, some other tests would be (not necessarily in this order):

1.) Examine LILO and see if you can boot a different kernel for testing purposes.  In GRUB it is very easy.  There is just a menu that comes up everytime you start the computer.  It has a list of the various kernels and you just select the one you want.  There must be a way to select another kernel with LILO (IF in fact you have more than one kernel installed--which it sounds like you do.)

2.) Add more repositories and then do another update and upgrade.

3.) Try the suggestions in that link I posted (about how to tweak Ubuntu for speed)

---

### Post by msfisher on 2007-06-04
I've tried both your suggestions and some other things I found on line with no luck.  However, I've also tried some completely different ideas.  I tried installing some other distros to see if the problem is specific to Ubuntu and Mandriva.  I found several odd things.  First, as I'd mentioned, all of the Ubuntu live cd's I'd burned gave errors on "hdc."  I think that may have been a CD-ROM error not a hard drive one.  I tried the Live CD's for Linux Mint 2.2 and PC LinuxOS 2007.  Neither one had a problem running from the CD, and the sound actually worked.  Once I installed them to disk, though, the sound was back to what it had been.  I tried burning a fresh Ubuntu 7.04 cd at a different speed, and, wonders, it started.  Plus, the sound was good.  However, when I installed to hard drive, the sound was shot again.  I noticed with one of the distros that during verbose boot an error "NVAUDIO not found" flashed by.  I don't know how to get a verbose boot from Ubuntu, so I can't say if it's there, too. Also, the Feisty install used the generic kernel. 

SO it's starting to look like this problem is in the sound driver.  How do I install a generic one, rather than the nvidia one that apparently is getting used?

I may start a new thread about this as well.

BTW, I also plan on trying Freespire and Sabayon to see if the problem persists.

---

### Post by Pragmatist on 2007-06-04
Please post the exact make and model of your motherboard.  I've tried to use the information in your earlier post, but there is no such motherboard on MSI's website.  If you have the book that came with your computer, that should have the information.  Since the sound is onboard, if we have the exact motherboard information, we can get the exact sound card chipset information.  Then it is just a matter of researching the driver.

---

### Post by msfisher on 2007-06-05
Motherboard is an MSI K8N Neo V2.0 (MS-7030, an older version than on the web site).  Chipset is nForce3 250.  Audio is shown as RealtekALC655 _in the manual_.

---

### Post by Pragmatist on 2007-06-05
Please post the output:

```
lsmod |grep snd
```

---

### Post by msfisher on 2007-06-07
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm

---

### Post by Pragmatist on 2007-06-07
I found these:

[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsRealtek?highlight=%28realtek%29]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsRealtek?highlight=%28realtek%29")

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/8820](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/8820)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/8050](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/8050)

Try this solution (in the second link given above):
>  [FONT=monospace]
 I followed the instructions in [bug #8050]("https://bugs.launchpad.net/bugs/8050") adding this two lines in
/etc/modprobe.d/aliases and everything works now:
 alias snd-card-0 snd_via82xx
options snd_via82xx index=0
 alias snd-card-1 snd_bt87x
options snd_bt87x index=1
 Thanks!
[/FONT]
         


---

### Post by msfisher on 2007-06-08
I gave it a shot, with the usual no luck.  I have some other info, though.

In EVERY live CD I've tried -- Ubuntu 7.04, Yoper, Freespire, PCLinuxOS -- THE SOUND WORKS.  It only DOESN'T work once I've installed to HD.  Here, for example, is the lsmod | grep snd from Yoper (which I have running right now):

snd_intel8x0          29084  0  
snd_ac97_codec    95652  1  snd_intel8x0
ac97_bus                 2048  1  snd_ac97_codec
snd_pcm                68104  2  snd_intel8x0,snd_ac97_codec
snd_timer               19204  1  snd_pcm
snd                         43296  4  snd_intel8x0,snd_ac97_codec,snd,snd_timer
soudncore                 6240  1  snd
snd_page_alloc         7560  2  snd_intel8x0,snd_pcm

---

