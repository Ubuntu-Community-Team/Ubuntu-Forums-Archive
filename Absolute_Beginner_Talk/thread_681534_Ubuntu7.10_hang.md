---
title: "Ubuntu7.10 hang"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by shivcharan on 2008-01-29
Hi Linux-Ubuntu Lovers,

I am new for Linux and also new for Ubuntu,
After successful installation of Ubuntu my system hang/pause for 2 to 10 minutes. And its happen randomly some time twice in a hour. I take a close look at log files and I guess it is problem of tsc clocksource because I notice there is log entry for installation of tsc clocksource after every hang. The log entry is :- "tsc clocksource has been installed". Please help me.

---

### Post by ajmorris on 2008-01-29
> **shivcharan said:**
> Hi Linux-Ubuntu Lovers,

I am new for Linux and also new for Ubuntu,
After successful installation of Ubuntu my system hang/pause for 2 to 10 minutes. And its happen randomly some time twice in a hour. I take a close look at log files and I guess it is problem of tsc clocksource because I notice there is log entry for installation of tsc clocksource after every hang. The log entry is :- "tsc clocksource has been installed". Please help me.

Hi there, 
could you please give the following details:
```
sudo lspci
```
Upload /var/log/syslog
and:
```
dmesg
```
and upload:
```
/var/log/Xorg.0.log
```

AJ

---

### Post by shivcharan on 2008-01-29
Hi ajmorris,
Thanks for your helping hand.:)
The output of command :- [COLOR="Red"]"sudo lspc[/COLOR]i" is ```
 shivcharan@shiv-ubuntu:~$ sudo lspci
[sudo] password for shivcharan:
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
 
```

