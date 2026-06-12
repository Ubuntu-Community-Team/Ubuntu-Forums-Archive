---
title: "internet not wrkin on feisty!! :("
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by raghuramos1987 on 2007-09-23
guys..i installed feisty on my comp which has xp also...wen i'm on xp net wrks...but the same doesn on feisty..i tried some of the things posted on other threads...here are the results...please help!!! :(

srinivasan@srinivasan-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
srinivasan@srinivasan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:66:24:C0:01  
          inet6 addr: fe80::219:66ff:fe24:c001/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11042 (10.7 KiB)  TX bytes:14782 (14.4 KiB)
          Interrupt:19 Base address:0x8c00 

eth0:avah Link encap:Ethernet  HWaddr 00:19:66:24:C0:01  
          inet addr:169.254.4.87  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:488 (488.0 b)  TX bytes:488 (488.0 b)

srinivasan@srinivasan-desktop:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001f640000 end: 000000001f740000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001f740000 size: 0000000000010000 end: 000000001f750000 type: 3
[    0.000000] copy_e820_map() start: 000000001f750000 size: 00000000000b0000 end: 000000001f800000 type: 4
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff380000 size: 0000000000c80000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f740000 (usable)
[    0.000000]  BIOS-e820: 000000001f740000 - 000000001f750000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f750000 - 000000001f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 128832) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128832
[    0.000000]   HighMem    128832 ->   128832
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128832
[    0.000000] On node 0 totalpages: 128832
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 974 pages used for memmap
[    0.000000]   Normal zone: 123762 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fa3e0
[    0.000000] ACPI: RSDT (v001 A_M_I  OEMRSDT  0x03000720 MSFT 0x00000097) @ 0x1f740000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x12000601 MSFT 0x00000097) @ 0x1f740200
[    0.000000] ACPI: MADT (v001 A_M_I  OEMAPIC  0x03000720 MSFT 0x00000097) @ 0x1f740300
[    0.000000] ACPI: OEMB (v001 A_M_I  OEMBIOS  0x03000720 MSFT 0x00000097) @ 0x1f750040
[    0.000000] ACPI: DSDT (v001  75i6G 75i6G292 0x00000292 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:df500000)
[    0.000000] Detected 2999.990 MHz processor.
[   17.984745] Built 1 zonelists.  Total pages: 127826
[   17.984750] Kernel command line: root=UUID=d5f08b5d-fecd-47d4-bd9c-6e4cb62bf450 ro quiet splash
[   17.984914] mapped APIC to ffffd000 (fee00000)
[   17.984917] mapped IOAPIC to ffffc000 (fec00000)
[   17.984920] Enabling fast FPU save and restore... done.
[   17.984923] Enabling unmasked SIMD FPU exception support... done.
[   17.984936] Initializing CPU#0
[   17.985015] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   17.986424] Console: colour VGA+ 80x25
[   17.986747] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.986992] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.995782] Memory: 499520k/515328k available (1992k kernel code, 15160k reserved, 893k data, 328k init, 0k highmem)
[   17.995793] virtual kernel memory layout:
[   17.995795]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   17.995796]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.995797]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   17.995798]     lowmem  : 0xc0000000 - 0xdf740000   ( 503 MB)
[   17.995799]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   17.995800]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   17.995801]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   17.995804] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.072929] Calibrating delay using timer specific routine.. 6003.94 BogoMIPS (lpj=12007891)
[   18.072972] Security Framework v1.0.0 initialized
[   18.072978] SELinux:  Disabled at boot.
[   18.072995] Mount-cache hash table entries: 512
[   18.073135] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e59d 00000000 00000001
[   18.073144] monitor/mwait feature present.
[   18.073145] using mwait in idle threads.
[   18.073152] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   18.073155] CPU: L2 cache: 2048K
[   18.073158] CPU: Physical Processor ID: 0
[   18.073160] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003180 0000e59d 00000000 00000001
[   18.073171] Compat vDSO mapped to ffffe000.
[   18.073175] Remapping vsyscall page to ffffe000
[   18.073191] Checking 'hlt' instruction... OK.
[   18.089007] SMP alternatives: switching to UP code
[   18.089376] Early unpacking initramfs... done
[   18.371274] ACPI: Core revision 20060707
[   18.371439] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.373477] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
[   18.373503] SMP alternatives: switching to SMP code
[   18.373679] Booting processor 1/1 eip 3000
[   18.384272] Initializing CPU#1
[   18.464523] Calibrating delay using timer specific routine.. 5999.78 BogoMIPS (lpj=11999566)
[   18.464534] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e59d 00000000 00000001
[   18.464542] monitor/mwait feature present.
[   18.464549] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   18.464552] CPU: L2 cache: 2048K
[   18.464555] CPU: Physical Processor ID: 0
[   18.464557] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003180 0000e59d 00000000 00000001
[   18.465116] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
[   18.465161] Total of 2 processors activated (12003.72 BogoMIPS).
[   18.465292] ENABLING IO-APIC IRQs
[   18.465476] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.612377] checking TSC synchronization across 2 CPUs: passed.
[    0.003996] Brought up 2 CPUs
[    0.397252] migration_cost=167
[    0.397584] Booting paravirtualized kernel on bare hardware
[    0.397672] Time: 23:55:54  Date: 08/22/107
[    0.397706] NET: Registered protocol family 16
[    0.397810] EISA bus registered
[    0.397817] ACPI: bus type pci registered
[    0.397889] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.397891] PCI: Using configuration type 1
[    0.397893] Setting up standard PCI resources
[    0.410197] ACPI: Interpreter enabled
[    0.410201] ACPI: Using IOAPIC for interrupt routing
[    0.410750] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.410758] PCI: Probing PCI hardware (bus 00)
[    0.411064] Boot video device is 0000:00:02.0
[    0.411423] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.411427] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.411746] PCI: Transparent bridge - 0000:00:1e.0
[    0.411769] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.413674] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.420629] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.420878] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.421130] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.421379] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.421627] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.421877] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.422125] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.422380] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.422530] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.422544] pnp: PnP ACPI init
[    0.426979] pnp: PnP ACPI: found 14 devices
[    0.426985] PnPBIOS: Disabled by ACPI PNP
[    0.427040] PCI: Using ACPI for IRQ routing
[    0.427043] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.429908] NET: Registered protocol family 8
[    0.429911] NET: Registered protocol family 20
[    0.430601] pnp: 00:0c: ioport range 0x290-0x29f has been reserved
[    0.430956] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.430965] PCI: Bridge: 0000:00:1e.0
[    0.430968]   IO window: b000-bfff
[    0.430974]   MEM window: ff000000-ff0fffff
[    0.430978]   PREFETCH window: disabled.
[    0.430991] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.431019] NET: Registered protocol family 2
[    0.475599] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.475689] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.475764] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.475807] TCP: Hash tables configured (established 16384 bind 8192)
[    0.475810] TCP reno registered
[    0.487652] checking if image is initramfs... it is
[    1.046001] Freeing initrd memory: 7007k freed
[    1.046759] audit: initializing netlink socket (disabled)
[    1.046779] audit(1190505354.752:1): initialized
[    1.046983] VFS: Disk quotas dquot_6.5.1
[    1.047007] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.047068] io scheduler noop registered
[    1.047071] io scheduler anticipatory registered
[    1.047073] io scheduler deadline registered
[    1.047087] io scheduler cfq registered (default)
[    1.047402] isapnp: Scanning for PnP cards...
[    1.398792] isapnp: No Plug & Play device found
[    1.427065] Real Time Clock Driver v1.12ac
[    1.427130] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.427258] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.427393] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.428041] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.428239] mice: PS/2 mouse device common for all mice
[    1.428933] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.429113] input: Macintosh mouse button emulation as /class/input/input0
[    1.429158] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.429163] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.429414] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.432233] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.432240] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.432360] EISA: Probing bus 0 at eisa.0
[    1.432399] EISA: Detected 0 cards.
[    1.462472] TCP cubic registered
[    1.462484] NET: Registered protocol family 1
[    1.462513] Starting balanced_irq
[    1.462520] Using IPI No-Shortcut mode
[    1.462615] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.462711] ACPI: (supports S0 S1 S3 S4 S5)
[    1.462770]   Magic number: 7:5:960
[    1.462784]   hash matches device ttyb1
[    1.463234] Freeing unused kernel memory: 328k freed
[    1.466477] Time: tsc clocksource has been installed.
[    2.663946] Capability LSM initialized
[    2.701666] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.701979] ACPI: Processor [CPU2] (supports 8 throttling states)
[    2.701988] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.701997] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.097951] usbcore: registered new interface driver usbfs
[    3.097991] usbcore: registered new interface driver hub
[    3.098025] usbcore: registered new device driver usb
[    3.099223] USB Universal Host Controller Interface driver v3.0
[    3.099320] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.099341] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.099349] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.099577] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.099613] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000dc00
[    3.099807] usb usb1: configuration #1 chosen from 1 choice
[    3.099860] hub 1-0:1.0: USB hub found
[    3.099871] hub 1-0:1.0: 2 ports detected
[    3.121724] 8139too Fast Ethernet driver 0.9.28
[    3.201114] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[    3.201139] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.201147] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.201185] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.201224] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e000
[    3.201357] usb usb2: configuration #1 chosen from 1 choice
[    3.201406] hub 2-0:1.0: USB hub found
[    3.201415] hub 2-0:1.0: 2 ports detected
[    3.304885] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.304905] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.304911] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.304947] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.304979] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
[    3.305145] usb usb3: configuration #1 chosen from 1 choice
[    3.305190] hub 3-0:1.0: USB hub found
[    3.305200] hub 3-0:1.0: 2 ports detected
[    3.408708] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[    3.408721] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.408727] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.408759] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.408783] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e800
[    3.408915] usb usb4: configuration #1 chosen from 1 choice
[    3.408961] hub 4-0:1.0: USB hub found
[    3.408971] hub 4-0:1.0: 2 ports detected
[    3.512772] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 22 (level, low) -> IRQ 19
[    3.513129] eth0: RealTek RTL8139 at 0xe0058c00, 00:19:66:24:c0:01, IRQ 19
[    3.513133] eth0:  Identified 8139 chip type 'RTL-8101'
[    3.516934] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.526197] SCSI subsystem initialized
[    3.534188] libata version 2.20 loaded.
[    3.536211] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.536235] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    3.536264] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.536354] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001fc00 irq 14
[    3.536404] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001fc08 irq 15
[    3.536436] scsi0 : ata_piix
[    3.692378] scsi1 : ata_piix
[    4.012230] ata2.00: ATAPI, max UDMA/33
[    4.176053] ata2.00: configured for UDMA/33
[    4.177005] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182F SB02 PQ: 0 ANSI: 5
[    4.177183] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    4.177207] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[    4.177232] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.177278] ata3: SATA max UDMA/133 cmd 0x0001d000 ctl 0x0001cc02 bmdma 0x0001c000 irq 18
[    4.177317] ata4: SATA max UDMA/133 cmd 0x0001c800 ctl 0x0001c402 bmdma 0x0001c008 irq 18
[    4.177330] scsi2 : ata_piix
[    4.341819] ATA: abnormal status 0x7F on port 0x0001d007
[    4.341837] scsi3 : ata_piix
[    4.547174] ata4.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.547181] ata4.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
[    4.547184] ata4.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.613732] ata4.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.613737] ata4.00: configured for UDMA/133
[    4.613866] scsi 3:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
[    4.614218] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[    4.614235] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.614241] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.614417] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.614457] ehci_hcd 0000:00:1d.7: debug port 1
[    4.614465] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    4.614477] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xff27fc00
[    4.618374] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.620727] usb usb5: configuration #1 chosen from 1 choice
[    4.620774] hub 5-0:1.0: USB hub found
[    4.620784] hub 5-0:1.0: 8 ports detected
[    4.743793] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.743803] Uniform CD-ROM driver Revision: 3.20
[    4.743890] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.745082] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.745103] sda: Write Protect is off
[    4.745109] sda: Mode Sense: 00 3a 00 00
[    4.745137] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.745217] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.745234] sda: Write Protect is off
[    4.745238] sda: Mode Sense: 00 3a 00 00
[    4.745264] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.745271]  sda:<5>sr 1:0:0:0: Attached scsi generic sg0 type 5
[    4.749810] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    4.761538]  sda1 sda2 < sda5 sda6 sda7 sda8 >
[    4.820287] sd 3:0:0:0: Attached scsi disk sda
[    5.144580] Attempting manual resume
[    5.144585] swsusp: Resume From Partition 8:8
[    5.144587] PM: Checking swsusp image.
[    5.154711] PM: Resume from disk failed.
[    5.196241] kjournald starting.  Commit interval 5 seconds
[    5.196249] EXT3-fs: mounted filesystem with ordered data mode.
[   12.046328] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   12.243613] NET: Registered protocol family 10
[   12.243759] lo: Disabled Privacy Extensions
[   13.360121] Linux agpgart interface v0.102 (c) Dave Jones
[   13.416705] agpgart: Detected an Intel 865 Chipset.
[   13.417459] agpgart: Detected 8060K stolen memory.
[   13.431231] agpgart: AGP aperture is 128M @ 0xf0000000
[   13.654599] intel_rng: FWH not detected
[   13.686652] parport: PnPBIOS parport detected.
[   13.686707] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   13.791780] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.810971] irda_init()
[   13.810986] NET: Registered protocol family 23
[   13.867902] input: PC Speaker as /class/input/input2
[   13.894229] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.905099] iTCO_vendor_support: vendor-support=0
[   13.906463] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   14.194448] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   14.194487] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   14.509523] intel8x0_measure_ac97_clock: measured 55812 usecs
[   14.509527] intel8x0: clocking to 48000
[   14.827999] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   14.830503] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   14.830550] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.000008] fuse init (API version 7.8)
[   15.019359] lp0: using parport0 (interrupt-driven).
[   15.047338] Adding 1156640k swap on /dev/disk/by-uuid/8e0ad4a7-d283-457c-83d8-125ef91f98cd.  Priority:-1 extents:1 across:1156640k
[   15.261886] EXT3 FS on sda7, internal journal
[   22.773283] eth0: no IPv6 routers present
[   27.221848] NET: Registered protocol family 17
[   30.016976] input: Power Button (FF) as /class/input/input4
[   30.017015] ACPI: Power Button (FF) [PWRF]
[   30.017109] input: Power Button (CM) as /class/input/input5
[   30.017138] ACPI: Power Button (CM) [PWRB]
[   30.081902] ibm_acpi: ec object not found
[   30.132422] Using specific hotkey driver
[   30.193547] No dock devices found.
[   30.231896] pcc_acpi: loading...
[   34.890513] [drm] Initialized drm 1.1.0 20060810
[   34.894133] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.894614] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   35.589731] ppdev: user-space parallel port driver
[   36.157818] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   36.157826] apm: disabled - APM is not SMP safe.
[   36.318026] Bluetooth: Core ver 2.11
[   36.318130] NET: Registered protocol family 31
[   36.318133] Bluetooth: HCI device and connection manager initialized
[   36.318138] Bluetooth: HCI socket layer initialized
[   36.337509] Bluetooth: L2CAP ver 2.8
[   36.337516] Bluetooth: L2CAP socket layer initialized
[   36.504177] Bluetooth: RFCOMM socket layer initialized
[   36.504204] Bluetooth: RFCOMM TTY layer initialized
[   36.504208] Bluetooth: RFCOMM ver 1.8
[  261.538024] eth0: link down
[  308.085974] eth0: link down
[  308.086770] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  357.127160] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  357.127588] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  362.411787] eth0: link down
[  364.092195] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  367.857045] eth0: no IPv6 routers present
srinivasan@srinivasan-desktop:~$

