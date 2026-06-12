---
title: "User Can No longer Startx"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by taddy_porter on 2007-05-05
I have an edgy system that was working perfectly. Yesterday when I logged in I got the normal KDM screen (using Gnome desktop with KDE apps). When I log in I get the Nvidia logo, then a quick grey screen, then it goes back to the KDM menu.

I tried logging in via the console. What I get is errors about cannot find font directories and then it gets thrown back to the console. I can su root then log in fine and I get a default desktop (which I'm using now). 

I figured the problem was the Nvidia drivers so I first tried dpkg -reconfigure -phigh xserver-xorg. That didn't work, so I went through the whole reconfigure process. Still same problem.

I just now tried upgrading the nvidiaglx-new drivers for Feisty, including the new kernel, but still the same problem.

I know I have issues with Python2.5 that are not allowing me to update to full Feisty(worrying about those later), but I don't think that has anything to do with my log on issues.

What should I try next?

---

### Post by Ph0B1uS on 2007-05-05
> **taddy_porter said:**
> I have an edgy system that was working perfectly. Yesterday when I logged in I got the normal KDM screen (using Gnome desktop with KDE apps). When I log in I get the Nvidia logo, then a quick grey screen, then it goes back to the KDM menu.

I tried logging in via the console. What I get is errors about cannot find font directories and then it gets thrown back to the console. I can su root then log in fine and I get a default desktop (which I'm using now). 

I figured the problem was the Nvidia drivers so I first tried dpkg -reconfigure -phigh xserver-xorg. That didn't work, so I went through the whole reconfigure process. Still same problem.

I just now tried upgrading the nvidiaglx-new drivers for Feisty, including the new kernel, but still the same problem.

I know I have issues with Python2.5 that are not allowing me to update to full Feisty(worrying about those later), but I don't think that has anything to do with my log on issues.

What should I try next?

Well an output from cat /var/log/xorg.log and an output from dmesg would be nice as it probably contains hints as to why the xserver won't start.

As for the python-issue i've no idea, a little more info would be nice on that issue too.

---

### Post by taddy_porter on 2007-05-05
Here's my dmsg:
```
[    0.000000] Linux version 2.6.20-15-386 (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Sun Apr 15 07:34:00 UTC 2007 (Ubuntu 2.6.20-15.27-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 00000000000a0000 end: 00000000000a0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 0000000000003000 end: 000000003fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000003fff3000 size: 000000000000d000 end: 0000000040000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 VIA694                                ) @ 0x000f7080
[    0.000000] ACPI: RSDT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3000
[    0.000000] ACPI: FADT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3040
[    0.000000] ACPI: DSDT (v001 VIA694 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Detected 1600.839 MHz processor.
[   35.397491] Built 1 zonelists.  Total pages: 260081
[   35.397494] Kernel command line: root=/dev/hdd2 ro quiet splash
[   35.397701] Found and enabled local APIC!
[   35.397704] mapped APIC to ffffd000 (fee00000)
[   35.397710] Enabling fast FPU save and restore... done.
[   35.397712] Enabling unmasked SIMD FPU exception support... done.
[   35.397726] Initializing CPU#0
[   35.397813] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   35.399171] Console: colour VGA+ 80x25
[   35.400205] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   35.401851] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   35.438667] Memory: 1029868k/1048512k available (1916k kernel code, 17820k reserved, 864k data, 328k init, 131008k highmem)
[   35.438680] virtual kernel memory layout:
[   35.438681]     fixmap  : 0xfffa9000 - 0xfffff000   ( 344 kB)
[   35.438683]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   35.438685]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   35.438686]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   35.438688]       .init : 0xc03ba000 - 0xc040c000   ( 328 kB)
[   35.438690]       .data : 0xc02df353 - 0xc03b7434   ( 864 kB)
[   35.438691]       .text : 0xc0100000 - 0xc02df353   (1916 kB)
[   35.438695] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   35.517689] Calibrating delay using timer specific routine.. 3204.12 BogoMIPS (lpj=6408240)
[   35.517739] Security Framework v1.0.0 initialized
[   35.517752] SELinux:  Disabled at boot.
[   35.517770] Mount-cache hash table entries: 512
[   35.517946] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[   35.517957] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   35.517961] CPU: L2 Cache: 256K (64 bytes/line)
[   35.517964] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[   35.517980] Compat vDSO mapped to ffffe000.
[   35.517988] Remapping vsyscall page to ffffe000
[   35.517999] CPU: AMD Athlon(tm) XP 1900+ stepping 02
[   35.518007] Checking 'hlt' instruction... OK.
[   35.534424] Early unpacking initramfs... done
[   35.830510] ACPI: Core revision 20060707
[   35.906745] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   35.908504] ACPI: setting ELCR to 0200 (from 1e20)
[   36.261153] Booting paravirtualized kernel on bare hardware
[   36.261254] Time: 15:13:57  Date: 04/05/107
[   36.261296] NET: Registered protocol family 16
[   36.261417] EISA bus registered
[   36.261423] ACPI: bus type pci registered
[   36.264922] spurious 8259A interrupt: IRQ7.
[   36.337551] PCI: PCI BIOS revision 2.10 entry at 0xfb4d0, last bus=1
[   36.337555] PCI: Using configuration type 1
[   36.337557] Setting up standard PCI resources
[   36.394994] ACPI: Interpreter enabled
[   36.395001] ACPI: Using PIC for interrupt routing
[   36.395682] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   36.395688] PCI: Probing PCI hardware (bus 00)
[   36.395793] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   36.396587] Boot video device is 0000:01:00.0
[   36.396635] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   36.418922] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   36.419282] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[   36.419647] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   36.420009] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[   36.420386] ACPI: PCI Interrupt Link [ALKA] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   36.420765] ACPI: PCI Interrupt Link [ALKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   36.421151] ACPI: PCI Interrupt Link [ALKC] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   36.421523] ACPI: PCI Interrupt Link [ALKD] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   36.424057] Linux Plug and Play Support v0.97 (c) Adam Belay
[   36.424072] pnp: PnP ACPI init
[   36.427672] pnp: PnP ACPI: found 12 devices
[   36.427679] PnPBIOS: Disabled by ACPI PNP
[   36.427757] PCI: Using ACPI for IRQ routing
[   36.427763] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   36.452376] NET: Registered protocol family 8
[   36.452379] NET: Registered protocol family 20
[   36.453104] PCI: Bridge: 0000:00:01.0
[   36.453107]   IO window: disabled.
[   36.453113]   MEM window: e0000000-e1ffffff
[   36.453117]   PREFETCH window: d8000000-dfffffff
[   36.453138] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   36.453171] NET: Registered protocol family 2
[   36.484712] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   36.485010] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[   36.486121] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   36.486609] TCP: Hash tables configured (established 131072 bind 65536)
[   36.486613] TCP reno registered
[   36.496819] checking if image is initramfs... it is
[   37.061650] Freeing initrd memory: 5314k freed
[   37.062213] audit: initializing netlink socket (disabled)
[   37.062233] audit(1178378037.500:1): initialized
[   37.062310] highmem bounce pool size: 64 pages
[   37.062390] VFS: Disk quotas dquot_6.5.1
[   37.062418] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   37.062494] io scheduler noop registered
[   37.062497] io scheduler anticipatory registered
[   37.062500] io scheduler deadline registered
[   37.062508] io scheduler cfq registered (default)
[   37.062838] isapnp: Scanning for PnP cards...
[   37.416103] isapnp: No Plug & Play device found
[   37.456112] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   37.456240] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.456496] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   37.457406] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.457851] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   37.458213] mice: PS/2 mouse device common for all mice
[   37.458842] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   37.459158] input: Macintosh mouse button emulation as /class/input/input0
[   37.459199] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   37.459205] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   37.459462] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   37.459466] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   37.711398] serio: i8042 KBD port at 0x60,0x64 irq 1
[   37.711624] EISA: Probing bus 0 at eisa.0
[   37.711645] Cannot allocate resource for EISA slot 4
[   37.711662] EISA: Detected 0 cards.
[   37.741744] TCP cubic registered
[   37.741752] NET: Registered protocol family 1
[   37.741821] Testing NMI watchdog ... OK.
[   37.781496] Using IPI Shortcut mode
[   37.781559] ACPI: (supports S0 S1 S4 S5)
[   37.781618]   Magic number: 7:127:234
[   37.781682]   hash matches device ttyv4
[   37.782345] Freeing unused kernel memory: 328k freed
[   37.783240] Time: tsc clocksource has been installed.
[   37.810264] input: AT Translated Set 2 keyboard as /class/input/input1
[   38.878876] Capability LSM initialized
[   38.918184] ACPI: Fan [FAN] (on)
[   38.922693] ACPI: Processor [CPU0] (supports 2 throttling states)
[   38.924493] ACPI: Thermal Zone [THRM] (50 C)
[   39.437121] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   39.437755] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   39.437760] PCI: setting IRQ 11 as level-triggered
[   39.437766] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   39.437774] PCI: VIA VLink IRQ fixup for 0000:00:11.1, from 255 to 11
[   39.437802] VP_IDE: chipset revision 6
[   39.437805] VP_IDE: not 100% native mode: will probe irqs later
[   39.437817] VP_IDE: VIA vt8233 (rev 00) IDE UDMA100 controller on pci0000:00:11.1
[   39.437828]     ide0: BM-DMA at 0xc400-0xc407, BIOS settings: hda:DMA, hdb:pio
[   39.437845]     ide1: BM-DMA at 0xc408-0xc40f, BIOS settings: hdc:DMA, hdd:DMA
[   39.437856] Probing IDE interface ide0...
[   40.300610] hda: LITE-ON DVD+RW LDW-401S, ATAPI CD/DVD-ROM drive
[   40.972346] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   40.972960] Probing IDE interface ide1...
[   41.387435] hdc: ST380021A, ATA DISK drive
[   41.667132] hdd: Maxtor 94098U8, ATA DISK drive
[   41.723676] ide1 at 0x170-0x177,0x376 on irq 15
[   41.765818] hda: ATAPI 40X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   41.765832] Uniform CD-ROM driver Revision: 3.20
[   41.780781] hdc: max request size: 128KiB
[   41.781083] hdc: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   41.781091] hdc: cache flushes not supported
[   41.781148]  hdc: hdc1
[   41.795553] hdd: max request size: 128KiB
[   41.795797] hdd: 80041248 sectors (40981 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(66)
[   41.795804] hdd: cache flushes not supported
[   41.795839]  hdd: hdd1 hdd2
[   42.099016] HPT372: IDE controller at PCI slot 0000:00:13.0
[   42.099557] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   42.099562] PCI: setting IRQ 10 as level-triggered
[   42.099567] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   42.099582] HPT372: chipset revision 5
[   42.099594] HPT372: 100% native mode on irq 10
[   42.099604] HPT37X: using 33MHz PCI clock
[   42.099716]     ide2: BM-DMA at 0xe400-0xe407, BIOS settings: hde:DMA, hdf:pio
[   42.099739]     ide3: BM-DMA at 0xe408-0xe40f, BIOS settings: hdg:DMA, hdh:pio
[   42.099758] Probing IDE interface ide2...
[   42.386448] hde: WDC WD1600JB-32EVA0, ATA DISK drive
[   43.058621] ide2 at 0xd400-0xd407,0xd802 on irq 10
[   43.058900] hde: max request size: 512KiB
[   43.071326] hde: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[   43.072997] hde: cache flushes supported
[   43.073040]  hde:
[   43.082724] Probing IDE interface ide3...
[   43.369377] hdg: Maxtor 6L200P0, ATA DISK drive
[   44.042034] ide3 at 0xdc00-0xdc07,0xe002 on irq 10
[   44.042185] hdg: max request size: 512KiB
[   44.063109] hdg: 398297088 sectors (203928 MB) w/8192KiB Cache, CHS=24792/255/63, UDMA(100)
[   44.064664] hdg: cache flushes supported
[   44.064702]  hdg: hdg1
[   44.255258] usbcore: registered new interface driver usbfs
[   44.255293] usbcore: registered new interface driver hub
[   44.255323] usbcore: registered new device driver usb
[   44.256276] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   44.256868] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 12
[   44.256873] PCI: setting IRQ 12 as level-triggered
[   44.256879] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[   44.256896] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   44.257109] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   44.257131] ohci_hcd 0000:00:0b.0: irq 12, io mem 0xe3100000
[   44.289766] USB Universal Host Controller Interface driver v3.0
[   44.351644] usb usb1: configuration #1 chosen from 1 choice
[   44.351865] hub 1-0:1.0: USB hub found
[   44.351884] hub 1-0:1.0: 3 ports detected
[   44.452745] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   44.452771] ohci_hcd 0000:00:0b.1: OHCI Host Controller
[   44.452899] ohci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   44.452923] ohci_hcd 0000:00:0b.1: irq 11, io mem 0xe3101000
[   44.538332] usb usb2: configuration #1 chosen from 1 choice
[   44.538571] hub 2-0:1.0: USB hub found
[   44.538589] hub 2-0:1.0: 2 ports detected
[   44.640835] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   44.640843] PCI: setting IRQ 5 as level-triggered
[   44.640848] ACPI: PCI Interrupt 0000:00:0b.2[C] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   44.640871] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[   44.640905] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 3
[   44.663831] ehci_hcd 0000:00:0b.2: irq 5, io mem 0xe3102000
[   44.663843] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   44.663980] usb usb3: configuration #1 chosen from 1 choice
[   44.664022] hub 3-0:1.0: USB hub found
[   44.664036] hub 3-0:1.0: 5 ports detected
[   44.767983] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[   44.768003] uhci_hcd 0000:00:11.2: UHCI Host Controller
[   44.768040] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 4
[   44.768068] uhci_hcd 0000:00:11.2: irq 12, io base 0x0000c800
[   44.768195] usb usb4: configuration #1 chosen from 1 choice
[   44.768235] hub 4-0:1.0: USB hub found
[   44.768248] hub 4-0:1.0: 2 ports detected
[   44.871770] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[   44.871790] uhci_hcd 0000:00:11.3: UHCI Host Controller
[   44.871820] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 5
[   44.871848] uhci_hcd 0000:00:11.3: irq 12, io base 0x0000cc00
[   44.871975] usb usb5: configuration #1 chosen from 1 choice
[   44.872014] hub 5-0:1.0: USB hub found
[   44.872026] hub 5-0:1.0: 2 ports detected
[   44.975624] ACPI: PCI Interrupt 0000:00:11.4[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[   44.975645] uhci_hcd 0000:00:11.4: UHCI Host Controller
[   44.975674] uhci_hcd 0000:00:11.4: new USB bus registered, assigned bus number 6
[   44.975703] uhci_hcd 0000:00:11.4: irq 12, io base 0x0000d000
[   44.975830] usb usb6: configuration #1 chosen from 1 choice
[   44.975870] hub 6-0:1.0: USB hub found
[   44.975883] hub 6-0:1.0: 2 ports detected
[   45.162914] Attempting manual resume
[   45.162921] swsusp: Resume From Partition 22:65
[   45.162924] PM: Checking swsusp image.
[   45.163192] PM: Resume from disk failed.
[   45.181236] EXT3-fs: INFO: recovery required on readonly filesystem.
[   45.181242] EXT3-fs: write access will be enabled during recovery.
[   45.239172] usb 4-2: new low speed USB device using uhci_hcd and address 2
[   45.421985] usb 4-2: configuration #1 chosen from 1 choice
[   45.934440] usbcore: registered new interface driver hiddev
[   45.949788] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[   45.949817] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:11.2-2
[   45.949838] usbcore: registered new interface driver usbhid
[   45.949843] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   59.483071] kjournald starting.  Commit interval 5 seconds
[   59.483103] EXT3-fs: hdd2: orphan cleanup on readonly fs
[   59.513570] ext3_orphan_cleanup: deleting unreferenced inode 229726
[   59.520708] EXT3-fs: hdd2: 1 orphan inode deleted
[   59.520710] EXT3-fs: recovery complete.
[   59.567123] EXT3-fs: mounted filesystem with ordered data mode.
[   77.770220] Linux agpgart interface v0.102 (c) Dave Jones
[   77.818070] irda_init()
[   77.818107] NET: Registered protocol family 23
[   77.889658] r8169 Gigabit Ethernet driver 2.2LK loaded
[   77.889692] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   77.889875] eth0: RTL8169s/8110s at 0xf887e000, 00:e0:4c:77:2e:7f, IRQ 10
[   77.925391] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[   77.934910] agpgart: AGP aperture is 128M @ 0xd0000000
[   78.183827] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   78.201183] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   78.542944] Real Time Clock Driver v1.12ac
[   78.570857] FDC 0 is a post-1991 82077
[   79.137201] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   79.165380] input: PC Speaker as /class/input/input3
[   79.182248] parport: PnPBIOS parport detected.
[   79.182301] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   79.213860] parport0: Printer, Brother HL-1230 series
[   79.251530] nvidia: module license 'NVIDIA' taints kernel.
[   80.055797] SCSI subsystem initialized
[   80.130169] libata version 2.20 loaded.
[   82.053300] gameport: CS46xx Gameport is pci0000:00:10.0/gameport0, speed 1569kHz
[   82.054982] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   82.055632] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[   82.741838] r8169: eth0: link up
[   83.453227] lp0: using parport0 (interrupt-driven).
[   83.497298] Adding 1228932k swap on /dev/disk/by-uuid/ad87fe69-f1bc-40f8-bd37-4e1df0e6d43c.  Priority:-1 extents:1 across:1228932k
[   83.591371] EXT3 FS on hdd2, internal journal
[   83.799522] NET: Registered protocol family 17
[   83.924598] kjournald starting.  Commit interval 5 seconds
[   83.924797] EXT3 FS on hdc1, internal journal
[   83.924803] EXT3-fs: mounted filesystem with ordered data mode.
[   83.979067] kjournald starting.  Commit interval 5 seconds
[   83.979286] EXT3 FS on hdg1, internal journal
[   83.979293] EXT3-fs: mounted filesystem with ordered data mode.
[   87.516658] NET: Registered protocol family 10
[   87.516794] lo: Disabled Privacy Extensions
[   91.533845] input: Power Button (FF) as /class/input/input4
[   91.566185] ACPI: Power Button (FF) [PWRF]
[   91.637001] input: Power Button (CM) as /class/input/input5
[   91.637319] ACPI: Power Button (CM) [PWRB]
[   91.680966] input: Sleep Button (CM) as /class/input/input6
[   91.681290] ACPI: Sleep Button (CM) [SLPB]
[   91.806254] Using specific hotkey driver
[   91.847340] No dock devices found.
[   91.906260] ibm_acpi: ec object not found
[   98.337685] eth0: no IPv6 routers present
[   98.413398] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   98.413423] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   98.413478] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  100.104794] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  100.104803] apm: overridden by ACPI.
[  110.286436] Bluetooth: Core ver 2.11
[  110.286526] NET: Registered protocol family 31
[  110.286529] Bluetooth: HCI device and connection manager initialized
[  110.286534] Bluetooth: HCI socket layer initialized
[  110.413940] Bluetooth: L2CAP ver 2.8
[  110.413948] Bluetooth: L2CAP socket layer initialized
[  110.905624] Bluetooth: RFCOMM socket layer initialized
[  110.905649] Bluetooth: RFCOMM TTY layer initialized
[  110.905651] Bluetooth: RFCOMM ver 1.8
[  144.573910] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  144.573938] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  144.573994] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

```
 

I get no such file on the cat /var/log/xorg.log

I created a separate thread for the python issue, but here's what I posted:

```
I've found several threads on people with the Python2.5 issues. I've tried all the solutions I've found, but none work for me.

I initially had 4 broken packages I had to fix manually. No big deal, but the Python2.5 is not allowing me to upgrade other packages. I get errors about having the 2.4 installed, even though I've had 2.5 for some time. I tried to reinstall manually but get the following:

Preparing to replace python2.5-minimal 2.5.1~rc1-0ubuntu3 (using python2.5-minimal_2.5.1~rc1-0ubuntu3_i386.deb) ...
Unpacking replacement python2.5-minimal ...
Setting up python2.5-minimal (2.5.1~rc1-0ubuntu3) ...
Linking and byte-compiling packages for runtime python2.5...
usage: pycentral [<options> ...] rtinstall <options>

pycentral: error: no such option: --ignore-errors
dpkg: error processing python2.5-minimal (--install):
subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
python2.5-minimal


I tried commenting out lines 540 & 541 in the python file as suggested on another thread, but no luck. Any ideas on what to do next? Aptitude won't work either.
```

---

### Post by taddy_porter on 2007-05-05
And here's my xorg.conf:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by taddy_porter on 2007-05-05
And my Xorg.0.log

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux taddy1 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May  5 12:17:13 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/X11/fonts/misc").
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(WW) FontPath is completely invalid.  Using compiled-in default.
(==) FontPath set to:
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3099 card 0000,0824 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b099 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10ec,8169 card 10ec,8169 rev 10 class 02,00,00 hdr 00
(II) PCI: 00:0b:0: chip 1033,0035 card 3083,0035 rev 43 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 1033,0035 card 3083,0035 rev 43 class 0c,03,10 hdr 00
(II) PCI: 00:0b:2: chip 1033,00e0 card 3083,00e0 rev 04 class 0c,03,20 hdr 00
(II) PCI: 00:10:0: chip 1013,6003 card 5053,3357 rev 01 class 04,01,00 hdr 00
(II) PCI: 00:11:0: chip 1106,3074 card 1106,3074 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:2: chip 1106,3038 card 0925,1234 rev 1b class 0c,03,00 hdr 00
(II) PCI: 00:11:3: chip 1106,3038 card 0925,1234 rev 1b class 0c,03,00 hdr 00
(II) PCI: 00:11:4: chip 1106,3038 card 0925,1234 rev 1b class 0c,03,00 hdr 00
(II) PCI: 00:13:0: chip 1103,0004 card 1103,0001 rev 05 class 01,04,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0332 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV35 [GeForce FX 5900XT] rev 161, Mem @ 0xe0000000/24, 0xd8000000/27
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[1] -1	0	0xe3103000 - 0xe3103fff (0x1000) MX[B]
	[2] -1	0	0xe3102000 - 0xe31020ff (0x100) MX[B]
	[3] -1	0	0xe3101000 - 0xe3101fff (0x1000) MX[B]
	[4] -1	0	0xe3100000 - 0xe3100fff (0x1000) MX[B]
	[5] -1	0	0xe3104000 - 0xe31040ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[10] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[12] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[15] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[1] -1	0	0xe3103000 - 0xe3103fff (0x1000) MX[B]
	[2] -1	0	0xe3102000 - 0xe31020ff (0x100) MX[B]
	[3] -1	0	0xe3101000 - 0xe3101fff (0x1000) MX[B]
	[4] -1	0	0xe3100000 - 0xe3100fff (0x1000) MX[B]
	[5] -1	0	0xe3104000 - 0xe31040ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[10] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[12] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[15] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[5] -1	0	0xe3103000 - 0xe3103fff (0x1000) MX[B]
	[6] -1	0	0xe3102000 - 0xe31020ff (0x100) MX[B]
	[7] -1	0	0xe3101000 - 0xe3101fff (0x1000) MX[B]
	[8] -1	0	0xe3100000 - 0xe3100fff (0x1000) MX[B]
	[9] -1	0	0xe3104000 - 0xe31040ff (0x100) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[5] -1	0	0xe3103000 - 0xe3103fff (0x1000) MX[B]
	[6] -1	0	0xe3102000 - 0xe31020ff (0x100) MX[B]
	[7] -1	0	0xe3101000 - 0xe3101fff (0x1000) MX[B]
	[8] -1	0	0xe3100000 - 0xe3100fff (0x1000) MX[B]
	[9] -1	0	0xe3104000 - 0xe31040ff (0x100) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[5] -1	0	0xe3103000 - 0xe3103fff (0x1000) MX[B]
	[6] -1	0	0xe3102000 - 0xe31020ff (0x100) MX[B]
	[7] -1	0	0xe3101000 - 0xe3101fff (0x1000) MX[B]
	[8] -1	0	0xe3100000 - 0xe3100fff (0x1000) MX[B]
	[9] -1	0	0xe3104000 - 0xe31040ff (0x100) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[24] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5900XT at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.35.20.38.52
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5900XT at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     STAC Electronics KDS VS-190is (CRT-0)
(--) NVIDIA(0): STAC Electronics KDS VS-190is (CRT-0): 400.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[1] 0	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe3000000 - 0xe30fffff (0x100000) MX[B]
	[7] -1	0	0xe3103000 - 0xe3103fff (0x1000) MX[B]
	[8] -1	0	0xe3102000 - 0xe31020ff (0x100) MX[B]
	[9] -1	0	0xe3101000 - 0xe3101fff (0x1000) MX[B]
	[10] -1	0	0xe3100000 - 0xe3100fff (0x1000) MX[B]
	[11] -1	0	0xe3104000 - 0xe31040ff (0x100) MX[B]
	[12] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[13] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[26] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[28] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[29] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "UseFBDev" is not used
(==) RandR enabled
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
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.

```

---

### Post by taddy_porter on 2007-05-05
This is ridiculous. I re-installed from scratch (my home is on a separate partition) and I still get the same thing. Happened after installing kde.

---

### Post by quixotic-cynic on 2007-09-30
Late, but this might help: [http://ubuntuforums.org/showthread.php?p=1264361#post1264361](http://ubuntuforums.org/showthread.php?p=1264361#post1264361)

---

