---
title: "Cd's dont work ahhhhhhh!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by yellowpagesguy on 2007-06-20
I got this Laptop like a month ago its a dell latitude L400. Today i tried to play a CD but it wouldnt work and said couldnt be mounted or something!

Im relatively new to Linux, im a former Microsoft XP addict :KS :KS

lool :lolflag: , anyhow i was wondering if i could just get some help..Cheers :popcorn:

 ):P

---

### Post by Damanther on 2007-06-20
Can you post the contents of your /etc/fstab file.

Also need the output of 'dmesg' after you have tried inserting the CD

---

### Post by LunatikOwl on 2007-06-20
Does it happen to be in UDF format?

If so Linux doesn't natively support some UDF  versions, try 'sudo apt-get install udftools'.

---

### Post by EagleRock on 2007-06-20
Also, try a different CD.  Try to pop in the Ubuntu install CD you used and see if it mounts automatically.  Also, are you referring to an audio CD or a data CD?

---

### Post by mlentink on 2007-06-20
> **yellowpagesguy said:**
> Today i tried to play a CD but it wouldnt work
What kind of cd were you trying to play? Data? Music? Video? Game?

---

### Post by yellowpagesguy on 2007-06-20
Demanther


for /etc/fstab file it said permission denied  :confused:



ok dmesg says

