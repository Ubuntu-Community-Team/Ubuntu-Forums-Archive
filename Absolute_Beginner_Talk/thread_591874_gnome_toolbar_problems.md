---
title: "gnome toolbar problems"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by cmittle on 2007-10-25
When I start up my laptop about 2 out of three times it loads my desktop picture, but the two toolbars wont load.  I've tried alt+F1 that doesn't activate any menus.  I've also tried alt+F2, and nothing happens.  I'm not familiar with many more desktop keyboard shortcuts so that's all I've tried.  If I restart using alt+ctrl+bksp my issue will not be resolved so I have to hold down the power button to shut off my laptop then press it again and start it up.  I tried starting up in failsafe Gnome and this doesn't typically help, at least not the first time.

Any direction in where to look so I can diagnose this problem, or any ideas on what may have caused this and how to fix it would be appreciated.

Thank you,
Cory

---

### Post by swoll1980 on 2007-10-26
Try clicking your mouse where the panal is supposed to be this worked for me when this happend and the panals apeared as soon as I clicked

---

### Post by cmittle on 2007-10-26
I've tried clicking around and nothing happens.

Thanks,
Cory

---

### Post by cmittle on 2007-10-28
Anybody else have an idea what could be causing this problem or how to repair it.  I noticed tonight when it finally did boot up I heard the music during start up.  I don't think that I've heard this music any of the times that it has been failing.  I don't know if that is associated with a certain component that isn't loading right.

Thank you,
Cory

---

### Post by cmittle on 2007-10-31
I managed to find the logs and this is what I've found.  This appears to be the logging from me trying to start my computer in the last few days.  I have noticed that after I type my log in information if I hear the music it has worked.  If after I type my log in information I hear no music, it will still carry on to load my background picture, but clicking and keyboard shortcuts get me no response.  Please let me know if any one has any ideas.

