---
title: "keep losing usb mouse"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by in2media on 2007-08-05
i keep losing my usb mouse in ubuntu 7.04
it seems to be when i reboot my laptop
any ideas

---

### Post by Golyadkin on 2007-08-05
Hmm, I have the same thing but not just with Ubuntu, also with Windows XP. Sometimes after rebooting, the BIOS doesn't find the USB mouse. If I pull it out and plug it back in, it is fine again. Maybe our USB ports are slowly dying :) or the mouse needs to be replaced.

---

### Post by tprzepiorka on 2007-08-05
I used to have the same problem on Ubuntu with an older computer of mine. 

To fix it instead of plugging the mouse into the PS/2 port I plugged it straight into USB and it worked perfectly. 

I'm not sure if you are using a USB-to-PS/2 adapter of plugging it straight into a USB port. I would suggest plugging straight into the USB port.

---

### Post by in2media on 2007-08-05
no im using a usb mouse plugged directly into usb port, its also always plugged in i never take it out??

---

### Post by fimbulvetr on 2007-08-05
The only time you can use it is when you unplug and plug it back in? Then it works?

If so, do a reboot, confirm it doesn't work when coming back up. Unplug and plug and paste the output of going to Terminal (Under Applications->Accessories->Terminal) and run:

```

dmesg

```

There should be a lot of stuff put out on the screen, copy and paste it all into a response.

---

### Post by in2media on 2007-08-05
no if the mouse is plugged in on reboot it dont work. if i move the mouse as it boots up the mouse will work, so its not so bad

---

### Post by fimbulvetr on 2007-08-05
> **in2media said:**
> no if the mouse is plugged in on reboot it dont work. if i move the mouse as it boots up the mouse will work, so its not so bad

Ok, can you still paste the dmesg I requested above though? Maybe we can post a bug report and get it fixed.

---

