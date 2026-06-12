---
title: "No sound on a PB easynote A6630"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by ullvarg on 2007-01-23
I have a Packard bell easynote A6630, it's about 1 year old and i have been running windows xp on up untill the last couple weeks when I started to look through a bunch of linux distros, Since Im a total linux noobe I went for ubunto, but I cant get my soundcard to work... Acording to PB's webpage it's runs a "Conexant 20468-31 AC'97 audio codec", I wen trough the steps in the wiki about debugging a soundcard and this is the info I got so far:
> 
ullvarg@eagel2:~$ tail -2 /proc/asound/oss/sndstat
Mixers:
0: Conexant id 31
ullvarg@eagel2:~$
ullvarg@eagel2:~$
ullvarg@eagel2:~$


> 
ullvarg@eagel2:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [on] Capture [off]
  Front Right: Playback 31 [100%] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [on] Capture [off]
  Front Right: Playback 31 [100%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Phone',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
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
  Mono: 3 [100%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [on]
Simple mixer control 'Aux',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [on]
  Front Right: Capture 0 [0%] [on]
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


> 
ullvarg@eagel2:~$ lspci -nv
00:00.0 0600: 8086:2590 (rev 03)
        Subsystem: 152d:0745
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 0300: 8086:2592 (rev 03)
        Subsystem: 152d:0745
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at b0000000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 0380: 8086:2792 (rev 03)
        Subsystem: 152d:0745
        Flags: fast devsel
        Memory at 32000000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: <access denied>

00:1c.0 0604: 8086:2660 (rev 04)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:1d.0 0c03: 8086:2658 (rev 04)
        Subsystem: 152d:0745
        Flags: bus master, medium devsel, latency 0, IRQ 217
        I/O ports at 1820 [size=32]

00:1d.1 0c03: 8086:2659 (rev 04)
        Subsystem: 152d:0745
        Flags: bus master, medium devsel, latency 0, IRQ 225
        I/O ports at 1840 [size=32]

00:1d.2 0c03: 8086:265a (rev 04)
        Subsystem: 152d:0745
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at 1860 [size=32]

00:1d.3 0c03: 8086:265b (rev 04)
        Subsystem: 152d:0745
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at 1880 [size=32]

00:1d.7 0c03: 8086:265c (rev 04) (prog-if 20)
        Subsystem: 152d:0745
        Flags: bus master, medium devsel, latency 0, IRQ 217
        Memory at b0040000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 0604: 8086:2448 (rev d4) (prog-if 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=216
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: b8000000-b80fffff
        Prefetchable memory behind bridge: 0000000030000000-0000000031f00000
        Capabilities: <access denied>

00:1e.2 0401: 8086:266e (rev 04)
        Subsystem: 152d:0745
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at b0040800 (32-bit, non-prefetchable) [size=512]
        Memory at b0040400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1e.3 0703: 8086:266d (rev 04)
        Subsystem: 152d:0745
        Flags: medium devsel, IRQ 201
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

00:1f.0 0601: 8086:2641 (rev 04)
        Subsystem: 152d:0745
        Flags: bus master, medium devsel, latency 0

00:1f.1 0101: 8086:266f (rev 04) (prog-if 8a)
        Subsystem: 152d:0745
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]

00:1f.3 0c05: 8086:266a (rev 04)
        Subsystem: 152d:0745
        Flags: medium devsel, IRQ 11
        I/O ports at 20a0 [size=32]

06:01.0 0607: 104c:8031
        Subsystem: 152d:0745
        Flags: bus master, medium devsel, latency 168, IRQ 177
        Memory at b8006000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 34000000-35fff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

06:01.2 0c00: 104c:8032 (prog-if 10)
        Subsystem: 152d:0745
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at b8007000 (32-bit, non-prefetchable) [size=2K]
        Memory at b8000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

06:01.3 0180: 104c:8033
        Subsystem: 152d:0745
        Flags: bus master, medium devsel, latency 57, IRQ 177
        Memory at b8004000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

06:03.0 0200: 17fe:2220
        Subsystem: 17fe:2220
        Flags: medium devsel, IRQ 255
        I/O ports at 4400 [size=32]
        Memory at b8008000 (32-bit, non-prefetchable) [size=32]
        Memory at b8007800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

06:08.0 0200: 10ec:8139 (rev 10)
        Subsystem: 152d:0745
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at 4000 [size=256]
        Memory at b8008400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>


> 
ullvarg@eagel2:~$ asoundconf list
Names of available sound cards:
ICH6


> 
ullvarg@eagel2:~$ cat /etc/asound.conf ~/.asoundrc*
cat: /etc/asound.conf: No such file or directory
cat: /home/ullvarg/.asoundrc*: No such file or directory


> 
ullvarg@eagel2:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[17179569.184000]  BIOS-e820: 000000001f6e0000 - 000000001f6ea000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001f6ea000 - 000000001f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 502MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 128736
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 124640 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6af0
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1f6e4e96
[17179569.184000] ACPI: FADT (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x1f6e9e88
[17179569.184000] ACPI: MADT (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x1f6e9efc
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1f6e9fd8
[17179569.184000] ACPI: MCFG (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x1f6e9f9c
[17179569.184000] ACPI: SSDT (v001 SataRe SataAhci 0x00001000 INTL 0x20030224) @ 0x1f6e523b
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x1f6e50ef
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x1f6e4ed6
[17179569.184000] ACPI: DSDT (v001 INTEL  ALVISO   0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1397.093 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.780000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.780000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.800000] Memory: 500712k/514944k available (1910k kernel code, 13732k reserved, 1070k data, 308k init, 0k highmem)
[17179570.800000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.880000] Calibrating delay using timer specific routine.. 2798.42 BogoMIPS (lpj=5596849)
[17179570.880000] Security Framework v1.0.0 initialized
[17179570.880000] SELinux:  Disabled at boot.
[17179570.880000] Mount-cache hash table entries: 512
[17179570.880000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[17179570.880000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[17179570.880000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.880000] CPU: L2 cache: 1024K
[17179570.880000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000000 00000000 00000000
[17179570.880000] Checking 'hlt' instruction... OK.
[17179570.896000] SMP alternatives: switching to UP code
[17179570.896000] Freeing SMP alternatives: 16k freed
[17179570.896000] checking if image is initramfs... it is
[17179571.560000] Freeing initrd memory: 5523k freed
[17179571.560000] ACPI: Core revision 20060707
[17179571.560000] ACPI: Looking for DSDT ... not found!
[17179571.596000] CPU0: Intel(R) Celeron(R) M processor         1.40GHz stepping 08
[17179571.596000] Total of 1 processors activated (2798.42 BogoMIPS).
[17179571.596000] ENABLING IO-APIC IRQs
[17179571.596000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179571.740000] Brought up 1 CPUs
[17179571.740000] migration_cost=0
[17179571.740000] NET: Registered protocol family 16
[17179571.740000] EISA bus registered
[17179571.740000] ACPI: bus type pci registered
[17179571.740000] PCI: Using MMCONFIG
[17179571.740000] Setting up standard PCI resources
[17179571.748000] ACPI: Interpreter enabled
[17179571.748000] ACPI: Using IOAPIC for interrupt routing
[17179571.748000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.748000] PCI: Probing PCI hardware (bus 00)
[17179571.748000] Boot video device is 0000:00:02.0
[17179571.748000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179571.748000] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[17179571.752000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179571.752000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.752000] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#07) (try 'pci=assign-busses')
[17179571.752000] Please report the result to linux-kernel to fix this permanently
[17179571.752000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.760000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179571.760000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179571.764000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179571.764000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[17179571.764000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179571.764000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179571.764000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179571.764000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[17179571.764000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[17179571.764000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179571.764000] ACPI: Embedded Controller [EC0] (gpe 29) interrupt mode.
[17179571.776000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.776000] pnp: PnP ACPI init
[17179571.776000] pnp: PnP ACPI: found 8 devices
[17179571.776000] PnPBIOS: Disabled by ACPI PNP
[17179571.776000] PCI: Using ACPI for IRQ routing
[17179571.776000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.776000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179571.776000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179571.776000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179571.776000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179571.776000] PCI: Bridge: 0000:00:1c.0
[17179571.776000]   IO window: disabled.
[17179571.776000]   MEM window: disabled.
[17179571.776000]   PREFETCH window: disabled.
[17179571.776000] PCI: Bus 7, cardbus bridge: 0000:06:01.0
[17179571.776000]   IO window: 00004800-000048ff
[17179571.776000]   IO window: 00004c00-00004cff
[17179571.776000]   PREFETCH window: 30000000-31ffffff
[17179571.776000]   MEM window: 34000000-35ffffff
[17179571.776000] PCI: Bridge: 0000:00:1e.0
[17179571.776000]   IO window: 4000-4fff
[17179571.776000]   MEM window: b8000000-b80fffff
[17179571.776000]   PREFETCH window: 30000000-31ffffff
[17179571.776000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179571.776000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179571.776000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.776000] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179571.780000] NET: Registered protocol family 2
[17179571.812000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179571.812000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179571.812000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179571.812000] TCP: Hash tables configured (established 16384 bind 8192)
[17179571.812000] TCP reno registered
[17179571.812000] Simple Boot Flag at 0x36 set to 0x1
[17179571.812000] audit: initializing netlink socket (disabled)
[17179571.812000] audit(1169531547.812:1): initialized
[17179571.812000] VFS: Disk quotas dquot_6.5.1
[17179571.812000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.812000] Initializing Cryptographic API
[17179571.812000] io scheduler noop registered
[17179571.812000] io scheduler anticipatory registered
[17179571.812000] io scheduler deadline registered
[17179571.812000] io scheduler cfq registered (default)
[17179571.812000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179571.812000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179571.812000] assign_interrupt_mode Found MSI capability
[17179571.812000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179571.812000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179571.812000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179571.812000] isapnp: Scanning for PnP cards...
[17179572.168000] isapnp: No Plug & Play device found
[17179572.196000] Real Time Clock Driver v1.12ac
[17179572.196000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.196000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 201
[17179572.196000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[17179572.200000] mice: PS/2 mouse device common for all mice
[17179572.200000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.200000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.200000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.200000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179572.200000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.200000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.200000] EISA: Probing bus 0 at eisa.0
[17179572.200000] Cannot allocate resource for EISA slot 1
[17179572.200000] Cannot allocate resource for EISA slot 2
[17179572.200000] Cannot allocate resource for EISA slot 4
[17179572.200000] EISA: Detected 0 cards.
[17179572.204000] TCP bic registered
[17179572.204000] NET: Registered protocol family 1
[17179572.204000] NET: Registered protocol family 8
[17179572.204000] NET: Registered protocol family 20
[17179572.204000] Using IPI No-Shortcut mode
[17179572.204000] ACPI: (supports S0 S3 S4 S5)
[17179572.204000] Freeing unused kernel memory: 308k freed
[17179572.236000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.336000] Capability LSM initialized
[17179573.372000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179573.372000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179573.372000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179573.372000] ACPI: Getting cpuindex for acpiid 0x1
[17179573.372000] ACPI: Thermal Zone [THRM] (58 C)
[17179573.696000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179573.696000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 209
[17179573.696000] ICH6: chipset revision 4
[17179573.696000] ICH6: not 100% native mode: will probe irqs later
[17179573.696000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:DMA
[17179573.696000] Probing IDE interface ide0...
[17179573.984000] hda: HTS421260H9AT00, ATA DISK drive
[17179574.768000] hdb: PHILIPS DVD+/-RW SDVD8431, ATAPI CD/DVD-ROM drive
[17179574.824000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.848000] hda: max request size: 512KiB
[17179574.856000] hda: 117210240 sectors (60011 MB) w/1570KiB Cache, CHS=16383/255/63, UDMA(33)
[17179574.860000] hda: cache flushes supported
[17179574.860000]  hda: hda1 hda2 < hda5 >
[17179574.904000] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.904000] Uniform CD-ROM driver Revision: 3.20
[17179575.280000] Probing IDE interface ide1...
[17179575.312000] usbcore: registered new driver usbfs
[17179575.312000] usbcore: registered new driver hub
[17179575.316000] USB Universal Host Controller Interface driver v3.0
[17179575.316000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 217
[17179575.316000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179575.316000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179575.316000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179575.316000] uhci_hcd 0000:00:1d.0: irq 217, io base 0x00001820
[17179575.316000] usb usb1: configuration #1 chosen from 1 choice
[17179575.320000] hub 1-0:1.0: USB hub found
[17179575.320000] hub 1-0:1.0: 2 ports detected
[17179575.380000] ieee1394: Initialized config rom entry `ip1394'
[17179575.424000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 225
[17179575.424000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179575.424000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179575.424000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179575.424000] uhci_hcd 0000:00:1d.1: irq 225, io base 0x00001840
[17179575.424000] usb usb2: configuration #1 chosen from 1 choice
[17179575.424000] hub 2-0:1.0: USB hub found
[17179575.424000] hub 2-0:1.0: 2 ports detected
[17179575.528000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 209
[17179575.528000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179575.528000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179575.528000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179575.528000] uhci_hcd 0000:00:1d.2: irq 209, io base 0x00001860
[17179575.528000] usb usb3: configuration #1 chosen from 1 choice
[17179575.528000] hub 3-0:1.0: USB hub found
[17179575.528000] hub 3-0:1.0: 2 ports detected
[17179575.632000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 177
[17179575.632000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179575.632000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179575.632000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179575.632000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x00001880
[17179575.632000] usb usb4: configuration #1 chosen from 1 choice
[17179575.632000] hub 4-0:1.0: USB hub found
[17179575.632000] hub 4-0:1.0: 2 ports detected
[17179575.736000] ACPI: PCI Interrupt 0000:06:01.2[A] -> GSI 16 (level, low) -> IRQ 177
[17179575.788000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 217
[17179575.788000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179575.788000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179575.788000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179575.788000] ehci_hcd 0000:00:1d.7: debug port 1
[17179575.788000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179575.788000] ehci_hcd 0000:00:1d.7: irq 217, io mem 0xb0040000
[17179575.792000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.792000] usb usb5: configuration #1 chosen from 1 choice
[17179575.792000] hub 5-0:1.0: USB hub found
[17179575.792000] hub 5-0:1.0: 8 ports detected
[17179575.792000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[b8007000-b80077ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179575.940000] Attempting manual resume
[17179576.020000] kjournald starting.  Commit interval 5 seconds
[17179576.020000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.376000] usb 3-1: new low speed USB device using uhci_hcd and address 3
[17179576.548000] usb 3-1: configuration #1 chosen from 1 choice
[17179577.064000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f000064104f]
[17179588.484000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.492000] agpgart: Detected an Intel 915GM Chipset.
[17179588.492000] agpgart: Detected 7932K stolen memory.
[17179588.512000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179589.208000] hw_random hardware driver 1.0.0 loaded
[17179589.516000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.592000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.856000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[17179589.892000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179589.896000] usbcore: registered new driver hiddev
[17179589.916000] input: Logitech Trackball as /class/input/input2
[17179589.916000] input: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.2-1
[17179589.916000] usbcore: registered new driver usbhid
[17179589.916000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179589.936000] ts: Compaq touchscreen protocol output
[17179589.964000] ACPI: PCI Interrupt 0000:06:01.3[A] -> GSI 16 (level, low) -> IRQ 177
[17179590.004000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 169
[17179590.004000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179590.044000] 8139too Fast Ethernet driver 0.9.27
[17179590.320000] intel8x0_measure_ac97_clock: measured 55646 usecs
[17179590.320000] intel8x0: clocking to 48000
[17179590.320000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179590.320000] eth0: RealTek RTL8139 at 0xe0258400, 00:c0:9f:ba:b4:43, IRQ 177
[17179590.320000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179590.328000] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179590.328000] Yenta: CardBus bridge found at 0000:06:01.0 [152d:0745]
[17179590.328000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179590.328000] Yenta: Routing CardBus interrupts to PCI
[17179590.328000] Yenta TI: socket 0000:06:01.0, mfunc 0x00a21b22, devctl 0x64
[17179590.344000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179590.560000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 177
[17179590.560000] Socket status: 30000006
[17179590.560000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[17179590.560000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[17179590.560000] cs: IO port probe 0x4000-0x4fff: clean.
[17179590.560000] pcmcia: parent PCI bridge Memory window: 0xb8000000 - 0xb80fffff
[17179590.560000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179590.728000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179591.032000] cs: IO port probe 0x100-0x3af: clean.
[17179591.036000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179591.036000] cs: IO port probe 0x820-0x8ff: clean.
[17179591.036000] cs: IO port probe 0xc00-0xcf7: clean.
[17179591.036000] cs: IO port probe 0xa00-0xaff: clean.
[17179591.200000] lp: driver loaded but no devices found
[17179591.252000] SCSI subsystem initialized
[17179591.272000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179591.272000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179591.296000] Adding 1485972k swap on /dev/disk/by-uuid/3ee05e44-19fd-4b73-ad7b-4d086a946529.  Priority:-1 extents:1 across:1485972k
[17179591.372000] EXT3 FS on hda1, internal journal
[17179591.820000] NET: Registered protocol family 17
[17179595.332000] NET: Registered protocol family 10
[17179595.332000] lo: Disabled Privacy Extensions
[17179595.332000] IPv6 over IPv4 tunneling driver
[17179597.160000] ACPI: Power Button (FF) [PWRF]
[17179597.160000] ACPI: Lid Switch [LID]
[17179597.160000] ACPI: Power Button (CM) [PWRB]
[17179597.160000] ACPI: Sleep Button (CM) [SLPB]
[17179597.292000] ACPI: EC HC smbus [SMBC]
[17179597.312000] ibm_acpi: ec object not found
[17179597.352000] pcc_acpi: loading...
[17179598.080000] ACPI: Smart Battery System [SBS0]
[17179598.212000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[17179599.800000] [drm] Initialized drm 1.0.1 20051102
[17179599.804000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179599.804000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179601.140000] apm: BIOS not found.
[17179606.152000] eth0: no IPv6 routers present
[17179607.236000] Bluetooth: Core ver 2.8
[17179607.236000] NET: Registered protocol family 31
[17179607.236000] Bluetooth: HCI device and connection manager initialized
[17179607.236000] Bluetooth: HCI socket layer initialized
[17179607.376000] Bluetooth: L2CAP ver 2.8
[17179607.376000] Bluetooth: L2CAP socket layer initialized
[17179607.636000] Bluetooth: RFCOMM socket layer initialized
[17179607.636000] Bluetooth: RFCOMM TTY layer initialized
[17179607.636000] Bluetooth: RFCOMM ver 1.7


Sorry for adding so much probably useless info, but i don't know whats important or not so I added it all:confused: 
If anyone have the energy and time to look into it I would verymuch aprishiate it.

---

### Post by carlosfocker on 2007-02-07
We should start with the basics first.  Is your speakers plugged into the right port (I know it seems silly but it happens). You should first check to see if any thing is muted.  Also it is common that PCM is set to 0% which would cause sound to not work.

Type this in a terminal

```
alsamixer
```

Check the PCM level and set it to about 80% if not set at all.  Also check if the master is muted.

---

