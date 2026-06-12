---
title: "Maverick rejecting wifi passwords but connects without passwords"
date: 2010-10-16
forum: Apple Hardware Users
---

### Post by jimwg on 2010-10-16
I've a 1.25mHz eMac running 10.4.11 and a 900mHz G3 iBook running Ubuntu 10.10. I can wifi connect with the iBook very well, but only without passwords. If I use 40 or 128 bit passwords in my eMac my iBook rejects them as "Bad Password." On the Ubuntu side, I've used passwords in Wicd Network Manager's WEP Paraphase, WEP Hex, and WEP Shared/Restricted modes but no dice. It's asthough Ubuntu is mis-decrypting incoming passwords from my eMac. I really don't want to connect in unsecured mode in this neighborhood, so can anyone offer me advice?

Thanks, truly!

JimWG

---

### Post by P4man on 2010-10-16
Im rather surprised you have ubuntu 10.10 running on a powerpc based mac. I thought support for that ended ages ago?

Anyway, its not uncommon for older and/or badly supported wifi cards to fail WEP and WPA. Usually Id suggest you give ndiswrapper a try, but I imagine on a powerpc that will never work. Perhaps this is solvable, if it is, someone is going the need to output of 

```
lspci
```

and possibly

```
lsusb
```

But I fear MACaddress protection on the access point is going to be your only real option.

---

### Post by jimwg on 2010-10-16
There're quite a few other home schools (and I guess charters too) in our local counties running Ubuntu on donated and older iMacs and iBooks, and the great thing about Linux is it doesn't make them feel obsolete or abandoned or forsaken! 
[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)



