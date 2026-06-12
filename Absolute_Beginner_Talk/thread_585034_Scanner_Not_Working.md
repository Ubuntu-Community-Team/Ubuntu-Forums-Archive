---
title: "Scanner Not Working"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by t.z0n3 on 2007-10-21
I know there are several threads like this one, but I can't find much help. 

My scanner is a Canoscan N1240U, and Sane's website says it is complete supported. Of course, that doesn't help. When I open the application, it finds my scanner, but when I tell it to scan, it won't do anything. The device is 'unlocked' (total newb check there). I need this thing to work, and it's frustrating me to no end. Does anybody have any ideas?

---

### Post by Daveth on 2007-10-21
well , it looks like it used to work, which is good news. I'll see what I can track down for you.

[https://wiki.ubuntu.com/HardwareSupportComponentsScannersCanon](https://wiki.ubuntu.com/HardwareSupportComponentsScannersCanon)

---

### Post by t.z0n3 on 2007-10-21
Thanks very much. ^_^

---

### Post by jviscosi on 2007-10-21
My scanner quit working a while ago because of some changes that had been made in the sleep time of USB devices, or something.  The workaround was running the scanner via a script instead of directly and invoking scanbuttond ahead of it, for instance:

```

scanbuttond -r 1000000 
kooka
kill `pidof scanbuttond`

```This keeps the scanner "awake" and lets it operate.  Not sure if it would work for you but may be worth a try.  (Replace "kooka" with your preferred scanner app, of course.)

More information can be found [here]("http://www.ubuntugeek.com/fixing-a-scanner-broken-by-the-feisty-upgrade.html").

---

### Post by Daveth on 2007-10-21
um, have you tried

```
sudo-find-scanner
```

and then

```
sudo apt-get install sane-utils
```

taken from 

[http://ubuntuforums.org/showthread.php?t=471779&highlight=canon+sane](http://ubuntuforums.org/showthread.php?t=471779&highlight=canon+sane)

- not your model but the process should be the same.



and for when you have it working (as I will never be able to re-find it again!)

[http://ubuntuforums.org/archive/index.php/t-189613.html](http://ubuntuforums.org/archive/index.php/t-189613.html)

---

### Post by t.z0n3 on 2007-10-21
Daveth, I tried that after looking at another person's thread, and it finds it, but no luck on making it work. Thanks much, though. It's a handy set of utils anyway.

As for jviscosi, I attempted everything and it worked: up to number 4. 

```
matthew@matthew:~$ scanimage -L
device `plustek:libusb:002:002' is a Canon N1240U/LiDE30 USB flatbed scanner
matthew@matthew:~$ scanimage -T -d plustek:libusb:002:002
scanimage: open of device plustek:libusb:002:002 failed: Error during device I/O

```

---

### Post by Daveth on 2007-10-21
what about uninstalling xsane, and then putting it back, hoping that it "bed in" with the system's recognition of the usb device and then work. After all, it is supposed to work out of the box- I think it just needs telling that!

---

### Post by jviscosi on 2007-10-21
> **t.z0n3 said:**
> I attempted everything and it worked: up to number 4. 

```
matthew@matthew:~$ scanimage -L
device `plustek:libusb:002:002' is a Canon N1240U/LiDE30 USB flatbed scanner
matthew@matthew:~$ scanimage -T -d plustek:libusb:002:002
scanimage: open of device plustek:libusb:002:002 failed: Error during device I/O

```

Hmm, does the **dmesg** command show you anything interesting?  

If the scanner is connected to a hub, I'd suggest moving it to a port on the computer (if you can) and trying again.  You could also try just moving it to a different port and also try a different cable, if you have one.

---

### Post by t.z0n3 on 2007-10-21
What should I be looking for in the dsmeg message?

```
matthew@matthew:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:50:39 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fef0000 end: 000000001fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fff0000 size: 0000000000003000 end: 000000001fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000001fff3000 size: 000000000000d000 end: 0000000020000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f75c0
[    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff74c0
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:10 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Detected 1830.100 MHz processor.
[   17.768774] Built 1 zonelists.  Total pages: 130033
[   17.768778] Kernel command line: root=UUID=c5ebd93a-701c-4b3b-b97e-6f5efd1fbc83 ro quiet splash
[   17.768952] mapped APIC to ffffd000 (fee00000)
[   17.768955] mapped IOAPIC to ffffc000 (fec00000)
[   17.768958] Enabling fast FPU save and restore... done.
[   17.768960] Enabling unmasked SIMD FPU exception support... done.
[   17.768971] Initializing CPU#0
[   17.769028] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   17.770322] Console: colour VGA+ 80x25
[   17.770636] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.770890] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.783420] Memory: 508600k/524224k available (1993k kernel code, 14980k reserved, 900k data, 328k init, 0k highmem)
[   17.783432] virtual kernel memory layout:
[   17.783433]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   17.783434]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.783436]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   17.783437]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   17.783438]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   17.783440]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
[   17.783441]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
[   17.783445] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.860946] Calibrating delay using timer specific routine.. 3662.96 BogoMIPS (lpj=7325933)
[   17.860992] Security Framework v1.0.0 initialized
[   17.860999] SELinux:  Disabled at boot.
[   17.861017] Mount-cache hash table entries: 512
[   17.861170] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   17.861180] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.861183] CPU: L2 Cache: 512K (64 bytes/line)
[   17.861186] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   17.861197] Compat vDSO mapped to ffffe000.
[   17.861202] Remapping vsyscall page to ffffe000
[   17.861212] Checking 'hlt' instruction... OK.
[   17.877059] SMP alternatives: switching to UP code
[   17.877302] Freeing SMP alternatives: 11k freed
[   17.877532] Early unpacking initramfs... done
[   18.198581] ACPI: Core revision 20060707
[   18.205319] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.208308] CPU0: AMD Athlon(tm) XP 2500+ stepping 00
[   18.208330] Total of 1 processors activated (3662.96 BogoMIPS).
[   18.208527] ENABLING IO-APIC IRQs
[   18.208735] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   18.352530] Brought up 1 CPUs
[   18.352788] Booting paravirtualized kernel on bare hardware
[   18.352864] Time: 14:00:26  Date: 09/21/107
[   18.352903] NET: Registered protocol family 16
[   18.353002] EISA bus registered
[   18.353007] ACPI: bus type pci registered
[   18.384861] PCI: PCI BIOS revision 2.10 entry at 0xfb4a0, last bus=2
[   18.384864] PCI: Using configuration type 1
[   18.384866] Setting up standard PCI resources
[   18.397371] ACPI: Interpreter enabled
[   18.397374] ACPI: Using IOAPIC for interrupt routing
[   18.397982] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.397988] PCI: Probing PCI hardware (bus 00)
[   18.398243] PCI: nForce2 C1 Halt Disconnect fixup
[   18.398846] Boot video device is 0000:02:00.0
[   18.398936] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.455740] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   18.456266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   18.457313] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   18.457621] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   18.457925] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   18.458230] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   18.458540] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   18.458847] ACPI: PCI Interrupt Link [LUBA] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   18.459152] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   18.459460] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   18.459764] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   18.460072] ACPI: PCI Interrupt Link [LACI] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   18.460387] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   18.460699] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   18.461006] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   18.461320] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   18.461626] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   18.461934] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   18.462222] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[   18.462492] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[   18.462760] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[   18.463028] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
[   18.463293] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   18.463644] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
[   18.463993] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[   18.464343] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[   18.464708] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[   18.465054] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[   18.465400] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[   18.465666] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[   18.466015] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
[   18.466362] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[   18.466706] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[   18.467051] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[   18.470136] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.470148] pnp: PnP ACPI init
[   18.475700] pnp: PnP ACPI: found 15 devices
[   18.475704] PnPBIOS: Disabled by ACPI PNP
[   18.475766] PCI: Using ACPI for IRQ routing
[   18.475772] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.510964] NET: Registered protocol family 8
[   18.510967] NET: Registered protocol family 20
[   18.511590] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
[   18.511594] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[   18.511597] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[   18.511600] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
[   18.511603] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
[   18.511606] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
[   18.511611] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
[   18.511614] pnp: 00:01: ioport range 0x5500-0x553f has been reserved
[   18.511906] PCI: Bridge: 0000:00:08.0
[   18.511908]   IO window: disabled.
[   18.511913]   MEM window: disabled.
[   18.511917]   PREFETCH window: disabled.
[   18.511924] PCI: Bridge: 0000:00:1e.0
[   18.511927]   IO window: c000-cfff
[   18.511931]   MEM window: e8000000-e9ffffff
[   18.511935]   PREFETCH window: c0000000-dfffffff
[   18.511946] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   18.511982] NET: Registered protocol family 2
[   18.548389] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   18.548486] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   18.548672] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   18.548765] TCP: Hash tables configured (established 16384 bind 8192)
[   18.548768] TCP reno registered
[   18.560407] checking if image is initramfs... it is
[   19.171168] Freeing initrd memory: 6786k freed
[   19.171679] audit: initializing netlink socket (disabled)
[   19.171700] audit(1192975227.492:1): initialized
[   19.171822] VFS: Disk quotas dquot_6.5.1
[   19.171841] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.171891] io scheduler noop registered
[   19.171894] io scheduler anticipatory registered
[   19.171896] io scheduler deadline registered
[   19.171904] io scheduler cfq registered (default)
[   19.172172] isapnp: Scanning for PnP cards...
[   19.526297] isapnp: No Plug & Play device found
[   19.551821] Real Time Clock Driver v1.12ac
[   19.551878] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.552013] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.552635] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.552864] mice: PS/2 mouse device common for all mice
[   19.553477] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.553729] input: Macintosh mouse button emulation as /class/input/input0
[   19.553765] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   19.553769] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   19.553988] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   19.557413] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.557420] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.557575] EISA: Probing bus 0 at eisa.0
[   19.557601] Cannot allocate resource for EISA slot 4
[   19.557604] Cannot allocate resource for EISA slot 5
[   19.557623] EISA: Detected 0 cards.
[   19.587693] TCP cubic registered
[   19.587700] NET: Registered protocol family 1
[   19.587723] Using IPI No-Shortcut mode
[   19.587784] ACPI: (supports S0 S1 S4 S5)
[   19.587837]   Magic number: 11:49:31
[   19.587848]   hash matches device ttyde
[   19.588409] Freeing unused kernel memory: 328k freed
[   19.591308] Time: tsc clocksource has been installed.
[   19.602775] input: AT Translated Set 2 keyboard as /class/input/input1
[   20.824327] Capability LSM initialized
[   21.370738] usbcore: registered new interface driver usbfs
[   21.370767] usbcore: registered new interface driver hub
[   21.370793] usbcore: registered new device driver usb
[   21.371529] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.372003] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   21.372013] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 16
[   21.372028] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   21.372032] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   21.372212] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   21.372232] ohci_hcd 0000:00:02.0: irq 16, io mem 0xea004000
[   21.413086] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   21.434446] SCSI subsystem initialized
[   21.439761] libata version 2.20 loaded.
[   21.459933] usb usb1: configuration #1 chosen from 1 choice
[   21.459975] hub 1-0:1.0: USB hub found
[   21.459988] hub 1-0:1.0: 3 ports detected
[   21.565912] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[   21.565923] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 17
[   21.565941] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   21.565945] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   21.565972] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   21.565992] ohci_hcd 0000:00:02.1: irq 17, io mem 0xea005000
[   21.581234] Floppy drive(s): fd0 is 1.44M
[   21.623283] FDC 0 is a post-1991 82077
[   21.629355] usb usb2: configuration #1 chosen from 1 choice
[   21.629402] hub 2-0:1.0: USB hub found
[   21.629417] hub 2-0:1.0: 3 ports detected
[   21.737837] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   21.737850] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 18
[   21.737864] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   21.737868] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   21.737895] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   21.737938] ehci_hcd 0000:00:02.2: debug port 1
[   21.737944] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   21.737957] ehci_hcd 0000:00:02.2: irq 18, io mem 0xea000000
[   21.737965] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.738050] usb usb3: configuration #1 chosen from 1 choice
[   21.738080] hub 3-0:1.0: USB hub found
[   21.738091] hub 3-0:1.0: 6 ports detected
[   21.841690] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   21.841697] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 16
[   21.841705] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   22.352817] eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:04.0
[   22.357426] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[   22.357453] NFORCE2: chipset revision 162
[   22.357456] NFORCE2: not 100% native mode: will probe irqs later
[   22.357461] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[   22.357467] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[   22.357478]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   22.357490]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   22.357498] Probing IDE interface ide0...
[   22.444496] usb 3-6: new high speed USB device using ehci_hcd and address 3
[   22.600943] usb 3-6: configuration #1 chosen from 1 choice
[   22.644480] hda: WDC WD1000BB-00CAA1, ATA DISK drive
[   22.908045] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   23.138572] usb 2-1: configuration #1 chosen from 1 choice
[   23.142868] usbcore: registered new interface driver libusual
[   23.147712] Initializing USB Mass Storage driver...
[   23.147833] scsi0 : SCSI emulation for USB Mass Storage devices
[   23.147887] usb-storage: device found at 3
[   23.147890] usb-storage: waiting for device to settle before scanning
[   23.147911] usbcore: registered new interface driver usb-storage
[   23.147915] USB Mass Storage support registered.
[   23.317343] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   23.336396] Probing IDE interface ide1...
[   24.071042] hdc: PIONEER DVD-RW DVR-105, ATAPI CD/DVD-ROM drive
[   24.854290] hdd: LITE-ON LTR-52246S, ATAPI CD/DVD-ROM drive
[   24.917632] ide1 at 0x170-0x177,0x376 on irq 15
[   24.931205] hda: max request size: 128KiB
[   24.944000] hda: 195371568 sectors (100030 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   24.944009] hda: cache flushes not supported
[   24.944065]  hda: hda1 hda2 hda3
[   24.988695] hdc: ATAPI 32X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[   24.988705] Uniform CD-ROM driver Revision: 3.20
[   25.026450] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   25.232058] Attempting manual resume
[   25.232063] swsusp: Resume From Partition 3:2
[   25.232065] PM: Checking swsusp image.
[   25.232202] PM: Resume from disk failed.
[   25.263673] kjournald starting.  Commit interval 5 seconds
[   25.263686] EXT3-fs: mounted filesystem with ordered data mode.
[   28.103531] usb-storage: device scan complete
[   28.104521] scsi 0:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1.02 PQ: 0 ANSI: 0
[   35.792041] NET: Registered protocol family 17
[   36.152118] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   36.152161] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5500
[   36.338635] Linux agpgart interface v0.102 (c) Dave Jones
[   36.384473] agpgart: Detected NVIDIA nForce2 chipset
[   36.394875] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.395308] agpgart: AGP aperture is 128M @ 0xe0000000
[   36.396684] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.985991] parport: PnPBIOS parport detected.
[   36.986023] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   37.088372] input: PC Speaker as /class/input/input2
[   37.403210] SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
[   37.444554] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   37.473064] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[   37.473071] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 21 (level, high) -> IRQ 17
[   37.473099] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   37.521873] usb 3-6: reset high speed USB device using ehci_hcd and address 3
[   37.797554] intel8x0_measure_ac97_clock: measured 56808 usecs
[   37.797558] intel8x0: clocking to 48000
[   38.053308] usb 3-6: reset high speed USB device using ehci_hcd and address 3
[   38.580794] usb 3-6: reset high speed USB device using ehci_hcd and address 3
[   39.112274] usb 3-6: reset high speed USB device using ehci_hcd and address 3
[   39.643758] usb 3-6: reset high speed USB device using ehci_hcd and address 3
[   40.175238] usb 3-6: reset high speed USB device using ehci_hcd and address 3
[   40.343694] sda: Write Protect is off
[   40.343699] sda: Mode Sense: 02 00 00 00
[   40.343702] sda: assuming drive cache: write through
[   40.610423] SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
[   40.730696] usb 3-6: reset high speed USB device using ehci_hcd and address 3
[   41.262177] usb 3-6: reset high speed USB device using ehci_hcd and address 3
[   41.793657] usb 3-6: reset high speed USB device using ehci_hcd and address 3
[   42.325139] usb 3-6: reset high speed USB device using ehci_hcd and address 3
[   42.852636] usb 3-6: reset high speed USB device using ehci_hcd and address 3
[   43.384111] usb 3-6: reset high speed USB device using ehci_hcd and address 3
[   43.548656] sda: Write Protect is off
[   43.548660] sda: Mode Sense: 02 00 00 00
[   43.548663] sda: assuming drive cache: write through
[   43.548669]  sda: sda1
[   43.813989] sd 0:0:0:0: Attached scsi removable disk sda
[   43.850760] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   44.568935] fuse init (API version 7.8)
[   44.594011] lp0: using parport0 (interrupt-driven).
[   44.625447] Adding 2000084k swap on /dev/disk/by-uuid/464be414-5b84-49fb-93d9-8b12c6ffc147.  Priority:-1 extents:1 across:2000084k
[   90.286793] EXT3 FS on hda1, internal journal
[   90.515841] NET: Registered protocol family 10
[   90.515944] lo: Disabled Privacy Extensions
[   90.561093] kjournald starting.  Commit interval 5 seconds
[   90.561235] EXT3 FS on hda3, internal journal
[   90.561241] EXT3-fs: mounted filesystem with ordered data mode.
[   95.687460] Using specific hotkey driver
[   95.730231] ibm_acpi: ec object not found
[   95.837358] input: Power Button (FF) as /class/input/input4
[   95.842132] ACPI: Power Button (FF) [PWRF]
[   95.876546] input: Power Button (CM) as /class/input/input5
[   95.881335] ACPI: Power Button (CM) [PWRB]
[   95.918397] No dock devices found.
[   96.005962] pcc_acpi: loading...
[  100.808282] eth0: no IPv6 routers present
[  101.710674] ppdev: user-space parallel port driver
[  103.287376] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  103.295163] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[  103.295565] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[  103.532945] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[  103.532959] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 19
[  103.549463] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  103.549470] apm: overridden by ACPI.
[  104.501251] Bluetooth: Core ver 2.11
[  104.501330] NET: Registered protocol family 31
[  104.501333] Bluetooth: HCI device and connection manager initialized
[  104.501337] Bluetooth: HCI socket layer initialized
[  104.635174] Bluetooth: L2CAP ver 2.8
[  104.635179] Bluetooth: L2CAP socket layer initialized
[  105.393771] Bluetooth: RFCOMM socket layer initialized
[  105.393789] Bluetooth: RFCOMM TTY layer initialized
[  105.393792] Bluetooth: RFCOMM ver 1.8
[  107.200149] [fglrx] Internal AGP support requested, but kernel AGP support active.
[  107.200159] [fglrx] Have to use kernel AGP support to avoid conflicts.
[  107.200164] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[  107.201184] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  107.201461] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  107.201762] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[  107.202093] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[  107.210578] [fglrx] total      GART = 134217728
[  107.210588] [fglrx] free       GART = 118222848
[  107.210591] [fglrx] max single GART = 118222848
[  107.210593] [fglrx] total      LFB  = 134217728
[  107.210595] [fglrx] free       LFB  = 116387840
[  107.210597] [fglrx] max single LFB  = 116387840
[  107.210599] [fglrx] total      Inv  = 0
[  107.210601] [fglrx] free       Inv  = 0
[  107.210603] [fglrx] max single Inv  = 0
[  107.210604] [fglrx] total      TIM  = 0
[  116.297198] eth0: no IPv6 routers present
[  147.671420] ISO 9660 Extensions: Microsoft Joliet Level 3
[  147.712343] ISO 9660 Extensions: RRIP_1991A
[  609.828507] ppdev0: registered pardevice
[  609.868179] ppdev0: unregistered pardevice
[  840.540824] ppdev0: registered pardevice
[  840.580019] ppdev0: unregistered pardevice
[ 7293.114687] ppdev0: registered pardevice
[ 7293.193750] ppdev0: unregistered pardevice
[10419.791152] ppdev0: registered pardevice
[10419.836055] ppdev0: unregistered pardevice

```

---

### Post by jviscosi on 2007-10-21
Actually that dmesg all looks normal to me (anything related to your scan attempt should have been at the bottom).

Can you try running scanimage via strace, i.e.:
[B]
strace scanimage -T -d plustek:libusb:002:002[/B]

That might show at what point it's failing.  There will be a lot of output so if you want to capture it in a file and review it at your leisure, you can run something like:

[B] strace -o scan.txt scanimage -T -d plustek:libusb:002:002

[/B]This will create a file in the current directory called scan.txt that will contain messages from scanimage as it runs.

---

### Post by t.z0n3 on 2007-10-21
```
matthew@matthew:~$  strace -o scan.txt scanimage -T -d plustek:libusb:002:002
umovestr: Input/output error
scanimage: scanning image of size 202x150 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 606 bytes...   PASS
scanimage: reading one byte...          PASS
scanimage: stepped read, 2 bytes...     PASS
scanimage: stepped read, 4 bytes...     PASS
scanimage: stepped read, 8 bytes...     PASS
scanimage: stepped read, 16 bytes...    PASS
scanimage: stepped read, 32 bytes...    PASS
scanimage: stepped read, 64 bytes...    PASS
scanimage: stepped read, 128 bytes...   PASS
scanimage: stepped read, 256 bytes...   PASS
scanimage: stepped read, 512 bytes...   PASS
scanimage: stepped read, 1024 bytes...  PASS
scanimage: stepped read, 1023 bytes...  PASS
scanimage: stepped read, 511 bytes...   PASS
scanimage: stepped read, 255 bytes...   PASS
scanimage: stepped read, 127 bytes...   PASS
scanimage: stepped read, 63 bytes...    PASS
scanimage: stepped read, 31 bytes...    PASS
scanimage: stepped read, 15 bytes...    PASS
scanimage: stepped read, 7 bytes...     PASS
scanimage: stepped read, 3 bytes...     PASS

```

Whatever that thing is at the top is what's wrong, apparently. And...wow. You know a lot about scanners. o.0

---

### Post by jviscosi on 2007-10-21
> **t.z0n3 said:**
> Whatever that thing is at the top is what's wrong, apparently. And...wow. You know a lot about scanners. o.0

LOL ... thanks, but I really don't know all that much about scanners in particular ... I've just been doing troubleshooting for a long time.  So far this is all fairly generic stuff; **dmesg** dumps system messages to your terminal (which can reveal interesting things) and **strace** watches system calls and signals.  It can actually be used with just about any program.

Anyway, it looks like in your case strace has altered scanimage's behavior, since you got all that output.  (It appears to be the correct output, too; it matches the output I get when I run scanimage, except I don't get the error that you do.)  I have seen this sort of behavior before and in fact I used to run my password-management program under strace all the time, because it would crash if invoked directly but ran fine if invoked via strace.  So that would lead me to think that your scanner is fine and you don't really need to move it to another port.  

I haven't found much about umovestr yet except that it might be a permissions issue and/or a bad address. You might not have permissions on the USB port as a regular user (I had such a problem once when I used to run Mandriva).  I'd try running scanimage without strace, as root, and see what happens, i.e., 

**sudo scanimage -T -d plustek:libusb:002:002**

I think at this point I would also try running your GUI scanning (xsane or kooka or whatever) and see what results you get.  If it doesn't work, try invoking it under strace (e.g., **strace -f -o xsane.trace xsane**) and see if it works then.  (The **-f** flag tells strace to follow forks, in case your scanner program forks off to another process.) If not, see if it reports the same error as scanimage.  You could also try running your scanner GUI as root.

DISCLAIMER:  Running stuff as root is in general not a good practice.  It is however a valuable troubleshooting tool.  ;-)

---

### Post by t.z0n3 on 2007-10-21
o.o It just suddenly worked. 

...Er... Whatever you did? Thanks. ^_^

---

### Post by jviscosi on 2007-10-21
It's probably the scanbuttond process that's making it work.  Keep that running and you should be fine!  :-)

---