[     0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000ea400 size: 0000000000015c00 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000000fef0000 end: 000000000fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000fff0000 size: 000000000000fc00 end: 000000000ffffc00 type: 3
[    0.000000] copy_e820_map() start: 000000000ffffc00 size: 0000000000000400 end: 0000000010000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fffea400 size: 0000000000015c00 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ea400 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffea400 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65520) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65520
[    0.000000]   HighMem     65520 ->    65520
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65520
[    0.000000] On node 0 totalpages: 65520
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 479 pages used for memmap
[    0.000000]   Normal zone: 60945 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6ed0
[    0.000000] ACPI: RSDT (v001 GATEWA SOLO3300 0x20000202  LTP 0x00000000) @ 0x0fffc6a9
[    0.000000] ACPI: FADT (v001 DELL   Atlas    0x20000202 PTL  0x000f4240) @ 0x0ffffb65
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x20000202  LTP 0x00000001) @ 0x0ffffbd9
[    0.000000] ACPI: DSDT (v001    PTL    BX-TJ 0x20000202 MSFT 0x01000007) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:effea400)
[    0.000000] Detected 497.864 MHz processor.
[   15.174948] Built 1 zonelists.  Total pages: 65009
[   15.174961] Kernel command line: root=UUID=aa8c49a2-b24a-4e19-afd5-a2993f82ab09 ro quiet splash
[   15.175730] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   15.175758] mapped APIC to ffffd000 (0120a000)
[   15.175771] Enabling fast FPU save and restore... done.
[   15.175782] Enabling unmasked SIMD FPU exception support... done.
[   15.175812] Initializing CPU#0
[   15.175936] PID hash table entries: 1024 (order: 10, 4096 bytes)
[   15.177746] Console: colour VGA+ 80x25
[   15.178300] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.178876] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   15.210972] Memory: 248888k/262080k available (1992k kernel code, 12704k reserved, 900k data, 328k init, 0k highmem)
[   15.211016] virtual kernel memory layout:
[   15.211021]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   15.211027]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.211033]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   15.211039]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[   15.211045]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   15.211050]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   15.211056]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   15.211070] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.287898] Calibrating delay using timer specific routine.. 996.76 BogoMIPS (lpj=1993538)
[   15.288052] Security Framework v1.0.0 initialized
[   15.288077] SELinux:  Disabled at boot.
[   15.288142] Mount-cache hash table entries: 512
[   15.288582] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   15.288622] CPU: L1 I cache: 16K, L1 D cache: 16K
[   15.288634] CPU: L2 cache: 256K
[   15.288645] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   15.288682] Compat vDSO mapped to ffffe000.
[   15.288705] Remapping vsyscall page to ffffe000
[   15.288738] Checking 'hlt' instruction... OK.
[   15.304190] SMP alternatives: switching to UP code
[   15.304734] Freeing SMP alternatives: 11k freed
[   15.305380] Early unpacking initramfs... done
[   16.504128] ACPI: Core revision 20060707
[   16.505979] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   16.512032] ACPI: setting ELCR to 0200 (from 0c08)
[   16.527411] CPU0: Intel Pentium III (Coppermine) stepping 06
[   16.527442] SMP motherboard not detected.
[   16.527452] Local APIC not detected. Using dummy APIC emulation.
[   16.527582] Brought up 1 CPUs
[   16.528427] Booting paravirtualized kernel on bare hardware
[   16.528627] Time:  2:59:56  Date: 05/15/107
[   16.528736] NET: Registered protocol family 16
[   16.529042] EISA bus registered
[   16.529058] ACPI: bus type pci registered
[   16.531385] PCI: PCI BIOS revision 2.10 entry at 0xfd9c5, last bus=1
[   16.531395] PCI: Using configuration type 1
[   16.531402] Setting up standard PCI resources
[   16.551820] ACPI: Interpreter enabled
[   16.551835] ACPI: Using PIC for interrupt routing
[   16.553022] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.553045] PCI: Probing PCI hardware (bus 00)
[   16.554042] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[   16.554057] PCI quirk: region 2180-218f claimed by PIIX4 SMB
[   16.554073] PIIX4 devres I PIO at 0398-0399
[   16.554507] Boot video device is 0000:01:00.0
[   16.554727] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.558265] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   16.559357] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[   16.560323] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[   16.561168] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 14 15)
[   16.561995] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[   16.608795] ACPI: Device [FDDA] status [00000008]: functional but not present; setting present
[   16.612331] ACPI: Device [CDRM] status [00000008]: functional but not present; setting present
[   16.622693] ACPI: Power Resource [PFN0] (off)
[   16.623114] ACPI: Power Resource [PFN1] (off)
[   16.623269] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.623307] pnp: PnP ACPI init
[   16.709337] pnp: PnP ACPI: found 12 devices
[   16.709354] PnPBIOS: Disabled by ACPI PNP
[   16.709527] PCI: Using ACPI for IRQ routing
[   16.709539] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.711768] NET: Registered protocol family 8
[   16.711777] NET: Registered protocol family 20
[   16.712302] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   16.712317] pnp: 00:06: ioport range 0x8000-0x803f could not be reserved
[   16.712330] pnp: 00:06: ioport range 0x2180-0x218f has been reserved
[   16.712342] pnp: 00:06: ioport range 0x398-0x399 has been reserved
[   16.713428] PCI: Bridge: 0000:00:01.0
[   16.713440]   IO window: e000-efff
[   16.713453]   MEM window: fd000000-fecfffff
[   16.713464]   PREFETCH window: 28000000-280fffff
[   16.713477] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[   16.713487]   IO window: 00001000-000010ff
[   16.713497]   IO window: 00001400-000014ff
[   16.713509]   PREFETCH window: 20000000-23ffffff
[   16.713520]   MEM window: 24000000-27ffffff
[   16.714359] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   16.714372] PCI: setting IRQ 10 as level-triggered
[   16.714382] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   16.714484] NET: Registered protocol family 2
[   16.747581] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   16.747850] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   16.748062] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   16.748174] TCP: Hash tables configured (established 8192 bind 4096)
[   16.748185] TCP reno registered
[   16.759764] checking if image is initramfs... it is
[   19.065284] Freeing initrd memory: 6750k freed
[   19.065913] Simple Boot Flag at 0x63 set to 0x1
[   19.066552] audit: initializing netlink socket (disabled)
[   19.066591] audit(1181876399.044:1): initialized
[   19.067040] VFS: Disk quotas dquot_6.5.1
[   19.067108] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.067268] io scheduler noop registered
[   19.067279] io scheduler anticipatory registered
[   19.067288] io scheduler deadline registered
[   19.067327] io scheduler cfq registered (default)
[   19.067354] Limiting direct PCI/PCI transfers.
[   19.068085] isapnp: Scanning for PnP cards...
[   19.421088] isapnp: No Plug & Play device found
[   19.531315] Real Time Clock Driver v1.12ac
[   19.531482] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.531719] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.534024] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.535006] mice: PS/2 mouse device common for all mice
[   19.537110] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.537929] input: Macintosh mouse button emulation as /class/input/input0
[   19.538088] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   19.538104] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   19.538740] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[   19.542152] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.542173] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.542648] EISA: Probing bus 0 at eisa.0
[   19.542670] Cannot allocate resource for EISA slot 1
[   19.542707] Cannot allocate resource for EISA slot 8
[   19.542715] EISA: Detected 0 cards.
[   19.572998] TCP cubic registered
[   19.573026] NET: Registered protocol family 1
[   19.573100] Using IPI No-Shortcut mode
[   19.573283] ACPI: (supports S0 S3 S4 S5)
[   19.573419]   Magic number: 11:776:965
[   19.573455]   hash matches device ttyb6
[   19.574277] Time: tsc clocksource has been installed.
[   19.574821] Freeing unused kernel memory: 328k freed
[   19.592266] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.487706] Capability LSM initialized
[   22.517230] ACPI: Transitioning device [FAN0] to D3
[   22.517243] ACPI: Transitioning device [FAN0] to D3
[   22.517256] ACPI: Fan [FAN0] (off)
[   22.517452] ACPI: Transitioning device [FAN1] to D3
[   22.517461] ACPI: Transitioning device [FAN1] to D3
[   22.517473] ACPI: Fan [FAN1] (off)
[   22.537454] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   22.537474] ACPI: Processor [CPU0] (supports 8 throttling states)
[   22.560650] ACPI: Thermal Zone [THRM] (32 C)
[   26.684649] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   26.684687] PIIX4: chipset revision 1
[   26.684696] PIIX4: not 100% native mode: will probe irqs later
[   26.684717]     ide0: BM-DMA at 0xfcd0-0xfcd7, BIOS settings: hda:pio, hdb:pio
[   26.684748]     ide1: BM-DMA at 0xfcd8-0xfcdf, BIOS settings: hdc:pio, hdd:pio
[   26.684770] Probing IDE interface ide0...
[   26.744872] usbcore: registered new interface driver usbfs
[   26.744947] usbcore: registered new interface driver hub
[   26.745029] usbcore: registered new device driver usb
[   26.750617] USB Universal Host Controller Interface driver v3.0
[   27.087559] hda: IBM-DJSA-210, ATA DISK drive
[   27.383758] Floppy drive(s): fd0 is 1.44M
[   27.403613] FDC 0 is a National Semiconductor PC87306
[   12.284000] Time: acpi_pm clocksource has been installed.
[   12.556000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   12.872000] Probing IDE interface ide1...
[   13.476000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   13.476000] PCI: setting IRQ 11 as level-triggered
[   13.476000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   13.476000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   13.476000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   13.476000] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000fce0
[   13.480000] usb usb1: configuration #1 chosen from 1 choice
[   13.480000] hub 1-0:1.0: USB hub found
[   13.480000] hub 1-0:1.0: 2 ports detected
[   13.484000] SCSI subsystem initialized
[   13.524000] libata version 2.20 loaded.
[   13.584000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   13.584000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[   13.584000] 0000:00:0d.0: 3Com PCI 3c905C Tornado at d0858c00.
[   13.620000] hub 1-0:1.0: over-current change on port 2
[   13.680000] hda: max request size: 128KiB
[   13.696000] hda: 19640880 sectors (10056 MB) w/384KiB Cache, CHS=19485/16/63, UDMA(33)
[   13.696000] hda: cache flushes not supported
[   13.696000]  hda: hda1 hda2 < hda5 >
[   14.148000] Attempting manual resume
[   14.148000] swsusp: Resume From Partition 3:5
[   14.148000] PM: Checking swsusp image.
[   14.180000] PM: Resume from disk failed.
[   14.272000] kjournald starting.  Commit interval 5 seconds
[   14.272000] EXT3-fs: mounted filesystem with ordered data mode.
[   43.964000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.984000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.820000] Linux agpgart interface v0.102 (c) Dave Jones
[   44.984000] Yenta: CardBus bridge found at 0000:00:0a.0 [1028:00dc]
[   44.984000] Yenta: Enabling burst memory read transactions
[   44.984000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   44.984000] Yenta: Routing CardBus interrupts to PCI
[   44.984000] Yenta TI: socket 0000:00:0a.0, mfunc 0x01201272, devctl 0x64
[   45.216000] Yenta: ISA IRQ mask 0x00b8, PCI irq 10
[   45.216000] Socket status: 30000010
[   45.240000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   45.244000] agpgart: Detected an Intel 440BX Chipset.
[   45.248000] agpgart: AGP aperture is 64M @ 0xf8000000
[   45.852000] pccard: PCMCIA card inserted into slot 0
[   47.180000] input: PC Speaker as /class/input/input2
[   47.460000] parport: PnPBIOS parport detected.
[   47.460000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   47.976000] Synaptics Touchpad, model: 1, fw: 4.1, id: 0x8848a1, caps: 0x0/0x0
[   48.020000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   48.372000] cs: IO port probe 0x100-0x3af: clean.
[   48.372000] cs: IO port probe 0x3e0-0x4ff: clean.
[   48.376000] cs: IO port probe 0x820-0x8ff: clean.
[   48.376000] cs: IO port probe 0xc00-0xcf7: clean.
[   48.376000] cs: IO port probe 0xa00-0xaff: clean.
[   48.376000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   48.384000] pcmcia: registering new device pcmcia0.0
[   48.780000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   48.780000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   49.140000] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   49.152000] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   49.236000] eth1: Hardware identity 0002:0002:0005:0000
[   49.236000] eth1: Station identity  001f:0001:0008:002a
[   49.236000] eth1: Firmware determined as Lucent/Agere 8.42
[   49.236000] eth1: Ad-hoc demo mode supported
[   49.236000] eth1: IEEE standard IBSS ad-hoc mode supported
[   49.236000] eth1: WEP supported, 104-bit key
[   49.236000] eth1: MAC address 00:02:2D:51:BA:5E
[   49.236000] eth1: Station name "HERMES I"
[   49.236000] eth1: ready
[   49.236000] eth1: orinoco_cs at 0.0, irq 3, io 0x0100-0x013f
[   49.456000] gameport: CS4281 Gameport is pci0000:00:08.0/gameport0, speed 2386kHz
[   49.856000] lp0: using parport0 (interrupt-driven).
[   49.952000] Adding 433712k swap on /dev/disk/by-uuid/f2c9011c-9922-4caa-a16f-5b30f4515593.  Priority:-1 extents:1 across:433712k
[   50.072000] EXT3 FS on hda1, internal journal
[   52.536000] NET: Registered protocol family 17
[   57.396000] ACPI: AC Adapter [ACAD] (on-line)
[   57.580000] ACPI: Battery Slot [BAT1] (battery present)
[   57.740000] input: Power Button (FF) as /class/input/input4
[   57.740000] ACPI: Power Button (FF) [PWRF]
[   57.784000] input: Lid Switch as /class/input/input5
[   57.784000] ACPI: Lid Switch [LID]
[   57.804000] input: Sleep Button (CM) as /class/input/input6
[   57.804000] ACPI: Sleep Button (CM) [SBTN]
[   58.272000] Using specific hotkey driver
[   58.368000] No dock devices found.
[   58.536000] ibm_acpi: IBM ThinkPad ACPI Extras v0.13
[   58.536000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   58.968000] pcc_acpi: loading...
[   69.364000] eth0:  setting half-duplex.
[   69.540000] eth1: New link status: Connected (0001)
[   73.856000] ppdev: user-space parallel port driver
[   77.404000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   77.404000] apm: overridden by ACPI.
[   79.896000] vboxdrv: Trying to deactivate NMI watchdog permanently...
[   79.896000] vboxdrv: Successfully done.
[   82.224000] Bluetooth: Core ver 2.11
[   82.224000] NET: Registered protocol family 31
[   82.224000] Bluetooth: HCI device and connection manager initialized
[   82.224000] Bluetooth: HCI socket layer initialized
[   82.352000] Bluetooth: L2CAP ver 2.8
[   82.352000] Bluetooth: L2CAP socket layer initialized
[   82.368000] Bluetooth: RFCOMM socket layer initialized
[   82.368000] Bluetooth: RFCOMM TTY layer initialized
[   82.368000] Bluetooth: RFCOMM ver 1.8
[  106.176000] NET: Registered protocol family 10
[  106.180000] lo: Disabled Privacy Extensions
[  106.180000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  116.292000] eth1: no IPv6 routers present
[  126.988000] eth1: New link status: Disconnected (0002)
[  127.176000] eth1: New link status: Connected (0001)
[  148.084000] eth1: no IPv6 routers present
[ 2408.324000] ACPI: Device [FDDA] status [00000008]: functional but not present; setting present

