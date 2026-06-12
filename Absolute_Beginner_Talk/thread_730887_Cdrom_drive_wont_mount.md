---
title: "Cdrom drive wont mount"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2008-03-21
Im helping a friend with his new Linux laptop, and everything is working fine, only the cdrom drive wont mount.

Its listed in  fstab like this:
> /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


When I double click the icon in "Computer" it says:
Unable to mount the selected volume.
Details: mount: special device /dev/scd0 does not exist

I thought it had something to do with powertop suggesting disabling cdrom polling so when I try the fix everytone else seem to be using I get following error:
> jesper@Jesper-laptop:~$ sudo hal-disable-polling --device /dev/scd0 --enable-polling
Cannot find storage device /dev/scd0.


Can anyone help me out here?  Would be awesome!

---

### Post by dannyboy79 on 2008-03-21
is your cd-rom really a scsi drive? If not, your fstab should be /dev/cdrom or /dev/dvd or /dev/dvdrw or /dev/cdrw. What does this command return when you enter it in a terminal session?

ls -la /dev/ | grep cd

OR

ls -la /dev/ | grep dvd

it should return what it's mapped to. Mine returns this FYI
cdrom -> hda

so I could also change my fstab to be /dev/hda instead of /dev/cdrom if I wanted but either hal or udev is mapping it automatically. Let me know if you need more help.

---

### Post by aktiwers on 2008-03-21
Hi and thanks for the reply! :)

> jesper@Jesper-laptop:~$ ls -la /dev/ | grep cd
crw-rw-rw-  1 root   tty       2, 221 2008-03-21 15:01 ptycd
crw-rw-rw-  1 root   tty       3, 221 2008-03-21 15:01 ttycd
jesper@Jesper-laptop:~$

> jesper@Jesper-laptop:~/Desktop/kernelcheck-1.0.5$ ls -la /dev/ | grep dvd
jesper@Jesper-laptop:~/Desktop/kernelcheck-1.0.5$ 


So what should I change my fstab to?

---

### Post by dannyboy79 on 2008-03-21
apparently your cdrom isn't even being registered or mapped by udev or hal? Are you sure your cdrom is even working? If you enter this command in your terminal session,

dmesg

It will be a lot of info
then scroll back up and see if you can see any errors about a cdrom.

When I do this command on my machine, this is what it returns.

dmesg | grep CD

[    3.996576] hda: Optiarc DVD RW AD-7170A, ATAPI CD/DVD-ROM drive
[    5.794396]  hdc:<6>hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[    5.795695] Uniform CD-ROM driver Revision: 3.20

---

### Post by aktiwers on 2008-03-21
The funny thing is that the cddrive did seam not to be registred correct when I installed Ubuntu, but then I gave it a good old slap and it worked and booted the CD. It even installed the Ubuntu from the drive, so I assumed it was fixed..

> jesper@Jesper-laptop:~/Desktop/kernelcheck-1.0.5$ dmesg | grep cd
[    8.172000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    8.172000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    8.172000] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001820
[    8.276000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    8.276000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    8.276000] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    8.380000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    8.380000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    8.380000] uhci_hcd 0000:00:1d.0: irq 22, io base 0x00001860
[    8.484000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    8.484000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    8.484000] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001880
[    8.588000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    8.588000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    8.588000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    8.692000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    8.692000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    8.692000] ehci_hcd 0000:00:1a.7: debug port 1
[    8.692000] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfc504800
[    8.696000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    8.800000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    8.800000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    8.800000] ehci_hcd 0000:00:1d.7: debug port 1
[    8.800000] ehci_hcd 0000:00:1d.7: irq 22, io mem 0xfc504c00
[    8.804000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    9.584000] usb 4-1: new low speed USB device using uhci_hcd and address 2
[ 1652.640000] usb 4-2: new low speed USB device using uhci_hcd and address 3
[ 1783.284000] usb 7-5: new high speed USB device using ehci_hcd and address 4
jesper@Jesper-laptop:~/Desktop/kernelcheck-1.0.5$

