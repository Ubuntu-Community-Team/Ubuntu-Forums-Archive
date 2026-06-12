---
title: "[SOLVED] lost sound"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by k33bz on 2008-01-19
Not sure how this happened, but I did some updates, (not sure which ones, was in hurry) but on the linux headers 16 I have lost sound, as well as control of my alsamixer, I have included pictures. Already tried to un-install and re-install the header. NOTE: sound works with linux header 15.

---

### Post by k33bz on 2008-01-19
Come on people, some one should know something, limited time frame here, need fix asap

---

### Post by k33bz on 2008-01-22
????

---

### Post by k33bz on 2008-02-08
bump

---

### Post by k33bz on 2008-02-29
ok, while working on a different problem I ran "dmesg" and came across something that caught my attention on my snd card, can anyone help me with this?

```
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 PTLTD                                 ) @ 0x000f6650
[    0.000000] ACPI: XSDT (v001 ACRSYS ACRPRDCT 0x06040000  LTP 0x00000000) @ 0x1f69257e
[    0.000000] ACPI: FADT (v003 INTEL  CALISTGA 0x06040000 ALAN 0x00000001) @ 0x1f69bc38
[    0.000000] ACPI: MADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69bd2c
[    0.000000] ACPI: HPET (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69bd94
[    0.000000] ACPI: MCFG (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69bdcc
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x1f69be08
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1f69be62
[    0.000000] ACPI: SLIC (v001 ACRSYS ACRPRDCT 0x06040000 acer 0x00000000) @ 0x1f69be8a
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050624) @ 0x1f692ad0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x1f6925ea
[    0.000000] ACPI: DSDT (v002 INTEL  CALISTGA 0x06040000 MSFT 0x03000000) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Detected 1600.182 MHz processor.
[   33.544062] Built 1 zonelists.  Total pages: 127651
[   33.544067] Kernel command line: root=UUID=6ad9127b-ab77-4b84-ba4b-9a38ec340bfd ro quiet splash
[   33.544220] mapped APIC to ffffd000 (fee00000)
[   33.544222] mapped IOAPIC to ffffc000 (fec00000)
[   33.544225] Enabling fast FPU save and restore... done.
[   33.544228] Enabling unmasked SIMD FPU exception support... done.
[   33.544236] Initializing CPU#0
[   33.544306] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   33.546001] Console: colour VGA+ 80x25
[   33.546171] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   33.546336] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   33.556628] Memory: 498100k/514624k available (1993k kernel code, 16004k reserved, 900k data, 328k init, 0k highmem)
[   33.556637] virtual kernel memory layout:
[   33.556638]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   33.556639]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   33.556640]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   33.556641]     lowmem  : 0xc0000000 - 0xdf690000   ( 502 MB)
[   33.556643]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   33.556644]       .data : 0xc02f24c9 - 0xc03d36d4   ( 900 kB)
[   33.556645]       .text : 0xc0100000 - 0xc02f24c9   (1993 kB)
[   33.556648] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   33.556803] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   33.556810] hpet0: 3 64-bit timers, 14318180 Hz
[   33.557815] Using HPET for base-timer
[   33.636686] Calibrating delay using timer specific routine.. 3203.83 BogoMIPS (lpj=6407672)
[   33.636727] Security Framework v1.0.0 initialized
[   33.636731] SELinux:  Disabled at boot.
[   33.636746] Mount-cache hash table entries: 512
[   33.636873] CPU: After generic identify, caps: afebfbff 20100000 00000000 00000000 0000e31d 00000000 00000001
[   33.636881] monitor/mwait feature present.
[   33.636883] using mwait in idle threads.
[   33.636886] CPU: L1 I cache: 32K, L1 D cache: 32K
[   33.636889] CPU: L2 cache: 1024K
[   33.636892] CPU: After all inits, caps: afebfbff 20100000 00000000 00003940 0000e31d 00000000 00000001
[   33.636900] Compat vDSO mapped to ffffe000.
[   33.636904] Remapping vsyscall page to ffffe000
[   33.636915] Checking 'hlt' instruction... OK.
[   33.652758] SMP alternatives: switching to UP code
[   33.652936] Freeing SMP alternatives: 11k freed
[   33.653112] Early unpacking initramfs... done
[   33.999351] ACPI: Core revision 20060707
[   34.024659] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   34.029047] CPU0: Intel(R) Celeron(R) M CPU        520  @ 1.60GHz stepping 06
[   34.029072] Total of 1 processors activated (3203.83 BogoMIPS).
[   34.029268] ENABLING IO-APIC IRQs
[   34.029463] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   34.175890] Brought up 1 CPUs
[   34.176119] Booting paravirtualized kernel on bare hardware
[   34.176200] Time: 12:27:39  Date: 01/29/108
[   34.176224] NET: Registered protocol family 16
[   34.176304] EISA bus registered
[   34.176308] ACPI: bus type pci registered
[   34.188418] PCI: PCI BIOS revision 2.10 entry at 0xfd6c2, last bus=12
[   34.188420] PCI: Using configuration type 1
[   34.188421] Setting up standard PCI resources
[   34.195358] ACPI: Interpreter enabled
[   34.195361] ACPI: Using IOAPIC for interrupt routing
[   34.195670] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   34.195676] PCI: Probing PCI hardware (bus 00)
[   34.196312] Boot video device is 0000:00:02.0
[   34.197000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   34.197005] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   34.197871] PCI: Transparent bridge - 0000:00:1e.0
[   34.197942] PCI: Bus #0b (-#0e) is hidden behind transparent bridge #0a (-#0b) (try 'pci=assign-busses')
[   34.197945] Please report the result to linux-kernel to fix this permanently
[   34.198015] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   34.203466] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   34.203720] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   34.203960] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   34.204645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   34.205156] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   34.205405] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   34.205656] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   34.205903] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   34.206154] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   34.206401] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   34.206650] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   34.206896] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   34.229129] Linux Plug and Play Support v0.97 (c) Adam Belay
[   34.229139] pnp: PnP ACPI init
[   34.232217] pnp: PnP ACPI: found 9 devices
[   34.232222] PnPBIOS: Disabled by ACPI PNP
[   34.232268] PCI: Using ACPI for IRQ routing
[   34.232271] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   34.232276] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   34.232278] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   34.232280] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   34.232283] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   34.232285] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   34.232287] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   34.232289] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   34.232291] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   34.232293] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[   34.263100] NET: Registered protocol family 8
[   34.263102] NET: Registered protocol family 20
[   34.263610] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   34.263631] PCI: Bridge: 0000:00:1c.0
[   34.263635]   IO window: 2000-2fff
[   34.263641]   MEM window: 34000000-340fffff
[   34.263646]   PREFETCH window: disabled.
[   34.263661] PCI: Bridge: 0000:00:1c.1
[   34.263662]   IO window: disabled.
[   34.263669]   MEM window: 34100000-341fffff
[   34.263673]   PREFETCH window: disabled.
[   34.263679] PCI: Bridge: 0000:00:1c.2
[   34.263680]   IO window: disabled.
[   34.263686]   MEM window: disabled.
[   34.263690]   PREFETCH window: disabled.
[   34.263699] PCI: Bus 11, cardbus bridge: 0000:0a:09.0
[   34.263701]   IO window: 00003000-000030ff
[   34.263706]   IO window: 00003400-000034ff
[   34.263712]   PREFETCH window: 30000000-33ffffff
[   34.263718]   MEM window: 38000000-3bffffff
[   34.263730] PCI: Bridge: 0000:00:1e.0
[   34.263733]   IO window: 3000-3fff
[   34.263739]   MEM window: d0200000-d02fffff
[   34.263744]   PREFETCH window: 30000000-33ffffff
[   34.263773] PCI: Enabling device 0000:00:1c.0 (0000 -> 0003)
[   34.263781] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.263789] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   34.263813] PCI: Enabling device 0000:00:1c.1 (0000 -> 0002)
[   34.263818] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   34.263825] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   34.263850] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   34.263858] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   34.263869] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[   34.263876] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   34.263893] PCI: Enabling device 0000:0a:09.0 (0000 -> 0003)
[   34.263898] ACPI: PCI Interrupt 0000:0a:09.0[A] -> GSI 20 (level, low) -> IRQ 19
[   34.263925] NET: Registered protocol family 2
[   34.299721] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   34.299790] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   34.299864] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   34.299902] TCP: Hash tables configured (established 16384 bind 8192)
[   34.299904] TCP reno registered
[   34.311756] checking if image is initramfs... it is
[   34.991882] Freeing initrd memory: 7868k freed
[   34.992101] Simple Boot Flag at 0x36 set to 0x1
[   34.992402] audit: initializing netlink socket (disabled)
[   34.992417] audit(1204288059.516:1): initialized
[   34.992521] VFS: Disk quotas dquot_6.5.1
[   34.992537] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   34.992583] io scheduler noop registered
[   34.992586] io scheduler anticipatory registered
[   34.992587] io scheduler deadline registered
[   34.992594] io scheduler cfq registered (default)
[   34.992832] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   34.992893] assign_interrupt_mode Found MSI capability
[   34.992896] Allocate Port Service[0000:00:1c.0:pcie00]
[   34.992926] Allocate Port Service[0000:00:1c.0:pcie02]
[   34.993050] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   34.993110] assign_interrupt_mode Found MSI capability
[   34.993113] Allocate Port Service[0000:00:1c.1:pcie00]
[   34.993142] Allocate Port Service[0000:00:1c.1:pcie02]
[   34.993267] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   34.993327] assign_interrupt_mode Found MSI capability
[   34.993329] Allocate Port Service[0000:00:1c.2:pcie00]
[   34.993359] Allocate Port Service[0000:00:1c.2:pcie02]
[   34.993533] isapnp: Scanning for PnP cards...
[   35.347372] isapnp: No Plug & Play device found
[   35.368565] Real Time Clock Driver v1.12ac
[   35.368621] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.369252] mice: PS/2 mouse device common for all mice
[   35.369757] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.369978] input: Macintosh mouse button emulation as /class/input/input0
[   35.370009] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   35.370054] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   35.370290] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   35.383697] i8042.c: Detected active multiplexing controller, rev 1.1.
[   35.391182] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.391187] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   35.391189] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   35.391192] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   35.391194] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   35.391583] EISA: Probing bus 0 at eisa.0
[   35.391590] Cannot allocate resource for EISA slot 1
[   35.391593] Cannot allocate resource for EISA slot 2
[   35.391595] Cannot allocate resource for EISA slot 3
[   35.391617] EISA: Detected 0 cards.
[   35.421667] TCP cubic registered
[   35.421672] NET: Registered protocol family 1
[   35.421691] Using IPI No-Shortcut mode
[   35.421749] ACPI: (supports S0 S3 S4 S5)
[   35.421795]   Magic number: 12:352:482
[   35.421961] Time: tsc clocksource has been installed.
[   35.422060] Freeing unused kernel memory: 328k freed
[   35.441008] input: AT Translated Set 2 keyboard as /class/input/input1
[   36.653747] Capability LSM initialized
[   36.685270] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   36.685277] ACPI: Processor [CPU0] (supports 8 throttling states)
[   36.685288] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   36.688918] ACPI: Thermal Zone [THRM] (36 C)
[   37.087261] usbcore: registered new interface driver usbfs
[   37.087281] usbcore: registered new interface driver hub
[   37.087302] usbcore: registered new device driver usb
[   37.088112] USB Universal Host Controller Interface driver v3.0
[   37.088161] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   37.088172] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   37.088177] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   37.088295] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   37.088329] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   37.088422] usb usb1: configuration #1 chosen from 1 choice
[   37.088444] hub 1-0:1.0: USB hub found
[   37.088449] hub 1-0:1.0: 2 ports detected
[   37.156149] SCSI subsystem initialized
[   37.179889] libata version 2.20 loaded.
[   37.191430] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   37.191441] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   37.191446] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   37.191468] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   37.191502] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001840
[   37.191583] usb usb2: configuration #1 chosen from 1 choice
[   37.191607] hub 2-0:1.0: USB hub found
[   37.191612] hub 2-0:1.0: 2 ports detected
[   37.295273] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   37.295286] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   37.295290] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   37.295315] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   37.295349] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   37.295432] usb usb3: configuration #1 chosen from 1 choice
[   37.295454] hub 3-0:1.0: USB hub found
[   37.295460] hub 3-0:1.0: 2 ports detected
[    3.684000] Time: hpet clocksource has been installed.
[    3.744000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.744000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.744000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.744000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.744000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    3.744000] usb usb4: configuration #1 chosen from 1 choice
[    3.744000] hub 4-0:1.0: USB hub found
[    3.744000] hub 4-0:1.0: 2 ports detected
[    3.848000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    3.848000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.848000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.848000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.848000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.848000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.848000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0644000
[    3.852000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.852000] usb usb5: configuration #1 chosen from 1 choice
[    3.852000] hub 5-0:1.0: USB hub found
[    3.852000] hub 5-0:1.0: 8 ports detected
[    3.956000] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.956000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.112000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[    4.112000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.112000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    4.112000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[    4.112000] scsi0 : ata_piix
[    4.276000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.276000] ata1.00: ATA-7: ST980811AS, 3.ALD, max UDMA/133
[    4.276000] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.284000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.284000] ata1.00: configured for UDMA/133
[    4.284000] scsi1 : ata_piix
[    4.604000] ata2.00: ATAPI, max UDMA/33
[    4.768000] ata2.00: configured for UDMA/33
[    4.768000] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.AL PQ: 0 ANSI: 5
[    4.768000] scsi 1:0:0:0: CD-ROM            Optiarc  CD-RW CRX880A    KX07 PQ: 0 ANSI: 5
[    4.788000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.788000] sda: Write Protect is off
[    4.788000] sda: Mode Sense: 00 3a 00 00
[    4.788000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.788000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.788000] sda: Write Protect is off
[    4.788000] sda: Mode Sense: 00 3a 00 00
[    4.788000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.788000]  sda: sda1 sda2 < sda5 >
[    4.872000] sd 0:0:0:0: Attached scsi disk sda
[    4.876000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.876000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.884000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.884000] Uniform CD-ROM driver Revision: 3.20
[    4.884000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.084000] Attempting manual resume
[    5.084000] swsusp: Resume From Partition 8:5
[    5.084000] PM: Checking swsusp image.
[    5.084000] PM: Resume from disk failed.
[    5.148000] kjournald starting.  Commit interval 5 seconds
[    5.148000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.868000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.868000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.084000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.096000] agpgart: Detected an Intel 945GM Chipset.
[   17.096000] agpgart: Detected 7932K stolen memory.
[   17.112000] agpgart: AGP aperture is 256M @ 0xc0000000
[   17.940000] ACPI: PCI Interrupt 0000:0a:09.2[A] -> GSI 20 (level, low) -> IRQ 19
[   17.976000] Yenta: CardBus bridge found at 0000:0a:09.0 [1025:0110]
[   17.976000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.976000] Yenta: Routing CardBus interrupts to PCI
[   17.976000] Yenta TI: socket 0000:0a:09.0, mfunc 0x01321b22, devctl 0x66
[   17.984000] intel_rng: FWH not detected
[   18.064000] iTCO_vendor_support: vendor-support=0
[   18.064000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   18.208000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 19
[   18.208000] Socket status: 30000006
[   18.208000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   18.208000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   18.208000] cs: IO port probe 0x3000-0x3fff: clean.
[   18.208000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   18.208000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   18.208000] PCI: Enabling device 0000:02:00.0 (0000 -> 0003)
[   18.208000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.208000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   18.208000] sky2 0000:02:00.0: v1.13 addr 0x34000000 irq 16 Yukon-FE (0xb7) rev 1
[   18.208000] sky2 eth0: addr 00:1b:24:26:5b:e1
[   18.316000] sky2 eth0: enabling interface
[   18.320000] sky2 eth0: ram buffer 4K
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[   18.520000] snd_hda_codec: Unknown symbol snd_ctl_add
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[   18.520000] snd_hda_codec: Unknown symbol snd_card_proc_new
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[   18.520000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[   18.520000] snd_hda_codec: Unknown symbol snd_ctl_new1
[   18.520000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[   18.520000] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_list
[   18.520000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_device_new
[   18.520000] snd_hda_codec: Unknown symbol snd_device_new
[   18.520000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[   18.520000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_new
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_suspend
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   18.520000] snd_hda_intel: Unknown symbol snd_device_new
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_resume
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   18.520000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   18.520000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   18.520000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   18.688000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   18.688000] cs: IO port probe 0x100-0x3af: clean.
[   18.692000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.692000] cs: IO port probe 0x820-0x8ff: clean.
[   18.692000] cs: IO port probe 0xc00-0xcf7: clean.
[   18.696000] cs: IO port probe 0xa00-0xaff: clean.
[   18.748000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   18.752000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   18.752000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.976000] fuse init (API version 7.8)
[   19.036000] lp: driver loaded but no devices found
[   19.100000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   19.196000] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[   19.196000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   19.196000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   19.196000] ndiswrapper (ZwClose:2467): closing handle 0xd82550e8 not implemented
[   19.196000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   19.624000] ndiswrapper: using IRQ 17
[   19.700000] NET: Registered protocol family 17
[   20.132000] wlan0: ethernet device 00:19:7e:4d:5b:1b using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   20.132000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   20.136000] usbcore: registered new interface driver ndiswrapper
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[   20.140000] snd_hda_codec: Unknown symbol snd_ctl_add
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[   20.140000] snd_hda_codec: Unknown symbol snd_card_proc_new
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[   20.140000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[   20.140000] snd_hda_codec: Unknown symbol snd_ctl_new1
[   20.140000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[   20.140000] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_list
[   20.140000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_device_new
[   20.140000] snd_hda_codec: Unknown symbol snd_device_new
[   20.140000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[   20.140000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_new
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_suspend
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   20.144000] snd_hda_intel: Unknown symbol snd_device_new
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_resume
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   20.144000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   20.144000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   20.144000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   20.160000] Adding 1477940k swap on /dev/disk/by-uuid/08ff4819-c6d6-4d01-a9fb-742b1f24f79a.  Priority:-1 extents:1 across:1477940k
[   20.360000] EXT3 FS on sda1, internal journal
[   24.476000] Using specific hotkey driver
[   24.544000] input: Power Button (FF) as /class/input/input3
[   24.548000] ACPI: Power Button (FF) [PWRF]
[   24.580000] input: Lid Switch as /class/input/input4
[   24.584000] ACPI: Lid Switch [LID]
[   24.620000] input: Power Button (CM) as /class/input/input5
[   24.624000] ACPI: Power Button (CM) [PWRB]
[   24.656000] input: Sleep Button (CM) as /class/input/input6
[   24.660000] ACPI: Sleep Button (CM) [SLPB]
[   24.688000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   24.716000] ACPI: ACPI Dock Station Driver 
[   24.920000] ACPI: AC Adapter [ACAD] (off-line)
[   24.984000] ACPI: Battery Slot [BAT1] (battery present)
[   25.044000] ibm_acpi: ec object not found
[   25.100000] pcc_acpi: loading...
[   25.108000] wmi_add device=dddda000
[   25.108000] calling WQBA
[   28.496000] ppdev: user-space parallel port driver
[   29.800000] [drm] Initialized drm 1.1.0 20060810
[   29.956000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.956000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   30.724000] NET: Registered protocol family 10
[   30.724000] lo: Disabled Privacy Extensions
[   30.724000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.936000] apm: BIOS not found.
[   41.344000] wlan0: no IPv6 routers present
[   51.728000] wlan0: no IPv6 routers present
[  112.068000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  112.244000] usb 2-1: configuration #1 chosen from 1 choice
[  112.364000] usbcore: registered new interface driver hiddev
[  112.380000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input7
[  112.380000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
[  112.380000] usbcore: registered new interface driver usbhid
[  112.380000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[  202.532000] usb 5-4: new high speed USB device using ehci_hcd and address 3
[  202.680000] usb 5-4: configuration #1 chosen from 1 choice
keebler@K33bz-mobile:~$ 

```

