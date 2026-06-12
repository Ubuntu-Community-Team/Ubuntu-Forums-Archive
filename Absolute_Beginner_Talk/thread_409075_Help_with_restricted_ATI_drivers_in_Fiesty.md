---
title: "Help with restricted ATI drivers in Fiesty"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by metroknight on 2007-04-14
Hi all,

	I need some help. I just upgraded to Fiesty (7.04) and everything was running fine until I went to my restricted drivers manager and made active my 3d effects. It showed that it was installed but not enabled so I put a checkmark next to it and closed. I rebooted the machine and now I get a blank screen. I'm talking about there is nothing coming to the monitor, no blue screen, no text, nothing. I'm using a Ati Radeon 9550 (shows up as a 9600).

	I need to know how to fix this in the recovery mode (text based). The first thing I would like to do isjust deactivate the 3d effect and see if that is the problem. If that doesn't fix it then I will need to do something more drastic.

	Right now I posting with my windows boot until I can get Ubuntu up and running again.

Thanks for any help or info.

---

### Post by xopher on 2007-04-14
Open up your xorg.conf:

```
sudo nano /etc/X11/xorg.conf
```

Go to your 3d-device section, and at Driver, replace fglrx with ati or radeon. These two are open-source drivers and should work without problems. Now save the file **CTRL+X**, and restart X:

```
sudo invoke-rc.d gdm restart
```

---

### Post by metroknight on 2007-04-14
Thank you for the help. I'm up and running with Fiesty again. Now I got to find out what is HAL and how to initialize him/it because I got an error code of "Failed to initialize HAL" on start up.

---

### Post by igknighted on 2007-04-14
Lots of people have had trouble with the restricted drivers manager.  The problem is if you don't use it to enable 3d drivers (nvidia or ATI) it will throw a fit.  I personally don't think it should ship default with feisty, it is a huge pain and very buggy, so ignore it as best you can is my advice.

---

### Post by metroknight on 2007-04-14
To Igknighted, Don't worry about that, I'm avoiding it for now maybe for even longer :) .

My next problem was with HAL but it seemed to clear up on it's own. I did a complete shutdown / restart and HAL is now working perfectly. Now I just need to make sure that certain programs I have are up to date and I should be good to go.

Thanks for you suggestions and help, xopher and igknighted.

---