---

### Post by alienexplorers on 2007-09-23
Is your eth0 wired or wireless.  Can you ping your router (192.168.1.1).  Can you ping [www.google.com](www.google.com).....

---

### Post by klytu on 2007-09-23
If you are trying to connect via ethernet (eth0 as AlienExplorers asked), please post the output of:

```
lspci -nn
```
```
sudo lshw -C network
```
and
```
sudo ethtool eth0
```

These outputs will tell us the name of the card and driver being used and the status of your ethernet connection.

---

### Post by raghuramos1987 on 2007-09-25
guys.thanks for the help but i'm not at the usual comp now...will get back and try these...

---

### Post by beanco on 2007-09-25
I am having problems too with the Net Connection. I just reinstalled Feisty from scratch


I cannot connect to the Net.

I tried the commands suggested above and got this

```

rob@rob-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 SE] [1002:5964] (rev 01)
01:00.1 Display controller [0380]: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) [1002:5d44] (rev 01)
02:05.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
rob@rob-desktop:~$ 


rob@rob-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@02:05.0
       logical name: eth0
       version: 02
       serial: 00:13:d4:eb:c7:61
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=N/A latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:fbfe0000-fbffffff ioport:e800-e83f irq:20

rob@rob-desktop:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes
```


It is long, it is confusing to me but if anybody has any ideas.... let me know

