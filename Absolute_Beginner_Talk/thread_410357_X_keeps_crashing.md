---
title: "X keeps crashing"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by 3ntity on 2007-04-15
Hey,
I run Dapper and Gnome. X keeps crashing on me when starting several applications; i try running the application, a black screen shows and it loads the login screen again [i.e. X restarts, i guess]. These include: Kaffeine, wine[cfg] or any wine-related application as well as the screensaver, which i've obviously turned off. AmaroK runs badly:i sometimes get an error message 'Cannot talk to klauncer', the media library is only filled half of the time. I have amaroK set to launch at startup, and have noticed lately that it can take very long for the icon to show after logging in.
The only 'important' things i've done as of late were to install dapper updates and compile wine from source. Any thoughts as to what i could have done wrong?
I should be upgrading to feisty when it comes out, but i'd still like to know what i've done wrong and how i can solve and prevent this.
Thanks in advance!

---

### Post by lamalex on 2007-04-15
next time this happens take look through dmesg and see if it's giving any relevant output, also do ```
cat /etc/X11/xorg.conf |grep vesa
```
and see if it comes back with anything, maybe you're using the wrong graphics driver.

---

### Post by 3ntity on 2007-04-15
> **Iamalex said:**
> next time this happens take look through dmesg and see if it's giving any relevant output, also do ```
cat /etc/X11/xorg.conf |grep vesa
```
and see if it comes back with anything, maybe you're using the wrong graphics driver.

Hey, thanks for the swift reply :)
Here's the output from dmesg - i can't make much out of it:
```
~$ dmesg
[17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4. 0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[17179569.184000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 126MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5b00
[17179569.184000] On node 0 totalpages: 261872
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32496 pages, LIFO batch:7
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 AWARD                                 ) @ 0x0 00f7510
[17179569.184000] ACPI: RSDT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @  0x3fef3040
[17179569.184000] ACPI: FADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @  0x3fef30c0
[17179569.184000] ACPI: MADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @  0x3fef6a40
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20040311) @  0x3fef6af0
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20040311) @  0x3fef6f80
[17179569.184000] ACPI: DSDT (v001 AWARD  AWRDACPI 0x00001000 MSFT 0x0100000e) @  0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:4 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:b ed00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdb3 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 3517.659 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.460000] Dentry cache hash table entries: 131072 (order: 7, 524288 byte s)
[17179569.460000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.484000] Memory: 1027808k/1047488k available (1977k kernel code, 18928k  reserved, 605k data, 288k init, 129984k highmem)
[17179569.484000] Checking if this processor honours the WP bit even in supervis or mode... Ok.
[17179569.564000] Calibrating delay using timer specific routine.. 7038.62 BogoM IPS (lpj=14077241)
[17179569.564000] Security Framework v1.0.0 initialized
[17179569.564000] SELinux:  Disabled at boot.
[17179569.564000] Mount-cache hash table entries: 512
[17179569.564000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000649d 00000000 00000000
[17179569.564000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 0 0000000 0000649d 00000000 00000000
[17179569.564000] monitor/mwait feature present.
[17179569.564000] using mwait in idle threads.
[17179569.564000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.564000] CPU: L2 cache: 2048K
[17179569.564000] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000008 0 0000649d 00000000 00000000
[17179569.564000] mtrr: v2.0 (20020519)
[17179569.564000] CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[17179569.564000] Enabling fast FPU save and restore... done.
[17179569.564000] Enabling unmasked SIMD FPU exception support... done.
[17179569.564000] Checking 'hlt' instruction... OK.
[17179569.580000] checking if image is initramfs... it is
[17179570.024000] Freeing initrd memory: 6618k freed
[17179570.036000] ACPI: Looking for DSDT ... not found!
[17179570.040000] ENABLING IO-APIC IRQs
[17179570.040000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.184000] NET: Registered protocol family 16
[17179570.184000] EISA bus registered
[17179570.184000] ACPI: bus type pci registered
[17179570.192000] PCI: PCI BIOS revision 2.10 entry at 0xfb5f0, last bus=1
[17179570.192000] PCI: Using configuration type 1
[17179570.192000] ACPI: Subsystem revision 20051216
[17179570.200000] ACPI: Interpreter enabled
[17179570.200000] ACPI: Using IOAPIC for interrupt routing
[17179570.200000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.200000] PCI: Probing PCI hardware (bus 00)
[17179570.200000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.204000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179570.204000] Boot video device is 0000:01:00.0
[17179570.204000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.220000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 14 15 )
[17179570.220000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 14 15 )
[17179570.220000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 14 15 )
[17179570.220000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 14 15 )
[17179570.220000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 14 15 )
[17179570.220000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 14 15 )
[17179570.220000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 14 15 )
[17179570.220000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 14 15 )
[17179570.220000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.220000] pnp: PnP ACPI init
[17179570.224000] pnp: PnP ACPI: found 11 devices
[17179570.224000] PnPBIOS: Disabled by ACPI PNP
[17179570.224000] PCI: Using ACPI for IRQ routing
[17179570.224000] PCI: If a device doesn't work, try "pci=routeirq".  If it help s, post a report
[17179570.256000] PCI: Bridge: 0000:00:01.0
[17179570.256000]   IO window: disabled.
[17179570.256000]   MEM window: e8000000-eaffffff
[17179570.256000]   PREFETCH window: d0000000-dfffffff
[17179570.256000] audit: initializing netlink socket (disabled)
[17179570.256000] audit(1176659650.256:1): initialized
[17179570.256000] highmem bounce pool size: 64 pages
[17179570.256000] VFS: Disk quotas dquot_6.5.1
[17179570.256000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.256000] Initializing Cryptographic API
[17179570.256000] io scheduler noop registered
[17179570.256000] io scheduler anticipatory registered
[17179570.256000] io scheduler deadline registered
[17179570.256000] io scheduler cfq registered
[17179570.256000] isapnp: Scanning for PnP cards...
[17179570.608000] isapnp: No Plug & Play device found
[17179570.620000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.652000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.656000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.656000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shar ing enabled
[17179571.656000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.656000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.656000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 b locksize
[17179571.656000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.656000] ide: Assuming 33MHz system bus speed for PIO modes; override w ith idebus=xx
[17179571.656000] mice: PS/2 mouse device common for all mice
[17179571.664000] EISA: Probing bus 0 at eisa.0
[17179571.664000] Cannot allocate resource for EISA slot 1
[17179571.664000] Cannot allocate resource for EISA slot 4
[17179571.664000] EISA: Detected 0 cards.
[17179571.664000] NET: Registered protocol family 2
[17179571.704000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.716000] IP route cache hash table entries: 32768 (order: 5, 131072 byt es)
[17179571.716000] TCP established hash table entries: 131072 (order: 7, 524288 b ytes)
[17179571.716000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.716000] TCP: Hash tables configured (established 131072 bind 65536)
[17179571.716000] TCP reno registered
[17179571.716000] TCP bic registered
[17179571.716000] NET: Registered protocol family 1
[17179571.716000] NET: Registered protocol family 8
[17179571.716000] NET: Registered protocol family 20
[17179571.716000] Using IPI Shortcut mode
[17179571.716000] ACPI wakeup devices:
[17179571.716000] FUTS PCI0 USB0 USB1 USB2 USB3 MAC0 AMR0 UAR1 PS2M PS2K
[17179571.716000] ACPI: (supports S0 S3 S4 S5)
[17179571.716000] Freeing unused kernel memory: 288k freed
[17179571.752000] vga16fb: initializing
[17179571.752000] vga16fb: mapped to 0xc00a0000
[17179572.204000] Console: switching to colour frame buffer device 80x25
[17179572.204000] fb0: VGA16 VGA frame buffer device
[17179573.296000] Capability LSM initialized
[17179573.528000] ACPI: Fan [FAN] (on)
[17179573.532000] ACPI: Thermal Zone [THRM] (50 C)
[17179574.108000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179574.108000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.108000] SIS5513: chipset revision 1
[17179574.108000] SIS5513: not 100% native mode: will probe irqs later
[17179574.108000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179574.108000]     ide0: BM-DMA at 0x4000-0x4007, BIOS settings: hda:DMA, hdb :pio
[17179574.108000]     ide1: BM-DMA at 0x4008-0x400f, BIOS settings: hdc:pio, hdd :pio
[17179574.108000] Probing IDE interface ide0...
[17179574.620000] hdb: ST3200822A, ATA DISK drive
[17179574.676000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.680000] Probing IDE interface ide1...
[17179575.696000] hdd: BENQ DVD DD DW1640, ATAPI CD/DVD-ROM drive
[17179575.752000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.756000] hdb: max request size: 1024KiB
[17179575.764000] hdb: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/ 255/63, UDMA(100)
[17179575.764000] hdb: cache flushes supported
[17179575.764000]  hdb: hdb1 hdb2 < hdb5 hdb6 > hdb3 hdb4
[17179575.820000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA (33)
[17179575.820000] Uniform CD-ROM driver Revision: 3.20
[17179576.076000] SCSI subsystem initialized
[17179576.076000] ACPI: bus type scsi registered
[17179576.076000] libata version 1.20 loaded.
[17179576.076000] sata_sis 0000:00:05.0: version 0.5
[17179576.076000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179576.076000] sata_sis 0000:00:05.0: Detected SiS 180/181 chipset in SATA mo de
[17179576.076000] ata1: SATA max UDMA/133 cmd 0xDC00 ctl 0xE002 bmdma 0xEC00 irq  177
[17179576.076000] ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE802 bmdma 0xEC08 irq  177
[17179576.292000] ata1: dev 0 cfg 00:0040 49:2f00 82:7c6b 83:7f09 84:4673 85:7c6 9 86:3e21 87:4663 88:007f 93:0000
[17179576.292000] ata1: dev 0 ATA-7, max UDMA/133, 490234752 sectors: LBA48
[17179576.292000] sata_get_dev_handle: SATA dev addr=0x50000, handle=0xdffe7940
[17179576.296000] ata1: dev 0 configured for UDMA/133
[17179576.296000] sata_get_dev_handle: SATA dev addr=0x50000, handle=0xdffe7940
[17179576.300000] scsi0 : sata_sis
[17179576.504000] ata2: no device found (phy stat 00000000)
[17179576.504000] scsi1 : sata_sis
[17179576.504000]   Vendor: ATA       Model: Maxtor 6L250S0    Rev: BACE
[17179576.504000]   Type:   Direct-Access                      ANSI SCSI revisio n: 05
[17179576.508000] Driver 'sd' needs updating - please use bus_type methods
[17179576.508000] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[17179576.508000] SCSI device sda: drive cache: write back
[17179576.512000] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[17179576.512000] SCSI device sda: drive cache: write back
[17179576.512000]  sda: sda1 sda2 < sda5 sda6 >
[17179576.560000] sd 0:0:0:0: Attached scsi disk sda
[17179576.804000] usbcore: registered new driver usbfs
[17179576.804000] usbcore: registered new driver hub
[17179576.804000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179576.804000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 185
[17179576.804000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179576.848000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus nu mber 1
[17179576.848000] ohci_hcd 0000:00:03.0: irq 185, io mem 0xec004000
[17179576.904000] hub 1-0:1.0: USB hub found
[17179576.904000] hub 1-0:1.0: 3 ports detected
[17179577.008000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 193
[17179577.008000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179577.036000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus nu mber 2
[17179577.036000] ohci_hcd 0000:00:03.1: irq 193, io mem 0xec000000
[17179577.092000] hub 2-0:1.0: USB hub found
[17179577.092000] hub 2-0:1.0: 3 ports detected
[17179577.196000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 201
[17179577.196000] ohci_hcd 0000:00:03.2: OHCI Host Controller
[17179577.224000] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus nu mber 3
[17179577.224000] ohci_hcd 0000:00:03.2: irq 201, io mem 0xec001000
[17179577.280000] hub 3-0:1.0: USB hub found
[17179577.280000] hub 3-0:1.0: 2 ports detected
[17179577.384000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 209
[17179577.384000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[17179577.384000] PCI: cache line size of 128 is not supported by device 0000:00 :03.3
[17179577.384000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus nu mber 4
[17179577.384000] ehci_hcd 0000:00:03.3: irq 209, io mem 0xec002000
[17179577.384000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 D ec 2004
[17179577.384000] hub 4-0:1.0: USB hub found
[17179577.384000] hub 4-0:1.0: 8 ports detected
[17179577.532000] Attempting manual resume
[17179577.556000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.564000] kjournald starting.  Commit interval 5 seconds
[17179578.192000] usb 3-1: new full speed USB device using ohci_hcd and address 2
[17179583.472000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179584.592000] sis900.c: v1.08.09 Sep. 19 2005
[17179584.592000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 217
[17179584.596000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address  9.
[17179584.628000] 0000:00:04.0: Using transceiver found at address 9 as default
[17179584.632000] eth0: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 217, 00:50:8d:7 7:10:18.
[17179584.648000] Linux agpgart interface v0.101 (c) Dave Jones
[17179584.652000] agpgart: Detected SiS 661 chipset
[17179584.660000] agpgart: AGP aperture is 128M @ 0xe0000000
[17179584.776000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 225
[17179585.036000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer d ev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0169
[17179585.036000] usbcore: registered new driver usblp
[17179585.036000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class dri ver
[17179585.048000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179585.092000] intel8x0_measure_ac97_clock: measured 54836 usecs
[17179585.092000] intel8x0: clocking to 48000
[17179585.096000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179585.112000] Initializing USB Mass Storage driver...
[17179585.112000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179585.112000] usb-storage: device found at 2
[17179585.112000] usb-storage: waiting for device to settle before scanning
[17179585.112000] usbcore: registered new driver usb-storage
[17179585.112000] USB Mass Storage support registered.
[17179585.244000] Real Time Clock Driver v1.12
[17179585.248000] input: PC Speaker as /class/input/input1
[17179585.300000] Floppy drive(s): fd0 is 1.44M
[17179585.332000] FDC 0 is a post-1991 82077
[17179585.352000] parport: PnPBIOS parport detected.
[17179585.352000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRIST ATE,COMPAT,ECP,DMA]
[17179585.540000] input: PS2++ Logitech MX Mouse as /class/input/input2
[17179585.696000] nvidia: module license 'NVIDIA' taints kernel.
[17179585.788000] ts: Compaq touchscreen protocol output
[17179585.960000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179585.960000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec  15 09:54:45 PST 2006
[17179587.032000] lp0: using parport0 (interrupt-driven).
[17179587.068000] Adding 2096472k swap on /dev/hdb1.  Priority:-1 extents:1 acro ss:2096472k
[17179587.368000] eth0: Media Link On 100mbps full-duplex
[17179587.368000] EXT3 FS on hdb3, internal journal
[17179587.484000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179587.484000] md: bitmap version 4.39
[17179587.616000] NET: Registered protocol family 10
[17179587.616000] lo: Disabled Privacy Extensions
[17179587.616000] IPv6 over IPv4 tunneling driver
[17179588.144000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@ redhat.com
[17179589.228000] cdrom: open failed.
[17179590.128000]   Vendor: Brother   Model: DCP-110C          Rev: 1.00
[17179590.128000]   Type:   Direct-Access                      ANSI SCSI revisio n: 02
[17179590.188000] sd 2:0:0:0: Attached scsi removable disk sdb
[17179590.188000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[17179590.192000] usb-storage: device scan complete
[17179598.156000] eth0: no IPv6 routers present
[17179607.616000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179607.656000] NTFS volume version 3.1.
[17179607.684000] kjournald starting.  Commit interval 5 seconds
[17179607.684000] EXT3 FS on sda5, internal journal
[17179607.684000] EXT3-fs: mounted filesystem with ordered data mode.
[17179607.728000] kjournald starting.  Commit interval 5 seconds
[17179607.728000] EXT3 FS on sda6, internal journal
[17179607.728000] EXT3-fs: mounted filesystem with ordered data mode.
[17179607.760000] kjournald starting.  Commit interval 5 seconds
[17179607.760000] EXT3 FS on hdb4, internal journal
[17179607.760000] EXT3-fs: mounted filesystem with ordered data mode.
[17179607.796000] FAT: utf8 is not a recommended IO charset for FAT filesystems,  filesystem will be case sensitive!
[17179607.856000] kjournald starting.  Commit interval 5 seconds
[17179607.856000] EXT3 FS on hdb6, internal journal
[17179607.856000] EXT3-fs: mounted filesystem with ordered data mode.
[17179609.364000] NET: Registered protocol family 17
[17179613.524000] ACPI: Power Button (FF) [PWRF]
[17179613.524000] ACPI: Power Button (CM) [PWRB]
[17179613.524000] ACPI: Sleep Button (CM) [FUTS]
[17179613.592000] ibm_acpi: ec object not found
[17179613.620000] pcc_acpi: loading...
[17179617.436000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179617.436000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179617.436000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179618.864000] ppdev: user-space parallel port driver
[17179619.296000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179619.296000] apm: overridden by ACPI.
[17179621.516000] Bluetooth: Core ver 2.8
[17179621.516000] NET: Registered protocol family 31
[17179621.516000] Bluetooth: HCI device and connection manager initialized
[17179621.516000] Bluetooth: HCI socket layer initialized
[17179621.536000] Bluetooth: L2CAP ver 2.8
[17179621.536000] Bluetooth: L2CAP socket layer initialized
[17179621.572000] Bluetooth: RFCOMM socket layer initialized
[17179621.572000] Bluetooth: RFCOMM TTY layer initialized
[17179621.572000] Bluetooth: RFCOMM ver 1.7
[17190175.832000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17190175.832000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17190175.832000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17195757.472000] cdrom: This disc doesn't have any tracks I recognize!
[17195865.412000] cdrom: This disc doesn't have any tracks I recognize!
[17195865.436000] cdrom: This disc doesn't have any tracks I recognize!
[17195865.644000] cdrom: This disc doesn't have any tracks I recognize!
[17195866.412000] scsi: unknown opcode 0x01
[17195922.848000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17195923.000000] ISO 9660 Extensions: RRIP_1991A
[17197570.184000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17197570.184000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17197570.188000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17199612.372000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17199612.372000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17199612.372000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

```

```
cat /etc/X11/xorg.conf |grep vesa
``` returns zilch

---

### Post by nautilus on 2007-04-15
Might we see the contents of /var/log/Xorg.0.log?

---

### Post by 3ntity on 2007-04-16
> **nautilus said:**
> Might we see the contents of /var/log/Xorg.0.log?

```
~$ cat /var/log/Xorg.0.log

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux Inti-ubuntu 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 16 10:28:57 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "BlankTime" "0"
(**) Option "StandbyTime" "0"
(**) Option "SuspendTime" "0"
(**) Option "OffTime" "0"
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.8
        X.Org XInput driver : 0.5
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(++) using VT number 8

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0661 card 147b,1807 rev 11 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1039,0003 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0964 card 0000,0000 rev 36 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 147b,1807 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 147b,1807 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 147b,1807 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 147b,1807 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 147b,1807 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 147b,1807 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 147b,1807 rev 91 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 1039,0180 card 147b,1807 rev 01 class 01,01,85 hdr 00
(II) PCI: 01:00:0: chip 10de,00f2 card 0000,0000 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xe8000000 - 0xeaffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] rev 162, Mem @ 0xe8000000/24, 0xd0000000/28, 0xe9000000/24
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xec003000 - 0xec003fff (0x1000) MX[B]
        [1] -1  0       0xec002000 - 0xec002fff (0x1000) MX[B]
        [2] -1  0       0xec001000 - 0xec001fff (0x1000) MX[B]
        [3] -1  0       0xec000000 - 0xec000fff (0x1000) MX[B]
        [4] -1  0       0xec004000 - 0xec004fff (0x1000) MX[B]
        [5] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [6] -1  0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [7] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [8] -1  0       0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
        [9] -1  0       0x0000ec00 - 0x0000ec0f (0x10) IX[B]
        [10] -1 0       0x0000e800 - 0x0000e803 (0x4) IX[B]
        [11] -1 0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [12] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [13] -1 0       0x0000dc00 - 0x0000dc07 (0x8) IX[B]
        [14] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [15] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [16] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [17] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xec003000 - 0xec003fff (0x1000) MX[B]
        [1] -1  0       0xec002000 - 0xec002fff (0x1000) MX[B]
        [2] -1  0       0xec001000 - 0xec001fff (0x1000) MX[B]
        [3] -1  0       0xec000000 - 0xec000fff (0x1000) MX[B]
        [4] -1  0       0xec004000 - 0xec004fff (0x1000) MX[B]
        [5] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [6] -1  0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [7] -1  0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [8] -1  0       0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
        [9] -1  0       0x0000ec00 - 0x0000ec0f (0x10) IX[B]
        [10] -1 0       0x0000e800 - 0x0000e803 (0x4) IX[B]
        [11] -1 0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [12] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [13] -1 0       0x0000dc00 - 0x0000dc07 (0x8) IX[B]
        [14] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [15] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [16] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [17] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xec003000 - 0xec003fff (0x1000) MX[B]
        [5] -1  0       0xec002000 - 0xec002fff (0x1000) MX[B]
        [6] -1  0       0xec001000 - 0xec001fff (0x1000) MX[B]
        [7] -1  0       0xec000000 - 0xec000fff (0x1000) MX[B]
        [8] -1  0       0xec004000 - 0xec004fff (0x1000) MX[B]
        [9] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [10] -1 0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [11] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [12] -1 0       0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x0000ec00 - 0x0000ec0f (0x10) IX[B]
        [16] -1 0       0x0000e800 - 0x0000e803 (0x4) IX[B]
        [17] -1 0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [18] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [19] -1 0       0x0000dc00 - 0x0000dc07 (0x8) IX[B]
        [20] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [21] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [22] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [23] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.0.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9746
        Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9746  Fri Dec 15 09:56:41 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
        compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xec003000 - 0xec003fff (0x1000) MX[B]
        [5] -1  0       0xec002000 - 0xec002fff (0x1000) MX[B]
        [6] -1  0       0xec001000 - 0xec001fff (0x1000) MX[B]
        [7] -1  0       0xec000000 - 0xec000fff (0x1000) MX[B]
        [8] -1  0       0xec004000 - 0xec004fff (0x1000) MX[B]
        [9] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [10] -1 0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [11] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [12] -1 0       0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x0000ec00 - 0x0000ec0f (0x10) IX[B]
        [16] -1 0       0x0000e800 - 0x0000e803 (0x4) IX[B]
        [17] -1 0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [18] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [19] -1 0       0x0000dc00 - 0x0000dc07 (0x8) IX[B]
        [20] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [21] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [22] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [23] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xec003000 - 0xec003fff (0x1000) MX[B]
        [5] -1  0       0xec002000 - 0xec002fff (0x1000) MX[B]
        [6] -1  0       0xec001000 - 0xec001fff (0x1000) MX[B]
        [7] -1  0       0xec000000 - 0xec000fff (0x1000) MX[B]
        [8] -1  0       0xec004000 - 0xec004fff (0x1000) MX[B]
        [9] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [10] -1 0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [11] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [12] -1 0       0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
        [13] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [14] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [15] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x0000ec00 - 0x0000ec0f (0x10) IX[B]
        [19] -1 0       0x0000e800 - 0x0000e803 (0x4) IX[B]
        [20] -1 0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [21] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [22] -1 0       0x0000dc00 - 0x0000dc07 (0x8) IX[B]
        [23] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [24] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [25] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [26] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
        [27] 0  0       0xea0003b0 - 0xea0003bb (0xc) IS[B]
        [28] 0  0       0xea0003c0 - 0xea0003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.66.52
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 at PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B]
        [1] 0   0       0xd0000000 - 0xdfffffff (0x10000000) MX[B]
        [2] 0   0       0xe8000000 - 0xe8ffffff (0x1000000) MX[B]
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xec003000 - 0xec003fff (0x1000) MX[B]
        [8] -1  0       0xec002000 - 0xec002fff (0x1000) MX[B]
        [9] -1  0       0xec001000 - 0xec001fff (0x1000) MX[B]
        [10] -1 0       0xec000000 - 0xec000fff (0x1000) MX[B]
        [11] -1 0       0xec004000 - 0xec004fff (0x1000) MX[B]
        [12] -1 0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [13] -1 0       0xe9000000 - 0xe9ffffff (0x1000000) MX[B](B)
        [14] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [15] -1 0       0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
        [16] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [17] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [18] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [19] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [20] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [21] -1 0       0x0000ec00 - 0x0000ec0f (0x10) IX[B]
        [22] -1 0       0x0000e800 - 0x0000e803 (0x4) IX[B]
        [23] -1 0       0x0000e400 - 0x0000e407 (0x8) IX[B]
        [24] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [25] -1 0       0x0000dc00 - 0x0000dc07 (0x8) IX[B]
        [26] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [27] -1 0       0x0000d400 - 0x0000d47f (0x80) IX[B]
        [28] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [29] -1 0       0x00004000 - 0x0000400f (0x10) IX[B]
        [30] 0  0       0xea0003b0 - 0xea0003bb (0xc) IS[B]
        [31] 0  0       0xea0003c0 - 0xea0003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
AUDIT: Mon Apr 16 10:29:00 2007: 5093 X: client 2 rejected from local host
AUDIT: Mon Apr 16 10:29:00 2007: 5093 X: client 4 rejected from local host
AUDIT: Mon Apr 16 10:29:00 2007: 5093 X: client 3 rejected from local host
AUDIT: Mon Apr 16 10:29:00 2007: 5093 X: client 6 rejected from local host
AUDIT: Mon Apr 16 10:29:00 2007: 5093 X: client 5 rejected from local host
AUDIT: Mon Apr 16 10:29:00 2007: 5093 X: client 2 rejected from local host

```
I guess the code at lines 346-350 indicate the possible problem:
```
...
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 at PCI:1:0:0 (GPU-0)
...
```

---

### Post by nautilus on 2007-04-16
Ahh perhaps, even so it should still work with GLX, just exceptionally slow.

But who cares, you want accelerated 3D anyway, right?

Unfortunately, I'm not the ubuntu 3d glx / nvidia pro around here (i do it manually *dodges floggings*) but I'm sure.. somebody knows...

In any case, hopefully that fixes the issue, when it's setup properly.

---

### Post by Thinkaboutit on 2007-04-17
I'm having the exact same problem... anyone found a fix yet? Or would it be best just to reinstall the nvidia drivers?

---

### Post by 3ntity on 2007-04-19
> **Thinkaboutit said:**
> I'm having the exact same problem... anyone found a fix yet? Or would it be best just to reinstall the nvidia drivers?

I'll be upgrading to Feisty this afternoon so i won't even try reinstalling the nVidia drivers... let me know if reinstalling helped though...
ps. i'd used envy to install the nvidia drivers...

---

### Post by talcite on 2007-04-21
I've had a similar problem before. Here's how I fixed it...

Firstly, nvidia-xconfig seems to conflict with the GLX package, so I removed that. 

One other thing that you might want to look out for is the envy script. It's a script that installs the latest nvidia driver for you. One button. 

That's pretty much all I had to do in order to get it up and running. 

GLX is required for most OpenGL and 3D stuff, so that's probably where your problem is.

---

### Post by 3ntity on 2007-04-22
> **talcite said:**
> 
One other thing that you might want to look out for is the envy script. It's a script that installs the latest nvidia driver for you. One button. 
I had installed the driver through envy :) Oh-so-useful and easy :)
> 
GLX is required for most OpenGL and 3D stuff, so that's probably where your problem is.

... which leads me to believe that Kaffeine uses GLX to render videos? Somehow that doesn't sound right tho... Totem and VLC didn't have problems displaying these videos, tho i prefer Kaffeine way more [who said VLC plays EVERYTHING? never's that been the case on my pc :/]

Oh yea, Feisty is wonderful :D It runs so much smoother than Dapper. ...so far :p

---

### Post by joeyea on 2007-06-30
hi i had this problem for ages and im a bit of a newbie so i didnt really no what to do.
After some fiddling around i realised if a ran the program from terminal and put sudo in front  it worked.
hope this is helpfull.

joe

---

### Post by mendingo84 on 2007-06-30
if you did the kernel upgrade yesterday (the one in the backports) and you run NVidia, then use Envy to reinstall the Nvidia driver ;). I did that :D. I'm on KDE and Aiglx though but i don't think it makes a difference. If you have the latest Nvidia drivers and do a kernel upgrade you have to reinstall the video drivers.

---

### Post by HunkirDowne on 2007-06-30
I have nVidia working here on Ubuntu feisty fawn but not on Debian etch.  Ubuntu works because "it just works" :^).   (Translation: I didn't do anything special -- default install as far as X & Gnome go.)  On Debian if I do a normal boot I get the background but a perpetual swirly and the little splash that shows what's loading doesn't appear.  If I switch the call to gdm to look for it in another directory, I get the little splash but no background (just the X hatches).  I'm probably way off on my verbiage but can clarify if there is any interest.  I can upload files from what works or from what doesn't work if that'll help.  I'd like to get Debian running here (runs on my desktop fine) but am doing just fine with Ubuntu so it's not like it's critical.

Hardware: Toshiba Satellite P25-S5092 +ubuntu -debian +ubuntuCE +xp
Dell Dimension 8200 +debian +ubuntuCE ?ubuntu.  (don't really remember if stock ubuntu works but I think something got hozed during install -- something I did with the partitions).

---