### Post by igknighted on 2007-04-14
HAL is the "Hardware Abstraction Layer".  See this for more details:
[http://en.wikipedia.org/wiki/HAL_%28software%29](http://en.wikipedia.org/wiki/HAL_%28software%29)
and
[http://en.wikipedia.org/wiki/Hardware_abstraction_layer](http://en.wikipedia.org/wiki/Hardware_abstraction_layer)

As for how to fix it, I would be curious to see what your dmesg log (/var/log/dmesg I think) says after you finish booting if it fails again.

---

### Post by metroknight on 2007-04-14
>  As for how to fix it, I would be curious to see what your dmesg log (/var/log/dmesg I think) says after you finish booting if it fails again.

It fixed itself but here is the log

[    0.000000] Linux version 2.6.20-15-386 (root@vernadsky) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Sat Apr 14 00:50:49 UTC 2007 (Ubuntu 2.6.20-15.25-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000005fefc000 end: 000000005fffc000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000005fffc000 size: 0000000000003000 end: 000000005ffff000 type: 3
[    0.000000] copy_e820_map() start: 000000005ffff000 size: 0000000000001000 end: 0000000060000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fffc000 (usable)
[    0.000000]  BIOS-e820: 000000005fffc000 - 000000005ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005ffff000 - 0000000060000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 639MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 393212) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   393212
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   393212
[    0.000000] On node 0 totalpages: 393212
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1279 pages used for memmap
[    0.000000]   HighMem zone: 162557 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5f50
[    0.000000] ACPI: RSDT (v001 ASUS   A7V8X-X  0x42302e31 MSFT 0x31313031) @ 0x5fffc000
[    0.000000] ACPI: FADT (v001 ASUS   A7V8X-X  0x42302e31 MSFT 0x31313031) @ 0x5fffc0b2
[    0.000000] ACPI: BOOT (v001 ASUS   A7V8X-X  0x42302e31 MSFT 0x31313031) @ 0x5fffc030
[    0.000000] ACPI: MADT (v001 ASUS   A7V8X-X  0x42302e31 MSFT 0x31313031) @ 0x5fffc058
[    0.000000] ACPI: DSDT (v001   ASUS A7V8X-X  0x00001000 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[    0.000000] Detected 1724.903 MHz processor.
[   14.361894] Built 1 zonelists.  Total pages: 390141
[   14.361896] Kernel command line: root=UUID=60592717-5bd8-4095-a265-06d1cacaa99a ro quiet splash
[   14.362095] mapped APIC to ffffd000 (fee00000)
[   14.362098] mapped IOAPIC to ffffc000 (fec00000)
[   14.362103] Enabling fast FPU save and restore... done.
[   14.362105] Enabling unmasked SIMD FPU exception support... done.
[   14.362119] Initializing CPU#0
[   14.362211] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   14.363172] Console: colour VGA+ 80x25
[   14.364174] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.365821] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.424567] Memory: 1546960k/1572848k available (1916k kernel code, 24664k reserved, 864k data, 328k init, 655344k highmem)
[   14.424580] virtual kernel memory layout:
[   14.424581]     fixmap  : 0xfffa9000 - 0xfffff000   ( 344 kB)
[   14.424583]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.424584]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.424586]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.424587]       .init : 0xc03ba000 - 0xc040c000   ( 328 kB)
[   14.424589]       .data : 0xc02df353 - 0xc03b7434   ( 864 kB)
[   14.424590]       .text : 0xc0100000 - 0xc02df353   (1916 kB)
[   14.424594] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.502067] Calibrating delay using timer specific routine.. 3452.90 BogoMIPS (lpj=6905804)
[   14.502119] Security Framework v1.0.0 initialized
[   14.502133] SELinux:  Disabled at boot.
[   14.502151] Mount-cache hash table entries: 512
[   14.502334] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   14.502345] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.502349] CPU: L2 Cache: 256K (64 bytes/line)
[   14.502352] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   14.502368] Compat vDSO mapped to ffffe000.
[   14.502376] Remapping vsyscall page to ffffe000
[   14.502387] CPU: AMD Athlon(TM) XP 2100+ stepping 01
[   14.502395] Checking 'hlt' instruction... OK.
[   14.518804] Early unpacking initramfs... done
[   14.936177] ACPI: Core revision 20060707
[   14.936992] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   14.942056] ENABLING IO-APIC IRQs
[   14.942376] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.089692] Booting paravirtualized kernel on bare hardware
[   15.089792] Time:  5:21:01  Date: 03/14/107
[   15.089836] NET: Registered protocol family 16
[   15.089962] EISA bus registered
[   15.089968] ACPI: bus type pci registered
[   15.091341] PCI: PCI BIOS revision 2.10 entry at 0xf1990, last bus=1
[   15.091344] PCI: Using configuration type 1
[   15.091346] Setting up standard PCI resources
[   15.108870] ACPI: Interpreter enabled
[   15.108876] ACPI: Using IOAPIC for interrupt routing
[   15.109574] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12)
[   15.109799] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[   15.110011] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[   15.110224] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[   15.110525] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 9 10 11 12)
[   15.110802] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 12)
[   15.111001] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   15.111108] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.111115] PCI: Probing PCI hardware (bus 00)
[   15.111461] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   15.111949] PCI quirk: region e400-e47f claimed by vt8235 PM
[   15.111953] PCI quirk: region e800-e80f claimed by vt8235 SMB
[   15.112178] Boot video device is 0000:01:00.0
[   15.112260] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.113647] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   15.118176] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.118193] pnp: PnP ACPI init
[   15.122656] pnp: PnP ACPI: found 13 devices
[   15.122662] PnPBIOS: Disabled by ACPI PNP
[   15.122736] PCI: Using ACPI for IRQ routing
[   15.122741] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.127297] NET: Registered protocol family 8
[   15.127299] NET: Registered protocol family 20
[   15.127581] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
[   15.127585] pnp: 00:02: ioport range 0xe800-0xe81f could not be reserved
[   15.127600] pnp: 00:0c: ioport range 0x290-0x297 has been reserved
[   15.127603] pnp: 00:0c: ioport range 0x370-0x375 has been reserved
[   15.127922] PCI: Bridge: 0000:00:01.0
[   15.127925]   IO window: d000-dfff
[   15.127931]   MEM window: c7000000-c7ffffff
[   15.127935]   PREFETCH window: c8000000-dfffffff
[   15.127957] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.127993] NET: Registered protocol family 2
[   15.165430] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.165733] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[   15.166902] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   15.167455] TCP: Hash tables configured (established 131072 bind 65536)
[   15.167459] TCP reno registered
[   15.177537] checking if image is initramfs... it is
[   15.962248] Freeing initrd memory: 8056k freed
[   15.962495] Simple Boot Flag at 0x3a set to 0x1
[   15.962848] audit: initializing netlink socket (disabled)
[   15.962867] audit(1176528061.680:1): initialized
[   15.962947] highmem bounce pool size: 64 pages
[   15.963018] VFS: Disk quotas dquot_6.5.1
[   15.963048] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.963123] io scheduler noop registered
[   15.963127] io scheduler anticipatory registered
[   15.963129] io scheduler deadline registered
[   15.963137] io scheduler cfq registered (default)
[   15.963448] isapnp: Scanning for PnP cards...
[   16.316726] isapnp: No Plug & Play device found
[   16.364761] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.364884] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.366192] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.366616] mice: PS/2 mouse device common for all mice
[   16.367235] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.367547] input: Macintosh mouse button emulation as /class/input/input0
[   16.367585] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   16.367590] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   16.367847] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   16.367851] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   16.371034] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.371044] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.371254] EISA: Probing bus 0 at eisa.0
[   16.371291] EISA: Detected 0 cards.
[   16.401371] TCP cubic registered
[   16.401379] NET: Registered protocol family 1
[   16.401408] Using IPI Shortcut mode
[   16.401484] ACPI: (supports S0 S1 S4 S5)
[   16.401531]   Magic number: 3:389:365
[   16.402287] Freeing unused kernel memory: 328k freed
[   16.404032] Time: tsc clocksource has been installed.
[   16.415065] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.663379] Capability LSM initialized
[   17.682377] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   17.833650] md: linear personality registered for level -1
[   17.838025] md: multipath personality registered for level -4
[   17.842291] md: raid0 personality registered for level 0
[   17.847134] md: raid1 personality registered for level 1
[   17.851328] raid5: automatically using best checksumming function: pIII_sse
[   17.870454]    pIII_sse  :  4513.000 MB/sec
[   17.870457] raid5: using function: pIII_sse (4513.000 MB/sec)
[   17.942387] raid6: int32x1    671 MB/s
[   18.010385] raid6: int32x2    743 MB/s
[   18.078281] raid6: int32x4    635 MB/s
[   18.146275] raid6: int32x8    437 MB/s
[   18.214099] raid6: mmxx1     1407 MB/s
[   18.282031] raid6: mmxx2     2137 MB/s
[   18.349941] raid6: sse1x1    1300 MB/s
[   18.417879] raid6: sse1x2    2203 MB/s
[   18.417882] raid6: using algorithm sse1x2 (2203 MB/s)
[   18.417886] md: raid6 personality registered for level 6
[   18.417888] md: raid5 personality registered for level 5
[   18.417891] md: raid4 personality registered for level 4
[   18.461996] md: raid10 personality registered for level 10
[   18.976367] usbcore: registered new interface driver usbfs
[   18.976401] usbcore: registered new interface driver hub
[   18.976428] usbcore: registered new device driver usb
[   18.977583] USB Universal Host Controller Interface driver v3.0
[   18.977673] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 16
[   18.977689] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   18.977937] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   18.977973] uhci_hcd 0000:00:10.0: irq 16, io base 0x0000b800
[   18.978137] usb usb1: configuration #1 chosen from 1 choice
[   18.978169] hub 1-0:1.0: USB hub found
[   18.978183] hub 1-0:1.0: 2 ports detected
[   19.050157] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   19.081379] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 16
[   19.081397] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   19.081427] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   19.081455] uhci_hcd 0000:00:10.1: irq 16, io base 0x0000b400
[   19.081575] usb usb2: configuration #1 chosen from 1 choice
[   19.081614] hub 2-0:1.0: USB hub found
[   19.081626] hub 2-0:1.0: 2 ports detected
[   19.185309] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 16
[   19.185327] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   19.185361] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   19.185390] uhci_hcd 0000:00:10.2: irq 16, io base 0x0000b000
[   19.185525] usb usb3: configuration #1 chosen from 1 choice
[   19.185559] hub 3-0:1.0: USB hub found
[   19.185573] hub 3-0:1.0: 2 ports detected
[   19.293175] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 16
[   19.293196] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   19.293256] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   19.293321] ehci_hcd 0000:00:10.3: irq 16, io mem 0xc6000000
[   19.293328] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.293456] usb usb4: configuration #1 chosen from 1 choice
[   19.293490] hub 4-0:1.0: USB hub found
[   19.293504] hub 4-0:1.0: 6 ports detected
[   19.320943] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   19.397110] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   19.397139] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   19.397141] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[   19.397154] VP_IDE: chipset revision 6
[   19.397157] VP_IDE: not 100% native mode: will probe irqs later
[   19.397169] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   19.397179]     ide0: BM-DMA at 0xa800-0xa807, BIOS settings: hda:DMA, hdb:DMA
[   19.397194]     ide1: BM-DMA at 0xa808-0xa80f, BIOS settings: hdc:DMA, hdd:DMA
[   19.397205] Probing IDE interface ide0...
[   19.812462] hda: ST380011A, ATA DISK drive
[   20.092162] hdb: ST340016A, ATA DISK drive
[   20.149033] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   20.156165] Probing IDE interface ide1...
[   20.999114] usb 4-6: new high speed USB device using ehci_hcd and address 6
[   21.019168] hdc: LITE-ON DVD SOHD-16P9S, ATAPI CD/DVD-ROM drive
[   21.131826] usb 4-6: configuration #1 chosen from 1 choice
[   21.370706] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   21.551812] usb 1-1: configuration #1 chosen from 1 choice
[   21.794252] usb 1-2: new full speed USB device using uhci_hcd and address 4
[   21.802327] hdd: HL-DT-ST GCE-8520B, ATAPI CD/DVD-ROM drive
[   21.858572] ide1 at 0x170-0x177,0x376 on irq 15
[   21.866191] SCSI subsystem initialized
[   21.872440] libata version 2.20 loaded.
[   21.874006] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 17
[   21.874123] eth0: VIA Rhine II at 0x1a400, 00:0e:a6:b8:8e:9a, IRQ 17.
[   21.874840] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
[   21.882765] hda: max request size: 512KiB
[   21.898208] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   21.904327] hda: cache flushes supported
[   21.904397]  hda: hda1 hda2 < hda5 >
[   21.925276] hdb: max request size: 128KiB
[   21.925582] hdb: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   21.925589] hdb: cache flushes not supported
[   21.925625]  hdb: hdb1 hdb2 < hdb5 >
[   21.959317] usb 1-2: configuration #1 chosen from 1 choice
[   21.962250] hub 1-2:1.0: USB hub found
[   21.965162] hub 1-2:1.0: 4 ports detected
[   21.977141] hdc: ATAPI 48X DVD-ROM drive, 254kB Cache, UDMA(33)
[   21.977153] Uniform CD-ROM driver Revision: 3.20
[   22.014701] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   22.313738] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   22.479247] usb 2-1: configuration #1 chosen from 1 choice
[   22.482230] hub 2-1:1.0: USB hub found
[   22.485118] hub 2-1:1.0: 4 ports detected
[   22.525836] kjournald starting.  Commit interval 5 seconds
[   22.525853] EXT3-fs: mounted filesystem with ordered data mode.
[   22.833141] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   23.040504] usb 2-2: configuration #1 chosen from 1 choice
[   23.246511] usb 1-2.2: new full speed USB device using uhci_hcd and address 5
[   23.330406] usb 1-2.2: device descriptor read/64, error -71
[   23.622142] usb 1-2.2: configuration #1 chosen from 1 choice
[   23.633637] usbcore: registered new interface driver libusual
[   23.634044] usbcore: registered new interface driver hiddev
[   23.705082] input: Microsoft Microsoft Trackball Optical® as /class/input/input2
[   23.705110] input: USB HID v1.00 Mouse [Microsoft Microsoft Trackball Optical®] on usb-0000:00:10.0-1
[   23.705136] usbcore: registered new interface driver usbhid
[   23.705141] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   24.020936] Initializing USB Mass Storage driver...
[   24.021103] scsi0 : SCSI emulation for USB Mass Storage devices
[   24.021166] usb-storage: device found at 6
[   24.021168] usb-storage: waiting for device to settle before scanning
[   24.021220] scsi1 : SCSI emulation for USB Mass Storage devices
[   24.021260] usb-storage: device found at 5
[   24.021262] usb-storage: waiting for device to settle before scanning
[   24.021273] usbcore: registered new interface driver usb-storage
[   24.021276] USB Mass Storage support registered.
[   29.014700] usb-storage: device scan complete
[   29.015823] scsi 0:0:0:0: Direct-Access     Generic  USB Flash Disk   0.00 PQ: 0 ANSI: 2
[   29.016054] usb-storage: device scan complete
[   29.019020] scsi 1:0:0:0: Direct-Access              MS Reader        1.05 PQ: 0 ANSI: 0 CCS
[   35.929373] ath_hal: module license 'Proprietary' taints kernel.
[   35.930265] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   36.078501] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.088717] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.477187] wlan: 0.8.4.2 (0.9.3)
[   36.505776] Linux agpgart interface v0.102 (c) Dave Jones
[   36.525920] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   36.544525] agpgart: AGP aperture is 256M @ 0xe0000000
[   36.665659] ath_pci: 0.9.4.5 (0.9.3)
[   36.665726] PCI: Enabling device 0000:00:0b.0 (0014 -> 0016)
[   36.665742] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 18
[   37.260946] irda_init()
[   37.260982] NET: Registered protocol family 23
[   37.597821] ath_rate_sample: 1.2 (0.9.3)
[   37.598599] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   37.598606] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   37.598615] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   37.598619] wifi0: mac 7.8 phy 4.5 radio 5.6
[   37.598624] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   37.598627] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   37.598629] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   37.598632] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   37.598634] wifi0: Use hw queue 8 for CAB traffic
[   37.598636] wifi0: Use hw queue 9 for beacons
[   37.872380] wifi0: Atheros 5212: mem=0xc6800000, irq=18
[   38.000683] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1204
[   38.000707] usbcore: registered new interface driver usblp
[   38.000712] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   38.087892] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 19
[   38.092807] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   38.214485] input: PC Speaker as /class/input/input3
[   38.236204] parport: PnPBIOS parport detected.
[   38.236275] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   38.256065] SCSI device sda: 2015232 512-byte hdwr sectors (1032 MB)
[   38.260053] sda: Write Protect is off
[   38.260059] sda: Mode Sense: 00 00 00 00
[   38.260062] sda: assuming drive cache: write through
[   38.267574] SCSI device sda: 2015232 512-byte hdwr sectors (1032 MB)
[   38.269309] sda: Write Protect is off
[   38.269316] sda: Mode Sense: 00 00 00 00
[   38.269319] sda: assuming drive cache: write through
[   38.269326]  sda:<6>Real Time Clock Driver v1.12ac
[   38.344556]  sda1
[   38.344712] sd 0:0:0:0: Attached scsi removable disk sda
[   38.351020] sd 1:0:0:0: Attached scsi removable disk sdb
[   38.368839] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   38.368884] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   38.606635] codec_read: codec 0 is not valid [0x107e5370]
[   38.612876] codec_read: codec 0 is not valid [0x107e5370]
[   38.619087] codec_read: codec 0 is not valid [0x107e5370]
[   38.625253] codec_read: codec 0 is not valid [0x107e5370]
[   39.750321] lp0: using parport0 (interrupt-driven).
[   39.827162] Adding 1614492k swap on /dev/disk/by-uuid/2bad6b68-cd67-41c3-8a87-270473b1bf2d.  Priority:-1 extents:1 across:1614492k
[   39.961043] EXT3 FS on hdb1, internal journal
[   40.608892] NET: Registered protocol family 17
[   41.711477] Adding 1614492k swap on /dev/disk/by-uuid/2bad6b68-cd67-41c3-8a87-270473b1bf2d.  Priority:-2 extents:1 across:1614492k

---

### Post by igknighted on 2007-04-14
if I had to guess I would have thought it would fix itself.  I bet in the goings on with the restricted driver thing it upset MadWiFi which works with HAL I believe, but it looks good now so I'd forget about it.

---

### Post by metroknight on 2007-04-14
Ok I will because all of that log is totally gibberish to me at this time.

---

### Post by sammao on 2007-04-21
This is the ****: Search for envy in google. Works for me..

---

### Post by metroknight on 2007-04-21
Why is this the ****: From what I've read on the  forums, envy is for Nvidia not what I have. Which is ATI. Oh, the google search just comes up with nonsense about the emotion envy.

---

### Post by koztaz on 2007-04-22
There is new version of ENVY (0.9.2) and it suports ATI driver 8.35.5

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

