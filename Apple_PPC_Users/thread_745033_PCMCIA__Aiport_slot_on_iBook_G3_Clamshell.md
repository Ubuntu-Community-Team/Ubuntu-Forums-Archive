---
title: "PCMCIA / Aiport slot on iBook G3 Clamshell"
date: 2008-04-04
forum: Apple PPC Users
---

### Post by hever on 2008-04-04
Hi there,

On my iBook G3 Clamshell it seems that there is no PCMCIA / Airport Slot detected.
What must I do to get it working, what modules must be loaded or what config must be made ?

I enabled the pcmcia, pcmcia-cs, airport and some other kernel modules... Perhaps I missed some or some influences each other ?

I also tried to load the kernel with pci=assign-busses. (See yaboot config.)
How can I find out if this works or changed something in my system ?
Perhaps my yaboot config is not correct...

sudo pccardctl ls -v gives me nothing.

At the moment there is a PCMCIA WLAN Card with Prism chipset plugged into the slot. It gets power. Sure I'm interested getting this card working but actually I'm interested in getting the PCMCIA Slot working.

Perhaps someone will anser, it's not a generic slot. But so many people get so many different  non Airport or non Airport Chipset equal Cards working so I think I will it also get working with your help.

In my opinion the Slot must be listed itself, regardless what is plugged into it.

Here are a lot of informations and I hope, they help you helping me ;)

Thanks in advance ...

**/etc/yaboot.conf snip:**
```
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"
        pci=assign-busses

```

**hever@iBook:~$ sudo lshw -businfo**
```

Bus info          Device             Class      Description
===========================================================
                                     system     iBook (first generation)
                                     bus        Motherboard
                  /proc/device-tree  memory     
                                     memory     320MiB System memory
                                     memory     64MiB SDRAM
                                     memory     256MiB Memory bank
cpu@0                                processor  740/750
                                     memory     32KiB L1 Cache
                                     memory     512KiB L2 Cache (unified)
pci@0000:00:0b.0                     bridge     UniNorth AGP
pci@0000:00:10.0                     display    Rage Mobility L AGP 2x
pci@0001:10:0b.0                     bridge     UniNorth PCI
pci@0001:10:17.0                     generic    KeyLargo Mac I/O
ide@0             ide0               bus        IDE Channel 0
ide@0.0           /dev/hda           disk       6007MB IBM-DARA-206000
ide@0.0,1         /dev/hda1          volume     31KiB Apple partition map
ide@0.0,2         /dev/hda2          volume     977KiB Apple Bootstrap
ide@0.0,3         /dev/hda3          volume     5427MiB EXT3 volume
ide@0.0,4         /dev/hda4          volume     300MiB Linux swap volume
ide@1             ide1               bus        IDE Channel 0
ide@1.0           /dev/hdc           disk       MATSHITA CR-175
pci@0001:10:18.0                     bus        KeyLargo USB
pci@0001:10:19.0                     bus        KeyLargo USB
pci@0002:20:0b.0                     bridge     UniNorth Internal PCI
pci@0002:20:0f.0  eth0               network    UniNorth GMAC (Sun GEM)

```

**hever@iBook:~$ sudo lspci -v**
```
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
	Flags: bus master, 66MHz, medium devsel, latency 16
	Capabilities: [80] AGP version 1.0

0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage Mobility L AGP 2x (rev 64) (prog-if 00 [VGA controller])
	Flags: bus master, stepping, medium devsel, latency 255, IRQ 48
	Memory at 91000000 (32-bit, non-prefetchable) [size=16M]
	I/O ports at 0400 [size=256]
	Memory at 90000000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at 90020000 [disabled] [size=128K]
	Capabilities: [50] AGP version 1.0
	Capabilities: [5c] Power Management version 1

0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth PCI
	Flags: bus master, 66MHz, medium devsel, latency 16

0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 02)
	Flags: bus master, medium devsel, latency 16
	Memory at 80000000 (32-bit, non-prefetchable) [size=512K]

0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB (prog-if 10 [OHCI])
	Flags: bus master, medium devsel, latency 16, IRQ 27
	Memory at 80080000 (32-bit, non-prefetchable) [size=4K]

0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB (prog-if 10 [OHCI])
	Flags: medium devsel, IRQ 28

0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth Internal PCI
	Flags: bus master, 66MHz, medium devsel, latency 16

0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM)
	Flags: bus master, 66MHz, slow devsel, latency 16, IRQ 41
	Memory at f5200000 (32-bit, non-prefetchable) [size=2M]
	Expansion ROM at f5000000 [disabled] [size=1M]

```