---

### Post by yellowpagesguy on 2007-06-20
> **EagleRock said:**
> Also, try a different CD.  Try to pop in the Ubuntu install CD you used and see if it mounts automatically.  Also, are you referring to an audio CD or a data CD?

thing is i dont have the cd and i didnt install ubuntu on the laptop see i got it off Ebay

---

### Post by LunatikOwl on 2007-06-20
a) You need super-user privileges to view fstab, try sudo cat /etc/fstab. 
b) have you tried to mount the cd manually? type 'man mount' to see how to use it.
- you may need to sudo in order to mount.
by [DEVICE] they mean /dev/cdrom, /dev/scd0... in short your cd device /dev file. 
-t [type] means udf or iso9660 for data and i don't know for audio.

---

### Post by Nikron on 2007-06-20
They probably don't work because you aren't in the correct group.  Use the command 'id' to tell us what groups you are in.

---

### Post by EagleRock on 2007-06-20
> **yellowpagesguy said:**
> thing is i dont have the cd and i didnt install ubuntu on the laptop see i got it off Ebay

You can try any other CD, then.  Also, if you want a copy of Ubuntu, just download it and burn the .iso.

Also, let us know if this happens with ANY cd, or a specific type.  If so, what type?

In regards to the /etc/fstab file, you can get the contents by opening up a terminal and typing "cat /etc/fstab"

In case that doesn't work, do "sudo cat /etc/fstab"

---