Im pretty sure this could have something to do with me trying to uptimes the power savings using powertop. I disabled cdrom polling but dont seam to be able to enable it again (as stated in first post)...

Hmm  I was thinking about compiling the latest kernel and see if that fixes it, but if you have more suggestions, please let me know :)

---

### Post by aktiwers on 2008-03-21
here is dmesg..  do you see anything there?

> 

[    0.000000] ACPI: DSDT 3F6D2BBB, 8FA8 (r2 INTEL  CRESTLNE  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 3F6DEFC0, 0040
[    0.000000] ACPI: HPET 3F6DBCCB, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 3F6DBD03, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 3F6DBD3F, 0032 (r1 Intel   CRESTLN  6040000          5A52)
[    0.000000] ACPI: TMOR 3F6DBD71, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: SLIC 3F6DBD97, 0176 (r1 ACRSYS ACRPRDCT  6040000 ANNI        1)
[    0.000000] ACPI: ASF! 3F6DBF0D, 0063 (r32 OEMID  OEMTBL    6040000 PTL         1)
[    0.000000] ACPI: APIC 3F6DBF70, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3F6DBFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 3F6D28DE, 02DD (r1 SataRe SataAhci     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6D2713, 01CB (r1 BrtRef  DD01BRT     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6D1B52, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6D1AAC, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6D15C6, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Built 1 zonelists.  Total pages: 257763
[    0.000000] Kernel command line: root=UUID=a640bb2e-0f6b-4ba6-8b32-74f385335a5a ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1662.608 MHz processor.
[   10.237946] Console: colour VGA+ 80x25
[   10.238339] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   10.238690] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.265413] Memory: 1018556k/1039168k available (2015k kernel code, 19904k reserved, 915k data, 364k init, 121664k highmem)
[   10.265422] virtual kernel memory layout:
[   10.265423]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   10.265424]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.265425]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   10.265427]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   10.265428]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   10.265429]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   10.265430]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   10.265433] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.265464] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   10.265607] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   10.265612] hpet0: 3 64-bit timers, 14318180 Hz
[   10.346507] Calibrating delay using timer specific routine.. 3328.53 BogoMIPS (lpj=6657061)
[   10.346526] Security Framework v1.0.0 initialized
[   10.346530] SELinux:  Disabled at boot.
[   10.346542] Mount-cache hash table entries: 512
[   10.346647] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   10.346654] monitor/mwait feature present.
[   10.346656] using mwait in idle threads.
[   10.346659] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.346662] CPU: L2 cache: 2048K
[   10.346664] CPU: Physical Processor ID: 0
[   10.346666] CPU: Processor Core ID: 0
[   10.346668] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   10.346676] Compat vDSO mapped to ffffe000.
[   10.346686] Checking 'hlt' instruction... OK.
[   10.362578] SMP alternatives: switching to UP code
[   10.362962] Early unpacking initramfs... done
[   10.692940] ACPI: Core revision 20070126
[   10.692996] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.835927] CPU0: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
[   10.835943] SMP alternatives: switching to SMP code
[   10.836022] Booting processor 1/1 eip 3000
[   10.846245] Initializing CPU#1
[   10.925613] Calibrating delay using timer specific routine.. 3324.92 BogoMIPS (lpj=6649858)
[   10.925619] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   10.925624] monitor/mwait feature present.
[   10.925627] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.925629] CPU: L2 cache: 2048K
[   10.925631] CPU: Physical Processor ID: 0
[   10.925633] CPU: Processor Core ID: 1
[   10.925635] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   10.926142] CPU1: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
[   10.926165] Total of 2 processors activated (6653.45 BogoMIPS).
[   10.926338] ENABLING IO-APIC IRQs
[   10.926540] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   11.073475] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   11.093461] Brought up 2 CPUs
[   11.233355] migration_cost=30
[   11.233479] Booting paravirtualized kernel on bare hardware
[   11.233567] Time: 14:00:54  Date: 02/21/108
[   11.233584] NET: Registered protocol family 16
[   11.233663] EISA bus registered
[   11.233667] ACPI: bus type pci registered
[   11.234034] PCI: PCI BIOS revision 3.00 entry at 0xfdba1, last bus=16
[   11.234036] PCI: Using configuration type 1
[   11.234038] Setting up standard PCI resources
[   11.236503] ACPI: EC: Look up EC in DSDT
[   11.237268] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   11.245257] ACPI: System BIOS is requesting _OSI(Linux)
[   11.245260] ACPI: Please test with "acpi_osi=!Linux"
[   11.245261] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
[   11.246105] ACPI: Interpreter enabled
[   11.246108] ACPI: (supports S0 S3 S4 S5)
[   11.246125] ACPI: Using IOAPIC for interrupt routing
[   11.653049] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   11.653099] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.653113] PCI: Probing PCI hardware (bus 00)
[   11.655372] PCI: Transparent bridge - 0000:00:1e.0
[   11.655514] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.655820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   11.655959] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   11.656096] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   11.656254] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   15.451195] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[   15.451308] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[   15.451418] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[   15.451527] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
[   15.451635] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 *11)
[   15.451744] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 *11)
[   15.451853] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11)
[   15.451961] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[   15.452091] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.452100] pnp: PnP ACPI init
[   15.452110] ACPI: bus type pnp registered
[   15.654391] pnp: PnP ACPI: found 11 devices
[   15.654393] ACPI: ACPI bus type pnp unregistered
[   15.654397] PnPBIOS: Disabled by ACPI PNP
[   15.654440] PCI: Using ACPI for IRQ routing
[   15.654443] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.789770] NET: Registered protocol family 8
[   15.789772] NET: Registered protocol family 20
[   15.789817] pnp: 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   15.789821] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   15.789824] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   15.789827] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   15.789836] pnp: 00:06: iomem range 0xfed00000-0xfed003ff could not be reserved
[   15.789842] pnp: 00:08: iomem range 0xff800000-0xff800fff could not be reserved
[   15.790130] Time: tsc clocksource has been installed.
[   15.790143] Switched to high resolution mode on CPU 0
[   15.790224] Switched to high resolution mode on CPU 1
[   15.820097] PCI: Bridge: 0000:00:1c.0
[   15.820100]   IO window: 2000-2fff
[   15.820107]   MEM window: f6000000-f7ffffff
[   15.820112]   PREFETCH window: f0000000-f1ffffff
[   15.820119] PCI: Bridge: 0000:00:1c.1
[   15.820122]   IO window: 3000-3fff
[   15.820129]   MEM window: f8000000-f9ffffff
[   15.820134]   PREFETCH window: f2000000-f3ffffff
[   15.820140] PCI: Bridge: 0000:00:1c.2
[   15.820144]   IO window: 4000-4fff
[   15.820151]   MEM window: fa000000-fbffffff
[   15.820156]   PREFETCH window: f4000000-f5ffffff
[   15.820164] PCI: Bus 16, cardbus bridge: 0000:0f:06.0
[   15.820166]   IO window: 00005000-000050ff
[   15.820172]   IO window: 00005400-000054ff
[   15.820178]   PREFETCH window: 50000000-53ffffff
[   15.820183]   MEM window: 58000000-5bffffff
[   15.820189] PCI: Bridge: 0000:00:1e.0
[   15.820192]   IO window: 5000-5fff
[   15.820199]   MEM window: fc200000-fc2fffff
[   15.820204]   PREFETCH window: 50000000-53ffffff
[   15.820236] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.820243] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.820270] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   15.820276] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.820303] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   15.820309] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.820324] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   15.820341] ACPI: PCI Interrupt 0000:0f:06.0[A] -> GSI 22 (level, low) -> IRQ 19
[   15.820355] NET: Registered protocol family 2
[   15.869736] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.869806] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   15.870507] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   15.870765] TCP: Hash tables configured (established 131072 bind 65536)
[   15.870768] TCP reno registered
[   15.885845] checking if image is initramfs... it is
[   16.537390] Freeing initrd memory: 7061k freed
[   16.537512] Simple Boot Flag at 0x36 set to 0x1
[   16.537964] audit: initializing netlink socket (disabled)
[   16.537981] audit(1206108058.764:1): initialized
[   16.538071] highmem bounce pool size: 64 pages
[   16.539865] VFS: Disk quotas dquot_6.5.1
[   16.539908] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.539991] io scheduler noop registered
[   16.539994] io scheduler anticipatory registered
[   16.539996] io scheduler deadline registered
[   16.540009] io scheduler cfq registered (default)
[   16.540027] Boot video device is 0000:00:02.0
[   16.540239] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.540302] assign_interrupt_mode Found MSI capability
[   16.540305] Allocate Port Service[0000:00:1c.0:pcie00]
[   16.540338] Allocate Port Service[0000:00:1c.0:pcie02]
[   16.540441] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   16.540504] assign_interrupt_mode Found MSI capability
[   16.540506] Allocate Port Service[0000:00:1c.1:pcie00]
[   16.540534] Allocate Port Service[0000:00:1c.1:pcie02]
[   16.540636] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   16.540699] assign_interrupt_mode Found MSI capability
[   16.540701] Allocate Port Service[0000:00:1c.2:pcie00]
[   16.540742] Allocate Port Service[0000:00:1c.2:pcie02]
[   16.540908] isapnp: Scanning for PnP cards...
[   16.894501] isapnp: No Plug & Play device found
[   16.914340] Real Time Clock Driver v1.12ac
[   16.914576] hpet_resources: 0xfed00000 is busy
[   16.914602] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.915648] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.915768] input: Macintosh mouse button emulation as /class/input/input0
[   16.915847] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.925666] i8042.c: Detected active multiplexing controller, rev 1.1.
[   16.932782] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.932786] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   16.932789] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   16.932791] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   16.932794] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   16.932897] mice: PS/2 mouse device common for all mice
[   16.933723] EISA: Probing bus 0 at eisa.0
[   16.933731] Cannot allocate resource for EISA slot 1
[   16.933734] Cannot allocate resource for EISA slot 2
[   16.933737] Cannot allocate resource for EISA slot 3
[   16.933739] Cannot allocate resource for EISA slot 4
[   16.933741] Cannot allocate resource for EISA slot 5
[   16.933757] EISA: Detected 0 cards.
[   16.933837] TCP cubic registered
[   16.933849] NET: Registered protocol family 1
[   16.933868] Using IPI No-Shortcut mode
[   16.934033]   Magic number: 0:6:31
[   16.934039]   hash matches device ttyde
[   16.934345] Freeing unused kernel memory: 364k freed
[   17.219699] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.135687] AppArmor: AppArmor initialized<5>audit(1206108060.264:2):  type=1505 info="AppArmor initialized" pid=1252
[   18.141463] fuse init (API version 7.8)
[   18.145762] Failure registering capabilities with primary security module.
[   18.182944] ACPI: SSDT 3F6D2455, 01F6 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   18.183190] ACPI: SSDT 3F6D1DB1, 061F (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   18.183777] Monitor-Mwait will be used to enter C-1 state
[   18.183781] Monitor-Mwait will be used to enter C-2 state
[   18.183783] Monitor-Mwait will be used to enter C-3 state
[   18.183788] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.184033] ACPI: SSDT 3F6D264B, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   18.184262] ACPI: SSDT 3F6D23D0, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   18.184882] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    7.664000] Marking TSC unstable due to: possible TSC halt in C2.
[    7.668000] Time: hpet clocksource has been installed.
[    7.672000] ACPI: Thermal Zone [TZS0] (32 C)
[    7.680000] ACPI: Thermal Zone [TZS1] (34 C)
[    8.172000] usbcore: registered new interface driver usbfs
[    8.172000] usbcore: registered new interface driver hub
[    8.172000] usbcore: registered new device driver usb
[    8.172000] USB Universal Host Controller Interface driver v3.0
[    8.172000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 20
[    8.172000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    8.172000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    8.172000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    8.172000] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001820
[    8.172000] usb usb1: configuration #1 chosen from 1 choice
[    8.172000] hub 1-0:1.0: USB hub found
[    8.172000] hub 1-0:1.0: 2 ports detected
[    8.184000] SCSI subsystem initialized
[    8.220000] libata version 2.21 loaded.
[    8.276000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[    8.276000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    8.276000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    8.276000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    8.276000] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    8.276000] usb usb2: configuration #1 chosen from 1 choice
[    8.276000] hub 2-0:1.0: USB hub found
[    8.276000] hub 2-0:1.0: 2 ports detected
[    8.380000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 22
[    8.380000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    8.380000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    8.380000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    8.380000] uhci_hcd 0000:00:1d.0: irq 22, io base 0x00001860
[    8.380000] usb usb3: configuration #1 chosen from 1 choice
[    8.380000] hub 3-0:1.0: USB hub found
[    8.380000] hub 3-0:1.0: 2 ports detected
[    8.484000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[    8.484000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    8.484000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    8.484000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    8.484000] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001880
[    8.484000] usb usb4: configuration #1 chosen from 1 choice
[    8.484000] hub 4-0:1.0: USB hub found
[    8.484000] hub 4-0:1.0: 2 ports detected
[    8.500000] Clocksource tsc unstable (delta = -187149226 ns)
[    8.588000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    8.588000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    8.588000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    8.588000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    8.588000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    8.588000] usb usb5: configuration #1 chosen from 1 choice
[    8.588000] hub 5-0:1.0: USB hub found
[    8.588000] hub 5-0:1.0: 2 ports detected
[    8.692000] tg3.c:v3.77 (May 31, 2007)
[    8.692000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    8.692000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    8.692000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 20 (level, low) -> IRQ 20
[    8.692000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    8.692000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    8.692000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    8.692000] ehci_hcd 0000:00:1a.7: debug port 1
[    8.692000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    8.692000] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfc504800
[    8.696000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    8.696000] usb usb6: configuration #1 chosen from 1 choice
[    8.696000] hub 6-0:1.0: USB hub found
[    8.696000] hub 6-0:1.0: 4 ports detected
[    8.712000] eth0: Tigon3 [partno(BCM95787m) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1d:72:19:f2:f6
[    8.712000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    8.712000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    8.800000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 22
[    8.800000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    8.800000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    8.800000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    8.800000] ehci_hcd 0000:00:1d.7: debug port 1
[    8.800000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    8.800000] ehci_hcd 0000:00:1d.7: irq 22, io mem 0xfc504c00
[    8.804000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    8.804000] usb usb7: configuration #1 chosen from 1 choice
[    8.804000] hub 7-0:1.0: USB hub found
[    8.804000] hub 7-0:1.0: 6 ports detected
[    8.908000] ahci 0000:00:1f.2: version 2.2
[    8.908000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 23
[    9.584000] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    9.760000] usb 4-1: configuration #1 chosen from 1 choice
[    9.772000] usbcore: registered new interface driver hiddev
[    9.784000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[    9.784000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
[    9.784000] usbcore: registered new interface driver usbhid
[    9.784000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    9.912000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    9.912000] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part 
[    9.912000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    9.912000] scsi0 : ahci
[    9.912000] scsi1 : ahci
[    9.912000] scsi2 : ahci
[    9.912000] ata1: SATA max UDMA/133 cmd 0xf8878100 ctl 0x00000000 bmdma 0x00000000 irq 23
[    9.912000] ata2: SATA max UDMA/133 cmd 0xf8878180 ctl 0x00000000 bmdma 0x00000000 irq 23
[    9.912000] ata3: SATA max UDMA/133 cmd 0xf8878200 ctl 0x00000000 bmdma 0x00000000 irq 23
[   10.400000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   10.788000] ata1.00: ATA-8: TOSHIBA MK1646GSX, LB113J, max UDMA/100
[   10.788000] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   10.788000] ata1.00: configured for UDMA/100
[   11.100000] ata2: SATA link down (SStatus 0 SControl 300)
[   11.416000] ata3: SATA link down (SStatus 0 SControl 300)
[   11.416000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1646GS LB11 PQ: 0 ANSI: 5
[   11.416000] ACPI: PCI Interrupt 0000:0f:06.1[A] -> GSI 22 (level, low) -> IRQ 19
[   11.468000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fc206000-fc2067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   11.468000] ata_piix 0000:00:1f.1: version 2.11
[   11.468000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 23
[   11.468000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   11.468000] scsi3 : ata_piix
[   11.468000] scsi4 : ata_piix
[   11.468000] ata4: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[   11.468000] ata5: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[   11.476000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   11.476000] sd 0:0:0:0: [sda] Write Protect is off
[   11.476000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.476000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.476000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   11.476000] sd 0:0:0:0: [sda] Write Protect is off
[   11.476000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.476000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.476000]  sda: sda1 sda2
[   11.548000] sd 0:0:0:0: [sda] Attached SCSI disk
[   11.552000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   11.808000] Attempting manual resume
[   11.808000] swsusp: Resume From Partition 8:1
[   11.808000] PM: Checking swsusp image.
[   11.808000] PM: Resume from disk failed.
[   11.840000] kjournald starting.  Commit interval 5 seconds
[   11.840000] EXT3-fs: mounted filesystem with ordered data mode.
[   12.740000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001d72ffff19f2f6]
[   18.088000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.104000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.228000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.324000] agpgart: Detected an Intel 965GM Chipset.
[   18.328000] agpgart: Detected 7676K stolen memory.
[   18.348000] agpgart: AGP aperture is 256M @ 0xd0000000
[   18.736000] ieee80211_crypt: registered algorithm 'NULL'
[   18.740000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.740000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.780000] Yenta: CardBus bridge found at 0000:0f:06.0 [1025:011f]
[   18.780000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   18.780000] Yenta: Routing CardBus interrupts to PCI
[   18.780000] Yenta TI: socket 0000:0f:06.0, mfunc 0x01aa1b22, devctl 0x64
[   18.784000] sdhci: Secure Digital Host Controller Interface driver
[   18.784000] sdhci: Copyright(c) Pierre Ossman
[   18.804000] irda_init()
[   18.804000] NET: Registered protocol family 23
[   18.824000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   18.824000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   19.020000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 19
[   19.020000] Socket status: 30000006
[   19.020000] Yenta: Raising subordinate bus# of parent bus (#0f) from #10 to #13
[   19.020000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   19.020000] cs: IO port probe 0x5000-0x5fff: clean.
[   19.020000] pcmcia: parent PCI bridge Memory window: 0xfc200000 - 0xfc2fffff
[   19.020000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   19.024000] sdhci: SDHCI controller found at 0000:0f:06.3 [104c:803c] (rev 0)
[   19.024000] ACPI: PCI Interrupt 0000:0f:06.3[A] -> GSI 22 (level, low) -> IRQ 19
[   19.024000] mmc0: SDHCI at 0xfc206800 irq 19 PIO
[   19.028000] ACPI: PCI Interrupt 0000:0f:06.2[A] -> GSI 22 (level, low) -> IRQ 19
[   19.028000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   19.028000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   19.028000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   19.028000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.028000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.052000] tifm_core: MMC/SD card detected in socket 0:1
[   19.084000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x12a0b1, caps: 0xa04713/0x204000
[   19.136000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   19.264000] pnp: Device 00:0a activated.
[   19.264000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   19.264000] nsc-ircc, chip->init
[   19.264000] nsc-ircc, Found chip at base=0x02e
[   19.264000] nsc-ircc, driver loaded (Dag Brattli)
[   19.264000] IrDA: Registered device irda0
[   19.264000] nsc-ircc, Found dongle: Supports SIR Mode only
[   19.264000] nsc-ircc, chip->init
[   19.264000] nsc-ircc, Found chip at base=0x02e
[   19.264000] nsc-ircc, driver loaded (Dag Brattli)
[   19.264000] nsc_ircc_open(), can't get iobase of 0x2f8
[   19.332000] cs: IO port probe 0x100-0x3af: clean.
[   19.336000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.336000] cs: IO port probe 0x820-0x8ff: clean.
[   19.336000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.340000] cs: IO port probe 0xa00-0xaff: clean.
[   20.016000] lp: driver loaded but no devices found
[   20.084000] Adding 1172704k swap on /dev/sda1.  Priority:-1 extents:1 across:1172704k
[   20.396000] EXT3 FS on sda2, internal journal
[   20.944000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   21.668000] No dock devices found.
[   22.028000] ACPI: Battery Slot [BAT0] (battery present)
[   22.052000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   22.112000] input: Power Button (FF) as /class/input/input4
[   22.112000] ACPI: Power Button (FF) [PWRF]
[   22.112000] input: Lid Switch as /class/input/input5
[   22.112000] ACPI: Lid Switch [LID0]
[   22.112000] input: Sleep Button (CM) as /class/input/input6
[   22.112000] ACPI: Sleep Button (CM) [SLPB]
[   22.172000] ACPI: AC Adapter [ADP1] (on-line)
[   23.388000] ppdev: user-space parallel port driver
[   23.664000] audit(1206108076.381:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5079 profile="/usr/sbin/cupsd"
[   23.716000] apm: BIOS not found.
[   24.016000] Failure registering capabilities with primary security module.
[   24.208000] Bluetooth: Core ver 2.11
[   24.208000] NET: Registered protocol family 31
[   24.208000] Bluetooth: HCI device and connection manager initialized
[   24.208000] Bluetooth: HCI socket layer initialized
[   24.244000] Bluetooth: L2CAP ver 2.8
[   24.244000] Bluetooth: L2CAP socket layer initialized
[   24.316000] Bluetooth: RFCOMM socket layer initialized
[   24.316000] Bluetooth: RFCOMM TTY layer initialized
[   24.316000] Bluetooth: RFCOMM ver 1.8
[   29.520000] [drm] Initialized drm 1.1.0 20060810
[   29.576000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.576000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   60.392000] NET: Registered protocol family 17
[   64.576000] ieee80211_crypt: registered algorithm 'TKIP'
[   71.164000] NET: Registered protocol family 10
[   71.164000] lo: Disabled Privacy Extensions
[   71.164000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   82.128000] eth1: no IPv6 routers present
[ 1626.656000] usb 4-1: USB disconnect, address 2
[ 1652.640000] usb 4-2: new low speed USB device using uhci_hcd and address 3
[ 1652.812000] usb 4-2: configuration #1 chosen from 1 choice
[ 1652.828000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input7
[ 1652.828000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2
[ 1783.284000] usb 7-5: new high speed USB device using ehci_hcd and address 4
[ 1783.416000] usb 7-5: configuration #1 chosen from 1 choice
[ 1783.588000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5711
[ 1783.588000] usbcore: registered new interface driver usblp
[ 1783.588000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[ 1783.600000] usbcore: registered new interface driver libusual
[ 1783.708000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 1783.708000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 1783.716000] Initializing USB Mass Storage driver...
[ 1783.716000] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1783.716000] usb-storage: device found at 4
[ 1783.716000] usb-storage: waiting for device to settle before scanning
[ 1783.716000] usbcore: registered new interface driver usb-storage
[ 1783.716000] USB Mass Storage support registered.
[ 1788.716000] usb-storage: device scan complete
[ 1788.716000] scsi 5:0:0:0: Direct-Access     HP       Photosmart C4180 1.00 PQ: 0 ANSI: 2
[ 1788.716000] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 1788.716000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[ 1942.876000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: removed
[ 1942.920000] audit(1206109996.062:4):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=12960 profile="/usr/sbin/cupsd"
[ 1942.968000] audit(1206109996.062:5):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=12965 profile="/usr/sbin/cupsd"
[ 2147.240000] audit(1206110200.074:6):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=13148 profile="/usr/sbin/cupsd"
[ 2147.260000] audit(1206110200.074:7):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=13151 profile="/usr/sbin/cupsd"
[ 2211.684000] usb 7-5: USB disconnect, address 4
jesper@Jesper-laptop:~/Desktop/kernelcheck-1.0.5$ 




---

### Post by dannyboy79 on 2008-03-21
nope, I don't see anything about a CDROM drive?? look thru your /dev/ directory and see if anything is linked to anything else.

use this command

ls -la /dev/ | grep ">"

---

### Post by aktiwers on 2008-03-21
> **dannyboy79 said:**
> nope, I don't see anything about a CDROM drive?? look thru your /dev/ directory and see if anything is linked to anything else.

use this command

ls -la /dev/ | grep ">"

hmm I dont see anyting in /dev/ ??

> jesper@Jesper-laptop:~/Desktop/kernelcheck-1.0.5$ ls -la /dev/ | grep ">"
lrwxrwxrwx  1 root   root          11 2008-03-21 15:01 core -> /proc/kcore
lrwxrwxrwx  1 root   root          13 2008-03-21 15:01 fd -> /proc/self/fd
lrwxrwxrwx  1 root   root          13 2008-03-21 15:01 MAKEDEV -> /sbin/MAKEDEV
lrwxrwxrwx  1 root   root          24 2008-03-21 15:01 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx  1 root   root          15 2008-03-21 15:01 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root   root          15 2008-03-21 15:01 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root   root          15 2008-03-21 15:01 stdout -> /proc/self/fd/1
jesper@Jesper-laptop:~/Desktop/kernelcheck-1.0.5$ 


hmm does this tell you anything?

---

### Post by OffAxis on 2008-03-21
can you boot (consistently) from a liveCD?
This'll cut out the software/ mounting part of it and let you know if it's a hardware problem.

---

### Post by jan quark on 2008-03-21
can you please post also the result of
```

sudo lshw -C disk
```

---

### Post by aktiwers on 2008-03-21
I sadly dont have a livecd here but when I put a DVD in the drive it seams like it start running and then stops...

Im still thinking about the cdrom polling thing?

Heres the output of that command:
> jesper@Jesper-laptop:~$ sudo lshw -C disk
[sudo] password for jesper:
  *-disk                  
       description: SCSI Disk
       product: TOSHIBA MK1646GS
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: LB11
       serial: Z7OSF52NS
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
jesper@Jesper-laptop:~$ 


---

### Post by aktiwers on 2008-03-21
Okay I just got done installing the latest with KernelCheck and it also updated my current kernel patch. and Now its Working!  

Thanks a lot for the help guys!

---

### Post by dannyboy79 on 2008-03-21
glad it's fixed to bad we don't know what the problem was? can you mark the thread "Solved"

---

### Post by aktiwers on 2008-03-23
I really think it has something to do with me disableling cdrom drive pulling in HAL and couldnt get it enabled again..

But yeah I dont know what the problem was, but a new Kernel patch did the trick.

urgh! How do i mark it as solved? :D

---