jimwg@icebook
~ $ lsmod
Module Size Used by
radeon 692092 0
ttm 46748 1 radeon
drm_kms_helper 24325 1 radeon
drm 142475 3 radeon,ttm,drm_kms_helper
uinput 10355 2
cpufreq_ondemand 10789 0
cpufreq_conservative 8952 0
cpufreq_userspace 5156 0
cpufreq_stats 5840 0
cpufreq_powersave 4138 0
parport_pc 28780 0
lp 10975 0
parport 32295 2 parport_pc,lp
sco 11560 2
bnep 13750 2
rfcomm 37794 0
l2cap 32868 4 bnep,rfcomm
crc16 4475 1 l2cap
bluetooth 52362 6 sco,bnep,rfcomm,l2cap
nfsd 243892 11
lockd 65427 1 nfsd
nfs_acl 5635 1 nfsd
auth_rpcgss 36656 1 nfsd
sunrpc 173447 10 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs 6642 1 nfsd
binfmt_misc 10371 1
fuse 57741 1
iptable_nat 8155 0
nf_nat 16339 1 iptable_nat
nf_conntrack_ipv4 13417 3 iptable_nat,nf_nat
nf_conntrack 52969 3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4 4391 1 nf_conntrack_ipv4
iptable_mangle 6113 0
iptable_filter 5502 0
ip_tables 13570 3 iptable_nat,iptable_mangle,iptable_filter
x_tables 14599 2 iptable_nat,ip_tables
pmu_battery 4706 0
power_supply 10795 1 pmu_battery
snd_powermac 57659 1
firewire_sbp2 16011 0
scsi_mod 126838 1 firewire_sbp2
loop 15945 0
snd_aoa_i2sbus 20629 0
snd_pcm_oss 42143 0
snd_mixer_oss 19030 1 snd_pcm_oss
snd_pcm 65033 3 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_page_alloc 9045 1 snd_pcm
snd_seq_midi 8216 0
snd_rawmidi 21199 1 snd_seq_midi
snd_seq_midi_event 7956 1 snd_seq_midi
snd_seq 51409 2 snd_seq_midi,snd_seq_midi_event
snd_timer 20956 2 snd_pcm,snd_seq
snd_seq_device 8405 3 snd_seq_midi,snd_rawmidi,snd_seq
snd 52643 11 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 8003 1 snd
evdev 11760 31
airport 6597 0
orinoco 61191 1 airport
cfg80211 117489 1 orinoco
rfkill 17994 3 bluetooth,cfg80211
snd_aoa_soundbus 6669 1 snd_aoa_i2sbus
ext3 124692 2
jbd 40847 1 ext3
mbcache 8286 1 ext3
usbhid 39928 0
hid 68185 1 usbhid
ohci_hcd 35272 0
ehci_hcd 42854 0
firewire_ohci 25992 0
ide_cd_mod 28561 0
sungem 30865 0
firewire_core 44186 2 firewire_sbp2,firewire_ohci
cdrom 36699 1 ide_cd_mod
sungem_phy 12982 1 sungem
crc_itu_t 4495 1 firewire_core
usbcore 131839 4 usbhid,ohci_hcd,ehci_hcd
nls_base 8693 1 usbcore
i2c_powermac 6651 0
jimwg@icebook
~ $ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 047d:104b Kensington
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jimwg@icebook
~ $ dmesg
[ 0.000000] Using PowerMac machine description
[ 0.000000] Total memory = 640MB; using 2048kB for hash table (at cfe00000)
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.32-5-powerpc (Debian 2.6.32-23) (dannf@debian.org) (gcc version 4.3.5 (Debian 4.3.5-3) ) #1 Sat Sep 18 02:18:04 UTC 2010
[ 0.000000] Found initrd at 0xc1b00000:0xc246b000
[ 0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0xc0
[ 0.000000] Mapped at 0xff7c0000
[ 0.000000] Found a Pangea mac-io controller, rev: 0, mapped at 0xff740000
[ 0.000000] Processor NAP mode on idle enabled.
[ 0.000000] PowerMac motherboard: iBook 2 rev. 2
[ 0.000000] via-pmu: Server Mode is disabled
[ 0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[ 0.000000] bootconsole [udbg0] enabled
[ 0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->0
[ 0.000000] PCI host bridge /pci@f0000000 ranges:
[ 0.000000] MEM 0x00000000f1000000..0x00000000f1ffffff -> 0x00000000f1000000
[ 0.000000] IO 0x00000000f0000000..0x00000000f07fffff -> 0x0000000000000000
[ 0.000000] MEM 0x0000000090000000..0x000000009fffffff -> 0x0000000090000000
[ 0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->0
[ 0.000000] PCI host bridge /pci@f2000000 (primary) ranges:
[ 0.000000] MEM 0x00000000f3000000..0x00000000f3ffffff -> 0x00000000f3000000
[ 0.000000] IO 0x00000000f2000000..0x00000000f27fffff -> 0x0000000000000000
[ 0.000000] MEM 0x0000000080000000..0x000000008fffffff -> 0x0000000080000000
[ 0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->0
[ 0.000000] PCI host bridge /pci@f4000000 ranges:
[ 0.000000] MEM 0x00000000f5000000..0x00000000f5ffffff -> 0x00000000f5000000
[ 0.000000] IO 0x00000000f4000000..0x00000000f47fffff -> 0x0000000000000000
[ 0.000000] nvram: Checking bank 0...
[ 0.000000] nvram: gen0=1538, gen1=1537
[ 0.000000] nvram: Active bank is: 0
[ 0.000000] nvram: OF partition at 0x410
[ 0.000000] nvram: XP partition at 0x1020
[ 0.000000] nvram: NR partition at 0x1120
[ 0.000000] Top of RAM: 0x28000000, Total RAM: 0x28000000
[ 0.000000] Memory hole size: 0MB
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000000 -> 0x00028000
[ 0.000000] Normal 0x00028000 -> 0x00028000
[ 0.000000] HighMem 0x00028000 -> 0x00028000
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[1] active PFN ranges
[ 0.000000] 0: 0x00000000 -> 0x00028000
[ 0.000000] On node 0 totalpages: 163840
[ 0.000000] free_area_init_node: node 0, pgdat c0504308, node_mem_map c0599000
[ 0.000000] DMA zone: 1280 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 162560 pages, LIFO batch:31
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 162560
[ 0.000000] Kernel command line: root=/dev/hda14 ro
[ 0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[ 0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.000000] High memory: 0k
[ 0.000000] Memory: 631424k/655360k available (4924k kernel code, 23536k reserved, 276k data, 478k bss, 232k init)
[ 0.000000] Kernel virtual memory layout:
[ 0.000000] * 0xfffef000..0xfffff000 : fixmap
[ 0.000000] * 0xff800000..0xffc00000 : highmem PTEs
[ 0.000000] * 0xfde72000..0xff800000 : early ioremap
[ 0.000000] * 0xe9000000..0xfde72000 : vmalloc & ioremap
[ 0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[ 0.000000] Hierarchical RCU implementation.
[ 0.000000] NR_IRQS:512
[ 0.000000] mpic: Setting up MPIC " MPIC 1 " version 1.2 at 80040000, max 4 CPUs
[ 0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[ 0.000000] mpic: Initializing for 64 sources
[ 0.000000] irq: irq 55 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 55
[ 0.000000] GMT Delta read from XPRAM: 0 minutes, DST: off
[ 0.000000] time_init: decrementer frequency = 24.835245 MHz
[ 0.000000] time_init: processor frequency = 900.000000 MHz
[ 0.000000] clocksource: timebase mult[a10fb9b] shift[22] registered
[ 0.000000] clockevent: decrementer mult[65b9a45] shift[32] cpu[0]
[ 0.000000] Console: colour dummy device 80x25
[ 0.000000] console [tty0] enabled, bootconsole disabled
[ 0.000000] irq: irq 22 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 22
[ 0.000000] irq: irq 23 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 23
[ 0.001804] Security Framework initialized
[ 0.001838] SELinux: Disabled at boot.
[ 0.001859] Mount-cache hash table entries: 512
[ 0.002369] device-tree: Duplicate name in /cpus/PowerPC,750@0, renamed to "l2-cache#1"
[ 0.003463] device-tree: Duplicate name in /pci@f2000000/mac-io@17/gpio@50, renamed to "extint-gpio4@5c#1"
[ 0.004514] Initializing cgroup subsys ns
[ 0.004576] Initializing cgroup subsys cpuacct
[ 0.004587] Initializing cgroup subsys devices
[ 0.004597] Initializing cgroup subsys freezer
[ 0.004607] Initializing cgroup subsys net_cls
[ 0.006065] devtmpfs: initialized
[ 0.006944] regulator: core version 0.5
[ 0.007148] NET: Registered protocol family 16
[ 0.007993] irq: irq 42 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 42
[ 0.008054] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
[ 0.008071] channel 0 bus <multibus>
[ 0.008079] channel 1 bus <multibus>
[ 0.008119] irq: irq 26 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 26
[ 0.008141] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
[ 0.008154] channel 0 bus <multibus>
[ 0.008173] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
[ 0.008185] channel 1 bus <multibus>
[ 0.008193] channel 2 bus <multibus>
[ 0.008251] irq: irq 25 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 25
[ 0.008279] irq: irq 47 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 47
[ 0.008430] PCI: Probing PCI hardware
[ 0.008733] pci 0000:00:10.0: reg 10 32bit mmio pref: [0x98000000-0x9fffffff]
[ 0.008743] pci 0000:00:10.0: reg 14 io port: [0x400-0x4ff]
[ 0.008752] pci 0000:00:10.0: reg 18 32bit mmio: [0x90000000-0x9000ffff]
[ 0.008770] pci 0000:00:10.0: reg 30 32bit mmio pref: [0x90020000-0x9003ffff]
[ 0.008795] pci 0000:00:10.0: supports D1 D2
[ 0.008854] irq: irq 48 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 48
[ 0.009141] pci 0001:10:17.0: reg 10 32bit mmio: [0x80000000-0x8007ffff]
[ 0.009213] pci 0001:10:18.0: reg 10 32bit mmio: [0x80081000-0x80081fff]
[ 0.009256] pci 0001:10:18.0: supports D1 D2
[ 0.009262] pci 0001:10:18.0: PME# supported from D1 D2 D3hot
[ 0.009281] pci 0001:10:18.0: PME# disabled
[ 0.009335] pci 0001:10:19.0: reg 10 32bit mmio: [0x80080000-0x80080fff]
[ 0.009377] pci 0001:10:19.0: supports D1 D2
[ 0.009382] pci 0001:10:19.0: PME# supported from D1 D2 D3hot
[ 0.009396] pci 0001:10:19.0: PME# disabled
[ 0.009448] irq: irq 27 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 27
[ 0.009472] irq: irq 28 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 28
[ 0.009815] pci 0002:20:0e.0: reg 10 32bit mmio: [0xf5000000-0xf5000fff]
[ 0.009848] pci 0002:20:0e.0: supports D1 D2
[ 0.009854] pci 0002:20:0e.0: PME# supported from D0 D1 D2 D3hot
[ 0.009869] pci 0002:20:0e.0: PME# disabled
[ 0.009910] pci 0002:20:0f.0: reg 10 32bit mmio: [0xf5200000-0xf53fffff]
[ 0.009932] pci 0002:20:0f.0: reg 30 32bit mmio pref: [0xf5100000-0xf51fffff]
[ 0.009984] irq: irq 40 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 40
[ 0.010006] irq: irq 41 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 41
[ 0.010233] PCI 0000:00 Cannot reserve Legacy IO [0x802000-0x802fff]
[ 0.010252] pci_bus 0000:00: resource 0 io: [0x802000-0x1001fff]
[ 0.010259] pci_bus 0000:00: resource 1 mem: [0xf1000000-0xf1ffffff]
[ 0.010265] pci_bus 0000:00: resource 2 mem: [0x90000000-0x9fffffff]
[ 0.010273] pci_bus 0001:10: resource 0 io: [0x00-0x7fffff]
[ 0.010280] pci_bus 0001:10: resource 1 mem: [0xf3000000-0xf3ffffff]
[ 0.010286] pci_bus 0001:10: resource 2 mem: [0x80000000-0x8fffffff]
[ 0.010294] pci_bus 0002:20: resource 0 io: [0xff7fe000-0xffffdfff]
[ 0.010300] pci_bus 0002:20: resource 1 mem: [0xf5000000-0xf5ffffff]
[ 0.013434] bio: create slab <bio-0> at 0
[ 0.013785] vgaarb: device added: PCI:0000:00:10.0,decodes=io+mem,owns=mem,locks=none
[ 0.013813] vgaarb: loaded
[ 0.014169] Switching to clocksource timebase
[ 0.018442] NET: Registered protocol family 2
[ 0.018685] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.020146] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.027252] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.029055] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.029073] TCP reno registered
[ 0.029503] NET: Registered protocol family 1
[ 0.029847] Unpacking initramfs...
[ 0.662703] Freeing initrd memory: 9644k freed
[ 0.664198] Thermal assist unit using timers, shrink_timer: 500 jiffies
[ 0.664687] Registering PowerMac CPU frequency driver
[ 0.664705] Low: 400 Mhz, High: 900 Mhz, Boot: 900 Mhz
[ 0.665164] audit: initializing netlink socket (disabled)
[ 0.665231] type=2000 audit(1287227835.660:1): initialized
[ 0.674604] VFS: Disk quotas dquot_6.5.2
[ 0.674825] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 0.674946] msgmni has been set to 1252
[ 0.675626] alg: No test for stdrng (krng)
[ 0.675743] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[ 0.675765] io scheduler noop registered
[ 0.675775] io scheduler anticipatory registered
[ 0.675787] io scheduler deadline registered
[ 0.675897] io scheduler cfq registered (default)
[ 0.676308] radeonfb 0000:00:10.0: enabling device (0086 -> 0087)
[ 0.870098] radeonfb 0000:00:10.0: Invalid ROM contents
[ 0.870117] radeonfb (0000:00:10.0): Invalid ROM signature 0 should be 0xaa55
[ 0.870129] radeonfb: Retrieved PLL infos from Open Firmware
[ 0.870145] radeonfb: Reference=27.00 MHz (RefDiv=12) Memory=180.00 Mhz, System=180.00 MHz
[ 0.870163] radeonfb: PLL min 12000 max 35000
[ 0.967233] i2c i2c-2: unable to read EDID block.
[ 1.119222] i2c i2c-2: unable to read EDID block.
[ 1.271221] i2c i2c-2: unable to read EDID block.
[ 1.423221] i2c i2c-3: unable to read EDID block.
[ 1.575221] i2c i2c-3: unable to read EDID block.
[ 1.727222] i2c i2c-3: unable to read EDID block.
[ 1.783180] radeonfb: Monitor 1 type LCD found
[ 1.783191] radeonfb: EDID probed
[ 1.783200] radeonfb: Monitor 2 type no found
[ 1.783228] radeonfb: Using Firmware dividers 0x000600ad from PPLL 0
[ 1.942196] radeonfb: Dynamic Clock Power Management enabled
[ 1.970040] Console: switching to colour frame buffer device 128x48
[ 1.984518] radeonfb: Backlight initialized (radeonbl0)
[ 1.984692] radeonfb (0000:00:10.0): ATI Radeon 4c57 "LW"
[ 1.988585] Generic non-volatile memory driver v1.1
[ 1.988817] Linux agpgart interface v0.103
[ 1.988998] agpgart-uninorth 0000:00:0b.0: Apple UniNorth/Pangea chipset
[ 1.991781] agpgart-uninorth 0000:00:0b.0: configuring for size idx: 64
[ 1.992081] agpgart-uninorth 0000:00:0b.0: AGP aperture is 256M @ 0x0
[ 1.992377] Serial: 8250/16550 driver, 4 ports, IRQ sharing disabled
[ 1.992993] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[ 1.993254] ttyPZ0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Serial port
[ 1.993568] ttyPZ1 at MMIO 0x80013000 (irq = 23) is a Z85c30 ESCC - Serial port
[ 1.993889] Serial: MPC52xx PSC UART driver
[ 1.994132] MacIO PCI driver attached to Pangea chipset
[ 1.994763] irq: irq 32 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 32
[ 1.995008] irq: irq 19 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 19
[ 1.995026] irq: irq 11 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 16
[ 1.995104] irq: irq 57 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 57
[ 1.995188] irq: irq 5 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 17
[ 1.995205] irq: irq 6 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 18
[ 1.995338] irq: irq 7 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 20
[ 1.995354] irq: irq 8 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 21
[ 1.995720] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[ 1.996325] Uniform Multi-Platform E-IDE driver
[ 1.996884] adb: starting probe task...
[ 2.247693] adb devices: [2]: 2 c3 [3]: 3 1 [7]: 7 1f
[ 2.254415] ADB keyboard at 2, handler 1
[ 2.254565] Detected ADB keyboard, type ANSI.
[ 2.260109] input: ADB keyboard as /devices/virtual/input/input1
[ 2.265682] input: ADB Powerbook buttons as /devices/virtual/input/input2
[ 2.285937] ADB mouse at 3, handler set to 4 (trackpad)
[ 2.350848] input: ADB mouse as /devices/virtual/input/input3
[ 2.356230] adb: finished probe task...
[ 3.014204] ide-pmac: Found Apple KeyLargo ATA-4 controller (macio), bus ID 2, irq 19
[ 3.019923] Probing IDE interface ide0...
[ 3.602514] hda: FUJITSU MHS2040AT D, ATA DISK drive
[ 4.110198] hdb: TOSHIBA DVD-ROM SD-R2412, ATAPI CD/DVD-ROM drive
[ 4.116086] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[ 4.152205] hda: host side 80-wire cable detection failed, limiting max speed to UDMA33
[ 4.158132] hda: UDMA/33 mode selected
[ 4.200712] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[ 4.200765] hdb: MWDMA2 mode selected
[ 4.206690] ide0 at 0xe902e000-0xe902e070,0xe902e160 on irq 19
[ 4.212754] ide-gd driver 1.18
[ 4.218564] hda: max request size: 512KiB
[ 4.606326] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=16383/255/63
[ 4.612883] hda: cache flushes supported
[ 4.619091] hda: [mac] hda1 hda2 hda3 hda4 hda5 hda6 hda7 hda8 hda9 hda10 hda11 hda12 hda13 hda14 hda15 hda16 hda17
[ 4.635110] mice: PS/2 mouse device common for all mice
[ 4.642021] rtc-generic rtc-generic: rtc core: registered rtc-generic as rtc0
[ 4.649770] TCP cubic registered
[ 4.657027] NET: Registered protocol family 10
[ 4.665019] lo: Disabled Privacy Extensions
[ 4.672619] Mobile IPv6
[ 4.679503] NET: Registered protocol family 17
[ 4.686686] PM: Resume from disk failed.
[ 4.686733] registered taskstats version 1
[ 4.693975] input: PMU as /devices/virtual/input/input4
[ 4.700935] Registered led device: pmu-led::front
[ 4.707978] rtc-generic rtc-generic: setting system clock to 2010-10-16 11:17:20 UTC (1287227840)
[ 4.715052] Initalizing network drop monitor service
[ 4.722148] Freeing unused kernel memory: 232k init
[ 4.818466] udev: starting version 161
[ 5.102943] PowerMac i2c bus pmu 2 registered
[ 5.201765] PowerMac i2c bus pmu 1 registered
[ 5.233702] PowerMac i2c bus mac-io 0 registered
[ 5.241263] PowerMac i2c bus uni-n 1 registered
[ 5.285431] PowerMac i2c bus uni-n 0 registered
[ 5.312316] usbcore: registered new interface driver usbfs
[ 5.331601] usbcore: registered new interface driver hub
[ 5.348989] usbcore: registered new device driver usb
[ 5.370937] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[ 5.414534] ide-cd driver 5.00
[ 5.455339] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 5.463052] PHY ID: 4061e4, addr: 0
[ 5.465252] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:0a:95:7e:75:14
[ 5.471972] eth0: Found BCM5221 PHY
[ 5.481009] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 5.488958] ohci_hcd 0001:10:18.0: enabling device (0000 -> 0002)
[ 5.503089] ohci_hcd 0001:10:18.0: OHCI Host Controller
[ 5.510027] ohci_hcd 0001:10:18.0: new USB bus registered, assigned bus number 1
[ 5.517159] ide-cd: hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[ 5.523804] Uniform CD-ROM driver Revision: 3.20
[ 5.568915] ohci_hcd 0001:10:18.0: irq 27, io mem 0x80081000
[ 5.582478] firewire_ohci: Added fw-ohci device 0002:20:0e.0, OHCI version 1.0
[ 5.655211] usb usb1: New USB device found, idVendor=1d6b, idProduct=0001
[ 5.661926] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 5.668443] usb usb1: Product: OHCI Host Controller
[ 5.674946] usb usb1: Manufacturer: Linux 2.6.32-5-powerpc ohci_hcd
[ 5.681481] usb usb1: SerialNumber: 0001:10:18.0
[ 5.689460] usb usb1: configuration #1 chosen from 1 choice
[ 5.696773] hub 1-0:1.0: USB hub found
[ 5.703038] hub 1-0:1.0: 2 ports detected
[ 5.709649] ohci_hcd 0001:10:19.0: enabling device (0000 -> 0002)
[ 5.715794] ohci_hcd 0001:10:19.0: OHCI Host Controller
[ 5.724958] ohci_hcd 0001:10:19.0: new USB bus registered, assigned bus number 2
[ 5.731375] ohci_hcd 0001:10:19.0: irq 28, io mem 0x80080000
[ 5.810515] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[ 5.816794] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 5.822936] usb usb2: Product: OHCI Host Controller
[ 5.829018] usb usb2: Manufacturer: Linux 2.6.32-5-powerpc ohci_hcd
[ 5.835151] usb usb2: SerialNumber: 0001:10:19.0
[ 5.842413] usb usb2: configuration #1 chosen from 1 choice
[ 5.848859] hub 2-0:1.0: USB hub found
[ 5.854892] hub 2-0:1.0: 2 ports detected
[ 6.082550] firewire_core: created device fw0: GUID 000a95fffe7e7514, S400
[ 6.090059] usb 1-1: new low speed USB device using ohci_hcd and address 2
[ 6.302485] usb 1-1: New USB device found, idVendor=047d, idProduct=104b
[ 6.308815] usb 1-1: New USB device strings: Mfr=0, Product=3, SerialNumber=0
[ 6.315026] usb 1-1: Product: Kensington Ci95m Wireless Mouse with Nano Receiver
[ 6.323693] usb 1-1: configuration #1 chosen from 1 choice
[ 6.384543] usbcore: registered new interface driver hiddev
[ 6.398070] input: Kensington Ci95m Wireless Mouse with Nano Receiver as /devices/pci0001:10/0001:10:18.0/usb1/1-1/1-1:1.0/input/input5
[ 6.412449] generic-usb 0003:047D:104B.0001: input,hidraw0: USB HID v1.11 Mouse [Kensington Ci95m Wireless Mouse with Nano Receiver] on usb-0001:10:18.0-1/input0
[ 6.427381] usbcore: registered new interface driver usbhid
[ 6.436001] usbhid: v2.6:USB HID core driver
[ 7.227063] PM: Starting manual resume from disk
[ 7.234563] PM: Resume from partition 3:9
[ 7.234567] PM: Checking hibernation image.
[ 7.256434] PM: Error -22 checking image file
[ 7.256439] PM: Resume from disk failed.
[ 7.356832] EXT3-fs: INFO: recovery required on readonly filesystem.
[ 7.364400] EXT3-fs: write access will be enabled during recovery.
[ 8.640112] kjournald starting. Commit interval 5 seconds
[ 8.647698] EXT3-fs: recovery complete.
[ 8.655659] EXT3-fs: mounted filesystem with ordered data mode.
[ 11.852041] udev: starting version 161
[ 13.050912] cfg80211: Using static regulatory domain info
[ 13.058823] cfg80211: Regulatory domain: US
[ 13.066609] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 13.074566] (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[ 13.082477] (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[ 13.090318] (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[ 13.098029] (5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[ 13.105634] (5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[ 13.113147] (5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[ 13.128376] cfg80211: Calling CRDA for country: US
[ 13.238276] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[ 13.283181] airport 0.15 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[ 13.283289] airport: Physical address 80030000
[ 14.486906] airport 0.00030000:radio: Hardware identity 0005:0001:0001:0002
[ 14.494775] airport 0.00030000:radio: Station identity 001f:0001:0008:0046
[ 14.502291] airport 0.00030000:radio: Firmware determined as Lucent/Agere 8.70
[ 14.510533] airport 0.00030000:radio: firmware: requesting agere_sta_fw.bin
[ 14.607495] airport 0.00030000:radio: firmware: requesting agere_sta_fw.bin
[ 14.634043] airport 0.00030000:radio: Cannot find firmware agere_sta_fw.bin
[ 14.641552] airport 0.00030000:radio: Hardware identity 0005:0001:0001:0002
[ 14.648890] airport 0.00030000:radio: Station identity 001f:0001:0008:0046
[ 14.656008] airport 0.00030000:radio: Firmware determined as Lucent/Agere 8.70
[ 14.662923] airport 0.00030000:radio: Ad-hoc demo mode supported
[ 14.669580] airport 0.00030000:radio: IEEE standard IBSS ad-hoc mode supported
[ 14.676045] airport 0.00030000:radio: WEP supported, 104-bit key
[ 18.369959] Adding 130040k swap on /dev/hda9. Priority:-1 extents:1 across:130040k
[ 18.640049] EXT3 FS on hda14, internal journal
[ 18.970724] loop: module loaded
[ 19.212543] SCSI subsystem initialized
[ 19.309160] irq: irq 1 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 24
[ 19.309220] irq: irq 2 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 29
[ 19.484272] irq: irq 58 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 58
[ 19.900922] input: PowerMac Beep as /devices/pci0001:10/0001:10:17.0/input/input6
[ 21.468811] kjournald starting. Commit interval 5 seconds
[ 21.475618] EXT3 FS on hda11, internal journal
[ 21.484108] EXT3-fs: mounted filesystem with ordered data mode.
[ 23.278001] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 23.580026] nf_conntrack version 0.5.0 (10026 buckets, 40104 max)
[ 23.590787] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[ 23.597735] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[ 23.604613] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[ 24.134006] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 25.946010] fuse init (API version 7.13)
[ 26.902958] RPC: Registered udp transport module.
[ 26.904077] RPC: Registered tcp transport module.
[ 26.905075] RPC: Registered tcp NFSv4.1 backchannel transport module.
[ 27.373452] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[ 27.611008] svc: failed to register lockdv1 RPC service (errno 97).
[ 27.617438] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[ 27.650394] NFSD: starting 90-second grace period
[ 30.645333] Bluetooth: Core ver 2.15
[ 30.646969] NET: Registered protocol family 31
[ 30.648029] Bluetooth: HCI device and connection manager initialized
[ 30.649033] Bluetooth: HCI socket layer initialized
[ 30.909496] Bluetooth: L2CAP ver 2.14
[ 30.910622] Bluetooth: L2CAP socket layer initialized
[ 30.954050] Bluetooth: RFCOMM TTY layer initialized
[ 30.955764] Bluetooth: RFCOMM socket layer initialized
[ 30.956780] Bluetooth: RFCOMM ver 1.11
[ 31.084916] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 31.086003] Bluetooth: BNEP filters: protocol multicast
[ 31.193322] Bluetooth: SCO (Voice Link) ver 0.6
[ 31.194400] Bluetooth: SCO socket layer initialized
[ 32.559560] lp: driver loaded but no devices found
[ 38.307185] ondemand governor failed, too long transition latency of HW, fallback to performance governor
[ 39.467985] radeonfb 0000:00:10.0: Invalid ROM contents
[ 39.468181] radeonfb 0000:00:10.0: Invalid ROM contents
[ 39.798852] [drm] Initialized drm 1.1.0 20060810
[ 40.444137] [drm] radeon kernel modesetting enabled.
[ 40.566795] input: Mouseemu virtual keyboard as /devices/virtual/input/input7
[ 40.569797] input: Mouseemu virtual mouse as /devices/virtual/input/input8
[ 53.727413] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 54.255272] radeonfb 0000:00:10.0: Invalid ROM contents
[ 54.256148] radeonfb 0000:00:10.0: Invalid ROM contents
[ 55.588002] eth1: New link status: Connected (0001)
[ 55.588935] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 66.294391] eth1: no IPv6 routers present
[ 140.282507] eth1: New link status: AP Out of Range (0004)
[ 140.385726] eth1: New link status: AP In Range (0005)
[ 142.550549] eth1: New link status: AP Out of Range (0004)
[ 142.721768] eth1: New link status: AP In Range (0005)
[ 144.992674] eth1: New link status: AP Out of Range (0004)
[ 145.092774] eth1: New link status: AP In Range (0005)
[ 174.485048] eth1: New link status: AP Out of Range (0004)
[ 195.355450] eth1: New link status: AP In Range (0005)
[ 203.157403] eth1: New link status: AP Out of Range (0004)
[ 203.248322] eth1: New link status: AP In Range (0005)
[ 209.198986] eth1: New link status: AP Out of Range (0004)
[ 209.292969] eth1: New link status: AP In Range (0005)
[ 211.444538] eth1: New link status: AP Out of Range (0004)
[ 211.529725] eth1: New link status: AP In Range (0005)
[ 213.681122] eth1: New link status: AP Out of Range (0004)
[ 213.771334] eth1: New link status: AP In Range (0005)
[ 215.921870] eth1: New link status: AP Out of Range (0004)
[ 216.009033] eth1: New link status: AP In Range (0005)
[ 218.158493] eth1: New link status: AP Out of Range (0004)
[ 218.252851] eth1: New link status: AP In Range (0005)
[ 220.407414] eth1: New link status: AP Out of Range (0004)
[ 220.505825] eth1: New link status: AP In Range (0005)
[ 222.715170] eth1: New link status: AP Out of Range (0004)
[ 222.867552] eth1: New link status: AP In Range (0005)
[ 225.018132] eth1: New link status: AP Out of Range (0004)
[ 225.113519] eth1: New link status: AP In Range (0005)
[ 227.268097] eth1: New link status: AP Out of Range (0004)
[ 227.366514] eth1: New link status: AP In Range (0005)
[ 229.524190] eth1: New link status: AP Out of Range (0004)
[ 239.979526] eth1: New link status: AP In Range (0005)
[ 242.131058] eth1: New link status: AP Out of Range (0004)
[ 242.215132] eth1: New link status: AP In Range (0005)
[ 244.367745] eth1: New link status: AP Out of Range (0004)
[ 254.806649] eth1: New link status: AP In Range (0005)
[ 256.958172] eth1: New link status: AP Out of Range (0004)
[ 257.054506] eth1: New link status: AP In Range (0005)
[ 259.207084] eth1: New link status: AP Out of Range (0004)
[ 259.294202] eth1: New link status: AP In Range (0005)
[ 261.440582] eth1: New link status: AP Out of Range (0004)
[ 261.528762] eth1: New link status: AP In Range (0005)
[ 263.684402] eth1: New link status: AP Out of Range (0004)
[ 263.780785] eth1: New link status: AP In Range (0005)
[ 265.939523] eth1: New link status: AP Out of Range (0004)
[ 266.032803] eth1: New link status: AP In Range (0005)
[ 268.192538] eth1: New link status: AP Out of Range (0004)
[ 268.285824] eth1: New link status: AP In Range (0005)
[ 270.440370] eth1: New link status: AP Out of Range (0004)
[ 270.530614] eth1: New link status: AP In Range (0005)
[ 272.682167] eth1: New link status: AP Out of Range (0004)
[ 272.766223] eth1: New link status: AP In Range (0005)
[ 274.912626] eth1: New link status: AP Out of Range (0004)
[ 274.999744] eth1: New link status: AP In Range (0005)
[ 277.192693] eth1: New link status: AP Out of Range (0004)
[ 277.286684] eth1: New link status: AP In Range (0005)
[ 279.454710] eth1: New link status: AP Out of Range (0004)
[ 279.541848] eth1: New link status: AP In Range (0005)
[ 281.692394] eth1: New link status: AP Out of Range (0004)
[ 281.776445] eth1: New link status: AP In Range (0005)
[ 283.921814] eth1: New link status: AP Out of Range (0004)
[ 284.008944] eth1: New link status: AP In Range (0005)
[ 286.154322] eth1: New link status: AP Out of Range (0004)
[ 286.255799] eth1: New link status: AP In Range (0005)
[ 288.457974] eth1: New link status: AP Out of Range (0004)
[ 288.551934] eth1: New link status: AP In Range (0005)
[ 290.705512] eth1: New link status: AP Out of Range (0004)
[ 290.805991] eth1: New link status: AP In Range (0005)
[ 292.968765] eth1: New link status: AP Out of Range (0004)
[ 293.059022] eth1: New link status: AP In Range (0005)
[ 295.210575] eth1: New link status: AP Out of Range (0004)
[ 295.294612] eth1: New link status: AP In Range (0005)
[ 297.464623] eth1: New link status: AP Out of Range (0004)
[ 297.560984] eth1: New link status: AP In Range (0005)
[ 299.715638] eth1: New link status: AP Out of Range (0004)
[ 299.799673] eth1: New link status: AP In Range (0005)
[ 302.076644] eth1: New link status: AP Out of Range (0004)
[ 302.170614] eth1: New link status: AP In Range (0005)
[ 304.327292] eth1: New link status: AP Out of Range (0004)
[ 304.411361] eth1: New link status: AP In Range (0005)
[ 306.590538] eth1: New link status: AP Out of Range (0004)
[ 306.726871] eth1: New link status: AP In Range (0005)
[ 308.878432] eth1: New link status: AP Out of Range (0004)
[ 319.320481] eth1: New link status: AP In Range (0005)
[ 322.454407] eth1: New link status: AP Out of Range (0004)
[ 323.563283] eth1: New link status: AP In Range (0005)
[ 325.833957] eth1: New link status: AP Out of Range (0004)
[ 325.931011] eth1: New link status: AP In Range (0005)
[ 328.081531] eth1: New link status: AP Out of Range (0004)
[ 328.165590] eth1: New link status: AP In Range (0005)
[ 330.441557] eth1: New link status: AP Out of Range (0004)
[ 334.622580] eth1: New link status: AP In Range (0005)
[ 340.784231] eth1: New link status: AP Out of Range (0004)
[ 342.814665] eth1: New link status: AP In Range (0005)
[ 344.974196] eth1: New link status: AP Out of Range (0004)
[ 348.446791] eth1: New link status: AP In Range (0005)
[ 350.716853] eth1: New link status: AP Out of Range (0004)
[ 357.048449] eth1: New link status: AP In Range (0005)
[ 359.727977] eth1: New link status: AP Out of Range (0004)
[ 359.812743] eth1: New link status: AP In Range (0005)
[ 361.971437] eth1: New link status: AP Out of Range (0004)
[ 362.058550] eth1: New link status: AP In Range (0005)
[ 364.210078] eth1: New link status: AP Out of Range (0004)
[ 364.312601] eth1: New link status: AP In Range (0005)
[ 367.511134] eth1: New link status: AP Out of Range (0004)
[ 367.694280] eth1: New link status: AP In Range (0005)
[ 371.299697] eth1: New link status: AP Out of Range (0004)
[ 371.445986] eth1: New link status: AP In Range (0005)
[ 373.597485] eth1: New link status: AP Out of Range (0004)
[ 389.100095] eth1: New link status: AP In Range (0005)
[ 536.557823] eth1: New link status: AP Out of Range (0004)
[ 536.666818] eth1: New link status: AP In Range (0005)
[ 964.799779] eth1: New link status: AP Out of Range (0004)
[ 964.892350] eth1: New link status: AP In Range (0005)
[ 1335.901856] eth1: New link status: AP Out of Range (0004)
[ 1335.995383] eth1: New link status: AP In Range (0005)
[ 1849.751254] eth1: New link status: AP Out of Range (0004)
[ 1849.836709] eth1: New link status: AP In Range (0005)
[ 2094.060525] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2094.271452] eth1: New link status: Connected (0001)
[ 2094.272371] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 2094.288741] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2095.040293] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2095.195343] eth1: New link status: Connected (0001)
[ 2095.196246] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 2097.461155] eth1: New link status: Disconnected (0002)
[ 2097.571821] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2097.971763] eth1: New link status: Connected (0001)
[ 2105.870053] eth1: no IPv6 routers present
[ 2120.023651] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2123.109931] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2123.192840] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2123.336265] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2123.924763] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2124.070355] eth1: New link status: Connected (0001)
[ 2124.071252] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 2126.095483] eth1: New link status: Disconnected (0002)
[ 2126.203504] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2126.837843] eth1: New link status: Connected (0001)
[ 2134.450267] eth1: no IPv6 routers present
jimwg@icebook
~ $