I have a router, not sure if this makes any difference...

thanks

robi

---

### Post by klytu on 2007-09-26
> **beanco said:**
> I am having problems too with the Net Connection. I just reinstalled Feisty from scratch


I cannot connect to the Net.

I tried the commands suggested above and got this

```

rob@rob-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 SE] [1002:5964] (rev 01)
01:00.1 Display controller [0380]: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) [1002:5d44] (rev 01)
02:05.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
rob@rob-desktop:~$ 


rob@rob-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@02:05.0
       logical name: eth0
       version: 02
       serial: 00:13:d4:eb:c7:61
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=N/A latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:fbfe0000-fbffffff ioport:e800-e83f irq:20

rob@rob-desktop:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes
```


It is long, it is confusing to me but if anybody has any ideas.... let me know

I have a router, not sure if this makes any difference...

thanks

robi

Your output indicates that your Intel Gigabit Ethernet device has been detected and that it's working. If your internet connection is through a modem connected to your router or if you have a combination modem/router unit, you should be able to connect to the internet. Were you able to connect before you reinstalled Feisty?

Try: ```
gksu network-admin
``` and check the settings under Wired Connection.  If your connection is through your router, you should probably have this set for automatic configuration (DHCP). You can confirm this by highlighting "Wired Connection" and clicking "Properties". If you have a modem listed, make sure that the modem is not set as the default route to the internet.

