---
title: "hangs for a while on bootup?"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by bzburr on 2006-07-01
Hi
newly installed ubuntu (and excited ubuntu user)
My ubuntu pauses for a long time when load at  "loading hardware drivers" during the boot up phase - can someone suggest what is wrong and what i need to do to fix it?

Buzz

---

### Post by halfvolle melk on 2006-07-01
No clue, but 'dmesg' tells you about stuff that happens during boot time. So open a terminal (Apps > Accs > Terminal) and type
```
dmesg
```
It may show some errors or <something> failed.

---

### Post by bzburr on 2006-07-01
cool ummm


[17179600.104000] drivers/usb/input/hid-core.c: usb_submit_urb(ctrl) failed
[17179600.104000] drivers/usb/input/hid-core.c: timeout initializing report 

and

[17179769.436000] cdrom: open failed.
[17179769.836000] ext3: No journal on filesystem on hda5

and a few other "things"
(full report below)
what do you reckon?
Buzz

===

[17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5d20
[17179569.184000] On node 0 totalpages: 262128
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32752 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AWARD                                 ) @ 0x000f7730
[17179569.184000] ACPI: RSDT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3000
[17179569.184000] ACPI: FADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3040
[17179569.184000] ACPI: MADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff6d00
[17179569.184000] ACPI: DSDT (v001 AWARD  AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:8 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 2000.763 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.152000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.152000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.188000] Memory: 1028816k/1048512k available (1976k kernel code, 18932k reserved, 606k data, 288k init, 131008k highmem)
[17179570.188000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.268000] Calibrating delay using timer specific routine.. 4003.60 BogoMIPS (lpj=8007214)
[17179570.268000] Security Framework v1.0.0 initialized
[17179570.268000] SELinux:  Disabled at boot.
[17179570.268000] Mount-cache hash table entries: 512
[17179570.268000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179570.268000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179570.268000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179570.268000] CPU: L2 Cache: 256K (64 bytes/line)
[17179570.268000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[17179570.268000] mtrr: v2.0 (20020519)
[17179570.268000] CPU: AMD Sempron(tm)   2800+ stepping 01
[17179570.268000] Enabling fast FPU save and restore... done.
[17179570.268000] Enabling unmasked SIMD FPU exception support... done.
[17179570.268000] Checking 'hlt' instruction... OK.
[17179570.284000] checking if image is initramfs... it is
[17179570.808000] Freeing initrd memory: 6614k freed
[17179570.828000] ACPI: Looking for DSDT ... not found!
[17179570.832000] ENABLING IO-APIC IRQs
[17179570.832000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.976000] NET: Registered protocol family 16
[17179570.976000] EISA bus registered
[17179570.976000] ACPI: bus type pci registered
[17179570.992000] PCI: PCI BIOS revision 2.10 entry at 0xfbce0, last bus=1
[17179570.992000] PCI: Using configuration type 1
[17179570.996000] ACPI: Subsystem revision 20051216
[17179571.004000] ACPI: Interpreter enabled
[17179571.004000] ACPI: Using IOAPIC for interrupt routing
[17179571.004000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.004000] PCI: Probing PCI hardware (bus 00)
[17179571.004000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179571.008000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179571.008000] Boot video device is 0000:01:00.0
[17179571.008000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.028000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179571.028000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179571.028000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[17179571.028000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179571.028000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179571.028000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179571.028000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179571.028000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179571.032000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.032000] pnp: PnP ACPI init
[17179571.032000] pnp: PnP ACPI: found 11 devices
[17179571.032000] PnPBIOS: Disabled by ACPI PNP
[17179571.032000] PCI: Using ACPI for IRQ routing
[17179571.032000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.044000] PCI: Device 0000:00:0a.0 not found by BIOS
[17179571.044000] PCI: Bridge: 0000:00:01.0
[17179571.044000]   IO window: 9000-9fff
[17179571.044000]   MEM window: e4000000-e5ffffff
[17179571.044000]   PREFETCH window: c0000000-dfffffff
[17179571.044000] audit: initializing netlink socket (disabled)
[17179571.044000] audit(1151832014.044:1): initialized
[17179571.044000] highmem bounce pool size: 64 pages
[17179571.044000] VFS: Disk quotas dquot_6.5.1
[17179571.044000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.044000] Initializing Cryptographic API
[17179571.044000] io scheduler noop registered
[17179571.044000] io scheduler anticipatory registered
[17179571.044000] io scheduler deadline registered
[17179571.044000] io scheduler cfq registered
[17179571.044000] isapnp: Scanning for PnP cards...
[17179571.400000] isapnp: No Plug & Play device found
[17179571.412000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179571.412000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179571.932000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.932000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.932000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.936000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.936000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.936000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.936000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.936000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.936000] mice: PS/2 mouse device common for all mice
[17179571.940000] EISA: Probing bus 0 at eisa.0
[17179571.940000] Cannot allocate resource for EISA slot 1
[17179571.940000] Cannot allocate resource for EISA slot 4
[17179571.940000] EISA: Detected 0 cards.
[17179571.940000] NET: Registered protocol family 2
[17179571.964000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.988000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.988000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179571.988000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.988000] TCP: Hash tables configured (established 262144 bind 65536)
[17179571.988000] TCP reno registered
[17179571.988000] TCP bic registered
[17179571.988000] NET: Registered protocol family 1
[17179571.988000] NET: Registered protocol family 8
[17179571.988000] NET: Registered protocol family 20
[17179571.988000] Using IPI Shortcut mode
[17179571.988000] ACPI wakeup devices: 
[17179571.988000] FUTS PCI0 USB0 USB1 USB2 USB3 MAC0 AMR0 UAR1 PS2K 
[17179571.988000] ACPI: (supports S0 S3 S4 S5)
[17179571.988000] Freeing unused kernel memory: 288k freed
[17179572.040000] vga16fb: initializing
[17179572.040000] vga16fb: mapped to 0xc00a0000
[17179572.132000] Console: switching to colour frame buffer device 80x25
[17179572.132000] fb0: VGA16 VGA frame buffer device
[17179573.200000] Capability LSM initialized
[17179573.316000] ACPI: Fan [FAN] (on)
[17179573.320000] ACPI: Thermal Zone [THRM] (49 C)
[17179573.904000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179573.908000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.908000] SIS5513: chipset revision 1
[17179573.908000] SIS5513: not 100% native mode: will probe irqs later
[17179573.908000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179573.908000]     ide0: BM-DMA at 0x4000-0x4007, BIOS settings: hda:DMA, hdb:DMA
[17179573.908000]     ide1: BM-DMA at 0x4008-0x400f, BIOS settings: hdc:DMA, hdd:DMA
[17179573.908000] Probing IDE interface ide0...
[17179574.196000] hda: ST320414A, ATA DISK drive
[17179574.476000] hdb: Maxtor 6B200P0, ATA DISK drive
[17179574.532000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.556000] Probing IDE interface ide1...
[17179575.292000] hdc: PIONEER DVD-RW DVR-110D, ATAPI CD/DVD-ROM drive
[17179576.076000] hdd: CREATIVE CD-RW RW2410E, ATAPI CD/DVD-ROM drive
[17179576.132000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.140000] hda: max request size: 128KiB
[17179576.140000] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(100)
[17179576.140000] hda: cache flushes not supported
[17179576.140000]  hda: hda1 hda2 < hda5 >
[17179576.180000] hdb: max request size: 1024KiB
[17179576.180000] hdb: 398297088 sectors (203928 MB) w/8192KiB Cache, CHS=24792/255/63, UDMA(133)
[17179576.184000] hdb: cache flushes supported
[17179576.184000]  hdb: hdb1 hdb2 < hdb5 >
[17179576.204000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[17179576.204000] Uniform CD-ROM driver Revision: 3.20
[17179576.588000] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.636000] SCSI subsystem initialized
[17179576.640000] ACPI: bus type scsi registered
[17179576.640000] libata version 1.20 loaded.
[17179576.640000] sata_sis 0000:00:05.0: version 0.5
[17179576.640000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179576.640000] sata_sis 0000:00:05.0: Detected SiS 180/181 chipset in SATA mode
[17179576.640000] ata1: SATA max UDMA/133 cmd 0xAC00 ctl 0xB002 bmdma 0xBC00 irq 177
[17179576.640000] ata2: SATA max UDMA/133 cmd 0xB400 ctl 0xB802 bmdma 0xBC08 irq 177
[17179576.844000] ata1: no device found (phy stat 00000000)
[17179576.844000] scsi0 : sata_sis
[17179577.048000] ata2: no device found (phy stat 00000000)
[17179577.048000] scsi1 : sata_sis
[17179577.096000] usbcore: registered new driver usbfs
[17179577.096000] usbcore: registered new driver hub
[17179577.100000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179577.100000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 185
[17179577.100000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179577.180000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[17179577.180000] ohci_hcd 0000:00:03.0: irq 185, io mem 0xe7004000
[17179577.236000] hub 1-0:1.0: USB hub found
[17179577.236000] hub 1-0:1.0: 3 ports detected
[17179577.340000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 193
[17179577.340000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179577.380000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[17179577.380000] ohci_hcd 0000:00:03.1: irq 193, io mem 0xe7000000
[17179577.436000] hub 2-0:1.0: USB hub found
[17179577.436000] hub 2-0:1.0: 3 ports detected
[17179577.540000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 201
[17179577.540000] ohci_hcd 0000:00:03.2: OHCI Host Controller
[17179577.568000] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[17179577.568000] ohci_hcd 0000:00:03.2: irq 201, io mem 0xe7001000
[17179577.624000] hub 3-0:1.0: USB hub found
[17179577.624000] hub 3-0:1.0: 2 ports detected
[17179577.728000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 209
[17179577.728000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[17179577.728000] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[17179577.728000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[17179577.728000] ehci_hcd 0000:00:03.3: irq 209, io mem 0xe7002000
[17179577.728000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.728000] hub 4-0:1.0: USB hub found
[17179577.728000] hub 4-0:1.0: 8 ports detected
[17179577.904000] Attempting manual resume
[17179577.936000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.948000] kjournald starting.  Commit interval 5 seconds
[17179578.596000] usb 4-5: new high speed USB device using ehci_hcd and address 3
[17179579.216000] usb 3-1: new low speed USB device using ohci_hcd and address 2
[17179579.736000] usb 3-2: new low speed USB device using ohci_hcd and address 3
[17179589.168000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.192000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.196000] agpgart: Detected SiS 741 chipset
[17179589.204000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179589.220000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.416000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 217
[17179589.572000] sis900.c: v1.08.09 Sep. 19 2005
[17179589.736000] intel8x0_measure_ac97_clock: measured 55608 usecs
[17179589.736000] intel8x0: clocking to 48000
[17179589.736000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 225
[17179589.736000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[17179589.744000] 0000:00:04.0: Using transceiver found at address 1 as default
[17179589.748000] eth0: SiS 900 PCI Fast Ethernet at 0xa800, IRQ 225, 00:11:d8:36:0c:35.
[17179589.748000] ACPI: PCI Interrupt 0000:00:0a.0[?]: no GSI
[17179589.748000] unable to grab memory region 0x0-0x7fff
[17179589.748000] Unable to handle kernel NULL pointer dereference at virtual address 00000154
[17179589.748000]  printing eip:
[17179589.748000] f8a446a3
[17179589.748000] *pde = 00000000
[17179589.748000] Oops: 0000 [#1]
[17179589.748000] PREEMPT 
[17179589.748000] Modules linked in: psmouse serio_raw snd_ymfpci gameport snd_opl3_lib snd_hwdep snd_mpu401_uart snd_rawmidi sis900 mii snd_seq_device snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc shpchp sis_agp agpgart pci_hotplug evdev ext3 jbd ide_generic ehci_hcd ohci_hcd usbcore sata_sis libata scsi_mod ide_cd cdrom ide_disk sis5513 generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[17179589.748000] CPU:    0
[17179589.748000] EIP:    0060:[<f8a446a3>]    Not tainted VLI
[17179589.748000] EFLAGS: 00010002   (2.6.15-25-386) 
[17179589.748000] EIP is at snd_ymfpci_ac3_done+0x13/0x50 [snd_ymfpci]
[17179589.748000] eax: 00000040   ebx: dfa49000   ecx: 00000000   edx: f7c7a000
[17179589.748000] esi: 00000000   edi: dff6dc00   ebp: 0000907f   esp: f7c7be54
[17179589.748000] ds: 007b   es: 007b   ss: 0068
[17179589.748000] Process modprobe (pid: 3030, threadinfo=f7c7a000 task=dfdcf050)
[17179589.748000] Stack: dfa49000 f8a46912 dfa49000 dfa49000 f8a46d48 dfa49000 f8a472f4 00000000 
[17179589.748000]        00007fff 00000800 00000000 00000000 dff6dc00 f8a434a3 f7c4f400 dff6dc00 
[17179589.748000]        0000907f f7c7becc dff75e00 00000050 00000042 00000800 f7c4f400 f8a46ec7 
[17179589.748000] Call Trace:
[17179589.748000]  [<f8a46912>] snd_ymfpci_free+0xa2/0x140 [snd_ymfpci]
[17179589.748000]  [<f8a46d48>] snd_ymfpci_create+0x218/0x250 [snd_ymfpci]
[17179589.748000]  [<f8a434a3>] snd_card_ymfpci_probe+0x1f3/0x6f0 [snd_ymfpci]
[17179589.748000]  [<c01e703c>] __pci_device_probe+0x3c/0x60
[17179589.748000]  [<c01e707f>] pci_device_probe+0x1f/0x40
[17179589.748000]  [<c02445bb>] driver_probe_device+0x3b/0xc0
[17179589.748000]  [<c02446b0>] __driver_attach+0x0/0x40
[17179589.748000]  [<c02446eb>] __driver_attach+0x3b/0x40
[17179589.748000]  [<c0243c98>] bus_for_each_dev+0x48/0x80
[17179589.748000]  [<c0244705>] driver_attach+0x15/0x20
[17179589.748000]  [<c02446b0>] __driver_attach+0x0/0x40
[17179589.748000]  [<c0244139>] bus_add_driver+0x69/0xc0
[17179589.748000]  [<c01e72ca>] __pci_register_driver+0x6a/0xa0
[17179589.748000]  [<f894900f>] alsa_card_ymfpci_init+0xf/0x12 [snd_ymfpci]
[17179589.748000]  [<c013823f>] sys_init_module+0x9f/0x1d0
[17179589.748000]  [<c010304b>] sysenter_past_esp+0x54/0x79
[17179589.748000] Code: 00 8d bc 27 00 00 00 00 b8 f4 ff ff ff 5b c3 e8 94 7f 8a c7 31 c0 eb e3 53 8b 5c 24 08 fa ba 00 e0 ff ff 21 e2 ff 42 14 8b 4b 10 <8b> 81 54 01 00 00 83 e0 e7 89 81 54 01 00 00 fb ff 4a 14 8b 42 
[17179589.748000]  <6>note: modprobe[3030] exited with preempt_count 1
[17179589.960000] Real Time Clock Driver v1.12
[17179589.960000] input: PC Speaker as /class/input/input1
[17179590.040000] usbcore: registered new driver hiddev
[17179590.056000] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input2
[17179590.056000] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:03.2-1
[17179590.268000] Floppy drive(s): fd0 is 1.44M
[17179590.284000] FDC 0 is a post-1991 82077
[17179590.328000] Initializing USB Mass Storage driver...
[17179590.896000] parport: PnPBIOS parport detected.
[17179590.896000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179591.556000] NET: Registered protocol family 17
[17179592.516000] eth0: Media Link On 100mbps full-duplex 
[17179599.152000] NET: Registered protocol family 10
[17179599.152000] lo: Disabled Privacy Extensions
[17179599.152000] IPv6 over IPv4 tunneling driver
[17179600.104000] drivers/usb/input/hid-core.c: usb_submit_urb(ctrl) failed
[17179600.104000] drivers/usb/input/hid-core.c: timeout initializing reports
[17179600.104000] 
[17179600.104000] input: Logitech Logitech Attack 3 as /class/input/input3
[17179600.104000] input: USB HID v1.10 Joystick [Logitech Logitech Attack 3] on usb-0000:00:03.2-2
[17179600.104000] usbcore: registered new driver usbhid
[17179600.104000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179600.104000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179600.104000] usb-storage: device found at 3
[17179600.104000] usb-storage: waiting for device to settle before scanning
[17179600.104000] usbcore: registered new driver usb-storage
[17179600.104000] USB Mass Storage support registered.
[17179600.136000] ts: Compaq touchscreen protocol output
[17179605.104000]   Vendor: HDT72252  Model: 5DLAT80           Rev: 0000
[17179605.104000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179605.108000] usb-storage: device scan complete
[17179605.132000] Driver 'sd' needs updating - please use bus_type methods
[17179605.136000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179605.136000] sda: assuming drive cache: write through
[17179605.140000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179605.140000] sda: assuming drive cache: write through
[17179605.140000]  sda: sda1
[17179605.156000] sd 2:0:0:0: Attached scsi disk sda
[17179605.164000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17179609.332000] eth0: no IPv6 routers present
[17179766.572000] lp0: using parport0 (interrupt-driven).
[17179766.632000] Unable to handle swap header version 104608
[17179766.756000] EXT3 FS on hda1, internal journal
[17179766.952000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179766.952000] md: bitmap version 4.39
[17179767.632000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179769.436000] cdrom: open failed.
[17179769.836000] ext3: No journal on filesystem on hda5
[17179769.848000] Unable to handle swap header version 104608
[17179771.080000] ACPI: Power Button (FF) [PWRF]
[17179771.080000] ACPI: Power Button (CM) [PWRB]
[17179771.080000] ACPI: Sleep Button (CM) [FUTS]
[17179771.196000] ibm_acpi: ec object not found
[17179771.232000] pcc_acpi: loading...
[17179777.508000] ppdev: user-space parallel port driver
[17179778.068000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179778.068000] apm: overridden by ACPI.
[17179781.556000] Bluetooth: Core ver 2.8
[17179781.556000] NET: Registered protocol family 31
[17179781.556000] Bluetooth: HCI device and connection manager initialized
[17179781.556000] Bluetooth: HCI socket layer initialized
[17179781.580000] Bluetooth: L2CAP ver 2.8
[17179781.580000] Bluetooth: L2CAP socket layer initialized
[17179781.584000] Bluetooth: RFCOMM socket layer initialized
[17179781.584000] Bluetooth: RFCOMM TTY layer initialized
[17179781.584000] Bluetooth: RFCOMM ver 1.7
[17179810.400000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179810.664000] ISOFS: changing to secondary root
[17179811.492000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180092.356000] ibm_acpi: ec object not found

---

### Post by givré on 2006-07-01
For me all is alright.
Try to boot on recovery mode and see where it hangs

---

### Post by bzburr on 2006-07-01
ahh its at etho:No IPv6 routers present

presumably i need to remove ipv6 something or other?

Buzz

---

### Post by givré on 2006-07-01
Try that [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by bzburr on 2006-07-01
thanks dude
followed the instructions there and now its hanging for a long time at
eth0:Media link on 100mbps full duplex 

:(
Buzz

---

### Post by bzburr on 2006-07-02
erm, hello anybody?
how do i fix ubuntu so it no longer takes _ages_ at
"eth0:Media link on 100mbps full duplex " when booting up?

Buzz

---

