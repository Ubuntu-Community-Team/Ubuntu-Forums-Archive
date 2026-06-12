---
title: "Eth1 not working correctly???"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by pgar23 on 2007-08-30
Wireless not working on laptop. Toshiba Satellite M45.

results of ifconfig -a:

```
payton@the-Laptop:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:27:E1:79   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:11  
 
eth1      Link encap:Ethernet  HWaddr 00:13:CE:8F:E3:92   
          inet6 addr: fe80::213:ceff:fe8f:e392/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:76 errors:2 dropped:2 overruns:0 frame:0 
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:8014 (7.8 KiB) 
          Interrupt:11 Base address:0xa000 Memory:b800b000-b800bfff  
 
eth1:avah Link encap:Ethernet  HWaddr 00:13:CE:8F:E3:92   
          inet addr:169.254.9.195  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:11 Base address:0xa000 Memory:b800b000-b800bfff  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:2308 (2.2 KiB)  TX bytes:2308 (2.2 KiB) 
```

I also ran ```
sudo ifup eth1
```
It said ifup: interface eth1 already configured

 Results of dmesg: ```
&#65279;payton@the-Laptop:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f6dfffc end: 000000003f7dfffc type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f7dfffc size: 000000000001ffc4 end: 000000003f7fffc0 type: 3
[    0.000000] copy_e820_map() start: 000000003f7fffc0 size: 0000000000000040 end: 000000003f800000 type: 4
[    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7dfffc (usable)
[    0.000000]  BIOS-e820: 000000003f7dfffc - 000000003f7fffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f7fffc0 - 000000003f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 260063) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   260063
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   260063
[    0.000000] On node 0 totalpages: 260063
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 239 pages used for memmap
[    0.000000]   HighMem zone: 30448 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 TOSINV                                ) @ 0x000e5010
[    0.000000] ACPI: RSDT (v001 INSYDE RSDT_000 0x00000100 ABCD 0x00010200) @ 0x3f7f86c7
[    0.000000] ACPI: FADT (v001 TOSINV FACP_000 0x00000100 0000 0x00010200) @ 0x3f7ffb30
[    0.000000] ACPI: MCFG (v001 INSYDE MCFG_000 0x30303030 0000 0x30303030) @ 0x3f7ffbc0
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030522) @ 0x3f7f88b5
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030522) @ 0x3f7f86fb
[    0.000000] ACPI: DSDT (v001 TOSINV SONOMA   0x00001004 INTL 0x02002036) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:c0700000)
[    0.000000] Detected 1596.089 MHz processor.
[    8.391008] Built 1 zonelists.  Total pages: 258032
[    8.391013] Kernel command line: root=UUID=64e99df0-a491-48dd-b159-394368ef108e ro quiet splash
[    8.391186] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    8.391191] mapped APIC to ffffd000 (017fc000)
[    8.391198] Enabling fast FPU save and restore... done.
[    8.391201] Enabling unmasked SIMD FPU exception support... done.
[    8.391208] Initializing CPU#0
[    8.391286] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    8.393085] Console: colour VGA+ 80x25
[    8.393485] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.393974] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.430162] Memory: 1020056k/1040252k available (1992k kernel code, 19380k reserved, 893k data, 328k init, 122748k highmem)
[    8.430172] virtual kernel memory layout:
[    8.430173]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    8.430175]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.430176]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.430177]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.430179]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[    8.430180]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[    8.430181]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[    8.430185] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.507191] Calibrating delay using timer specific routine.. 3195.36 BogoMIPS (lpj=6390726)
[    8.507234] Security Framework v1.0.0 initialized
[    8.507244] SELinux:  Disabled at boot.
[    8.507261] Mount-cache hash table entries: 512
[    8.507407] CPU: After generic identify, caps: afe9f9ff 00000000 00000000 00000000 00000180 00000000 00000000
[    8.507419] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.507421] CPU: L2 cache: 2048K
[    8.507424] CPU: After all inits, caps: afe9f9ff 00000000 00000000 00002040 00000180 00000000 00000000
[    8.507434] Compat vDSO mapped to ffffe000.
[    8.507438] Remapping vsyscall page to ffffe000
[    8.507451] Checking 'hlt' instruction... OK.
[    8.523277] SMP alternatives: switching to UP code
[    8.523463] Freeing SMP alternatives: 11k freed
[    8.523651] Early unpacking initramfs... done
[    8.870231] ACPI: Core revision 20060707
[    8.870341] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    8.873228] ACPI: setting ELCR to 0200 (from 0c20)
[    8.952062] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[    8.952070] SMP motherboard not detected.
[    8.952073] Local APIC not detected. Using dummy APIC emulation.
[    8.952108] Brought up 1 CPUs
[    8.952357] Booting paravirtualized kernel on bare hardware
[    8.952444] Time: 13:37:09  Date: 07/30/107
[    8.952473] NET: Registered protocol family 16
[    8.952560] EISA bus registered
[    8.952565] ACPI: bus type pci registered
[    8.952619] PCI: PCI BIOS revision 2.10 entry at 0xea7d4, last bus=5
[    8.952622] PCI: Using configuration type 1
[    8.952624] Setting up standard PCI resources
[    8.955963] ACPI: Interpreter enabled
[    8.955965] ACPI: Using PIC for interrupt routing
[    8.956714] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.956719] PCI: Probing PCI hardware (bus 00)
[    8.957655] Boot video device is 0000:00:02.0
[    8.958274] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    8.958280] PCI quirk: region 1300-133f claimed by ICH6 GPIO
[    8.959066] PCI: Transparent bridge - 0000:00:1e.0
[    8.959134] PCI: Bus #06 (-#09) is hidden behind transparent bridge #05 (-#05) (try 'pci=assign-busses')
[    8.959137] Please report the result to linux-kernel to fix this permanently
[    8.959186] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.987442] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    8.987745] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    8.988858] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    8.995224] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *11)
[    8.995543] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[    8.995799] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 *11)
[    8.996059] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[    8.996313] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 11)
[    8.996565] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 10) *0, disabled.
[    8.996866] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *11
[    8.997118] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11
[    9.000137] ACPI: Power Resource [PFA1] (off)
[    9.000266] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.000274] pnp: PnP ACPI init
[    9.008244] pnp: PnP ACPI: found 9 devices
[    9.008248] PnPBIOS: Disabled by ACPI PNP
[    9.008288] PCI: Using ACPI for IRQ routing
[    9.008290] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.008326] PCI: Cannot allocate resource region 0 of device 0000:05:06.0
[    9.017292] NET: Registered protocol family 8
[    9.017295] NET: Registered protocol family 20
[    9.017625] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    9.017629] PCI: Bridge: 0000:00:1c.0
[    9.017632]   IO window: c000-dfff
[    9.017639]   MEM window: cc000000-cfffffff
[    9.017644]   PREFETCH window: 9c000000-9fffffff
[    9.017649] PCI: Bridge: 0000:00:1c.1
[    9.017653]   IO window: a000-bfff
[    9.017659]   MEM window: c8000000-cbffffff
[    9.017663]   PREFETCH window: 98000000-9bffffff
[    9.017677] PCI: Bus 6, cardbus bridge: 0000:05:06.0
[    9.017679]   IO window: 00008000-000080ff
[    9.017684]   IO window: 00008400-000084ff
[    9.017690]   PREFETCH window: 88000000-8bffffff
[    9.017695]   MEM window: bc000000-bfffffff
[    9.017700] PCI: Bridge: 0000:00:1e.0
[    9.017704]   IO window: 8000-9fff
[    9.017710]   MEM window: b8000000-c7ffffff
[    9.017714]   PREFETCH window: 88000000-97ffffff
[    9.017933] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    9.017936] PCI: setting IRQ 10 as level-triggered
[    9.017941] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    9.017950] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.018154] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    9.018156] PCI: setting IRQ 11 as level-triggered
[    9.018161] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    9.018168] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.018181] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.018378] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    9.018381] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    9.018406] NET: Registered protocol family 2
[    9.054756] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.054860] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.055706] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.056210] TCP: Hash tables configured (established 131072 bind 65536)
[    9.056213] TCP reno registered
[    9.066851] checking if image is initramfs... it is
[    9.753291] Freeing initrd memory: 6759k freed
[    9.753741] audit: initializing netlink socket (disabled)
[    9.753760] audit(1188481029.468:1): initialized
[    9.753843] highmem bounce pool size: 64 pages
[    9.753918] VFS: Disk quotas dquot_6.5.1
[    9.753938] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.753999] io scheduler noop registered
[    9.754002] io scheduler anticipatory registered
[    9.754005] io scheduler deadline registered
[    9.754015] io scheduler cfq registered (default)
[    9.754322] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.754376] assign_interrupt_mode Found MSI capability
[    9.754380] Allocate Port Service[0000:00:1c.0:pcie00]
[    9.754415] Allocate Port Service[0000:00:1c.0:pcie02]
[    9.754530] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.754581] assign_interrupt_mode Found MSI capability
[    9.754584] Allocate Port Service[0000:00:1c.1:pcie00]
[    9.754618] Allocate Port Service[0000:00:1c.1:pcie02]
[    9.754788] isapnp: Scanning for PnP cards...
[   10.108701] isapnp: No Plug & Play device found
[   10.134093] Real Time Clock Driver v1.12ac
[   10.134157] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.135117] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[   10.135121] PCI: setting IRQ 5 as level-triggered
[   10.135126] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   10.135137] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   10.135233] mice: PS/2 mouse device common for all mice
[   10.135801] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.136038] input: Macintosh mouse button emulation as /class/input/input0
[   10.136073] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   10.136077] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   10.136305] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.140991] i8042.c: Detected active multiplexing controller, rev 1.1.
[   10.142618] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.142622] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   10.142625] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   10.142628] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   10.142630] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   10.142754] EISA: Probing bus 0 at eisa.0
[   10.142762] Cannot allocate resource for EISA slot 1
[   10.142786] Cannot allocate resource for EISA slot 8
[   10.142788] EISA: Detected 0 cards.
[   10.172872] TCP cubic registered
[   10.172884] NET: Registered protocol family 1
[   10.172906] Using IPI No-Shortcut mode
[   10.172973] ACPI: (supports S0 S3 S4 S5)
[   10.173023]   Magic number: 3:227:636
[   10.173074]   hash matches device ptycf
[   10.173149]   hash matches device 0000:00:1c.1:pcie02
[   10.173342] Freeing unused kernel memory: 328k freed
[   10.173717] Time: tsc clocksource has been installed.
[   10.176212] input: AT Translated Set 2 keyboard as /class/input/input1
[   11.386420] Capability LSM initialized
[   11.416835] ACPI: Transitioning device [FAN1] to D3
[   11.416839] ACPI: Transitioning device [FAN1] to D3
[   11.416842] ACPI: Fan [FAN1] (off)
[   11.421109] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   11.421115] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.421124] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.004000] Time: acpi_pm clocksource has been installed.
[    3.020000] ACPI: Thermal Zone [TZCR] (48 C)
[    3.028000] ACPI: Thermal Zone [TZCL] (39 C)
[    3.396000] usbcore: registered new interface driver usbfs
[    3.396000] usbcore: registered new interface driver hub
[    3.396000] usbcore: registered new device driver usb
[    3.396000] USB Universal Host Controller Interface driver v3.0
[    3.396000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    3.396000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.396000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.396000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.396000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.396000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[    3.396000] usb usb1: configuration #1 chosen from 1 choice
[    3.396000] hub 1-0:1.0: USB hub found
[    3.396000] hub 1-0:1.0: 2 ports detected
[    3.488000] SCSI subsystem initialized
[    3.492000] libata version 2.20 loaded.
[    3.500000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    3.500000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.500000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.500000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.500000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.500000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001220
[    3.500000] usb usb2: configuration #1 chosen from 1 choice
[    3.500000] hub 2-0:1.0: USB hub found
[    3.500000] hub 2-0:1.0: 2 ports detected
[    3.604000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.604000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.604000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.604000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.604000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001240
[    3.604000] usb usb3: configuration #1 chosen from 1 choice
[    3.604000] hub 3-0:1.0: USB hub found
[    3.604000] hub 3-0:1.0: 2 ports detected
[    3.604000] ieee1394: Initialized config rom entry `ip1394'
[    3.708000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.708000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.708000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.708000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.708000] uhci_hcd 0000:00:1d.3: irq 11, io base 0x00001260
[    3.708000] usb usb4: configuration #1 chosen from 1 choice
[    3.708000] hub 4-0:1.0: USB hub found
[    3.708000] hub 4-0:1.0: 2 ports detected
[    3.812000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[    3.812000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.812000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.812000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.812000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.812000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.812000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.812000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000
[    3.816000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.816000] usb usb5: configuration #1 chosen from 1 choice
[    3.816000] hub 5-0:1.0: USB hub found
[    3.816000] hub 5-0:1.0: 8 ports detected
[    3.920000] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.920000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.076000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    4.076000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.076000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14
[    4.076000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15
[    4.076000] scsi0 : ata_piix
[    4.240000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.240000] ata1.00: ATA-6: HTS541080G9AT00, MB4OA60A, max UDMA/100
[    4.240000] ata1.00: 156301488 sectors, multi 16: LBA48 
[    4.240000] ata1.00: applying bridge limits
[    4.248000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.248000] ata1.00: configured for UDMA/100
[    4.248000] scsi1 : ata_piix
[    4.568000] ata2.00: ATAPI, max UDMA/33
[    4.732000] ata2.00: configured for UDMA/33
[    4.732000] scsi 0:0:0:0: Direct-Access     ATA      HTS541080G9AT00  MB4O PQ: 0 ANSI: 5
[    4.732000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.00 PQ: 0 ANSI: 5
[    4.740000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 6
[    4.740000] PCI: setting IRQ 6 as level-triggered
[    4.740000] ACPI: PCI Interrupt 0000:05:06.2[C] -> Link [LNKG] -> GSI 6 (level, low) -> IRQ 6
[    4.796000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.800000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.800000] sda: Write Protect is off
[    4.800000] sda: Mode Sense: 00 3a 00 00
[    4.800000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.800000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.800000] sda: Write Protect is off
[    4.800000] sda: Mode Sense: 00 3a 00 00
[    4.800000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.800000]  sda: sda1 sda2 sda3
[    4.848000] sd 0:0:0:0: Attached scsi disk sda
[    4.852000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.852000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.860000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.860000] Uniform CD-ROM driver Revision: 3.20
[    4.860000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.152000] Attempting manual resume
[    5.152000] swsusp: Resume From Partition 8:3
[    5.152000] PM: Checking swsusp image.
[    5.152000] PM: Resume from disk failed.
[    5.164000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.164000] EXT3-fs: write access will be enabled during recovery.
[    6.068000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d127e179]
[    6.696000] kjournald starting.  Commit interval 5 seconds
[    6.696000] EXT3-fs: sda2: orphan cleanup on readonly fs
[    6.696000] ext3_orphan_cleanup: deleting unreferenced inode 2550953
[    6.696000] EXT3-fs: sda2: 1 orphan inode deleted
[    6.696000] EXT3-fs: recovery complete.
[    6.732000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.296000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.300000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.532000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.648000] agpgart: Detected an Intel 915GM Chipset.
[   18.648000] agpgart: Detected 7932K stolen memory.
[   18.664000] agpgart: AGP aperture is 256M @ 0xa0000000
[   18.664000] intel_rng: FWH not detected
[   18.736000] iTCO_vendor_support: vendor-support=0
[   18.736000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   18.736000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   18.736000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.984000] Yenta: CardBus bridge found at 0000:05:06.0 [1179:ff10]
[   18.984000] Yenta: Enabling burst memory read transactions
[   18.984000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   18.984000] Yenta: Routing CardBus interrupts to PCI
[   18.984000] Yenta TI: socket 0000:05:06.0, mfunc 0x01aa1b22, devctl 0x66
[   19.216000] Yenta: ISA IRQ mask 0x0098, PCI irq 11
[   19.216000] Socket status: 30000006
[   19.216000] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   19.216000] pcmcia: parent PCI bridge I/O window: 0x8000 - 0x9fff
[   19.216000] cs: IO port probe 0x8000-0x9fff: clean.
[   19.216000] pcmcia: parent PCI bridge Memory window: 0xb8000000 - 0xc7ffffff
[   19.216000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x97ffffff
[   19.216000] ACPI: PCI Interrupt 0000:05:06.3[D] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   19.460000] ieee80211_crypt: registered algorithm 'NULL'
[   19.460000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.460000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.484000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   19.484000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.484000] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   19.484000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   19.844000] sdhci: Secure Digital Host Controller Interface driver
[   19.844000] sdhci: Copyright(c) Pierre Ossman
[   19.844000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   19.844000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   19.844000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   19.844000] sky2 0000:01:00.0: v1.13 addr 0xcc000000 irq 11 Yukon-FE (0xb7) rev 1
[   19.848000] sky2 eth1: addr 00:a0:d1:27:e1:79
[   19.848000] sdhci: SDHCI controller found at 0000:05:06.4 [104c:8034] (rev 0)
[   19.848000] ACPI: PCI Interrupt 0000:05:06.4[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   19.848000] mmc0: SDHCI at 0xb800a000 irq 11 DMA
[   19.852000] mmc1: SDHCI at 0xb800a100 irq 11 DMA
[   19.852000] mmc2: SDHCI at 0xb800a200 irq 11 DMA
[   20.088000] ieee80211_crypt: registered algorithm 'WEP'
[   20.236000] cs: IO port probe 0x100-0x3af: excluding 0x300-0x307 0x310-0x31f
[   20.236000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   20.236000] cs: IO port probe 0x820-0x8ff: clean.
[   20.240000] cs: IO port probe 0xc00-0xcf7: clean.
[   20.240000] cs: IO port probe 0xa00-0xaff: clean.
[   20.292000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   20.292000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   21.112000] intel8x0_measure_ac97_clock: measured 55499 usecs
[   21.112000] intel8x0: clocking to 48000
[   21.260000] lp: driver loaded but no devices found
[   21.304000] Adding 996020k swap on /dev/disk/by-uuid/66c4a7cd-0d5a-42ea-b352-497342f5bdb5.  Priority:-1 extents:1 across:996020k
[   21.420000] NET: Registered protocol family 17
[   21.476000] EXT3 FS on sda2, internal journal
[   21.628000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   21.700000] NTFS volume version 3.1.
[   22.192000] Using specific hotkey driver
[   22.212000] ACPI: ACPI Dock Station Driver 
[   22.228000] ACPI: Battery Slot [BAT1] (battery absent)
[   22.248000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   22.404000] input: Power Button (FF) as /class/input/input2
[   22.408000] ACPI: Power Button (FF) [PWRF]
[   22.444000] input: Lid Switch as /class/input/input3
[   22.448000] ACPI: Lid Switch [LID0]
[   22.488000] input: Power Button (CM) as /class/input/input4
[   22.488000] ACPI: Power Button (CM) [PWRB]
[   22.500000] ibm_acpi: ec object not found
[   22.528000] ACPI: AC Adapter [AC] (on-line)
[   22.556000] pcc_acpi: loading...
[   25.464000] sky2 eth0: enabling interface
[   25.468000] sky2 eth0: ram buffer 4K
[   26.308000] [drm] Initialized drm 1.1.0 20060810
[   26.312000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   26.312000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   27.304000] ppdev: user-space parallel port driver
[   28.012000] apm: BIOS not found.
[   28.128000] Bluetooth: Core ver 2.11
[   28.128000] NET: Registered protocol family 31
[   28.128000] Bluetooth: HCI device and connection manager initialized
[   28.128000] Bluetooth: HCI socket layer initialized
[   28.168000] Bluetooth: L2CAP ver 2.8
[   28.168000] Bluetooth: L2CAP socket layer initialized
[   28.348000] Bluetooth: RFCOMM socket layer initialized
[   28.348000] Bluetooth: RFCOMM TTY layer initialized
[   28.348000] Bluetooth: RFCOMM ver 1.8
[   41.804000] NET: Registered protocol family 10
[   41.804000] lo: Disabled Privacy Extensions
[   41.804000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.412000] eth1: no IPv6 routers present
[  131.824000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[  132.004000] usb 1-1: configuration #1 chosen from 1 choice
[  132.180000] usbcore: registered new interface driver hiddev
[  132.196000] input: Kensington      Kensington USB/PS2 Wheel Mouse as /class/input/input5
[  132.196000] input: USB HID v1.10 Mouse [Kensington      Kensington USB/PS2 Wheel Mouse] on usb-0000:00:1d.0-1
[  132.196000] usbcore: registered new interface driver usbhid
[  132.196000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[  162.612000] usb 5-2: new high speed USB device using ehci_hcd and address 3
[  162.744000] usb 5-2: configuration #1 chosen from 1 choice
[  162.884000] usbcore: registered new interface driver libusual
[  162.896000] Initializing USB Mass Storage driver...
[  162.896000] scsi2 : SCSI emulation for USB Mass Storage devices
[  162.896000] usbcore: registered new interface driver usb-storage
[  162.896000] USB Mass Storage support registered.
[  162.896000] usb-storage: device found at 3
[  162.896000] usb-storage: waiting for device to settle before scanning
[  167.896000] usb-storage: device scan complete
[  167.896000] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[  167.896000] SCSI device sdb: 1994385 512-byte hdwr sectors (1021 MB)
[  167.896000] sdb: Write Protect is off
[  167.896000] sdb: Mode Sense: 03 00 00 00
[  167.896000] sdb: assuming drive cache: write through
[  167.900000] SCSI device sdb: 1994385 512-byte hdwr sectors (1021 MB)
[  167.900000] sdb: Write Protect is off
[  167.900000] sdb: Mode Sense: 03 00 00 00
[  167.900000] sdb: assuming drive cache: write through
[  167.900000]  sdb: sdb1
[  167.904000] sd 2:0:0:0: Attached scsi removable disk sdb
[  167.904000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  263.172000] usb 5-2: USB disconnect, address 3
[  566.968000] usb 5-2: new high speed USB device using ehci_hcd and address 4
[  567.100000] usb 5-2: configuration #1 chosen from 1 choice
[  567.248000] scsi3 : SCSI emulation for USB Mass Storage devices
[  567.324000] usb-storage: device found at 4
[  567.324000] usb-storage: waiting for device to settle before scanning
[  572.324000] usb-storage: device scan complete
[  572.328000] scsi 3:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[  572.336000] SCSI device sdb: 1994385 512-byte hdwr sectors (1021 MB)
[  572.336000] sdb: Write Protect is off
[  572.340000] sdb: Mode Sense: 03 00 00 00
[  572.340000] sdb: assuming drive cache: write through
[  572.340000] SCSI device sdb: 1994385 512-byte hdwr sectors (1021 MB)
[  572.340000] sdb: Write Protect is off
[  572.340000] sdb: Mode Sense: 03 00 00 00
[  572.340000] sdb: assuming drive cache: write through
[  572.340000]  sdb: sdb1
[  572.344000] sd 3:0:0:0: Attached scsi removable disk sdb
[  572.344000] sd 3:0:0:0: Attached scsi generic sg2 type 0
payton@the-Laptop:~$ 
```

SORRY THIS THREAD IS SO LONG.


Need help.
TIA.

---

### Post by annda on 2007-08-30
hi,

first make sure that the driver is loaded - this thread can help you do that:
[http://ubuntuforums.org/showthread.php?t=477304](http://ubuntuforums.org/showthread.php?t=477304)

second, make sure the network manager is configured correctly - by the way, what tool/applet are you using for this? and what is your router's encryption (WEP or WPA)? do you have an ASCII or a hexadecimal key? is it on the first position in the router's list of keys?

i'm out of ideas for the moment...

---

### Post by igknighted on 2007-08-30
eth1 is typically a wired connection... run 'iwconfig' to see if it shows up as a wireless device.  If it does, please post the info that annda requested.

Also, what is the result of "lspci", this will tell us adapter we are dealing with.

this line is the only reference I could find to eth1, which is a really odd thing to see:
> [   52.412000] eth1: no IPv6 routers present

---

