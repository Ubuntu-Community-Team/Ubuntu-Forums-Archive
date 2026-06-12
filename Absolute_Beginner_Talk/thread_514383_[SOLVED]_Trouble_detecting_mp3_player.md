---
title: "[SOLVED] Trouble detecting mp3 player"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-07-31
hello, 

i have trouble mounting a Philips MP3 player on my computer. i dont believe there should be anything wrong with the pc, as i just bought it a few days ago, spanking new, and i installed feisty. 

the problem is, when i connect my player to the pc, the player shows no signs of life (or suddenly dies). the computer doesn't detect it either. my pc doesnt recognize my ipod either, nor my camera. 

is this a software thing or are my usb ports not alright?
any help appreciated. 

thanks in advance.

p.s. i forgot to add that my old laptop that was much weaker specs wise and had feisty installed recognized my camera, my ipod, and this mp3 player.

---

### Post by aysiu on 2007-07-31
Plug in the MP3 player.

Open a [terminal](http://www.psychocats.net/ubuntu/terminal) and paste in ```
sudo fdisk -l
``` and ```
df -h
``` then paste the output back here.

---

### Post by shadowboxer_k on 2007-07-31
ok, here is what appeared on terminal after typing the commands. i had my camera plugged in at the moment.

kris@kris-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9584    76983448+   c  W95 FAT32 (LBA)
/dev/sda2   *        9585       19080    76276620   83  Linux
/dev/sda3           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris
kris@kris-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              72G  9.5G   59G  14% /
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  100K  506M   1% /proc/bus/usb
udev                  506M  100K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
kris@kris-desktop:~$

---

### Post by shadowboxer_k on 2007-07-31
i guess my computer has trouble detecting peripherals in general.

can anyone help, please? i wonder how i can find out if it's a hardware problem.

---

### Post by annda on 2007-07-31
it's just a shot. to see if kernel sees anything going on with your hardware, plug it in and
```

dmesg
```

---

### Post by shadowboxer_k on 2007-07-31
amazingly, it worked after a reboot. with the mp3 player anyway.

thanks to everyone for the help!

---

### Post by darkwing|duck on 2007-08-15
ok same problem and when i go into terminal and dmesg
i get this

[    0.000000] copy_e820_map() start: 00000000ff7c0000 size: 0000000000840000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262064) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262064
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262064
[    0.000000] On node 0 totalpages: 262064
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32433 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f9bb0
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x12000506 MSFT 0x00000097) @ 0x3ffb0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x12000506 MSFT 0x00000097) @ 0x3ffb0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x12000506 MSFT 0x00000097) @ 0x3ffb0390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x12000506 MSFT 0x00000097) @ 0x3ffc0040
[    0.000000] ACPI: DSDT (v001  939M2 939M2150 0x00000150 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec10000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 2, version 17, address 0xfec10000, GSI 24-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf7c0000)
[    0.000000] Detected 2400.086 MHz processor.
[   26.129693] Built 1 zonelists.  Total pages: 260017
[   26.129696] Kernel command line: root=UUID=b89f7023-fd70-4ce1-99fa-676d5a7984f4 ro quiet splash
[   26.129801] mapped APIC to ffffd000 (fee00000)
[   26.129803] mapped IOAPIC to ffffc000 (fec00000)
[   26.129805] mapped IOAPIC to ffffb000 (fec10000)
[   26.129808] Enabling fast FPU save and restore... done.
[   26.129810] Enabling unmasked SIMD FPU exception support... done.
[   26.129816] Initializing CPU#0
[   26.129857] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   26.132556] Console: colour VGA+ 80x25
[   26.132910] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   26.133259] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.148676] Memory: 1028056k/1048256k available (1992k kernel code, 19456k reserved, 900k data, 328k init, 130752k highmem)
[   26.148684] virtual kernel memory layout:
[   26.148685]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   26.148686]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.148687]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   26.148688]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   26.148689]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   26.148690]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   26.148691]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   26.148694] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.225721] Calibrating delay using timer specific routine.. 4803.35 BogoMIPS (lpj=9606715)
[   26.225755] Security Framework v1.0.0 initialized
[   26.225761] SELinux:  Disabled at boot.
[   26.225773] Mount-cache hash table entries: 512
[   26.225883] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   26.225890] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.225892] CPU: L2 Cache: 512K (64 bytes/line)
[   26.225894] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   26.225903] Compat vDSO mapped to ffffe000.
[   26.225906] Remapping vsyscall page to ffffe000
[   26.225915] Checking 'hlt' instruction... OK.
[   26.241813] SMP alternatives: switching to UP code
[   26.242000] Freeing SMP alternatives: 11k freed
[   26.242162] Early unpacking initramfs... done
[   26.474081] ACPI: Core revision 20060707
[   26.474477] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   26.475826] CPU0: AMD Athlon(tm) 64 Processor 3800+ stepping 02
[   26.475839] Total of 1 processors activated (4803.35 BogoMIPS).
[   26.476367] ENABLING IO-APIC IRQs
[   26.476600] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   26.621164] Brought up 1 CPUs
[   26.621331] Booting paravirtualized kernel on bare hardware
[   26.621381] Time: 17:03:08  Date: 07/15/107
[   26.621401] NET: Registered protocol family 16
[   26.621460] EISA bus registered
[   26.621463] ACPI: bus type pci registered
[   26.622089] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[   26.622091] PCI: Using configuration type 1
[   26.622092] Setting up standard PCI resources
[   26.629592] ACPI: Interpreter enabled
[   26.629593] ACPI: Using IOAPIC for interrupt routing
[   26.630220] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.630223] PCI: Probing PCI hardware (bus 00)
[   26.630592] PCI quirk: region 0800-083f claimed by ali7101 ACPI
[   26.630951] Boot video device is 0000:03:00.0
[   26.631241] PCI: Transparent bridge - 0000:00:06.0
[   26.631273] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.642245] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   26.642424] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HTT_._PRT]
[   26.646780] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEB1._PRT]
[   26.646932] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEB2._PRT]
[   26.647472] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   26.647682] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   26.647890] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15), disabled.
[   26.648097] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15), disabled.
[   26.648306] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   26.648516] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   26.648731] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   26.648941] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[   26.649193] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   26.649247] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.649254] pnp: PnP ACPI init
[   26.652917] pnp: PnP ACPI: found 15 devices
[   26.652920] PnPBIOS: Disabled by ACPI PNP
[   26.652960] PCI: Using ACPI for IRQ routing
[   26.652962] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.660611] NET: Registered protocol family 8
[   26.660612] NET: Registered protocol family 20
[   26.661094] pnp: 00:0d: ioport range 0x290-0x29f has been reserved
[   26.661267] PCI: Bridge: 0000:00:01.0
[   26.661268]   IO window: disabled.
[   26.661271]   MEM window: fa700000-fa7fffff
[   26.661273]   PREFETCH window: disabled.
[   26.661276] PCI: Bridge: 0000:00:02.0
[   26.661277]   IO window: disabled.
[   26.661279]   MEM window: fa800000-fa8fffff
[   26.661281]   PREFETCH window: disabled.
[   26.661284] PCI: Bridge: 0000:00:05.0
[   26.661285]   IO window: disabled.
[   26.661289]   MEM window: fa900000-fe9fffff
[   26.661292]   PREFETCH window: c7f00000-d7efffff
[   26.661297] PCI: Bridge: 0000:00:06.0
[   26.661299]   IO window: d000-dfff
[   26.661303]   MEM window: fea00000-feafffff
[   26.661306]   PREFETCH window: 50000000-500fffff
[   26.661321] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 29 (level, low) -> IRQ 16
[   26.661325] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.661331] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 34 (level, low) -> IRQ 17
[   26.661334] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   26.661340] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   26.661346] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   26.661367] NET: Registered protocol family 2
[   26.689097] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.689232] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   26.690039] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   26.690407] TCP: Hash tables configured (established 131072 bind 65536)
[   26.690409] TCP reno registered
[   26.701124] checking if image is initramfs... it is
[   27.158305] Freeing initrd memory: 6766k freed
[   27.158633] audit: initializing netlink socket (disabled)
[   27.158644] audit(1187197389.108:1): initialized
[   27.158690] highmem bounce pool size: 64 pages
[   27.158734] VFS: Disk quotas dquot_6.5.1
[   27.158750] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.158789] io scheduler noop registered
[   27.158791] io scheduler anticipatory registered
[   27.158792] io scheduler deadline registered
[   27.158797] io scheduler cfq registered (default)
[   27.232355] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   27.232377] assign_interrupt_mode Found MSI capability
[   27.232379] Allocate Port Service[0000:00:01.0:pcie00]
[   27.232433] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   27.232455] assign_interrupt_mode Found MSI capability
[   27.232456] Allocate Port Service[0000:00:02.0:pcie00]
[   27.232547] isapnp: Scanning for PnP cards...
[   27.585935] isapnp: No Plug & Play device found
[   27.601547] Real Time Clock Driver v1.12ac
[   27.601580] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.601687] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.601823] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   27.602229] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.602355] mice: PS/2 mouse device common for all mice
[   27.602687] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.602845] input: Macintosh mouse button emulation as /class/input/input0
[   27.602866] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   27.602869] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   27.603039] PNP: No PS/2 controller found. Probing ports directly.
[   27.605325] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.605329] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.605420] EISA: Probing bus 0 at eisa.0
[   27.605454] EISA: Detected 0 cards.
[   27.635478] TCP cubic registered
[   27.635483] NET: Registered protocol family 1
[   27.635498] Using IPI No-Shortcut mode
[   27.635534] ACPI: (supports S0 S1 S3 S4 S5)
[   27.635565]   Magic number: 3:455:87
[   27.635645] Time: tsc clocksource has been installed.
[   27.635892] Freeing unused kernel memory: 328k freed
[   28.846869] Capability LSM initialized
[   28.878064] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   29.300924] SCSI subsystem initialized
[   29.304178] libata version 2.20 loaded.
[   29.306755] ALI15X3: IDE controller at PCI slot 0000:00:12.0
[   29.306767] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 19 (level, low) -> IRQ 18
[   29.306775] ALI15X3: chipset revision 199
[   29.306777] ALI15X3: not 100% native mode: will probe irqs later
[   29.306790]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:DMA
[   29.306803]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
[   29.306811] Probing IDE interface ide0...
[   29.329945] usbcore: registered new interface driver usbfs
[   29.329963] usbcore: registered new interface driver hub
[   29.329983] usbcore: registered new device driver usb
[   29.330475] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   29.387710] Linux Tulip driver version 1.1.14 (December 15, 2004)
[   29.407831] ieee1394: Initialized config rom entry `ip1394'
[   29.457763] Floppy drive(s): fd0 is 1.44M
[   29.513923] FDC 0 is a post-1991 82077
[   29.824586] hdb: WDC WD1200JB-00GVC0, ATA DISK drive
[   29.885608] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   29.903356] Probing IDE interface ide1...
[   30.639377] hdc: SONY CD-RW CRX195E1, ATAPI CD/DVD-ROM drive
[   31.426209] hdd: TDK DVDRW0404N, ATAPI CD/DVD-ROM drive
[   31.487681] ide1 at 0x170-0x177,0x376 on irq 15
[   31.497320] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 20 (level, low) -> IRQ 19
[   31.497333] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   31.497500] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   31.497516] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfebfe000
[   31.502325] hdb: max request size: 512KiB
[   31.511766] hdb: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   31.513788] hdb: cache flushes supported
[   31.513828]  hdb: hdb1 hdb2 < hdb5 >
[   31.555888] usb usb1: configuration #1 chosen from 1 choice
[   31.555909] hub 1-0:1.0: USB hub found
[   31.555917] hub 1-0:1.0: 3 ports detected
[   31.571776] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 1984kB Cache, UDMA(33)
[   31.571783] Uniform CD-ROM driver Revision: 3.20
[   31.612136] hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   31.661784] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 21 (level, low) -> IRQ 20
[   31.661798] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   31.661812] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   31.661828] ohci_hcd 0000:00:13.1: irq 20, io mem 0xfebfd000
[   31.723635] usb usb2: configuration #1 chosen from 1 choice
[   31.723660] hub 2-0:1.0: USB hub found
[   31.723668] hub 2-0:1.0: 3 ports detected
[   31.788640] Attempting manual resume
[   31.788643] swsusp: Resume From Partition 3:69
[   31.788644] PM: Checking swsusp image.
[   31.808716] PM: Resume from disk failed.
[   31.829505] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 22 (level, low) -> IRQ 21
[   31.829519] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   31.829534] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   31.829551] ohci_hcd 0000:00:13.2: irq 21, io mem 0xfebfc000
[   31.853092] kjournald starting.  Commit interval 5 seconds
[   31.853099] EXT3-fs: mounted filesystem with ordered data mode.
[   31.891388] usb usb3: configuration #1 chosen from 1 choice
[   31.891410] hub 3-0:1.0: USB hub found
[   31.891419] hub 3-0:1.0: 3 ports detected
[   31.969218] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   31.997344] ACPI: PCI Interrupt 0000:00:13.3[D] -> GSI 23 (level, low) -> IRQ 22
[   31.997354] ehci_hcd 0000:00:13.3: EHCI Host Controller
[   31.997370] ehci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   31.997397] ehci_hcd 0000:00:13.3: debug port 1
[   32.025134] ehci_hcd 0000:00:13.3: irq 22, io mem 0xfebff800
[   32.025140] ehci_hcd 0000:00:13.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.025195] usb usb4: configuration #1 chosen from 1 choice
[   32.025211] hub 4-0:1.0: USB hub found
[   32.025219] hub 4-0:1.0: 8 ports detected
[   32.133129] ACPI: PCI Interrupt 0000:04:05.0[A] -> GSI 20 (level, low) -> IRQ 19
[   32.133811] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.
[   32.140894] eth0: ADMtek Comet rev 17 at Port 0xd800, 00:14:BF:53:1D:65, IRQ 19.
[   32.140968] ACPI: PCI Interrupt 0000:04:06.2[B] -> GSI 22 (level, low) -> IRQ 21
[   32.190679] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   33.347171] usb 4-3: new high speed USB device using ehci_hcd and address 4
[   33.467101] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c015105f531]
[   35.260921] usb 4-3: configuration #128 chosen from 1 choice
[   35.935360] usb 1-1: new full speed USB device using ohci_hcd and address 3
[   36.154049] usb 1-1: configuration #1 chosen from 1 choice
[   36.466582] usb 1-2: new full speed USB device using ohci_hcd and address 4
[   36.671313] usb 1-2: configuration #1 chosen from 1 choice
[   36.674229] hub 1-2:1.0: USB hub found
[   36.677209] hub 1-2:1.0: 4 ports detected
[   37.185516] usb 2-3: new low speed USB device using ohci_hcd and address 2
[   37.369249] usb 2-3: device descriptor read/64, error -62
[   37.656824] usb 2-3: device descriptor read/64, error -62
[   37.936412] usb 2-3: new low speed USB device using ohci_hcd and address 3
[   38.120137] usb 2-3: device descriptor read/64, error -62
[   38.407722] usb 2-3: device descriptor read/64, error -62
[   38.687295] usb 2-3: new low speed USB device using ohci_hcd and address 4
[   39.102682] usb 2-3: device not accepting address 4, error -62
[   39.278430] usb 2-3: new low speed USB device using ohci_hcd and address 5
[   39.693823] usb 2-3: device not accepting address 5, error -62
[   40.077249] usb 3-2: new low speed USB device using ohci_hcd and address 2
[   40.260980] usb 3-2: device descriptor read/64, error -62
[   40.548551] usb 3-2: device descriptor read/64, error -62
[   40.828133] usb 3-2: new low speed USB device using ohci_hcd and address 3
[   40.905051] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.915674] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.983667] NET: Registered protocol family 17
[   41.011855] usb 3-2: device descriptor read/64, error -62
[   41.251369] gameport: EMU10K1 is pci0000:04:06.1/gameport0, io 0xdc00, speed 1028kHz
[   41.257807] ali15x3_smbus 0000:00:07.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   41.257811] ali15x3_smbus 0000:00:07.1: ALI15X3 not detected, module not inserted.
[   41.260403] ali1535_smbus 0000:00:07.1: ALI1535_smb region uninitialized - upgrade BIOS?
[   41.260406] ali1535_smbus 0000:00:07.1: ALI1535 not detected, module not inserted.
[   41.307418] usb 3-2: device descriptor read/64, error -62
[   41.480591] Linux agpgart interface v0.102 (c) Dave Jones
[   41.527769] uli526x: ULi M5261/M5263 net driver, version 0.9.3 (2005-7-29)
[   41.527816] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 17 (level, low) -> IRQ 23
[   41.549305] eth1: ULi M5263 at pci0000:00:11.0, 00:13:8f:73:ec:2f, irq 23.
[   41.567524] ali1563: SMBus control = 0403
[   41.567559] ali1563_probe: Returning 0
[   41.577244] ath_hal: module license 'Proprietary' taints kernel.
[   41.577754] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   41.606981] usb 3-2: new low speed USB device using ohci_hcd and address 4
[   41.775186] input: PC Speaker as /class/input/input1
[   41.864380] wlan: 0.8.4.2 (0.9.3.1)
[   41.886308] ath_pci: 0.9.4.5 (0.9.3.1)
[   41.886360] ACPI: PCI Interrupt 0000:04:07.0[A] -> GSI 22 (level, low) -> IRQ 21
[   42.406838] usb 3-2: device not accepting address 4, error -62
[   42.435651] agpgart: Detected AGP bridge 20
[   42.435664] Setting up ULi AGP.
[   42.437666] agpgart: AGP aperture is 64M @ 0xdc000000
[   42.464491] parport: PnPBIOS parport detected.
[   42.464600] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   42.683420] 0000:04:05.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   42.683431] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   42.780175] irda_init()
[   42.780193] NET: Registered protocol family 23
[   42.793222] usb 3-2: new low speed USB device using ohci_hcd and address 5
[   43.046435] ath_rate_sample: 1.2 (0.9.3.1)
[   43.046673] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   43.046677] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   43.046684] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   43.046687] wifi0: mac 7.8 phy 4.5 radio 5.6
[   43.046690] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   43.046692] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   43.046693] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   43.046695] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   43.046696] wifi0: Use hw queue 8 for CAB traffic
[   43.046698] wifi0: Use hw queue 9 for beacons
[   43.140335] wifi0: Atheros 5212: mem=0xfeae0000, irq=21
[   43.144641] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 24
[   43.144820] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   43.208606] usb 3-2: device not accepting address 5, error -62
[   43.443690] usb 1-2.1: new low speed USB device using ohci_hcd and address 5
[   43.503764] ACPI: PCI Interrupt 0000:04:06.0[A] -> GSI 21 (level, low) -> IRQ 20
[   43.507549] Installing spdif_bug patch: Audigy 2 ZS [SB0350]
[   43.562992] usb 1-2.1: configuration #1 chosen from 1 choice
[   43.801562] usb 1-2.4: new full speed USB device using ohci_hcd and address 6
[   43.933435] usb 1-2.4: configuration #1 chosen from 1 choice
[   43.937411] usbcore: registered new interface driver hiddev
[   43.937470] usbcore: registered new interface driver xpad
[   43.937472] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   43.945474] input: Logitech USB Gaming Mouse as /class/input/input2
[   43.945555] input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:13.0-1
[   43.958394] hiddev96: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:13.0-1
[   43.963401] input: Gaming Keyboard as /class/input/input3
[   43.963431] input: USB HID v1.10 Keyboard [Gaming Keyboard] on usb-0000:00:13.0-2.1
[   43.977376] input: Gaming Keyboard as /class/input/input4
[   43.977425] input,hiddev97: USB HID v1.10 Device [Gaming Keyboard] on usb-0000:00:13.0-2.1
[   43.986395] input: G15 Keyboard G15 Keyboard as /class/input/input5
[   43.986452] input,hiddev98: USB HID v1.11 Keypad [G15 Keyboard G15 Keyboard] on usb-0000:00:13.0-2.4
[   43.986465] usbcore: registered new interface driver usbhid
[   43.986467] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   44.279880] fuse init (API version 7.8)
[   44.311787] lp0: using parport0 (interrupt-driven).
[   44.359388] Adding 3028212k swap on /dev/disk/by-uuid/4d7f4a87-9394-438d-9331-17e1c407731b.  Priority:-1 extents:1 across:3028212k
[   44.490192] EXT3 FS on hdb1, internal journal
[   44.678915] NET: Registered protocol family 10
[   44.678992] lo: Disabled Privacy Extensions
[   44.679079] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   45.965152] uli526x: eth1 NIC Link is Down
[   48.396360] No dock devices found.
[   48.404245] Using specific hotkey driver
[   48.437434] ibm_acpi: ec object not found
[   48.533210] input: Power Button (FF) as /class/input/input6
[   48.536318] ACPI: Power Button (FF) [PWRF]
[   48.559163] input: Power Button (CM) as /class/input/input7
[   48.562265] ACPI: Power Button (CM) [PWRB]
[   48.594768] pcc_acpi: loading...
[   48.787194] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3800+ processors (version 2.00.00)
[   48.787230] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0x6
[   48.787232] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0x8
[   48.787233] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0xa
[   48.787235] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0xa
[   48.787237] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0xa
[   53.506435] agpgart: Found an AGP 3.0 compliant device at 0000:00:04.0.
[   53.506470] agpgart: Putting AGP V3 device at 0000:00:04.0 into 8x mode
[   53.506493] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
[   54.408020] ppdev: user-space parallel port driver
[   54.908213] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   54.908217] apm: overridden by ACPI.
[   55.132991] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   55.247133] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   55.247436] NFSD: starting 90-second grace period
[   29.428000] Time: acpi_pm clocksource has been installed.
[   30.472000] Bluetooth: Core ver 2.11
[   30.472000] NET: Registered protocol family 31
[   30.472000] Bluetooth: HCI device and connection manager initialized
[   30.472000] Bluetooth: HCI socket layer initialized
[   30.608000] Bluetooth: L2CAP ver 2.8
[   30.608000] Bluetooth: L2CAP socket layer initialized
[   31.404000] usb 2-3: new low speed USB device using ohci_hcd and address 6
[   31.588000] usb 2-3: device descriptor read/64, error -62
[   31.876000] usb 2-3: device descriptor read/64, error -62
[   32.156000] usb 2-3: new low speed USB device using ohci_hcd and address 7
[   32.340000] usb 2-3: device descriptor read/64, error -62
[   32.628000] usb 2-3: device descriptor read/64, error -62
[   32.908000] usb 2-3: new low speed USB device using ohci_hcd and address 8
[   33.324000] usb 2-3: device not accepting address 8, error -62
[   33.500000] usb 2-3: new low speed USB device using ohci_hcd and address 9
[   33.916000] usb 2-3: device not accepting address 9, error -62
[   34.244000] usb 3-2: new low speed USB device using ohci_hcd and address 6
[   34.428000] usb 3-2: device descriptor read/64, error -62
[   34.716000] usb 3-2: device descriptor read/64, error -62
[   34.996000] usb 3-2: new low speed USB device using ohci_hcd and address 7
[   35.180000] usb 3-2: device descriptor read/64, error -62
[   35.468000] usb 3-2: device descriptor read/64, error -62
[   35.748000] usb 3-2: new low speed USB device using ohci_hcd and address 8
[   36.164000] usb 3-2: device not accepting address 8, error -62
[   36.340000] usb 3-2: new low speed USB device using ohci_hcd and address 9
[   36.756000] usb 3-2: device not accepting address 9, error -62
[   36.808000] Bluetooth: RFCOMM socket layer initialized
[   36.808000] Bluetooth: RFCOMM TTY layer initialized
[   36.808000] Bluetooth: RFCOMM ver 1.8
[   44.564000] eth0: no IPv6 routers present

---

