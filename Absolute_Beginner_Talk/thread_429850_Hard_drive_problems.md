---
title: "Hard drive problems"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by misfito on 2007-05-01
How do i fix the errors in my HHDD i got a some freezes and crashes....i want to fix'em.



please HELP!!!:confused: :confused: 












hard drive problems

---

### Post by starcraft.man on 2007-05-01
Thats.... REALLY Vague. Can you be a bit more specific? I mean there are so many problems that can happen on a hard drive. Do you mean actual physical errors that weren't corrected by your ECC on your drive? If thats the case, I dunno >.>.

---

### Post by kittyhawk63 on 2007-05-01
> **misfito said:**
> How do i fix the errors in my HHDD i got a some freezes and crashes....i want to fix'em.
Please HELP!!!
hard drive problems

When do you experience the freezes and crashes? 
What video card do you have? 
What Linux program are you using?

---

### Post by KCormier on 2007-05-01
What makes you say they're hard drive errors?  If you get error messages, what are they (please be as exact as possible!! :))

---

### Post by misfito on 2007-05-01
Hey I got a Maxtor 6L200S0    
This is the log when i got the errors (crashes and freezes)
I splited it because this thing didnt let me put the whole thing in 1 piece
I think I got Hard drive errors because when the system restared I end up with the SCRUB screen and the system trying to load again but I got some weird messages saying that It (dont remember exactly what it said) has some errors and I have to fix'em manually using a command (that I dont remember the name anymore ) Because it didnt work automatically. I dont wanna go thru that again but if it happens I'll take a picture of everything in screen.