---

### Post by beanco on 2007-09-26
yeah in the old install of feisty I coudl use the Net.. 

I have a router, but have no idea how it sworks, how to set the dchp on it, etc.


it was doen by a friend... months ago...

so if I udnerstand correctly this is likely the culprit and should be reset. right?

I will try the command you suggest.. but the

[HTML]and check the settings under Wired Connection. If your connection is through your router, you should probably have this set for automatic configuration (DHCP). You can confirm this by highlighting "Wired Connection" and clicking "Properties". If you have a modem listed, make sure that the modem is not set as the default route to the internet[/HTML]


where? how? 

thanks

robi

---

### Post by klytu on 2007-09-26
> **beanco said:**
> yeah in the old install of feisty I coudl use the Net.. 

I have a router, but have no idea how it sworks, how to set the dchp on it, etc.


it was doen by a friend... months ago...

so if I udnerstand correctly this is likely the culprit and should be reset. right?

I will try the command you suggest.. but the

[HTML]and check the settings under Wired Connection. If your connection is through your router, you should probably have this set for automatic configuration (DHCP). You can confirm this by highlighting "Wired Connection" and clicking "Properties". If you have a modem listed, make sure that the modem is not set as the default route to the internet[/HTML]


where? how? 

thanks

robi

You probably won't have to change any of the router's settings (by the way, what is the make and model of your router?). They are usually very easy to set up; in many cases you can just plug in the ethernet cables and go.  I meant for you to check for DHCP by issuing the command ```
gksu network-admin
``` A box should pop-up in the Gnome GUI requesting your password, then after you enter your password the GUI for Network Administration appears. You should see listed "Wired Connection" and also possibly "Modem" or some other entries. Highlight "Wired Connection" and then click the "Properties" buttion on the right. Confirm that your wired connection is set to Automatic (DHCP).  If you get any error messages, post those. Or if the Network Administration GUI doesn't appear at all when you issue the command I suggested, post back and we'll try to help.