```
Oct 28 19:09:48 cory-laptop syslogd 1.4.1#21ubuntu3: restart.
Oct 28 19:12:55 cory-laptop kernel: [  833.804000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:12:55 cory-laptop kernel: [  833.804000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:12:56 cory-laptop kernel: [  834.552000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:12:56 cory-laptop kernel: [  835.304000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:12:59 cory-laptop kernel: [  838.060000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:13:00 cory-laptop kernel: [  838.808000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:13:01 cory-laptop kernel: [  839.560000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:13:04 cory-laptop kernel: [  842.316000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:13:04 cory-laptop kernel: [  842.316000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:13:04 cory-laptop kernel: [  843.064000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:13:05 cory-laptop kernel: [  843.816000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:13:08 cory-laptop kernel: [  846.572000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:13:08 cory-laptop kernel: [  847.320000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:13:09 cory-laptop kernel: [  848.072000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:15:26 cory-laptop kernel: [  985.152000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:15:26 cory-laptop kernel: [  985.156000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:15:26 cory-laptop kernel: [  985.160000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:15:26 cory-laptop kernel: [  985.164000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:15:26 cory-laptop kernel: [  985.168000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:15:26 cory-laptop kernel: [  985.172000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:15:26 cory-laptop kernel: [  985.176000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:15:26 cory-laptop kernel: [  985.176000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:15:26 cory-laptop kernel: [  985.180000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:15:26 cory-laptop kernel: [  985.184000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:18:28 cory-laptop kernel: [ 1166.424000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:18:32 cory-laptop kernel: [ 1170.420000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:18:40 cory-laptop kernel: [ 1178.508000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:18:40 cory-laptop kernel: [ 1179.252000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:18:41 cory-laptop kernel: [ 1179.896000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:18:41 cory-laptop kernel: [ 1180.004000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:25 cory-laptop kernel: [ 1583.916000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:25 cory-laptop kernel: [ 1583.916000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:26 cory-laptop kernel: [ 1584.664000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:27 cory-laptop kernel: [ 1585.416000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:31 cory-laptop kernel: [ 1588.168000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:31 cory-laptop kernel: [ 1588.168000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:31 cory-laptop kernel: [ 1588.916000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:34 cory-laptop kernel: [ 1592.424000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:34 cory-laptop kernel: [ 1592.424000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:34 cory-laptop kernel: [ 1593.172000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:35 cory-laptop kernel: [ 1593.924000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:38 cory-laptop kernel: [ 1596.680000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:39 cory-laptop kernel: [ 1597.428000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:41 cory-laptop kernel: [ 1598.180000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 28 19:25:45 cory-laptop exiting on signal 15
Oct 29 19:04:54 cory-laptop syslogd 1.4.1#21ubuntu3: restart.
Oct 29 19:04:54 cory-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Oct 29 19:04:54 cory-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Oct 29 19:04:54 cory-laptop kernel: Symbols match kernel version 2.6.22.
Oct 29 19:04:54 cory-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002ef40000 (usable)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000002ef40000 - 000000002ef50000 (ACPI data)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000002ef50000 - 000000002f000000 (reserved)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] 751MB LOWMEM available.
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] Zone PFN ranges:
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]   DMA             0 ->     4096
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]   Normal       4096 ->   192320
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]   HighMem    192320 ->   192320
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 29 19:04:54 cory-laptop kernel: [    0.000000]     0:        0 ->   192320
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] DMI 2.3 present.
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F0180 checksum 0
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] ACPI: RSDP 000F0180, 0014 (r0 TOSHIB)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] ACPI: RSDT 2EF40000, 0030 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] ACPI: FACP 2EF40058, 0084 (r2 TOSHIB 750        970814 TASM  4010000)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] ACPI: DSDT 2EF40110, 4B25 (r1 TOSHIB AFCF7    20030326 MSFT  100000E)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] ACPI: FACS 000EEE00, 0040
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] ACPI: DBGP 2EF400DC, 0034 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] ACPI: BOOT 2EF40030, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xd808
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f000000:cfc10000)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 190818
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] Kernel command line: root=UUID=e6f50239-1aea-4ce9-bff6-f65118a4cdb9 ro quiet splash
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] Initializing CPU#0
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 29 19:04:54 cory-laptop kernel: [    0.000000] Detected 2394.027 MHz processor.
Oct 29 19:04:54 cory-laptop kernel: [    7.575530] Console: colour VGA+ 80x25
Oct 29 19:04:54 cory-laptop kernel: [    7.576218] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 29 19:04:54 cory-laptop kernel: [    7.577275] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 29 19:04:54 cory-laptop kernel: [    7.596313] Memory: 750860k/769280k available (2015k kernel code, 17808k reserved, 916k data, 364k init, 0k highmem)
Oct 29 19:04:54 cory-laptop kernel: [    7.596325] virtual kernel memory layout:
Oct 29 19:04:54 cory-laptop kernel: [    7.596326]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Oct 29 19:04:54 cory-laptop kernel: [    7.596328]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 29 19:04:54 cory-laptop kernel: [    7.596329]     vmalloc : 0xef800000 - 0xff7fe000   ( 255 MB)
Oct 29 19:04:54 cory-laptop kernel: [    7.596330]     lowmem  : 0xc0000000 - 0xeef40000   ( 751 MB)
Oct 29 19:04:54 cory-laptop kernel: [    7.596331]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Oct 29 19:04:54 cory-laptop kernel: [    7.596333]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Oct 29 19:04:54 cory-laptop kernel: [    7.596334]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Oct 29 19:04:54 cory-laptop kernel: [    7.596337] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 29 19:04:54 cory-laptop kernel: [    7.596382] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 29 19:04:54 cory-laptop kernel: [    7.676273] Calibrating delay using timer specific routine.. 4792.20 BogoMIPS (lpj=9584407)
Oct 29 19:04:54 cory-laptop kernel: [    7.676304] Security Framework v1.0.0 initialized
Oct 29 19:04:54 cory-laptop kernel: [    7.676313] SELinux:  Disabled at boot.
Oct 29 19:04:54 cory-laptop kernel: [    7.676328] Mount-cache hash table entries: 512
Oct 29 19:04:54 cory-laptop kernel: [    7.676510] CPU: Trace cache: 12K uops, L1 D cache: 8K
Oct 29 19:04:54 cory-laptop kernel: [    7.676513] CPU: L2 cache: 256K
Oct 29 19:04:54 cory-laptop kernel: [    7.676516] CPU: Hyper-Threading is disabled
Oct 29 19:04:54 cory-laptop kernel: [    7.676533] Compat vDSO mapped to ffffe000.
Oct 29 19:04:54 cory-laptop kernel: [    7.676549] Checking 'hlt' instruction... OK.
Oct 29 19:04:54 cory-laptop kernel: [    7.692379] SMP alternatives: switching to UP code
Oct 29 19:04:54 cory-laptop kernel: [    7.692699] Freeing SMP alternatives: 11k freed
Oct 29 19:04:54 cory-laptop kernel: [    7.693061] Early unpacking initramfs... done
Oct 29 19:04:54 cory-laptop kernel: [    8.034486] ACPI: Core revision 20070126
Oct 29 19:04:54 cory-laptop kernel: [    8.034561] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 29 19:04:54 cory-laptop kernel: [    8.036385] ACPI: setting ELCR to 0200 (from 0e00)
Oct 29 19:04:54 cory-laptop kernel: [    8.036543] CPU0: Intel Mobile Intel(R) Celeron(R) CPU 2.40GHz stepping 09
Oct 29 19:04:54 cory-laptop kernel: [    8.036551] SMP motherboard not detected.
Oct 29 19:04:54 cory-laptop kernel: [    8.036554] Local APIC not detected. Using dummy APIC emulation.
Oct 29 19:04:54 cory-laptop kernel: [    8.036600] Brought up 1 CPUs
Oct 29 19:04:54 cory-laptop kernel: [    8.036769] Booting paravirtualized kernel on bare hardware
Oct 29 19:04:54 cory-laptop kernel: [    8.036840] Time:  0:04:28  Date: 09/30/107
Oct 29 19:04:54 cory-laptop kernel: [    8.036876] NET: Registered protocol family 16
Oct 29 19:04:54 cory-laptop kernel: [    8.037024] EISA bus registered
Oct 29 19:04:54 cory-laptop kernel: [    8.037042] ACPI: bus type pci registered
Oct 29 19:04:54 cory-laptop kernel: [    8.037154] PCI: PCI BIOS revision 2.10 entry at 0xfd317, last bus=3
Oct 29 19:04:54 cory-laptop kernel: [    8.037157] PCI: Using configuration type 1
Oct 29 19:04:54 cory-laptop kernel: [    8.037158] Setting up standard PCI resources
Oct 29 19:04:54 cory-laptop kernel: [    8.042673] ACPI: Interpreter enabled
Oct 29 19:04:54 cory-laptop kernel: [    8.042679] ACPI: (supports S0 S3 S4 S5)
Oct 29 19:04:54 cory-laptop kernel: [    8.042702] ACPI: Using PIC for interrupt routing
Oct 29 19:04:54 cory-laptop kernel: [    8.051089] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 29 19:04:54 cory-laptop kernel: [    8.051608] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
Oct 29 19:04:54 cory-laptop kernel: [    8.051613] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
Oct 29 19:04:54 cory-laptop kernel: [    8.051938] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
Oct 29 19:04:54 cory-laptop kernel: [    8.052041] PCI: Transparent bridge - 0000:00:1e.0
Oct 29 19:04:54 cory-laptop kernel: [    8.054196] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
Oct 29 19:04:54 cory-laptop kernel: [    8.054323] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
Oct 29 19:04:54 cory-laptop kernel: [    8.054446] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
Oct 29 19:04:54 cory-laptop kernel: [    8.054570] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
Oct 29 19:04:54 cory-laptop kernel: [    8.054701] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
Oct 29 19:04:54 cory-laptop kernel: [    8.054828] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
Oct 29 19:04:54 cory-laptop kernel: [    8.054954] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
Oct 29 19:04:54 cory-laptop kernel: [    8.055077] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
Oct 29 19:04:54 cory-laptop kernel: [    8.055428] ACPI: Power Resource [PFAN] (off)
Oct 29 19:04:54 cory-laptop kernel: [    8.055449] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 29 19:04:54 cory-laptop kernel: [    8.055473] pnp: PnP ACPI init
Oct 29 19:04:54 cory-laptop kernel: [    8.055489] ACPI: bus type pnp registered
Oct 29 19:04:54 cory-laptop kernel: [    8.059016] pnp: PnP ACPI: found 10 devices
Oct 29 19:04:54 cory-laptop kernel: [    8.059021] ACPI: ACPI bus type pnp unregistered
Oct 29 19:04:54 cory-laptop kernel: [    8.059027] PnPBIOS: Disabled by ACPI PNP
Oct 29 19:04:54 cory-laptop kernel: [    8.059111] PCI: Using ACPI for IRQ routing
Oct 29 19:04:54 cory-laptop kernel: [    8.059116] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 29 19:04:54 cory-laptop kernel: [    8.063683] NET: Registered protocol family 8
Oct 29 19:04:54 cory-laptop kernel: [    8.063686] NET: Registered protocol family 20
Oct 29 19:04:54 cory-laptop kernel: [    8.063823] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
Oct 29 19:04:54 cory-laptop kernel: [    8.063828] pnp: 00:00: iomem range 0xe0000-0xeffff could not be reserved
Oct 29 19:04:54 cory-laptop kernel: [    8.063832] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
Oct 29 19:04:54 cory-laptop kernel: [    8.063835] pnp: 00:00: iomem range 0x100000-0x2ef3ffff could not be reserved
Oct 29 19:04:54 cory-laptop kernel: [    8.067623] Time: tsc clocksource has been installed.
Oct 29 19:04:54 cory-laptop kernel: [    8.094396] PCI: Bus 2, cardbus bridge: 0000:01:0b.0
Oct 29 19:04:54 cory-laptop kernel: [    8.094400]   IO window: 0000c000-0000c0ff
Oct 29 19:04:54 cory-laptop kernel: [    8.094404]   IO window: 0000c400-0000c4ff
Oct 29 19:04:54 cory-laptop kernel: [    8.094410]   PREFETCH window: 38000000-3bffffff
Oct 29 19:04:54 cory-laptop kernel: [    8.094415]   MEM window: 40000000-43ffffff
Oct 29 19:04:54 cory-laptop kernel: [    8.094420] PCI: Bridge: 0000:00:1e.0
Oct 29 19:04:54 cory-laptop kernel: [    8.094423]   IO window: c000-cfff
Oct 29 19:04:54 cory-laptop kernel: [    8.094429]   MEM window: cff00000-cfffffff
Oct 29 19:04:54 cory-laptop kernel: [    8.094434]   PREFETCH window: 38000000-3bffffff
Oct 29 19:04:54 cory-laptop kernel: [    8.094467] PCI: Enabling device 0000:01:0b.0 (0000 -> 0003)
Oct 29 19:04:54 cory-laptop kernel: [    8.094723] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Oct 29 19:04:54 cory-laptop kernel: [    8.094730] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:04:54 cory-laptop kernel: [    8.094758] NET: Registered protocol family 2
Oct 29 19:04:54 cory-laptop kernel: [    8.131576] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 29 19:04:54 cory-laptop kernel: [    8.131777] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Oct 29 19:04:54 cory-laptop kernel: [    8.133826] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 29 19:04:54 cory-laptop kernel: [    8.134527] TCP: Hash tables configured (established 131072 bind 65536)
Oct 29 19:04:54 cory-laptop kernel: [    8.134535] TCP reno registered
Oct 29 19:04:54 cory-laptop kernel: [    8.143699] checking if image is initramfs... it is
Oct 29 19:04:54 cory-laptop kernel: [    8.594779] Switched to high resolution mode on CPU 0
Oct 29 19:04:54 cory-laptop kernel: [    8.810607] Freeing initrd memory: 7115k freed
Oct 29 19:04:54 cory-laptop kernel: [    8.810799] Simple Boot Flag at 0x7c set to 0x1
Oct 29 19:04:54 cory-laptop kernel: [    8.811083] audit: initializing netlink socket (disabled)
Oct 29 19:04:54 cory-laptop kernel: [    8.811102] audit(1193702667.976:1): initialized
Oct 29 19:04:54 cory-laptop kernel: [    8.814067] VFS: Disk quotas dquot_6.5.1
Oct 29 19:04:54 cory-laptop kernel: [    8.814150] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 29 19:04:54 cory-laptop kernel: [    8.814345] io scheduler noop registered
Oct 29 19:04:54 cory-laptop kernel: [    8.814349] io scheduler anticipatory registered
Oct 29 19:04:54 cory-laptop kernel: [    8.814351] io scheduler deadline registered
Oct 29 19:04:54 cory-laptop kernel: [    8.814383] io scheduler cfq registered (default)
Oct 29 19:04:54 cory-laptop kernel: [    8.814664] isapnp: Scanning for PnP cards...
Oct 29 19:04:54 cory-laptop kernel: [    9.167125] isapnp: No Plug & Play device found
Oct 29 19:04:54 cory-laptop kernel: [    9.245119] Real Time Clock Driver v1.12ac
Oct 29 19:04:54 cory-laptop kernel: [    9.245269] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 29 19:04:54 cory-laptop kernel: [    9.246880] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
Oct 29 19:04:54 cory-laptop kernel: [    9.247097] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Oct 29 19:04:54 cory-laptop kernel: [    9.247101] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:04:54 cory-laptop kernel: [    9.247111] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Oct 29 19:04:54 cory-laptop kernel: [    9.248022] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 29 19:04:54 cory-laptop kernel: [    9.248361] input: Macintosh mouse button emulation as /class/input/input0
Oct 29 19:04:54 cory-laptop kernel: [    9.248490] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 29 19:04:54 cory-laptop kernel: [    9.265380] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 29 19:04:54 cory-laptop kernel: [    9.265391] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 29 19:04:54 cory-laptop kernel: [    9.265755] mice: PS/2 mouse device common for all mice
Oct 29 19:04:54 cory-laptop kernel: [    9.265949] EISA: Probing bus 0 at eisa.0
Oct 29 19:04:54 cory-laptop kernel: [    9.265958] Cannot allocate resource for EISA slot 1
Oct 29 19:04:54 cory-laptop kernel: [    9.265976] EISA: Detected 0 cards.
Oct 29 19:04:54 cory-laptop kernel: [    9.266162] TCP cubic registered
Oct 29 19:04:54 cory-laptop kernel: [    9.266181] NET: Registered protocol family 1
Oct 29 19:04:54 cory-laptop kernel: [    9.266211] Using IPI No-Shortcut mode
Oct 29 19:04:54 cory-laptop kernel: [    9.266449]   Magic number: 11:787:52
Oct 29 19:04:54 cory-laptop kernel: [    9.267143] Freeing unused kernel memory: 364k freed
Oct 29 19:04:54 cory-laptop kernel: [    9.323154] input: AT Translated Set 2 keyboard as /class/input/input1
Oct 29 19:04:54 cory-laptop kernel: [   10.569937] AppArmor: AppArmor initialized<5>audit(1193702669.976:2):  type=1505 info="AppArmor initialized" pid=1183
Oct 29 19:04:54 cory-laptop kernel: [   10.581337] fuse init (API version 7.8)
Oct 29 19:04:54 cory-laptop kernel: [   10.589390] Failure registering capabilities with primary security module.
Oct 29 19:04:54 cory-laptop kernel: [   10.601345] ACPI: Transitioning device [FAN] to D3
Oct 29 19:04:54 cory-laptop kernel: [   10.601351] ACPI: Transitioning device [FAN] to D3
Oct 29 19:04:54 cory-laptop kernel: [   10.601356] ACPI: Fan [FAN] (off)
Oct 29 19:04:54 cory-laptop kernel: [   10.608495] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct 29 19:04:54 cory-laptop kernel: [   10.609915] ACPI: Thermal Zone [THRM] (31 C)
Oct 29 19:04:54 cory-laptop kernel: [   11.482689] usbcore: registered new interface driver usbfs
Oct 29 19:04:54 cory-laptop kernel: [   11.482723] usbcore: registered new interface driver hub
Oct 29 19:04:54 cory-laptop kernel: [   11.482758] usbcore: registered new device driver usb
Oct 29 19:04:54 cory-laptop kernel: [   11.483848] USB Universal Host Controller Interface driver v3.0
Oct 29 19:04:54 cory-laptop kernel: [   11.484199] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Oct 29 19:04:54 cory-laptop kernel: [   11.484207] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 29 19:04:54 cory-laptop kernel: [   11.484225] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 29 19:04:54 cory-laptop kernel: [   11.484445] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Oct 29 19:04:54 cory-laptop kernel: [   11.484477] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018c0
Oct 29 19:04:54 cory-laptop kernel: [   11.484643] usb usb1: configuration #1 chosen from 1 choice
Oct 29 19:04:54 cory-laptop kernel: [   11.484677] hub 1-0:1.0: USB hub found
Oct 29 19:04:54 cory-laptop kernel: [   11.484688] hub 1-0:1.0: 2 ports detected
Oct 29 19:04:54 cory-laptop kernel: [   11.509144] SCSI subsystem initialized
Oct 29 19:04:54 cory-laptop kernel: [   11.570776] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
Oct 29 19:04:54 cory-laptop kernel: [   11.570781] e100: Copyright(c) 1999-2006 Intel Corporation
Oct 29 19:04:54 cory-laptop kernel: [   11.595015] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Oct 29 19:04:54 cory-laptop kernel: [   11.595020] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:04:54 cory-laptop kernel: [   11.595206] scsi0 : ata_piix
Oct 29 19:04:54 cory-laptop kernel: [   11.595280] scsi1 : ata_piix
Oct 29 19:04:54 cory-laptop kernel: [   11.595436] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Oct 29 19:04:54 cory-laptop kernel: [   11.595441] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Oct 29 19:04:54 cory-laptop kernel: [   11.757586] ata1.00: ATA-6: IC25N040ATMR04-0, MO2OAD0A, max UDMA/100
Oct 29 19:04:54 cory-laptop kernel: [   11.757591] ata1.00: 78140160 sectors, multi 0: LBA48 
Oct 29 19:04:54 cory-laptop kernel: [   11.773519] ata1.00: configured for UDMA/100
Oct 29 19:04:54 cory-laptop kernel: [   11.825009] usb 1-2: new low speed USB device using uhci_hcd and address 2
Oct 29 19:04:54 cory-laptop kernel: [    4.256000] Marking TSC unstable due to: possible TSC halt in C2.
Oct 29 19:04:54 cory-laptop kernel: [    4.260000] Time: acpi_pm clocksource has been installed.
Oct 29 19:04:54 cory-laptop kernel: [    4.440000] usb 1-2: configuration #1 chosen from 1 choice
Oct 29 19:04:54 cory-laptop kernel: [    4.460000] usbcore: registered new interface driver hiddev
Oct 29 19:04:54 cory-laptop kernel: [    4.500000] input: HID 1241:1166 as /class/input/input2
Oct 29 19:04:54 cory-laptop kernel: [    4.500000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:1d.0-2
Oct 29 19:04:54 cory-laptop kernel: [    4.500000] usbcore: registered new interface driver usbhid
Oct 29 19:04:54 cory-laptop kernel: [    4.500000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 29 19:04:54 cory-laptop kernel: [    4.512000] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R2412, 1330, max UDMA/33
Oct 29 19:04:54 cory-laptop kernel: [    4.684000] ata2.00: configured for UDMA/33
Oct 29 19:04:54 cory-laptop kernel: [    4.684000] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATMR04-0 MO2O PQ: 0 ANSI: 5
Oct 29 19:04:54 cory-laptop kernel: [    4.700000] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2412 1330 PQ: 0 ANSI: 5
Oct 29 19:04:54 cory-laptop kernel: [    4.700000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Oct 29 19:04:54 cory-laptop kernel: [    4.700000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Oct 29 19:04:54 cory-laptop kernel: [    4.700000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:04:54 cory-laptop kernel: [    4.700000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 29 19:04:54 cory-laptop kernel: [    4.700000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Oct 29 19:04:54 cory-laptop kernel: [    4.700000] ehci_hcd 0000:00:1d.7: debug port 1
Oct 29 19:04:54 cory-laptop kernel: [    4.700000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x3c080000
Oct 29 19:04:54 cory-laptop kernel: [    4.704000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 29 19:04:54 cory-laptop kernel: [    4.704000] usb usb2: configuration #1 chosen from 1 choice
Oct 29 19:04:54 cory-laptop kernel: [    4.704000] hub 2-0:1.0: USB hub found
Oct 29 19:04:54 cory-laptop kernel: [    4.704000] hub 2-0:1.0: 6 ports detected
Oct 29 19:04:54 cory-laptop kernel: [    4.728000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Oct 29 19:04:54 cory-laptop kernel: [    4.728000] sd 0:0:0:0: [sda] Write Protect is off
Oct 29 19:04:54 cory-laptop kernel: [    4.728000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 29 19:04:54 cory-laptop kernel: [    4.728000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Oct 29 19:04:54 cory-laptop kernel: [    4.728000] sd 0:0:0:0: [sda] Write Protect is off
Oct 29 19:04:54 cory-laptop kernel: [    4.728000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 29 19:04:54 cory-laptop kernel: [    4.728000]  sda:<6>usb 1-2: USB disconnect, address 2
Oct 29 19:04:54 cory-laptop kernel: [    4.756000]  sda1 sda2 < sda5 >
Oct 29 19:04:54 cory-laptop kernel: [    4.784000] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 29 19:04:54 cory-laptop kernel: [    4.792000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 29 19:04:54 cory-laptop kernel: [    4.792000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Oct 29 19:04:54 cory-laptop kernel: [    4.808000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
Oct 29 19:04:54 cory-laptop kernel: [    4.808000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:04:54 cory-laptop kernel: [    4.832000] e100: eth0: e100_probe: addr 0xcffff000, irq 11, MAC addr 00:08:0D:2F:C7:65
Oct 29 19:04:54 cory-laptop kernel: [    4.900000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Oct 29 19:04:54 cory-laptop kernel: [    4.900000] Uniform CD-ROM driver Revision: 3.20
Oct 29 19:04:54 cory-laptop kernel: [    5.108000] Attempting manual resume
Oct 29 19:04:54 cory-laptop kernel: [    5.172000] kjournald starting.  Commit interval 5 seconds
Oct 29 19:04:54 cory-laptop kernel: [    5.172000] EXT3-fs: mounted filesystem with ordered data mode.
Oct 29 19:04:54 cory-laptop kernel: [    5.500000] usb 1-2: new low speed USB device using uhci_hcd and address 3
Oct 29 19:04:54 cory-laptop kernel: [    5.696000] usb 1-2: configuration #1 chosen from 1 choice
Oct 29 19:04:54 cory-laptop kernel: [    5.744000] input: HID 1241:1166 as /class/input/input3
Oct 29 19:04:54 cory-laptop kernel: [    5.744000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:1d.0-2
Oct 29 19:04:54 cory-laptop kernel: [   19.524000] Linux agpgart interface v0.102 (c) Dave Jones
Oct 29 19:04:54 cory-laptop kernel: [   19.532000] agpgart: Detected an Intel 855GM Chipset.
Oct 29 19:04:54 cory-laptop kernel: [   19.532000] agpgart: Detected 16252K stolen memory.
Oct 29 19:04:54 cory-laptop kernel: [   19.540000] agpgart: AGP aperture is 128M @ 0xd8000000
Oct 29 19:04:54 cory-laptop kernel: [   19.844000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 29 19:04:54 cory-laptop kernel: [   19.888000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 29 19:04:54 cory-laptop kernel: [   20.528000] input: PC Speaker as /class/input/input4
Oct 29 19:04:54 cory-laptop kernel: [   20.552000] Yenta: CardBus bridge found at 0000:01:0b.0 [1179:0001]
Oct 29 19:04:54 cory-laptop kernel: [   20.680000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
Oct 29 19:04:54 cory-laptop kernel: [   20.680000] Socket status: 30000020
Oct 29 19:04:54 cory-laptop kernel: [   20.680000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
Oct 29 19:04:54 cory-laptop kernel: [   20.680000] cs: IO port probe 0xc000-0xcfff: clean.
Oct 29 19:04:54 cory-laptop kernel: [   20.680000] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xcfffffff
Oct 29 19:04:54 cory-laptop kernel: [   20.680000] pcmcia: parent PCI bridge Memory window: 0x38000000 - 0x3bffffff
Oct 29 19:04:54 cory-laptop kernel: [   20.772000] iTCO_vendor_support: vendor-support=0
Oct 29 19:04:54 cory-laptop kernel: [   20.772000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Oct 29 19:04:54 cory-laptop kernel: [   21.116000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
Oct 29 19:04:54 cory-laptop kernel: [   21.116000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:04:54 cory-laptop kernel: [   21.324000] pccard: CardBus card inserted into slot 0
Oct 29 19:04:54 cory-laptop kernel: [   21.344000] input: PS/2 Mouse as /class/input/input5
Oct 29 19:04:54 cory-laptop kernel: [   21.380000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
Oct 29 19:04:54 cory-laptop kernel: [   21.380000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Oct 29 19:04:54 cory-laptop kernel: [   21.380000] cs: IO port probe 0x820-0x8ff: clean.
Oct 29 19:04:54 cory-laptop kernel: [   21.380000] cs: IO port probe 0xc00-0xcf7: clean.
Oct 29 19:04:54 cory-laptop kernel: [   21.380000] cs: IO port probe 0xa00-0xaff: clean.
Oct 29 19:04:54 cory-laptop kernel: [   21.388000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input6
Oct 29 19:04:54 cory-laptop kernel: [   21.400000] pnp: Device 00:09 activated.
Oct 29 19:04:54 cory-laptop kernel: [   21.400000] parport_pc 00:09: reported by Plug and Play ACPI
Oct 29 19:04:54 cory-laptop kernel: [   21.400000] pnp: Device 00:09 disabled.
Oct 29 19:04:54 cory-laptop kernel: [   21.408000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0xd860)
Oct 29 19:04:54 cory-laptop kernel: [   21.408000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Oct 29 19:04:54 cory-laptop kernel: [   21.540000] intel8x0_measure_ac97_clock: measured 54907 usecs
Oct 29 19:04:54 cory-laptop kernel: [   21.540000] intel8x0: clocking to 48000
Oct 29 19:04:54 cory-laptop kernel: [   21.684000] acx: Loaded combined PCI/USB driver, firmware_ver=default
Oct 29 19:04:54 cory-laptop kernel: [   21.684000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Oct 29 19:04:54 cory-laptop kernel: [   21.688000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Oct 29 19:04:54 cory-laptop kernel: [   21.688000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:04:54 cory-laptop kernel: [   21.688000] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x40020000, phymem2:0x40000000, mem1:0xefab4000, mem1_size:8192, mem2:0xefb80000, mem2_size:131072
Oct 29 19:04:54 cory-laptop kernel: [   21.688000] acx: loading firmware for acx1111 chipset with radio ID 16
Oct 29 19:04:54 cory-laptop kernel: [   22.544000] NVS_vendor_offs:0221 probe_delay:200 eof_memory:1114112
Oct 29 19:04:54 cory-laptop kernel: [   22.544000] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
Oct 29 19:04:54 cory-laptop kernel: [   22.544000] AntennaID:00 Len:02 Data:01 02 
Oct 29 19:04:54 cory-laptop kernel: [   22.544000] PowerLevelID:01 Len:02 Data:001E 000A 
Oct 29 19:04:54 cory-laptop kernel: [   22.544000] DataRatesID:02 Len:05 Data:02 04 11 22 44 
Oct 29 19:04:54 cory-laptop kernel: [   22.544000] DomainID:03 Len:06 Data:10 20 30 31 32 40 
Oct 29 19:04:54 cory-laptop kernel: [   22.544000] ProductID:04 Len:09 Data:TI ACX100
Oct 29 19:04:54 cory-laptop kernel: [   22.544000] ManufacturerID:05 Len:07 Data:TI Test
Oct 29 19:04:54 cory-laptop kernel: [   22.604000] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
Oct 29 19:04:54 cory-laptop kernel: [   22.604000] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.22-14-generic
Oct 29 19:04:54 cory-laptop kernel: [   22.604000] usbcore: registered new interface driver acx_usb
Oct 29 19:04:54 cory-laptop kernel: [   23.252000] lp: driver loaded but no devices found
Oct 29 19:04:54 cory-laptop kernel: [   23.312000] Adding 698788k swap on /dev/sda5.  Priority:-1 extents:1 across:698788k
Oct 29 19:04:54 cory-laptop kernel: [   23.696000] EXT3 FS on sda1, internal journal
Oct 29 19:04:54 cory-laptop kernel: [   24.264000] NET: Registered protocol family 17
Oct 29 19:04:54 cory-laptop kernel: [   25.404000] ACPI: Battery Slot [BAT1] (battery present)
Oct 29 19:04:54 cory-laptop kernel: [   25.652000] No dock devices found.
Oct 29 19:04:54 cory-laptop kernel: [   25.684000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
Oct 29 19:04:54 cory-laptop kernel: [   25.684000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
Oct 29 19:04:54 cory-laptop kernel: [   25.688000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
Oct 29 19:04:54 cory-laptop kernel: [   25.688000] toshiba_acpi: ktoshkeyd will check 2 times per second
Oct 29 19:04:54 cory-laptop kernel: [   25.692000] toshiba_acpi: Dropped 0 keys from the queue on startup
Oct 29 19:04:54 cory-laptop kernel: [   25.716000] ACPI: AC Adapter [ADP1] (on-line)
Oct 29 19:04:54 cory-laptop kernel: [   25.776000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
Oct 29 19:04:54 cory-laptop kernel: [   25.848000] input: Power Button (FF) as /class/input/input7
Oct 29 19:04:54 cory-laptop kernel: [   25.852000] ACPI: Power Button (FF) [PWRF]
Oct 29 19:04:54 cory-laptop kernel: [   25.896000] input: Lid Switch as /class/input/input8
Oct 29 19:04:54 cory-laptop kernel: [   25.900000] ACPI: Lid Switch [LID]
Oct 29 19:04:54 cory-laptop kernel: [   25.940000] input: Power Button (CM) as /class/input/input9
Oct 29 19:04:54 cory-laptop kernel: [   25.948000] ACPI: Power Button (CM) [PWRB]
Oct 29 19:04:55 cory-laptop kernel: [   27.480000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:04:55 cory-laptop kernel: [   27.672000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Oct 29 19:04:55 cory-laptop kernel: [   27.672000] Intel ICH Modem: probe of 0000:00:1f.6 failed with error -13
Oct 29 19:04:59 cory-laptop kernel: [   31.440000] NET: Registered protocol family 10
Oct 29 19:04:59 cory-laptop kernel: [   31.440000] lo: Disabled Privacy Extensions
Oct 29 19:04:59 cory-laptop kernel: [   31.440000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 29 19:04:59 cory-laptop kernel: [   31.624000] wlan0: duplicate address detected!
Oct 29 19:05:07 cory-laptop kernel: [   40.080000] [drm] Initialized drm 1.1.0 20060810
Oct 29 19:05:08 cory-laptop kernel: [   40.124000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 29 19:05:08 cory-laptop kernel: [   40.128000] [drm] Initialized i915 1.6.0 20060119 on minor 0
Oct 29 19:05:08 cory-laptop kernel: [   40.128000] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
Oct 29 19:05:08 cory-laptop kernel: [   40.132000] [drm] Initialized i915 1.6.0 20060119 on minor 1
Oct 29 19:05:08 cory-laptop kernel: [   40.664000] ppdev: user-space parallel port driver
Oct 29 19:05:09 cory-laptop kernel: [   41.216000] audit(1193702708.654:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4912 profile="/usr/sbin/cupsd"
Oct 29 19:05:09 cory-laptop kernel: [   41.328000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
Oct 29 19:05:09 cory-laptop kernel: [   41.328000] apm: overridden by ACPI.
Oct 29 19:05:09 cory-laptop kernel: [   41.880000] Failure registering capabilities with primary security module.
Oct 29 19:05:09 cory-laptop dhcdbd: Started up.
Oct 29 19:05:10 cory-laptop kernel: [   42.252000] Bluetooth: Core ver 2.11
Oct 29 19:05:10 cory-laptop kernel: [   42.252000] NET: Registered protocol family 31
Oct 29 19:05:10 cory-laptop kernel: [   42.252000] Bluetooth: HCI device and connection manager initialized
Oct 29 19:05:10 cory-laptop kernel: [   42.252000] Bluetooth: HCI socket layer initialized
Oct 29 19:05:10 cory-laptop kernel: [   42.292000] Bluetooth: L2CAP ver 2.8
Oct 29 19:05:10 cory-laptop kernel: [   42.292000] Bluetooth: L2CAP socket layer initialized
Oct 29 19:05:10 cory-laptop kernel: [   42.300000] Bluetooth: RFCOMM socket layer initialized
Oct 29 19:05:10 cory-laptop kernel: [   42.300000] Bluetooth: RFCOMM TTY layer initialized
Oct 29 19:05:10 cory-laptop kernel: [   42.300000] Bluetooth: RFCOMM ver 1.8
Oct 29 19:05:16 cory-laptop kernel: [   48.704000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:06:09 cory-laptop exiting on signal 15
Oct 29 19:07:06 cory-laptop syslogd 1.4.1#21ubuntu3: restart.
Oct 29 19:07:07 cory-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Oct 29 19:07:07 cory-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Oct 29 19:07:07 cory-laptop kernel: Symbols match kernel version 2.6.22.
Oct 29 19:07:07 cory-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002ef40000 (usable)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000002ef40000 - 000000002ef50000 (ACPI data)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000002ef50000 - 000000002f000000 (reserved)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] 751MB LOWMEM available.
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] Zone PFN ranges:
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]   DMA             0 ->     4096
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]   Normal       4096 ->   192320
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]   HighMem    192320 ->   192320
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 29 19:07:07 cory-laptop kernel: [    0.000000]     0:        0 ->   192320
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] DMI 2.3 present.
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F0180 checksum 0
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] ACPI: RSDP 000F0180, 0014 (r0 TOSHIB)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] ACPI: RSDT 2EF40000, 0030 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] ACPI: FACP 2EF40058, 0084 (r2 TOSHIB 750        970814 TASM  4010000)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] ACPI: DSDT 2EF40110, 4B25 (r1 TOSHIB AFCF7    20030326 MSFT  100000E)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] ACPI: FACS 000EEE00, 0040
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] ACPI: DBGP 2EF400DC, 0034 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] ACPI: BOOT 2EF40030, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xd808
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f000000:cfc10000)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 190818
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] Kernel command line: root=UUID=e6f50239-1aea-4ce9-bff6-f65118a4cdb9 ro quiet splash
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] Initializing CPU#0
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 29 19:07:07 cory-laptop kernel: [    0.000000] Detected 2394.135 MHz processor.
Oct 29 19:07:07 cory-laptop kernel: [    7.180064] Console: colour VGA+ 80x25
Oct 29 19:07:07 cory-laptop kernel: [    7.180752] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 29 19:07:07 cory-laptop kernel: [    7.181806] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 29 19:07:07 cory-laptop kernel: [    7.200817] Memory: 750860k/769280k available (2015k kernel code, 17808k reserved, 916k data, 364k init, 0k highmem)
Oct 29 19:07:07 cory-laptop kernel: [    7.200829] virtual kernel memory layout:
Oct 29 19:07:07 cory-laptop kernel: [    7.200830]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Oct 29 19:07:07 cory-laptop kernel: [    7.200831]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 29 19:07:07 cory-laptop kernel: [    7.200833]     vmalloc : 0xef800000 - 0xff7fe000   ( 255 MB)
Oct 29 19:07:07 cory-laptop kernel: [    7.200834]     lowmem  : 0xc0000000 - 0xeef40000   ( 751 MB)
Oct 29 19:07:07 cory-laptop kernel: [    7.200835]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Oct 29 19:07:07 cory-laptop kernel: [    7.200836]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Oct 29 19:07:07 cory-laptop kernel: [    7.200837]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Oct 29 19:07:07 cory-laptop kernel: [    7.200841] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 29 19:07:07 cory-laptop kernel: [    7.200884] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 29 19:07:07 cory-laptop kernel: [    7.280774] Calibrating delay using timer specific routine.. 4792.21 BogoMIPS (lpj=9584426)
Oct 29 19:07:07 cory-laptop kernel: [    7.280806] Security Framework v1.0.0 initialized
Oct 29 19:07:07 cory-laptop kernel: [    7.280816] SELinux:  Disabled at boot.
Oct 29 19:07:07 cory-laptop kernel: [    7.280830] Mount-cache hash table entries: 512
Oct 29 19:07:07 cory-laptop kernel: [    7.281013] CPU: Trace cache: 12K uops, L1 D cache: 8K
Oct 29 19:07:07 cory-laptop kernel: [    7.281016] CPU: L2 cache: 256K
Oct 29 19:07:07 cory-laptop kernel: [    7.281019] CPU: Hyper-Threading is disabled
Oct 29 19:07:07 cory-laptop kernel: [    7.281035] Compat vDSO mapped to ffffe000.
Oct 29 19:07:07 cory-laptop kernel: [    7.281051] Checking 'hlt' instruction... OK.
Oct 29 19:07:07 cory-laptop kernel: [    7.296882] SMP alternatives: switching to UP code
Oct 29 19:07:07 cory-laptop kernel: [    7.297200] Freeing SMP alternatives: 11k freed
Oct 29 19:07:07 cory-laptop kernel: [    7.297566] Early unpacking initramfs... done
Oct 29 19:07:07 cory-laptop kernel: [    7.638715] ACPI: Core revision 20070126
Oct 29 19:07:07 cory-laptop kernel: [    7.638793] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 29 19:07:07 cory-laptop kernel: [    7.640620] ACPI: setting ELCR to 0200 (from 0e00)
Oct 29 19:07:07 cory-laptop kernel: [    7.640778] CPU0: Intel Mobile Intel(R) Celeron(R) CPU 2.40GHz stepping 09
Oct 29 19:07:07 cory-laptop kernel: [    7.640786] SMP motherboard not detected.
Oct 29 19:07:07 cory-laptop kernel: [    7.640789] Local APIC not detected. Using dummy APIC emulation.
Oct 29 19:07:07 cory-laptop kernel: [    7.640835] Brought up 1 CPUs
Oct 29 19:07:07 cory-laptop kernel: [    7.641004] Booting paravirtualized kernel on bare hardware
Oct 29 19:07:07 cory-laptop kernel: [    7.641077] Time:  0:06:40  Date: 09/30/107
Oct 29 19:07:07 cory-laptop kernel: [    7.641113] NET: Registered protocol family 16
Oct 29 19:07:07 cory-laptop kernel: [    7.641262] EISA bus registered
Oct 29 19:07:07 cory-laptop kernel: [    7.641280] ACPI: bus type pci registered
Oct 29 19:07:07 cory-laptop kernel: [    7.641393] PCI: PCI BIOS revision 2.10 entry at 0xfd317, last bus=3
Oct 29 19:07:07 cory-laptop kernel: [    7.641396] PCI: Using configuration type 1
Oct 29 19:07:07 cory-laptop kernel: [    7.641398] Setting up standard PCI resources
Oct 29 19:07:07 cory-laptop kernel: [    7.646910] ACPI: Interpreter enabled
Oct 29 19:07:07 cory-laptop kernel: [    7.646916] ACPI: (supports S0 S3 S4 S5)
Oct 29 19:07:07 cory-laptop kernel: [    7.646940] ACPI: Using PIC for interrupt routing
Oct 29 19:07:07 cory-laptop kernel: [    7.655335] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 29 19:07:07 cory-laptop kernel: [    7.655860] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
Oct 29 19:07:07 cory-laptop kernel: [    7.655864] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
Oct 29 19:07:07 cory-laptop kernel: [    7.656120] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
Oct 29 19:07:07 cory-laptop kernel: [    7.656284] PCI: Transparent bridge - 0000:00:1e.0
Oct 29 19:07:07 cory-laptop kernel: [    7.658364] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
Oct 29 19:07:07 cory-laptop kernel: [    7.658491] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
Oct 29 19:07:07 cory-laptop kernel: [    7.658616] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
Oct 29 19:07:07 cory-laptop kernel: [    7.658741] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
Oct 29 19:07:07 cory-laptop kernel: [    7.658871] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
Oct 29 19:07:07 cory-laptop kernel: [    7.658998] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
Oct 29 19:07:07 cory-laptop kernel: [    7.659126] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
Oct 29 19:07:07 cory-laptop kernel: [    7.659252] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
Oct 29 19:07:07 cory-laptop kernel: [    7.659590] ACPI: Power Resource [PFAN] (off)
Oct 29 19:07:07 cory-laptop kernel: [    7.659610] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 29 19:07:07 cory-laptop kernel: [    7.659635] pnp: PnP ACPI init
Oct 29 19:07:07 cory-laptop kernel: [    7.659651] ACPI: bus type pnp registered
Oct 29 19:07:07 cory-laptop kernel: [    7.663156] pnp: PnP ACPI: found 10 devices
Oct 29 19:07:07 cory-laptop kernel: [    7.663162] ACPI: ACPI bus type pnp unregistered
Oct 29 19:07:07 cory-laptop kernel: [    7.663168] PnPBIOS: Disabled by ACPI PNP
Oct 29 19:07:07 cory-laptop kernel: [    7.663252] PCI: Using ACPI for IRQ routing
Oct 29 19:07:07 cory-laptop kernel: [    7.663257] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 29 19:07:07 cory-laptop kernel: [    7.667772] NET: Registered protocol family 8
Oct 29 19:07:07 cory-laptop kernel: [    7.667775] NET: Registered protocol family 20
Oct 29 19:07:07 cory-laptop kernel: [    7.667909] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
Oct 29 19:07:07 cory-laptop kernel: [    7.667914] pnp: 00:00: iomem range 0xe0000-0xeffff could not be reserved
Oct 29 19:07:07 cory-laptop kernel: [    7.667918] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
Oct 29 19:07:07 cory-laptop kernel: [    7.667921] pnp: 00:00: iomem range 0x100000-0x2ef3ffff could not be reserved
Oct 29 19:07:07 cory-laptop kernel: [    7.668131] Time: tsc clocksource has been installed.
Oct 29 19:07:07 cory-laptop kernel: [    7.698538] PCI: Bus 2, cardbus bridge: 0000:01:0b.0
Oct 29 19:07:07 cory-laptop kernel: [    7.698542]   IO window: 0000c000-0000c0ff
Oct 29 19:07:07 cory-laptop kernel: [    7.698547]   IO window: 0000c400-0000c4ff
Oct 29 19:07:07 cory-laptop kernel: [    7.698552]   PREFETCH window: 38000000-3bffffff
Oct 29 19:07:07 cory-laptop kernel: [    7.698557]   MEM window: 40000000-43ffffff
Oct 29 19:07:07 cory-laptop kernel: [    7.698562] PCI: Bridge: 0000:00:1e.0
Oct 29 19:07:07 cory-laptop kernel: [    7.698565]   IO window: c000-cfff
Oct 29 19:07:07 cory-laptop kernel: [    7.698571]   MEM window: cff00000-cfffffff
Oct 29 19:07:07 cory-laptop kernel: [    7.698576]   PREFETCH window: 38000000-3bffffff
Oct 29 19:07:07 cory-laptop kernel: [    7.698609] PCI: Enabling device 0000:01:0b.0 (0000 -> 0003)
Oct 29 19:07:07 cory-laptop kernel: [    7.698860] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Oct 29 19:07:07 cory-laptop kernel: [    7.698868] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:07:07 cory-laptop kernel: [    7.698895] NET: Registered protocol family 2
Oct 29 19:07:07 cory-laptop kernel: [    7.736078] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 29 19:07:07 cory-laptop kernel: [    7.736276] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Oct 29 19:07:07 cory-laptop kernel: [    7.738348] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 29 19:07:07 cory-laptop kernel: [    7.739080] TCP: Hash tables configured (established 131072 bind 65536)
Oct 29 19:07:07 cory-laptop kernel: [    7.739088] TCP reno registered
Oct 29 19:07:07 cory-laptop kernel: [    7.748194] checking if image is initramfs... it is
Oct 29 19:07:07 cory-laptop kernel: [    8.199278] Switched to high resolution mode on CPU 0
Oct 29 19:07:07 cory-laptop kernel: [    8.416130] Freeing initrd memory: 7115k freed
Oct 29 19:07:07 cory-laptop kernel: [    8.416321] Simple Boot Flag at 0x7c set to 0x1
Oct 29 19:07:07 cory-laptop kernel: [    8.416608] audit: initializing netlink socket (disabled)
Oct 29 19:07:07 cory-laptop kernel: [    8.416627] audit(1193702799.972:1): initialized
Oct 29 19:07:07 cory-laptop kernel: [    8.419704] VFS: Disk quotas dquot_6.5.1
Oct 29 19:07:07 cory-laptop kernel: [    8.419791] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 29 19:07:07 cory-laptop kernel: [    8.419964] io scheduler noop registered
Oct 29 19:07:07 cory-laptop kernel: [    8.419968] io scheduler anticipatory registered
Oct 29 19:07:07 cory-laptop kernel: [    8.419970] io scheduler deadline registered
Oct 29 19:07:07 cory-laptop kernel: [    8.419999] io scheduler cfq registered (default)
Oct 29 19:07:07 cory-laptop kernel: [    8.420283] isapnp: Scanning for PnP cards...
Oct 29 19:07:07 cory-laptop kernel: [    8.772703] isapnp: No Plug & Play device found
Oct 29 19:07:07 cory-laptop kernel: [    8.853625] Real Time Clock Driver v1.12ac
Oct 29 19:07:07 cory-laptop kernel: [    8.853776] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 29 19:07:07 cory-laptop kernel: [    8.855445] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
Oct 29 19:07:07 cory-laptop kernel: [    8.855661] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Oct 29 19:07:07 cory-laptop kernel: [    8.855665] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:07:07 cory-laptop kernel: [    8.855675] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Oct 29 19:07:07 cory-laptop kernel: [    8.856582] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 29 19:07:07 cory-laptop kernel: [    8.856923] input: Macintosh mouse button emulation as /class/input/input0
Oct 29 19:07:07 cory-laptop kernel: [    8.857053] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 29 19:07:07 cory-laptop kernel: [    8.872889] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 29 19:07:07 cory-laptop kernel: [    8.872899] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 29 19:07:07 cory-laptop kernel: [    8.873234] mice: PS/2 mouse device common for all mice
Oct 29 19:07:07 cory-laptop kernel: [    8.873428] EISA: Probing bus 0 at eisa.0
Oct 29 19:07:07 cory-laptop kernel: [    8.873437] Cannot allocate resource for EISA slot 1
Oct 29 19:07:07 cory-laptop kernel: [    8.873455] EISA: Detected 0 cards.
Oct 29 19:07:07 cory-laptop kernel: [    8.873587] TCP cubic registered
Oct 29 19:07:07 cory-laptop kernel: [    8.873659] NET: Registered protocol family 1
Oct 29 19:07:07 cory-laptop kernel: [    8.873690] Using IPI No-Shortcut mode
Oct 29 19:07:07 cory-laptop kernel: [    8.873922]   Magic number: 11:340:103
Oct 29 19:07:07 cory-laptop kernel: [    8.874637] Freeing unused kernel memory: 364k freed
Oct 29 19:07:07 cory-laptop kernel: [    8.930021] input: AT Translated Set 2 keyboard as /class/input/input1
Oct 29 19:07:07 cory-laptop kernel: [   10.177084] AppArmor: AppArmor initialized<5>audit(1193702801.972:2):  type=1505 info="AppArmor initialized" pid=1183
Oct 29 19:07:07 cory-laptop kernel: [   10.188352] fuse init (API version 7.8)
Oct 29 19:07:07 cory-laptop kernel: [   10.196628] Failure registering capabilities with primary security module.
Oct 29 19:07:07 cory-laptop kernel: [   10.209914] ACPI: Transitioning device [FAN] to D3
Oct 29 19:07:07 cory-laptop kernel: [   10.209920] ACPI: Transitioning device [FAN] to D3
Oct 29 19:07:07 cory-laptop kernel: [   10.209925] ACPI: Fan [FAN] (off)
Oct 29 19:07:07 cory-laptop kernel: [   10.217036] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct 29 19:07:07 cory-laptop kernel: [   10.218404] ACPI: Thermal Zone [THRM] (50 C)
Oct 29 19:07:07 cory-laptop kernel: [   11.064771] usbcore: registered new interface driver usbfs
Oct 29 19:07:07 cory-laptop kernel: [   11.064805] usbcore: registered new interface driver hub
Oct 29 19:07:07 cory-laptop kernel: [   11.064840] usbcore: registered new device driver usb
Oct 29 19:07:07 cory-laptop kernel: [   11.065978] USB Universal Host Controller Interface driver v3.0
Oct 29 19:07:07 cory-laptop kernel: [   11.066366] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Oct 29 19:07:07 cory-laptop kernel: [   11.066375] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 29 19:07:07 cory-laptop kernel: [   11.066394] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 29 19:07:07 cory-laptop kernel: [   11.066608] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Oct 29 19:07:07 cory-laptop kernel: [   11.066640] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018c0
Oct 29 19:07:07 cory-laptop kernel: [   11.066805] usb usb1: configuration #1 chosen from 1 choice
Oct 29 19:07:07 cory-laptop kernel: [   11.066842] hub 1-0:1.0: USB hub found
Oct 29 19:07:07 cory-laptop kernel: [   11.066855] hub 1-0:1.0: 2 ports detected
Oct 29 19:07:07 cory-laptop kernel: [   11.143067] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
Oct 29 19:07:07 cory-laptop kernel: [   11.143072] e100: Copyright(c) 1999-2006 Intel Corporation
Oct 29 19:07:07 cory-laptop kernel: [   11.218118] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Oct 29 19:07:07 cory-laptop kernel: [   11.218380] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Oct 29 19:07:07 cory-laptop kernel: [   11.218384] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:07:07 cory-laptop kernel: [   11.218407] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 29 19:07:07 cory-laptop kernel: [   11.218463] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Oct 29 19:07:07 cory-laptop kernel: [   11.218509] ehci_hcd 0000:00:1d.7: debug port 1
Oct 29 19:07:07 cory-laptop kernel: [   11.218528] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x3c080000
Oct 29 19:07:07 cory-laptop kernel: [   11.222399] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 29 19:07:07 cory-laptop kernel: [   11.222518] usb usb2: configuration #1 chosen from 1 choice
Oct 29 19:07:07 cory-laptop kernel: [   11.222552] hub 2-0:1.0: USB hub found
Oct 29 19:07:07 cory-laptop kernel: [   11.222563] hub 2-0:1.0: 6 ports detected
Oct 29 19:07:07 cory-laptop kernel: [   11.243687] SCSI subsystem initialized
Oct 29 19:07:07 cory-laptop kernel: [   11.326661] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
Oct 29 19:07:07 cory-laptop kernel: [   11.326668] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:07:07 cory-laptop kernel: [   11.365091] e100: eth0: e100_probe: addr 0xcffff000, irq 11, MAC addr 00:08:0D:2F:C7:65
Oct 29 19:07:07 cory-laptop kernel: [   11.371018] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Oct 29 19:07:07 cory-laptop kernel: [   11.371022] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:07:07 cory-laptop kernel: [   11.371209] scsi0 : ata_piix
Oct 29 19:07:07 cory-laptop kernel: [   11.371286] scsi1 : ata_piix
Oct 29 19:07:07 cory-laptop kernel: [   11.371447] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Oct 29 19:07:07 cory-laptop kernel: [   11.371451] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Oct 29 19:07:07 cory-laptop kernel: [    4.280000] Marking TSC unstable due to: possible TSC halt in C2.
Oct 29 19:07:07 cory-laptop kernel: [    4.288000] Time: acpi_pm clocksource has been installed.
Oct 29 19:07:07 cory-laptop kernel: [    4.344000] ata1.00: ATA-6: IC25N040ATMR04-0, MO2OAD0A, max UDMA/100
Oct 29 19:07:07 cory-laptop kernel: [    4.344000] ata1.00: 78140160 sectors, multi 0: LBA48 
Oct 29 19:07:07 cory-laptop kernel: [    4.360000] ata1.00: configured for UDMA/100
Oct 29 19:07:07 cory-laptop kernel: [    4.680000] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R2412, 1330, max UDMA/33
Oct 29 19:07:07 cory-laptop kernel: [    4.724000] usb 1-2: new low speed USB device using uhci_hcd and address 2
Oct 29 19:07:07 cory-laptop kernel: [    4.852000] ata2.00: configured for UDMA/33
Oct 29 19:07:07 cory-laptop kernel: [    4.852000] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATMR04-0 MO2O PQ: 0 ANSI: 5
Oct 29 19:07:07 cory-laptop kernel: [    4.868000] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2412 1330 PQ: 0 ANSI: 5
Oct 29 19:07:07 cory-laptop kernel: [    4.892000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Oct 29 19:07:07 cory-laptop kernel: [    4.892000] sd 0:0:0:0: [sda] Write Protect is off
Oct 29 19:07:07 cory-laptop kernel: [    4.892000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 29 19:07:07 cory-laptop kernel: [    4.892000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Oct 29 19:07:07 cory-laptop kernel: [    4.892000] sd 0:0:0:0: [sda] Write Protect is off
Oct 29 19:07:07 cory-laptop kernel: [    4.892000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 29 19:07:07 cory-laptop kernel: [    4.892000]  sda:<6>usb 1-2: configuration #1 chosen from 1 choice
Oct 29 19:07:07 cory-laptop kernel: [    4.924000]  sda1 sda2 <<6>usbcore: registered new interface driver hiddev
Oct 29 19:07:07 cory-laptop kernel: [    4.956000]  sda5 >
Oct 29 19:07:07 cory-laptop kernel: [    4.956000] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 29 19:07:07 cory-laptop kernel: [    4.960000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 29 19:07:07 cory-laptop kernel: [    4.960000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Oct 29 19:07:07 cory-laptop kernel: [    4.988000] input: HID 1241:1166 as /class/input/input2
Oct 29 19:07:07 cory-laptop kernel: [    4.988000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:1d.0-2
Oct 29 19:07:07 cory-laptop kernel: [    4.988000] usbcore: registered new interface driver usbhid
Oct 29 19:07:07 cory-laptop kernel: [    4.988000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 29 19:07:07 cory-laptop kernel: [    5.048000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Oct 29 19:07:07 cory-laptop kernel: [    5.048000] Uniform CD-ROM driver Revision: 3.20
Oct 29 19:07:07 cory-laptop kernel: [    5.244000] Attempting manual resume
Oct 29 19:07:07 cory-laptop kernel: [    5.300000] kjournald starting.  Commit interval 5 seconds
Oct 29 19:07:07 cory-laptop kernel: [    5.300000] EXT3-fs: mounted filesystem with ordered data mode.
Oct 29 19:07:07 cory-laptop kernel: [   19.448000] Linux agpgart interface v0.102 (c) Dave Jones
Oct 29 19:07:07 cory-laptop kernel: [   19.460000] agpgart: Detected an Intel 855GM Chipset.
Oct 29 19:07:07 cory-laptop kernel: [   19.460000] agpgart: Detected 16252K stolen memory.
Oct 29 19:07:07 cory-laptop kernel: [   19.468000] agpgart: AGP aperture is 128M @ 0xd8000000
Oct 29 19:07:07 cory-laptop kernel: [   20.024000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 29 19:07:07 cory-laptop kernel: [   20.032000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 29 19:07:07 cory-laptop kernel: [   20.428000] input: PC Speaker as /class/input/input3
Oct 29 19:07:07 cory-laptop kernel: [   20.540000] iTCO_vendor_support: vendor-support=0
Oct 29 19:07:07 cory-laptop kernel: [   20.540000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Oct 29 19:07:07 cory-laptop kernel: [   20.712000] Yenta: CardBus bridge found at 0000:01:0b.0 [1179:0001]
Oct 29 19:07:07 cory-laptop kernel: [   20.840000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
Oct 29 19:07:07 cory-laptop kernel: [   20.840000] Socket status: 30000020
Oct 29 19:07:07 cory-laptop kernel: [   20.840000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
Oct 29 19:07:07 cory-laptop kernel: [   20.840000] cs: IO port probe 0xc000-0xcfff: clean.
Oct 29 19:07:07 cory-laptop kernel: [   20.840000] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xcfffffff
Oct 29 19:07:07 cory-laptop kernel: [   20.840000] pcmcia: parent PCI bridge Memory window: 0x38000000 - 0x3bffffff
Oct 29 19:07:07 cory-laptop kernel: [   21.224000] input: PS/2 Mouse as /class/input/input4
Oct 29 19:07:07 cory-laptop kernel: [   21.228000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
Oct 29 19:07:07 cory-laptop kernel: [   21.228000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:07:07 cory-laptop kernel: [   21.268000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input5
Oct 29 19:07:07 cory-laptop kernel: [   21.276000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0xd860)
Oct 29 19:07:07 cory-laptop kernel: [   21.276000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Oct 29 19:07:07 cory-laptop kernel: [   21.280000] pnp: Device 00:09 activated.
Oct 29 19:07:07 cory-laptop kernel: [   21.280000] parport_pc 00:09: reported by Plug and Play ACPI
Oct 29 19:07:07 cory-laptop kernel: [   21.280000] pnp: Device 00:09 disabled.
Oct 29 19:07:07 cory-laptop kernel: [   21.476000] pccard: CardBus card inserted into slot 0
Oct 29 19:07:07 cory-laptop kernel: [   21.584000] acx: Loaded combined PCI/USB driver, firmware_ver=default
Oct 29 19:07:07 cory-laptop kernel: [   21.584000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Oct 29 19:07:07 cory-laptop kernel: [   21.604000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
Oct 29 19:07:07 cory-laptop kernel: [   21.608000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Oct 29 19:07:07 cory-laptop kernel: [   21.608000] cs: IO port probe 0x820-0x8ff: clean.
Oct 29 19:07:07 cory-laptop kernel: [   21.608000] cs: IO port probe 0xc00-0xcf7: clean.
Oct 29 19:07:07 cory-laptop kernel: [   21.608000] cs: IO port probe 0xa00-0xaff: clean.
Oct 29 19:07:07 cory-laptop kernel: [   21.652000] intel8x0_measure_ac97_clock: measured 54885 usecs
Oct 29 19:07:07 cory-laptop kernel: [   21.652000] intel8x0: clocking to 48000
Oct 29 19:07:07 cory-laptop kernel: [   21.656000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Oct 29 19:07:07 cory-laptop kernel: [   21.656000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:07:07 cory-laptop kernel: [   21.656000] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x40020000, phymem2:0x40000000, mem1:0xef92c000, mem1_size:8192, mem2:0xefb80000, mem2_size:131072
Oct 29 19:07:07 cory-laptop kernel: [   21.656000] acx: loading firmware for acx1111 chipset with radio ID 16
Oct 29 19:07:07 cory-laptop kernel: [   22.672000] NVS_vendor_offs:0221 probe_delay:200 eof_memory:1114112
Oct 29 19:07:07 cory-laptop kernel: [   22.672000] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
Oct 29 19:07:07 cory-laptop kernel: [   22.672000] AntennaID:00 Len:02 Data:01 02 
Oct 29 19:07:07 cory-laptop kernel: [   22.672000] PowerLevelID:01 Len:02 Data:001E 000A 
Oct 29 19:07:07 cory-laptop kernel: [   22.672000] DataRatesID:02 Len:05 Data:02 04 11 22 44 
Oct 29 19:07:07 cory-laptop kernel: [   22.672000] DomainID:03 Len:06 Data:10 20 30 31 32 40 
Oct 29 19:07:07 cory-laptop kernel: [   22.672000] ProductID:04 Len:09 Data:TI ACX100
Oct 29 19:07:07 cory-laptop kernel: [   22.672000] ManufacturerID:05 Len:07 Data:TI Test
Oct 29 19:07:07 cory-laptop kernel: [   22.732000] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
Oct 29 19:07:07 cory-laptop kernel: [   22.732000] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.22-14-generic
Oct 29 19:07:07 cory-laptop kernel: [   22.732000] usbcore: registered new interface driver acx_usb
Oct 29 19:07:07 cory-laptop kernel: [   23.320000] lp: driver loaded but no devices found
Oct 29 19:07:07 cory-laptop kernel: [   23.396000] Adding 698788k swap on /dev/sda5.  Priority:-1 extents:1 across:698788k
Oct 29 19:07:07 cory-laptop kernel: [   23.800000] EXT3 FS on sda1, internal journal
Oct 29 19:07:07 cory-laptop kernel: [   24.564000] NET: Registered protocol family 17
Oct 29 19:07:07 cory-laptop kernel: [   25.488000] ACPI: Battery Slot [BAT1] (battery present)
Oct 29 19:07:07 cory-laptop kernel: [   25.724000] No dock devices found.
Oct 29 19:07:07 cory-laptop kernel: [   25.756000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
Oct 29 19:07:07 cory-laptop kernel: [   25.756000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
Oct 29 19:07:07 cory-laptop kernel: [   25.760000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
Oct 29 19:07:07 cory-laptop kernel: [   25.760000] toshiba_acpi: ktoshkeyd will check 2 times per second
Oct 29 19:07:07 cory-laptop kernel: [   25.764000] toshiba_acpi: Dropped 0 keys from the queue on startup
Oct 29 19:07:07 cory-laptop kernel: [   25.784000] ACPI: AC Adapter [ADP1] (on-line)
Oct 29 19:07:07 cory-laptop kernel: [   25.844000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
Oct 29 19:07:07 cory-laptop kernel: [   25.916000] input: Power Button (FF) as /class/input/input6
Oct 29 19:07:07 cory-laptop kernel: [   25.920000] ACPI: Power Button (FF) [PWRF]
Oct 29 19:07:07 cory-laptop kernel: [   25.960000] input: Lid Switch as /class/input/input7
Oct 29 19:07:07 cory-laptop kernel: [   25.968000] ACPI: Lid Switch [LID]
Oct 29 19:07:07 cory-laptop kernel: [   26.008000] input: Power Button (CM) as /class/input/input8
Oct 29 19:07:07 cory-laptop kernel: [   26.016000] ACPI: Power Button (CM) [PWRB]
Oct 29 19:07:07 cory-laptop kernel: [   26.708000] NET: Registered protocol family 10
Oct 29 19:07:07 cory-laptop kernel: [   26.708000] lo: Disabled Privacy Extensions
Oct 29 19:07:07 cory-laptop kernel: [   27.344000] wlan0: duplicate address detected!
Oct 29 19:07:07 cory-laptop kernel: [   27.940000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:07:07 cory-laptop kernel: [   28.004000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Oct 29 19:07:07 cory-laptop kernel: [   28.004000] Intel ICH Modem: probe of 0000:00:1f.6 failed with error -13
Oct 29 19:07:08 cory-laptop kernel: [   28.276000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 29 19:07:19 cory-laptop kernel: [   39.200000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:07:19 cory-laptop kernel: [   39.920000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:07:20 cory-laptop kernel: [   40.576000] [drm] Initialized drm 1.1.0 20060810
Oct 29 19:07:20 cory-laptop kernel: [   40.600000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:07:20 cory-laptop kernel: [   40.636000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 29 19:07:20 cory-laptop kernel: [   40.640000] [drm] Initialized i915 1.6.0 20060119 on minor 0
Oct 29 19:07:20 cory-laptop kernel: [   40.640000] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
Oct 29 19:07:20 cory-laptop kernel: [   40.644000] [drm] Initialized i915 1.6.0 20060119 on minor 1
Oct 29 19:07:21 cory-laptop kernel: [   41.120000] ppdev: user-space parallel port driver
Oct 29 19:07:21 cory-laptop kernel: [   41.928000] audit(1193702841.696:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4903 profile="/usr/sbin/cupsd"
Oct 29 19:07:22 cory-laptop kernel: [   42.140000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
Oct 29 19:07:22 cory-laptop kernel: [   42.140000] apm: overridden by ACPI.
Oct 29 19:07:22 cory-laptop kernel: [   42.636000] Failure registering capabilities with primary security module.
Oct 29 19:07:22 cory-laptop dhcdbd: Started up.
Oct 29 19:07:22 cory-laptop kernel: [   42.884000] Bluetooth: Core ver 2.11
Oct 29 19:07:22 cory-laptop kernel: [   42.884000] NET: Registered protocol family 31
Oct 29 19:07:22 cory-laptop kernel: [   42.884000] Bluetooth: HCI device and connection manager initialized
Oct 29 19:07:22 cory-laptop kernel: [   42.884000] Bluetooth: HCI socket layer initialized
Oct 29 19:07:22 cory-laptop kernel: [   42.900000] Bluetooth: L2CAP ver 2.8
Oct 29 19:07:22 cory-laptop kernel: [   42.900000] Bluetooth: L2CAP socket layer initialized
Oct 29 19:07:22 cory-laptop kernel: [   42.956000] Bluetooth: RFCOMM socket layer initialized
Oct 29 19:07:22 cory-laptop kernel: [   42.956000] Bluetooth: RFCOMM TTY layer initialized
Oct 29 19:07:22 cory-laptop kernel: [   42.956000] Bluetooth: RFCOMM ver 1.8
Oct 29 19:08:12 cory-laptop kernel: [   92.788000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:08:19 cory-laptop kernel: [  100.092000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:09:25 cory-laptop syslogd 1.4.1#21ubuntu3: restart.
Oct 29 19:09:26 cory-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Oct 29 19:09:26 cory-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Oct 29 19:09:26 cory-laptop kernel: Symbols match kernel version 2.6.22.
Oct 29 19:09:26 cory-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002ef40000 (usable)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000002ef40000 - 000000002ef50000 (ACPI data)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000002ef50000 - 000000002f000000 (reserved)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] 751MB LOWMEM available.
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] Zone PFN ranges:
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]   DMA             0 ->     4096
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]   Normal       4096 ->   192320
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]   HighMem    192320 ->   192320
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 29 19:09:26 cory-laptop kernel: [    0.000000]     0:        0 ->   192320
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] DMI 2.3 present.
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F0180 checksum 0
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] ACPI: RSDP 000F0180, 0014 (r0 TOSHIB)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] ACPI: RSDT 2EF40000, 0030 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] ACPI: FACP 2EF40058, 0084 (r2 TOSHIB 750        970814 TASM  4010000)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] ACPI: DSDT 2EF40110, 4B25 (r1 TOSHIB AFCF7    20030326 MSFT  100000E)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] ACPI: FACS 000EEE00, 0040
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] ACPI: DBGP 2EF400DC, 0034 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] ACPI: BOOT 2EF40030, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xd808
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f000000:cfc10000)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 190818
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] Kernel command line: root=UUID=e6f50239-1aea-4ce9-bff6-f65118a4cdb9 ro quiet splash
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] Initializing CPU#0
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 29 19:09:26 cory-laptop kernel: [    0.000000] Detected 2394.097 MHz processor.
Oct 29 19:09:26 cory-laptop kernel: [    7.568912] Console: colour VGA+ 80x25
Oct 29 19:09:26 cory-laptop kernel: [    7.569605] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 29 19:09:26 cory-laptop kernel: [    7.570657] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 29 19:09:26 cory-laptop kernel: [    7.589708] Memory: 750860k/769280k available (2015k kernel code, 17808k reserved, 916k data, 364k init, 0k highmem)
Oct 29 19:09:26 cory-laptop kernel: [    7.589719] virtual kernel memory layout:
Oct 29 19:09:26 cory-laptop kernel: [    7.589720]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Oct 29 19:09:26 cory-laptop kernel: [    7.589722]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 29 19:09:26 cory-laptop kernel: [    7.589723]     vmalloc : 0xef800000 - 0xff7fe000   ( 255 MB)
Oct 29 19:09:26 cory-laptop kernel: [    7.589724]     lowmem  : 0xc0000000 - 0xeef40000   ( 751 MB)
Oct 29 19:09:26 cory-laptop kernel: [    7.589725]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Oct 29 19:09:26 cory-laptop kernel: [    7.589727]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Oct 29 19:09:26 cory-laptop kernel: [    7.589728]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Oct 29 19:09:26 cory-laptop kernel: [    7.589731] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 29 19:09:26 cory-laptop kernel: [    7.589776] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 29 19:09:26 cory-laptop kernel: [    7.669667] Calibrating delay using timer specific routine.. 4792.23 BogoMIPS (lpj=9584470)
Oct 29 19:09:26 cory-laptop kernel: [    7.669699] Security Framework v1.0.0 initialized
Oct 29 19:09:26 cory-laptop kernel: [    7.669708] SELinux:  Disabled at boot.
Oct 29 19:09:26 cory-laptop kernel: [    7.669723] Mount-cache hash table entries: 512
Oct 29 19:09:26 cory-laptop kernel: [    7.669905] CPU: Trace cache: 12K uops, L1 D cache: 8K
Oct 29 19:09:26 cory-laptop kernel: [    7.669908] CPU: L2 cache: 256K
Oct 29 19:09:26 cory-laptop kernel: [    7.669911] CPU: Hyper-Threading is disabled
Oct 29 19:09:26 cory-laptop kernel: [    7.669928] Compat vDSO mapped to ffffe000.
Oct 29 19:09:26 cory-laptop kernel: [    7.669944] Checking 'hlt' instruction... OK.
Oct 29 19:09:26 cory-laptop kernel: [    7.685774] SMP alternatives: switching to UP code
Oct 29 19:09:26 cory-laptop kernel: [    7.686092] Freeing SMP alternatives: 11k freed
Oct 29 19:09:26 cory-laptop kernel: [    7.686456] Early unpacking initramfs... done
Oct 29 19:09:26 cory-laptop kernel: [    8.028130] ACPI: Core revision 20070126
Oct 29 19:09:26 cory-laptop kernel: [    8.028210] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 29 19:09:26 cory-laptop kernel: [    8.030036] ACPI: setting ELCR to 0200 (from 0e00)
Oct 29 19:09:26 cory-laptop kernel: [    8.030195] CPU0: Intel Mobile Intel(R) Celeron(R) CPU 2.40GHz stepping 09
Oct 29 19:09:26 cory-laptop kernel: [    8.030204] SMP motherboard not detected.
Oct 29 19:09:26 cory-laptop kernel: [    8.030206] Local APIC not detected. Using dummy APIC emulation.
Oct 29 19:09:26 cory-laptop kernel: [    8.030253] Brought up 1 CPUs
Oct 29 19:09:26 cory-laptop kernel: [    8.030419] Booting paravirtualized kernel on bare hardware
Oct 29 19:09:26 cory-laptop kernel: [    8.030491] Time:  0:08:59  Date: 09/30/107
Oct 29 19:09:26 cory-laptop kernel: [    8.030527] NET: Registered protocol family 16
Oct 29 19:09:26 cory-laptop kernel: [    8.030672] EISA bus registered
Oct 29 19:09:26 cory-laptop kernel: [    8.030690] ACPI: bus type pci registered
Oct 29 19:09:26 cory-laptop kernel: [    8.030802] PCI: PCI BIOS revision 2.10 entry at 0xfd317, last bus=3
Oct 29 19:09:26 cory-laptop kernel: [    8.030804] PCI: Using configuration type 1
Oct 29 19:09:26 cory-laptop kernel: [    8.030806] Setting up standard PCI resources
Oct 29 19:09:26 cory-laptop kernel: [    8.036303] ACPI: Interpreter enabled
Oct 29 19:09:26 cory-laptop kernel: [    8.036309] ACPI: (supports S0 S3 S4 S5)
Oct 29 19:09:26 cory-laptop kernel: [    8.036333] ACPI: Using PIC for interrupt routing
Oct 29 19:09:26 cory-laptop kernel: [    8.044788] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 29 19:09:26 cory-laptop kernel: [    8.045373] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
Oct 29 19:09:26 cory-laptop kernel: [    8.045378] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
Oct 29 19:09:26 cory-laptop kernel: [    8.045639] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
Oct 29 19:09:26 cory-laptop kernel: [    8.045740] PCI: Transparent bridge - 0000:00:1e.0
Oct 29 19:09:26 cory-laptop kernel: [    8.047799] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
Oct 29 19:09:26 cory-laptop kernel: [    8.047925] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
Oct 29 19:09:26 cory-laptop kernel: [    8.048048] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
Oct 29 19:09:26 cory-laptop kernel: [    8.048172] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
Oct 29 19:09:26 cory-laptop kernel: [    8.048303] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
Oct 29 19:09:26 cory-laptop kernel: [    8.048429] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
Oct 29 19:09:26 cory-laptop kernel: [    8.048553] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
Oct 29 19:09:26 cory-laptop kernel: [    8.048676] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
Oct 29 19:09:26 cory-laptop kernel: [    8.049025] ACPI: Power Resource [PFAN] (off)
Oct 29 19:09:26 cory-laptop kernel: [    8.049111] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 29 19:09:26 cory-laptop kernel: [    8.049136] pnp: PnP ACPI init
Oct 29 19:09:26 cory-laptop kernel: [    8.049154] ACPI: bus type pnp registered
Oct 29 19:09:26 cory-laptop kernel: [    8.052586] pnp: PnP ACPI: found 10 devices
Oct 29 19:09:26 cory-laptop kernel: [    8.052591] ACPI: ACPI bus type pnp unregistered
Oct 29 19:09:26 cory-laptop kernel: [    8.052597] PnPBIOS: Disabled by ACPI PNP
Oct 29 19:09:26 cory-laptop kernel: [    8.052682] PCI: Using ACPI for IRQ routing
Oct 29 19:09:26 cory-laptop kernel: [    8.052686] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 29 19:09:26 cory-laptop kernel: [    8.057250] NET: Registered protocol family 8
Oct 29 19:09:26 cory-laptop kernel: [    8.057254] NET: Registered protocol family 20
Oct 29 19:09:26 cory-laptop kernel: [    8.057386] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
Oct 29 19:09:26 cory-laptop kernel: [    8.057391] pnp: 00:00: iomem range 0xe0000-0xeffff could not be reserved
Oct 29 19:09:26 cory-laptop kernel: [    8.057394] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
Oct 29 19:09:26 cory-laptop kernel: [    8.057397] pnp: 00:00: iomem range 0x100000-0x2ef3ffff could not be reserved
Oct 29 19:09:26 cory-laptop kernel: [    8.061018] Time: tsc clocksource has been installed.
Oct 29 19:09:26 cory-laptop kernel: [    8.087943] PCI: Bus 2, cardbus bridge: 0000:01:0b.0
Oct 29 19:09:26 cory-laptop kernel: [    8.087946]   IO window: 0000c000-0000c0ff
Oct 29 19:09:26 cory-laptop kernel: [    8.087951]   IO window: 0000c400-0000c4ff
Oct 29 19:09:26 cory-laptop kernel: [    8.087956]   PREFETCH window: 38000000-3bffffff
Oct 29 19:09:26 cory-laptop kernel: [    8.087961]   MEM window: 40000000-43ffffff
Oct 29 19:09:26 cory-laptop kernel: [    8.087966] PCI: Bridge: 0000:00:1e.0
Oct 29 19:09:26 cory-laptop kernel: [    8.087969]   IO window: c000-cfff
Oct 29 19:09:26 cory-laptop kernel: [    8.087975]   MEM window: cff00000-cfffffff
Oct 29 19:09:26 cory-laptop kernel: [    8.087980]   PREFETCH window: 38000000-3bffffff
Oct 29 19:09:26 cory-laptop kernel: [    8.088013] PCI: Enabling device 0000:01:0b.0 (0000 -> 0003)
Oct 29 19:09:26 cory-laptop kernel: [    8.088271] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Oct 29 19:09:26 cory-laptop kernel: [    8.088279] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:09:26 cory-laptop kernel: [    8.088306] NET: Registered protocol family 2
Oct 29 19:09:26 cory-laptop kernel: [    8.124966] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 29 19:09:26 cory-laptop kernel: [    8.125166] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Oct 29 19:09:26 cory-laptop kernel: [    8.127248] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 29 19:09:26 cory-laptop kernel: [    8.127979] TCP: Hash tables configured (established 131072 bind 65536)
Oct 29 19:09:26 cory-laptop kernel: [    8.127987] TCP reno registered
Oct 29 19:09:26 cory-laptop kernel: [    8.137094] checking if image is initramfs... it is
Oct 29 19:09:26 cory-laptop kernel: [    8.588173] Switched to high resolution mode on CPU 0
Oct 29 19:09:26 cory-laptop kernel: [    8.803755] Freeing initrd memory: 7115k freed
Oct 29 19:09:26 cory-laptop kernel: [    8.803945] Simple Boot Flag at 0x7c set to 0x1
Oct 29 19:09:26 cory-laptop kernel: [    8.804229] audit: initializing netlink socket (disabled)
Oct 29 19:09:26 cory-laptop kernel: [    8.804248] audit(1193702938.976:1): initialized
Oct 29 19:09:26 cory-laptop kernel: [    8.807201] VFS: Disk quotas dquot_6.5.1
Oct 29 19:09:26 cory-laptop kernel: [    8.807287] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 29 19:09:26 cory-laptop kernel: [    8.807459] io scheduler noop registered
Oct 29 19:09:26 cory-laptop kernel: [    8.807462] io scheduler anticipatory registered
Oct 29 19:09:26 cory-laptop kernel: [    8.807464] io scheduler deadline registered
Oct 29 19:09:26 cory-laptop kernel: [    8.807494] io scheduler cfq registered (default)
Oct 29 19:09:26 cory-laptop kernel: [    8.807816] isapnp: Scanning for PnP cards...
Oct 29 19:09:26 cory-laptop kernel: [    9.160241] isapnp: No Plug & Play device found
Oct 29 19:09:26 cory-laptop kernel: [    9.238854] Real Time Clock Driver v1.12ac
Oct 29 19:09:26 cory-laptop kernel: [    9.239072] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 29 19:09:26 cory-laptop kernel: [    9.240654] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
Oct 29 19:09:26 cory-laptop kernel: [    9.240873] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Oct 29 19:09:26 cory-laptop kernel: [    9.240877] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:09:26 cory-laptop kernel: [    9.240886] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Oct 29 19:09:26 cory-laptop kernel: [    9.241792] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 29 19:09:26 cory-laptop kernel: [    9.242135] input: Macintosh mouse button emulation as /class/input/input0
Oct 29 19:09:26 cory-laptop kernel: [    9.242265] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 29 19:09:26 cory-laptop kernel: [    9.256181] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 29 19:09:26 cory-laptop kernel: [    9.256191] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 29 19:09:26 cory-laptop kernel: [    9.256540] mice: PS/2 mouse device common for all mice
Oct 29 19:09:26 cory-laptop kernel: [    9.256735] EISA: Probing bus 0 at eisa.0
Oct 29 19:09:26 cory-laptop kernel: [    9.256744] Cannot allocate resource for EISA slot 1
Oct 29 19:09:26 cory-laptop kernel: [    9.256762] EISA: Detected 0 cards.
Oct 29 19:09:26 cory-laptop kernel: [    9.256950] TCP cubic registered
Oct 29 19:09:26 cory-laptop kernel: [    9.256968] NET: Registered protocol family 1
Oct 29 19:09:26 cory-laptop kernel: [    9.256998] Using IPI No-Shortcut mode
Oct 29 19:09:26 cory-laptop kernel: [    9.257237]   Magic number: 11:340:103
Oct 29 19:09:26 cory-laptop kernel: [    9.257915] Freeing unused kernel memory: 364k freed
Oct 29 19:09:26 cory-laptop kernel: [    9.313811] input: AT Translated Set 2 keyboard as /class/input/input1
Oct 29 19:09:26 cory-laptop kernel: [   10.559323] AppArmor: AppArmor initialized<5>audit(1193702940.476:2):  type=1505 info="AppArmor initialized" pid=1183
Oct 29 19:09:26 cory-laptop kernel: [   10.570470] fuse init (API version 7.8)
Oct 29 19:09:26 cory-laptop kernel: [   10.578563] Failure registering capabilities with primary security module.
Oct 29 19:09:26 cory-laptop kernel: [   10.590657] ACPI: Transitioning device [FAN] to D3
Oct 29 19:09:26 cory-laptop kernel: [   10.590662] ACPI: Transitioning device [FAN] to D3
Oct 29 19:09:26 cory-laptop kernel: [   10.590668] ACPI: Fan [FAN] (off)
Oct 29 19:09:26 cory-laptop kernel: [   10.597768] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct 29 19:09:26 cory-laptop kernel: [   10.599131] ACPI: Thermal Zone [THRM] (56 C)
Oct 29 19:09:26 cory-laptop kernel: [   11.470628] usbcore: registered new interface driver usbfs
Oct 29 19:09:26 cory-laptop kernel: [   11.470660] usbcore: registered new interface driver hub
Oct 29 19:09:26 cory-laptop kernel: [   11.470696] usbcore: registered new device driver usb
Oct 29 19:09:26 cory-laptop kernel: [   11.472284] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Oct 29 19:09:26 cory-laptop kernel: [   11.472547] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Oct 29 19:09:26 cory-laptop kernel: [   11.472551] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:09:26 cory-laptop kernel: [   11.472574] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 29 19:09:26 cory-laptop kernel: [   11.472787] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Oct 29 19:09:26 cory-laptop kernel: [   11.472836] ehci_hcd 0000:00:1d.7: debug port 1
Oct 29 19:09:26 cory-laptop kernel: [   11.472856] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x3c080000
Oct 29 19:09:26 cory-laptop kernel: [   11.476739] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 29 19:09:26 cory-laptop kernel: [   11.476882] usb usb1: configuration #1 chosen from 1 choice
Oct 29 19:09:26 cory-laptop kernel: [   11.476917] hub 1-0:1.0: USB hub found
Oct 29 19:09:26 cory-laptop kernel: [   11.476929] hub 1-0:1.0: 6 ports detected
Oct 29 19:09:26 cory-laptop kernel: [   11.498544] USB Universal Host Controller Interface driver v3.0
Oct 29 19:09:26 cory-laptop kernel: [   11.540641] SCSI subsystem initialized
Oct 29 19:09:26 cory-laptop kernel: [   11.560351] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
Oct 29 19:09:26 cory-laptop kernel: [   11.560355] e100: Copyright(c) 1999-2006 Intel Corporation
Oct 29 19:09:26 cory-laptop kernel: [   11.581733] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Oct 29 19:09:26 cory-laptop kernel: [   11.581744] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 29 19:09:26 cory-laptop kernel: [   11.581762] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 29 19:09:26 cory-laptop kernel: [   11.581826] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Oct 29 19:09:26 cory-laptop kernel: [   11.581856] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018c0
Oct 29 19:09:26 cory-laptop kernel: [   11.581993] usb usb2: configuration #1 chosen from 1 choice
Oct 29 19:09:26 cory-laptop kernel: [   11.582030] hub 2-0:1.0: USB hub found
Oct 29 19:09:26 cory-laptop kernel: [   11.582040] hub 2-0:1.0: 2 ports detected
Oct 29 19:09:26 cory-laptop kernel: [   11.685982] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Oct 29 19:09:26 cory-laptop kernel: [   11.685986] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:09:26 cory-laptop kernel: [   11.686228] scsi0 : ata_piix
Oct 29 19:09:26 cory-laptop kernel: [   11.686308] scsi1 : ata_piix
Oct 29 19:09:26 cory-laptop kernel: [   11.686468] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Oct 29 19:09:26 cory-laptop kernel: [   11.686472] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Oct 29 19:09:26 cory-laptop kernel: [    4.260000] Marking TSC unstable due to: possible TSC halt in C2.
Oct 29 19:09:26 cory-laptop kernel: [    4.268000] Time: acpi_pm clocksource has been installed.
Oct 29 19:09:26 cory-laptop kernel: [    4.268000] ata1.00: ATA-6: IC25N040ATMR04-0, MO2OAD0A, max UDMA/100
Oct 29 19:09:26 cory-laptop kernel: [    4.268000] ata1.00: 78140160 sectors, multi 0: LBA48 
Oct 29 19:09:26 cory-laptop kernel: [    4.284000] ata1.00: configured for UDMA/100
Oct 29 19:09:26 cory-laptop kernel: [    4.424000] usb 2-2: new low speed USB device using uhci_hcd and address 2
Oct 29 19:09:26 cory-laptop kernel: [    4.604000] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R2412, 1330, max UDMA/33
Oct 29 19:09:26 cory-laptop kernel: [    4.624000] usb 2-2: configuration #1 chosen from 1 choice
Oct 29 19:09:26 cory-laptop kernel: [    4.644000] usbcore: registered new interface driver hiddev
Oct 29 19:09:26 cory-laptop kernel: [    4.684000] input: HID 1241:1166 as /class/input/input2
Oct 29 19:09:26 cory-laptop kernel: [    4.684000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:1d.0-2
Oct 29 19:09:26 cory-laptop kernel: [    4.684000] usbcore: registered new interface driver usbhid
Oct 29 19:09:26 cory-laptop kernel: [    4.684000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 29 19:09:26 cory-laptop kernel: [    4.780000] ata2.00: configured for UDMA/33
Oct 29 19:09:26 cory-laptop kernel: [    4.780000] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATMR04-0 MO2O PQ: 0 ANSI: 5
Oct 29 19:09:26 cory-laptop kernel: [    4.796000] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2412 1330 PQ: 0 ANSI: 5
Oct 29 19:09:26 cory-laptop kernel: [    4.796000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
Oct 29 19:09:26 cory-laptop kernel: [    4.796000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:09:26 cory-laptop kernel: [    4.820000] e100: eth0: e100_probe: addr 0xcffff000, irq 11, MAC addr 00:08:0D:2F:C7:65
Oct 29 19:09:26 cory-laptop kernel: [    4.844000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Oct 29 19:09:26 cory-laptop kernel: [    4.844000] sd 0:0:0:0: [sda] Write Protect is off
Oct 29 19:09:26 cory-laptop kernel: [    4.844000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 29 19:09:26 cory-laptop kernel: [    4.844000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Oct 29 19:09:26 cory-laptop kernel: [    4.844000] sd 0:0:0:0: [sda] Write Protect is off
Oct 29 19:09:26 cory-laptop kernel: [    4.844000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 29 19:09:26 cory-laptop kernel: [    4.844000]  sda: sda1 sda2 < sda5 >
Oct 29 19:09:26 cory-laptop kernel: [    4.900000] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 29 19:09:26 cory-laptop kernel: [    4.908000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 29 19:09:26 cory-laptop kernel: [    4.908000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Oct 29 19:09:26 cory-laptop kernel: [    4.992000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Oct 29 19:09:26 cory-laptop kernel: [    4.992000] Uniform CD-ROM driver Revision: 3.20
Oct 29 19:09:26 cory-laptop kernel: [    5.184000] Attempting manual resume
Oct 29 19:09:26 cory-laptop kernel: [    5.204000] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct 29 19:09:26 cory-laptop kernel: [    5.204000] EXT3-fs: write access will be enabled during recovery.
Oct 29 19:09:26 cory-laptop kernel: [    6.960000] kjournald starting.  Commit interval 5 seconds
Oct 29 19:09:26 cory-laptop kernel: [    6.960000] EXT3-fs: recovery complete.
Oct 29 19:09:26 cory-laptop kernel: [    6.964000] EXT3-fs: mounted filesystem with ordered data mode.
Oct 29 19:09:26 cory-laptop kernel: [   20.508000] Linux agpgart interface v0.102 (c) Dave Jones
Oct 29 19:09:26 cory-laptop kernel: [   20.548000] agpgart: Detected an Intel 855GM Chipset.
Oct 29 19:09:26 cory-laptop kernel: [   20.548000] agpgart: Detected 16252K stolen memory.
Oct 29 19:09:26 cory-laptop kernel: [   20.644000] agpgart: AGP aperture is 128M @ 0xd8000000
Oct 29 19:09:26 cory-laptop kernel: [   20.788000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 29 19:09:26 cory-laptop kernel: [   20.828000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 29 19:09:26 cory-laptop kernel: [   20.856000] iTCO_vendor_support: vendor-support=0
Oct 29 19:09:26 cory-laptop kernel: [   20.856000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Oct 29 19:09:26 cory-laptop kernel: [   20.856000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0xd860)
Oct 29 19:09:26 cory-laptop kernel: [   20.856000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Oct 29 19:09:26 cory-laptop kernel: [   21.332000] Yenta: CardBus bridge found at 0000:01:0b.0 [1179:0001]
Oct 29 19:09:26 cory-laptop kernel: [   21.460000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
Oct 29 19:09:26 cory-laptop kernel: [   21.460000] Socket status: 30000020
Oct 29 19:09:26 cory-laptop kernel: [   21.460000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
Oct 29 19:09:26 cory-laptop kernel: [   21.460000] cs: IO port probe 0xc000-0xcfff: clean.
Oct 29 19:09:26 cory-laptop kernel: [   21.460000] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xcfffffff
Oct 29 19:09:26 cory-laptop kernel: [   21.460000] pcmcia: parent PCI bridge Memory window: 0x38000000 - 0x3bffffff
Oct 29 19:09:26 cory-laptop kernel: [   21.648000] input: PC Speaker as /class/input/input3
Oct 29 19:09:26 cory-laptop kernel: [   22.096000] pccard: CardBus card inserted into slot 0
Oct 29 19:09:26 cory-laptop kernel: [   22.116000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
Oct 29 19:09:26 cory-laptop kernel: [   22.116000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:09:26 cory-laptop kernel: [   22.212000] acx: Loaded combined PCI/USB driver, firmware_ver=default
Oct 29 19:09:26 cory-laptop kernel: [   22.212000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Oct 29 19:09:26 cory-laptop kernel: [   22.264000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
Oct 29 19:09:26 cory-laptop kernel: [   22.264000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Oct 29 19:09:26 cory-laptop kernel: [   22.264000] cs: IO port probe 0x820-0x8ff: clean.
Oct 29 19:09:26 cory-laptop kernel: [   22.264000] cs: IO port probe 0xc00-0xcf7: clean.
Oct 29 19:09:26 cory-laptop kernel: [   22.264000] cs: IO port probe 0xa00-0xaff: clean.
Oct 29 19:09:26 cory-laptop kernel: [   22.372000] input: PS/2 Mouse as /class/input/input4
Oct 29 19:09:26 cory-laptop kernel: [   22.416000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input5
Oct 29 19:09:26 cory-laptop kernel: [   22.428000] pnp: Device 00:09 activated.
Oct 29 19:09:26 cory-laptop kernel: [   22.428000] parport_pc 00:09: reported by Plug and Play ACPI
Oct 29 19:09:26 cory-laptop kernel: [   22.428000] pnp: Device 00:09 disabled.
Oct 29 19:09:26 cory-laptop kernel: [   22.536000] intel8x0_measure_ac97_clock: measured 54935 usecs
Oct 29 19:09:26 cory-laptop kernel: [   22.536000] intel8x0: clocking to 48000
Oct 29 19:09:26 cory-laptop kernel: [   22.536000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Oct 29 19:09:26 cory-laptop kernel: [   22.536000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:09:26 cory-laptop kernel: [   22.536000] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x40020000, phymem2:0x40000000, mem1:0xefa8c000, mem1_size:8192, mem2:0xefb80000, mem2_size:131072
Oct 29 19:09:26 cory-laptop kernel: [   22.536000] acx: loading firmware for acx1111 chipset with radio ID 16
Oct 29 19:09:26 cory-laptop kernel: [   23.500000] NVS_vendor_offs:0221 probe_delay:200 eof_memory:1114112
Oct 29 19:09:26 cory-laptop kernel: [   23.500000] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
Oct 29 19:09:26 cory-laptop kernel: [   23.500000] AntennaID:00 Len:02 Data:01 02 
Oct 29 19:09:26 cory-laptop kernel: [   23.500000] PowerLevelID:01 Len:02 Data:001E 000A 
Oct 29 19:09:26 cory-laptop kernel: [   23.500000] DataRatesID:02 Len:05 Data:02 04 11 22 44 
Oct 29 19:09:26 cory-laptop kernel: [   23.500000] DomainID:03 Len:06 Data:10 20 30 31 32 40 
Oct 29 19:09:26 cory-laptop kernel: [   23.500000] ProductID:04 Len:09 Data:TI ACX100
Oct 29 19:09:26 cory-laptop kernel: [   23.500000] ManufacturerID:05 Len:07 Data:TI Test
Oct 29 19:09:26 cory-laptop kernel: [   23.560000] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
Oct 29 19:09:26 cory-laptop kernel: [   23.560000] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.22-14-generic
Oct 29 19:09:26 cory-laptop kernel: [   23.560000] usbcore: registered new interface driver acx_usb
Oct 29 19:09:26 cory-laptop kernel: [   24.360000] lp: driver loaded but no devices found
Oct 29 19:09:26 cory-laptop kernel: [   24.424000] Adding 698788k swap on /dev/sda5.  Priority:-1 extents:1 across:698788k
Oct 29 19:09:26 cory-laptop kernel: [   24.840000] EXT3 FS on sda1, internal journal
Oct 29 19:09:26 cory-laptop kernel: [   25.204000] NET: Registered protocol family 17
Oct 29 19:09:26 cory-laptop kernel: [   26.072000] ACPI: Battery Slot [BAT1] (battery present)
Oct 29 19:09:26 cory-laptop kernel: [   26.332000] No dock devices found.
Oct 29 19:09:26 cory-laptop kernel: [   26.364000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
Oct 29 19:09:26 cory-laptop kernel: [   26.364000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
Oct 29 19:09:26 cory-laptop kernel: [   26.368000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
Oct 29 19:09:26 cory-laptop kernel: [   26.368000] toshiba_acpi: ktoshkeyd will check 2 times per second
Oct 29 19:09:26 cory-laptop kernel: [   26.372000] toshiba_acpi: Dropped 0 keys from the queue on startup
Oct 29 19:09:26 cory-laptop kernel: [   26.400000] ACPI: AC Adapter [ADP1] (on-line)
Oct 29 19:09:26 cory-laptop kernel: [   26.464000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
Oct 29 19:09:26 cory-laptop kernel: [   26.532000] input: Power Button (FF) as /class/input/input6
Oct 29 19:09:26 cory-laptop kernel: [   26.540000] ACPI: Power Button (FF) [PWRF]
Oct 29 19:09:26 cory-laptop kernel: [   26.584000] input: Lid Switch as /class/input/input7
Oct 29 19:09:26 cory-laptop kernel: [   26.588000] ACPI: Lid Switch [LID]
Oct 29 19:09:26 cory-laptop kernel: [   26.632000] input: Power Button (CM) as /class/input/input8
Oct 29 19:09:26 cory-laptop kernel: [   26.636000] ACPI: Power Button (CM) [PWRB]
Oct 29 19:09:26 cory-laptop kernel: [   28.156000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 29 19:09:27 cory-laptop kernel: [   28.676000] AC'97 1 does not respond - RESET
Oct 29 19:09:27 cory-laptop kernel: [   28.676000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Oct 29 19:09:27 cory-laptop kernel: [   28.676000] Intel ICH Modem: probe of 0000:00:1f.6 failed with error -5
Oct 29 19:09:31 cory-laptop kernel: [   32.604000] NET: Registered protocol family 10
Oct 29 19:09:31 cory-laptop kernel: [   32.604000] lo: Disabled Privacy Extensions
Oct 29 19:09:31 cory-laptop kernel: [   32.604000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 29 19:09:31 cory-laptop kernel: [   33.132000] wlan0: duplicate address detected!
Oct 29 19:09:39 cory-laptop kernel: [   41.100000] [drm] Initialized drm 1.1.0 20060810
Oct 29 19:09:40 cory-laptop kernel: [   41.120000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 29 19:09:40 cory-laptop kernel: [   41.120000] [drm] Initialized i915 1.6.0 20060119 on minor 0
Oct 29 19:09:40 cory-laptop kernel: [   41.120000] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
Oct 29 19:09:40 cory-laptop kernel: [   41.120000] [drm] Initialized i915 1.6.0 20060119 on minor 1
Oct 29 19:09:40 cory-laptop kernel: [   41.392000] ppdev: user-space parallel port driver
Oct 29 19:09:40 cory-laptop kernel: [   42.080000] audit(1193702980.581:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4913 profile="/usr/sbin/cupsd"
Oct 29 19:09:41 cory-laptop kernel: [   42.252000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
Oct 29 19:09:41 cory-laptop kernel: [   42.252000] apm: overridden by ACPI.
Oct 29 19:09:41 cory-laptop kernel: [   42.904000] Failure registering capabilities with primary security module.
Oct 29 19:09:41 cory-laptop dhcdbd: Started up.
Oct 29 19:09:41 cory-laptop kernel: [   43.168000] Bluetooth: Core ver 2.11
Oct 29 19:09:41 cory-laptop kernel: [   43.168000] NET: Registered protocol family 31
Oct 29 19:09:41 cory-laptop kernel: [   43.168000] Bluetooth: HCI device and connection manager initialized
Oct 29 19:09:41 cory-laptop kernel: [   43.168000] Bluetooth: HCI socket layer initialized
Oct 29 19:09:41 cory-laptop kernel: [   43.184000] Bluetooth: L2CAP ver 2.8
Oct 29 19:09:41 cory-laptop kernel: [   43.184000] Bluetooth: L2CAP socket layer initialized
Oct 29 19:09:42 cory-laptop kernel: [   43.204000] Bluetooth: RFCOMM socket layer initialized
Oct 29 19:09:42 cory-laptop kernel: [   43.204000] Bluetooth: RFCOMM TTY layer initialized
Oct 29 19:09:42 cory-laptop kernel: [   43.204000] Bluetooth: RFCOMM ver 1.8
Oct 29 19:09:49 cory-laptop kernel: [   50.524000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:09:49 cory-laptop kernel: [   50.524000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:09:50 cory-laptop kernel: [   51.240000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:09:50 cory-laptop kernel: [   51.956000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:09:53 cory-laptop kernel: [   54.724000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:09:53 cory-laptop kernel: [   54.724000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:09:54 cory-laptop kernel: [   55.540000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:09:55 cory-laptop kernel: [   56.260000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:09:57 cory-laptop kernel: [   59.028000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:09:57 cory-laptop kernel: [   59.028000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:09:58 cory-laptop kernel: [   59.744000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:10:02 cory-laptop kernel: [   63.228000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:10:02 cory-laptop kernel: [   63.964000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:10:03 cory-laptop kernel: [   64.712000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:25 cory-laptop kernel: [  206.252000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:25 cory-laptop kernel: [  206.256000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:25 cory-laptop kernel: [  207.004000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:26 cory-laptop kernel: [  207.756000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:29 cory-laptop kernel: [  210.508000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:29 cory-laptop kernel: [  210.508000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:30 cory-laptop kernel: [  211.256000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:30 cory-laptop kernel: [  211.996000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:33 cory-laptop kernel: [  214.760000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:33 cory-laptop kernel: [  214.764000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:34 cory-laptop kernel: [  215.516000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:35 cory-laptop kernel: [  216.268000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:37 cory-laptop kernel: [  219.028000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:38 cory-laptop kernel: [  219.764000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:12:39 cory-laptop kernel: [  220.532000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:13:18 cory-laptop kernel: [  260.048000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:14:28 cory-laptop kernel: [  330.164000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:14:33 cory-laptop kernel: [  334.524000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:14:47 cory-laptop kernel: [  348.596000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:16:13 cory-laptop kernel: [  434.892000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:16:13 cory-laptop kernel: [  434.896000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:16:13 cory-laptop kernel: [  434.900000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:16:13 cory-laptop kernel: [  434.904000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:16:13 cory-laptop kernel: [  434.908000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:16:13 cory-laptop kernel: [  434.908000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:16:13 cory-laptop kernel: [  434.912000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:16:13 cory-laptop kernel: [  434.920000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:16:13 cory-laptop kernel: [  434.920000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:16:13 cory-laptop kernel: [  434.924000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:17:12 cory-laptop syslogd 1.4.1#21ubuntu3: restart.
Oct 29 19:18:18 cory-laptop kernel: [  559.672000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:20:27 cory-laptop kernel: [  688.272000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:20:36 cory-laptop kernel: [  697.360000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:20:36 cory-laptop kernel: [  698.096000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:20:37 cory-laptop kernel: [  698.848000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:04 cory-laptop kernel: [  785.616000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:04 cory-laptop kernel: [  785.616000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:05 cory-laptop kernel: [  786.364000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:05 cory-laptop kernel: [  787.116000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:08 cory-laptop kernel: [  789.868000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:08 cory-laptop kernel: [  789.868000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:09 cory-laptop kernel: [  790.616000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:10 cory-laptop kernel: [  791.364000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:12 cory-laptop kernel: [  794.116000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:12 cory-laptop kernel: [  794.120000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:13 cory-laptop kernel: [  794.864000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:14 cory-laptop kernel: [  795.616000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:17 cory-laptop kernel: [  798.364000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:17 cory-laptop kernel: [  799.116000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:22:18 cory-laptop kernel: [  799.864000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:26:35 cory-laptop kernel: [ 1056.688000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:28:24 cory-laptop kernel: [ 1165.324000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 29 19:30:23 cory-laptop exiting on signal 15
Oct 31 18:47:04 cory-laptop syslogd 1.4.1#21ubuntu3: restart.
Oct 31 18:47:04 cory-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Oct 31 18:47:04 cory-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Oct 31 18:47:04 cory-laptop kernel: Symbols match kernel version 2.6.22.
Oct 31 18:47:04 cory-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002ef40000 (usable)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000002ef40000 - 000000002ef50000 (ACPI data)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000002ef50000 - 000000002f000000 (reserved)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] 751MB LOWMEM available.
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] Zone PFN ranges:
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]   DMA             0 ->     4096
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]   Normal       4096 ->   192320
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]   HighMem    192320 ->   192320
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 31 18:47:04 cory-laptop kernel: [    0.000000]     0:        0 ->   192320
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] DMI 2.3 present.
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F0180 checksum 0
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] ACPI: RSDP 000F0180, 0014 (r0 TOSHIB)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] ACPI: RSDT 2EF40000, 0030 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] ACPI: FACP 2EF40058, 0084 (r2 TOSHIB 750        970814 TASM  4010000)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] ACPI: DSDT 2EF40110, 4B25 (r1 TOSHIB AFCF7    20030326 MSFT  100000E)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] ACPI: FACS 000EEE00, 0040
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] ACPI: DBGP 2EF400DC, 0034 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] ACPI: BOOT 2EF40030, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xd808
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f000000:cfc10000)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 190818
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] Kernel command line: root=UUID=e6f50239-1aea-4ce9-bff6-f65118a4cdb9 ro quiet splash
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] Initializing CPU#0
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 31 18:47:04 cory-laptop kernel: [    0.000000] Detected 2394.130 MHz processor.
Oct 31 18:47:04 cory-laptop kernel: [    7.082339] Console: colour VGA+ 80x25
Oct 31 18:47:04 cory-laptop kernel: [    7.083028] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 31 18:47:04 cory-laptop kernel: [    7.084080] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 31 18:47:04 cory-laptop kernel: [    7.103112] Memory: 750860k/769280k available (2015k kernel code, 17808k reserved, 916k data, 364k init, 0k highmem)
Oct 31 18:47:04 cory-laptop kernel: [    7.103123] virtual kernel memory layout:
Oct 31 18:47:04 cory-laptop kernel: [    7.103125]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Oct 31 18:47:04 cory-laptop kernel: [    7.103126]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 31 18:47:04 cory-laptop kernel: [    7.103127]     vmalloc : 0xef800000 - 0xff7fe000   ( 255 MB)
Oct 31 18:47:04 cory-laptop kernel: [    7.103128]     lowmem  : 0xc0000000 - 0xeef40000   ( 751 MB)
Oct 31 18:47:04 cory-laptop kernel: [    7.103129]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Oct 31 18:47:04 cory-laptop kernel: [    7.103130]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Oct 31 18:47:04 cory-laptop kernel: [    7.103132]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Oct 31 18:47:04 cory-laptop kernel: [    7.103135] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 31 18:47:04 cory-laptop kernel: [    7.103179] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 31 18:47:04 cory-laptop kernel: [    7.183069] Calibrating delay using timer specific routine.. 4792.21 BogoMIPS (lpj=9584434)
Oct 31 18:47:04 cory-laptop kernel: [    7.183101] Security Framework v1.0.0 initialized
Oct 31 18:47:04 cory-laptop kernel: [    7.183111] SELinux:  Disabled at boot.
Oct 31 18:47:04 cory-laptop kernel: [    7.183126] Mount-cache hash table entries: 512
Oct 31 18:47:04 cory-laptop kernel: [    7.183307] CPU: Trace cache: 12K uops, L1 D cache: 8K
Oct 31 18:47:04 cory-laptop kernel: [    7.183310] CPU: L2 cache: 256K
Oct 31 18:47:04 cory-laptop kernel: [    7.183313] CPU: Hyper-Threading is disabled
Oct 31 18:47:04 cory-laptop kernel: [    7.183329] Compat vDSO mapped to ffffe000.
Oct 31 18:47:04 cory-laptop kernel: [    7.183345] Checking 'hlt' instruction... OK.
Oct 31 18:47:04 cory-laptop kernel: [    7.199177] SMP alternatives: switching to UP code
Oct 31 18:47:04 cory-laptop kernel: [    7.199496] Freeing SMP alternatives: 11k freed
Oct 31 18:47:04 cory-laptop kernel: [    7.199860] Early unpacking initramfs... done
Oct 31 18:47:04 cory-laptop kernel: [    7.541383] ACPI: Core revision 20070126
Oct 31 18:47:04 cory-laptop kernel: [    7.541463] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 31 18:47:04 cory-laptop kernel: [    7.543290] ACPI: setting ELCR to 0200 (from 0e00)
Oct 31 18:47:04 cory-laptop kernel: [    7.543447] CPU0: Intel Mobile Intel(R) Celeron(R) CPU 2.40GHz stepping 09
Oct 31 18:47:04 cory-laptop kernel: [    7.543456] SMP motherboard not detected.
Oct 31 18:47:04 cory-laptop kernel: [    7.543458] Local APIC not detected. Using dummy APIC emulation.
Oct 31 18:47:04 cory-laptop kernel: [    7.543505] Brought up 1 CPUs
Oct 31 18:47:04 cory-laptop kernel: [    7.543674] Booting paravirtualized kernel on bare hardware
Oct 31 18:47:04 cory-laptop kernel: [    7.543746] Time: 23:46:38  Date: 09/31/107
Oct 31 18:47:04 cory-laptop kernel: [    7.543781] NET: Registered protocol family 16
Oct 31 18:47:04 cory-laptop kernel: [    7.543927] EISA bus registered
Oct 31 18:47:04 cory-laptop kernel: [    7.543945] ACPI: bus type pci registered
Oct 31 18:47:04 cory-laptop kernel: [    7.544056] PCI: PCI BIOS revision 2.10 entry at 0xfd317, last bus=3
Oct 31 18:47:04 cory-laptop kernel: [    7.544059] PCI: Using configuration type 1
Oct 31 18:47:04 cory-laptop kernel: [    7.544061] Setting up standard PCI resources
Oct 31 18:47:04 cory-laptop kernel: [    7.549556] ACPI: Interpreter enabled
Oct 31 18:47:04 cory-laptop kernel: [    7.549562] ACPI: (supports S0 S3 S4 S5)
Oct 31 18:47:04 cory-laptop kernel: [    7.549586] ACPI: Using PIC for interrupt routing
Oct 31 18:47:04 cory-laptop kernel: [    7.557947] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 31 18:47:04 cory-laptop kernel: [    7.558526] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
Oct 31 18:47:04 cory-laptop kernel: [    7.558531] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
Oct 31 18:47:04 cory-laptop kernel: [    7.558793] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
Oct 31 18:47:04 cory-laptop kernel: [    7.558895] PCI: Transparent bridge - 0000:00:1e.0
Oct 31 18:47:04 cory-laptop kernel: [    7.561040] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
Oct 31 18:47:04 cory-laptop kernel: [    7.561165] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
Oct 31 18:47:04 cory-laptop kernel: [    7.561289] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
Oct 31 18:47:04 cory-laptop kernel: [    7.561414] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
Oct 31 18:47:04 cory-laptop kernel: [    7.561546] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
Oct 31 18:47:04 cory-laptop kernel: [    7.561671] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
Oct 31 18:47:04 cory-laptop kernel: [    7.561796] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
Oct 31 18:47:04 cory-laptop kernel: [    7.561920] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
Oct 31 18:47:04 cory-laptop kernel: [    7.562271] ACPI: Power Resource [PFAN] (off)
Oct 31 18:47:04 cory-laptop kernel: [    7.562291] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 31 18:47:04 cory-laptop kernel: [    7.562316] pnp: PnP ACPI init
Oct 31 18:47:04 cory-laptop kernel: [    7.562333] ACPI: bus type pnp registered
Oct 31 18:47:04 cory-laptop kernel: [    7.565849] pnp: PnP ACPI: found 10 devices
Oct 31 18:47:04 cory-laptop kernel: [    7.565854] ACPI: ACPI bus type pnp unregistered
Oct 31 18:47:04 cory-laptop kernel: [    7.565859] PnPBIOS: Disabled by ACPI PNP
Oct 31 18:47:04 cory-laptop kernel: [    7.565944] PCI: Using ACPI for IRQ routing
Oct 31 18:47:04 cory-laptop kernel: [    7.565949] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 31 18:47:04 cory-laptop kernel: [    7.570513] NET: Registered protocol family 8
Oct 31 18:47:04 cory-laptop kernel: [    7.570516] NET: Registered protocol family 20
Oct 31 18:47:04 cory-laptop kernel: [    7.570652] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
Oct 31 18:47:04 cory-laptop kernel: [    7.570657] pnp: 00:00: iomem range 0xe0000-0xeffff could not be reserved
Oct 31 18:47:04 cory-laptop kernel: [    7.570660] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
Oct 31 18:47:04 cory-laptop kernel: [    7.570663] pnp: 00:00: iomem range 0x100000-0x2ef3ffff could not be reserved
Oct 31 18:47:04 cory-laptop kernel: [    7.574420] Time: tsc clocksource has been installed.
Oct 31 18:47:04 cory-laptop kernel: [    7.601216] PCI: Bus 2, cardbus bridge: 0000:01:0b.0
Oct 31 18:47:04 cory-laptop kernel: [    7.601219]   IO window: 0000c000-0000c0ff
Oct 31 18:47:04 cory-laptop kernel: [    7.601224]   IO window: 0000c400-0000c4ff
Oct 31 18:47:04 cory-laptop kernel: [    7.601229]   PREFETCH window: 38000000-3bffffff
Oct 31 18:47:04 cory-laptop kernel: [    7.601234]   MEM window: 40000000-43ffffff
Oct 31 18:47:04 cory-laptop kernel: [    7.601239] PCI: Bridge: 0000:00:1e.0
Oct 31 18:47:04 cory-laptop kernel: [    7.601243]   IO window: c000-cfff
Oct 31 18:47:04 cory-laptop kernel: [    7.601248]   MEM window: cff00000-cfffffff
Oct 31 18:47:04 cory-laptop kernel: [    7.601253]   PREFETCH window: 38000000-3bffffff
Oct 31 18:47:04 cory-laptop kernel: [    7.601287] PCI: Enabling device 0000:01:0b.0 (0000 -> 0003)
Oct 31 18:47:04 cory-laptop kernel: [    7.601544] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Oct 31 18:47:04 cory-laptop kernel: [    7.601552] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:47:04 cory-laptop kernel: [    7.601579] NET: Registered protocol family 2
Oct 31 18:47:04 cory-laptop kernel: [    7.638371] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 31 18:47:04 cory-laptop kernel: [    7.638564] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Oct 31 18:47:04 cory-laptop kernel: [    7.640647] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 31 18:47:04 cory-laptop kernel: [    7.641380] TCP: Hash tables configured (established 131072 bind 65536)
Oct 31 18:47:04 cory-laptop kernel: [    7.641389] TCP reno registered
Oct 31 18:47:04 cory-laptop kernel: [    7.650497] checking if image is initramfs... it is
Oct 31 18:47:04 cory-laptop kernel: [    8.101574] Switched to high resolution mode on CPU 0
Oct 31 18:47:04 cory-laptop kernel: [    8.317373] Freeing initrd memory: 7115k freed
Oct 31 18:47:04 cory-laptop kernel: [    8.317565] Simple Boot Flag at 0x7c set to 0x1
Oct 31 18:47:04 cory-laptop kernel: [    8.317845] audit: initializing netlink socket (disabled)
Oct 31 18:47:04 cory-laptop kernel: [    8.317864] audit(1193874397.976:1): initialized
Oct 31 18:47:04 cory-laptop kernel: [    8.320813] VFS: Disk quotas dquot_6.5.1
Oct 31 18:47:04 cory-laptop kernel: [    8.320900] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 31 18:47:04 cory-laptop kernel: [    8.321071] io scheduler noop registered
Oct 31 18:47:04 cory-laptop kernel: [    8.321075] io scheduler anticipatory registered
Oct 31 18:47:04 cory-laptop kernel: [    8.321077] io scheduler deadline registered
Oct 31 18:47:04 cory-laptop kernel: [    8.321107] io scheduler cfq registered (default)
Oct 31 18:47:04 cory-laptop kernel: [    8.321435] isapnp: Scanning for PnP cards...
Oct 31 18:47:04 cory-laptop kernel: [    8.673858] isapnp: No Plug & Play device found
Oct 31 18:47:04 cory-laptop kernel: [    8.750427] Real Time Clock Driver v1.12ac
Oct 31 18:47:04 cory-laptop kernel: [    8.750571] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 31 18:47:04 cory-laptop kernel: [    8.752140] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
Oct 31 18:47:04 cory-laptop kernel: [    8.752356] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Oct 31 18:47:04 cory-laptop kernel: [    8.752360] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:47:04 cory-laptop kernel: [    8.752370] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Oct 31 18:47:04 cory-laptop kernel: [    8.753365] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 31 18:47:04 cory-laptop kernel: [    8.753704] input: Macintosh mouse button emulation as /class/input/input0
Oct 31 18:47:04 cory-laptop kernel: [    8.753830] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 31 18:47:04 cory-laptop kernel: [    8.769081] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 31 18:47:04 cory-laptop kernel: [    8.769090] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 31 18:47:04 cory-laptop kernel: [    8.769435] mice: PS/2 mouse device common for all mice
Oct 31 18:47:04 cory-laptop kernel: [    8.769635] EISA: Probing bus 0 at eisa.0
Oct 31 18:47:04 cory-laptop kernel: [    8.769644] Cannot allocate resource for EISA slot 1
Oct 31 18:47:04 cory-laptop kernel: [    8.769662] EISA: Detected 0 cards.
Oct 31 18:47:04 cory-laptop kernel: [    8.769852] TCP cubic registered
Oct 31 18:47:04 cory-laptop kernel: [    8.769868] NET: Registered protocol family 1
Oct 31 18:47:04 cory-laptop kernel: [    8.769898] Using IPI No-Shortcut mode
Oct 31 18:47:04 cory-laptop kernel: [    8.770140]   Magic number: 11:33:809
Oct 31 18:47:04 cory-laptop kernel: [    8.770297]   hash matches device ptys3
Oct 31 18:47:04 cory-laptop kernel: [    8.770819] Freeing unused kernel memory: 364k freed
Oct 31 18:47:04 cory-laptop kernel: [    8.788465] input: AT Translated Set 2 keyboard as /class/input/input1
Oct 31 18:47:04 cory-laptop kernel: [   10.077764] AppArmor: AppArmor initialized<5>audit(1193874399.976:2):  type=1505 info="AppArmor initialized" pid=1183
Oct 31 18:47:04 cory-laptop kernel: [   10.089127] fuse init (API version 7.8)
Oct 31 18:47:04 cory-laptop kernel: [   10.097362] Failure registering capabilities with primary security module.
Oct 31 18:47:04 cory-laptop kernel: [   10.112309] ACPI: Transitioning device [FAN] to D3
Oct 31 18:47:04 cory-laptop kernel: [   10.112314] ACPI: Transitioning device [FAN] to D3
Oct 31 18:47:04 cory-laptop kernel: [   10.112319] ACPI: Fan [FAN] (off)
Oct 31 18:47:04 cory-laptop kernel: [   10.119417] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct 31 18:47:04 cory-laptop kernel: [   10.120791] ACPI: Thermal Zone [THRM] (32 C)
Oct 31 18:47:04 cory-laptop kernel: [   10.986086] usbcore: registered new interface driver usbfs
Oct 31 18:47:04 cory-laptop kernel: [   10.986120] usbcore: registered new interface driver hub
Oct 31 18:47:04 cory-laptop kernel: [   10.986155] usbcore: registered new device driver usb
Oct 31 18:47:04 cory-laptop kernel: [   10.987275] USB Universal Host Controller Interface driver v3.0
Oct 31 18:47:04 cory-laptop kernel: [   10.987624] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Oct 31 18:47:04 cory-laptop kernel: [   10.987633] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:47:04 cory-laptop kernel: [   10.987651] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 31 18:47:04 cory-laptop kernel: [   10.987861] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Oct 31 18:47:04 cory-laptop kernel: [   10.987894] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018c0
Oct 31 18:47:04 cory-laptop kernel: [   10.988059] usb usb1: configuration #1 chosen from 1 choice
Oct 31 18:47:04 cory-laptop kernel: [   10.988094] hub 1-0:1.0: USB hub found
Oct 31 18:47:04 cory-laptop kernel: [   10.988105] hub 1-0:1.0: 2 ports detected
Oct 31 18:47:04 cory-laptop kernel: [   11.042165] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
Oct 31 18:47:04 cory-laptop kernel: [   11.042170] e100: Copyright(c) 1999-2006 Intel Corporation
Oct 31 18:47:04 cory-laptop kernel: [   11.100434] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Oct 31 18:47:04 cory-laptop kernel: [   11.100695] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Oct 31 18:47:04 cory-laptop kernel: [   11.100699] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:47:04 cory-laptop kernel: [   11.100723] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 31 18:47:04 cory-laptop kernel: [   11.100776] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Oct 31 18:47:04 cory-laptop kernel: [   11.100821] ehci_hcd 0000:00:1d.7: debug port 1
Oct 31 18:47:04 cory-laptop kernel: [   11.100839] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x3c080000
Oct 31 18:47:04 cory-laptop kernel: [   11.104727] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 31 18:47:04 cory-laptop kernel: [   11.104837] usb usb2: configuration #1 chosen from 1 choice
Oct 31 18:47:04 cory-laptop kernel: [   11.104879] hub 2-0:1.0: USB hub found
Oct 31 18:47:04 cory-laptop kernel: [   11.104889] hub 2-0:1.0: 6 ports detected
Oct 31 18:47:04 cory-laptop kernel: [   11.111238] SCSI subsystem initialized
Oct 31 18:47:04 cory-laptop kernel: [   11.208962] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
Oct 31 18:47:04 cory-laptop kernel: [   11.208968] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:47:04 cory-laptop kernel: [   11.232544] e100: eth0: e100_probe: addr 0xcffff000, irq 11, MAC addr 00:08:0D:2F:C7:65
Oct 31 18:47:04 cory-laptop kernel: [   11.270256] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Oct 31 18:47:04 cory-laptop kernel: [   11.270260] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:47:04 cory-laptop kernel: [   11.270446] scsi0 : ata_piix
Oct 31 18:47:04 cory-laptop kernel: [   11.270521] scsi1 : ata_piix
Oct 31 18:47:04 cory-laptop kernel: [   11.270682] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Oct 31 18:47:04 cory-laptop kernel: [   11.270686] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Oct 31 18:47:04 cory-laptop kernel: [    4.300000] Marking TSC unstable due to: possible TSC halt in C2.
Oct 31 18:47:04 cory-laptop kernel: [    4.324000] Time: acpi_pm clocksource has been installed.
Oct 31 18:47:04 cory-laptop kernel: [    4.340000] ata1.00: ATA-6: IC25N040ATMR04-0, MO2OAD0A, max UDMA/100
Oct 31 18:47:04 cory-laptop kernel: [    4.340000] ata1.00: 78140160 sectors, multi 0: LBA48 
Oct 31 18:47:04 cory-laptop kernel: [    4.356000] ata1.00: configured for UDMA/100
Oct 31 18:47:04 cory-laptop kernel: [    4.676000] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R2412, 1330, max UDMA/33
Oct 31 18:47:05 cory-laptop kernel: [    4.740000] usb 1-2: new low speed USB device using uhci_hcd and address 2
Oct 31 18:47:05 cory-laptop kernel: [    4.840000] ata2.00: configured for UDMA/33
Oct 31 18:47:05 cory-laptop kernel: [    4.840000] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATMR04-0 MO2O PQ: 0 ANSI: 5
Oct 31 18:47:05 cory-laptop kernel: [    4.840000] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2412 1330 PQ: 0 ANSI: 5
Oct 31 18:47:05 cory-laptop kernel: [    4.864000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Oct 31 18:47:05 cory-laptop kernel: [    4.864000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 18:47:05 cory-laptop kernel: [    4.864000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 18:47:05 cory-laptop kernel: [    4.864000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Oct 31 18:47:05 cory-laptop kernel: [    4.864000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 18:47:05 cory-laptop kernel: [    4.864000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 18:47:05 cory-laptop kernel: [    4.864000]  sda: sda1 sda2 < sda5 >
Oct 31 18:47:05 cory-laptop kernel: [    4.920000] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 31 18:47:05 cory-laptop kernel: [    4.924000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 31 18:47:05 cory-laptop kernel: [    4.924000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Oct 31 18:47:05 cory-laptop kernel: [    4.936000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Oct 31 18:47:05 cory-laptop kernel: [    4.936000] Uniform CD-ROM driver Revision: 3.20
Oct 31 18:47:05 cory-laptop kernel: [    4.936000] usb 1-2: configuration #1 chosen from 1 choice
Oct 31 18:47:05 cory-laptop kernel: [    5.004000] usbcore: registered new interface driver hiddev
Oct 31 18:47:05 cory-laptop kernel: [    5.044000] input: HID 1241:1166 as /class/input/input2
Oct 31 18:47:05 cory-laptop kernel: [    5.044000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:1d.0-2
Oct 31 18:47:05 cory-laptop kernel: [    5.044000] usbcore: registered new interface driver usbhid
Oct 31 18:47:05 cory-laptop kernel: [    5.044000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 31 18:47:05 cory-laptop kernel: [    5.244000] Attempting manual resume
Oct 31 18:47:05 cory-laptop kernel: [    5.304000] kjournald starting.  Commit interval 5 seconds
Oct 31 18:47:05 cory-laptop kernel: [    5.304000] EXT3-fs: mounted filesystem with ordered data mode.
Oct 31 18:47:05 cory-laptop kernel: [   19.412000] Linux agpgart interface v0.102 (c) Dave Jones
Oct 31 18:47:05 cory-laptop kernel: [   19.456000] agpgart: Detected an Intel 855GM Chipset.
Oct 31 18:47:05 cory-laptop kernel: [   19.456000] agpgart: Detected 16252K stolen memory.
Oct 31 18:47:05 cory-laptop kernel: [   19.468000] agpgart: AGP aperture is 128M @ 0xd8000000
Oct 31 18:47:05 cory-laptop kernel: [   20.216000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 31 18:47:05 cory-laptop kernel: [   20.232000] input: PC Speaker as /class/input/input3
Oct 31 18:47:05 cory-laptop kernel: [   20.408000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 31 18:47:05 cory-laptop kernel: [   20.604000] iTCO_vendor_support: vendor-support=0
Oct 31 18:47:05 cory-laptop kernel: [   20.616000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Oct 31 18:47:05 cory-laptop kernel: [   20.692000] Yenta: CardBus bridge found at 0000:01:0b.0 [1179:0001]
Oct 31 18:47:05 cory-laptop kernel: [   20.852000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
Oct 31 18:47:05 cory-laptop kernel: [   20.852000] Socket status: 30000020
Oct 31 18:47:05 cory-laptop kernel: [   20.852000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
Oct 31 18:47:05 cory-laptop kernel: [   20.852000] cs: IO port probe 0xc000-0xcfff: clean.
Oct 31 18:47:05 cory-laptop kernel: [   20.852000] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xcfffffff
Oct 31 18:47:05 cory-laptop kernel: [   20.852000] pcmcia: parent PCI bridge Memory window: 0x38000000 - 0x3bffffff
Oct 31 18:47:05 cory-laptop kernel: [   21.044000] input: PS/2 Mouse as /class/input/input4
Oct 31 18:47:05 cory-laptop kernel: [   21.088000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input5
Oct 31 18:47:05 cory-laptop kernel: [   21.100000] pnp: Device 00:09 activated.
Oct 31 18:47:05 cory-laptop kernel: [   21.100000] parport_pc 00:09: reported by Plug and Play ACPI
Oct 31 18:47:05 cory-laptop kernel: [   21.100000] pnp: Device 00:09 disabled.
Oct 31 18:47:05 cory-laptop kernel: [   21.100000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0xd860)
Oct 31 18:47:05 cory-laptop kernel: [   21.100000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Oct 31 18:47:05 cory-laptop kernel: [   21.136000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
Oct 31 18:47:05 cory-laptop kernel: [   21.136000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:47:05 cory-laptop kernel: [   21.508000] pccard: CardBus card inserted into slot 0
Oct 31 18:47:05 cory-laptop kernel: [   21.560000] intel8x0_measure_ac97_clock: measured 54950 usecs
Oct 31 18:47:05 cory-laptop kernel: [   21.560000] intel8x0: clocking to 48000
Oct 31 18:47:05 cory-laptop kernel: [   21.796000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
Oct 31 18:47:05 cory-laptop kernel: [   21.796000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Oct 31 18:47:05 cory-laptop kernel: [   21.800000] cs: IO port probe 0x820-0x8ff: clean.
Oct 31 18:47:05 cory-laptop kernel: [   21.800000] cs: IO port probe 0xc00-0xcf7: clean.
Oct 31 18:47:05 cory-laptop kernel: [   21.800000] cs: IO port probe 0xa00-0xaff: clean.
Oct 31 18:47:05 cory-laptop kernel: [   21.832000] acx: Loaded combined PCI/USB driver, firmware_ver=default
Oct 31 18:47:05 cory-laptop kernel: [   21.832000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Oct 31 18:47:05 cory-laptop kernel: [   21.832000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Oct 31 18:47:05 cory-laptop kernel: [   21.832000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:47:05 cory-laptop kernel: [   21.832000] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x40020000, phymem2:0x40000000, mem1:0xefab4000, mem1_size:8192, mem2:0xefb80000, mem2_size:131072
Oct 31 18:47:05 cory-laptop kernel: [   21.836000] acx: loading firmware for acx1111 chipset with radio ID 16
Oct 31 18:47:05 cory-laptop kernel: [   22.692000] NVS_vendor_offs:0221 probe_delay:200 eof_memory:1114112
Oct 31 18:47:05 cory-laptop kernel: [   22.692000] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
Oct 31 18:47:05 cory-laptop kernel: [   22.692000] AntennaID:00 Len:02 Data:01 02 
Oct 31 18:47:05 cory-laptop kernel: [   22.692000] PowerLevelID:01 Len:02 Data:001E 000A 
Oct 31 18:47:05 cory-laptop kernel: [   22.692000] DataRatesID:02 Len:05 Data:02 04 11 22 44 
Oct 31 18:47:05 cory-laptop kernel: [   22.692000] DomainID:03 Len:06 Data:10 20 30 31 32 40 
Oct 31 18:47:05 cory-laptop kernel: [   22.692000] ProductID:04 Len:09 Data:TI ACX100
Oct 31 18:47:05 cory-laptop kernel: [   22.692000] ManufacturerID:05 Len:07 Data:TI Test
Oct 31 18:47:05 cory-laptop kernel: [   22.752000] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
Oct 31 18:47:05 cory-laptop kernel: [   22.752000] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.22-14-generic
Oct 31 18:47:05 cory-laptop kernel: [   22.752000] usbcore: registered new interface driver acx_usb
Oct 31 18:47:05 cory-laptop kernel: [   23.312000] lp: driver loaded but no devices found
Oct 31 18:47:05 cory-laptop kernel: [   23.388000] Adding 698788k swap on /dev/sda5.  Priority:-1 extents:1 across:698788k
Oct 31 18:47:05 cory-laptop kernel: [   23.768000] EXT3 FS on sda1, internal journal
Oct 31 18:47:05 cory-laptop kernel: [   24.484000] NET: Registered protocol family 17
Oct 31 18:47:05 cory-laptop kernel: [   25.564000] ACPI: Battery Slot [BAT1] (battery present)
Oct 31 18:47:05 cory-laptop kernel: [   25.804000] No dock devices found.
Oct 31 18:47:05 cory-laptop kernel: [   25.836000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
Oct 31 18:47:05 cory-laptop kernel: [   25.836000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
Oct 31 18:47:05 cory-laptop kernel: [   25.840000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
Oct 31 18:47:05 cory-laptop kernel: [   25.840000] toshiba_acpi: ktoshkeyd will check 2 times per second
Oct 31 18:47:05 cory-laptop kernel: [   25.844000] toshiba_acpi: Dropped 0 keys from the queue on startup
Oct 31 18:47:05 cory-laptop kernel: [   25.860000] ACPI: AC Adapter [ADP1] (on-line)
Oct 31 18:47:05 cory-laptop kernel: [   25.920000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
Oct 31 18:47:05 cory-laptop kernel: [   25.988000] input: Power Button (FF) as /class/input/input6
Oct 31 18:47:05 cory-laptop kernel: [   25.996000] ACPI: Power Button (FF) [PWRF]
Oct 31 18:47:05 cory-laptop kernel: [   26.036000] input: Lid Switch as /class/input/input7
Oct 31 18:47:05 cory-laptop kernel: [   26.044000] ACPI: Lid Switch [LID]
Oct 31 18:47:05 cory-laptop kernel: [   26.084000] input: Power Button (CM) as /class/input/input8
Oct 31 18:47:05 cory-laptop kernel: [   26.092000] ACPI: Power Button (CM) [PWRB]
Oct 31 18:47:05 cory-laptop kernel: [   27.620000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:47:05 cory-laptop kernel: [   27.800000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Oct 31 18:47:05 cory-laptop kernel: [   27.800000] Intel ICH Modem: probe of 0000:00:1f.6 failed with error -13
Oct 31 18:47:12 cory-laptop kernel: [   34.644000] NET: Registered protocol family 10
Oct 31 18:47:12 cory-laptop kernel: [   34.644000] lo: Disabled Privacy Extensions
Oct 31 18:47:12 cory-laptop kernel: [   34.644000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 31 18:47:13 cory-laptop kernel: [   35.644000] wlan0: duplicate address detected!
Oct 31 18:47:18 cory-laptop kernel: [   40.352000] [drm] Initialized drm 1.1.0 20060810
Oct 31 18:47:18 cory-laptop kernel: [   40.412000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:47:18 cory-laptop kernel: [   40.412000] [drm] Initialized i915 1.6.0 20060119 on minor 0
Oct 31 18:47:18 cory-laptop kernel: [   40.412000] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
Oct 31 18:47:18 cory-laptop kernel: [   40.412000] [drm] Initialized i915 1.6.0 20060119 on minor 1
Oct 31 18:47:18 cory-laptop kernel: [   40.824000] ppdev: user-space parallel port driver
Oct 31 18:47:19 cory-laptop kernel: [   41.432000] audit(1193874439.256:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4928 profile="/usr/sbin/cupsd"
Oct 31 18:47:19 cory-laptop kernel: [   41.628000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
Oct 31 18:47:19 cory-laptop kernel: [   41.628000] apm: overridden by ACPI.
Oct 31 18:47:20 cory-laptop kernel: [   42.184000] Failure registering capabilities with primary security module.
Oct 31 18:47:20 cory-laptop dhcdbd: Started up.
Oct 31 18:47:20 cory-laptop kernel: [   42.480000] Bluetooth: Core ver 2.11
Oct 31 18:47:20 cory-laptop kernel: [   42.480000] NET: Registered protocol family 31
Oct 31 18:47:20 cory-laptop kernel: [   42.480000] Bluetooth: HCI device and connection manager initialized
Oct 31 18:47:20 cory-laptop kernel: [   42.480000] Bluetooth: HCI socket layer initialized
Oct 31 18:47:20 cory-laptop kernel: [   42.500000] Bluetooth: L2CAP ver 2.8
Oct 31 18:47:20 cory-laptop kernel: [   42.500000] Bluetooth: L2CAP socket layer initialized
Oct 31 18:47:20 cory-laptop kernel: [   42.560000] Bluetooth: RFCOMM socket layer initialized
Oct 31 18:47:20 cory-laptop kernel: [   42.560000] Bluetooth: RFCOMM TTY layer initialized
Oct 31 18:47:20 cory-laptop kernel: [   42.560000] Bluetooth: RFCOMM ver 1.8
Oct 31 18:48:56 cory-laptop syslogd 1.4.1#21ubuntu3: restart.
Oct 31 18:48:57 cory-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Oct 31 18:48:57 cory-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Oct 31 18:48:57 cory-laptop kernel: Symbols match kernel version 2.6.22.
Oct 31 18:48:57 cory-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002ef40000 (usable)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000002ef40000 - 000000002ef50000 (ACPI data)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000002ef50000 - 000000002f000000 (reserved)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] 751MB LOWMEM available.
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] Zone PFN ranges:
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]   DMA             0 ->     4096
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]   Normal       4096 ->   192320
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]   HighMem    192320 ->   192320
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 31 18:48:57 cory-laptop kernel: [    0.000000]     0:        0 ->   192320
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] DMI 2.3 present.
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F0180 checksum 0
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] ACPI: RSDP 000F0180, 0014 (r0 TOSHIB)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] ACPI: RSDT 2EF40000, 0030 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] ACPI: FACP 2EF40058, 0084 (r2 TOSHIB 750        970814 TASM  4010000)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] ACPI: DSDT 2EF40110, 4B25 (r1 TOSHIB AFCF7    20030326 MSFT  100000E)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] ACPI: FACS 000EEE00, 0040
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] ACPI: DBGP 2EF400DC, 0034 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] ACPI: BOOT 2EF40030, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xd808
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f000000:cfc10000)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 190818
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] Kernel command line: root=UUID=e6f50239-1aea-4ce9-bff6-f65118a4cdb9 ro quiet splash
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] Initializing CPU#0
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 31 18:48:57 cory-laptop kernel: [    0.000000] Detected 2394.113 MHz processor.
Oct 31 18:48:57 cory-laptop kernel: [    7.872132] Console: colour VGA+ 80x25
Oct 31 18:48:57 cory-laptop kernel: [    7.872814] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 31 18:48:57 cory-laptop kernel: [    7.873831] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 31 18:48:57 cory-laptop kernel: [    7.893020] Memory: 750860k/769280k available (2015k kernel code, 17808k reserved, 916k data, 364k init, 0k highmem)
Oct 31 18:48:57 cory-laptop kernel: [    7.893032] virtual kernel memory layout:
Oct 31 18:48:57 cory-laptop kernel: [    7.893034]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Oct 31 18:48:57 cory-laptop kernel: [    7.893035]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 31 18:48:57 cory-laptop kernel: [    7.893036]     vmalloc : 0xef800000 - 0xff7fe000   ( 255 MB)
Oct 31 18:48:57 cory-laptop kernel: [    7.893037]     lowmem  : 0xc0000000 - 0xeef40000   ( 751 MB)
Oct 31 18:48:57 cory-laptop kernel: [    7.893038]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Oct 31 18:48:57 cory-laptop kernel: [    7.893039]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Oct 31 18:48:57 cory-laptop kernel: [    7.893041]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Oct 31 18:48:57 cory-laptop kernel: [    7.893044] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 31 18:48:57 cory-laptop kernel: [    7.893088] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 31 18:48:57 cory-laptop kernel: [    7.972978] Calibrating delay using timer specific routine.. 4792.33 BogoMIPS (lpj=9584660)
Oct 31 18:48:57 cory-laptop kernel: [    7.973009] Security Framework v1.0.0 initialized
Oct 31 18:48:57 cory-laptop kernel: [    7.973019] SELinux:  Disabled at boot.
Oct 31 18:48:57 cory-laptop kernel: [    7.973033] Mount-cache hash table entries: 512
Oct 31 18:48:57 cory-laptop kernel: [    7.973212] CPU: Trace cache: 12K uops, L1 D cache: 8K
Oct 31 18:48:57 cory-laptop kernel: [    7.973216] CPU: L2 cache: 256K
Oct 31 18:48:57 cory-laptop kernel: [    7.973218] CPU: Hyper-Threading is disabled
Oct 31 18:48:57 cory-laptop kernel: [    7.973234] Compat vDSO mapped to ffffe000.
Oct 31 18:48:57 cory-laptop kernel: [    7.973250] Checking 'hlt' instruction... OK.
Oct 31 18:48:57 cory-laptop kernel: [    7.989081] SMP alternatives: switching to UP code
Oct 31 18:48:57 cory-laptop kernel: [    7.989386] Freeing SMP alternatives: 11k freed
Oct 31 18:48:57 cory-laptop kernel: [    7.989741] Early unpacking initramfs... done
Oct 31 18:48:57 cory-laptop kernel: [    8.331445] ACPI: Core revision 20070126
Oct 31 18:48:57 cory-laptop kernel: [    8.331520] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 31 18:48:57 cory-laptop kernel: [    8.333350] ACPI: setting ELCR to 0200 (from 0e00)
Oct 31 18:48:57 cory-laptop kernel: [    8.333510] CPU0: Intel Mobile Intel(R) Celeron(R) CPU 2.40GHz stepping 09
Oct 31 18:48:57 cory-laptop kernel: [    8.333518] SMP motherboard not detected.
Oct 31 18:48:57 cory-laptop kernel: [    8.333521] Local APIC not detected. Using dummy APIC emulation.
Oct 31 18:48:57 cory-laptop kernel: [    8.333567] Brought up 1 CPUs
Oct 31 18:48:57 cory-laptop kernel: [    8.333736] Booting paravirtualized kernel on bare hardware
Oct 31 18:48:57 cory-laptop kernel: [    8.333808] Time: 23:48:30  Date: 09/31/107
Oct 31 18:48:57 cory-laptop kernel: [    8.333843] NET: Registered protocol family 16
Oct 31 18:48:57 cory-laptop kernel: [    8.333990] EISA bus registered
Oct 31 18:48:57 cory-laptop kernel: [    8.334008] ACPI: bus type pci registered
Oct 31 18:48:57 cory-laptop kernel: [    8.334121] PCI: PCI BIOS revision 2.10 entry at 0xfd317, last bus=3
Oct 31 18:48:57 cory-laptop kernel: [    8.334123] PCI: Using configuration type 1
Oct 31 18:48:57 cory-laptop kernel: [    8.334125] Setting up standard PCI resources
Oct 31 18:48:57 cory-laptop kernel: [    8.339628] ACPI: Interpreter enabled
Oct 31 18:48:57 cory-laptop kernel: [    8.339634] ACPI: (supports S0 S3 S4 S5)
Oct 31 18:48:57 cory-laptop kernel: [    8.339657] ACPI: Using PIC for interrupt routing
Oct 31 18:48:57 cory-laptop kernel: [    8.348118] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 31 18:48:57 cory-laptop kernel: [    8.348704] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
Oct 31 18:48:57 cory-laptop kernel: [    8.348709] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
Oct 31 18:48:57 cory-laptop kernel: [    8.348973] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
Oct 31 18:48:57 cory-laptop kernel: [    8.349075] PCI: Transparent bridge - 0000:00:1e.0
Oct 31 18:48:57 cory-laptop kernel: [    8.351142] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
Oct 31 18:48:57 cory-laptop kernel: [    8.351269] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
Oct 31 18:48:57 cory-laptop kernel: [    8.351392] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
Oct 31 18:48:57 cory-laptop kernel: [    8.351518] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
Oct 31 18:48:57 cory-laptop kernel: [    8.351649] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
Oct 31 18:48:57 cory-laptop kernel: [    8.351775] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
Oct 31 18:48:57 cory-laptop kernel: [    8.351901] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
Oct 31 18:48:57 cory-laptop kernel: [    8.352025] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
Oct 31 18:48:57 cory-laptop kernel: [    8.352448] ACPI: Power Resource [PFAN] (off)
Oct 31 18:48:57 cory-laptop kernel: [    8.352471] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 31 18:48:57 cory-laptop kernel: [    8.352495] pnp: PnP ACPI init
Oct 31 18:48:57 cory-laptop kernel: [    8.352513] ACPI: bus type pnp registered
Oct 31 18:48:57 cory-laptop kernel: [    8.355923] pnp: PnP ACPI: found 10 devices
Oct 31 18:48:57 cory-laptop kernel: [    8.355928] ACPI: ACPI bus type pnp unregistered
Oct 31 18:48:57 cory-laptop kernel: [    8.355933] PnPBIOS: Disabled by ACPI PNP
Oct 31 18:48:57 cory-laptop kernel: [    8.356019] PCI: Using ACPI for IRQ routing
Oct 31 18:48:57 cory-laptop kernel: [    8.356024] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 31 18:48:57 cory-laptop kernel: [    8.360593] NET: Registered protocol family 8
Oct 31 18:48:57 cory-laptop kernel: [    8.360596] NET: Registered protocol family 20
Oct 31 18:48:57 cory-laptop kernel: [    8.360734] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
Oct 31 18:48:57 cory-laptop kernel: [    8.360738] pnp: 00:00: iomem range 0xe0000-0xeffff could not be reserved
Oct 31 18:48:57 cory-laptop kernel: [    8.360741] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
Oct 31 18:48:57 cory-laptop kernel: [    8.360744] pnp: 00:00: iomem range 0x100000-0x2ef3ffff could not be reserved
Oct 31 18:48:57 cory-laptop kernel: [    8.364329] Time: tsc clocksource has been installed.
Oct 31 18:48:57 cory-laptop kernel: [    8.391300] PCI: Bus 2, cardbus bridge: 0000:01:0b.0
Oct 31 18:48:57 cory-laptop kernel: [    8.391303]   IO window: 0000c000-0000c0ff
Oct 31 18:48:57 cory-laptop kernel: [    8.391308]   IO window: 0000c400-0000c4ff
Oct 31 18:48:57 cory-laptop kernel: [    8.391313]   PREFETCH window: 38000000-3bffffff
Oct 31 18:48:57 cory-laptop kernel: [    8.391318]   MEM window: 40000000-43ffffff
Oct 31 18:48:57 cory-laptop kernel: [    8.391323] PCI: Bridge: 0000:00:1e.0
Oct 31 18:48:57 cory-laptop kernel: [    8.391326]   IO window: c000-cfff
Oct 31 18:48:57 cory-laptop kernel: [    8.391332]   MEM window: cff00000-cfffffff
Oct 31 18:48:57 cory-laptop kernel: [    8.391337]   PREFETCH window: 38000000-3bffffff
Oct 31 18:48:57 cory-laptop kernel: [    8.391372] PCI: Enabling device 0000:01:0b.0 (0000 -> 0003)
Oct 31 18:48:57 cory-laptop kernel: [    8.391628] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Oct 31 18:48:57 cory-laptop kernel: [    8.391636] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:48:57 cory-laptop kernel: [    8.391663] NET: Registered protocol family 2
Oct 31 18:48:57 cory-laptop kernel: [    8.428280] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 31 18:48:57 cory-laptop kernel: [    8.428485] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Oct 31 18:48:57 cory-laptop kernel: [    8.430555] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 31 18:48:57 cory-laptop kernel: [    8.431289] TCP: Hash tables configured (established 131072 bind 65536)
Oct 31 18:48:57 cory-laptop kernel: [    8.431298] TCP reno registered
Oct 31 18:48:57 cory-laptop kernel: [    8.440408] checking if image is initramfs... it is
Oct 31 18:48:57 cory-laptop kernel: [    8.891482] Switched to high resolution mode on CPU 0
Oct 31 18:48:57 cory-laptop kernel: [    9.107101] Freeing initrd memory: 7115k freed
Oct 31 18:48:57 cory-laptop kernel: [    9.107292] Simple Boot Flag at 0x7c set to 0x1
Oct 31 18:48:57 cory-laptop kernel: [    9.107576] audit: initializing netlink socket (disabled)
Oct 31 18:48:57 cory-laptop kernel: [    9.107594] audit(1193874509.976:1): initialized
Oct 31 18:48:57 cory-laptop kernel: [    9.110547] VFS: Disk quotas dquot_6.5.1
Oct 31 18:48:57 cory-laptop kernel: [    9.110633] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 31 18:48:57 cory-laptop kernel: [    9.110806] io scheduler noop registered
Oct 31 18:48:57 cory-laptop kernel: [    9.110809] io scheduler anticipatory registered
Oct 31 18:48:57 cory-laptop kernel: [    9.110812] io scheduler deadline registered
Oct 31 18:48:57 cory-laptop kernel: [    9.110841] io scheduler cfq registered (default)
Oct 31 18:48:57 cory-laptop kernel: [    9.111164] isapnp: Scanning for PnP cards...
Oct 31 18:48:57 cory-laptop kernel: [    9.463592] isapnp: No Plug & Play device found
Oct 31 18:48:57 cory-laptop kernel: [    9.541540] Real Time Clock Driver v1.12ac
Oct 31 18:48:57 cory-laptop kernel: [    9.541688] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 31 18:48:57 cory-laptop kernel: [    9.543388] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
Oct 31 18:48:57 cory-laptop kernel: [    9.543606] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Oct 31 18:48:57 cory-laptop kernel: [    9.543610] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:48:57 cory-laptop kernel: [    9.543620] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Oct 31 18:48:57 cory-laptop kernel: [    9.544507] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 31 18:48:57 cory-laptop kernel: [    9.544847] input: Macintosh mouse button emulation as /class/input/input0
Oct 31 18:48:57 cory-laptop kernel: [    9.544974] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 31 18:48:57 cory-laptop kernel: [    9.560587] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 31 18:48:57 cory-laptop kernel: [    9.560596] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 31 18:48:57 cory-laptop kernel: [    9.560933] mice: PS/2 mouse device common for all mice
Oct 31 18:48:57 cory-laptop kernel: [    9.561122] EISA: Probing bus 0 at eisa.0
Oct 31 18:48:57 cory-laptop kernel: [    9.561131] Cannot allocate resource for EISA slot 1
Oct 31 18:48:57 cory-laptop kernel: [    9.561149] EISA: Detected 0 cards.
Oct 31 18:48:57 cory-laptop kernel: [    9.561279] TCP cubic registered
Oct 31 18:48:57 cory-laptop kernel: [    9.561295] NET: Registered protocol family 1
Oct 31 18:48:57 cory-laptop kernel: [    9.561383] Using IPI No-Shortcut mode
Oct 31 18:48:57 cory-laptop kernel: [    9.561619]   Magic number: 11:583:859
Oct 31 18:48:57 cory-laptop kernel: [    9.561785]   hash matches device ptyse
Oct 31 18:48:57 cory-laptop kernel: [    9.562351] Freeing unused kernel memory: 364k freed
Oct 31 18:48:57 cory-laptop kernel: [    9.616982] input: AT Translated Set 2 keyboard as /class/input/input1
Oct 31 18:48:57 cory-laptop kernel: [   10.862568] AppArmor: AppArmor initialized<5>audit(1193874511.476:2):  type=1505 info="AppArmor initialized" pid=1183
Oct 31 18:48:57 cory-laptop kernel: [   10.874022] fuse init (API version 7.8)
Oct 31 18:48:57 cory-laptop kernel: [   10.882187] Failure registering capabilities with primary security module.
Oct 31 18:48:57 cory-laptop kernel: [   10.894089] ACPI: Transitioning device [FAN] to D3
Oct 31 18:48:57 cory-laptop kernel: [   10.894094] ACPI: Transitioning device [FAN] to D3
Oct 31 18:48:57 cory-laptop kernel: [   10.894100] ACPI: Fan [FAN] (off)
Oct 31 18:48:57 cory-laptop kernel: [   10.901188] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct 31 18:48:57 cory-laptop kernel: [   10.902592] ACPI: Thermal Zone [THRM] (51 C)
Oct 31 18:48:57 cory-laptop kernel: [   11.764897] usbcore: registered new interface driver usbfs
Oct 31 18:48:57 cory-laptop kernel: [   11.764932] usbcore: registered new interface driver hub
Oct 31 18:48:57 cory-laptop kernel: [   11.764966] usbcore: registered new device driver usb
Oct 31 18:48:57 cory-laptop kernel: [   11.766104] USB Universal Host Controller Interface driver v3.0
Oct 31 18:48:57 cory-laptop kernel: [   11.766484] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Oct 31 18:48:57 cory-laptop kernel: [   11.766493] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:48:57 cory-laptop kernel: [   11.766512] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 31 18:48:57 cory-laptop kernel: [   11.766716] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Oct 31 18:48:57 cory-laptop kernel: [   11.766750] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018c0
Oct 31 18:48:57 cory-laptop kernel: [   11.766913] usb usb1: configuration #1 chosen from 1 choice
Oct 31 18:48:57 cory-laptop kernel: [   11.766948] hub 1-0:1.0: USB hub found
Oct 31 18:48:57 cory-laptop kernel: [   11.766959] hub 1-0:1.0: 2 ports detected
Oct 31 18:48:57 cory-laptop kernel: [   11.843205] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
Oct 31 18:48:57 cory-laptop kernel: [   11.843210] e100: Copyright(c) 1999-2006 Intel Corporation
Oct 31 18:48:57 cory-laptop kernel: [   11.922254] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Oct 31 18:48:57 cory-laptop kernel: [   11.922513] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Oct 31 18:48:57 cory-laptop kernel: [   11.922517] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:48:57 cory-laptop kernel: [   11.922540] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 31 18:48:57 cory-laptop kernel: [   11.922597] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Oct 31 18:48:57 cory-laptop kernel: [   11.922644] ehci_hcd 0000:00:1d.7: debug port 1
Oct 31 18:48:57 cory-laptop kernel: [   11.922662] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x3c080000
Oct 31 18:48:57 cory-laptop kernel: [   11.926533] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 31 18:48:57 cory-laptop kernel: [   11.926654] usb usb2: configuration #1 chosen from 1 choice
Oct 31 18:48:57 cory-laptop kernel: [   11.926692] hub 2-0:1.0: USB hub found
Oct 31 18:48:57 cory-laptop kernel: [   11.926703] hub 2-0:1.0: 6 ports detected
Oct 31 18:48:57 cory-laptop kernel: [   11.944848] SCSI subsystem initialized
Oct 31 18:48:57 cory-laptop kernel: [   12.030800] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
Oct 31 18:48:57 cory-laptop kernel: [   12.030806] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:48:57 cory-laptop kernel: [   12.066065] e100: eth0: e100_probe: addr 0xcffff000, irq 11, MAC addr 00:08:0D:2F:C7:65
Oct 31 18:48:57 cory-laptop kernel: [   12.082130] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Oct 31 18:48:57 cory-laptop kernel: [   12.082135] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:48:57 cory-laptop kernel: [   12.082360] scsi0 : ata_piix
Oct 31 18:48:57 cory-laptop kernel: [   12.082439] scsi1 : ata_piix
Oct 31 18:48:57 cory-laptop kernel: [   12.082605] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Oct 31 18:48:57 cory-laptop kernel: [   12.082610] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Oct 31 18:48:57 cory-laptop kernel: [    4.308000] Marking TSC unstable due to: possible TSC halt in C2.
Oct 31 18:48:57 cory-laptop kernel: [    4.316000] Time: acpi_pm clocksource has been installed.
Oct 31 18:48:57 cory-laptop kernel: [    4.364000] ata1.00: ATA-6: IC25N040ATMR04-0, MO2OAD0A, max UDMA/100
Oct 31 18:48:57 cory-laptop kernel: [    4.364000] ata1.00: 78140160 sectors, multi 0: LBA48 
Oct 31 18:48:57 cory-laptop kernel: [    4.380000] ata1.00: configured for UDMA/100
Oct 31 18:48:57 cory-laptop kernel: [    4.700000] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R2412, 1330, max UDMA/33
Oct 31 18:48:57 cory-laptop kernel: [    4.732000] usb 1-2: new low speed USB device using uhci_hcd and address 2
Oct 31 18:48:57 cory-laptop kernel: [    4.872000] ata2.00: configured for UDMA/33
Oct 31 18:48:57 cory-laptop kernel: [    4.872000] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATMR04-0 MO2O PQ: 0 ANSI: 5
Oct 31 18:48:57 cory-laptop kernel: [    4.888000] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2412 1330 PQ: 0 ANSI: 5
Oct 31 18:48:57 cory-laptop kernel: [    4.912000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Oct 31 18:48:57 cory-laptop kernel: [    4.912000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 18:48:57 cory-laptop kernel: [    4.912000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 18:48:57 cory-laptop kernel: [    4.912000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Oct 31 18:48:57 cory-laptop kernel: [    4.912000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 18:48:57 cory-laptop kernel: [    4.912000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 18:48:57 cory-laptop kernel: [    4.912000]  sda:<6>usb 1-2: configuration #1 chosen from 1 choice
Oct 31 18:48:57 cory-laptop kernel: [    4.940000]  sda1 sda2 <<6>usbcore: registered new interface driver hiddev
Oct 31 18:48:57 cory-laptop kernel: [    4.968000]  sda5 >
Oct 31 18:48:57 cory-laptop kernel: [    4.968000] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 31 18:48:57 cory-laptop kernel: [    4.976000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 31 18:48:57 cory-laptop kernel: [    4.976000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Oct 31 18:48:57 cory-laptop kernel: [    4.996000] input: HID 1241:1166 as /class/input/input2
Oct 31 18:48:57 cory-laptop kernel: [    4.996000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:1d.0-2
Oct 31 18:48:57 cory-laptop kernel: [    4.996000] usbcore: registered new interface driver usbhid
Oct 31 18:48:57 cory-laptop kernel: [    4.996000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 31 18:48:57 cory-laptop kernel: [    5.068000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Oct 31 18:48:57 cory-laptop kernel: [    5.068000] Uniform CD-ROM driver Revision: 3.20
Oct 31 18:48:57 cory-laptop kernel: [    5.268000] Attempting manual resume
Oct 31 18:48:57 cory-laptop kernel: [    5.288000] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct 31 18:48:57 cory-laptop kernel: [    5.288000] EXT3-fs: write access will be enabled during recovery.
Oct 31 18:48:57 cory-laptop kernel: [    6.720000] kjournald starting.  Commit interval 5 seconds
Oct 31 18:48:57 cory-laptop kernel: [    6.720000] EXT3-fs: recovery complete.
Oct 31 18:48:57 cory-laptop kernel: [    6.720000] EXT3-fs: mounted filesystem with ordered data mode.
Oct 31 18:48:57 cory-laptop kernel: [   20.352000] Linux agpgart interface v0.102 (c) Dave Jones
Oct 31 18:48:57 cory-laptop kernel: [   20.364000] agpgart: Detected an Intel 855GM Chipset.
Oct 31 18:48:57 cory-laptop kernel: [   20.364000] agpgart: Detected 16252K stolen memory.
Oct 31 18:48:57 cory-laptop kernel: [   20.372000] agpgart: AGP aperture is 128M @ 0xd8000000
Oct 31 18:48:57 cory-laptop kernel: [   21.216000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 31 18:48:57 cory-laptop kernel: [   21.276000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 31 18:48:57 cory-laptop kernel: [   21.296000] iTCO_vendor_support: vendor-support=0
Oct 31 18:48:57 cory-laptop kernel: [   21.296000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Oct 31 18:48:57 cory-laptop kernel: [   21.296000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0xd860)
Oct 31 18:48:57 cory-laptop kernel: [   21.300000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Oct 31 18:48:57 cory-laptop kernel: [   21.380000] input: PC Speaker as /class/input/input3
Oct 31 18:48:57 cory-laptop kernel: [   21.640000] Yenta: CardBus bridge found at 0000:01:0b.0 [1179:0001]
Oct 31 18:48:57 cory-laptop kernel: [   21.768000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
Oct 31 18:48:57 cory-laptop kernel: [   21.768000] Socket status: 30000020
Oct 31 18:48:57 cory-laptop kernel: [   21.768000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
Oct 31 18:48:57 cory-laptop kernel: [   21.768000] cs: IO port probe 0xc000-0xcfff: clean.
Oct 31 18:48:57 cory-laptop kernel: [   21.768000] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xcfffffff
Oct 31 18:48:57 cory-laptop kernel: [   21.768000] pcmcia: parent PCI bridge Memory window: 0x38000000 - 0x3bffffff
Oct 31 18:48:57 cory-laptop kernel: [   22.068000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
Oct 31 18:48:57 cory-laptop kernel: [   22.068000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:48:57 cory-laptop kernel: [   22.080000] input: PS/2 Mouse as /class/input/input4
Oct 31 18:48:57 cory-laptop kernel: [   22.132000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input5
Oct 31 18:48:57 cory-laptop kernel: [   22.140000] pnp: Device 00:09 activated.
Oct 31 18:48:57 cory-laptop kernel: [   22.140000] parport_pc 00:09: reported by Plug and Play ACPI
Oct 31 18:48:57 cory-laptop kernel: [   22.140000] pnp: Device 00:09 disabled.
Oct 31 18:48:57 cory-laptop kernel: [   22.404000] pccard: CardBus card inserted into slot 0
Oct 31 18:48:57 cory-laptop kernel: [   22.460000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
Oct 31 18:48:57 cory-laptop kernel: [   22.460000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Oct 31 18:48:57 cory-laptop kernel: [   22.460000] cs: IO port probe 0x820-0x8ff: clean.
Oct 31 18:48:57 cory-laptop kernel: [   22.460000] cs: IO port probe 0xc00-0xcf7: clean.
Oct 31 18:48:57 cory-laptop kernel: [   22.464000] cs: IO port probe 0xa00-0xaff: clean.
Oct 31 18:48:57 cory-laptop kernel: [   22.492000] intel8x0_measure_ac97_clock: measured 54766 usecs
Oct 31 18:48:57 cory-laptop kernel: [   22.492000] intel8x0: clocking to 48000
Oct 31 18:48:57 cory-laptop kernel: [   22.608000] acx: Loaded combined PCI/USB driver, firmware_ver=default
Oct 31 18:48:57 cory-laptop kernel: [   22.608000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Oct 31 18:48:57 cory-laptop kernel: [   22.612000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Oct 31 18:48:57 cory-laptop kernel: [   22.612000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:48:57 cory-laptop kernel: [   22.612000] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x40020000, phymem2:0x40000000, mem1:0xefaa8000, mem1_size:8192, mem2:0xefb80000, mem2_size:131072
Oct 31 18:48:57 cory-laptop kernel: [   22.612000] acx: loading firmware for acx1111 chipset with radio ID 16
Oct 31 18:48:57 cory-laptop kernel: [   23.468000] NVS_vendor_offs:0221 probe_delay:200 eof_memory:1114112
Oct 31 18:48:57 cory-laptop kernel: [   23.468000] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
Oct 31 18:48:57 cory-laptop kernel: [   23.468000] AntennaID:00 Len:02 Data:01 02 
Oct 31 18:48:57 cory-laptop kernel: [   23.468000] PowerLevelID:01 Len:02 Data:001E 000A 
Oct 31 18:48:57 cory-laptop kernel: [   23.468000] DataRatesID:02 Len:05 Data:02 04 11 22 44 
Oct 31 18:48:57 cory-laptop kernel: [   23.468000] DomainID:03 Len:06 Data:10 20 30 31 32 40 
Oct 31 18:48:57 cory-laptop kernel: [   23.468000] ProductID:04 Len:09 Data:TI ACX100
Oct 31 18:48:57 cory-laptop kernel: [   23.468000] ManufacturerID:05 Len:07 Data:TI Test
Oct 31 18:48:57 cory-laptop kernel: [   23.528000] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
Oct 31 18:48:57 cory-laptop kernel: [   23.528000] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.22-14-generic
Oct 31 18:48:57 cory-laptop kernel: [   23.528000] usbcore: registered new interface driver acx_usb
Oct 31 18:48:57 cory-laptop kernel: [   24.216000] lp: driver loaded but no devices found
Oct 31 18:48:57 cory-laptop kernel: [   24.280000] Adding 698788k swap on /dev/sda5.  Priority:-1 extents:1 across:698788k
Oct 31 18:48:57 cory-laptop kernel: [   24.672000] EXT3 FS on sda1, internal journal
Oct 31 18:48:57 cory-laptop kernel: [   25.076000] NET: Registered protocol family 17
Oct 31 18:48:57 cory-laptop kernel: [   25.872000] ACPI: Battery Slot [BAT1] (battery present)
Oct 31 18:48:57 cory-laptop kernel: [   26.132000] No dock devices found.
Oct 31 18:48:57 cory-laptop kernel: [   26.164000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
Oct 31 18:48:57 cory-laptop kernel: [   26.164000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
Oct 31 18:48:57 cory-laptop kernel: [   26.168000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
Oct 31 18:48:57 cory-laptop kernel: [   26.168000] toshiba_acpi: ktoshkeyd will check 2 times per second
Oct 31 18:48:57 cory-laptop kernel: [   26.172000] toshiba_acpi: Dropped 0 keys from the queue on startup
Oct 31 18:48:57 cory-laptop kernel: [   26.196000] ACPI: AC Adapter [ADP1] (on-line)
Oct 31 18:48:57 cory-laptop kernel: [   26.256000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
Oct 31 18:48:57 cory-laptop kernel: [   26.328000] input: Power Button (FF) as /class/input/input6
Oct 31 18:48:57 cory-laptop kernel: [   26.332000] ACPI: Power Button (FF) [PWRF]
Oct 31 18:48:57 cory-laptop kernel: [   26.376000] input: Lid Switch as /class/input/input7
Oct 31 18:48:57 cory-laptop kernel: [   26.380000] ACPI: Lid Switch [LID]
Oct 31 18:48:57 cory-laptop kernel: [   26.424000] input: Power Button (CM) as /class/input/input8
Oct 31 18:48:57 cory-laptop kernel: [   26.428000] ACPI: Power Button (CM) [PWRB]
Oct 31 18:48:57 cory-laptop kernel: [   27.892000] NET: Registered protocol family 10
Oct 31 18:48:57 cory-laptop kernel: [   27.892000] lo: Disabled Privacy Extensions
Oct 31 18:48:58 cory-laptop kernel: [   28.080000] wlan0: duplicate address detected!
Oct 31 18:48:58 cory-laptop kernel: [   28.288000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:48:58 cory-laptop kernel: [   28.296000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Oct 31 18:48:58 cory-laptop kernel: [   28.296000] Intel ICH Modem: probe of 0000:00:1f.6 failed with error -13
Oct 31 18:48:58 cory-laptop kernel: [   28.568000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 31 18:49:10 cory-laptop kernel: [   40.476000] [drm] Initialized drm 1.1.0 20060810
Oct 31 18:49:10 cory-laptop kernel: [   40.504000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:49:10 cory-laptop kernel: [   40.508000] [drm] Initialized i915 1.6.0 20060119 on minor 0
Oct 31 18:49:10 cory-laptop kernel: [   40.508000] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
Oct 31 18:49:10 cory-laptop kernel: [   40.512000] [drm] Initialized i915 1.6.0 20060119 on minor 1
Oct 31 18:49:10 cory-laptop kernel: [   41.032000] ppdev: user-space parallel port driver
Oct 31 18:49:11 cory-laptop kernel: [   41.824000] audit(1193874551.264:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4912 profile="/usr/sbin/cupsd"
Oct 31 18:49:11 cory-laptop kernel: [   41.968000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
Oct 31 18:49:11 cory-laptop kernel: [   41.968000] apm: overridden by ACPI.
Oct 31 18:49:12 cory-laptop kernel: [   42.404000] Failure registering capabilities with primary security module.
Oct 31 18:49:12 cory-laptop dhcdbd: Started up.
Oct 31 18:49:12 cory-laptop kernel: [   42.640000] Bluetooth: Core ver 2.11
Oct 31 18:49:12 cory-laptop kernel: [   42.640000] NET: Registered protocol family 31
Oct 31 18:49:12 cory-laptop kernel: [   42.640000] Bluetooth: HCI device and connection manager initialized
Oct 31 18:49:12 cory-laptop kernel: [   42.640000] Bluetooth: HCI socket layer initialized
Oct 31 18:49:12 cory-laptop kernel: [   42.660000] Bluetooth: L2CAP ver 2.8
Oct 31 18:49:12 cory-laptop kernel: [   42.660000] Bluetooth: L2CAP socket layer initialized
Oct 31 18:49:12 cory-laptop kernel: [   42.684000] Bluetooth: RFCOMM socket layer initialized
Oct 31 18:49:12 cory-laptop kernel: [   42.684000] Bluetooth: RFCOMM TTY layer initialized
Oct 31 18:49:12 cory-laptop kernel: [   42.684000] Bluetooth: RFCOMM ver 1.8
Oct 31 18:50:18 cory-laptop kernel: [  108.236000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:18 cory-laptop kernel: [  108.236000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:18 cory-laptop kernel: [  108.984000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:19 cory-laptop kernel: [  109.736000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:22 cory-laptop kernel: [  112.488000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:22 cory-laptop kernel: [  112.488000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:23 cory-laptop kernel: [  113.236000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:23 cory-laptop kernel: [  113.988000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:26 cory-laptop kernel: [  116.740000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:26 cory-laptop kernel: [  116.740000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:27 cory-laptop kernel: [  117.488000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:28 cory-laptop kernel: [  118.240000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:30 cory-laptop kernel: [  120.992000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:31 cory-laptop kernel: [  121.740000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:50:32 cory-laptop kernel: [  122.492000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:51:27 cory-laptop syslogd 1.4.1#21ubuntu3: restart.
Oct 31 18:51:28 cory-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Oct 31 18:51:28 cory-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Oct 31 18:51:28 cory-laptop kernel: Symbols match kernel version 2.6.22.
Oct 31 18:51:28 cory-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002ef40000 (usable)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000002ef40000 - 000000002ef50000 (ACPI data)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]  BIOS-e820: 000000002ef50000 - 000000002f000000 (reserved)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] 751MB LOWMEM available.
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] Zone PFN ranges:
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]   DMA             0 ->     4096
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]   Normal       4096 ->   192320
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]   HighMem    192320 ->   192320
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 31 18:51:28 cory-laptop kernel: [    0.000000]     0:        0 ->   192320
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] DMI 2.3 present.
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F0180 checksum 0
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] ACPI: RSDP 000F0180, 0014 (r0 TOSHIB)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] ACPI: RSDT 2EF40000, 0030 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] ACPI: FACP 2EF40058, 0084 (r2 TOSHIB 750        970814 TASM  4010000)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] ACPI: DSDT 2EF40110, 4B25 (r1 TOSHIB AFCF7    20030326 MSFT  100000E)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] ACPI: FACS 000EEE00, 0040
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] ACPI: DBGP 2EF400DC, 0034 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] ACPI: BOOT 2EF40030, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xd808
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f000000:cfc10000)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 190818
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] Kernel command line: root=UUID=e6f50239-1aea-4ce9-bff6-f65118a4cdb9 ro quiet splash
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] Initializing CPU#0
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 31 18:51:28 cory-laptop kernel: [    0.000000] Detected 2394.061 MHz processor.
Oct 31 18:51:28 cory-laptop kernel: [    7.155742] Console: colour VGA+ 80x25
Oct 31 18:51:28 cory-laptop kernel: [    7.156434] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 31 18:51:28 cory-laptop kernel: [    7.157488] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 31 18:51:28 cory-laptop kernel: [    7.176538] Memory: 750860k/769280k available (2015k kernel code, 17808k reserved, 916k data, 364k init, 0k highmem)
Oct 31 18:51:28 cory-laptop kernel: [    7.176550] virtual kernel memory layout:
Oct 31 18:51:28 cory-laptop kernel: [    7.176551]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Oct 31 18:51:28 cory-laptop kernel: [    7.176553]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 31 18:51:28 cory-laptop kernel: [    7.176554]     vmalloc : 0xef800000 - 0xff7fe000   ( 255 MB)
Oct 31 18:51:28 cory-laptop kernel: [    7.176555]     lowmem  : 0xc0000000 - 0xeef40000   ( 751 MB)
Oct 31 18:51:28 cory-laptop kernel: [    7.176556]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Oct 31 18:51:28 cory-laptop kernel: [    7.176557]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Oct 31 18:51:28 cory-laptop kernel: [    7.176559]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Oct 31 18:51:28 cory-laptop kernel: [    7.176562] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 31 18:51:28 cory-laptop kernel: [    7.176606] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 31 18:51:28 cory-laptop kernel: [    7.256497] Calibrating delay using timer specific routine.. 4792.22 BogoMIPS (lpj=9584456)
Oct 31 18:51:28 cory-laptop kernel: [    7.256527] Security Framework v1.0.0 initialized
Oct 31 18:51:28 cory-laptop kernel: [    7.256537] SELinux:  Disabled at boot.
Oct 31 18:51:28 cory-laptop kernel: [    7.256552] Mount-cache hash table entries: 512
Oct 31 18:51:28 cory-laptop kernel: [    7.256736] CPU: Trace cache: 12K uops, L1 D cache: 8K
Oct 31 18:51:28 cory-laptop kernel: [    7.256739] CPU: L2 cache: 256K
Oct 31 18:51:28 cory-laptop kernel: [    7.256742] CPU: Hyper-Threading is disabled
Oct 31 18:51:28 cory-laptop kernel: [    7.256760] Compat vDSO mapped to ffffe000.
Oct 31 18:51:28 cory-laptop kernel: [    7.256776] Checking 'hlt' instruction... OK.
Oct 31 18:51:28 cory-laptop kernel: [    7.272602] SMP alternatives: switching to UP code
Oct 31 18:51:28 cory-laptop kernel: [    7.272921] Freeing SMP alternatives: 11k freed
Oct 31 18:51:28 cory-laptop kernel: [    7.273286] Early unpacking initramfs... done
Oct 31 18:51:28 cory-laptop kernel: [    7.614518] ACPI: Core revision 20070126
Oct 31 18:51:28 cory-laptop kernel: [    7.614597] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 31 18:51:28 cory-laptop kernel: [    7.616418] ACPI: setting ELCR to 0200 (from 0e00)
Oct 31 18:51:28 cory-laptop kernel: [    7.616575] CPU0: Intel Mobile Intel(R) Celeron(R) CPU 2.40GHz stepping 09
Oct 31 18:51:28 cory-laptop kernel: [    7.616583] SMP motherboard not detected.
Oct 31 18:51:28 cory-laptop kernel: [    7.616586] Local APIC not detected. Using dummy APIC emulation.
Oct 31 18:51:28 cory-laptop kernel: [    7.616634] Brought up 1 CPUs
Oct 31 18:51:28 cory-laptop kernel: [    7.616802] Booting paravirtualized kernel on bare hardware
Oct 31 18:51:28 cory-laptop kernel: [    7.616874] Time: 23:51:01  Date: 09/31/107
Oct 31 18:51:28 cory-laptop kernel: [    7.616911] NET: Registered protocol family 16
Oct 31 18:51:28 cory-laptop kernel: [    7.617057] EISA bus registered
Oct 31 18:51:28 cory-laptop kernel: [    7.617075] ACPI: bus type pci registered
Oct 31 18:51:28 cory-laptop kernel: [    7.617189] PCI: PCI BIOS revision 2.10 entry at 0xfd317, last bus=3
Oct 31 18:51:28 cory-laptop kernel: [    7.617191] PCI: Using configuration type 1
Oct 31 18:51:28 cory-laptop kernel: [    7.617193] Setting up standard PCI resources
Oct 31 18:51:28 cory-laptop kernel: [    7.622710] ACPI: Interpreter enabled
Oct 31 18:51:28 cory-laptop kernel: [    7.622716] ACPI: (supports S0 S3 S4 S5)
Oct 31 18:51:28 cory-laptop kernel: [    7.622740] ACPI: Using PIC for interrupt routing
Oct 31 18:51:28 cory-laptop kernel: [    7.631175] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 31 18:51:28 cory-laptop kernel: [    7.631697] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
Oct 31 18:51:28 cory-laptop kernel: [    7.631702] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
Oct 31 18:51:28 cory-laptop kernel: [    7.632020] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
Oct 31 18:51:28 cory-laptop kernel: [    7.632122] PCI: Transparent bridge - 0000:00:1e.0
Oct 31 18:51:28 cory-laptop kernel: [    7.634170] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
Oct 31 18:51:28 cory-laptop kernel: [    7.634298] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
Oct 31 18:51:28 cory-laptop kernel: [    7.634422] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
Oct 31 18:51:28 cory-laptop kernel: [    7.634547] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
Oct 31 18:51:28 cory-laptop kernel: [    7.634676] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
Oct 31 18:51:28 cory-laptop kernel: [    7.634804] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
Oct 31 18:51:28 cory-laptop kernel: [    7.634932] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
Oct 31 18:51:28 cory-laptop kernel: [    7.635059] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
Oct 31 18:51:28 cory-laptop kernel: [    7.635398] ACPI: Power Resource [PFAN] (off)
Oct 31 18:51:28 cory-laptop kernel: [    7.635417] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 31 18:51:28 cory-laptop kernel: [    7.635443] pnp: PnP ACPI init
Oct 31 18:51:28 cory-laptop kernel: [    7.635459] ACPI: bus type pnp registered
Oct 31 18:51:28 cory-laptop kernel: [    7.638965] pnp: PnP ACPI: found 10 devices
Oct 31 18:51:28 cory-laptop kernel: [    7.638970] ACPI: ACPI bus type pnp unregistered
Oct 31 18:51:28 cory-laptop kernel: [    7.638976] PnPBIOS: Disabled by ACPI PNP
Oct 31 18:51:28 cory-laptop kernel: [    7.639061] PCI: Using ACPI for IRQ routing
Oct 31 18:51:28 cory-laptop kernel: [    7.639066] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 31 18:51:28 cory-laptop kernel: [    7.643583] NET: Registered protocol family 8
Oct 31 18:51:28 cory-laptop kernel: [    7.643586] NET: Registered protocol family 20
Oct 31 18:51:28 cory-laptop kernel: [    7.643721] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
Oct 31 18:51:28 cory-laptop kernel: [    7.643726] pnp: 00:00: iomem range 0xe0000-0xeffff could not be reserved
Oct 31 18:51:28 cory-laptop kernel: [    7.643729] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
Oct 31 18:51:28 cory-laptop kernel: [    7.643732] pnp: 00:00: iomem range 0x100000-0x2ef3ffff could not be reserved
Oct 31 18:51:28 cory-laptop kernel: [    7.643854] Time: tsc clocksource has been installed.
Oct 31 18:51:28 cory-laptop kernel: [    7.674383] PCI: Bus 2, cardbus bridge: 0000:01:0b.0
Oct 31 18:51:28 cory-laptop kernel: [    7.674387]   IO window: 0000c000-0000c0ff
Oct 31 18:51:28 cory-laptop kernel: [    7.674392]   IO window: 0000c400-0000c4ff
Oct 31 18:51:28 cory-laptop kernel: [    7.674397]   PREFETCH window: 38000000-3bffffff
Oct 31 18:51:28 cory-laptop kernel: [    7.674402]   MEM window: 40000000-43ffffff
Oct 31 18:51:28 cory-laptop kernel: [    7.674407] PCI: Bridge: 0000:00:1e.0
Oct 31 18:51:28 cory-laptop kernel: [    7.674410]   IO window: c000-cfff
Oct 31 18:51:28 cory-laptop kernel: [    7.674416]   MEM window: cff00000-cfffffff
Oct 31 18:51:28 cory-laptop kernel: [    7.674420]   PREFETCH window: 38000000-3bffffff
Oct 31 18:51:28 cory-laptop kernel: [    7.674453] PCI: Enabling device 0000:01:0b.0 (0000 -> 0003)
Oct 31 18:51:28 cory-laptop kernel: [    7.674712] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Oct 31 18:51:28 cory-laptop kernel: [    7.674720] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:51:28 cory-laptop kernel: [    7.674748] NET: Registered protocol family 2
Oct 31 18:51:28 cory-laptop kernel: [    7.711801] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 31 18:51:28 cory-laptop kernel: [    7.712000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Oct 31 18:51:28 cory-laptop kernel: [    7.714074] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 31 18:51:28 cory-laptop kernel: [    7.714806] TCP: Hash tables configured (established 131072 bind 65536)
Oct 31 18:51:28 cory-laptop kernel: [    7.714815] TCP reno registered
Oct 31 18:51:28 cory-laptop kernel: [    7.723923] checking if image is initramfs... it is
Oct 31 18:51:28 cory-laptop kernel: [    8.175003] Switched to high resolution mode on CPU 0
Oct 31 18:51:28 cory-laptop kernel: [    8.390733] Freeing initrd memory: 7115k freed
Oct 31 18:51:28 cory-laptop kernel: [    8.390920] Simple Boot Flag at 0x7c set to 0x1
Oct 31 18:51:28 cory-laptop kernel: [    8.391208] audit: initializing netlink socket (disabled)
Oct 31 18:51:28 cory-laptop kernel: [    8.391227] audit(1193874660.972:1): initialized
Oct 31 18:51:28 cory-laptop kernel: [    8.394365] VFS: Disk quotas dquot_6.5.1
Oct 31 18:51:28 cory-laptop kernel: [    8.394451] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 31 18:51:28 cory-laptop kernel: [    8.394655] io scheduler noop registered
Oct 31 18:51:28 cory-laptop kernel: [    8.394659] io scheduler anticipatory registered
Oct 31 18:51:28 cory-laptop kernel: [    8.394661] io scheduler deadline registered
Oct 31 18:51:28 cory-laptop kernel: [    8.394695] io scheduler cfq registered (default)
Oct 31 18:51:28 cory-laptop kernel: [    8.394985] isapnp: Scanning for PnP cards...
Oct 31 18:51:28 cory-laptop kernel: [    8.747417] isapnp: No Plug & Play device found
Oct 31 18:51:28 cory-laptop kernel: [    8.826982] Real Time Clock Driver v1.12ac
Oct 31 18:51:28 cory-laptop kernel: [    8.827131] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 31 18:51:28 cory-laptop kernel: [    8.828691] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
Oct 31 18:51:28 cory-laptop kernel: [    8.828908] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Oct 31 18:51:28 cory-laptop kernel: [    8.828912] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:51:28 cory-laptop kernel: [    8.828921] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Oct 31 18:51:28 cory-laptop kernel: [    8.829939] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 31 18:51:28 cory-laptop kernel: [    8.830274] input: Macintosh mouse button emulation as /class/input/input0
Oct 31 18:51:28 cory-laptop kernel: [    8.830403] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 31 18:51:28 cory-laptop kernel: [    8.846070] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 31 18:51:28 cory-laptop kernel: [    8.846080] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 31 18:51:28 cory-laptop kernel: [    8.846421] mice: PS/2 mouse device common for all mice
Oct 31 18:51:28 cory-laptop kernel: [    8.846613] EISA: Probing bus 0 at eisa.0
Oct 31 18:51:28 cory-laptop kernel: [    8.846622] Cannot allocate resource for EISA slot 1
Oct 31 18:51:28 cory-laptop kernel: [    8.846640] EISA: Detected 0 cards.
Oct 31 18:51:28 cory-laptop kernel: [    8.846770] TCP cubic registered
Oct 31 18:51:28 cory-laptop kernel: [    8.846845] NET: Registered protocol family 1
Oct 31 18:51:28 cory-laptop kernel: [    8.846875] Using IPI No-Shortcut mode
Oct 31 18:51:28 cory-laptop kernel: [    8.847108]   Magic number: 11:136:910
Oct 31 18:51:28 cory-laptop kernel: [    8.847241]   hash matches device ptyz6
Oct 31 18:51:28 cory-laptop kernel: [    8.847803] Freeing unused kernel memory: 364k freed
Oct 31 18:51:28 cory-laptop kernel: [    8.903540] input: AT Translated Set 2 keyboard as /class/input/input1
Oct 31 18:51:28 cory-laptop kernel: [   10.148776] AppArmor: AppArmor initialized<5>audit(1193874662.972:2):  type=1505 info="AppArmor initialized" pid=1183
Oct 31 18:51:28 cory-laptop kernel: [   10.160019] fuse init (API version 7.8)
Oct 31 18:51:28 cory-laptop kernel: [   10.168221] Failure registering capabilities with primary security module.
Oct 31 18:51:28 cory-laptop kernel: [   10.181547] ACPI: Transitioning device [FAN] to D3
Oct 31 18:51:28 cory-laptop kernel: [   10.181552] ACPI: Transitioning device [FAN] to D3
Oct 31 18:51:28 cory-laptop kernel: [   10.181558] ACPI: Fan [FAN] (off)
Oct 31 18:51:28 cory-laptop kernel: [   10.188554] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct 31 18:51:28 cory-laptop kernel: [   10.189923] ACPI: Thermal Zone [THRM] (56 C)
Oct 31 18:51:28 cory-laptop kernel: [   11.071884] usbcore: registered new interface driver usbfs
Oct 31 18:51:28 cory-laptop kernel: [   11.071916] usbcore: registered new interface driver hub
Oct 31 18:51:28 cory-laptop kernel: [   11.071950] usbcore: registered new device driver usb
Oct 31 18:51:28 cory-laptop kernel: [   11.073165] USB Universal Host Controller Interface driver v3.0
Oct 31 18:51:28 cory-laptop kernel: [   11.073516] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Oct 31 18:51:28 cory-laptop kernel: [   11.073525] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:51:28 cory-laptop kernel: [   11.073543] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 31 18:51:28 cory-laptop kernel: [   11.073777] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Oct 31 18:51:28 cory-laptop kernel: [   11.073809] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018c0
Oct 31 18:51:28 cory-laptop kernel: [   11.074026] usb usb1: configuration #1 chosen from 1 choice
Oct 31 18:51:28 cory-laptop kernel: [   11.074061] hub 1-0:1.0: USB hub found
Oct 31 18:51:28 cory-laptop kernel: [   11.074071] hub 1-0:1.0: 2 ports detected
Oct 31 18:51:28 cory-laptop kernel: [   11.138653] SCSI subsystem initialized
Oct 31 18:51:28 cory-laptop kernel: [   11.177340] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
Oct 31 18:51:28 cory-laptop kernel: [   11.177344] e100: Copyright(c) 1999-2006 Intel Corporation
Oct 31 18:51:28 cory-laptop kernel: [   11.213904] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Oct 31 18:51:28 cory-laptop kernel: [   11.214166] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Oct 31 18:51:28 cory-laptop kernel: [   11.214171] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:51:28 cory-laptop kernel: [   11.214194] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 31 18:51:28 cory-laptop kernel: [   11.214251] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Oct 31 18:51:28 cory-laptop kernel: [   11.214296] ehci_hcd 0000:00:1d.7: debug port 1
Oct 31 18:51:28 cory-laptop kernel: [   11.214315] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x3c080000
Oct 31 18:51:28 cory-laptop kernel: [   11.218209] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 31 18:51:28 cory-laptop kernel: [   11.218332] usb usb2: configuration #1 chosen from 1 choice
Oct 31 18:51:28 cory-laptop kernel: [   11.218367] hub 2-0:1.0: USB hub found
Oct 31 18:51:28 cory-laptop kernel: [   11.218379] hub 2-0:1.0: 6 ports detected
Oct 31 18:51:28 cory-laptop kernel: [   11.324632] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Oct 31 18:51:28 cory-laptop kernel: [   11.324636] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:51:28 cory-laptop kernel: [   11.324816] scsi0 : ata_piix
Oct 31 18:51:28 cory-laptop kernel: [   11.324889] scsi1 : ata_piix
Oct 31 18:51:28 cory-laptop kernel: [   11.325048] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Oct 31 18:51:28 cory-laptop kernel: [   11.325053] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Oct 31 18:51:28 cory-laptop kernel: [    4.300000] Marking TSC unstable due to: possible TSC halt in C2.
Oct 31 18:51:28 cory-laptop kernel: [    4.312000] Time: acpi_pm clocksource has been installed.
Oct 31 18:51:28 cory-laptop kernel: [    4.320000] ata1.00: ATA-6: IC25N040ATMR04-0, MO2OAD0A, max UDMA/100
Oct 31 18:51:28 cory-laptop kernel: [    4.320000] ata1.00: 78140160 sectors, multi 0: LBA48 
Oct 31 18:51:28 cory-laptop kernel: [    4.336000] ata1.00: configured for UDMA/100
Oct 31 18:51:28 cory-laptop kernel: [    4.656000] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R2412, 1330, max UDMA/33
Oct 31 18:51:28 cory-laptop kernel: [    4.756000] usb 1-2: new low speed USB device using uhci_hcd and address 2
Oct 31 18:51:28 cory-laptop kernel: [    4.848000] ata2.00: configured for UDMA/33
Oct 31 18:51:28 cory-laptop kernel: [    4.848000] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATMR04-0 MO2O PQ: 0 ANSI: 5
Oct 31 18:51:28 cory-laptop kernel: [    4.864000] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2412 1330 PQ: 0 ANSI: 5
Oct 31 18:51:28 cory-laptop kernel: [    4.864000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
Oct 31 18:51:28 cory-laptop kernel: [    4.864000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:51:28 cory-laptop kernel: [    4.888000] e100: eth0: e100_probe: addr 0xcffff000, irq 11, MAC addr 00:08:0D:2F:C7:65
Oct 31 18:51:28 cory-laptop kernel: [    4.912000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Oct 31 18:51:28 cory-laptop kernel: [    4.912000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 18:51:28 cory-laptop kernel: [    4.912000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 18:51:28 cory-laptop kernel: [    4.912000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Oct 31 18:51:28 cory-laptop kernel: [    4.912000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 18:51:28 cory-laptop kernel: [    4.912000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 18:51:28 cory-laptop kernel: [    4.912000]  sda: sda1 sda2 <<6>usb 1-2: configuration #1 chosen from 1 choice
Oct 31 18:51:28 cory-laptop kernel: [    4.972000]  sda5 >
Oct 31 18:51:28 cory-laptop kernel: [    4.972000] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 31 18:51:28 cory-laptop kernel: [    4.976000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 31 18:51:28 cory-laptop kernel: [    4.976000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Oct 31 18:51:28 cory-laptop kernel: [    5.000000] usbcore: registered new interface driver hiddev
Oct 31 18:51:28 cory-laptop kernel: [    5.044000] input: HID 1241:1166 as /class/input/input2
Oct 31 18:51:28 cory-laptop kernel: [    5.044000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:1d.0-2
Oct 31 18:51:28 cory-laptop kernel: [    5.044000] usbcore: registered new interface driver usbhid
Oct 31 18:51:28 cory-laptop kernel: [    5.044000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 31 18:51:28 cory-laptop kernel: [    5.052000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Oct 31 18:51:28 cory-laptop kernel: [    5.052000] Uniform CD-ROM driver Revision: 3.20
Oct 31 18:51:28 cory-laptop kernel: [    5.292000] Attempting manual resume
Oct 31 18:51:28 cory-laptop kernel: [    5.312000] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct 31 18:51:28 cory-laptop kernel: [    5.312000] EXT3-fs: write access will be enabled during recovery.
Oct 31 18:51:28 cory-laptop kernel: [    7.136000] kjournald starting.  Commit interval 5 seconds
Oct 31 18:51:28 cory-laptop kernel: [    7.136000] EXT3-fs: recovery complete.
Oct 31 18:51:28 cory-laptop kernel: [    7.136000] EXT3-fs: mounted filesystem with ordered data mode.
Oct 31 18:51:28 cory-laptop kernel: [   20.488000] Linux agpgart interface v0.102 (c) Dave Jones
Oct 31 18:51:28 cory-laptop kernel: [   20.544000] agpgart: Detected an Intel 855GM Chipset.
Oct 31 18:51:28 cory-laptop kernel: [   20.544000] agpgart: Detected 16252K stolen memory.
Oct 31 18:51:28 cory-laptop kernel: [   20.556000] agpgart: AGP aperture is 128M @ 0xd8000000
Oct 31 18:51:28 cory-laptop kernel: [   21.144000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 31 18:51:28 cory-laptop kernel: [   21.148000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 31 18:51:28 cory-laptop kernel: [   21.364000] input: PC Speaker as /class/input/input3
Oct 31 18:51:28 cory-laptop kernel: [   21.536000] iTCO_vendor_support: vendor-support=0
Oct 31 18:51:28 cory-laptop kernel: [   21.608000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Oct 31 18:51:28 cory-laptop kernel: [   21.608000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0xd860)
Oct 31 18:51:28 cory-laptop kernel: [   21.608000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Oct 31 18:51:28 cory-laptop kernel: [   21.692000] Yenta: CardBus bridge found at 0000:01:0b.0 [1179:0001]
Oct 31 18:51:28 cory-laptop kernel: [   21.820000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
Oct 31 18:51:28 cory-laptop kernel: [   21.820000] Socket status: 30000020
Oct 31 18:51:28 cory-laptop kernel: [   21.820000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
Oct 31 18:51:28 cory-laptop kernel: [   21.820000] cs: IO port probe 0xc000-0xcfff: clean.
Oct 31 18:51:28 cory-laptop kernel: [   21.820000] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xcfffffff
Oct 31 18:51:28 cory-laptop kernel: [   21.820000] pcmcia: parent PCI bridge Memory window: 0x38000000 - 0x3bffffff
Oct 31 18:51:28 cory-laptop kernel: [   22.184000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
Oct 31 18:51:28 cory-laptop kernel: [   22.184000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:51:28 cory-laptop kernel: [   22.392000] input: PS/2 Mouse as /class/input/input4
Oct 31 18:51:28 cory-laptop kernel: [   22.436000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input5
Oct 31 18:51:28 cory-laptop kernel: [   22.448000] pnp: Device 00:09 activated.
Oct 31 18:51:28 cory-laptop kernel: [   22.448000] parport_pc 00:09: reported by Plug and Play ACPI
Oct 31 18:51:28 cory-laptop kernel: [   22.448000] pnp: Device 00:09 disabled.
Oct 31 18:51:28 cory-laptop kernel: [   22.456000] pccard: CardBus card inserted into slot 0
Oct 31 18:51:28 cory-laptop kernel: [   22.604000] intel8x0_measure_ac97_clock: measured 54041 usecs
Oct 31 18:51:28 cory-laptop kernel: [   22.604000] intel8x0: clocking to 48000
Oct 31 18:51:28 cory-laptop kernel: [   22.688000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
Oct 31 18:51:28 cory-laptop kernel: [   22.688000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Oct 31 18:51:28 cory-laptop kernel: [   22.688000] cs: IO port probe 0x820-0x8ff: clean.
Oct 31 18:51:28 cory-laptop kernel: [   22.688000] cs: IO port probe 0xc00-0xcf7: clean.
Oct 31 18:51:28 cory-laptop kernel: [   22.688000] cs: IO port probe 0xa00-0xaff: clean.
Oct 31 18:51:28 cory-laptop kernel: [   22.724000] acx: Loaded combined PCI/USB driver, firmware_ver=default
Oct 31 18:51:28 cory-laptop kernel: [   22.724000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Oct 31 18:51:28 cory-laptop kernel: [   22.724000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Oct 31 18:51:28 cory-laptop kernel: [   22.724000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:51:28 cory-laptop kernel: [   22.724000] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x40020000, phymem2:0x40000000, mem1:0xef95c000, mem1_size:8192, mem2:0xefb80000, mem2_size:131072
Oct 31 18:51:28 cory-laptop kernel: [   22.724000] acx: loading firmware for acx1111 chipset with radio ID 16
Oct 31 18:51:28 cory-laptop kernel: [   23.640000] NVS_vendor_offs:0221 probe_delay:200 eof_memory:1114112
Oct 31 18:51:28 cory-laptop kernel: [   23.640000] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
Oct 31 18:51:28 cory-laptop kernel: [   23.640000] AntennaID:00 Len:02 Data:01 02 
Oct 31 18:51:28 cory-laptop kernel: [   23.640000] PowerLevelID:01 Len:02 Data:001E 000A 
Oct 31 18:51:28 cory-laptop kernel: [   23.640000] DataRatesID:02 Len:05 Data:02 04 11 22 44 
Oct 31 18:51:28 cory-laptop kernel: [   23.640000] DomainID:03 Len:06 Data:10 20 30 31 32 40 
Oct 31 18:51:28 cory-laptop kernel: [   23.640000] ProductID:04 Len:09 Data:TI ACX100
Oct 31 18:51:28 cory-laptop kernel: [   23.640000] ManufacturerID:05 Len:07 Data:TI Test
Oct 31 18:51:28 cory-laptop kernel: [   23.700000] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
Oct 31 18:51:28 cory-laptop kernel: [   23.700000] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.22-14-generic
Oct 31 18:51:28 cory-laptop kernel: [   23.700000] usbcore: registered new interface driver acx_usb
Oct 31 18:51:28 cory-laptop kernel: [   24.344000] lp: driver loaded but no devices found
Oct 31 18:51:28 cory-laptop kernel: [   24.404000] Adding 698788k swap on /dev/sda5.  Priority:-1 extents:1 across:698788k
Oct 31 18:51:28 cory-laptop kernel: [   24.796000] EXT3 FS on sda1, internal journal
Oct 31 18:51:28 cory-laptop kernel: [   25.416000] NET: Registered protocol family 17
Oct 31 18:51:28 cory-laptop kernel: [   26.168000] ACPI: Battery Slot [BAT1] (battery present)
Oct 31 18:51:28 cory-laptop kernel: [   26.428000] No dock devices found.
Oct 31 18:51:28 cory-laptop kernel: [   26.460000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
Oct 31 18:51:28 cory-laptop kernel: [   26.460000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
Oct 31 18:51:28 cory-laptop kernel: [   26.464000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
Oct 31 18:51:28 cory-laptop kernel: [   26.464000] toshiba_acpi: ktoshkeyd will check 2 times per second
Oct 31 18:51:28 cory-laptop kernel: [   26.468000] toshiba_acpi: Dropped 0 keys from the queue on startup
Oct 31 18:51:28 cory-laptop kernel: [   26.484000] ACPI: AC Adapter [ADP1] (on-line)
Oct 31 18:51:28 cory-laptop kernel: [   26.544000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
Oct 31 18:51:28 cory-laptop kernel: [   26.612000] input: Power Button (FF) as /class/input/input6
Oct 31 18:51:28 cory-laptop kernel: [   26.620000] ACPI: Power Button (FF) [PWRF]
Oct 31 18:51:28 cory-laptop kernel: [   26.660000] input: Lid Switch as /class/input/input7
Oct 31 18:51:28 cory-laptop kernel: [   26.668000] ACPI: Lid Switch [LID]
Oct 31 18:51:28 cory-laptop kernel: [   26.708000] input: Power Button (CM) as /class/input/input8
Oct 31 18:51:28 cory-laptop kernel: [   26.716000] ACPI: Power Button (CM) [PWRB]
Oct 31 18:51:29 cory-laptop kernel: [   28.380000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 31 18:51:29 cory-laptop kernel: [   28.676000] NET: Registered protocol family 10
Oct 31 18:51:29 cory-laptop kernel: [   28.676000] lo: Disabled Privacy Extensions
Oct 31 18:51:29 cory-laptop kernel: [   28.676000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 31 18:51:29 cory-laptop kernel: [   28.884000] AC'97 1 does not respond - RESET
Oct 31 18:51:29 cory-laptop kernel: [   28.884000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Oct 31 18:51:29 cory-laptop kernel: [   28.884000] Intel ICH Modem: probe of 0000:00:1f.6 failed with error -5
Oct 31 18:51:31 cory-laptop kernel: [   31.016000] ICMPv6 NA: someone advertises our address on wlan0!
Oct 31 18:51:42 cory-laptop kernel: [   41.780000] [drm] Initialized drm 1.1.0 20060810
Oct 31 18:51:42 cory-laptop kernel: [   41.788000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 31 18:51:42 cory-laptop kernel: [   41.792000] [drm] Initialized i915 1.6.0 20060119 on minor 0
Oct 31 18:51:42 cory-laptop kernel: [   41.792000] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
Oct 31 18:51:42 cory-laptop kernel: [   41.792000] [drm] Initialized i915 1.6.0 20060119 on minor 1
Oct 31 18:51:43 cory-laptop kernel: [   42.296000] ppdev: user-space parallel port driver
Oct 31 18:51:43 cory-laptop kernel: [   43.004000] audit(1193874703.633:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4934 profile="/usr/sbin/cupsd"
Oct 31 18:51:43 cory-laptop kernel: [   43.100000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
Oct 31 18:51:43 cory-laptop kernel: [   43.100000] apm: overridden by ACPI.
Oct 31 18:51:44 cory-laptop kernel: [   43.556000] Failure registering capabilities with primary security module.
Oct 31 18:51:44 cory-laptop dhcdbd: Started up.
Oct 31 18:51:44 cory-laptop kernel: [   43.804000] Bluetooth: Core ver 2.11
Oct 31 18:51:44 cory-laptop kernel: [   43.804000] NET: Registered protocol family 31
Oct 31 18:51:44 cory-laptop kernel: [   43.804000] Bluetooth: HCI device and connection manager initialized
Oct 31 18:51:44 cory-laptop kernel: [   43.804000] Bluetooth: HCI socket layer initialized
Oct 31 18:51:44 cory-laptop kernel: [   43.820000] Bluetooth: L2CAP ver 2.8
Oct 31 18:51:44 cory-laptop kernel: [   43.820000] Bluetooth: L2CAP socket layer initialized
Oct 31 18:51:44 cory-laptop kernel: [   43.860000] Bluetooth: RFCOMM socket layer initialized
Oct 31 18:51:44 cory-laptop kernel: [   43.860000] Bluetooth: RFCOMM TTY layer initialized
Oct 31 18:51:44 cory-laptop kernel: [   43.860000] Bluetooth: RFCOMM ver 1.8
Oct 31 18:53:38 cory-laptop kernel: [  158.112000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:54:26 cory-laptop kernel: [  206.012000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:54:41 cory-laptop kernel: [  220.964000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:54:44 cory-laptop kernel: [  223.960000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:54:51 cory-laptop kernel: [  231.028000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:54:52 cory-laptop kernel: [  231.776000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:54:53 cory-laptop kernel: [  232.524000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 18:58:52 cory-laptop syslogd 1.4.1#21ubuntu3: restart.
Oct 31 19:01:38 cory-laptop kernel: [  637.912000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:01:38 cory-laptop kernel: [  637.916000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:01:38 cory-laptop kernel: [  637.916000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:01:38 cory-laptop kernel: [  637.920000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:01:38 cory-laptop kernel: [  637.924000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:01:38 cory-laptop kernel: [  637.928000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:01:38 cory-laptop kernel: [  637.932000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:01:38 cory-laptop kernel: [  637.936000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:01:38 cory-laptop kernel: [  637.944000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:33 cory-laptop kernel: [  692.640000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:33 cory-laptop kernel: [  692.640000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:34 cory-laptop kernel: [  693.388000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:34 cory-laptop kernel: [  694.136000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:37 cory-laptop kernel: [  696.888000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:37 cory-laptop kernel: [  696.888000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:38 cory-laptop kernel: [  697.636000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:39 cory-laptop kernel: [  698.388000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:41 cory-laptop kernel: [  701.140000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:41 cory-laptop kernel: [  701.140000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:42 cory-laptop kernel: [  701.888000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:43 cory-laptop kernel: [  702.636000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:46 cory-laptop kernel: [  705.388000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:46 cory-laptop kernel: [  706.136000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:02:47 cory-laptop kernel: [  706.888000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:04:30 cory-laptop kernel: [  809.296000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:05:36 cory-laptop kernel: [  875.756000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:09:00 cory-laptop kernel: [ 1079.676000] wlan0: tx error 0x20, buf 12! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Oct 31 19:09:02 cory-laptop kernel: [ 1081.804000] wlan0: tx error 0x20, buf 09! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Oct 31 19:09:58 cory-laptop kernel: [ 1137.344000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:09:58 cory-laptop kernel: [ 1138.088000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:09:59 cory-laptop kernel: [ 1138.840000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:14:38 cory-laptop kernel: [ 1417.524000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:14:48 cory-laptop kernel: [ 1427.664000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:14:48 cory-laptop kernel: [ 1427.664000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:14:49 cory-laptop kernel: [ 1428.412000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:14:49 cory-laptop kernel: [ 1429.160000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:14:52 cory-laptop kernel: [ 1431.912000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:14:52 cory-laptop kernel: [ 1431.916000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:14:53 cory-laptop kernel: [ 1432.660000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:14:54 cory-laptop kernel: [ 1433.412000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:14:56 cory-laptop kernel: [ 1436.164000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:14:56 cory-laptop kernel: [ 1436.164000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:14:57 cory-laptop kernel: [ 1436.912000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:14:58 cory-laptop kernel: [ 1437.664000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:15:01 cory-laptop kernel: [ 1440.412000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:15:01 cory-laptop kernel: [ 1441.160000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:15:02 cory-laptop kernel: [ 1441.912000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:17:34 cory-laptop kernel: [ 1593.404000] acx: got IV_ICV_Failure (crypto) IRQ(s)
Oct 31 19:24:41 cory-laptop kernel: [ 2020.884000] acx: got IV_ICV_Failure (crypto) IRQ(s)
```

Thank you,
Cory

---

