---
title: "Error When Trying To Mount"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by itsdevivi on 2007-08-19
I am trying to mount a cd and this is the errormessage that comes up. Btw i am using a pc, not a laptop.




"mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"


If anyone knows how to fix this error please reply asap.

---

### Post by Jimmyfj on 2007-08-19
Which release do you use? My Ubuntu, both 7.04 and 7.10 automounts just fine?

Edit: Have you tried running the suggested command in a terminal: dmesg | tail or so ?

---

### Post by itsdevivi on 2007-08-19
I have a pc and i am trying to mount a cd on cd-rom drive with command:
"sudo mount /media/cdrom0"

The error message that comes up is:

mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

PLEASE HELP!!!

---

### Post by taurus on 2007-08-19
What kind of CD is that?  Post the output of this command from a terminal?

```
dmesg | tail
```

---

### Post by itsdevivi on 2007-08-19
I recently tried to mount cd rom drive (i have a pc by the way) and i used the command "sudo mount /media/cdrom0"
the errormessage that appears is:

"mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
"

if anybody knows how to fix this let me know please

---

### Post by taurus on 2007-08-19
No need to double post.

[http://ubuntuforums.org/showthread.php?t=529726](http://ubuntuforums.org/showthread.php?t=529726)

---

### Post by itsdevivi on 2007-08-19
after typing in dmesg i get:
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000c8000 size: 0000000000008000 end: 00000000000d0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fbf0000 end: 000000001fcf0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fcf0000 size: 000000000000c000 end: 000000001fcfc000 type: 3
[    0.000000] copy_e820_map() start: 000000001fcfc000 size: 0000000000004000 end: 000000001fd00000 type: 4
[    0.000000] copy_e820_map() start: 000000001fd00000 size: 0000000000180000 end: 000000001fe80000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fe80000 size: 0000000000180000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000080000 end: 00000000ffc00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000c8000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fcf0000 (usable)
[    0.000000]  BIOS-e820: 000000001fcf0000 - 000000001fcfc000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fcfc000 - 000000001fd00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fd00000 - 000000001fe80000 (usable)
[    0.000000]  BIOS-e820: 000000001fe80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 130688) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130688
[    0.000000]   HighMem    130688 ->   130688
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130688
[    0.000000] On node 0 totalpages: 130688
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125603 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6670
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1fcf7072
[    0.000000] ACPI: FADT (v001 INTEL  Whitney  0x06040000 PTL  0x000f4240) @ 0x1fcfbf0a
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x1fcfbf7e
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1fcfbfd8
[    0.000000] ACPI: DSDT (v001  INTEL  Whitney 0x06040000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:11 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb80000)
[    0.000000] Detected 1395.825 MHz processor.
[   98.035098] Built 1 zonelists.  Total pages: 129667
[   98.035104] Kernel command line: root=UUID=221e8755-efb9-4215-9967-205a6e651bc5 ro quiet splash
[   98.035428] mapped APIC to ffffd000 (fee00000)
[   98.035434] mapped IOAPIC to ffffc000 (fec00000)
[   98.035442] Enabling fast FPU save and restore... done.
[   98.035446] Enabling unmasked SIMD FPU exception support... done.
[   98.035465] Initializing CPU#0
[   98.035567] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   98.037652] Console: colour VGA+ 80x25
[   98.039102] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   98.041031] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   98.095094] Memory: 507192k/522752k available (1992k kernel code, 14976k reserved, 900k data, 328k init, 0k highmem)
[   98.095113] virtual kernel memory layout:
[   98.095115]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   98.095118]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   98.095120]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   98.095122]     lowmem  : 0xc0000000 - 0xdfe80000   ( 510 MB)
[   98.095124]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   98.095126]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   98.095128]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   98.095134] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   98.171459] Calibrating delay using timer specific routine.. 2793.65 BogoMIPS (lpj=5587312)
[   98.171541] Security Framework v1.0.0 initialized
[   98.171562] SELinux:  Disabled at boot.
[   98.171594] Mount-cache hash table entries: 512
[   98.171884] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   98.171904] CPU: L1 I cache: 16K, L1 D cache: 16K
[   98.171908] CPU: L2 cache: 256K
[   98.171914] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[   98.171931] Compat vDSO mapped to ffffe000.
[   98.171943] Remapping vsyscall page to ffffe000
[   98.171961] Checking 'hlt' instruction... OK.
[   98.187657] SMP alternatives: switching to UP code
[   98.188021] Freeing SMP alternatives: 11k freed
[   98.188409] Early unpacking initramfs... done
[   98.741837] ACPI: Core revision 20060707
[   98.742867] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   98.763827] CPU0: Intel(R) Celeron(TM) CPU                1400MHz stepping 01
[   98.763875] Total of 1 processors activated (2793.65 BogoMIPS).
[   98.764028] ENABLING IO-APIC IRQs
[   98.764246] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   98.910949] Brought up 1 CPUs
[   98.911503] Booting paravirtualized kernel on bare hardware
[   98.911647] Time: 20:20:43  Date: 07/19/107
[   98.911727] NET: Registered protocol family 16
[   98.911988] EISA bus registered
[   98.911999] ACPI: bus type pci registered
[   98.912925] PCI: PCI BIOS revision 2.10 entry at 0xfd9a8, last bus=1
[   98.912929] PCI: Using configuration type 1
[   98.912932] Setting up standard PCI resources
[   98.921243] ACPI: Interpreter enabled
[   98.921257] ACPI: Using IOAPIC for interrupt routing
[   98.921965] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   98.921979] PCI: Probing PCI hardware (bus 00)
[   98.922877] Boot video device is 0000:00:01.0
[   98.923001] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   98.923007] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   98.923420] PCI: Transparent bridge - 0000:00:1e.0
[   98.923457] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   98.926411] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   98.926755] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   98.927196] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   98.927497] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   98.928186] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[   98.929782] ACPI: Power Resource [FN01] (on)
[   98.929943] Linux Plug and Play Support v0.97 (c) Adam Belay
[   98.929969] pnp: PnP ACPI init
[   98.962224] pnp: PnP ACPI: found 14 devices
[   98.962239] PnPBIOS: Disabled by ACPI PNP
[   98.962381] PCI: Using ACPI for IRQ routing
[   98.962389] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   98.964788] NET: Registered protocol family 8
[   98.964792] NET: Registered protocol family 20
[   98.965951] PCI: Ignore bogus resource 6 [0:0] of 0000:00:01.0
[   98.965963] PCI: Bridge: 0000:00:1e.0
[   98.965968]   IO window: 2000-2fff
[   98.965978]   MEM window: f4100000-f41fffff
[   98.965983]   PREFETCH window: disabled.
[   98.966003] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   98.966078] NET: Registered protocol family 2
[   99.002960] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   99.003180] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   99.003707] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   99.004041] TCP: Hash tables configured (established 16384 bind 8192)
[   99.004048] TCP reno registered
[   99.015128] checking if image is initramfs... it is
[  100.014803] Freeing initrd memory: 6780k freed
[  100.015519] Simple Boot Flag at 0x35 set to 0x1
[  100.016123] audit: initializing netlink socket (disabled)
[  100.016159] audit(1187554844.048:1): initialized
[  100.016513] VFS: Disk quotas dquot_6.5.1
[  100.016561] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  100.016703] io scheduler noop registered
[  100.016708] io scheduler anticipatory registered
[  100.016712] io scheduler deadline registered
[  100.016735] io scheduler cfq registered (default)
[  100.017250] isapnp: Scanning for PnP cards...
[  100.370883] isapnp: No Plug & Play device found
[  100.449770] Real Time Clock Driver v1.12ac
[  100.449897] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  100.450077] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  100.451834] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  100.452423] mice: PS/2 mouse device common for all mice
[  100.453723] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  100.454329] input: Macintosh mouse button emulation as /class/input/input0
[  100.454397] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  100.454406] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  100.454809] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[  100.458731] serio: i8042 KBD port at 0x60,0x64 irq 1
[  100.458748] serio: i8042 AUX port at 0x60,0x64 irq 12
[  100.459078] EISA: Probing bus 0 at eisa.0
[  100.459097] Cannot allocate resource for EISA slot 1
[  100.459102] Cannot allocate resource for EISA slot 2
[  100.459129] EISA: Detected 0 cards.
[  100.489286] TCP cubic registered
[  100.489308] NET: Registered protocol family 1
[  100.489359] Using IPI No-Shortcut mode
[  100.489516] ACPI: (supports S0<6>Time: tsc clocksource has been installed.
[  100.489537]  S1 S3 S4 S5)
[  100.489598]   Magic number: 3:832:346
[  100.489799]   hash matches device tty63
[  100.491236] Freeing unused kernel memory: 328k freed
[  100.503941] input: AT Translated Set 2 keyboard as /class/input/input1
[  102.031906] Capability LSM initialized
[  102.114518] ACPI: Transitioning device [FAN1] to D0
[  102.114528] ACPI: Transitioning device [FAN1] to D0
[  102.114533] ACPI: Fan [FAN1] (off)
[  102.124027] ACPI: Invalid PBLK length [5]
[  102.128573] ACPI: Thermal Zone [THRM] (-273 C)
[  103.591073] SCSI subsystem initialized
[  103.606928] libata version 2.20 loaded.
[  103.616082] ata_piix 0000:00:1f.1: version 2.10ac1
[  103.616148] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[  103.616273] ata1: PATA max UDMA/66 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011080 irq 14
[  103.616341] ata2: PATA max UDMA/66 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011088 irq 15
[  103.616372] scsi0 : ata_piix
[  103.638073] usbcore: registered new interface driver usbfs
[  103.638129] usbcore: registered new interface driver hub
[  103.638178] usbcore: registered new device driver usb
[  103.641244] USB Universal Host Controller Interface driver v3.0
[  103.682212] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[  103.807539] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[  103.807553] ata1.00: ATA-7: WDC WD1600JB-00REA0, 20.00K20, max UDMA/100
[  103.807558] ata1.00: 312581808 sectors, multi 16: LBA48 
[  103.819121] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[  103.819136] ata1.00: configured for UDMA/66
[  103.819166] scsi1 : ata_piix
[  103.899257] Floppy drive(s): fd0 is 1.44M
[  103.965342] FDC 0 is a post-1991 82077
[  104.146702] ata2.00: ATAPI, max MWDMA2
[  104.318559] ata2.00: configured for MWDMA2
[  104.320765] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JB-00R 20.0 PQ: 0 ANSI: 5
[  104.322573] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4120B 2.03 PQ: 0 ANSI: 5
[  104.325854] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 16
[  104.325885] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[  104.325893] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[  104.326176] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[  104.326256] uhci_hcd 0000:00:1f.2: irq 16, io base 0x000010a0
[  104.326524] usb usb1: configuration #1 chosen from 1 choice
[  104.326580] hub 1-0:1.0: USB hub found
[  104.326598] hub 1-0:1.0: 2 ports detected
[  104.358286] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[  104.358348] sda: Write Protect is off
[  104.358352] sda: Mode Sense: 00 3a 00 00
[  104.358380] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  104.358542] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[  104.358557] sda: Write Protect is off
[  104.358561] sda: Mode Sense: 00 3a 00 00
[  104.358584] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  104.358590]  sda: sda1 sda2 < sda5 sda6 > sda3
[  104.393370] sd 0:0:0:0: Attached scsi disk sda
[  104.405007] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  104.405304] sr 1:0:0:0: Attached scsi generic sg1 type 5
[  104.421376] sr0: scsi3-mmc drive: 61x/32x writer cd/rw xa/form2 cdda tray
[  104.421389] Uniform CD-ROM driver Revision: 3.20
[  104.421807] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  104.434818] 8139cp 0000:01:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[  104.434829] 8139cp 0000:01:06.0: Try the "8139too" driver instead.
[  104.438794] 8139too Fast Ethernet driver 0.9.28
[  104.438893] PCI: Enabling device 0000:01:06.0 (0100 -> 0103)
[  104.438908] ACPI: PCI Interrupt 0000:01:06.0[A] -> GSI 19 (level, low) -> IRQ 16
[  104.439322] eth0: RealTek RTL8139 at 0xe0828000, 00:40:2b:36:d6:bc, IRQ 16
[  104.439327] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[  104.733953] usb 1-2: new full speed USB device using uhci_hcd and address 2
[  104.750464] Attempting manual resume
[  104.750473] swsusp: Resume From Partition 8:6
[  104.750476] PM: Checking swsusp image.
[  104.750870] PM: Resume from disk failed.
[  104.819109] kjournald starting.  Commit interval 5 seconds
[  104.819144] EXT3-fs: mounted filesystem with ordered data mode.
[  104.896957] usb 1-2: configuration #1 chosen from 1 choice
[  104.899873] hub 1-2:1.0: USB hub found
[  104.902713] hub 1-2:1.0: 4 ports detected
[  114.058333] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  115.621295] NET: Registered protocol family 17
[  116.988612] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  116.993253] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  116.999260] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[  117.135803] intel_rng: FWH not detected
[  117.173102] iTCO_vendor_support: vendor-support=0
[  117.176021] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[  117.176196] iTCO_wdt: Found a ICH TCO device (Version=1, TCOBASE=0x1060)
[  117.176260] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  117.387655] Linux agpgart interface v0.102 (c) Dave Jones
[  117.656413] agpgart: Detected an Intel i810 E Chipset.
[  117.669718] agpgart: AGP aperture is 64M @ 0xf8000000
[  118.113512] parport: PnPBIOS parport detected.
[  118.113578] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  118.196460] input: PC Speaker as /class/input/input2
[  118.850409] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[  118.851259] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[  118.851321] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  119.173534] intel8x0_measure_ac97_clock: measured 58687 usecs
[  119.173547] intel8x0: clocking to 48000
[  119.494988] fuse init (API version 7.8)
[  119.540536] lp0: using parport0 (interrupt-driven).
[  119.619514] Adding 1502004k swap on /dev/disk/by-uuid/c25766b9-f1df-4bf6-b114-47a44c7d2be0.  Priority:-1 extents:1 across:1502004k
[  119.777705] EXT3 FS on sda3, internal journal
[  120.008484] NET: Registered protocol family 10
[  120.008720] lo: Disabled Privacy Extensions
[  126.417869] input: Power Button (FF) as /class/input/input4
[  126.427812] ACPI: Power Button (FF) [PWRF]
[  126.479897] input: Power Button (CM) as /class/input/input5
[  126.489631] ACPI: Power Button (CM) [PWRB]
[  126.518131] No dock devices found.
[  126.619215] ibm_acpi: ec object not found
[  126.848149] Using specific hotkey driver
[  126.949257] pcc_acpi: loading...
[  130.483752] eth0: no IPv6 routers present
[  134.000927] ppdev: user-space parallel port driver
[  135.068381] apm: BIOS not found.
[  135.648516] Bluetooth: Core ver 2.11
[  135.648687] NET: Registered protocol family 31
[  135.648691] Bluetooth: HCI device and connection manager initialized
[  135.648699] Bluetooth: HCI socket layer initialized
[  135.700339] Bluetooth: L2CAP ver 2.8
[  135.700352] Bluetooth: L2CAP socket layer initialized
[  136.261904] Bluetooth: RFCOMM socket layer initialized
[  136.261954] Bluetooth: RFCOMM TTY layer initialized
[  136.261958] Bluetooth: RFCOMM ver 1.8
[  139.456384] sr 1:0:0:0: SCSI error: return code = 0x08000002
[  139.456401] sr0: Current: sense key: Medium Error
[  139.456405]     Additional sense: L-EC uncorrectable error
[  139.456419] end_request: I/O error, dev sr0, sector 64
[  139.456430] Buffer I/O error on device sr0, logical block 8
[  147.017924] sr 1:0:0:0: SCSI error: return code = 0x08000002
[  147.017941] sr0: Current: sense key: Medium Error
[  147.017947]     Additional sense: L-EC uncorrectable error
[  147.017963] end_request: I/O error, dev sr0, sector 64
[  147.017973] Buffer I/O error on device sr0, logical block 8
[  148.828013] eth0: no IPv6 routers present
[  232.378751] sr 1:0:0:0: SCSI error: return code = 0x08000002
[  232.378767] sr0: Current: sense key: Medium Error
[  232.378772]     Additional sense: L-EC uncorrectable error
[  232.378785] end_request: I/O error, dev sr0, sector 64
[  232.379328] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  469.382127] sr 1:0:0:0: SCSI error: return code = 0x08000002
[  469.382143] sr0: Current: sense key: Medium Error
[  469.382148]     Additional sense: L-EC uncorrectable error
[  469.382162] end_request: I/O error, dev sr0, sector 64
[  469.382806] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 1122.831743] sr 1:0:0:0: SCSI error: return code = 0x08000002
[ 1122.831760] sr0: Current: sense key: Medium Error
[ 1122.831765]     Additional sense: L-EC uncorrectable error
[ 1122.831779] end_request: I/O error, dev sr0, sector 64
[ 1122.832399] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

after typing in    dmesg | tail   i get

[  469.382127] sr 1:0:0:0: SCSI error: return code = 0x08000002
[  469.382143] sr0: Current: sense key: Medium Error
[  469.382148]     Additional sense: L-EC uncorrectable error
[  469.382162] end_request: I/O error, dev sr0, sector 64
[  469.382806] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 1122.831743] sr 1:0:0:0: SCSI error: return code = 0x08000002
[ 1122.831760] sr0: Current: sense key: Medium Error
[ 1122.831765]     Additional sense: L-EC uncorrectable error
[ 1122.831779] end_request: I/O error, dev sr0, sector 64
[ 1122.832399] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

---

### Post by itsdevivi on 2007-08-19
what should i do to start the mount?

---

### Post by wirelessmonkey on 2007-08-19
It looks like your CD may be damaged or dirty, take a look.

---

### Post by K.Mandla on 2007-08-20
(Moved to Absolute Beginner Talk. ;) )

---

### Post by taurus on 2007-08-20
Another thread of the same question.  

What kind of CD is that?

---