---

### Post by beanco on 2007-09-26
> **klytu said:**
>   I meant for you to check for DHCP by issuing the command ```
gksu network-admin
``` A box should pop-up in the Gnome GUI requesting your password, then after you enter your password the GUI for Network Administration appears. You should see listed "Wired Connection" and also possibly "Modem" or some other entries. Highlight "Wired Connection" and then click the "Properties" buttion on the right. Confirm that your wired connection is set to Automatic (DHCP).  If you get any error messages, post those. Or if the Network Administration GUI doesn't appear at all when you issue the command I suggested, post back and we'll try to help.

i figured that is what you meant. That is what I did. 

ran gksu networkadmin.... got the box, highlighted wired conection, all the stuff you suggested but it did not help. It just did not connect....

the entire system was too slow, i had several freezes, I had some error msg about .... them Human....

and a few other wierd things.

it was very annoying. at this very minute I am installing it all anew!

maybe with this new installation it will just work fine.

thankis

robi

---

### Post by klytu on 2007-09-26
> **beanco said:**
> i figured that is what you meant. That is what I did. 

ran gksu networkadmin.... got the box, highlighted wired conection, all the stuff you suggested but it did not help. It just did not connect....

the entire system was too slow, i had several freezes, I had some error msg about .... them Human....

and a few other wierd things.