Phew! There you go!

Thanks for your analysis!

JimWG

---

### Post by P4man on 2010-10-16
Maybe this thread can help:
[http://www.mail-archive.com/networkmanager-list@gnome.org/msg15489.html](http://www.mail-archive.com/networkmanager-list@gnome.org/msg15489.html)

Seems like the same issue. You could try the wpa_supplicant approach (even for wep apparently)

---

### Post by jimwg on 2010-10-25
Re: Ubuntu 10.04 Wicd "Bad Password" issue with DWA-125
Please please help me out with this issue that I've been struggling with since Sept. I've a G3 900mhZ iBook running Wicd on Ubuntu 10.04 and a eMac running 10.4.11. My iBook can only link with the eMac via an unsecured (no password) connection. Otherwise all I get are "Bad Passwords" or less commonly "Can't find I.P. address". I've done the WEP Key Maker route and it doesn't work for me but I think I just might be doing things wrong. On my eMac's Shared Airport panel I only have WEP encryption options to create WEP key lengths at 128 or 40 bits. WEP Key Maker states you you must insert a "$" at the beginning of its key to work in Airport, but if I do that the key becomes 13 digits long and Airport rejects that. So even if use that 13-digit length key in the WEP HEX panel on Wicd it doesn't work. Or is there a "trick" to this? Could it be that Wicd expects WPA instead of WEP but my iBook's Airport card only takes WEP? I know I sound confused and I guess I am! I REALLY don't want to use an unsecured connection in a densely populated city, so I'd me beholden to anyone who can help me step by step!

Thanks!

JimWG

---