---

### Post by superprash2003 on 2008-02-29
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by k33bz on 2008-03-01
nope sorry, It dont even recognize the card at all in those menus.

---

### Post by xeth_delta on 2008-03-01
You will need to either reinstall the drivers or recompile them. Here you have a link with explanations on how to do it. If you need any help, please do ask.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
section: Getting the ALSA drivers from a *fresh* kernel (reinstallation)
section: ALSA drivers compilaton (compilation)

---

### Post by Nepherte on 2008-03-01
You probably upgraded your kernel and the alsa drivers you have were not compiled against the newer kernel. You'll have to compile them again.

---

### Post by k33bz on 2008-03-01
> **xeth_delta said:**
> You will need to either reinstall the drivers or recompile them. Here you have a link with explanations on how to do it. If you need any help, please do ask.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
section: Getting the ALSA drivers from a *fresh* kernel (reinstallation)
section: ALSA drivers compilaton (compilation)


tried to do it with fresh kernel, still have same problem
cant get the other one to work, cant find my driver for it, matter fact cant find any driver for anything on the page. So I copied this, hope someone knows what driver module I need.

no drop menu box shown, and I looked at site:
(3) Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).


```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at d0440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

---

### Post by k33bz on 2008-03-01
> **xeth_delta said:**
> You will need to either reinstall the drivers or recompile them. Here you have a link with explanations on how to do it. If you need any help, please do ask.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
section: Getting the ALSA drivers from a *fresh* kernel (reinstallation)
section: ALSA drivers compilaton (compilation)


tried to do it with fresh kernel, still have same problem
cant get the other one to work, cant find my driver for it, matter fact cant find any driver for anything on the page. So I copied this, hope someone knows what driver module I need.

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at d0440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

---

### Post by k33bz on 2008-03-01
> **xeth_delta said:**
> You will need to either reinstall the drivers or recompile them. Here you have a link with explanations on how to do it. If you need any help, please do ask.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
section: Getting the ALSA drivers from a *fresh* kernel (reinstallation)
section: ALSA drivers compilaton (compilation)


tried to do it with fresh kernel, still have same problem
cant get the other one to work, cant find my driver for it, matter fact cant find any driver for anything on the page. So I copied this, hope someone knows what driver module I need.

no drop menu box shown, and I looked at site:
(3) Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).


```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at d0440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