it was very annoying. at this very minute I am installing it all anew!

maybe with this new installation it will just work fine.

thankis

robi

OK. Good luck with the new installation. If you get any error messages, try to make a note of them; they may be related to your connection issue.

---

### Post by beanco on 2007-09-27
isntalled it no worries.

but i still cannot connect to the internet!

I checked the network settings it seems ok.

There is a little icon in the top panel that says wired connection successful or sg to that extent.

I really need to get the Net connection going because I will need the computer for work... this is getting annoying.

robi

---

### Post by BoyOfDestiny on 2007-09-27
> **beanco said:**
> isntalled it no worries.

but i still cannot connect to the internet!

I checked the network settings it seems ok.

There is a little icon in the top panel that says wired connection successful or sg to that extent.

I really need to get the Net connection going because I will need the computer for work... this is getting annoying.

robi

Hmm... What is your ip address? Also, you said someone configured your router... Can you connect whatever you have straight to your machine (i.e. cable modem to back of computer, rather than through the router?)

---

### Post by beanco on 2007-09-27
i will try the line directly to the computer tonight.

i just have to get to it befroe my wife starts using the line for her laptop

which I have not managed to do yet.


robi

---

### Post by beanco on 2007-10-01
back up and running. thanks for all the help!

They guy who set up the router had forgotten to tell me the FIX IP for the LAN.. that is why I could not get online. once the IP were put in, things went smoothly.

robi

---

### Post by raghuramos1987 on 2007-11-20
i'm sorry ot have replied so late. i was asked to run these cmds and post the output. i was not in town and got to it immediately... now i installed gutsy over the feisty version(erasin the feisty one) still no net :(. these are the outputs. i'm able to access net thru windows but not thru gutsy...

PLZ HELP :(

srinivasan@srinivasan-desktop:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
srinivasan@srinivasan-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
srinivasan@srinivasan-desktop:~$ sudo lshw -C network
[sudo] password for srinivasan:
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:19:66:24:c0:01
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
srinivasan@srinivasan-desktop:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)

---

