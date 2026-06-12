---
title: "audiotestsrc problem"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-11-11
hey there having a problem with sound..

after im logged in for awhile and i try running banshee/rythmbox, or just system sounds, they stop, so i open up sound preferences and try "test" and get this

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

what does this mean, and how do i go about fixing this?

---

### Post by dynamethod on 2007-11-12
ok, as soon as i boot up the PC, i have no problems, but after 5 minutes i loose sound, anyone else having this problem? its driving me crazy, i have to boot every 5 minutes just to have sound?? no logs in /var/crash either :/

---

### Post by dynamethod on 2007-11-13
btw ive tried this thread: [http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is](http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is)


but it does not help fix my problem, heres the output of aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

and my output of lspci -v:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8113
        Flags: bus master, medium devsel, latency 32
        Memory at e0000000 (32-bit, non-prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: cff00000-cfffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
        Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
        Subsystem: ASUSTeK Computer Inc. Unknown device 810e
        Flags: bus master, medium devsel, latency 128, IRQ 21
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ASUSTeK Computer Inc. Unknown device 810f
        Flags: bus master, medium devsel, latency 64, IRQ 22
        I/O ports at d800 [size=256]
        I/O ports at d400 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 810e
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at cfefc000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 810e
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at cfefd000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 810e
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at cfefe000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 810e
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at cfeff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: ASUSTeK Computer Inc. Unknown device 810e
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at d000 [size=256]
        Memory at cfefb000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at cfec0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc R420 JK [Radeon X800] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0002
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 21
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at e000 [size=256]
        Memory at cffe0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at cffc0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc R420 [Radeon X800] (Secondary)
        Subsystem: ATI Technologies Inc Unknown device 0003
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Memory at cfff0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

and my lsmod output:

```
Module                  Size  Used by
iptable_filter          3968  0 
ip_tables              13924  1 iptable_filter
x_tables               16260  1 ip_tables
isofs                  36412  0 
udf                    87204  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
fglrx                 656352  29 
rfcomm                 42136  0 
l2cap                  26240  3 rfcomm
bluetooth              57060  2 rfcomm,l2cap
ppdev                  10244  0 
ipv6                  273892  14 
speedstep_lib           6404  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
container               5504  0 
video                  18060  0 
ac                      6148  0 
battery                11012  0 
lp                     12580  0 
snd_intel8x0           34972  2 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  1 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
joydev                 11328  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               8068  0 
psmouse                39952  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
xpad                    9988  0 
shpchp                 34580  0 
af_packet              24840  2 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sis_agp                10116  1 
snd                    54660  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  2 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
agpgart                35016  2 fglrx,sis_agp
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
usb_storage            73024  1 
ide_core              116804  1 usb_storage
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
libusual               18448  1 usb_storage
sg                     36764  0 
sr_mod                 17828  0 
sd_mod                 30336  5 
cdrom                  37536  1 sr_mod
pata_sis               15236  2 
ata_generic             8452  0 
libata                125168  2 pata_sis,ata_generic
scsi_mod              147084  5 usb_storage,sg,sr_mod,sd_mod,libata
sis900                 24960  0 
mii                     6528  1 sis900
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  7 usbhid,xpad,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

and my dmesg output:

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000004ffc0000 - 000000004ffd0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004ffd0000 - 0000000050000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 383MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 327616) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   327616
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   327616
[    0.000000] On node 0 totalpages: 327616
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 767 pages used for memmap
[    0.000000]   HighMem zone: 97473 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FB230 checksum 0
[    0.000000] ACPI: RSDP 000FB230, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 4FFC0000, 0030 (r1 A M I  OEMRSDT   1000606 MSFT       97)
[    0.000000] ACPI: FACP 4FFC0200, 0081 (r2 A M I  OEMFACP   1000606 MSFT       97)
[    0.000000] ACPI: DSDT 4FFC03F0, 3710 (r1  A0211 A0211044       44 INTL  2002026)
[    0.000000] ACPI: FACS 4FFD0000, 0040
[    0.000000] ACPI: APIC 4FFC0390, 005C (r1 A M I  OEMAPIC   1000606 MSFT       97)
[    0.000000] ACPI: OEMB 4FFD0040, 0040 (r1 A M I  AMI_OEM   1000606 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:af780000)
[    0.000000] Built 1 zonelists.  Total pages: 325057
[    0.000000] Kernel command line: root=UUID=b018d804-3c90-4fae-87fe-00d2c9c24231 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2993.368 MHz processor.
[   26.144993] Console: colour VGA+ 80x25
[   26.145812] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   26.146527] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.191994] Memory: 1287068k/1310464k available (2015k kernel code, 22292k reserved, 916k data, 364k init, 392960k highmem)
[   26.192009] virtual kernel memory layout:
[   26.192010]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   26.192011]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.192012]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   26.192013]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   26.192015]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   26.192016]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   26.192017]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   26.192020] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.192086] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   26.272093] Calibrating delay using timer specific routine.. 5990.44 BogoMIPS (lpj=11980883)
[   26.272141] Security Framework v1.0.0 initialized
[   26.272152] SELinux:  Disabled at boot.
[   26.272168] Mount-cache hash table entries: 512
[   26.272381] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   26.272390] monitor/mwait feature present.
[   26.272392] using mwait in idle threads.
[   26.272401] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   26.272403] CPU: L2 cache: 1024K
[   26.272407] CPU: Physical Processor ID: 0
[   26.272409] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000
[   26.272423] Compat vDSO mapped to ffffe000.
[   26.272446] Checking 'hlt' instruction... OK.
[   26.288283] SMP alternatives: switching to UP code
[   26.289019] Early unpacking initramfs... done
[   26.592437] ACPI: Core revision 20070126
[   26.592499] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.594450] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
[   26.594474] SMP alternatives: switching to SMP code
[   26.594656] Booting processor 1/1 eip 3000
[   26.605205] Initializing CPU#1
[   26.683967] Calibrating delay using timer specific routine.. 5986.72 BogoMIPS (lpj=11973453)
[   26.683979] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   26.683987] monitor/mwait feature present.
[   26.683995] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   26.683998] CPU: L2 cache: 1024K
[   26.684001] CPU: Physical Processor ID: 0
[   26.684003] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000
[   26.684390] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
[   26.684435] Total of 2 processors activated (11977.16 BogoMIPS).
[   26.684535] ENABLING IO-APIC IRQs
[   26.684717] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   26.724584] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   26.724625] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   26.724628] ...trying to set up timer as Virtual Wire IRQ... works.
[   26.872051] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   26.892064] Brought up 2 CPUs
[   27.255812] migration_cost=301
[   27.256051] Booting paravirtualized kernel on bare hardware
[   27.256130] Time: 10:44:35  Date: 10/14/107
[   27.256162] NET: Registered protocol family 16
[   27.256279] EISA bus registered
[   27.256286] ACPI: bus type pci registered
[   27.258415] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   27.258418] PCI: Using configuration type 1
[   27.258420] Setting up standard PCI resources
[   27.272762] ACPI: EC: Look up EC in DSDT
[   27.276213] ACPI: Interpreter enabled
[   27.276217] ACPI: (supports S0 S1 S3 S4 S5)
[   27.276239] ACPI: Using IOAPIC for interrupt routing
[   27.283989] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.284006] PCI: Probing PCI hardware (bus 00)
[   27.284830] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   27.289803] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[   27.289919] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   27.290027] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[   27.290132] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[   27.290237] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[   27.290342] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *10 11 12 14 15)
[   27.290450] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 7 10 11 12 14 15)
[   27.290560] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[   27.290664] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.290683] pnp: PnP ACPI init
[   27.290694] ACPI: bus type pnp registered
[   27.293998] pnp: PnP ACPI: found 12 devices
[   27.294001] ACPI: ACPI bus type pnp unregistered
[   27.294007] PnPBIOS: Disabled by ACPI PNP
[   27.294076] PCI: Using ACPI for IRQ routing
[   27.294079] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.303282] NET: Registered protocol family 8
[   27.303285] NET: Registered protocol family 20
[   27.303368] pnp: 00:06: ioport range 0x290-0x297 has been reserved
[   27.303375] pnp: 00:07: iomem range 0xffe80000-0xffefffff could not be reserved
[   27.303382] pnp: 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   27.303385] pnp: 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[   27.303388] pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   27.303395] pnp: 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   27.303398] pnp: 00:0b: iomem range 0xc0000-0xdffff could not be reserved
[   27.303401] pnp: 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[   27.303404] pnp: 00:0b: iomem range 0x100000-0x4fffffff could not be reserved
[   27.303805] Time: tsc clocksource has been installed.
[   27.333773] PCI: Bridge: 0000:00:01.0
[   27.333777]   IO window: e000-efff
[   27.333783]   MEM window: cff00000-cfffffff
[   27.333788]   PREFETCH window: d0000000-dfffffff
[   27.333814] NET: Registered protocol family 2
[   27.371958] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   27.372122] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   27.373640] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   27.374313] TCP: Hash tables configured (established 131072 bind 65536)
[   27.374318] TCP reno registered
[   27.384173] checking if image is initramfs... it is
[   27.835658] Switched to high resolution mode on CPU 0
[   27.835766] Switched to high resolution mode on CPU 1
[   27.984867] Freeing initrd memory: 7328k freed
[   27.985657] audit: initializing netlink socket (disabled)
[   27.985683] audit(1195037075.456:1): initialized
[   27.985816] highmem bounce pool size: 64 pages
[   27.988281] VFS: Disk quotas dquot_6.5.1
[   27.988350] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.988472] io scheduler noop registered
[   27.988475] io scheduler anticipatory registered
[   27.988477] io scheduler deadline registered
[   27.988494] io scheduler cfq registered (default)
[   28.495423] Boot video device is 0000:01:00.0
[   28.495627] isapnp: Scanning for PnP cards...
[   28.847176] isapnp: No Plug & Play device found
[   28.875164] Real Time Clock Driver v1.12ac
[   28.875359] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.875467] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.876269] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.877117] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.877405] input: Macintosh mouse button emulation as /class/input/input0
[   28.877501] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   28.877504] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   28.877820] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.877830] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.878005] mice: PS/2 mouse device common for all mice
[   28.878131] EISA: Probing bus 0 at eisa.0
[   28.878172] EISA: Detected 0 cards.
[   28.878414] TCP cubic registered
[   28.878431] NET: Registered protocol family 1
[   28.878459] Using IPI No-Shortcut mode
[   28.878646]   Magic number: 15:824:729
[   28.879379] Freeing unused kernel memory: 364k freed
[   28.911404] input: AT Translated Set 2 keyboard as /class/input/input1
[   30.117151] AppArmor: AppArmor initialized<5>audit(1195037077.456:2):  type=1505 info="AppArmor initialized" pid=1193
[   30.124886] fuse init (API version 7.8)
[   30.130919] Failure registering capabilities with primary security module.
[   30.170599] ACPI: Processor [CPU1] (supports 8 throttling states)
[   30.170626] ACPI: Processor [CPU2] (supports 8 throttling states)
[   30.799853] usbcore: registered new interface driver usbfs
[   30.799896] usbcore: registered new interface driver hub
[   30.799934] usbcore: registered new device driver usb
[   30.801151] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   30.801211] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   30.801230] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   30.801499] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   30.801525] ohci_hcd 0000:00:03.0: irq 16, io mem 0xcfefc000
[   30.892989] usb usb1: configuration #1 chosen from 1 choice
[   30.893036] hub 1-0:1.0: USB hub found
[   30.893053] hub 1-0:1.0: 3 ports detected
[   30.936237] sis900.c: v1.08.10 Apr. 2 2006
[   30.977498] SCSI subsystem initialized
[   30.986890] libata version 2.21 loaded.
[   30.995338] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[   30.995363] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   30.995579] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   30.995606] ohci_hcd 0000:00:03.1: irq 17, io mem 0xcfefd000
[   31.052729] usb usb2: configuration #1 chosen from 1 choice
[   31.052776] hub 2-0:1.0: USB hub found
[   31.052790] hub 2-0:1.0: 3 ports detected
[   31.154717] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[   31.154743] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   31.154796] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   31.154828] ohci_hcd 0000:00:03.2: irq 18, io mem 0xcfefe000
[   31.212654] usb usb3: configuration #1 chosen from 1 choice
[   31.212704] hub 3-0:1.0: USB hub found
[   31.212721] hub 3-0:1.0: 2 ports detected
[   31.298510] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   31.314873] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
[   31.314895] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   31.314948] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   31.315014] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   31.315032] ehci_hcd 0000:00:03.3: irq 19, io mem 0xcfeff000
[   31.474469] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.474635] usb usb4: configuration #1 chosen from 1 choice
[   31.474690] hub 4-0:1.0: USB hub found
[   31.474708] hub 4-0:1.0: 8 ports detected
[   31.578796] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 20
[   31.580133] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   31.591191] 0000:00:04.0: Using transceiver found at address 1 as default
[   31.592009] eth0: SiS 900 PCI Fast Ethernet at 0xd000, IRQ 20, 00:17:31:51:c5:5e.
[   31.595996] pata_sis 0000:00:02.5: version 0.5.1
[   31.596056] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 21
[   31.596267] scsi0 : pata_sis
[   31.596377] scsi1 : pata_sis
[   31.596590] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   31.596596] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   31.758752] ata1.00: ATA-7: Maxtor 2F030J0, VAM51JJ0, max UDMA/133
[   31.758757] ata1.00: 60058656 sectors, multi 16: LBA 
[   31.774718] ata1.00: configured for UDMA/133
[   31.882322] usb 1-1: device not accepting address 2, error -62
[   32.094486] ata2.01: ATAPI: HL-DT-STDVD-ROM GDR8162B, 0015, max UDMA/33
[   32.282420] ata2.01: configured for UDMA/33
[   32.282612] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 2F030J0   VAM5 PQ: 0 ANSI: 5
[   32.289171] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8162B 0015 PQ: 0 ANSI: 5
[   32.304993] sd 0:0:0:0: [sda] 60058656 512-byte hardware sectors (30750 MB)
[   32.305018] sd 0:0:0:0: [sda] Write Protect is off
[   32.305024] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.305055] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.305192] sd 0:0:0:0: [sda] 60058656 512-byte hardware sectors (30750 MB)
[   32.305216] sd 0:0:0:0: [sda] Write Protect is off
[   32.305221] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.305257] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.305265]  sda: sda1 sda2 sda3 < sda5 >
[   32.369731] sd 0:0:0:0: [sda] Attached SCSI disk
[   32.375177] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   32.375211] sr 1:0:1:0: Attached scsi generic sg1 type 5
[   32.401338] sr0: scsi3-mmc drive: 20x/48x cd/rw xa/form2 cdda tray
[   32.401346] Uniform CD-ROM driver Revision: 3.20
[   32.401437] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   32.562122] usb 4-1: new high speed USB device using ehci_hcd and address 2
[   32.706160] usb 4-1: configuration #1 chosen from 1 choice
[   32.826702] Attempting manual resume
[   32.826706] swsusp: Resume From Partition 8:5
[   32.826709] PM: Checking swsusp image.
[   32.826931] PM: Resume from disk failed.
[   32.882470] kjournald starting.  Commit interval 5 seconds
[   32.882489] EXT3-fs: mounted filesystem with ordered data mode.
[   33.074082] usbcore: registered new interface driver libusual
[   33.377845] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   33.589703] usb 2-1: configuration #1 chosen from 1 choice
[   33.893679] usb 1-2: new low speed USB device using ohci_hcd and address 4
[   33.905041] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.905049] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   34.103635] usb 1-2: configuration #1 chosen from 1 choice
[   34.254305] Initializing USB Mass Storage driver...
[   34.254441] scsi2 : SCSI emulation for USB Mass Storage devices
[   34.254514] usb-storage: device found at 2
[   34.254517] usb-storage: waiting for device to settle before scanning
[   34.254538] usbcore: registered new interface driver usb-storage
[   34.254542] USB Mass Storage support registered.
[   39.252299] usb-storage: device scan complete
[   39.252773] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.04 PQ: 0 ANSI: 0 CCS
[   39.254007] sd 2:0:0:0: [sdb] 499712 512-byte hardware sectors (256 MB)
[   39.254619] sd 2:0:0:0: [sdb] Write Protect is off
[   39.254623] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   39.254626] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   39.256617] sd 2:0:0:0: [sdb] 499712 512-byte hardware sectors (256 MB)
[   39.257241] sd 2:0:0:0: [sdb] Write Protect is off
[   39.257245] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   39.257246] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   39.257250]  sdb: sdb1
[   39.258067] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   39.258114] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   42.743735] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.762031] Linux agpgart interface v0.102 (c) Dave Jones
[   43.006851] agpgart: Detected SiS chipset - id:1633
[   43.015798] agpgart: AGP aperture is 128M @ 0xe0000000
[   43.076837] NET: Registered protocol family 17
[   43.101075] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.108041] usbcore: registered new interface driver xpad
[   43.108049] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   43.139760] eth0: Media Link On 100mbps full-duplex 
[   43.265494] usbcore: registered new interface driver hiddev
[   43.272279] input: PS/2+USB Mouse as /class/input/input2
[   43.272383] input: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:03.1-1
[   43.282005] input: 2-Axis,8-Button   as /class/input/input3
[   43.282066] input: USB HID v1.10 Joystick [2-Axis,8-Button  ] on usb-0000:00:03.0-2
[   43.282092] usbcore: registered new interface driver usbhid
[   43.282099] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   43.300965] input: PC Speaker as /class/input/input4
[   43.451134] parport_pc 00:05: reported by Plug and Play ACPI
[   43.451241] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   43.964466] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 22
[   44.286367] intel8x0_measure_ac97_clock: measured 54833 usecs
[   44.286371] intel8x0: clocking to 48000
[   44.837122] lp0: using parport0 (interrupt-driven).
[   44.892308] Adding 666656k swap on /dev/sda5.  Priority:-1 extents:1 across:666656k
[   45.339107] EXT3 FS on sda2, internal journal
[   46.577531] No dock devices found.
[   46.647099] input: Power Button (FF) as /class/input/input5
[   46.647131] ACPI: Power Button (FF) [PWRF]
[   46.647272] input: Power Button (CM) as /class/input/input6
[   46.647295] ACPI: Power Button (CM) [PWRB]
[   47.347406] NET: Registered protocol family 10
[   47.347590] lo: Disabled Privacy Extensions
[   48.611796] ppdev: user-space parallel port driver
[   48.774367] audit(1194990296.577:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4761 profile="/usr/sbin/cupsd"
[   48.977916] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   48.977924] apm: disabled - APM is not SMP safe.
[   49.196311] Failure registering capabilities with primary security module.
[   49.408361] Bluetooth: Core ver 2.11
[   49.408579] NET: Registered protocol family 31
[   49.408584] Bluetooth: HCI device and connection manager initialized
[   49.408590] Bluetooth: HCI socket layer initialized
[   49.428344] Bluetooth: L2CAP ver 2.8
[   49.428354] Bluetooth: L2CAP socket layer initialized
[   49.491529] Bluetooth: RFCOMM socket layer initialized
[   49.491562] Bluetooth: RFCOMM TTY layer initialized
[   49.491566] Bluetooth: RFCOMM ver 1.8
[   52.434697] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   52.438477] [fglrx] Maximum main memory to use for locked dma buffers: 1172 MBytes.
[   52.439950] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   52.530139] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   53.796099] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   53.796106] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   53.796111] [fglrx] AGP detected, AgpState   = 0x1f004e1b (hardware caps of chipset)
[   53.796877] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   53.796906] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   53.797901] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   53.797921] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[   53.809372] [fglrx] total      GART = 134217728
[   53.809384] [fglrx] free       GART = 118222848
[   53.809389] [fglrx] max single GART = 118222848
[   53.809393] [fglrx] total      LFB  = 134217728
[   53.809397] [fglrx] free       LFB  = 116387840
[   53.809400] [fglrx] max single LFB  = 116387840
[   53.809403] [fglrx] total      Inv  = 134217728
[   53.809406] [fglrx] free       Inv  = 134217728
[   53.809409] [fglrx] max single Inv  = 134217728
[   53.809411] [fglrx] total      TIM  = 0
[   57.738069] eth0: no IPv6 routers present
[10235.172534] ip_tables: (C) 2000-2006 Netfilter Core Team
[19247.633262] UDP: short packet: From 76.208.213.81:45411 44262/71 to 192.168.1.243:60010

```

ive done a fresh install of gutsy yesterday, but today i still have these problems :S

---

### Post by dynamethod on 2007-12-05
seems to happen when i try watch a video on youtube, then try to listen to some music on rythmbox i get "Couldn't start playback (null) "

---