### Post by in2media on 2007-08-05
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128723
[    0.000000]   HighMem    128723 ->   128723
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128723
[    0.000000] On node 0 totalpages: 128723
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123654 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc1f0
[    0.000000] ACPI: RSDT (v001 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x1f6d3d56
[    0.000000] ACPI: FADT (v001 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x1f6d4800
[    0.000000] ACPI: HPET (v001 DELL    M07     0x00000001 ASL  0x00000061) @ 0x1f6d4f00
[    0.000000] ACPI: MADT (v001 DELL    M07     0x27d70402 ASL  0x00000047) @ 0x1f6d5000
[    0.000000] ACPI: MCFG (v016 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x1f6d4fc0
[    0.000000] ACPI: SLIC (v001 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x1f6d509c
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050624) @ 0x1f6d4272
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x1f6d3d96
[    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 INTL 0x20050624) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
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
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:d0000000)
[    0.000000] Detected 1729.500 MHz processor.
[    8.283291] Built 1 zonelists.  Total pages: 127718
[    8.283297] Kernel command line: root=UUID=c91e275d-3220-43cc-8fbe-cc241f67f593 ro quiet splash
[    8.283456] mapped APIC to ffffd000 (fee00000)
[    8.283458] mapped IOAPIC to ffffc000 (fec00000)
[    8.283461] Enabling fast FPU save and restore... done.
[    8.283464] Enabling unmasked SIMD FPU exception support... done.
[    8.283471] Initializing CPU#0
[    8.283539] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    8.285457] Console: colour VGA+ 80x25
[    8.285624] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.285824] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.296828] Memory: 499512k/514892k available (1992k kernel code, 14924k reserved, 900k data, 328k init, 0k highmem)
[    8.296837] virtual kernel memory layout:
[    8.296839]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    8.296840]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.296841]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[    8.296842]     lowmem  : 0xc0000000 - 0xdf6d3000   ( 502 MB)
[    8.296844]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    8.296845]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    8.296846]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    8.296850] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.297006] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    8.297013] hpet0: 3 64-bit timers, 14318180 Hz
[    8.298019] Using HPET for base-timer
[    8.376997] Calibrating delay using timer specific routine.. 3462.63 BogoMIPS (lpj=6925275)
[    8.377040] Security Framework v1.0.0 initialized
[    8.377048] SELinux:  Disabled at boot.
[    8.377063] Mount-cache hash table entries: 512
[    8.377198] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[    8.377206] monitor/mwait feature present.
[    8.377208] using mwait in idle threads.
[    8.377214] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.377217] CPU: L2 cache: 1024K
[    8.377220] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000
[    8.377229] Compat vDSO mapped to ffffe000.
[    8.377232] Remapping vsyscall page to ffffe000
[    8.377245] Checking 'hlt' instruction... OK.
[    8.393096] SMP alternatives: switching to UP code
[    8.393284] Freeing SMP alternatives: 11k freed
[    8.393467] Early unpacking initramfs... done
[    8.722275] ACPI: Core revision 20060707
[    8.738350] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    8.741299] CPU0: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz stepping 08
[    8.741324] Total of 1 processors activated (3462.63 BogoMIPS).
[    8.741524] ENABLING IO-APIC IRQs
[    8.741726] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    8.888950] Brought up 1 CPUs
[    8.889182] Booting paravirtualized kernel on bare hardware
[    8.889265] Time: 15:54:45  Date: 07/05/107
[    8.889291] NET: Registered protocol family 16
[    8.889371] EISA bus registered
[    8.889375] ACPI: bus type pci registered
[    8.918198] PCI: PCI BIOS revision 2.10 entry at 0xfadf6, last bus=12
[    8.918201] PCI: Using configuration type 1
[    8.918203] Setting up standard PCI resources
[    8.945268] ACPI: Interpreter enabled
[    8.945271] ACPI: Using IOAPIC for interrupt routing
[    8.946836] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.946845] PCI: Probing PCI hardware (bus 00)
[    8.946984] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    8.960804] Boot video device is 0000:00:02.0
[    8.961435] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    8.961439] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    8.962306] PCI: Transparent bridge - 0000:00:1e.0
[    8.962374] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
[    8.962376] Please report the result to linux-kernel to fix this permanently
[    8.962428] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.001294] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    9.001559] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    9.001808] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *0, disabled.
[    9.002069] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    9.002331] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    9.002594] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    9.002857] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    9.003121] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    9.004836] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    9.005764] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.006000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.006546] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.006556] pnp: PnP ACPI init
[    9.053277] pnp: PnP ACPI: found 13 devices
[    9.053282] PnPBIOS: Disabled by ACPI PNP
[    9.053333] PCI: Using ACPI for IRQ routing
[    9.053336] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.092146] NET: Registered protocol family 8
[    9.092148] NET: Registered protocol family 20
[    9.111342] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    9.111345] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
[    9.111348] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
[    9.111353] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    9.111356] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[    9.111359] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[    9.111362] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[    9.111365] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[    9.111370] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[    9.111378] pnp: 00:08: ioport range 0xc80-0xcff could not be reserved
[    9.111381] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[    9.111383] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[    9.111386] pnp: 00:08: ioport range 0xcb0-0xcbf has been reserved
[    9.111389] pnp: 00:08: ioport range 0x930-0x97f has been reserved
[    9.111642] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    9.111649] PCI: Bridge: 0000:00:1c.0
[    9.111650]   IO window: disabled.
[    9.111656]   MEM window: disabled.
[    9.111660]   PREFETCH window: disabled.
[    9.111666] PCI: Bridge: 0000:00:1c.1
[    9.111668]   IO window: disabled.
[    9.111674]   MEM window: efd00000-efdfffff
[    9.111678]   PREFETCH window: disabled.
[    9.111690] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[    9.111692]   IO window: 00002000-000020ff
[    9.111697]   IO window: 00002400-000024ff
[    9.111703]   PREFETCH window: 30000000-33ffffff
[    9.111708]   MEM window: 34000000-37ffffff
[    9.111713] PCI: Bridge: 0000:00:1e.0
[    9.111717]   IO window: 2000-2fff
[    9.111723]   MEM window: efc00000-efcfffff
[    9.111728]   PREFETCH window: 30000000-33ffffff
[    9.111761] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.111768] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.111792] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    9.111798] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.111813] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.111830] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[    9.111835] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 19 (level, low) -> IRQ 18
[    9.111862] NET: Registered protocol family 2
[    9.144932] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    9.145004] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    9.145106] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    9.145158] TCP: Hash tables configured (established 16384 bind 8192)
[    9.145161] TCP reno registered
[    9.156974] checking if image is initramfs... it is
[    9.798887] Freeing initrd memory: 6788k freed
[    9.800443] audit: initializing netlink socket (disabled)
[    9.800457] audit(1186329285.584:1): initialized
[    9.800571] VFS: Disk quotas dquot_6.5.1
[    9.800591] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.800639] io scheduler noop registered
[    9.800641] io scheduler anticipatory registered
[    9.800643] io scheduler deadline registered
[    9.800651] io scheduler cfq registered (default)
[    9.800925] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.800984] assign_interrupt_mode Found MSI capability
[    9.800987] Allocate Port Service[0000:00:1c.0:pcie00]
[    9.801018] Allocate Port Service[0000:00:1c.0:pcie02]
[    9.801138] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.801197] assign_interrupt_mode Found MSI capability
[    9.801199] Allocate Port Service[0000:00:1c.1:pcie00]
[    9.801229] Allocate Port Service[0000:00:1c.1:pcie02]
[    9.801400] isapnp: Scanning for PnP cards...
[   10.155716] isapnp: No Plug & Play device found
[   10.180768] Real Time Clock Driver v1.12ac
[   10.180828] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.180980] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.181768] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.181964] mice: PS/2 mouse device common for all mice
[   10.182479] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.182711] input: Macintosh mouse button emulation as /class/input/input0
[   10.182742] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   10.182746] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   10.182993] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.187004] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.187010] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.187155] EISA: Probing bus 0 at eisa.0
[   10.187224] EISA: Mainboard N__FFFF detected.
[   10.187255] Cannot allocate resource for EISA slot 1
[   10.187257] Cannot allocate resource for EISA slot 2
[   10.187283] EISA: Detected 0 cards.
[   10.217384] TCP cubic registered
[   10.217391] NET: Registered protocol family 1
[   10.217410] Using IPI No-Shortcut mode
[   10.217483] ACPI: (supports S0 S3 S4 S5)
[   10.217530]   Magic number: 3:867:941
[   10.217633]   hash matches device ptyyc
[   10.217843] Freeing unused kernel memory: 328k freed
[   10.218823] input: AT Translated Set 2 keyboard as /class/input/input1
[   10.220706] Time: tsc clocksource has been installed.
[   11.437771] Capability LSM initialized
[   11.471003] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   11.471009] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.471017] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   11.475196] ACPI: Thermal Zone [THM] (30 C)
[   11.843267] usbcore: registered new interface driver usbfs
[   11.843288] usbcore: registered new interface driver hub
[   11.843309] usbcore: registered new device driver usb
[   11.844129] USB Universal Host Controller Interface driver v3.0
[   11.844184] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[   11.844198] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.844202] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.844360] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.844393] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000bf80
[   11.844510] usb usb1: configuration #1 chosen from 1 choice
[   11.844532] hub 1-0:1.0: USB hub found
[   11.844537] hub 1-0:1.0: 2 ports detected
[   11.948602] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
[   11.948617] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.948621] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.948642] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.948678] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000bf60
[   11.948765] usb usb2: configuration #1 chosen from 1 choice
[   11.948789] hub 2-0:1.0: USB hub found
[   11.948794] hub 2-0:1.0: 2 ports detected
[   11.961604] ieee1394: Initialized config rom entry `ip1394'
[   12.052569] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
[   12.052584] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.052588] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.052608] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   12.052642] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000bf40
[   12.052729] usb usb3: configuration #1 chosen from 1 choice
[   12.052751] hub 3-0:1.0: USB hub found
[   12.052757] hub 3-0:1.0: 2 ports detected
[    3.744000] Time: hpet clocksource has been installed.
[    3.760000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 22
[    3.760000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.760000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.760000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.760000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x0000bf20
[    3.760000] usb usb4: configuration #1 chosen from 1 choice
[    3.760000] hub 4-0:1.0: USB hub found
[    3.760000] hub 4-0:1.0: 2 ports detected
[    3.792000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    3.868000] SCSI subsystem initialized
[    3.872000] b44.c:v1.01 (Jun 16, 2006)
[    3.872000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    3.876000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:19:b9:54:33:92
[    3.880000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[    3.880000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.880000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.880000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.880000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.880000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.880000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80000
[    3.884000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.884000] usb usb5: configuration #1 chosen from 1 choice
[    3.884000] hub 5-0:1.0: USB hub found
[    3.884000] hub 5-0:1.0: 8 ports detected
[    3.884000] libata version 2.20 loaded.
[    3.988000] ACPI: PCI Interrupt 0000:02:01.4[A] -> GSI 19 (level, low) -> IRQ 18
[    4.036000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[efcfd000-efcfd7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.044000] ata_piix 0000:00:1f.2: version 2.10ac1
[    4.044000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.044000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[    4.044000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.044000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    4.044000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    4.044000] scsi0 : ata_piix
[    4.208000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.208000] ata1.00: ATA-7: TOSHIBA MK8034GSX, AH301D, max UDMA/100
[    4.208000] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    4.216000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.216000] ata1.00: configured for UDMA/100
[    4.216000] scsi1 : ata_piix
[    4.324000] usb 1-2: device not accepting address 2, error -71
[    4.560000] ata2.00: ATAPI, max UDMA/33
[    4.748000] ata2.00: configured for UDMA/33
[    4.748000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8034GS AH30 PQ: 0 ANSI: 5
[    4.756000] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632D DE04 PQ: 0 ANSI: 5
[    4.768000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.768000] sda: Write Protect is off
[    4.768000] sda: Mode Sense: 00 3a 00 00
[    4.768000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.768000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.768000] sda: Write Protect is off
[    4.768000] sda: Mode Sense: 00 3a 00 00
[    4.768000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.768000]  sda: sda1 sda2 < sda5 >
[    4.824000] sd 0:0:0:0: Attached scsi disk sda
[    4.828000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.828000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.876000] usb 5-2: new high speed USB device using ehci_hcd and address 2
[    4.928000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.928000] Uniform CD-ROM driver Revision: 3.20
[    4.928000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.008000] usb 5-2: configuration #1 chosen from 1 choice
[    5.008000] hub 5-2:1.0: USB hub found
[    5.008000] hub 5-2:1.0: 4 ports detected
[    5.032000] Attempting manual resume
[    5.032000] swsusp: Resume From Partition 8:5
[    5.032000] PM: Checking swsusp image.
[    5.032000] PM: Resume from disk failed.
[    5.072000] kjournald starting.  Commit interval 5 seconds
[    5.072000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.312000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[484fc00006f9e850]
[    5.720000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    5.896000] usb 2-2: configuration #1 chosen from 1 choice
[    6.156000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    6.364000] usb 3-1: configuration #1 chosen from 1 choice
[   16.328000] NET: Registered protocol family 17
[   16.636000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.640000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.824000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.068000] agpgart: Detected an Intel 945GM Chipset.
[   17.068000] agpgart: Detected 7932K stolen memory.
[   17.084000] agpgart: AGP aperture is 256M @ 0xd0000000
[   17.084000] intel_rng: FWH not detected
[   17.152000] iTCO_vendor_support: vendor-support=0
[   17.160000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   17.160000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   17.160000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.564000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:01d4]
[   17.564000] Yenta O2: res at 0x94/0xD4: 00/ea
[   17.564000] Yenta O2: enabling read prefetch/write burst
[   17.692000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 18
[   17.692000] Socket status: 30000006
[   17.692000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   17.692000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   17.692000] cs: IO port probe 0x2000-0x2fff: clean.
[   17.692000] pcmcia: parent PCI bridge Memory window: 0xefc00000 - 0xefcfffff
[   17.692000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   17.736000] input: PC Speaker as /class/input/input2
[   17.736000] ieee80211_crypt: registered algorithm 'NULL'
[   17.740000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.740000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.824000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   17.824000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   17.824000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   17.824000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   17.836000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   17.868000] usbcore: registered new interface driver libusual
[   18.016000] usbcore: registered new interface driver hiddev
[   18.024000] Initializing USB Mass Storage driver...
[   18.048000] input: PS/2 Mouse as /class/input/input3
[   18.068000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   18.156000] usb 2-2: USB disconnect, address 2
[   18.156000] usbhid: probe of 2-2:1.0 failed with error -32
[   18.268000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[   18.268000] cs: IO port probe 0x100-0x3af: clean.
[   18.268000] cs: IO port probe 0x3e0-0x4ff: clean.
[   18.268000] cs: IO port probe 0x820-0x8ff:<6>ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   18.272000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   18.272000]  clean.
[   18.272000] cs: IO port probe 0xc00-0xcf7: excluding 0xc90-0xc97
[   18.272000] cs: IO port probe 0xa00-0xaff: clean.
[   18.444000] usb 2-2: configuration #1 chosen from 1 choice
[   18.464000] scsi2 : SCSI emulation for USB Mass Storage devices
[   18.464000] usbcore: registered new interface driver usb-storage
[   18.464000] USB Mass Storage support registered.
[   18.464000] usb-storage: device found at 2
[   18.464000] usb-storage: waiting for device to settle before scanning
[   18.476000] input: USB Optical Mouse USB Optical Mouse as /class/input/input5
[   18.476000] input: USB HID v1.10 Mouse [USB Optical Mouse USB Optical Mouse] on usb-0000:00:1d.1-2
[   18.476000] usbcore: registered new interface driver usbhid
[   18.476000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   18.768000] fuse init (API version 7.8)
[   18.964000] lp: driver loaded but no devices found
[   19.008000] Adding 1477940k swap on /dev/disk/by-uuid/e1d8d879-90fa-4d96-b18e-9c88a5ade32b.  Priority:-1 extents:1 across:1477940k
[   19.144000] EXT3 FS on sda1, internal journal
[   19.852000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   23.464000] usb-storage: device scan complete
[   23.480000] scsi 2:0:0:0: Direct-Access     Y-E DATA USB-FDU          7.03 PQ: 0 ANSI: 0 CCS
[   23.560000] sd 2:0:0:0: Attached scsi removable disk sdb
[   23.560000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   60.080000] NET: Registered protocol family 10
[   60.084000] lo: Disabled Privacy Extensions
[   60.084000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   72.048000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   88.708000] Using specific hotkey driver
[   88.736000] ACPI: AC Adapter [AC] (off-line)
[   88.852000] ACPI: Battery Slot [BAT0] (battery present)
[   88.852000] ACPI: Battery Slot [BAT1] (battery absent)
[   88.880000] ACPI: ACPI Dock Station Driver 
[   88.928000] input: Lid Switch as /class/input/input6
[   88.932000] ACPI: Lid Switch [LID]
[   88.968000] input: Power Button (CM) as /class/input/input7
[   88.972000] ACPI: Power Button (CM) [PBTN]
[   89.004000] input: Sleep Button (CM) as /class/input/input8
[   89.008000] ACPI: Sleep Button (CM) [SBTN]
[   89.020000] ibm_acpi: ec object not found
[   89.052000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   89.052000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   89.108000] pcc_acpi: loading...
[   93.892000] [drm] Initialized drm 1.1.0 20060810
[   93.896000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   93.896000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   94.624000] ppdev: user-space parallel port driver
[   95.280000] apm: BIOS not found.
[   95.468000] Bluetooth: Core ver 2.11
[   95.468000] NET: Registered protocol family 31
[   95.468000] Bluetooth: HCI device and connection manager initialized
[   95.468000] Bluetooth: HCI socket layer initialized
[   95.508000] Bluetooth: L2CAP ver 2.8
[   95.508000] Bluetooth: L2CAP socket layer initialized
[   95.644000] Bluetooth: RFCOMM socket layer initialized
[   95.644000] Bluetooth: RFCOMM TTY layer initialized
[   95.644000] Bluetooth: RFCOMM ver 1.8
[  151.792000] ieee80211_crypt: registered algorithm 'WEP'
[  151.868000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  170.348000] eth1: no IPv6 routers present
john@john-laptop:~$ 

just rebooted and all works ??

---

### Post by fimbulvetr on 2007-08-05
Hah, that's pretty lame (your mouse):

```

[ 18.476000] input: USB Optical Mouse USB Optical Mouse as /class/input/input5
[ 18.476000] input: USB HID v1.10 Mouse [USB Optical Mouse USB Optical Mouse] on usb-0000:00:1d.1-2

```

It's just recognized as "Usb optical mouse"! 

Can you paste the model/brand information?  (Look at the sticks on your mouse or the box it came in)

and the output from Applications->Accessories->Terminal:

```

lsusb

```

---

### Post by in2media on 2007-08-05
john@john-laptop:~$ lsusb
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 057b:0000 Y-E Data, Inc. FlashBuster-U Floppy
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
john@john-laptop:~$ 

on sticks on mouse just says optical 3d mouse
i cant remember what said on box?

---