And output of command :- [COLOR="Red"]"sudo lspc[/COLOR]i" is ```
 shivcharan@shiv-ubuntu:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bef0000 (usable)
[    0.000000]  BIOS-e820: 000000001bef0000 - 000000001bef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bef3000 - 000000001bf00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 446MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6060
[    0.000000] Entering add_active_range(0, 0, 114416) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114416
[    0.000000]   HighMem    114416 ->   114416
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114416
[    0.000000] On node 0 totalpages: 114416
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 861 pages used for memmap
[    0.000000]   Normal zone: 109459 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7ED0 checksum 0
[    0.000000] ACPI: RSDP 000F7ED0, 0014 (r0 ATi   )
[    0.000000] ACPI: RSDT 1BEF3040, 0038 (r1 ATi    AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1BEF30C0, 0074 (r1 ATi    AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1BEF3180, 3782 (r1 ATI    AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 1BEF0000, 0040
[    0.000000] ACPI: MCFG 1BEF6A80, 003C (r1 ATi    AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 1BEF6980, 0084 (r1 ATi    AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 1BEF6B00, 015C (r1 ATI     Cpu0Ist     3000 INTL 20040311)
[    0.000000] ACPI: SSDT 1BEF6F90, 0275 (r1 ATI       CpuPm     3000 INTL 20040311)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1bf00000:c4100000)
[    0.000000] Built 1 zonelists.  Total pages: 113523
[    0.000000] Kernel command line: root=UUID=df6f973e-151d-4ff6-a1e9-997478f1267a ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 3000.314 MHz processor.
[   28.921374] Console: colour VGA+ 80x25
[   28.921798] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.922122] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.931469] Memory: 442124k/457664k available (2015k kernel code, 14964k reserved, 916k data, 364k init, 0k highmem)
[   28.931479] virtual kernel memory layout:
[   28.931481]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   28.931482]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.931483]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[   28.931484]     lowmem  : 0xc0000000 - 0xdbef0000   ( 446 MB)
[   28.931485]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   28.931486]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   28.931487]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   28.931490] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.931531] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   29.011487] Calibrating delay using timer specific routine.. 6007.43 BogoMIPS (lpj=12014860)
[   29.011513] Security Framework v1.0.0 initialized
[   29.011518] SELinux:  Disabled at boot.
[   29.011530] Mount-cache hash table entries: 512
[   29.011656] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[   29.011665] monitor/mwait feature present.
[   29.011667] using mwait in idle threads.
[   29.011674] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   29.011677] CPU: L2 cache: 2048K
[   29.011680] CPU: Physical Processor ID: 0
[   29.011682] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000
[   29.011692] Compat vDSO mapped to ffffe000.
[   29.011708] Checking 'hlt' instruction... OK.
[   29.027575] SMP alternatives: switching to UP code
[   29.028002] Early unpacking initramfs... done
[   29.309396] ACPI: Core revision 20070126
[   29.309454] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   29.338188] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[   29.338213] SMP alternatives: switching to SMP code
[   29.338361] Booting processor 1/1 eip 3000
[   29.348656] Initializing CPU#1
[   29.427117] Calibrating delay using timer specific routine.. 6000.69 BogoMIPS (lpj=12001385)
[   29.427128] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[   29.427135] monitor/mwait feature present.
[   29.427142] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   29.427145] CPU: L2 cache: 2048K
[   29.427148] CPU: Physical Processor ID: 0
[   29.427151] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000
[   29.427684] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[   29.427729] Total of 2 processors activated (12008.12 BogoMIPS).
[   29.427902] ENABLING IO-APIC IRQs
[   29.428104] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   29.575112] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   29.595110] Brought up 2 CPUs
[   29.993847] migration_cost=444
[   29.994042] Booting paravirtualized kernel on bare hardware
[   29.994133] Time: 16:35:27  Date: 00/29/108
[   29.994161] NET: Registered protocol family 16
[   29.994260] EISA bus registered
[   29.994266] ACPI: bus type pci registered
[   29.996394] PCI: PCI BIOS revision 3.00 entry at 0xf1df0, last bus=2
[   29.996396] PCI: Using configuration type 1
[   29.996398] Setting up standard PCI resources
[   29.997873] ACPI: EC: Look up EC in DSDT
[   30.001544] ACPI: Interpreter enabled
[   30.001548] ACPI: (supports S0 S3 S4 S5)
[   30.001569] ACPI: Using IOAPIC for interrupt routing
[   30.006211] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.006235] PCI: Probing PCI hardware (bus 00)
[   30.007660] PCI: Transparent bridge - 0000:00:14.4
[   30.007705] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.007900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   30.008030] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   30.017039] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   30.017147] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   30.017253] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   30.017357] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   30.017463] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   30.017567] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11)
[   30.017671] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11)
[   30.017775] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11)
[   30.017894] Linux Plug and Play Support v0.97 (c) Adam Belay
[   30.017909] pnp: PnP ACPI init
[   30.017919] ACPI: bus type pnp registered
[   30.020579] pnp: PnP ACPI: found 14 devices
[   30.020582] ACPI: ACPI bus type pnp unregistered
[   30.020588] PnPBIOS: Disabled by ACPI PNP
[   30.020648] PCI: Using ACPI for IRQ routing
[   30.020652] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   30.020660] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   30.087140] NET: Registered protocol family 8
[   30.087143] NET: Registered protocol family 20
[   30.087209] pnp: 00:01: ioport range 0x228-0x22f has been reserved
[   30.087212] pnp: 00:01: ioport range 0x40b-0x40b has been reserved
[   30.087215] pnp: 00:01: ioport range 0x4d6-0x4d6 has been reserved
[   30.087218] pnp: 00:01: ioport range 0xc00-0xc01 has been reserved
[   30.087221] pnp: 00:01: ioport range 0xc14-0xc14 has been reserved
[   30.087223] pnp: 00:01: ioport range 0xc50-0xc52 has been reserved
[   30.087226] pnp: 00:01: ioport range 0xc6c-0xc6d has been reserved
[   30.087229] pnp: 00:01: ioport range 0xc6f-0xc6f has been reserved
[   30.087243] pnp: 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[   30.087249] pnp: 00:0d: iomem range 0xf0000-0xf3fff could not be reserved
[   30.087252] pnp: 00:0d: iomem range 0xf4000-0xf7fff could not be reserved
[   30.087255] pnp: 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[   30.087257] pnp: 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   30.090547] Time: tsc clocksource has been installed.
[   30.117614] PCI: Bridge: 0000:00:01.0
[   30.117618]   IO window: e000-efff
[   30.117623]   MEM window: fde00000-fdefffff
[   30.117627]   PREFETCH window: d8000000-dfffffff
[   30.117632] PCI: Bridge: 0000:00:14.4
[   30.117636]   IO window: d000-dfff
[   30.117643]   MEM window: fdd00000-fddfffff
[   30.117649]   PREFETCH window: fdc00000-fdcfffff
[   30.117682] NET: Registered protocol family 2
[   30.154534] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   30.154574] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   30.154693] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   30.154765] TCP: Hash tables configured (established 16384 bind 16384)
[   30.154768] TCP reno registered
[   30.166645] checking if image is initramfs... it is
[   30.614231] Switched to high resolution mode on CPU 1
[   30.618094] Switched to high resolution mode on CPU 0
[   30.727447] Freeing initrd memory: 7066k freed
[   30.728147] audit: initializing netlink socket (disabled)
[   30.728168] audit(1201624527.516:1): initialized
[   30.730701] VFS: Disk quotas dquot_6.5.1
[   30.730767] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.730875] io scheduler noop registered
[   30.730878] io scheduler anticipatory registered
[   30.730880] io scheduler deadline registered
[   30.730896] io scheduler cfq registered (default)
[   30.730915] PCI: MSI quirk detected. MSI deactivated.
[   30.730981] Boot video device is 0000:01:05.0
[   30.731162] isapnp: Scanning for PnP cards...
[   31.082922] isapnp: No Plug & Play device found
[   31.110940] Real Time Clock Driver v1.12ac
[   31.111063] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.111204] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.111967] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.112835] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.113088] input: Macintosh mouse button emulation as /class/input/input0
[   31.113186] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   31.115970] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.115978] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.116182] mice: PS/2 mouse device common for all mice
[   31.116316] EISA: Probing bus 0 at eisa.0
[   31.116342] Cannot allocate resource for EISA slot 4
[   31.116365] EISA: Detected 0 cards.
[   31.116468] TCP cubic registered
[   31.116480] NET: Registered protocol family 1
[   31.116504] Using IPI No-Shortcut mode
[   31.116687]   Magic number: 8:873:591
[   31.116779]   hash matches device ptyc9
[   31.117301] Freeing unused kernel memory: 364k freed
[   31.140900] input: AT Translated Set 2 keyboard as /class/input/input1
[   32.309756] AppArmor: AppArmor initialized<5>audit(1201624529.016:2):  type=1505 info="AppArmor initialized" pid=1196
[   32.317917] fuse init (API version 7.8)
[   32.323498] Failure registering capabilities with primary security module.
[   32.356505] ACPI: Fan [FAN] (on)
[   32.361500] ACPI: Processor [CPU0] (supports 8 throttling states)
[   32.361655] ACPI: SSDT 1BEF6F00, 0087 (r1 ATI     Cpu1Ist     3000 INTL 20040311)
[   32.361784] ACPI: Processor [CPU1] (supports 8 throttling states)
[   32.361801] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   32.361815] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   32.365004] ACPI: Thermal Zone [THRM] (40 C)
[   32.826970] usbcore: registered new interface driver usbfs
[   32.827010] usbcore: registered new interface driver hub
[   32.827052] usbcore: registered new device driver usb
[   32.828673] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 16
[   32.828692] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   32.828939] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[   32.829005] ehci_hcd 0000:00:13.2: irq 16, io mem 0xfe02b000
[   32.829020] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.829170] usb usb1: configuration #1 chosen from 1 choice
[   32.829210] hub 1-0:1.0: USB hub found
[   32.829218] hub 1-0:1.0: 8 ports detected
[   32.860021] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   32.901206] SCSI subsystem initialized
[   32.909600] libata version 2.21 loaded.
[   32.963312] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 16
[   32.963342] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   32.963403] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[   32.963433] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02d000
[   33.019974] usb usb2: configuration #1 chosen from 1 choice
[   33.020021] hub 2-0:1.0: USB hub found
[   33.020038] hub 2-0:1.0: 4 ports detected
[   33.056311] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   33.058196] Floppy drive(s): fd0 is 1.44M
[   33.075577] FDC 0 is a post-1991 82077
[   33.123862] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 16
[   33.123884] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   33.123924] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[   33.123945] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe02c000
[   33.183756] usb usb3: configuration #1 chosen from 1 choice
[   33.183800] hub 3-0:1.0: USB hub found
[   33.183813] hub 3-0:1.0: 4 ports detected
[   33.292095] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   33.292105] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
[   33.292121] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   33.292127] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[   33.292209] sata_sil 0000:00:11.0: version 2.2
[   33.292270] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 17
[   33.292402] scsi0 : sata_sil
[   33.292481] scsi1 : sata_sil
[   33.292534] ata1: SATA max UDMA/100 cmd 0xdc8a0080 ctl 0xdc8a008a bmdma 0xdc8a0000 irq 17
[   33.292541] ata2: SATA max UDMA/100 cmd 0xdc8a00c0 ctl 0xdc8a00ca bmdma 0xdc8a0008 irq 17
[   33.301162] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.301169] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.305360] 8139too Fast Ethernet driver 0.9.28
[   33.603268] ata1: SATA link down (SStatus 0 SControl 310)
[   33.723155] usb 3-2: new full speed USB device using ohci_hcd and address 2
[   33.914976] ata2: SATA link down (SStatus 0 SControl 310)
[   33.915090] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[   33.915158] scsi2 : sata_sil
[   33.915237] scsi3 : sata_sil
[   33.915284] ata3: SATA max UDMA/100 cmd 0xdc8a2080 ctl 0xdc8a208a bmdma 0xdc8a2000 irq 18
[   33.915293] ata4: SATA max UDMA/100 cmd 0xdc8a20c0 ctl 0xdc8a20ca bmdma 0xdc8a2008 irq 18
[   33.936089] usb 3-2: configuration #2 chosen from 2 choices
[   34.226687] ata3: SATA link down (SStatus 0 SControl 310)
[   34.538395] ata4: SATA link down (SStatus 0 SControl 310)
[   34.538446] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   34.538472] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[   34.538492] ATIIXP: chipset revision 128
[   34.538495] ATIIXP: not 100% native mode: will probe irqs later
[   34.538507]     ide0: BM-DMA at 0xf400-0xf407, BIOS settings: hda:pio, hdb:pio
[   34.538525]     ide1: BM-DMA at 0xf408-0xf40f, BIOS settings: hdc:pio, hdd:pio
[   34.538539] Probing IDE interface ide0...
[   35.274148] hda: HL-DT-ST GCE-8527B, ATAPI CD/DVD-ROM drive
[   35.945107] hda: selected mode 0x42
[   35.965195] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   35.977908] Probing IDE interface ide1...
[   36.265221] hdc: ST3802110A, ATA DISK drive
[   36.936181] hdc: selected mode 0x45
[   36.936415] ide1 at 0x170-0x177,0x376 on irq 15
[   36.938321] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 21 (level, low) -> IRQ 20
[   36.939763] eth0: RealTek RTL8139 at 0xdc854000, 00:16:76:0c:22:0c, IRQ 20
[   36.939766] eth0:  Identified 8139 chip type 'RTL-8101'
[   36.939800] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 16 (level, low) -> IRQ 19
[   36.940524] eth1: RealTek RTL8139 at 0xdc85c000, 00:01:0a:11:36:6f, IRQ 19
[   36.940528] eth1:  Identified 8139 chip type 'RTL-8139C'
[   36.948846] hdc: max request size: 512KiB
[   36.957487] hda: ATAPI 52X CD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[   36.957497] Uniform CD-ROM driver Revision: 3.20
[   36.991600] hdc: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   37.016025] hdc: cache flushes supported
[   37.016064]  hdc: hdc1 hdc2 < hdc5 hdc6 hdc7 hdc8 hdc9 >
[   37.603437] Attempting manual resume
[   37.603442] swsusp: Resume From Partition 22:5
[   37.603444] PM: Checking swsusp image.
[   37.603631] PM: Resume from disk failed.
[   37.625711] kjournald starting.  Commit interval 5 seconds
[   37.625726] EXT3-fs: mounted filesystem with ordered data mode.
[   42.418544] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   43.688270] Linux agpgart interface v0.102 (c) Dave Jones
[   43.757110] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.759429] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.102603] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   44.138525] input: PC Speaker as /class/input/input2
[   44.734983] eth2: register 'cdc_ether' at usb-0000:00:13.1-2, CDC Ethernet Device, 00:0f:a3:6d:dc:ca
[   44.735006] usbcore: registered new interface driver cdc_ether
[   44.879708] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 19
[   45.069565] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   45.072224] parport_pc 00:09: reported by Plug and Play ACPI
[   45.072312] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   46.236944] lp0: using parport0 (interrupt-driven).
[   46.318388] Adding 1036152k swap on /dev/hdc5.  Priority:-1 extents:1 across:1036152k
[   46.741068] EXT3 FS on hdc9, internal journal
[  142.317686] input: Power Button (FF) as /class/input/input4
[  142.317722] ACPI: Power Button (FF) [PWRF]
[  142.317786] input: Power Button (CM) as /class/input/input5
[  142.317814] ACPI: Power Button (CM) [PWRB]
[  142.452079] No dock devices found.
[  146.415345] eth0: link down
[  147.440634] Failure registering capabilities with primary security module.
[  148.204265] ppdev: user-space parallel port driver
[  148.827420] audit(1201604846.431:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4979 profile="/usr/sbin/cupsd"
[  151.291046] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  151.291053] apm: disabled - APM is not SMP safe.
[  154.547109] Failure registering capabilities with primary security module.
[  156.223068] Bluetooth: Core ver 2.11
[  156.223540] NET: Registered protocol family 31
[  156.223549] Bluetooth: HCI device and connection manager initialized
[  156.223556] Bluetooth: HCI socket layer initialized
[  156.323505] Bluetooth: L2CAP ver 2.8
[  156.323513] Bluetooth: L2CAP socket layer initialized
[  156.474932] Bluetooth: RFCOMM socket layer initialized
[  156.475337] Bluetooth: RFCOMM TTY layer initialized
[  156.475344] Bluetooth: RFCOMM ver 1.8
[  167.222982] hda-intel: Invalid position buffer, using LPIB read method instead.
[  924.774877] Clocksource tsc unstable (delta = 112478942256 ns)
[  924.775460] Time: acpi_pm clocksource has been installed.
 
```