[B]
hever@iBook:~$ sudo lsmod[/B]
```

Module                  Size  Used by
sg                     43268  0 
scsi_mod              192916  1 sg
ipv6                  310504  8 
af_packet              25956  2 
uinput                 11264  2 
ppdev                  11428  0 
lp                     13516  0 
parport                44816  2 ppdev,lp
cpufreq_userspace       5528  0 
cpufreq_conservative     9024  0 
cpufreq_powersave       2080  0 
cpufreq_ondemand        9792  0 
cpufreq_stats           6116  0 
iptable_filter          3136  0 
ip_tables              15624  1 iptable_filter
x_tables               17604  1 ip_tables
p80211                 37968  0 
ide_platform            3600  0 
ide_generic             1056  0 [permanent]
p54pci                 13024  0 
p54common              14816  1 p54pci
airport                 7520  0 
orinoco                45172  1 airport
hermes                  8352  2 airport,orinoco
mmc_core               60056  0 
mac80211              189896  2 p54pci,p54common
p8023                   2208  0 
8021q                  27180  0 
bridge                 66120  0 
ieee80211              36613  0 
ieee80211_crypt         6592  1 ieee80211
ath_hal               239774  0 
i82092                 13576  0 
pd6729                 13988  0 
yenta_socket           31628  0 
rsrc_nonstatic         13792  3 i82092,pd6729,yenta_socket
prism54                69324  0 
cfg80211               17008  1 mac80211
snd_vxpocket           16740  0 
pcmcia                 48528  1 snd_vxpocket
pcmcia_core            49176  5 i82092,pd6729,yenta_socket,rsrc_nonstatic,pcmcia
snd_vx_lib             38432  1 snd_vxpocket
apm_emu                 2496  0 
apm_emulation          10268  2 apm_emu
snd_powermac           50336  1 
snd_aoa_i2sbus         25060  0 
snd_pcm_oss            47488  0 
snd_mixer_oss          20896  1 snd_pcm_oss
snd_pcm                87812  4 snd_vx_lib,snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_page_alloc         12040  1 snd_pcm
snd_seq_dummy           4100  0 
snd_seq_oss            40820  0 
snd_seq_midi            9952  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      8288  2 snd_seq_oss,snd_seq_midi
snd_seq                62944  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26820  2 snd_pcm,snd_seq
snd_seq_device          9484  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pmac_zilog             21448  0 
serial_core            25600  1 pmac_zilog
snd                    70548  14 snd_vxpocket,snd_vx_lib,snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9028  1 snd
snd_aoa_soundbus        7524  1 snd_aoa_i2sbus
evdev                  14400  16 
uninorth_agp           11980  1 
agpgart                41244  1 uninorth_agp
ext3                  162888  1 
jbd                    57716  1 ext3
mbcache                 9632  1 ext3
ide_cd                 36996  0 
cdrom                  47196  1 ide_cd
ide_disk               19872  3 
ohci_hcd               38756  0 
sungem                 36260  0 
sungem_phy             13184  1 sungem
usbcore               173640  2 ohci_hcd
windfarm_core          14544  0 
fuse                   57620  1 
```