> 
---
May  1 09:18:46 My-linux kernel: [17217975.092000] atkbd.c: Unknown key released (translated set 2, code 0x7f on isa0060/serio0).
May  1 09:18:46 My-linux kernel: [17217975.092000] atkbd.c: Use 'setkeycodes 7f <keycode>' to make it known.
May  1 09:35:42 My-linux -- MARK --
May  1 09:55:43 My-linux -- MARK --
May  1 10:15:43 My-linux -- MARK --
May  1 10:21:03 My-linux gconfd (hugo-4927): Exiting
May  1 10:21:03 My-linux gconfd (hugo-22681): starting (version 2.14.0), pid 22681 user 'hugo'
May  1 10:21:04 My-linux gconfd (hugo-22681): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  1 10:21:04 My-linux gconfd (hugo-22681): Resolved address "xml:readwrite:/home/hugo/.gconf" to a writable configuration source at position 1
May  1 10:21:04 My-linux gconfd (hugo-22681): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  1 10:21:04 My-linux gconfd (hugo-22681): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May  1 10:21:04 My-linux gconfd (hugo-22681): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May  1 10:21:07 My-linux shutdown[4512]: shutting down for system reboot
May  1 10:21:10 My-linux kernel: [17221718.596000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May  1 10:21:10 My-linux kernel: [17221718.596000] apm: disabled on user request.
May  1 10:21:18 My-linux exiting on signal 15
May  1 10:22:53 My-linux syslogd 1.4.1#17ubuntu7: restart.
May  1 10:22:53 My-linux kernel: Inspecting /boot/System.map-2.6.15-28-386
May  1 10:22:53 My-linux kernel: Loaded 23072 symbols from /boot/System.map-2.6.15-28-386.
May  1 10:22:53 My-linux kernel: Symbols match kernel version 2.6.15.
May  1 10:22:53 My-linux kernel: No module symbols loaded - kernel modules not enabled. 
May  1 10:22:53 My-linux kernel: [17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007
May  1 10:22:53 My-linux kernel: [17179569.184000] BIOS-provided physical RAM map:
May  1 10:22:53 My-linux kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
May  1 10:22:53 My-linux kernel: [17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
May  1 10:22:53 My-linux kernel: [17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  1 10:22:53 My-linux kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
May  1 10:22:53 My-linux kernel: [17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
May  1 10:22:53 My-linux kernel: [17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
May  1 10:22:53 My-linux kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
May  1 10:22:53 My-linux kernel: [17179569.184000] 0MB HIGHMEM available.
May  1 10:22:53 My-linux kernel: [17179569.184000] 511MB LOWMEM available.
May  1 10:22:53 My-linux kernel: [17179569.184000] found SMP MP-table at 000f5e10
May  1 10:22:53 My-linux kernel: [17179569.184000] DMI 2.2 present.
May  1 10:22:53 My-linux kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x408
May  1 10:22:53 My-linux kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  1 10:22:53 My-linux kernel: [17179569.184000] Processor #0 15:2 APIC version 20
May  1 10:22:53 My-linux kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
May  1 10:22:53 My-linux kernel: [17179569.184000] Processor #1 15:2 APIC version 20
May  1 10:22:53 My-linux kernel: [17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
May  1 10:22:53 My-linux kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
May  1 10:22:53 My-linux kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
May  1 10:22:53 My-linux kernel: [17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  1 10:22:53 My-linux kernel: [17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
May  1 10:22:53 My-linux kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  1 10:22:53 My-linux kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  1 10:22:53 My-linux kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  1 10:22:53 My-linux kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
May  1 10:22:53 My-linux kernel: [17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
May  1 10:22:53 My-linux kernel: [17179569.184000] Built 1 zonelists
May  1 10:22:53 My-linux kernel: [17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
May  1 10:22:53 My-linux kernel: [17179569.184000] Initializing CPU#0
May  1 10:22:53 My-linux kernel: [17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
May  1 10:22:53 My-linux kernel: [17179569.184000] Detected 2793.530 MHz processor.
May  1 10:22:53 My-linux kernel: [17179569.184000] Using pmtmr for high-res timesource
May  1 10:22:53 My-linux kernel: [17179569.184000] Console: colour VGA+ 80x25
May  1 10:22:53 My-linux kernel: [17179569.736000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  1 10:22:53 My-linux kernel: [17179569.736000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  1 10:22:53 My-linux kernel: [17179569.744000] Memory: 508852k/524224k available (1977k kernel code, 14804k reserved, 605k data, 288k init, 0k highmem)
May  1 10:22:53 My-linux kernel: [17179569.744000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May  1 10:22:53 My-linux kernel: [17179569.824000] Calibrating delay using timer specific routine.. 5591.19 BogoMIPS (lpj=11182398)
May  1 10:22:53 My-linux kernel: [17179569.824000] Security Framework v1.0.0 initialized
May  1 10:22:53 My-linux kernel: [17179569.824000] SELinux:  Disabled at boot.
May  1 10:22:53 My-linux kernel: [17179569.824000] Mount-cache hash table entries: 512
May  1 10:22:53 My-linux kernel: [17179569.824000] CPU: Trace cache: 12K uops, L1 D cache: 8K
May  1 10:22:53 My-linux kernel: [17179569.824000] CPU: L2 cache: 512K
May  1 10:22:53 My-linux kernel: [17179569.824000] mtrr: v2.0 (20020519)
May  1 10:22:53 My-linux kernel: [17179569.824000] CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 05
May  1 10:22:53 My-linux kernel: [17179569.824000] Enabling fast FPU save and restore... done.
May  1 10:22:53 My-linux kernel: [17179569.824000] Enabling unmasked SIMD FPU exception support... done.
May  1 10:22:53 My-linux kernel: [17179569.824000] Checking 'hlt' instruction... OK.
May  1 10:22:53 My-linux kernel: [17179569.840000] checking if image is initramfs... it is
May  1 10:22:53 My-linux kernel: [17179570.320000] Freeing initrd memory: 6617k freed
May  1 10:22:53 My-linux kernel: [17179570.328000] ACPI: Looking for DSDT ... not found!
May  1 10:22:53 My-linux kernel: [17179570.332000] ENABLING IO-APIC IRQs
May  1 10:22:53 My-linux kernel: [17179570.332000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
May  1 10:22:53 My-linux kernel: [17179570.472000] NET: Registered protocol family 16
May  1 10:22:53 My-linux kernel: [17179570.472000] EISA bus registered
May  1 10:22:53 My-linux kernel: [17179570.472000] ACPI: bus type pci registered
May  1 10:22:53 My-linux kernel: [17179570.472000] PCI: PCI BIOS revision 2.10 entry at 0xfba10, last bus=3
May  1 10:22:53 My-linux kernel: [17179570.472000] PCI: Using configuration type 1
May  1 10:22:53 My-linux kernel: [17179570.472000] ACPI: Subsystem revision 20051216
May  1 10:22:53 My-linux kernel: [17179570.476000] ACPI: Interpreter enabled
May  1 10:22:53 My-linux kernel: [17179570.476000] ACPI: Using IOAPIC for interrupt routing
May  1 10:22:53 My-linux kernel: [17179570.476000] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  1 10:22:53 My-linux kernel: [17179570.480000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
May  1 10:22:53 My-linux kernel: [17179570.480000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
May  1 10:22:53 My-linux kernel: [17179570.480000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
May  1 10:22:53 My-linux kernel: [17179570.480000] PCI: Transparent bridge - 0000:00:1e.0
May  1 10:22:53 My-linux kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May  1 10:22:53 My-linux kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May  1 10:22:53 My-linux kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May  1 10:22:53 My-linux kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
May  1 10:22:53 My-linux kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
May  1 10:22:53 My-linux kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May  1 10:22:53 My-linux kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May  1 10:22:53 My-linux kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May  1 10:22:53 My-linux kernel: [17179570.492000] Linux Plug and Play Support v0.97 (c) Adam Belay
May  1 10:22:53 My-linux kernel: [17179570.492000] pnp: PnP ACPI init
May  1 10:22:53 My-linux kernel: [17179570.496000] pnp: PnP ACPI: found 14 devices
May  1 10:22:53 My-linux kernel: [17179570.496000] PnPBIOS: Disabled by ACPI PNP
May  1 10:22:53 My-linux kernel: [17179570.496000] PCI: Using ACPI for IRQ routing
May  1 10:22:53 My-linux kernel: [17179570.496000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May  1 10:22:53 My-linux kernel: [17179570.524000] pnp: 00:0b: ioport range 0x400-0x4bf could not be reserved
May  1 10:22:53 My-linux kernel: [17179570.524000] PCI: Bridge: 0000:00:01.0
May  1 10:22:53 My-linux kernel: [17179570.524000]   IO window: a000-afff
May  1 10:22:53 My-linux kernel: [17179570.524000]   MEM window: f4000000-f5ffffff
May  1 10:22:53 My-linux kernel: [17179570.524000]   PREFETCH window: d0000000-efffffff
May  1 10:22:53 My-linux kernel: [17179570.524000] PCI: Bridge: 0000:00:03.0
May  1 10:22:53 My-linux kernel: [17179570.524000]   IO window: 9000-9fff
May  1 10:22:53 My-linux kernel: [17179570.524000]   MEM window: f8000000-f80fffff
May  1 10:22:53 My-linux kernel: [17179570.524000]   PREFETCH window: disabled.
May  1 10:22:53 My-linux kernel: [17179570.524000] PCI: Bridge: 0000:00:1e.0
May  1 10:22:53 My-linux kernel: [17179570.524000]   IO window: 6000-8fff
May  1 10:22:53 My-linux kernel: [17179570.524000]   MEM window: f6000000-f7ffffff
May  1 10:22:53 My-linux kernel: [17179570.524000]   PREFETCH window: 30000000-300fffff
May  1 10:22:53 My-linux kernel: [17179570.524000] audit: initializing netlink socket (disabled)
May  1 10:22:53 My-linux kernel: [17179570.524000] audit(1178040139.524:1): initialized
May  1 10:22:53 My-linux kernel: [17179570.524000] VFS: Disk quotas dquot_6.5.1
May  1 10:22:53 My-linux kernel: [17179570.524000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  1 10:22:53 My-linux kernel: [17179570.524000] Initializing Cryptographic API
May  1 10:22:53 My-linux kernel: [17179570.524000] io scheduler noop registered
May  1 10:22:53 My-linux kernel: [17179570.524000] io scheduler anticipatory registered
May  1 10:22:53 My-linux kernel: [17179570.524000] io scheduler deadline registered
May  1 10:22:53 My-linux kernel: [17179570.524000] io scheduler cfq registered
May  1 10:22:53 My-linux kernel: [17179570.524000] isapnp: Scanning for PnP cards...
May  1 10:22:53 My-linux kernel: [17179570.876000] isapnp: No Plug & Play device found
May  1 10:22:53 My-linux kernel: [17179570.892000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
May  1 10:22:53 My-linux kernel: [17179570.900000] serio: i8042 AUX port at 0x60,0x64 irq 12
May  1 10:22:53 My-linux kernel: [17179570.900000] serio: i8042 KBD port at 0x60,0x64 irq 1
May  1 10:22:53 My-linux kernel: [17179570.900000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
May  1 10:22:53 My-linux kernel: [17179570.900000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  1 10:22:53 My-linux kernel: [17179570.900000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  1 10:22:53 My-linux kernel: [17179570.904000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  1 10:22:53 My-linux kernel: [17179570.904000] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  1 10:22:53 My-linux kernel: [17179570.904000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May  1 10:22:53 My-linux kernel: [17179570.904000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
May  1 10:22:53 My-linux kernel: [17179570.904000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
May  1 10:22:53 My-linux kernel: [17179570.904000] mice: PS/2 mouse device common for all mice
May  1 10:22:53 My-linux kernel: [17179570.904000] EISA: Probing bus 0 at eisa.0
May  1 10:22:53 My-linux kernel: [17179570.904000] Cannot allocate resource for EISA slot 6
May  1 10:22:53 My-linux kernel: [17179570.904000] Cannot allocate resource for EISA slot 7
May  1 10:22:53 My-linux kernel: [17179570.904000] Cannot allocate resource for EISA slot 8
May  1 10:22:53 My-linux kernel: [17179570.904000] EISA: Detected 0 cards.
May  1 10:22:53 My-linux kernel: [17179570.904000] NET: Registered protocol family 2
May  1 10:22:53 My-linux kernel: [17179570.940000] input: AT Translated Set 2 keyboard as /class/input/input0
May  1 10:22:53 My-linux kernel: [17179570.952000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
May  1 10:22:53 My-linux kernel: [17179570.952000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
May  1 10:22:53 My-linux kernel: [17179570.952000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
May  1 10:22:53 My-linux kernel: [17179570.952000] TCP: Hash tables configured (established 32768 bind 32768)
May  1 10:22:53 My-linux kernel: [17179570.952000] TCP reno registered
May  1 10:22:53 My-linux kernel: [17179570.952000] TCP bic registered
May  1 10:22:53 My-linux kernel: [17179570.952000] NET: Registered protocol family 1
May  1 10:22:53 My-linux kernel: [17179570.952000] NET: Registered protocol family 8
May  1 10:22:53 My-linux kernel: [17179570.952000] NET: Registered protocol family 20
May  1 10:22:53 My-linux kernel: [17179570.952000] Using IPI Shortcut mode
May  1 10:22:53 My-linux kernel: [17179570.952000] ACPI wakeup devices: 
May  1 10:22:53 My-linux kernel: [17179570.952000] PCI0 CSAD HUB0 UAR1 UAR2 USB0 USB1 USB2 USB3 USBE MODM 
May  1 10:22:53 My-linux kernel: [17179570.952000] ACPI: (supports S0 S1 S4 S5)
May  1 10:22:53 My-linux kernel: [17179570.952000] Freeing unused kernel memory: 288k freed
May  1 10:22:53 My-linux kernel: [17179570.992000] vga16fb: mapped to 0xc00a0000
May  1 10:22:53 My-linux kernel: [17179571.052000] Console: switching to colour frame buffer device 80x25
May  1 10:22:53 My-linux kernel: [17179571.052000] fb0: VGA16 VGA frame buffer device
May  1 10:22:53 My-linux kernel: [17179572.068000] Capability LSM initialized
May  1 10:22:53 My-linux kernel: [17179572.192000] ACPI: Fan [FAN] (on)
May  1 10:22:53 My-linux kernel: [17179572.196000] ACPI: Thermal Zone [THRM] (40 C)
May  1 10:22:53 My-linux kernel: [17179572.684000] SCSI subsystem initialized
May  1 10:22:53 My-linux kernel: [17179572.684000] ACPI: bus type scsi registered
May  1 10:22:53 My-linux kernel: [17179572.684000] ACPI: PCI Interrupt 0000:03:05.0[A] -> GSI 20 (level, low) -> IRQ 169
May  1 10:22:53 My-linux kernel: [17179572.684000] ata1: SATA max UDMA/100 cmd 0xE0860080 ctl 0xE086008A bmdma 0xE0860000 irq 169
May  1 10:22:53 My-linux kernel: [17179572.684000] ata2: SATA max UDMA/100 cmd 0xE08600C0 ctl 0xE08600CA bmdma 0xE0860008 irq 169
May  1 10:22:53 My-linux kernel: [17179572.888000] ata1: no device found (phy stat 00000000)
May  1 10:22:53 My-linux kernel: [17179572.888000] scsi0 : sata_sil
May  1 10:22:53 My-linux kernel: [17179573.092000] ata2: no device found (phy stat 00000000)
May  1 10:22:53 My-linux kernel: [17179573.092000] scsi1 : sata_sil
May  1 10:22:53 My-linux kernel: [17179573.128000] HPT372N: IDE controller at PCI slot 0000:03:06.0
May  1 10:22:53 My-linux kernel: [17179573.128000] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 21 (level, low) -> IRQ 177
May  1 10:22:53 My-linux kernel: [17179573.128000] HPT372N: chipset revision 6
May  1 10:22:53 My-linux kernel: [17179573.128000] HPT372N: 100%% native mode on irq 177
May  1 10:22:53 My-linux kernel: [17179573.128000] hpt: HPT372N detected, using 372N timing.
May  1 10:22:53 My-linux kernel: [17179573.128000] FREQ: 79 PLL: 35
May  1 10:22:53 My-linux kernel: [17179573.132000] HPT37X: using 50MHz internal PLL
May  1 10:22:53 My-linux kernel: [17179573.132000]     ide2: BM-DMA at 0x8400-0x8407, BIOS settings: hde:pio, hdf:pio
May  1 10:22:53 My-linux kernel: [17179573.132000] hpt: HPT372N detected, using 372N timing.
May  1 10:22:53 My-linux kernel: [17179573.132000] FREQ: 146 PLL: 66
May  1 10:22:53 My-linux kernel: [17179574.592000] hpt: no known IDE timings, disabling DMA.
May  1 10:22:53 My-linux kernel: [17179575.768000] ICH5: IDE controller at PCI slot 0000:00:1f.1
May  1 10:22:53 My-linux kernel: [17179575.768000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 185
May  1 10:22:53 My-linux kernel: [17179575.768000] ICH5: chipset revision 2
May  1 10:22:53 My-linux kernel: [17179575.768000] ICH5: not 100%% native mode: will probe irqs later
May  1 10:22:53 My-linux kernel: [17179575.768000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
May  1 10:22:53 My-linux kernel: [17179575.768000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
May  1 10:22:53 My-linux kernel: [17179576.504000] hda: Memorex 48MAX 244816AJ, ATAPI CD/DVD-ROM drive
May  1 10:22:53 My-linux kernel: [17179577.288000] hdb: Memorex DVD16+/-DL4RWnD2, ATAPI CD/DVD-ROM drive
May  1 10:22:53 My-linux kernel: [17179577.344000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
May  1 10:22:53 My-linux kernel: [17179577.920000] hda: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
May  1 10:22:53 My-linux kernel: [17179577.920000] Uniform CD-ROM driver Revision: 3.20
May  1 10:22:53 My-linux kernel: [17179577.988000] hdb: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
May  1 10:22:53 My-linux kernel: [17179578.056000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 185
May  1 10:22:53 My-linux kernel: [17179578.056000] ata3: PATA max UDMA/133 cmd 0xC000 ctl 0xC402 bmdma 0xD000 irq 185
May  1 10:22:53 My-linux kernel: [17179578.056000] ata4: PATA max UDMA/133 cmd 0xC800 ctl 0xCC02 bmdma 0xD008 irq 185
May  1 10:22:53 My-linux kernel: [17179578.220000] ata3: dev 0 ATA-7, max UDMA/133, 398297088 sectors: LBA48
May  1 10:22:53 My-linux kernel: [17179578.224000] ata3: dev 0 configured for UDMA/133
May  1 10:22:53 My-linux kernel: [17179578.228000] scsi2 : ata_piix
May  1 10:22:53 My-linux kernel: [17179579.448000] scsi3 : ata_piix
May  1 10:22:53 My-linux kernel: [17179579.448000]   Vendor: ATA       Model: Maxtor 6L200S0    Rev: BANC
May  1 10:22:53 My-linux kernel: [17179579.448000]   Type:   Direct-Access                      ANSI SCSI revision: 05
May  1 10:22:53 My-linux kernel: [17179579.456000] Driver 'sd' needs updating - please use bus_type methods
May  1 10:22:53 My-linux kernel: [17179579.456000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
May  1 10:22:53 My-linux kernel: [17179579.456000] SCSI device sda: drive cache: write back
May  1 10:22:53 My-linux kernel: [17179579.456000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
May  1 10:22:53 My-linux kernel: [17179579.456000] SCSI device sda: drive cache: write back
May  1 10:22:53 My-linux kernel: [17179579.456000]  sda: sda1 sda2 < sda5 >
May  1 10:22:53 My-linux kernel: [17179579.492000] sd 2:0:0:0: Attached scsi disk sda
May  1 10:22:53 My-linux kernel: [17179579.672000] usbcore: registered new driver usbfs
May  1 10:22:53 My-linux kernel: [17179579.672000] usbcore: registered new driver hub
May  1 10:22:53 My-linux kernel: [17179579.672000] USB Universal Host Controller Interface driver v2.3
May  1 10:22:53 My-linux kernel: [17179579.672000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 193
May  1 10:22:53 My-linux kernel: [17179579.672000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May  1 10:22:53 My-linux kernel: [17179579.672000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
May  1 10:22:53 My-linux kernel: [17179579.672000] uhci_hcd 0000:00:1d.0: irq 193, io base 0x0000bc00
May  1 10:22:53 My-linux kernel: [17179579.676000] hub 1-0:1.0: USB hub found
May  1 10:22:53 My-linux kernel: [17179579.676000] hub 1-0:1.0: 2 ports detected
May  1 10:22:53 My-linux kernel: [17179579.780000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 201
May  1 10:22:53 My-linux kernel: [17179579.780000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May  1 10:22:53 My-linux kernel: [17179579.780000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
May  1 10:22:53 My-linux kernel: [17179579.780000] uhci_hcd 0000:00:1d.1: irq 201, io base 0x0000b000
May  1 10:22:53 My-linux kernel: [17179579.780000] hub 2-0:1.0: USB hub found
May  1 10:22:53 My-linux kernel: [17179579.780000] hub 2-0:1.0: 2 ports detected
May  1 10:22:53 My-linux kernel: [17179579.884000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
May  1 10:22:53 My-linux kernel: [17179579.884000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May  1 10:22:53 My-linux kernel: [17179579.884000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
May  1 10:22:53 My-linux kernel: [17179579.884000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x0000b400
May  1 10:22:53 My-linux kernel: [17179579.884000] hub 3-0:1.0: USB hub found
May  1 10:22:53 My-linux kernel: [17179579.884000] hub 3-0:1.0: 2 ports detected
May  1 10:22:53 My-linux kernel: [17179579.988000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 193
May  1 10:22:53 My-linux kernel: [17179579.988000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
May  1 10:22:53 My-linux kernel: [17179579.988000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
May  1 10:22:53 My-linux kernel: [17179579.988000] uhci_hcd 0000:00:1d.3: irq 193, io base 0x0000b800
May  1 10:22:53 My-linux kernel: [17179579.988000] hub 4-0:1.0: USB hub found
May  1 10:22:53 My-linux kernel: [17179579.988000] hub 4-0:1.0: 2 ports detected
May  1 10:22:53 My-linux kernel: [17179580.092000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 209
May  1 10:22:53 My-linux kernel: [17179580.092000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May  1 10:22:53 My-linux kernel: [17179580.092000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
May  1 10:22:53 My-linux kernel: [17179580.092000] ehci_hcd 0000:00:1d.7: irq 209, io mem 0xf8100000
May  1 10:22:53 My-linux kernel: [17179580.096000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  1 10:22:53 My-linux kernel: [17179580.096000] hub 5-0:1.0: USB hub found
May  1 10:22:53 My-linux kernel: [17179580.096000] hub 5-0:1.0: 8 ports detected
May  1 10:22:53 My-linux kernel: [17179580.200000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
May  1 10:22:53 My-linux kernel: [17179580.200000] ACPI: PCI Interrupt 0000:03:0a.0[A] -> GSI 19 (level, low) -> IRQ 201
May  1 10:22:53 My-linux kernel: [17179580.200000] PCI: Via IRQ fixup for 0000:03:0a.0, from 10 to 9
May  1 10:22:53 My-linux kernel: [17179580.252000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[201]  MMIO=[f7001000-f70017ff]  Max Packet=[2048]
May  1 10:22:53 My-linux kernel: [17179582.028000] Attempting manual resume
May  1 10:22:53 My-linux kernel: [17179582.076000] EXT3-fs: mounted filesystem with ordered data mode.
May  1 10:22:53 My-linux kernel: [17179582.092000] kjournald starting.  Commit interval 5 seconds
May  1 10:22:53 My-linux kernel: [17179588.212000] sd 2:0:0:0: Attached scsi generic sg0 type 0
May  1 10:22:53 My-linux kernel: [17179589.580000] Linux agpgart interface v0.101 (c) Dave Jones
May  1 10:22:53 My-linux kernel: [17179589.680000] agpgart: Detected an Intel i875 Chipset.
May  1 10:22:53 My-linux kernel: [17179589.684000] agpgart: AGP aperture is 64M @ 0xf0000000
May  1 10:22:53 My-linux kernel: [17179589.688000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  1 10:22:53 My-linux kernel: [17179589.692000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  1 10:22:53 My-linux kernel: [17179590.016000] Real Time Clock Driver v1.12
May  1 10:22:53 My-linux kernel: [17179590.128000] input: PC Speaker as /class/input/input1
May  1 10:22:53 My-linux kernel: [17179590.148000] parport: PnPBIOS parport detected.
May  1 10:22:53 My-linux kernel: [17179590.148000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May  1 10:22:53 My-linux kernel: [17179590.152000] FDC 0 is a post-1991 82077
May  1 10:22:53 My-linux kernel: [17179590.744000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
May  1 10:22:53 My-linux kernel: [17179590.744000] Copyright (c) 1999-2005 Intel Corporation.
May  1 10:22:53 My-linux kernel: [17179590.744000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 185
May  1 10:22:53 My-linux kernel: [17179590.800000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
May  1 10:22:53 My-linux kernel: [17179590.856000] ts: Compaq touchscreen protocol output
May  1 10:22:53 My-linux kernel: [17179591.120000] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:50:2c:09:7d:72
May  1 10:22:53 My-linux kernel: [17179591.364000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
May  1 10:22:53 My-linux kernel: [17179591.364000] ACPI: PCI Interrupt 0000:03:07.0[A] -> GSI 22 (level, low) -> IRQ 217
May  1 10:22:53 My-linux kernel: [17179592.980000] lp0: using parport0 (interrupt-driven).
May  1 10:22:53 My-linux kernel: [17179593.012000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
May  1 10:22:53 My-linux kernel: [17179593.012000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
May  1 10:22:53 My-linux kernel: [17179593.012000] ieee1394: sbp2: Try serialize_io=0 for better performance
May  1 10:22:53 My-linux kernel: [17179593.068000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
May  1 10:22:53 My-linux kernel: [17179593.068000] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
May  1 10:22:53 My-linux kernel: [17179593.204000] EXT3 FS on sda1, internal journal
May  1 10:22:53 My-linux kernel: [17179593.284000] NET: Registered protocol family 17
May  1 10:22:53 My-linux kernel: [17179593.376000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
May  1 10:22:53 My-linux kernel: [17179593.376000] md: bitmap version 4.39
May  1 10:22:53 My-linux kernel: [17179593.884000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
May  1 10:22:53 My-linux kernel: [17179594.756000] NET: Registered protocol family 10
May  1 10:22:53 My-linux kernel: [17179594.756000] lo: Disabled Privacy Extensions
May  1 10:22:53 My-linux kernel: [17179594.756000] IPv6 over IPv4 tunneling driver
May  1 10:22:53 My-linux kernel: [17179598.188000] cdrom: hda: mrw address space DMA selected
May  1 10:22:53 My-linux kernel: [17179598.192000] cdrom: open failed.
May  1 10:22:53 My-linux kernel: [17179604.116000] ACPI: Power Button (FF) [PWRF]
May  1 10:22:53 My-linux kernel: [17179604.116000] ACPI: Power Button (CM) [PWRB]
May  1 10:22:53 My-linux kernel: [17179604.244000] pcc_acpi: loading...
May  1 10:22:57 My-linux hpiod: 0.9.7 accepting connections at 39138... 
May  1 10:22:57 My-linux kernel: [17179609.372000] [drm] Initialized drm 1.0.1 20051102
May  1 10:22:57 My-linux kernel: [17179609.380000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 193
May  1 10:22:57 My-linux kernel: [17179609.380000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
May  1 10:22:58 My-linux kernel: [17179609.996000] ppdev: user-space parallel port driver
May  1 10:22:58 My-linux kernel: [17179610.304000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May  1 10:22:58 My-linux kernel: [17179610.304000] apm: overridden by ACPI.
May  1 10:22:58 My-linux kernel: [17179610.452000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
May  1 10:22:58 My-linux kernel: [17179610.452000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
May  1 10:22:58 My-linux kernel: [17179610.452000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
May  1 10:22:58 My-linux kernel: [17179610.588000] Bluetooth: Core ver 2.8
May  1 10:22:58 My-linux kernel: [17179610.588000] NET: Registered protocol family 31
May  1 10:22:58 My-linux kernel: [17179610.588000] Bluetooth: HCI device and connection manager initialized
May  1 10:22:58 My-linux kernel: [17179610.588000] Bluetooth: HCI socket layer initialized
May  1 10:22:58 My-linux kernel: [17179610.608000] Bluetooth: L2CAP ver 2.8
May  1 10:22:58 My-linux kernel: [17179610.608000] Bluetooth: L2CAP socket layer initialized
May  1 10:22:58 My-linux kernel: [17179610.628000] Bluetooth: RFCOMM socket layer initialized
May  1 10:22:58 My-linux kernel: [17179610.628000] Bluetooth: RFCOMM TTY layer initialized
May  1 10:22:58 My-linux kernel: [17179610.628000] Bluetooth: RFCOMM ver 1.7
May  1 10:23:15 My-linux kernel: [17179626.788000] [drm] Setting GART location based on new memory map
May  1 10:23:15 My-linux kernel: [17179626.788000] [drm] Loading R300 Microcode
May  1 10:23:15 My-linux kernel: [17179626.788000] [drm] writeback test succeeded in 1 usecs
May  1 10:23:59 My-linux gconfd (hugo-4929): starting (version 2.14.0), pid 4929 user 'hugo'
May  1 10:23:59 My-linux gconfd (hugo-4929): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  1 10:23:59 My-linux gconfd (hugo-4929): Resolved address "xml:readwrite:/home/hugo/.gconf" to a writable configuration source at position 1
May  1 10:23:59 My-linux gconfd (hugo-4929): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  1 10:23:59 My-linux gconfd (hugo-4929): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May  1 10:23:59 My-linux gconfd (hugo-4929): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May  1 10:24:01 My-linux gconfd (hugo-4929): Resolved address "xml:readwrite:/home/hugo/.gconf" to a writable configuration source at position 0
May  1 10:24:03 My-linux kernel: [17179675.628000] cdrom: hda: mrw address space DMA selected
May  1 10:24:04 My-linux kernel: [17179675.772000] UDF-fs: No VRS found
May  1 10:24:04 My-linux kernel: [17179675.932000] cdrom: hda: mrw address space DMA selected
May  1 10:24:04 My-linux kernel: [17179676.004000] UDF-fs: No VRS found
May  1 10:24:04 My-linux kernel: [17179676.216000] cdrom: hda: mrw address space DMA selected
May  1 10:24:20 My-linux gconfd (hugo-4929): Exiting
May  1 10:24:20 My-linux gconfd (hugo-5034): starting (version 2.14.0), pid 5034 user 'hugo'
May  1 10:24:20 My-linux gconfd (hugo-5034): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  1 10:24:20 My-linux gconfd (hugo-5034): Resolved address "xml:readwrite:/home/hugo/.gconf" to a writable configuration source at position 1
May  1 10:24:20 My-linux gconfd (hugo-5034): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  1 10:24:20 My-linux gconfd (hugo-5034): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May  1 10:24:20 My-linux gconfd (hugo-5034): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May  1 10:24:22 My-linux shutdown[4514]: shutting down for system reboot
May  1 10:24:24 My-linux kernel: [17179695.828000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May  1 10:24:24 My-linux kernel: [17179695.828000] apm: disabled on user request.
May  1 10:24:30 My-linux kernel: Kernel logging (proc) stopped.
May  1 10:24:30 My-linux kernel: Kernel log daemon terminating.
May  1 10:24:30 My-linux exiting on signal 15
May  1 10:26:03 My-linux syslogd 1.4.1#17ubuntu7: restart.
May  1 10:26:03 My-linux kernel: Inspecting /boot/System.map-2.6.15-28-386
May  1 10:26:04 My-linux kernel: Loaded 23072 symbols from /boot/System.map-2.6.15-28-386.
May  1 10:26:04 My-linux kernel: Symbols match kernel version 2.6.15.
May  1 10:26:04 My-linux kernel: No module symbols loaded - kernel modules not enabled. 
May  1 10:26:04 My-linux kernel: [17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007
May  1 10:26:04 My-linux kernel: [17179569.184000] BIOS-provided physical RAM map:
May  1 10:26:04 My-linux kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
May  1 10:26:04 My-linux kernel: [17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
May  1 10:26:04 My-linux kernel: [17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  1 10:26:04 My-linux kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
May  1 10:26:04 My-linux kernel: [17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
May  1 10:26:04 My-linux kernel: [17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
May  1 10:26:04 My-linux kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
May  1 10:26:04 My-linux kernel: [17179569.184000] 0MB HIGHMEM available.
May  1 10:26:04 My-linux kernel: [17179569.184000] 511MB LOWMEM available.
May  1 10:26:04 My-linux kernel: [17179569.184000] found SMP MP-table at 000f5e10
May  1 10:26:04 My-linux kernel: [17179569.184000] DMI 2.2 present.
May  1 10:26:04 My-linux kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x408
May  1 10:26:04 My-linux kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  1 10:26:04 My-linux kernel: [17179569.184000] Processor #0 15:2 APIC version 20
May  1 10:26:04 My-linux kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
May  1 10:26:04 My-linux kernel: [17179569.184000] Processor #1 15:2 APIC version 20
May  1 10:26:04 My-linux kernel: [17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
May  1 10:26:04 My-linux kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
May  1 10:26:04 My-linux kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
May  1 10:26:04 My-linux kernel: [17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  1 10:26:04 My-linux kernel: [17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
May  1 10:26:04 My-linux kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  1 10:26:04 My-linux kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  1 10:26:04 My-linux kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  1 10:26:04 My-linux kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
May  1 10:26:04 My-linux kernel: [17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
May  1 10:26:04 My-linux kernel: [17179569.184000] Built 1 zonelists
May  1 10:26:04 My-linux kernel: [17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
May  1 10:26:04 My-linux kernel: [17179569.184000] Initializing CPU#0
May  1 10:26:04 My-linux kernel: [17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)

---

### Post by misfito on 2007-05-01
Here is the other part of the log
I dunno if it was correct from me to put it all like i did :(

> 
May  1 10:26:04 My-linux kernel: [17179569.184000] Detected 2793.332 MHz processor.
May  1 10:26:04 My-linux kernel: [17179569.184000] Using pmtmr for high-res timesource
May  1 10:26:04 My-linux kernel: [17179569.184000] Console: colour VGA+ 80x25
May  1 10:26:04 My-linux kernel: [17179572.580000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  1 10:26:04 My-linux kernel: [17179572.584000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  1 10:26:04 My-linux kernel: [17179572.592000] Memory: 508852k/524224k available (1977k kernel code, 14804k reserved, 605k data, 288k init, 0k highmem)
May  1 10:26:04 My-linux kernel: [17179572.592000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May  1 10:26:04 My-linux kernel: [17179572.672000] Calibrating delay using timer specific routine.. 5591.18 BogoMIPS (lpj=11182372)
May  1 10:26:04 My-linux kernel: [17179572.672000] Security Framework v1.0.0 initialized
May  1 10:26:04 My-linux kernel: [17179572.672000] SELinux:  Disabled at boot.
May  1 10:26:04 My-linux kernel: [17179572.672000] Mount-cache hash table entries: 512
May  1 10:26:04 My-linux kernel: [17179572.672000] CPU: Trace cache: 12K uops, L1 D cache: 8K
May  1 10:26:04 My-linux kernel: [17179572.672000] CPU: L2 cache: 512K
May  1 10:26:04 My-linux kernel: [17179572.672000] mtrr: v2.0 (20020519)
May  1 10:26:04 My-linux kernel: [17179572.672000] CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 05
May  1 10:26:04 My-linux kernel: [17179572.672000] Enabling fast FPU save and restore... done.
May  1 10:26:04 My-linux kernel: [17179572.672000] Enabling unmasked SIMD FPU exception support... done.
May  1 10:26:04 My-linux kernel: [17179572.672000] Checking 'hlt' instruction... OK.
May  1 10:26:04 My-linux kernel: [17179572.688000] checking if image is initramfs... it is
May  1 10:26:04 My-linux kernel: [17179573.168000] Freeing initrd memory: 6617k freed
May  1 10:26:04 My-linux kernel: [17179573.176000] ACPI: Looking for DSDT ... not found!
May  1 10:26:04 My-linux kernel: [17179573.176000] ENABLING IO-APIC IRQs
May  1 10:26:04 My-linux kernel: [17179573.176000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
May  1 10:26:04 My-linux kernel: [17179573.320000] NET: Registered protocol family 16
May  1 10:26:04 My-linux kernel: [17179573.320000] EISA bus registered
May  1 10:26:04 My-linux kernel: [17179573.320000] ACPI: bus type pci registered
May  1 10:26:04 My-linux kernel: [17179573.320000] PCI: PCI BIOS revision 2.10 entry at 0xfba10, last bus=3
May  1 10:26:04 My-linux kernel: [17179573.320000] PCI: Using configuration type 1
May  1 10:26:04 My-linux kernel: [17179573.320000] ACPI: Subsystem revision 20051216
May  1 10:26:04 My-linux kernel: [17179573.324000] ACPI: Interpreter enabled
May  1 10:26:04 My-linux kernel: [17179573.324000] ACPI: Using IOAPIC for interrupt routing
May  1 10:26:04 My-linux kernel: [17179573.324000] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  1 10:26:04 My-linux kernel: [17179573.328000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
May  1 10:26:04 My-linux kernel: [17179573.328000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
May  1 10:26:04 My-linux kernel: [17179573.328000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
May  1 10:26:04 My-linux kernel: [17179573.328000] PCI: Transparent bridge - 0000:00:1e.0
May  1 10:26:04 My-linux kernel: [17179573.340000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May  1 10:26:04 My-linux kernel: [17179573.340000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May  1 10:26:04 My-linux kernel: [17179573.340000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May  1 10:26:04 My-linux kernel: [17179573.340000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
May  1 10:26:04 My-linux kernel: [17179573.340000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
May  1 10:26:04 My-linux kernel: [17179573.340000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May  1 10:26:04 My-linux kernel: [17179573.340000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May  1 10:26:04 My-linux kernel: [17179573.340000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May  1 10:26:04 My-linux kernel: [17179573.340000] Linux Plug and Play Support v0.97 (c) Adam Belay
May  1 10:26:04 My-linux kernel: [17179573.340000] pnp: PnP ACPI init
May  1 10:26:04 My-linux kernel: [17179573.344000] pnp: PnP ACPI: found 14 devices
May  1 10:26:04 My-linux kernel: [17179573.344000] PnPBIOS: Disabled by ACPI PNP
May  1 10:26:04 My-linux kernel: [17179573.344000] PCI: Using ACPI for IRQ routing
May  1 10:26:04 My-linux kernel: [17179573.344000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May  1 10:26:04 My-linux kernel: [17179573.372000] pnp: 00:0b: ioport range 0x400-0x4bf could not be reserved
May  1 10:26:04 My-linux kernel: [17179573.372000] PCI: Bridge: 0000:00:01.0
May  1 10:26:04 My-linux kernel: [17179573.372000]   IO window: a000-afff
May  1 10:26:04 My-linux kernel: [17179573.372000]   MEM window: f4000000-f5ffffff
May  1 10:26:04 My-linux kernel: [17179573.372000]   PREFETCH window: d0000000-efffffff
May  1 10:26:04 My-linux kernel: [17179573.372000] PCI: Bridge: 0000:00:03.0
May  1 10:26:04 My-linux kernel: [17179573.372000]   IO window: 9000-9fff
May  1 10:26:04 My-linux kernel: [17179573.372000]   MEM window: f8000000-f80fffff
May  1 10:26:04 My-linux kernel: [17179573.372000]   PREFETCH window: disabled.
May  1 10:26:04 My-linux kernel: [17179573.372000] PCI: Bridge: 0000:00:1e.0
May  1 10:26:04 My-linux kernel: [17179573.372000]   IO window: 6000-8fff
May  1 10:26:04 My-linux kernel: [17179573.372000]   MEM window: f6000000-f7ffffff
May  1 10:26:04 My-linux kernel: [17179573.372000]   PREFETCH window: 30000000-300fffff
May  1 10:26:04 My-linux kernel: [17179573.372000] audit: initializing netlink socket (disabled)
May  1 10:26:04 My-linux kernel: [17179573.372000] audit(1178040333.372:1): initialized
May  1 10:26:04 My-linux kernel: [17179573.372000] VFS: Disk quotas dquot_6.5.1
May  1 10:26:04 My-linux kernel: [17179573.372000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  1 10:26:04 My-linux kernel: [17179573.372000] Initializing Cryptographic API
May  1 10:26:04 My-linux kernel: [17179573.372000] io scheduler noop registered
May  1 10:26:04 My-linux kernel: [17179573.372000] io scheduler anticipatory registered
May  1 10:26:04 My-linux kernel: [17179573.372000] io scheduler deadline registered
May  1 10:26:04 My-linux kernel: [17179573.372000] io scheduler cfq registered
May  1 10:26:04 My-linux kernel: [17179573.372000] isapnp: Scanning for PnP cards...
May  1 10:26:04 My-linux kernel: [17179573.724000] isapnp: No Plug & Play device found
May  1 10:26:04 My-linux kernel: [17179573.740000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
May  1 10:26:04 My-linux kernel: [17179573.748000] serio: i8042 AUX port at 0x60,0x64 irq 12
May  1 10:26:04 My-linux kernel: [17179573.748000] serio: i8042 KBD port at 0x60,0x64 irq 1
May  1 10:26:04 My-linux kernel: [17179573.748000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
May  1 10:26:04 My-linux kernel: [17179573.748000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  1 10:26:04 My-linux kernel: [17179573.748000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  1 10:26:04 My-linux kernel: [17179573.752000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  1 10:26:04 My-linux kernel: [17179573.752000] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  1 10:26:04 My-linux kernel: [17179573.752000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May  1 10:26:04 My-linux kernel: [17179573.752000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
May  1 10:26:04 My-linux kernel: [17179573.752000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
May  1 10:26:04 My-linux kernel: [17179573.752000] mice: PS/2 mouse device common for all mice
May  1 10:26:04 My-linux kernel: [17179573.752000] EISA: Probing bus 0 at eisa.0
May  1 10:26:04 My-linux kernel: [17179573.752000] Cannot allocate resource for EISA slot 6
May  1 10:26:04 My-linux kernel: [17179573.752000] Cannot allocate resource for EISA slot 7
May  1 10:26:04 My-linux kernel: [17179573.752000] Cannot allocate resource for EISA slot 8
May  1 10:26:04 My-linux kernel: [17179573.752000] EISA: Detected 0 cards.
May  1 10:26:04 My-linux kernel: [17179573.752000] NET: Registered protocol family 2
May  1 10:26:04 My-linux kernel: [17179573.788000] input: AT Translated Set 2 keyboard as /class/input/input0
May  1 10:26:04 My-linux kernel: [17179573.800000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
May  1 10:26:04 My-linux kernel: [17179573.800000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
May  1 10:26:04 My-linux kernel: [17179573.800000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
May  1 10:26:04 My-linux kernel: [17179573.800000] TCP: Hash tables configured (established 32768 bind 32768)
May  1 10:26:04 My-linux kernel: [17179573.800000] TCP reno registered
May  1 10:26:04 My-linux kernel: [17179573.800000] TCP bic registered
May  1 10:26:04 My-linux kernel: [17179573.800000] NET: Registered protocol family 1
May  1 10:26:04 My-linux kernel: [17179573.800000] NET: Registered protocol family 8
May  1 10:26:04 My-linux kernel: [17179573.800000] NET: Registered protocol family 20
May  1 10:26:04 My-linux kernel: [17179573.800000] Using IPI Shortcut mode
May  1 10:26:04 My-linux kernel: [17179573.800000] ACPI wakeup devices: 
May  1 10:26:04 My-linux kernel: [17179573.800000] PCI0 CSAD HUB0 UAR1 UAR2 USB0 USB1 USB2 USB3 USBE MODM 
May  1 10:26:04 My-linux kernel: [17179573.800000] ACPI: (supports S0 S1 S4 S5)
May  1 10:26:04 My-linux kernel: [17179573.800000] Freeing unused kernel memory: 288k freed
May  1 10:26:04 My-linux kernel: [17179573.840000] vga16fb: mapped to 0xc00a0000
May  1 10:26:04 My-linux kernel: [17179573.948000] Console: switching to colour frame buffer device 80x25
May  1 10:26:04 My-linux kernel: [17179573.948000] fb0: VGA16 VGA frame buffer device
May  1 10:26:04 My-linux kernel: [17179575.016000] Capability LSM initialized
May  1 10:26:04 My-linux kernel: [17179575.140000] ACPI: Fan [FAN] (on)
May  1 10:26:04 My-linux kernel: [17179575.144000] ACPI: Thermal Zone [THRM] (40 C)
May  1 10:26:04 My-linux kernel: [17179575.612000] SCSI subsystem initialized
May  1 10:26:04 My-linux kernel: [17179575.616000] ACPI: bus type scsi registered
May  1 10:26:04 My-linux kernel: [17179575.616000] ACPI: PCI Interrupt 0000:03:05.0[A] -> GSI 20 (level, low) -> IRQ 169
May  1 10:26:04 My-linux kernel: [17179575.616000] ata1: SATA max UDMA/100 cmd 0xE0860080 ctl 0xE086008A bmdma 0xE0860000 irq 169
May  1 10:26:04 My-linux kernel: [17179575.616000] ata2: SATA max UDMA/100 cmd 0xE08600C0 ctl 0xE08600CA bmdma 0xE0860008 irq 169
May  1 10:26:04 My-linux kernel: [17179575.820000] ata1: no device found (phy stat 00000000)
May  1 10:26:04 My-linux kernel: [17179575.820000] scsi0 : sata_sil
May  1 10:26:04 My-linux kernel: [17179576.024000] ata2: no device found (phy stat 00000000)
May  1 10:26:04 My-linux kernel: [17179576.024000] scsi1 : sata_sil
May  1 10:26:04 My-linux kernel: [17179576.056000] HPT372N: IDE controller at PCI slot 0000:03:06.0
May  1 10:26:04 My-linux kernel: [17179576.056000] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 21 (level, low) -> IRQ 177
May  1 10:26:04 My-linux kernel: [17179576.056000] HPT372N: chipset revision 6
May  1 10:26:04 My-linux kernel: [17179576.056000] HPT372N: 100%% native mode on irq 177
May  1 10:26:04 My-linux kernel: [17179576.056000] hpt: HPT372N detected, using 372N timing.
May  1 10:26:04 My-linux kernel: [17179576.056000] FREQ: 79 PLL: 35
May  1 10:26:04 My-linux kernel: [17179576.060000] HPT37X: using 50MHz internal PLL
May  1 10:26:04 My-linux kernel: [17179576.060000]     ide2: BM-DMA at 0x8400-0x8407, BIOS settings: hde:pio, hdf:pio
May  1 10:26:04 My-linux kernel: [17179576.060000] hpt: HPT372N detected, using 372N timing.
May  1 10:26:04 My-linux kernel: [17179576.060000] FREQ: 145 PLL: 66
May  1 10:26:04 My-linux kernel: [17179577.512000] hpt: no known IDE timings, disabling DMA.
May  1 10:26:04 My-linux kernel: [17179578.680000] ICH5: IDE controller at PCI slot 0000:00:1f.1
May  1 10:26:04 My-linux kernel: [17179578.680000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 185
May  1 10:26:04 My-linux kernel: [17179578.680000] ICH5: chipset revision 2
May  1 10:26:04 My-linux kernel: [17179578.680000] ICH5: not 100%% native mode: will probe irqs later
May  1 10:26:04 My-linux kernel: [17179578.680000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
May  1 10:26:04 My-linux kernel: [17179578.680000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
May  1 10:26:04 My-linux kernel: [17179579.416000] hda: Memorex 48MAX 244816AJ, ATAPI CD/DVD-ROM drive
May  1 10:26:04 My-linux kernel: [17179580.200000] hdb: Memorex DVD16+/-DL4RWnD2, ATAPI CD/DVD-ROM drive
May  1 10:26:04 My-linux kernel: [17179580.256000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
May  1 10:26:04 My-linux kernel: [17179580.832000] hda: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
May  1 10:26:04 My-linux kernel: [17179580.832000] Uniform CD-ROM driver Revision: 3.20
May  1 10:26:04 My-linux kernel: [17179580.908000] hdb: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
May  1 10:26:04 My-linux kernel: [17179580.968000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 185
May  1 10:26:04 My-linux kernel: [17179580.968000] ata3: PATA max UDMA/133 cmd 0xC000 ctl 0xC402 bmdma 0xD000 irq 185
May  1 10:26:04 My-linux kernel: [17179580.968000] ata4: PATA max UDMA/133 cmd 0xC800 ctl 0xCC02 bmdma 0xD008 irq 185
May  1 10:26:04 My-linux kernel: [17179581.132000] ata3: dev 0 ATA-7, max UDMA/133, 398297088 sectors: LBA48
May  1 10:26:04 My-linux kernel: [17179581.136000] ata3: dev 0 configured for UDMA/133
May  1 10:26:04 My-linux kernel: [17179581.140000] scsi2 : ata_piix
May  1 10:26:04 My-linux kernel: [17179582.360000] scsi3 : ata_piix
May  1 10:26:04 My-linux kernel: [17179582.360000]   Vendor: ATA       Model: Maxtor 6L200S0    Rev: BANC
May  1 10:26:04 My-linux kernel: [17179582.360000]   Type:   Direct-Access                      ANSI SCSI revision: 05
May  1 10:26:04 My-linux kernel: [17179582.368000] Driver 'sd' needs updating - please use bus_type methods
May  1 10:26:04 My-linux kernel: [17179582.368000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
May  1 10:26:04 My-linux kernel: [17179582.368000] SCSI device sda: drive cache: write back
May  1 10:26:04 My-linux kernel: [17179582.368000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
May  1 10:26:04 My-linux kernel: [17179582.368000] SCSI device sda: drive cache: write back
May  1 10:26:04 My-linux kernel: [17179582.368000]  sda: sda1 sda2 < sda5 >
May  1 10:26:04 My-linux kernel: [17179582.404000] sd 2:0:0:0: Attached scsi disk sda
May  1 10:26:04 My-linux kernel: [17179582.612000] usbcore: registered new driver usbfs
May  1 10:26:04 My-linux kernel: [17179582.612000] usbcore: registered new driver hub
May  1 10:26:04 My-linux kernel: [17179582.616000] USB Universal Host Controller Interface driver v2.3
May  1 10:26:04 My-linux kernel: [17179582.616000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 193
May  1 10:26:04 My-linux kernel: [17179582.616000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May  1 10:26:04 My-linux kernel: [17179582.616000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
May  1 10:26:04 My-linux kernel: [17179582.616000] uhci_hcd 0000:00:1d.0: irq 193, io base 0x0000bc00
May  1 10:26:04 My-linux kernel: [17179582.616000] hub 1-0:1.0: USB hub found
May  1 10:26:04 My-linux kernel: [17179582.616000] hub 1-0:1.0: 2 ports detected
May  1 10:26:04 My-linux kernel: [17179582.720000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 201
May  1 10:26:04 My-linux kernel: [17179582.720000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May  1 10:26:04 My-linux kernel: [17179582.720000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
May  1 10:26:04 My-linux kernel: [17179582.720000] uhci_hcd 0000:00:1d.1: irq 201, io base 0x0000b000
May  1 10:26:04 My-linux kernel: [17179582.720000] hub 2-0:1.0: USB hub found
May  1 10:26:04 My-linux kernel: [17179582.720000] hub 2-0:1.0: 2 ports detected
May  1 10:26:04 My-linux kernel: [17179582.824000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
May  1 10:26:04 My-linux kernel: [17179582.824000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May  1 10:26:04 My-linux kernel: [17179582.824000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
May  1 10:26:04 My-linux kernel: [17179582.824000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x0000b400
May  1 10:26:04 My-linux kernel: [17179582.824000] hub 3-0:1.0: USB hub found
May  1 10:26:04 My-linux kernel: [17179582.824000] hub 3-0:1.0: 2 ports detected
May  1 10:26:04 My-linux kernel: [17179582.928000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 193
May  1 10:26:04 My-linux kernel: [17179582.928000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
May  1 10:26:04 My-linux kernel: [17179582.928000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
May  1 10:26:04 My-linux kernel: [17179582.928000] uhci_hcd 0000:00:1d.3: irq 193, io base 0x0000b800
May  1 10:26:04 My-linux kernel: [17179582.928000] hub 4-0:1.0: USB hub found
May  1 10:26:04 My-linux kernel: [17179582.928000] hub 4-0:1.0: 2 ports detected
May  1 10:26:04 My-linux kernel: [17179583.032000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 209
May  1 10:26:04 My-linux kernel: [17179583.032000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May  1 10:26:04 My-linux kernel: [17179583.032000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
May  1 10:26:04 My-linux kernel: [17179583.032000] ehci_hcd 0000:00:1d.7: irq 209, io mem 0xf8100000
May  1 10:26:04 My-linux kernel: [17179583.036000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
May  1 10:26:04 My-linux kernel: [17179583.036000] hub 5-0:1.0: USB hub found
May  1 10:26:04 My-linux kernel: [17179583.036000] hub 5-0:1.0: 8 ports detected
May  1 10:26:04 My-linux kernel: [17179583.140000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
May  1 10:26:04 My-linux kernel: [17179583.140000] ACPI: PCI Interrupt 0000:03:0a.0[A] -> GSI 19 (level, low) -> IRQ 201
May  1 10:26:04 My-linux kernel: [17179583.140000] PCI: Via IRQ fixup for 0000:03:0a.0, from 10 to 9
May  1 10:26:04 My-linux kernel: [17179583.192000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[201]  MMIO=[f7001000-f70017ff]  Max Packet=[2048]
May  1 10:26:04 My-linux kernel: [17179584.952000] Attempting manual resume
May  1 10:26:04 My-linux kernel: [17179584.960000] kjournald starting.  Commit interval 5 seconds
May  1 10:26:04 My-linux kernel: [17179584.960000] EXT3-fs: mounted filesystem with ordered data mode.
May  1 10:26:04 My-linux kernel: [17179590.876000] sd 2:0:0:0: Attached scsi generic sg0 type 0
May  1 10:26:04 My-linux kernel: [17179592.284000] Linux agpgart interface v0.101 (c) Dave Jones
May  1 10:26:04 My-linux kernel: [17179592.288000] agpgart: Detected an Intel i875 Chipset.
May  1 10:26:04 My-linux kernel: [17179592.292000] agpgart: AGP aperture is 64M @ 0xf0000000
May  1 10:26:04 My-linux kernel: [17179592.352000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  1 10:26:04 My-linux kernel: [17179592.356000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  1 10:26:04 My-linux kernel: [17179592.808000] Real Time Clock Driver v1.12
May  1 10:26:04 My-linux kernel: [17179592.940000] FDC 0 is a post-1991 82077
May  1 10:26:04 My-linux kernel: [17179593.020000] input: PC Speaker as /class/input/input1
May  1 10:26:04 My-linux kernel: [17179593.220000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
May  1 10:26:04 My-linux kernel: [17179593.220000] Copyright (c) 1999-2005 Intel Corporation.
May  1 10:26:04 My-linux kernel: [17179593.220000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 185
May  1 10:26:04 My-linux kernel: [17179593.504000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
May  1 10:26:04 My-linux kernel: [17179593.600000] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:50:2c:09:7d:72
May  1 10:26:04 My-linux kernel: [17179593.636000] ts: Compaq touchscreen protocol output
May  1 10:26:04 My-linux kernel: [17179593.844000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
May  1 10:26:04 My-linux kernel: [17179593.844000] ACPI: PCI Interrupt 0000:03:07.0[A] -> GSI 22 (level, low) -> IRQ 217
May  1 10:26:04 My-linux kernel: [17179594.172000] parport: PnPBIOS parport detected.
May  1 10:26:04 My-linux kernel: [17179594.172000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May  1 10:26:04 My-linux kernel: [17179594.852000] lp0: using parport0 (interrupt-driven).
May  1 10:26:04 My-linux kernel: [17179594.884000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
May  1 10:26:04 My-linux kernel: [17179594.884000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
May  1 10:26:04 My-linux kernel: [17179594.884000] ieee1394: sbp2: Try serialize_io=0 for better performance
May  1 10:26:04 My-linux kernel: [17179594.940000] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
May  1 10:26:04 My-linux kernel: [17179595.088000] EXT3 FS on sda1, internal journal
May  1 10:26:04 My-linux kernel: [17179595.240000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
May  1 10:26:04 My-linux kernel: [17179595.240000] md: bitmap version 4.39
May  1 10:26:04 My-linux kernel: [17179595.396000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
May  1 10:26:04 My-linux kernel: [17179595.972000] NET: Registered protocol family 17
May  1 10:26:04 My-linux kernel: [17179595.980000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
May  1 10:26:04 My-linux kernel: [17179600.008000] NET: Registered protocol family 10
May  1 10:26:04 My-linux kernel: [17179600.012000] lo: Disabled Privacy Extensions
May  1 10:26:04 My-linux kernel: [17179600.012000] IPv6 over IPv4 tunneling driver
May  1 10:26:04 My-linux kernel: [17179600.468000] cdrom: hda: mrw address space DMA selected
May  1 10:26:04 My-linux kernel: [17179600.476000] cdrom: open failed.
May  1 10:26:04 My-linux kernel: [17179606.348000] ACPI: Power Button (FF) [PWRF]
May  1 10:26:04 My-linux kernel: [17179606.348000] ACPI: Power Button (CM) [PWRB]
May  1 10:26:04 My-linux kernel: [17179606.464000] pcc_acpi: loading...
May  1 10:26:07 My-linux hpiod: 0.9.7 accepting connections at 42830... 
May  1 10:26:08 My-linux kernel: [17179612.128000] [drm] Initialized drm 1.0.1 20051102
May  1 10:26:08 My-linux kernel: [17179612.152000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 193
May  1 10:26:08 My-linux kernel: [17179612.152000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
May  1 10:26:09 My-linux kernel: [17179612.572000] ppdev: user-space parallel port driver
May  1 10:26:09 My-linux kernel: [17179612.772000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May  1 10:26:09 My-linux kernel: [17179612.772000] apm: overridden by ACPI.
May  1 10:26:09 My-linux kernel: [17179613.124000] Bluetooth: Core ver 2.8
May  1 10:26:09 My-linux kernel: [17179613.124000] NET: Registered protocol family 31
May  1 10:26:09 My-linux kernel: [17179613.124000] Bluetooth: HCI device and connection manager initialized
May  1 10:26:09 My-linux kernel: [17179613.124000] Bluetooth: HCI socket layer initialized
May  1 10:26:09 My-linux kernel: [17179613.144000] Bluetooth: L2CAP ver 2.8
May  1 10:26:09 My-linux kernel: [17179613.144000] Bluetooth: L2CAP socket layer initialized
May  1 10:26:09 My-linux kernel: [17179613.180000] Bluetooth: RFCOMM socket layer initialized
May  1 10:26:09 My-linux kernel: [17179613.180000] Bluetooth: RFCOMM TTY layer initialized
May  1 10:26:09 My-linux kernel: [17179613.180000] Bluetooth: RFCOMM ver 1.7
May  1 10:26:09 My-linux kernel: [17179613.224000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
May  1 10:26:09 My-linux kernel: [17179613.224000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
May  1 10:26:09 My-linux kernel: [17179613.224000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
May  1 10:26:26 My-linux kernel: [17179629.552000] [drm] Setting GART location based on new memory map
May  1 10:26:26 My-linux kernel: [17179629.552000] [drm] Loading R300 Microcode
May  1 10:26:26 My-linux kernel: [17179629.552000] [drm] writeback test succeeded in 1 usecs
May  1 10:34:43 My-linux gconfd (hugo-4919): starting (version 2.14.0), pid 4919 user 'hugo'
May  1 10:34:43 My-linux gconfd (hugo-4919): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  1 10:34:43 My-linux gconfd (hugo-4919): Resolved address "xml:readwrite:/home/hugo/.gconf" to a writable configuration source at position 1
May  1 10:34:43 My-linux gconfd (hugo-4919): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  1 10:34:43 My-linux gconfd (hugo-4919): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May  1 10:34:43 My-linux gconfd (hugo-4919): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May  1 10:34:46 My-linux gconfd (hugo-4919): Resolved address "xml:readwrite:/home/hugo/.gconf" to a writable configuration source at position 0
May  1 10:34:48 My-linux kernel: [17180132.356000] cdrom: hda: mrw address space DMA selected
May  1 10:34:49 My-linux kernel: [17180132.608000] UDF-fs: No VRS found
May  1 10:34:49 My-linux kernel: [17180132.780000] cdrom: hda: mrw address space DMA selected
May  1 10:34:49 My-linux kernel: [17180132.852000] UDF-fs: No VRS found
May  1 10:34:49 My-linux kernel: [17180133.404000] cdrom: hda: mrw address space DMA selected
May  1 10:46:03 My-linux -- MARK --
May  1 11:06:04 My-linux -- MARK --
May  1 11:26:04 My-linux -- MARK --
May  1 11:46:04 My-linux -- MARK --
May  1 12:06:05 My-linux -- MARK --
May  1 12:26:05 My-linux -- MARK --
May  1 13:00:21 My-linux syslogd 1.4.1#17ubuntu7: restart.
May  1 13:00:21 My-linux kernel: Inspecting /boot/System.map-2.6.15-28-386
May  1 13:00:21 My-linux kernel: Loaded 23072 symbols from /boot/System.map-2.6.15-28-386.
May  1 13:00:21 My-linux kernel: Symbols match kernel version 2.6.15.
May  1 13:00:21 My-linux kernel: No module symbols loaded - kernel modules not enabled. 
May  1 13:00:21 My-linux kernel: [17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007
May  1 13:00:21 My-linux kernel: [17179569.184000] BIOS-provided physical RAM map:
May  1 13:00:21 My-linux kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
May  1 13:00:21 My-linux kernel: [17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
May  1 13:00:21 My-linux kernel: [17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May  1 13:00:21 My-linux kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
May  1 13:00:21 My-linux kernel: [17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
May  1 13:00:21 My-linux kernel: [17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
May  1 13:00:21 My-linux kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
May  1 13:00:21 My-linux kernel: [17179569.184000] 0MB HIGHMEM available.
May  1 13:00:21 My-linux kernel: [17179569.184000] 511MB LOWMEM available.
May  1 13:00:21 My-linux kernel: [17179569.184000] found SMP MP-table at 000f5e10
May  1 13:00:21 My-linux kernel: [17179569.184000] DMI 2.2 present.
May  1 13:00:21 My-linux kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x408
May  1 13:00:21 My-linux kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  1 13:00:21 My-linux kernel: [17179569.184000] Processor #0 15:2 APIC version 20
May  1 13:00:21 My-linux kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
May  1 13:00:21 My-linux kernel: [17179569.184000] Processor #1 15:2 APIC version 20
May  1 13:00:21 My-linux kernel: [17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
May  1 13:00:21 My-linux kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
May  1 13:00:21 My-linux kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
May  1 13:00:21 My-linux kernel: [17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  1 13:00:21 My-linux kernel: [17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
May  1 13:00:21 My-linux kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  1 13:00:21 My-linux kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  1 13:00:21 My-linux kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  1 13:00:21 My-linux kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
May  1 13:00:21 My-linux kernel: [17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
May  1 13:00:21 My-linux kernel: [17179569.184000] Built 1 zonelists
May  1 13:00:21 My-linux kernel: [17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
May  1 13:00:21 My-linux kernel: [17179569.184000] Initializing CPU#0
May  1 13:00:21 My-linux kernel: [17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
May  1 13:00:21 My-linux kernel: [17179569.184000] Detected 2793.316 MHz processor.
May  1 13:00:21 My-linux kernel: [17179569.184000] Using pmtmr for high-res timesource
May  1 13:00:21 My-linux kernel: [17179569.184000] Console: colour VGA+ 80x25
May  1 13:00:21 My-linux kernel: [17179569.268000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  1 13:00:21 My-linux kernel: [17179569.268000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  1 13:00:21 My-linux kernel: [17179569.276000] Memory: 508852k/524224k available (1977k kernel code, 14804k reserved, 605k data, 288k init, 0k highmem)
May  1 13:00:21 My-linux kernel: [17179569.276000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May  1 13:00:21 My-linux kernel: [17179569.356000] Calibrating delay using timer specific routine.. 5591.20 BogoMIPS (lpj=11182401)
May  1 13:00:21 My-linux kernel: [17179569.356000] Security Framework v1.0.0 initialized
May  1 13:00:21 My-linux kernel: [17179569.356000] SELinux:  Disabled at boot.
May  1 13:00:21 My-linux kernel: [17179569.356000] Mount-cache hash table entries: 512
May  1 13:00:21 My-linux kernel: [17179569.356000] CPU: Trace cache: 12K uops, L1 D cache: 8K
May  1 13:00:21 My-linux kernel: [17179569.356000] CPU: L2 cache: 512K
May  1 13:00:21 My-linux kernel: [17179569.356000] mtrr: v2.0 (20020519)
May  1 13:00:21 My-linux kernel: [17179569.356000] CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 05
May  1 13:00:21 My-linux kernel: [17179569.356000] Enabling fast FPU save and restore... done.
May  1 13:00:21 My-linux kernel: [17179569.356000] Enabling unmasked SIMD FPU exception support... done.
May  1 13:00:21 My-linux kernel: [17179569.356000] Checking 'hlt' instruction... OK.
May  1 13:00:21 My-linux kernel: [17179569.372000] checking if image is initramfs... it is
May  1 13:00:21 My-linux kernel: [17179569.856000] Freeing initrd memory: 6617k freed
May  1 13:00:21 My-linux kernel: [17179569.860000] ACPI: Looking for DSDT ... not found!
May  1 13:00:21 My-linux kernel: [17179569.864000] ENABLING IO-APIC IRQs
May  1 13:00:21 My-linux kernel: [17179569.864000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
May  1 13:00:21 My-linux kernel: [17179570.008000] NET: Registered protocol family 16
May  1 13:00:21 My-linux kernel: [17179570.008000] EISA bus registered
May  1 13:00:21 My-linux kernel: [17179570.008000] ACPI: bus type pci registered
May  1 13:00:21 My-linux kernel: [17179570.008000] PCI: PCI BIOS revision 2.10 entry at 0xfba10, last bus=3
May  1 13:00:21 My-linux kernel: [17179570.008000] PCI: Using configuration type 1
May  1 13:00:21 My-linux kernel: [17179570.008000] ACPI: Subsystem revision 20051216
May  1 13:00:21 My-linux kernel: [17179570.012000] ACPI: Interpreter enabled
May  1 13:00:21 My-linux kernel: [17179570.012000] ACPI: Using IOAPIC for interrupt routing
May  1 13:00:21 My-linux kernel: [17179570.012000] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  1 13:00:21 My-linux kernel: [17179570.016000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
May  1 13:00:21 My-linux kernel: [17179570.016000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
May  1 13:00:21 My-linux kernel: [17179570.016000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
May  1 13:00:21 My-linux kernel: [17179570.016000] PCI: Transparent bridge - 0000:00:1e.0
May  1 13:00:21 My-linux kernel: [17179570.028000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May  1 13:00:21 My-linux kernel: [17179570.028000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
May  1 13:00:21 My-linux kernel: [17179570.028000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May  1 13:00:21 My-linux kernel: [17179570.028000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
May  1 13:00:21 My-linux kernel: [17179570.028000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
May  1 13:00:21 My-linux kernel: [17179570.028000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May  1 13:00:21 My-linux kernel: [17179570.028000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 *11 12 14 15)
May  1 13:00:21 My-linux kernel: [17179570.028000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
May  1 13:00:21 My-linux kernel: [17179570.028000] Linux Plug and Play Support v0.97 (c) Adam Belay
May  1 13:00:21 My-linux kernel: [17179570.028000] pnp: PnP ACPI init
May  1 13:00:21 My-linux kernel: [17179570.032000] pnp: PnP ACPI: found 14 devices
May  1 13:00:21 My-linux kernel: [17179570.032000] PnPBIOS: Disabled by ACPI PNP
May  1 13:00:21 My-linux kernel: [17179570.032000] PCI: Using ACPI for IRQ routing
May  1 13:00:21 My-linux kernel: [17179570.032000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May  1 13:00:21 My-linux kernel: [17179570.060000] pnp: 00:0b: ioport range 0x400-0x4bf could not be reserved
May  1 13:00:21 My-linux kernel: [17179570.060000] PCI: Bridge: 0000:00:01.0
May  1 13:00:21 My-linux kernel: [17179570.060000]   IO window: a000-afff
May  1 13:00:21 My-linux kernel: [17179570.060000]   MEM window: f4000000-f5ffffff
May  1 13:00:21 My-linux kernel: [17179570.060000]   PREFETCH window: d0000000-efffffff
May  1 13:00:21 My-linux kernel: [17179570.060000] PCI: Bridge: 0000:00:03.0
May  1 13:00:21 My-linux kernel: [17179570.060000]   IO window: 9000-9fff
May  1 13:00:21 My-linux kernel: [17179570.060000]   MEM window: f8000000-f80fffff
May  1 13:00:21 My-linux kernel: [17179570.060000]   PREFETCH window: disabled.
May  1 13:00:21 My-linux kernel: [17179570.060000] PCI: Bridge: 0000:00:1e.0
May  1 13:00:21 My-linux kernel: [17179570.060000]   IO window: 6000-8fff
May  1 13:00:21 My-linux kernel: [17179570.060000]   MEM window: f6000000-f7ffffff
May  1 13:00:21 My-linux kernel: [17179570.060000]   PREFETCH window: 30000000-300fffff
May  1 13:00:21 My-linux kernel: [17179570.060000] audit: initializing netlink socket (disabled)
May  1 13:00:21 My-linux kernel: [17179570.060000] audit(1178049590.060:1): initialized
May  1 13:00:21 My-linux kernel: [17179570.060000] VFS: Disk quotas dquot_6.5.1
May  1 13:00:21 My-linux kernel: [17179570.060000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
 

---

### Post by misfito on 2007-05-01
i got more log but what i posted is to long already

Is making me crazy:(

---