Regards
Shivcharan.

---

### Post by shivcharan on 2008-01-31
> **ajmorris said:**
> Hi there, 
could you please give the following details:
```
sudo lspci
```
Upload /var/log/syslog
and:
```
dmesg
```
and upload:
```
/var/log/Xorg.0.log
```

AJ

Hi ajmorris,

Do you get solution?
Are you download my log files?
If not please refer post #3
I am waiting for your response:confused:

---

### Post by dstew on 2008-01-31
This may be a kernel bug. What is your hardware?

---

### Post by CheAziz on 2008-02-01
Hi,

I am also having the same problem...

Output for the sudo lspci command is:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Proces
sor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Exp
ress Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Gr
aphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US
B UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US
B UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                            B UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                            B UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                            B2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (IC                                            H6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem                                             Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev                                             03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE                                             Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contr                                            oller (rev 03)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connec                                            tion (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Co                                            ntroller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

I will appreciate your help...

---

### Post by shivcharan on 2008-02-01
> **dstew said:**
> This may be a kernel bug. What is your hardware?

Hi dstew,

Configuration of my PC is ```
 P4 3GHz, Intel motherboard with 500Mb ram 
, 2 ethernet plus 1usb port of ADSL modem from Huawi - SmartAx MT841
```

---

### Post by SBFC on 2008-02-02
I'm actually getting the same message when choosing 'Rescue a broken system' from the alternate install cd.

Put my drives in a completely new system and was going to see if I could get everything working without reinstalling but this error won't let me do anything. Just sits there.

---

### Post by SBFC on 2008-02-02
I updated by BIOS to the newest version and everything works! My new MOBO is an Asus M2A-VM HDMI. Came with v0502 of the BIOS and I updated to v1605. 

I'm actually very relieved everything works. I put together a new system and replaced everything but my drives and gpu and I thought Ubuntu would complain. But after updating my BIOS everything started up without a hitch...

---