**hever@iBook:~$ sudo dmesg**
```

[    0.000000] Crash kernel location must be 0x2000000
[    0.000000] Reserving 0MB of memory at 32MB for crashkernel (System RAM: 320MB)
[    0.000000] Using PowerMac machine description
[    0.000000] Total memory = 320MB; using 1024kB for hash table (at cff00000)
[    0.000000] Linux version 2.6.24-12-powerpc (buildd@adare) (gcc version 4.1.3 20080308 (prerelease) (Ubuntu 4.1.2-21ubuntu1)) #1 Wed Mar 12 22:31:50 UTC 2008 (Ubuntu 2.6.24-12.22-powerpc)
[    0.000000] Found initrd at 0xc1a00000:0xc21d6000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0x03
[    0.000000] Mapped at 0xfdfc0000
[    0.000000] Found a Keylargo mac-io controller, rev: 2, mapped at 0xfdf40000
[    0.000000] PowerMac motherboard: iBook (first generation)
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    0.000000] console [udbg0] enabled
[    0.000000] Entering add_active_range(0, 0, 81920) 0 entries of 256 used
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->0
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->0
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->0
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=422, gen1=421
[    0.000000] nvram: Active bank is: 0
[    0.000000] nvram: OF partition at 0x210
[    0.000000] nvram: XP partition at 0x1220
[    0.000000] nvram: NR partition at 0x1320
[    0.000000] Top of RAM: 0x14000000, Total RAM: 0x14000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->    81920
[    0.000000]   Normal      81920 ->    81920
[    0.000000]   HighMem     81920 ->    81920
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    81920
[    0.000000] On node 0 totalpages: 81920
[    0.000000]   DMA zone: 640 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 81280 pages, LIFO batch:15
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 81280
[    0.000000] Kernel command line: root=/dev/hda3 ro quiet splash 
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] GMT Delta read from XPRAM: 60 minutes, DST: off
[    0.000000] time_init: decrementer frequency = 16.644216 MHz
[    0.000000] time_init: processor frequency   = 299.999997 MHz
[    0.000023] clocksource: timebase mult[f052dfb] shift[22] registered
[    0.000046] clockevent: decrementer mult[442] shift[16] cpu[0]
[    0.000268] Console: colour dummy device 80x25
[    0.000289] console handover: boot [udbg0] -> real [tty0]
[    0.002748] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.005240] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.058676] High memory: 0k
[    0.058696] Memory: 310972k/327680k available (3608k kernel code, 16360k reserved, 148k data, 351k bss, 208k init)
[    0.058889] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    0.058905] Calibrating delay loop... 33.15 BogoMIPS (lpj=66304)
[    0.140499] Security Framework initialized
[    0.140549] SELinux:  Disabled at boot.
[    0.140668] AppArmor: AppArmor initialized
[    0.140693] Failure registering capabilities with primary security module.
[    0.140735] Mount-cache hash table entries: 512
[    0.141607] device-tree: Duplicate name in /cpus/PowerPC,750@0, renamed to "l2-cache#1"
[    0.146112] net_namespace: 64 bytes
[    0.148482] NET: Registered protocol family 16
[    0.150703] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
[    0.150727]  channel 0 bus <multibus>
[    0.150738]  channel 1 bus <multibus>
[    0.150797] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
[    0.150812]  channel 0 bus <multibus>
[    0.150843] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000
[    0.150857]  channel 1 bus <multibus>
[    0.150868]  channel 2 bus <multibus>
[    0.151521] PCI: Probing PCI hardware
[    0.155580] PCI: Cannot allocate resource region 0 of device 0001:10:19.0
[    0.155658] Apple USB OHCI 0001:10:19.0 disabled by firmware
[    0.164910] NET: Registered protocol family 8
[    0.164933] NET: Registered protocol family 20
[    0.165362] AppArmor: AppArmor Filesystem Enabled
[    0.167780] NET: Registered protocol family 2
[    0.168536] Time: timebase clocksource has been installed.
[    0.168608] Switched to high resolution mode on CPU 0
[    0.200877] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.201936] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.203100] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[    0.203658] TCP: Hash tables configured (established 16384 bind 16384)
[    0.203675] TCP reno registered
[    0.213362] checking if image is initramfs... it is
[    3.778599] Freeing initrd memory: 6144k freed
[    3.781031] Freeing initrd memory: 1876k freed
[    3.781863] Thermal assist unit using timers, shrink_timer: 500 jiffies
[    3.784502] audit: initializing netlink socket (disabled)
[    3.784697] audit(1207298750.784:1): initialized
[    3.799062] VFS: Disk quotas dquot_6.5.1
[    3.799214] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.800377] io scheduler noop registered
[    3.800393] io scheduler anticipatory registered
[    3.800406] io scheduler deadline registered
[    3.800487] io scheduler cfq registered (default)
[    3.802107] PCI: Enabling device 0000:00:10.0 (0086 -> 0087)
[    3.802167] atyfb: using auxiliary register aperture
[    3.802673] atyfb: 3D RAGE Mobility L (Mach64 LN, AGP 2x) [0x4c4e rev 0x64]
[    3.802732] atyfb: 4M SDRAM (2:1) (32-bit), 14.31818 MHz XTAL, 230 MHz PLL, 70 Mhz MCLK, 53 MHz XCLK
[    3.807931] aty: Backlight initialized (atybl0)
[    3.808484] atyfb: monitor sense=0, mode 20
[    3.865427] Console: switching to colour frame buffer device 100x37
[    3.877701] atyfb: fb0: ATY Mach64 frame buffer device on PCI
[    4.131211] Generic RTC Driver v1.07
[    4.131498] Macintosh non-volatile memory driver v1.1
[    4.135633] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    4.136050] MacIO PCI driver attached to Keylargo chipset
[    4.142446] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    4.143329] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    4.143356] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.143483] adb: starting probe task...
[    4.395102] adb devices: [2]: 2 c4 [3]: 3 1 [7]: 7 1f
[    4.401626] ADB keyboard at 2, handler 1
[    4.401672] Detected ADB keyboard, type ISO, swapping keys.
[    4.402129] input: ADB keyboard as /devices/virtual/input/input1
[    4.412956] input: ADB Powerbook buttons as /devices/virtual/input/input2
[    4.439610] ADB mouse at 3, handler set to 4 (trackpad)
[    4.499374] input: ADB mouse as /devices/virtual/input/input3
[    4.499406] adb: finished probe task...
[    5.164564] ide0: Found Apple KeyLargo ATA-4 controller, bus ID 2, irq 19
[    5.164623] Probing IDE interface ide0...
[    6.124893] hda: IBM-DARA-206000, ATA DISK drive
[    6.124987] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    6.125330] hda: UDMA/33 mode selected
[    6.125820] ide0 at 0xd5018000-0xd5018007,0xd5018160 on irq 19
[    7.144563] ide1: Found Apple KeyLargo ATA-3 controller, bus ID 0, irq 20
[    7.144621] Probing IDE interface ide1...
[    7.880752] hdc: MATSHITA CR-175, ATAPI CD/DVD-ROM drive
[    7.880833] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    7.880970] hdc: MWDMA2 mode selected
[    7.881173] ide1 at 0xd501a000-0xd501a007,0xd501a160 on irq 20
[    8.900562] ide2: Found Apple KeyLargo ATA-3 controller, bus ID 1, irq 21
[    8.900620] Probing IDE interface ide2...
[    9.492979] mice: PS/2 mouse device common for all mice
[    9.493689] PowerMac i2c bus pmu 2 registered
[    9.493995] PowerMac i2c bus pmu 1 registered
[    9.494253] PowerMac i2c bus mac-io 0 registered
[    9.494523] PowerMac i2c bus uni-n 1 registered
[    9.494788] PowerMac i2c bus uni-n 0 registered
[    9.495386] NET: Registered protocol family 1
[    9.495667] registered taskstats version 1
[    9.496497] input: PMU as /devices/virtual/input/input4
[    9.504874] Registered led device: pmu-front-led
[    9.504915] Freeing unused kernel memory: 208k init
[   11.125776] atyfb: h_disp too large ffffffff(ff)
[   12.325391] fuse init (API version 7.9)
[   17.762506] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[   17.794539] usbcore: registered new interface driver usbfs
[   17.795116] usbcore: registered new interface driver hub
[   17.797689] usbcore: registered new device driver usb
[   17.810003] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.810275] PCI: Enabling device 0001:10:18.0 (0000 -> 0002)
[   17.810338] ohci_hcd 0001:10:18.0: OHCI Host Controller
[   17.811656] ohci_hcd 0001:10:18.0: new USB bus registered, assigned bus number 1
[   17.811768] ohci_hcd 0001:10:18.0: irq 27, io mem 0x80080000
[   17.833000] PHY ID: 406212, addr: 0
[   17.834559] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:0a:27:91:90:80
[   17.834575] eth0: Found BCM5201 PHY
[   17.884920] usb usb1: configuration #1 chosen from 1 choice
[   17.885090] hub 1-0:1.0: USB hub found
[   17.885140] hub 1-0:1.0: 2 ports detected
[   17.989274] Apple USB OHCI 0001:10:19.0 disabled by firmware
[   19.689237] hda: max request size: 128KiB
[   20.011944] hda: 11733120 sectors (6007 MB) w/418KiB Cache, CHS=12416/15/63
[   20.011983] hda: cache flushes not supported
[   20.012274]  hda: [mac] hda1 hda2 hda3 hda4
[   20.049991] hdc: ATAPI 24X CD-ROM drive, 128kB Cache
[   20.050039] Uniform CD-ROM driver Revision: 3.20
[   24.370766] Attempting manual resume
[   24.646700] kjournald starting.  Commit interval 5 seconds
[   24.646785] EXT3-fs: mounted filesystem with ordered data mode.
[   29.832751] eth0: Link is up at 100 Mbps, full-duplex.
[   47.914112] Linux agpgart interface v0.102
[   48.009374] agpgart: Detected Apple UniNorth chipset
[   48.009960] agpgart: configuring for size idx: 8
[   48.019480] agpgart: AGP aperture is 32M @ 0x0
[   61.734704] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   61.734893] pmac_zilog: serial modem detected
[   61.735044] ttyPZ0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Internal modem
[   61.737710] ttyPZ1 at MMIO 0x80013000 (irq = 50) is a Z85c30 ESCC - Serial port
[   71.122931] input: PowerMac Beep as /devices/pci0001:10/0001:10:17.0/input/input5
[   71.687144] apm_emu: PMU APM Emulation initialized.
[   72.970075] Loaded prism54 driver, version 1.2
[   73.424878] ath_hal: module license 'Proprietary' taints kernel.
[   73.439802] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413, REGOPS_FUNC)
[   73.678616] ieee80211_crypt: registered algorithm 'NULL'
[   73.715722] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   73.715759] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   73.975163] Bridge firewalling registered
[   74.167387] 802.1Q VLAN Support v1.8 Ben Greear <greearb@candelatech.com>
[   74.167464] All bugs added by David S. Miller <davem@redhat.com>
[   75.054790] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   75.075874] airport 0.15 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   75.309002] Probing IDE interface ide2...
[   76.941438] Adding 307924k swap on /dev/hda4.  Priority:-1 extents:1 across:307924k
[   78.301963] EXT3 FS on hda3, internal journal
[   83.380256] ip_tables: (C) 2000-2006 Netfilter Core Team
[   95.172061] eth0: Link is up at 100 Mbps, full-duplex.
[   95.172111] eth0: Pause is disabled
[   98.144141] hda: host max PIO4 wanted PIO0 selected PIO0
[  101.777962] lp: driver loaded but no devices found
[  103.450385] ppdev: user-space parallel port driver
[  105.173811] audit(1207302452.376:2): operation="inode_permission" request_mask="a::" denied_mask="a::" name="/dev/tty" pid=5120 profile="/usr/sbin/cupsd" namespace="default"
[  107.877543] input: Mouseemu virtual keyboard as /devices/virtual/input/input6
[  107.915824] input: Mouseemu virtual mouse as /devices/virtual/input/input7
[  135.271256] NET: Registered protocol family 17
[  139.363544] NET: Registered protocol family 10
[  139.367118] lo: Disabled Privacy Extensions
[  149.705805] eth0: no IPv6 routers present
[  806.509734] Unable to handle kernel paging request for data at address 0x48034000
[  806.509790] Faulting instruction address: 0xc0013c3c
[  806.509818] BUG: scheduling while atomic: tracker-extract/8435/0x10000001
[  806.509833] Call Trace:
[  806.509845] [ca811a10] [c0008cd8] show_stack+0x3c/0x194 (unreliable)
[  806.509910] [ca811a40] [c002fdcc] __schedule_bug+0x64/0x78
[  806.509953] [ca811a60] [c028ab30] schedule+0x2f0/0x2f4
[  806.509988] [ca811ab0] [c002fe04] __cond_resched+0x24/0x50
[  806.510013] [ca811ac0] [c028abf0] cond_resched+0x50/0x58
[  806.510034] [ca811ad0] [c028b378] mutex_lock+0x18/0x5c
[  806.510059] [ca811af0] [c001237c] die+0x1d8/0x254
[  806.510100] [ca811b20] [c001751c] bad_page_fault+0x90/0xd8
[  806.510137] [ca811b30] [c00145b4] handle_page_fault+0x7c/0x80
[  806.510158] --- Exception: 300 at __flush_dcache_icache+0x14/0x40
[  806.510193]     LR = update_mmu_cache+0x11c/0x120
[  806.510205] [ca811bf0] [c0081f3c] __pagevec_lru_add_active+0x11c/0x138 (unreliable)
[  806.510249] [ca811c10] [c008c1fc] handle_mm_fault+0x914/0xd68
[  806.510272] [ca811c60] [c008c77c] get_user_pages+0x12c/0x4f4
[  806.510293] [ca811cb0] [c00dd090] elf_core_dump+0xb48/0xd44
[  806.510326] [ca811d50] [c00a8e70] do_coredump+0x718/0x740
[  806.510349] [ca811e50] [c0042b20] get_signal_to_deliver+0x2e0/0x410
[  806.510376] [ca811e80] [c0009ff0] do_signal+0x48/0x26c
[  806.510402] [ca811f40] [c0014910] do_user_signal+0x74/0xc4
[  806.510422] --- Exception: 700 at 0xe416f20
[  806.510454]     LR = 0xe416ed8
[  806.522650] Oops: Kernel access of bad area, sig: 11 [#1]
[  806.522672] PowerMac
[  806.522680] Modules linked in: ipv6 af_packet uinput ppdev lp parport cpufreq_userspace cpufreq_conservative cpufreq_powersave cpufreq_ondemand cpufreq_stats iptable_filter ip_tables x_tables p80211 ide_platform ide_generic p54pci p54common airport orinoco hermes mmc_core mac80211 p8023 8021q bridge ieee80211 ieee80211_crypt ath_hal(P) i82092 pd6729 yenta_socket rsrc_nonstatic prism54 cfg80211 snd_vxpocket pcmcia pcmcia_core snd_vx_lib apm_emu apm_emulation snd_powermac snd_aoa_i2sbus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device pmac_zilog serial_core snd soundcore snd_aoa_soundbus evdev uninorth_agp agpgart ext3 jbd mbcache ide_cd cdrom ide_disk ohci_hcd sungem sungem_phy usbcore windfarm_core fuse
[  806.522972] NIP: c0013c3c LR: c0017930 CTR: 00000080
[  806.522994] REGS: ca811b40 TRAP: 0300   Tainted: P         (2.6.24-12-powerpc)
[  806.523008] MSR: 00009032 <EE,ME,IR,DR>  CR: 24822482  XER: 00000000
[  806.523040] DAR: 48034000, DSISR: 40000000
[  806.523054] TASK = c7a59940[8435] 'tracker-extract' THREAD: ca810000
[  806.523067] GPR00: c091b680 ca811bf0 c7a59940 48034000 00000080 0d6f5181 48034000 c03973a4 
[  806.523102] GPR08: c05c8ea0 c091b680 00000000 c041b000 00000020 1001c424 d2327200 d2cce400 
[  806.523135] GPR16: 0036c654 ffffffff c0390000 c03f0000 00000001 c03b0000 d2e3e480 0d6f5181 
[  806.523169] GPR24: c091b680 cae5b688 48034000 ca810000 cae5b688 48034000 0d6f5181 c05c8ea0 
[  806.523205] NIP [c0013c3c] __flush_dcache_icache+0x14/0x40
[  806.523245] LR [c0017930] update_mmu_cache+0x11c/0x120
[  806.523273] Call Trace:
[  806.523283] [ca811bf0] [c0081f3c] __pagevec_lru_add_active+0x11c/0x138 (unreliable)
[  806.523315] [ca811c10] [c008c1fc] handle_mm_fault+0x914/0xd68
[  806.523336] [ca811c60] [c008c77c] get_user_pages+0x12c/0x4f4
[  806.523358] [ca811cb0] [c00dd090] elf_core_dump+0xb48/0xd44
[  806.523382] [ca811d50] [c00a8e70] do_coredump+0x718/0x740
[  806.523402] [ca811e50] [c0042b20] get_signal_to_deliver+0x2e0/0x410
[  806.523425] [ca811e80] [c0009ff0] do_signal+0x48/0x26c
[  806.523453] [ca811f40] [c0014910] do_user_signal+0x74/0xc4
[  806.523472] --- Exception: 700 at 0xe416f20
[  806.523508]     LR = 0xe416ed8
[  806.523517] Instruction dump:
[  806.523531] 4d820020 7c8903a6 7c001bac 38630020 4200fff8 7c0004ac 4e800020 60000000 
[  806.523566] 54630026 38800080 7c8903a6 7c661b78 <7c00186c> 38630020 4200fff8 7c0004ac 
[  806.523619] ---[ end trace 84e350e1d8646847 ]---
[  806.523637] note: tracker-extract[8435] exited with preempt_count 1
[  806.523663] BUG: scheduling while atomic: tracker-extract/8435/0x10000001
[  806.523675] Call Trace:
[  806.523685] [ca8119b0] [c0008cd8] show_stack+0x3c/0x194 (unreliable)
[  806.523713] [ca8119e0] [c002fdcc] __schedule_bug+0x64/0x78
[  806.523745] [ca811a00] [c028ab30] schedule+0x2f0/0x2f4
[  806.523770] [ca811a50] [c002fe04] __cond_resched+0x24/0x50
[  806.523793] [ca811a60] [c028abf0] cond_resched+0x50/0x58
[  806.523815] [ca811a70] [c028b77c] down_read+0x18/0x50
[  806.523839] [ca811a90] [c0065d24] acct_collect+0x44/0x174
[  806.523885] [ca811ab0] [c0037c38] do_exit+0x138/0x78c
[  806.523911] [ca811af0] [c00123f8] kernel_bad_stack+0x0/0x4c
[  806.523935] [ca811b20] [c001751c] bad_page_fault+0x90/0xd8
[  806.523958] [ca811b30] [c00145b4] handle_page_fault+0x7c/0x80
[  806.523979] --- Exception: 300 at __flush_dcache_icache+0x14/0x40
[  806.524008]     LR = update_mmu_cache+0x11c/0x120
[  806.524020] [ca811bf0] [c0081f3c] __pagevec_lru_add_active+0x11c/0x138 (unreliable)
[  806.524050] [ca811c10] [c008c1fc] handle_mm_fault+0x914/0xd68
[  806.524071] [ca811c60] [c008c77c] get_user_pages+0x12c/0x4f4
[  806.524092] [ca811cb0] [c00dd090] elf_core_dump+0xb48/0xd44
[  806.524115] [ca811d50] [c00a8e70] do_coredump+0x718/0x740
[  806.524136] [ca811e50] [c0042b20] get_signal_to_deliver+0x2e0/0x410
[  806.524159] [ca811e80] [c0009ff0] do_signal+0x48/0x26c
[  806.524183] [ca811f40] [c0014910] do_user_signal+0x74/0xc4
[  806.524202] --- Exception: 700 at 0xe416f20
[  806.524233]     LR = 0xe416ed8
[ 1964.606396] SCSI subsystem initialized
```

---