---

### Post by xeth_delta on 2008-03-02
> **k33bz said:**
> tried to do it with fresh kernel, still have same problem
cant get the other one to work, cant find my driver for it, matter fact cant find any driver for anything on the page. So I copied this, hope someone knows what driver module I need.

no drop menu box shown, and I looked at site:
(3) Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).


```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at d0440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

Ok, it seems you will have to recompile the drivers. Let's try the following:
```
sudo lshw -C sound
```
```
lspci | grep -i aud
```
We need to first find out exactly what card you have. Post the output.

---

### Post by hhhhhx on 2008-03-02
K33bz, i have the same problem, if you find a solution, please tell me, i'll work on it too :)

---

### Post by k33bz on 2008-03-03
> **xeth_delta said:**
> Ok, it seems you will have to recompile the drivers. Let's try the following:
```
sudo lshw -C sound
```
```
lspci | grep -i aud
```
We need to first find out exactly what card you have. Post the output.




```
keebler@K33bz-mobile:~$ sudo lshw -C sound
Password:
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:d0440000-d0443fff irq:10
keebler@K33bz-mobile:~$ lspci | grep -i aud
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
keebler@K33bz-mobile:~$ 


```

---

### Post by k33bz on 2008-03-03
> **xhhux said:**
> K33bz, i have the same problem, if you find a solution, please tell me, i'll work on it too :)

will do, let me know if you come up with a solution as well

---

### Post by xeth_delta on 2008-03-03
Now that is funny, your computer has the same southbridge as mine, so I suppose we gan get yours back, too. THe think that could be different is the codec being used, but we need to first load the modules to find that out.

How far have you got with the compilation of the drivers? My next post should explain how to do that.

---

### Post by xeth_delta on 2008-03-03
First, download the drivers from the alsa website: [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

Since you are at it, get also the library and the utilities, to have all of the same version.

Once you have them on your computer uncompress:

```
tar -xjf alsa-driver-1.0.16.tar.bz2
tar -xjf alsa-lib-1.0.16.tar.bz2
tar -xjf alsa-utils-1.0.16.tar.bz2
```

You will need some extra packages for the utilities:
```
sudo aptitude install libncurses5 libncurses5-dev
```

Proceed to each one of the newly unpacked directories
```
cd alsa-lib-1.0.16
./configure
make
sudo make install
```

```
cd alsa-driver-1.0.16
./configure --with cards=hda-intel --with-oss=yes --with-sequencer=yes
make
sudo make install
```

```
cd alsa-utils-1.0.16
./configure
make
sudo make install
```

Do not remove these directories. You will need them, should you want to remove what you just installed. To uninstall, just run a "make uninstall" inside them.

Configure the new modules
```
sudo alsaconf
```
Follow the instructions.

Reboot and see what happens, check if the modules are loaded
```
lsmod | grep -i snd
```
Check if there is sound.
Good luck and let me know if you need further help.

---

### Post by k33bz on 2008-03-03
WOW, AFTER A LONG TIME WITH OUT SOUND ON THAT LINUX HEADER I FINALLY GOT SOUND

Thank you so much xeth_delta, really do appreciate it, this problem was bugging me so much.


Only problem I have with it is that for some reason my left speaker is quite a bit louder than my right one, not much of a problem considering I had no sound, Hated having to go back to my old header (which is very unstable) to watch a movie or hear some music.

So thanks again

---

### Post by xeth_delta on 2008-03-04
You are most welcome! I think it would be possible to solve this issue, too. We need to know what configuration has to be passed when loading the modules. Do the following and post results:
```
sudo /etc/init.d/alsasound restart
```
```
dmesg | grep -i hda
```
or
```
dmesg
```
The relevant line in the case of my system is::
```
[   49.496000] hda_codec: STAC922x, Apple subsys_id=106b2200
```

---

### Post by k33bz on 2008-03-04
from dmesg

wouldnt let me grep it with the other code

```
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6680
[    0.000000] Entering add_active_range(0, 0, 128656) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128656
[    0.000000]   HighMem    128656 ->   128656
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128656
[    0.000000] On node 0 totalpages: 128656
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123587 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 PTLTD                                 ) @ 0x000f6650
[    0.000000] ACPI: XSDT (v001 ACRSYS ACRPRDCT 0x06040000  LTP 0x00000000) @ 0x1f69257e
[    0.000000] ACPI: FADT (v003 INTEL  CALISTGA 0x06040000 ALAN 0x00000001) @ 0x1f69bc38
[    0.000000] ACPI: MADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69bd2c
[    0.000000] ACPI: HPET (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69bd94
[    0.000000] ACPI: MCFG (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69bdcc
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x1f69be08
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1f69be62
[    0.000000] ACPI: SLIC (v001 ACRSYS ACRPRDCT 0x06040000 acer 0x00000000) @ 0x1f69be8a
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050624) @ 0x1f692ad0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x1f6925ea
[    0.000000] ACPI: DSDT (v002 INTEL  CALISTGA 0x06040000 MSFT 0x03000000) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Detected 1600.188 MHz processor.
[   22.578279] Built 1 zonelists.  Total pages: 127651
[   22.578284] Kernel command line: root=UUID=6ad9127b-ab77-4b84-ba4b-9a38ec340bfd ro quiet splash
[   22.578437] mapped APIC to ffffd000 (fee00000)
[   22.578440] mapped IOAPIC to ffffc000 (fec00000)
[   22.578443] Enabling fast FPU save and restore... done.
[   22.578445] Enabling unmasked SIMD FPU exception support... done.
[   22.578453] Initializing CPU#0
[   22.578522] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   22.580220] Console: colour VGA+ 80x25
[   22.580390] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.580556] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.590819] Memory: 498100k/514624k available (1993k kernel code, 16004k reserved, 900k data, 328k init, 0k highmem)
[   22.590828] virtual kernel memory layout:
[   22.590829]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   22.590830]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.590831]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   22.590832]     lowmem  : 0xc0000000 - 0xdf690000   ( 502 MB)
[   22.590834]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   22.590835]       .data : 0xc02f24c9 - 0xc03d36d4   ( 900 kB)
[   22.590836]       .text : 0xc0100000 - 0xc02f24c9   (1993 kB)
[   22.590839] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.590996] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   22.591001] hpet0: 3 64-bit timers, 14318180 Hz
[   22.592006] Using HPET for base-timer
[   22.670877] Calibrating delay using timer specific routine.. 3203.83 BogoMIPS (lpj=6407668)
[   22.670916] Security Framework v1.0.0 initialized
[   22.670920] SELinux:  Disabled at boot.
[   22.670934] Mount-cache hash table entries: 512
[   22.671060] CPU: After generic identify, caps: afebfbff 20100000 00000000 00000000 0000e31d 00000000 00000001
[   22.671068] monitor/mwait feature present.
[   22.671070] using mwait in idle threads.
[   22.671074] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.671076] CPU: L2 cache: 1024K
[   22.671079] CPU: After all inits, caps: afebfbff 20100000 00000000 00003940 0000e31d 00000000 00000001
[   22.671088] Compat vDSO mapped to ffffe000.
[   22.671091] Remapping vsyscall page to ffffe000
[   22.671102] Checking 'hlt' instruction... OK.
[   22.686949] SMP alternatives: switching to UP code
[   22.687124] Freeing SMP alternatives: 11k freed
[   22.687296] Early unpacking initramfs... done
[   23.033537] ACPI: Core revision 20060707
[   23.058807] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   23.063197] CPU0: Intel(R) Celeron(R) M CPU        520  @ 1.60GHz stepping 06
[   23.063222] Total of 1 processors activated (3203.83 BogoMIPS).
[   23.063419] ENABLING IO-APIC IRQs
[   23.063615] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.210083] Brought up 1 CPUs
[   23.210313] Booting paravirtualized kernel on bare hardware
[   23.210393] Time: 17:35:51  Date: 02/04/108
[   23.210417] NET: Registered protocol family 16
[   23.210496] EISA bus registered
[   23.210500] ACPI: bus type pci registered
[   23.223333] PCI: PCI BIOS revision 2.10 entry at 0xfd6c2, last bus=12
[   23.223335] PCI: Using configuration type 1
[   23.223336] Setting up standard PCI resources
[   23.230252] ACPI: Interpreter enabled
[   23.230255] ACPI: Using IOAPIC for interrupt routing
[   23.230561] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.230567] PCI: Probing PCI hardware (bus 00)
[   23.231197] Boot video device is 0000:00:02.0
[   23.231886] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   23.231891] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   23.232756] PCI: Transparent bridge - 0000:00:1e.0
[   23.232829] PCI: Bus #0b (-#0e) is hidden behind transparent bridge #0a (-#0b) (try 'pci=assign-busses')
[   23.232831] Please report the result to linux-kernel to fix this permanently
[   23.232903] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.238359] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   23.238609] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   23.238819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   23.239513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   23.240027] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   23.240277] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   23.240528] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   23.240775] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   23.241027] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   23.241273] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   23.241521] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   23.241768] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   23.262543] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.262553] pnp: PnP ACPI init
[   23.265614] pnp: PnP ACPI: found 9 devices
[   23.265618] PnPBIOS: Disabled by ACPI PNP
[   23.265663] PCI: Using ACPI for IRQ routing
[   23.265666] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.265670] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   23.265673] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   23.265675] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   23.265677] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   23.265679] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   23.265681] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   23.265683] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   23.265685] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   23.265688] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[   23.296739] NET: Registered protocol family 8
[   23.296741] NET: Registered protocol family 20
[   23.297249] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   23.297270] PCI: Bridge: 0000:00:1c.0
[   23.297274]   IO window: 2000-2fff
[   23.297280]   MEM window: 34000000-340fffff
[   23.297285]   PREFETCH window: disabled.
[   23.297300] PCI: Bridge: 0000:00:1c.1
[   23.297301]   IO window: disabled.
[   23.297307]   MEM window: 34100000-341fffff
[   23.297312]   PREFETCH window: disabled.
[   23.297318] PCI: Bridge: 0000:00:1c.2
[   23.297319]   IO window: disabled.
[   23.297325]   MEM window: disabled.
[   23.297329]   PREFETCH window: disabled.
[   23.297337] PCI: Bus 11, cardbus bridge: 0000:0a:09.0
[   23.297339]   IO window: 00003000-000030ff
[   23.297345]   IO window: 00003400-000034ff
[   23.297350]   PREFETCH window: 30000000-33ffffff
[   23.297356]   MEM window: 38000000-3bffffff
[   23.297361] PCI: Bridge: 0000:00:1e.0
[   23.297364]   IO window: 3000-3fff
[   23.297370]   MEM window: d0200000-d02fffff
[   23.297375]   PREFETCH window: 30000000-33ffffff
[   23.297406] PCI: Enabling device 0000:00:1c.0 (0000 -> 0003)
[   23.297413] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.297421] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.297445] PCI: Enabling device 0000:00:1c.1 (0000 -> 0002)
[   23.297450] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   23.297457] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   23.297483] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.297490] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   23.297502] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[   23.297508] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   23.297525] PCI: Enabling device 0000:0a:09.0 (0000 -> 0003)
[   23.297531] ACPI: PCI Interrupt 0000:0a:09.0[A] -> GSI 20 (level, low) -> IRQ 19
[   23.297560] NET: Registered protocol family 2
[   23.325925] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   23.325992] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   23.326062] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   23.326100] TCP: Hash tables configured (established 16384 bind 8192)
[   23.326102] TCP reno registered
[   23.337963] checking if image is initramfs... it is
[   24.018126] Freeing initrd memory: 7868k freed
[   24.018341] Simple Boot Flag at 0x36 set to 0x1
[   24.018648] audit: initializing netlink socket (disabled)
[   24.018663] audit(1204652151.508:1): initialized
[   24.018772] VFS: Disk quotas dquot_6.5.1
[   24.018788] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.018835] io scheduler noop registered
[   24.018838] io scheduler anticipatory registered
[   24.018840] io scheduler deadline registered
[   24.018846] io scheduler cfq registered (default)
[   24.019087] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.019149] assign_interrupt_mode Found MSI capability
[   24.019152] Allocate Port Service[0000:00:1c.0:pcie00]
[   24.019183] Allocate Port Service[0000:00:1c.0:pcie02]
[   24.019308] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   24.019368] assign_interrupt_mode Found MSI capability
[   24.019371] Allocate Port Service[0000:00:1c.1:pcie00]
[   24.019400] Allocate Port Service[0000:00:1c.1:pcie02]
[   24.019524] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   24.019585] assign_interrupt_mode Found MSI capability
[   24.019587] Allocate Port Service[0000:00:1c.2:pcie00]
[   24.019617] Allocate Port Service[0000:00:1c.2:pcie02]
[   24.019791] isapnp: Scanning for PnP cards...
[   24.373651] isapnp: No Plug & Play device found
[   24.394773] Real Time Clock Driver v1.12ac
[   24.394829] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.395461] mice: PS/2 mouse device common for all mice
[   24.395965] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.396182] input: Macintosh mouse button emulation as /class/input/input0
[   24.396214] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.396258] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.396497] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.410949] i8042.c: Detected active multiplexing controller, rev 1.1.
[   24.417706] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.417711] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   24.417714] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   24.417716] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   24.417718] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   24.418103] EISA: Probing bus 0 at eisa.0
[   24.418111] Cannot allocate resource for EISA slot 1
[   24.418114] Cannot allocate resource for EISA slot 2
[   24.418116] Cannot allocate resource for EISA slot 3
[   24.418138] EISA: Detected 0 cards.
[   24.448194] TCP cubic registered
[   24.448200] NET: Registered protocol family 1
[   24.448222] Using IPI No-Shortcut mode
[   24.448278] ACPI: (supports S0 S3 S4 S5)
[   24.448324]   Magic number: 0:114:592
[   24.448584] Freeing unused kernel memory: 328k freed
[   24.452161] Time: tsc clocksource has been installed.
[   24.468225] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.679936] Capability LSM initialized
[   25.711325] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   25.711332] ACPI: Processor [CPU0] (supports 8 throttling states)
[   25.711342] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   25.714976] ACPI: Thermal Zone [THRM] (31 C)
[   26.105293] usbcore: registered new interface driver usbfs
[   26.105314] usbcore: registered new interface driver hub
[   26.105334] usbcore: registered new device driver usb
[   26.106139] USB Universal Host Controller Interface driver v3.0
[   26.106185] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   26.106196] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   26.106200] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   26.106316] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   26.106351] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   26.106443] usb usb1: configuration #1 chosen from 1 choice
[   26.106467] hub 1-0:1.0: USB hub found
[   26.106472] hub 1-0:1.0: 2 ports detected
[   26.209644] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   26.209656] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   26.209661] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   26.209684] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   26.209719] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001840
[   26.209803] usb usb2: configuration #1 chosen from 1 choice
[   26.209825] hub 2-0:1.0: USB hub found
[   26.209831] hub 2-0:1.0: 2 ports detected
[   26.240072] SCSI subsystem initialized
[   26.244984] libata version 2.20 loaded.
[   26.313471] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   26.313484] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   26.313489] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   26.313517] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   26.313552] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   26.313638] usb usb3: configuration #1 chosen from 1 choice
[   26.313660] hub 3-0:1.0: USB hub found
[   26.313666] hub 3-0:1.0: 2 ports detected
[    3.672000] Time: hpet clocksource has been installed.
[    3.728000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.728000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.728000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.728000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.728000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    3.728000] usb usb4: configuration #1 chosen from 1 choice
[    3.728000] hub 4-0:1.0: USB hub found
[    3.728000] hub 4-0:1.0: 2 ports detected
[    3.832000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    3.832000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.832000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.832000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.832000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.832000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.832000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0644000
[    3.836000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.836000] usb usb5: configuration #1 chosen from 1 choice
[    3.836000] hub 5-0:1.0: USB hub found
[    3.836000] hub 5-0:1.0: 8 ports detected
[    3.864000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.940000] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.940000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.096000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[    4.096000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.096000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    4.096000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[    4.096000] scsi0 : ata_piix
[    4.260000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.260000] ata1.00: ATA-7: ST980811AS, 3.ALD, max UDMA/133
[    4.260000] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.268000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.268000] ata1.00: configured for UDMA/133
[    4.268000] scsi1 : ata_piix
[    4.480000] usb 5-4: new high speed USB device using ehci_hcd and address 3
[    4.588000] ata2.00: ATAPI, max UDMA/33
[    4.612000] usb 5-4: configuration #1 chosen from 1 choice
[    4.752000] ata2.00: configured for UDMA/33
[    4.752000] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.AL PQ: 0 ANSI: 5
[    4.752000] scsi 1:0:0:0: CD-ROM            Optiarc  CD-RW CRX880A    KX07 PQ: 0 ANSI: 5
[    4.772000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.772000] sda: Write Protect is off
[    4.772000] sda: Mode Sense: 00 3a 00 00
[    4.772000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.772000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.772000] sda: Write Protect is off
[    4.772000] sda: Mode Sense: 00 3a 00 00
[    4.772000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.772000]  sda: sda1 sda2 < sda5 >
[    4.820000] sd 0:0:0:0: Attached scsi disk sda
[    4.824000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.824000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.836000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.836000] Uniform CD-ROM driver Revision: 3.20
[    4.836000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.852000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[    4.960000] Attempting manual resume
[    4.960000] swsusp: Resume From Partition 8:5
[    4.960000] PM: Checking swsusp image.
[    4.960000] PM: Resume from disk failed.
[    5.004000] kjournald starting.  Commit interval 5 seconds
[    5.004000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.028000] usb 2-1: configuration #1 chosen from 1 choice
[   16.784000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.788000] agpgart: Detected an Intel 945GM Chipset.
[   16.788000] agpgart: Detected 7932K stolen memory.
[   16.804000] agpgart: AGP aperture is 256M @ 0xc0000000
[   16.812000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.816000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.584000] intel_rng: FWH not detected
[   17.720000] iTCO_vendor_support: vendor-support=0
[   17.724000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   17.760000] ACPI: PCI Interrupt 0000:0a:09.2[A] -> GSI 20 (level, low) -> IRQ 19
[   17.796000] Yenta: CardBus bridge found at 0000:0a:09.0 [1025:0110]
[   17.796000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.796000] Yenta: Routing CardBus interrupts to PCI
[   17.796000] Yenta TI: socket 0000:0a:09.0, mfunc 0x01321b22, devctl 0x66
[   17.824000] usbcore: registered new interface driver hiddev
[   17.936000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[   17.936000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
[   17.936000] usbcore: registered new interface driver usbhid
[   17.936000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   18.048000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 19
[   18.048000] Socket status: 30000006
[   18.048000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   18.048000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   18.048000] cs: IO port probe 0x3000-0x3fff: clean.
[   18.048000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   18.048000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   18.048000] PCI: Enabling device 0000:02:00.0 (0000 -> 0003)
[   18.048000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.048000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   18.048000] sky2 0000:02:00.0: v1.13 addr 0x34000000 irq 16 Yukon-FE (0xb7) rev 1
[   18.048000] sky2 eth0: addr 00:1b:24:26:5b:e1
[   18.232000] sky2 eth0: enabling interface
[   18.236000] sky2 eth0: ram buffer 4K
[   18.292000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   18.292000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   18.460000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   18.520000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   18.524000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   18.524000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.536000] cs: IO port probe 0x100-0x3af: clean.
[   18.536000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.536000] cs: IO port probe 0x820-0x8ff: clean.
[   18.536000] cs: IO port probe 0xc00-0xcf7: clean.
[   18.540000] cs: IO port probe 0xa00-0xaff: clean.
[   18.832000] fuse init (API version 7.8)
[   18.892000] lp: driver loaded but no devices found
[   18.948000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   19.028000] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[   19.028000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   19.028000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   19.028000] ndiswrapper (ZwClose:2467): closing handle 0xd6fb46e8 not implemented
[   19.028000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   19.456000] ndiswrapper: using IRQ 17
[   19.524000] NET: Registered protocol family 17
[   20.000000] wlan0: ethernet device 00:19:7e:4d:5b:1b using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   20.000000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   20.212000] usbcore: registered new interface driver ndiswrapper
[   20.232000] Adding 1477940k swap on /dev/disk/by-uuid/08ff4819-c6d6-4d01-a9fb-742b1f24f79a.  Priority:-1 extents:1 across:1477940k
[   20.344000] EXT3 FS on sda1, internal journal
[   24.608000] Using specific hotkey driver
[   24.684000] input: Power Button (FF) as /class/input/input4
[   24.688000] ACPI: Power Button (FF) [PWRF]
[   24.724000] input: Lid Switch as /class/input/input5
[   24.728000] ACPI: Lid Switch [LID]
[   24.764000] input: Power Button (CM) as /class/input/input6
[   24.764000] ACPI: Power Button (CM) [PWRB]
[   24.800000] input: Sleep Button (CM) as /class/input/input7
[   24.804000] ACPI: Sleep Button (CM) [SLPB]
[   24.824000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   24.852000] ACPI: ACPI Dock Station Driver 
[   25.068000] ACPI: AC Adapter [ACAD] (on-line)
[   25.128000] ACPI: Battery Slot [BAT1] (battery present)
[   25.184000] ibm_acpi: ec object not found
[   25.252000] pcc_acpi: loading...
[   25.260000] wmi_add device=ddd94000
[   25.260000] calling WQBA
[   28.668000] ppdev: user-space parallel port driver
[   29.948000] [drm] Initialized drm 1.1.0 20060810
[   29.972000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.976000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   37.408000] apm: BIOS not found.
[   46.420000] NET: Registered protocol family 10
[   46.420000] lo: Disabled Privacy Extensions
[   46.420000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.924000] wlan0: no IPv6 routers present
[   74.992000] NET: Registered protocol family 4
[   75.036000] NET: Registered protocol family 3
[   75.068000] NET: Registered protocol family 5
[  604.416000] usb 5-4: USB disconnect, address 3
[  612.928000] usb 5-4: new high speed USB device using ehci_hcd and address 4
[  613.076000] usb 5-4: configuration #1 chosen from 1 choice
keebler@K33bz-mobile:~$ 


```

---

### Post by xeth_delta on 2008-03-04
What brand and model is your computer?
Try
```
sudo /etc/init.d/alsasound stop
```
```
sudo modprobe snd-hda-intel
```
Any messages? Look again with dmesg.

---

### Post by k33bz on 2008-03-05
Its an Acer Laptop model aspire 3680-2419

ya i know not the best laptop to use linux on, but i really hate windows, lol

```
keebler@K33bz-mobile:~$ sudo /etc/init.d/alsasound stop
Password:
Shutting down sound driver: ERROR: Module snd_hda_intel is in use
ERROR: Module snd_mixer_oss is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd is in use by snd_hda_intel,snd_mixer_oss,snd_pcm,snd_hwdep,snd_timer
done

```

```
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6680
[    0.000000] Entering add_active_range(0, 0, 128656) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128656
[    0.000000]   HighMem    128656 ->   128656
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128656
[    0.000000] On node 0 totalpages: 128656
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123587 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 PTLTD                                 ) @ 0x000f6650
[    0.000000] ACPI: XSDT (v001 ACRSYS ACRPRDCT 0x06040000  LTP 0x00000000) @ 0x1f69257e
[    0.000000] ACPI: FADT (v003 INTEL  CALISTGA 0x06040000 ALAN 0x00000001) @ 0x1f69bc38
[    0.000000] ACPI: MADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69bd2c
[    0.000000] ACPI: HPET (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69bd94
[    0.000000] ACPI: MCFG (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69bdcc
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x1f69be08
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1f69be62
[    0.000000] ACPI: SLIC (v001 ACRSYS ACRPRDCT 0x06040000 acer 0x00000000) @ 0x1f69be8a
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050624) @ 0x1f692ad0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x1f6925ea
[    0.000000] ACPI: DSDT (v002 INTEL  CALISTGA 0x06040000 MSFT 0x03000000) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Detected 1600.188 MHz processor.
[   22.578279] Built 1 zonelists.  Total pages: 127651
[   22.578284] Kernel command line: root=UUID=6ad9127b-ab77-4b84-ba4b-9a38ec340bfd ro quiet splash
[   22.578437] mapped APIC to ffffd000 (fee00000)
[   22.578440] mapped IOAPIC to ffffc000 (fec00000)
[   22.578443] Enabling fast FPU save and restore... done.
[   22.578445] Enabling unmasked SIMD FPU exception support... done.
[   22.578453] Initializing CPU#0
[   22.578522] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   22.580220] Console: colour VGA+ 80x25
[   22.580390] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.580556] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.590819] Memory: 498100k/514624k available (1993k kernel code, 16004k reserved, 900k data, 328k init, 0k highmem)
[   22.590828] virtual kernel memory layout:
[   22.590829]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   22.590830]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.590831]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   22.590832]     lowmem  : 0xc0000000 - 0xdf690000   ( 502 MB)
[   22.590834]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   22.590835]       .data : 0xc02f24c9 - 0xc03d36d4   ( 900 kB)
[   22.590836]       .text : 0xc0100000 - 0xc02f24c9   (1993 kB)
[   22.590839] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.590996] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   22.591001] hpet0: 3 64-bit timers, 14318180 Hz
[   22.592006] Using HPET for base-timer
[   22.670877] Calibrating delay using timer specific routine.. 3203.83 BogoMIPS (lpj=6407668)
[   22.670916] Security Framework v1.0.0 initialized
[   22.670920] SELinux:  Disabled at boot.
[   22.670934] Mount-cache hash table entries: 512
[   22.671060] CPU: After generic identify, caps: afebfbff 20100000 00000000 00000000 0000e31d 00000000 00000001
[   22.671068] monitor/mwait feature present.
[   22.671070] using mwait in idle threads.
[   22.671074] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.671076] CPU: L2 cache: 1024K
[   22.671079] CPU: After all inits, caps: afebfbff 20100000 00000000 00003940 0000e31d 00000000 00000001
[   22.671088] Compat vDSO mapped to ffffe000.
[   22.671091] Remapping vsyscall page to ffffe000
[   22.671102] Checking 'hlt' instruction... OK.
[   22.686949] SMP alternatives: switching to UP code
[   22.687124] Freeing SMP alternatives: 11k freed
[   22.687296] Early unpacking initramfs... done
[   23.033537] ACPI: Core revision 20060707
[   23.058807] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   23.063197] CPU0: Intel(R) Celeron(R) M CPU        520  @ 1.60GHz stepping 06
[   23.063222] Total of 1 processors activated (3203.83 BogoMIPS).
[   23.063419] ENABLING IO-APIC IRQs
[   23.063615] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.210083] Brought up 1 CPUs
[   23.210313] Booting paravirtualized kernel on bare hardware
[   23.210393] Time: 17:35:51  Date: 02/04/108
[   23.210417] NET: Registered protocol family 16
[   23.210496] EISA bus registered
[   23.210500] ACPI: bus type pci registered
[   23.223333] PCI: PCI BIOS revision 2.10 entry at 0xfd6c2, last bus=12
[   23.223335] PCI: Using configuration type 1
[   23.223336] Setting up standard PCI resources
[   23.230252] ACPI: Interpreter enabled
[   23.230255] ACPI: Using IOAPIC for interrupt routing
[   23.230561] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.230567] PCI: Probing PCI hardware (bus 00)
[   23.231197] Boot video device is 0000:00:02.0
[   23.231886] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   23.231891] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   23.232756] PCI: Transparent bridge - 0000:00:1e.0
[   23.232829] PCI: Bus #0b (-#0e) is hidden behind transparent bridge #0a (-#0b) (try 'pci=assign-busses')
[   23.232831] Please report the result to linux-kernel to fix this permanently
[   23.232903] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.238359] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   23.238609] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   23.238819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   23.239513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   23.240027] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   23.240277] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   23.240528] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   23.240775] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   23.241027] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   23.241273] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   23.241521] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   23.241768] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   23.262543] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.262553] pnp: PnP ACPI init
[   23.265614] pnp: PnP ACPI: found 9 devices
[   23.265618] PnPBIOS: Disabled by ACPI PNP
[   23.265663] PCI: Using ACPI for IRQ routing
[   23.265666] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.265670] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   23.265673] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   23.265675] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   23.265677] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   23.265679] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   23.265681] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   23.265683] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   23.265685] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   23.265688] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[   23.296739] NET: Registered protocol family 8
[   23.296741] NET: Registered protocol family 20
[   23.297249] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   23.297270] PCI: Bridge: 0000:00:1c.0
[   23.297274]   IO window: 2000-2fff
[   23.297280]   MEM window: 34000000-340fffff
[   23.297285]   PREFETCH window: disabled.
[   23.297300] PCI: Bridge: 0000:00:1c.1
[   23.297301]   IO window: disabled.
[   23.297307]   MEM window: 34100000-341fffff
[   23.297312]   PREFETCH window: disabled.
[   23.297318] PCI: Bridge: 0000:00:1c.2
[   23.297319]   IO window: disabled.
[   23.297325]   MEM window: disabled.
[   23.297329]   PREFETCH window: disabled.
[   23.297337] PCI: Bus 11, cardbus bridge: 0000:0a:09.0
[   23.297339]   IO window: 00003000-000030ff
[   23.297345]   IO window: 00003400-000034ff
[   23.297350]   PREFETCH window: 30000000-33ffffff
[   23.297356]   MEM window: 38000000-3bffffff
[   23.297361] PCI: Bridge: 0000:00:1e.0
[   23.297364]   IO window: 3000-3fff
[   23.297370]   MEM window: d0200000-d02fffff
[   23.297375]   PREFETCH window: 30000000-33ffffff
[   23.297406] PCI: Enabling device 0000:00:1c.0 (0000 -> 0003)
[   23.297413] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.297421] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.297445] PCI: Enabling device 0000:00:1c.1 (0000 -> 0002)
[   23.297450] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   23.297457] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   23.297483] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.297490] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   23.297502] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[   23.297508] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   23.297525] PCI: Enabling device 0000:0a:09.0 (0000 -> 0003)
[   23.297531] ACPI: PCI Interrupt 0000:0a:09.0[A] -> GSI 20 (level, low) -> IRQ 19
[   23.297560] NET: Registered protocol family 2
[   23.325925] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   23.325992] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   23.326062] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   23.326100] TCP: Hash tables configured (established 16384 bind 8192)
[   23.326102] TCP reno registered
[   23.337963] checking if image is initramfs... it is
[   24.018126] Freeing initrd memory: 7868k freed
[   24.018341] Simple Boot Flag at 0x36 set to 0x1
[   24.018648] audit: initializing netlink socket (disabled)
[   24.018663] audit(1204652151.508:1): initialized
[   24.018772] VFS: Disk quotas dquot_6.5.1
[   24.018788] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.018835] io scheduler noop registered
[   24.018838] io scheduler anticipatory registered
[   24.018840] io scheduler deadline registered
[   24.018846] io scheduler cfq registered (default)
[   24.019087] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.019149] assign_interrupt_mode Found MSI capability
[   24.019152] Allocate Port Service[0000:00:1c.0:pcie00]
[   24.019183] Allocate Port Service[0000:00:1c.0:pcie02]
[   24.019308] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   24.019368] assign_interrupt_mode Found MSI capability
[   24.019371] Allocate Port Service[0000:00:1c.1:pcie00]
[   24.019400] Allocate Port Service[0000:00:1c.1:pcie02]
[   24.019524] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   24.019585] assign_interrupt_mode Found MSI capability
[   24.019587] Allocate Port Service[0000:00:1c.2:pcie00]
[   24.019617] Allocate Port Service[0000:00:1c.2:pcie02]
[   24.019791] isapnp: Scanning for PnP cards...
[   24.373651] isapnp: No Plug & Play device found
[   24.394773] Real Time Clock Driver v1.12ac
[   24.394829] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.395461] mice: PS/2 mouse device common for all mice
[   24.395965] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.396182] input: Macintosh mouse button emulation as /class/input/input0
[   24.396214] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.396258] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.396497] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.410949] i8042.c: Detected active multiplexing controller, rev 1.1.
[   24.417706] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.417711] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   24.417714] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   24.417716] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   24.417718] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   24.418103] EISA: Probing bus 0 at eisa.0
[   24.418111] Cannot allocate resource for EISA slot 1
[   24.418114] Cannot allocate resource for EISA slot 2
[   24.418116] Cannot allocate resource for EISA slot 3
[   24.418138] EISA: Detected 0 cards.
[   24.448194] TCP cubic registered
[   24.448200] NET: Registered protocol family 1
[   24.448222] Using IPI No-Shortcut mode
[   24.448278] ACPI: (supports S0 S3 S4 S5)
[   24.448324]   Magic number: 0:114:592
[   24.448584] Freeing unused kernel memory: 328k freed
[   24.452161] Time: tsc clocksource has been installed.
[   24.468225] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.679936] Capability LSM initialized
[   25.711325] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   25.711332] ACPI: Processor [CPU0] (supports 8 throttling states)
[   25.711342] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   25.714976] ACPI: Thermal Zone [THRM] (31 C)
[   26.105293] usbcore: registered new interface driver usbfs
[   26.105314] usbcore: registered new interface driver hub
[   26.105334] usbcore: registered new device driver usb
[   26.106139] USB Universal Host Controller Interface driver v3.0
[   26.106185] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   26.106196] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   26.106200] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   26.106316] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   26.106351] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   26.106443] usb usb1: configuration #1 chosen from 1 choice
[   26.106467] hub 1-0:1.0: USB hub found
[   26.106472] hub 1-0:1.0: 2 ports detected
[   26.209644] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   26.209656] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   26.209661] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   26.209684] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   26.209719] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001840
[   26.209803] usb usb2: configuration #1 chosen from 1 choice
[   26.209825] hub 2-0:1.0: USB hub found
[   26.209831] hub 2-0:1.0: 2 ports detected
[   26.240072] SCSI subsystem initialized
[   26.244984] libata version 2.20 loaded.
[   26.313471] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   26.313484] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   26.313489] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   26.313517] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   26.313552] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   26.313638] usb usb3: configuration #1 chosen from 1 choice
[   26.313660] hub 3-0:1.0: USB hub found
[   26.313666] hub 3-0:1.0: 2 ports detected
[    3.672000] Time: hpet clocksource has been installed.
[    3.728000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.728000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.728000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.728000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.728000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    3.728000] usb usb4: configuration #1 chosen from 1 choice
[    3.728000] hub 4-0:1.0: USB hub found
[    3.728000] hub 4-0:1.0: 2 ports detected
[    3.832000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    3.832000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.832000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.832000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.832000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.832000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.832000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0644000
[    3.836000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.836000] usb usb5: configuration #1 chosen from 1 choice
[    3.836000] hub 5-0:1.0: USB hub found
[    3.836000] hub 5-0:1.0: 8 ports detected
[    3.864000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.940000] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.940000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.096000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[    4.096000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.096000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    4.096000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[    4.096000] scsi0 : ata_piix
[    4.260000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.260000] ata1.00: ATA-7: ST980811AS, 3.ALD, max UDMA/133
[    4.260000] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.268000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.268000] ata1.00: configured for UDMA/133
[    4.268000] scsi1 : ata_piix
[    4.480000] usb 5-4: new high speed USB device using ehci_hcd and address 3
[    4.588000] ata2.00: ATAPI, max UDMA/33
[    4.612000] usb 5-4: configuration #1 chosen from 1 choice
[    4.752000] ata2.00: configured for UDMA/33
[    4.752000] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.AL PQ: 0 ANSI: 5
[    4.752000] scsi 1:0:0:0: CD-ROM            Optiarc  CD-RW CRX880A    KX07 PQ: 0 ANSI: 5
[    4.772000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.772000] sda: Write Protect is off
[    4.772000] sda: Mode Sense: 00 3a 00 00
[    4.772000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.772000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.772000] sda: Write Protect is off
[    4.772000] sda: Mode Sense: 00 3a 00 00
[    4.772000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.772000]  sda: sda1 sda2 < sda5 >
[    4.820000] sd 0:0:0:0: Attached scsi disk sda
[    4.824000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.824000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.836000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.836000] Uniform CD-ROM driver Revision: 3.20
[    4.836000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.852000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[    4.960000] Attempting manual resume
[    4.960000] swsusp: Resume From Partition 8:5
[    4.960000] PM: Checking swsusp image.
[    4.960000] PM: Resume from disk failed.
[    5.004000] kjournald starting.  Commit interval 5 seconds
[    5.004000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.028000] usb 2-1: configuration #1 chosen from 1 choice
[   16.784000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.788000] agpgart: Detected an Intel 945GM Chipset.
[   16.788000] agpgart: Detected 7932K stolen memory.
[   16.804000] agpgart: AGP aperture is 256M @ 0xc0000000
[   16.812000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.816000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.584000] intel_rng: FWH not detected
[   17.720000] iTCO_vendor_support: vendor-support=0
[   17.724000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   17.760000] ACPI: PCI Interrupt 0000:0a:09.2[A] -> GSI 20 (level, low) -> IRQ 19
[   17.796000] Yenta: CardBus bridge found at 0000:0a:09.0 [1025:0110]
[   17.796000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.796000] Yenta: Routing CardBus interrupts to PCI
[   17.796000] Yenta TI: socket 0000:0a:09.0, mfunc 0x01321b22, devctl 0x66
[   17.824000] usbcore: registered new interface driver hiddev
[   17.936000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[   17.936000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
[   17.936000] usbcore: registered new interface driver usbhid
[   17.936000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   18.048000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 19
[   18.048000] Socket status: 30000006
[   18.048000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   18.048000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   18.048000] cs: IO port probe 0x3000-0x3fff: clean.
[   18.048000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   18.048000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   18.048000] PCI: Enabling device 0000:02:00.0 (0000 -> 0003)
[   18.048000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.048000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   18.048000] sky2 0000:02:00.0: v1.13 addr 0x34000000 irq 16 Yukon-FE (0xb7) rev 1
[   18.048000] sky2 eth0: addr 00:1b:24:26:5b:e1
[   18.232000] sky2 eth0: enabling interface
[   18.236000] sky2 eth0: ram buffer 4K
[   18.292000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   18.292000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   18.460000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   18.520000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   18.524000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   18.524000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.536000] cs: IO port probe 0x100-0x3af: clean.
[   18.536000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.536000] cs: IO port probe 0x820-0x8ff: clean.
[   18.536000] cs: IO port probe 0xc00-0xcf7: clean.
[   18.540000] cs: IO port probe 0xa00-0xaff: clean.
[   18.832000] fuse init (API version 7.8)
[   18.892000] lp: driver loaded but no devices found
[   18.948000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   19.028000] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[   19.028000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   19.028000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   19.028000] ndiswrapper (ZwClose:2467): closing handle 0xd6fb46e8 not implemented
[   19.028000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   19.456000] ndiswrapper: using IRQ 17
[   19.524000] NET: Registered protocol family 17
[   20.000000] wlan0: ethernet device 00:19:7e:4d:5b:1b using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   20.000000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   20.212000] usbcore: registered new interface driver ndiswrapper
[   20.232000] Adding 1477940k swap on /dev/disk/by-uuid/08ff4819-c6d6-4d01-a9fb-742b1f24f79a.  Priority:-1 extents:1 across:1477940k
[   20.344000] EXT3 FS on sda1, internal journal
[   24.608000] Using specific hotkey driver
[   24.684000] input: Power Button (FF) as /class/input/input4
[   24.688000] ACPI: Power Button (FF) [PWRF]
[   24.724000] input: Lid Switch as /class/input/input5
[   24.728000] ACPI: Lid Switch [LID]
[   24.764000] input: Power Button (CM) as /class/input/input6
[   24.764000] ACPI: Power Button (CM) [PWRB]
[   24.800000] input: Sleep Button (CM) as /class/input/input7
[   24.804000] ACPI: Sleep Button (CM) [SLPB]
[   24.824000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   24.852000] ACPI: ACPI Dock Station Driver 
[   25.068000] ACPI: AC Adapter [ACAD] (on-line)
[   25.128000] ACPI: Battery Slot [BAT1] (battery present)
[   25.184000] ibm_acpi: ec object not found
[   25.252000] pcc_acpi: loading...
[   25.260000] wmi_add device=ddd94000
[   25.260000] calling WQBA
[   28.668000] ppdev: user-space parallel port driver
[   29.948000] [drm] Initialized drm 1.1.0 20060810
[   29.972000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.976000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   37.408000] apm: BIOS not found.
[   46.420000] NET: Registered protocol family 10
[   46.420000] lo: Disabled Privacy Extensions
[   46.420000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.924000] wlan0: no IPv6 routers present
[   74.992000] NET: Registered protocol family 4
[   75.036000] NET: Registered protocol family 3
[   75.068000] NET: Registered protocol family 5
[  604.416000] usb 5-4: USB disconnect, address 3
[  612.928000] usb 5-4: new high speed USB device using ehci_hcd and address 4
[  613.076000] usb 5-4: configuration #1 chosen from 1 choice
[37697.100000] cdrom: This disc doesn't have any tracks I recognize!
[37864.360000] ISO 9660 Extensions: Microsoft Joliet Level 3
[37864.444000] ISO 9660 Extensions: RRIP_1991A
[40099.116000] wlan0: no IPv6 routers present
keebler@K33bz-mobile:~$ 

```

---

### Post by xeth_delta on 2008-03-05
Your laptop is not bad for linux, don't worry. I don't like windows either.
Back on-topic, for some reason you cannot unload the modules. Try
```
sudo modprobe snd-hda-intel
dmesg
```
Look for those lines.
In the alsa source directory there is a file called "alsa-kernel/Documentation/ALSA-Configuration.txt" If you search for the hda-intel section you will see different codecs used for the chipset, and possible models and brands of computers. In the list there is the acer option. Try using it in the file "/etc/modprobe.d/alsa-base. Make a backup of the file and near the end append the line:
```
options snd-hda-intel model=acer
```
if that is not enough try also adding
```
options snd-hda-intel position_fix=1
```
Reboot to make the modules reload, since it seems not to be possible in your system via "alsasound restart".

---

### Post by k33bz on 2008-03-05
That made it a lil better, but still quite a bit of difference, nothing I cant live with though

---

### Post by xeth_delta on 2008-03-05
> **k33bz said:**
> That made it a lil better, but still quite a bit of difference, nothing I cant live with though

I guess that an option would then be to simply shift the balance, for example with alsamixer or what you use in Gnome.

---

### Post by k33bz on 2008-03-06
> **xeth_delta said:**
> I guess that an option would then be to simply shift the balance, for example with alsamixer or what you use in Gnome.

ya thats what i been doin, Didnt seem to have any other choice, lol


Got a diferent question though. I know its possible cause I had it set up that way before, just dont know how i did it, How do I save my configurations to my alsa mixer, instead of every time I log in changing my volume controls to the way I want them, for example, my surround settings, everytime I log in it is muted and turned all the way down. How do I fix that?

---

### Post by xeth_delta on 2008-03-06
> **k33bz said:**
> ya thats what i been doin, Didnt seem to have any other choice, lol


Got a diferent question though. I know its possible cause I had it set up that way before, just dont know how i did it, How do I save my configurations to my alsa mixer, instead of every time I log in changing my volume controls to the way I want them, for example, my surround settings, everytime I log in it is muted and turned all the way down. How do I fix that?

You can try with alsact. Change the mixer as you want, and:

```
alsactl store 0
```

---

### Post by xeth_delta on 2008-03-06
One more thing, though. If you could only load the modules we could now what codec is exactly being used and hence know what other parameters to pass.

Did you try "sudo modprobe snd-hda-intel" without restarting alsa and checking dmesg? If that does not work, try restarting in safe mode and try modprobe and dmesg.

---

### Post by k33bz on 2008-03-06
what am i looking for when i run dmesg?

---

### Post by xeth_delta on 2008-03-06
> **k33bz said:**
> what am i looking for when i run dmesg?

For something like:
```
[   49.496000] hda_codec: STAC922x, Apple subsys_id=106b2200
```
The STAC922x is, in the case of my sysem, the used codec.

---

### Post by k33bz on 2008-03-06
> **xeth_delta said:**
> For something like:
```
[   49.496000] hda_codec: STAC922x, Apple subsys_id=106b2200
```
The STAC922x is, in the case of my sysem, the used codec.

ok i have looked over it twice it dont see my codecs at all

---

### Post by xeth_delta on 2008-03-06
> **k33bz said:**
> ok i have looked over it twice it dont see my codecs at all

Even after logging in safe mode / pure command line? Ok, I have yet another suggestion. It would imply black-listing the sound module temorarily and loading it manually. To blacklist the module
```
gksu /etc/modprobe.d/blacklist
```
add at the end a "blacklist snd-hda-intel" and save. Restart, modprobe, dmesg, you know. Is there any relevant info about the sound card?
After that remove the blacklist line and save.

---

### Post by xeth_delta on 2008-03-22
It's been a long time since the post started, but I think that for the sake of completeness I should post a command that would help identify what codec the sound card has. I found this in another thread and it actually looks obvious now:
```
grep Codec /proc/asound/card0/codec#*
```

---

