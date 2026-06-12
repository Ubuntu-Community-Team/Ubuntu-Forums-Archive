---
title: "No Sound After Reboot, Ubutu 7 (Feisty Fawn)"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by kettle on 2007-05-07
Hi, 

  I just installed Ubuntu for the first time about a week ago.  Everything was running smoothly until today when, after a reboot, the sound on my machine simply stopped working.  I've made no changes to anything other than the screen resolution and cannot for the life of me figure out what is going wrong.  I had a similar problem happen in Fedora Core 6, which in part was what led me to try Ubuntu, having heard that it was a bit more user friendly.  However after spending several hours searching, googling and pulling my hair out over this basic feature which I think ought to 'just work' I'm starting to wonder if this is worth the hassle...

  I found a number of similar problems and solutions during the course of my googling, including:

**deleting the alsa conf file and restarting:
$ sudo rm /var/lib/alsa/asound.state 
$ sudo /etc/init.d/alsa-utils restart

**reinstalling the entire sound system: 
$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
$ sudo apt-get install gdm ubuntu-desktop
$ sudo apt-get install linux-sound-base alsa-base alsa-utils

however, none of these solved my problem. Below is my dmesg output, please let me know what other bits of info might be of use.  Again, the sound worked perfectly fine directly following the install, and through several restarts however after the last restart there was simply nothing.  Any help will be greatly appreciated:


[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fde0000 end: 000000007fee0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007fee0000 size: 0000000000003000 end: 000000007fee3000 type: 4
[    0.000000] copy_e820_map() start: 000000007fee3000 size: 000000000000d000 end: 000000007fef0000 type: 3
[    0.000000] copy_e820_map() start: 000000007fef0000 size: 0000000000010000 end: 000000007ff00000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4fb0
[    0.000000] Entering add_active_range(0, 0, 524000) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524000
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524000
[    0.000000] On node 0 totalpages: 524000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292323 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 IntelR                                ) @ 0x000f9190
[    0.000000] ACPI: RSDT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fee3040
[    0.000000] ACPI: FADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fee30c0
[    0.000000] ACPI: MCFG (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fee7480
[    0.000000] ACPI: MADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fee73c0
[    0.000000] ACPI: DSDT (v001 INTELR AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] Detected 2128.112 MHz processor.
[   20.436072] Built 1 zonelists.  Total pages: 519907
[   20.436076] Kernel command line: root=UUID=a10e812b-1a81-4094-beb3-01d7b9560216 ro quiet splash
[   20.436207] mapped APIC to ffffd000 (fee00000)
[   20.436209] mapped IOAPIC to ffffc000 (fec00000)
[   20.436213] Enabling fast FPU save and restore... done.
[   20.436215] Enabling unmasked SIMD FPU exception support... done.
[   20.436223] Initializing CPU#0
[   20.436282] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   20.438412] Console: colour VGA+ 80x25
[   20.438754] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   20.439120] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.525049] Memory: 2066900k/2096000k available (1992k kernel code, 27908k reserved, 893k data, 328k init, 1178496k highmem)
[   20.525058] virtual kernel memory layout:
[   20.525059]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   20.525060]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.525061]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   20.525062]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   20.525063]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   20.525064]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   20.525065]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   20.525068] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.604226] Calibrating delay using timer specific routine.. 4259.28 BogoMIPS (lpj=8518571)
[   20.604266] Security Framework v1.0.0 initialized
[   20.604277] SELinux:  Disabled at boot.
[   20.604292] Mount-cache hash table entries: 512
[   20.604442] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[   20.604454] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.604456] CPU: L2 cache: 2048K
[   20.604459] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
[   20.604469] Compat vDSO mapped to ffffe000.
[   20.604473] Remapping vsyscall page to ffffe000
[   20.604484] Checking 'hlt' instruction... OK.
[   20.620342] SMP alternatives: switching to UP code
[   20.620578] Freeing SMP alternatives: 11k freed
[   20.620749] Early unpacking initramfs... done
[   20.890396] ACPI: Core revision 20060707
[   20.896102] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   20.899187] CPU0: Intel(R) Pentium(R) M processor 2.13GHz stepping 08
[   20.899206] Total of 1 processors activated (4259.28 BogoMIPS).
[   20.899353] ENABLING IO-APIC IRQs
[   20.899525] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.044098] Brought up 1 CPUs
[   21.044292] Booting paravirtualized kernel on bare hardware
[   21.044349] Time:  7:14:20  Date: 04/07/107
[   21.044371] NET: Registered protocol family 16
[   21.044437] EISA bus registered
[   21.044441] ACPI: bus type pci registered
[   21.068883] PCI: PCI BIOS revision 3.00 entry at 0xfb3c0, last bus=4
[   21.068885] PCI: Using configuration type 1
[   21.068886] Setting up standard PCI resources
[   21.087023] ACPI: Interpreter enabled
[   21.087024] ACPI: Using IOAPIC for interrupt routing
[   21.087404] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.087411] PCI: Probing PCI hardware (bus 00)
[   21.087950] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   21.087954] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   21.088139] Boot video device is 0000:01:00.0
[   21.088552] PCI: Transparent bridge - 0000:00:1e.0
[   21.088595] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.098800] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   21.098971] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[   21.099335] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   21.102191] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   21.102392] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   21.102591] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   21.102791] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   21.102989] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   21.103189] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   21.103387] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   21.103589] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   21.103777] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.103783] pnp: PnP ACPI init
[   21.106662] pnp: PnP ACPI: found 14 devices
[   21.106666] PnPBIOS: Disabled by ACPI PNP
[   21.106702] PCI: Using ACPI for IRQ routing
[   21.106704] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.130604] NET: Registered protocol family 8
[   21.130605] NET: Registered protocol family 20
[   21.130918] pnp: 00:0a: ioport range 0x400-0x4bf could not be reserved
[   21.131113] PCI: Bridge: 0000:00:01.0
[   21.131114]   IO window: disabled.
[   21.131118]   MEM window: b0000000-cfffffff
[   21.131120]   PREFETCH window: 80000000-800fffff
[   21.131123] PCI: Bridge: 0000:00:1c.0
[   21.131126]   IO window: b000-bfff
[   21.131130]   MEM window: d0000000-d00fffff
[   21.131133]   PREFETCH window: 80100000-801fffff
[   21.131137] PCI: Bridge: 0000:00:1c.1
[   21.131139]   IO window: c000-cfff
[   21.131143]   MEM window: d0100000-d01fffff
[   21.131146]   PREFETCH window: 80200000-802fffff
[   21.131150] PCI: Bridge: 0000:00:1e.0
[   21.131152]   IO window: d000-dfff
[   21.131156]   MEM window: d0200000-d02fffff
[   21.131159]   PREFETCH window: disabled.
[   21.131171] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.131176] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   21.131189] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.131193] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.131207] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   21.131211] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.131219] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   21.131235] NET: Registered protocol family 2
[   21.168066] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.168154] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.168904] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.169416] TCP: Hash tables configured (established 131072 bind 65536)
[   21.169419] TCP reno registered
[   21.180141] checking if image is initramfs... it is
[   21.714063] Freeing initrd memory: 7010k freed
[   21.714451] audit: initializing netlink socket (disabled)
[   21.714464] audit(1178522060.356:1): initialized
[   21.714527] highmem bounce pool size: 64 pages
[   21.714581] VFS: Disk quotas dquot_6.5.1
[   21.714598] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.714645] io scheduler noop registered
[   21.714647] io scheduler anticipatory registered
[   21.714649] io scheduler deadline registered
[   21.714658] io scheduler cfq registered (default)
[   21.714888] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   21.714914] assign_interrupt_mode Found MSI capability
[   21.714917] Allocate Port Service[0000:00:01.0:pcie00]
[   21.714980] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.715012] assign_interrupt_mode Found MSI capability
[   21.715015] Allocate Port Service[0000:00:1c.0:pcie00]
[   21.715038] Allocate Port Service[0000:00:1c.0:pcie02]
[   21.715109] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.715141] assign_interrupt_mode Found MSI capability
[   21.715143] Allocate Port Service[0000:00:1c.1:pcie00]
[   21.715167] Allocate Port Service[0000:00:1c.1:pcie02]
[   21.715285] isapnp: Scanning for PnP cards...
[   22.068265] isapnp: No Plug & Play device found
[   22.087546] Real Time Clock Driver v1.12ac
[   22.087592] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.087731] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.087869] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   22.088335] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.088533] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   22.088707] mice: PS/2 mouse device common for all mice
[   22.089134] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.089322] input: Macintosh mouse button emulation as /class/input/input0
[   22.089352] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   22.089355] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   22.089543] PNP: No PS/2 controller found. Probing ports directly.
[   22.092049] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.092053] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.092153] EISA: Probing bus 0 at eisa.0
[   22.092179] EISA: Detected 0 cards.
[   22.122250] TCP cubic registered
[   22.122257] NET: Registered protocol family 1
[   22.122275] Using IPI No-Shortcut mode
[   22.122318] ACPI: (supports S0 S3 S4 S5)
[   22.122359]   Magic number: 7:426:217
[   22.122380]   hash matches device ttyu1
[   22.122616] Freeing unused kernel memory: 328k freed
[   22.123672] Time: tsc clocksource has been installed.
[   23.303662] Capability LSM initialized
[   23.326639] ACPI: Fan [FAN] (on)
[   23.329143] ACPI: Processor [CPU0] (supports 2 throttling states)
[   23.330119] ACPI: Thermal Zone [THRM] (40 C)
[   23.614563] usbcore: registered new interface driver usbfs
[   23.614581] usbcore: registered new interface driver hub
[   23.614597] usbcore: registered new device driver usb
[   23.615241] USB Universal Host Controller Interface driver v3.0
[   23.615287] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[   23.615297] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.615300] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.615441] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   23.615466] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000e300
[   23.615545] usb usb1: configuration #1 chosen from 1 choice
[   23.615562] hub 1-0:1.0: USB hub found
[   23.615566] hub 1-0:1.0: 2 ports detected
[   23.658857] SCSI subsystem initialized
[   23.662889] libata version 2.20 loaded.
[   23.702555] ieee1394: Initialized config rom entry `ip1394'
[   23.723163] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   23.723174] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.723177] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.723194] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   23.723223] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e000
[   23.723297] usb usb2: configuration #1 chosen from 1 choice
[   23.723324] hub 2-0:1.0: USB hub found
[   23.723329] hub 2-0:1.0: 2 ports detected
[   23.806123] FDC 0 is a post-1991 82077
[   23.831113] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   23.831124] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.831128] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.831145] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   23.831171] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e100
[   23.831246] usb usb3: configuration #1 chosen from 1 choice
[   23.831265] hub 3-0:1.0: USB hub found
[   23.831271] hub 3-0:1.0: 2 ports detected
[   23.939009] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   23.939016] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   23.939019] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   23.939033] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   23.939055] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e200
[   23.939121] usb usb4: configuration #1 chosen from 1 choice
[   23.939139] hub 4-0:1.0: USB hub found
[   23.939145] hub 4-0:1.0: 2 ports detected
[   24.048107] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[   24.048119] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   24.048122] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   24.048145] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   24.048172] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   24.048178] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xd0304000
[   24.052062] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.052983] usb usb5: configuration #1 chosen from 1 choice
[   24.053003] hub 5-0:1.0: USB hub found
[   24.053009] hub 5-0:1.0: 8 ports detected
[   24.160700] ata_piix 0000:00:1f.1: version 2.10ac1
[   24.160716] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 20
[   24.160733] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.160771] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   24.170575] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   24.170594] scsi0 : ata_piix
[   24.483086] ata1.00: ATAPI, max UDMA/33
[   24.643006] ata1.00: configured for UDMA/33
[   24.643011] scsi1 : ata_piix
[   24.790604] usb 4-2: new low speed USB device using uhci_hcd and address 2
[   24.813259] ATA: abnormal status 0x7F on port 0x00010177
[   24.813794] scsi 0:0:0:0: CD-ROM            LITE-ON  DVD SOHD-167T    9S1B PQ: 0 ANSI: 5
[   24.814377] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   24.814397] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   24.814412] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.814434] ata3: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e502 bmdma 0x0001e800 irq 19
[   24.814451] ata4: SATA max UDMA/133 cmd 0x0001e600 ctl 0x0001e702 bmdma 0x0001e808 irq 19
[   24.814457] scsi2 : ata_piix
[   24.963735] usb 4-2: configuration #1 chosen from 1 choice
[   24.981122] ATA: abnormal status 0x7F on port 0x0001e407
[   24.981152] scsi3 : ata_piix
[   24.985510] usbcore: registered new interface driver hiddev
[   25.002771] input: HID 0566:3002 as /class/input/input1
[   25.002782] input: USB HID v1.10 Keyboard [HID 0566:3002] on usb-0000:00:1d.3-2
[   25.038682] input: HID 0566:3002 as /class/input/input2
[   25.038709] input,hiddev96: USB HID v1.10 Device [HID 0566:3002] on usb-0000:00:1d.3-2
[   25.038717] usbcore: registered new interface driver usbhid
[   25.038719] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   25.192746] ata4.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   25.192752] ata4.00: ATA-7: ST3160815AS, 3.AAC, max UDMA/133
[   25.192754] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   25.259355] ata4.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   25.259359] ata4.00: configured for UDMA/133
[   25.259695] scsi 3:0:0:0: Direct-Access     ATA      ST3160815AS      3.AA PQ: 0 ANSI: 5
[   25.260779] ACPI: PCI Interrupt 0000:04:09.0[A] -> GSI 21 (level, low) -> IRQ 21
[   25.314220] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[d0200000-d02007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   25.326671] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   25.326674] Uniform CD-ROM driver Revision: 3.20
[   25.326708] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   25.329807] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   25.329825] scsi 3:0:0:0: Attached scsi generic sg1 type 0
[   25.334212] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   25.334222] sda: Write Protect is off
[   25.334223] sda: Mode Sense: 00 3a 00 00
[   25.334233] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.334270] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   25.334276] sda: Write Protect is off
[   25.334277] sda: Mode Sense: 00 3a 00 00
[   25.334287] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.334290]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[   25.426966] sd 3:0:0:0: Attached scsi disk sda
[   25.703098] Attempting manual resume
[   25.703102] swsusp: Resume From Partition 8:7
[   25.703103] PM: Checking swsusp image.
[   25.703225] PM: Resume from disk failed.
[   25.732171] kjournald starting.  Commit interval 5 seconds
[   25.732178] EXT3-fs: mounted filesystem with ordered data mode.
[   26.598011] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc5600d4c7e7]
[   33.921172] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.923034] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.937514] iTCO_vendor_support: vendor-support=0
[   33.939283] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   33.939355] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0460)
[   33.939390] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   33.950697] intel_rng: FWH not detected
[   33.992390] Linux agpgart interface v0.102 (c) Dave Jones
[   33.995215] agpgart: Detected an Intel 915GM Chipset.
[   34.011807] agpgart: AGP aperture is 256M @ 0x0
[   34.679619] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.679631] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   34.679654] sky2 0000:02:00.0: v1.13 addr 0xd0020000 irq 16 Yukon-EC (0xb6) rev 1
[   34.679750] sky2 eth0: addr 00:13:d3:bc:8e:e8
[   34.679768] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   34.679774] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   34.679795] sky2 0000:03:00.0: v1.13 addr 0xd0120000 irq 17 Yukon-EC (0xb6) rev 1
[   34.679876] sky2 eth1: addr 00:13:d3:bc:8e:e9
[   34.840608] input: PC Speaker as /class/input/input3
[   34.844915] sky2 eth0: enabling interface
[   34.846731] sky2 eth0: ram buffer 48K
[   34.860772] sky2 eth1: enabling interface
[   34.862587] sky2 eth1: ram buffer 48K
[   34.868314] usbcore: registered new interface driver xpad
[   34.868317] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   34.971507] parport: PnPBIOS parport detected.
[   34.971556] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   35.085753] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.085769] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   35.274500] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   35.343294] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4
[   35.390662] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   35.390684] Model 1001 Rev 00000000 Serial 10011102
[   35.544302] fuse init (API version 7.8)
[   35.560999] lp0: using parport0 (interrupt-driven).
[   35.588197] Adding 1389580k swap on /dev/disk/by-uuid/a990cc55-0c97-4b82-a135-1601ccfa8d67.  Priority:-1 extents:1 across:1389580k
[   35.795500] EXT3 FS on sda6, internal journal
[   36.091075] NET: Registered protocol family 17
[   37.550289] sky2 eth0: Link is up at 1000 Mbps, full duplex, flow control both
[   39.633047] NET: Registered protocol family 10
[   39.633126] lo: Disabled Privacy Extensions
[   39.633201] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   39.840753] ibm_acpi: ec object not found
[   39.898469] input: Power Button (FF) as /class/input/input5
[   39.901028] ACPI: Power Button (FF) [PWRF]
[   39.927624] input: Power Button (CM) as /class/input/input6
[   39.930141] ACPI: Power Button (CM) [PWRB]
[   39.978368] No dock devices found.
[   39.985754] Using specific hotkey driver
[   40.059632] pcc_acpi: loading...
[   44.591538] ppdev: user-space parallel port driver
[   47.735187] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   47.735191] apm: overridden by ACPI.
[   26.984000] Time: acpi_pm clocksource has been installed.
[   27.020000] Bluetooth: Core ver 2.11
[   27.020000] NET: Registered protocol family 31
[   27.020000] Bluetooth: HCI device and connection manager initialized
[   27.020000] Bluetooth: HCI socket layer initialized
[   27.048000] Bluetooth: L2CAP ver 2.8
[   27.048000] Bluetooth: L2CAP socket layer initialized
[   27.152000] Bluetooth: RFCOMM socket layer initialized
[   27.152000] Bluetooth: RFCOMM TTY layer initialized
[   27.152000] Bluetooth: RFCOMM ver 1.8
[   38.504000] eth0: no IPv6 routers present

--frustrated new user

---

### Post by Todd Bealmear on 2007-05-07
My sound occasionally doesn't work after I resume from hibernation - it normally works fine after I reboot.  I'm assuming you've tried to reboot?

If you also experienced the problem under FC6, I'd imagine this is probably a hardware issue.

---

### Post by kettle on 2007-05-07
I think it probably is a hardware issue, but if it works the first time I boot the computer after installing the distro, shouldn't there be a way to reset everything to the factory settings and get it working again?

Is there anywhere else I could go for more help?

---

### Post by Tommy James on 2007-05-07
My sound worked until an update was applied.  My sound works again if you move the master volume slide.  Can't find another fix and I've posted the problem in the forum with no luck.  You might try it...

---

### Post by Irish J on 2007-05-07
very interested to get a reply to this if anyone can? :D

---

### Post by Esben Kramer on 2007-05-08
I get no sound if I boot up with a cable in the line-in. If I plug it in after the boot, everything works.

---

### Post by sn00pster on 2007-05-21
This seems to be a common problem with the new kernel. I have sound when i boot into Kernel 2.6.20-12. But when i load kernel 2.6.20-15 i get so sound. I can tell at book because my Laptop has Optical out and the Optical light come on with the old kernel, No light with the new kernel.

My fix is using the older kernel which it what came with the Beta Release.

I'm a Noob to linux. I just hope someone out there knows how to fix this.

Cheers
Jimbob

---

### Post by loopyloopy on 2007-12-02
Hi,

i've been a long time user of Dapper and had no issues with sound on this machine.

recently i upgraded to Feisty and have started having this problem.

i am using an SBLive! Value soundcard for my stereo speakers.

I have noticed that i can restore sound if i reboot using a different kernel, but then if i reboot using that same kernel i lose sound again.

eg i would boot with 2.6.20-16-386, i would get no sound.
if i reboot with the same kernel, no sound.

if i reboot with 2.6.20-16-generic i would get sound.
if i then reboot with 2.6.20-16-generic i would lose sound, 
so i would then reboot with 2.6.20-16-386 and sound would be restored.

it seems something is getting toggled depending on how a reboot was done.  no amount of fiddling with the Alsa mixer has made any difference.

I would appreciate any help here.

 cat /proc/asound/cards
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with AD1888 at 0x1000, irq 19
 1 [Live           ]: EMU10K1 - SBLive! Value [CT4780]
                      SBLive! Value [CT4780] (rev.6, serial:0x80221102) at 0xd400, irq 20


..another thing i've noticed.  whenever i do a system update, i also lose all sound

---

