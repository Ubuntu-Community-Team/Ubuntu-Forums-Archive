---
title: "Ubuntu shows only 1 core for Mac mini 3.1"
date: 2010-03-31
forum: Apple Hardware Users
---

### Post by Legolas17 on 2010-03-31
I noticed that ubuntu only detects 1 core on a mini 3.1 dual core. Has anyone the sam issue? Or has someone an idear an what's happening. Already tried 32 bit and 64bit.

---

### Post by linuxopjemac on 2010-03-31
It's likely that you've accidentally installed the -386 flavour of the kernel. This flavour doesn't have SMP enabled, so no dual core.

Make sure you have the 'linux-generic' package installed - this will ensure that you've got the most recent -generic kernel + associated drivers/firmware installed - and then remove the linux-image-some.numbers-here-386 package.

Also ensure you have ACPI features enabled.
maybe with this code in grub:
acpi=noirq and pnpacpi=off.

---

### Post by realzippy on 2010-03-31
type in terminal:

```
cat /proc/cpuinfo
```

to be sure.linux counts from "0"....


ACPI should have no effect on detected CPUs....

---

### Post by Legolas17 on 2010-03-31
chris@chris-desktop:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     P7550  @ 2.26GHz
stepping    : 10
cpu MHz        : 1596.000
cache size    : 3072 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 4509.93
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

chris@chris-desktop:~$ uname -r
2.6.31-14-generic


hmm still no 2 cores

---

### Post by linuxopjemac on 2010-03-31
do you boot with acpi=off ?

---

### Post by Legolas17 on 2010-03-31
have no idear how to know that acpi = off?

linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=aa16806c-c858-45a2-8787-9bdd4a401bcb ro   quiet splash acpi=noirq pnpacpi=off

---

### Post by linuxopjemac on 2010-03-31
this should be fine I think....

---

### Post by linuxopjemac on 2010-03-31
man, you are using an old kernel!! I would upgrade your kernel a.s.a.p. and report the  results...

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by realzippy on 2010-03-31
EdiT:
deleted,we know your kernel yet...

---

### Post by linuxopjemac on 2010-03-31
after you did that and rebooted, give us a dmesg
```
sudo dmesg
```

and post it here

---

### Post by linuxopjemac on 2010-03-31
If that does not solve your problem, you might want to digg your way into grub-efi booting. It might give you dual core...no guarantees though...

[http://mac.linux.be/content/karmic-koala-macbook-52-0](http://mac.linux.be/content/karmic-koala-macbook-52-0)

general
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

---

### Post by Legolas17 on 2010-03-31
```

```[    5.062713] Brought up 1 CPUs
[    5.062716] Total of 1 processors activated (4510.63 BogoMIPS).
[    5.062725] CPU0 attaching NULL sched-domain.
[    5.062934] Booting paravirtualized kernel on bare hardware
[    5.063085] regulator: core version 0.5
[    5.063161] Time: 14:29:20  Date: 03/31/10
[    5.063207] NET: Registered protocol family 16
[    5.063319] ACPI: bus type pci registered
[    5.063570] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 255
[    5.063573] PCI: MCFG area at f0000000 reserved in E820
[    5.063575] PCI: updated MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    5.064903] PCI: Using MMCONFIG at f0000000 - f3ffffff
[    5.064905] PCI: Using configuration type 1 for base access
[    5.065646] bio: create slab <bio-0> at 0
[    5.066623] ACPI: EC: EC description table is found, configuring boot EC
[    5.066786] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    5.081886] ACPI: BIOS _OSI(Linux) query ignored
[    5.082410] ACPI: Interpreter enabled
[    5.082413] ACPI: (supports S0 S3 S4 S5)
[    5.082434] ACPI: Using PIC for interrupt routing
[    5.091602] ACPI: EC: GPE = 0x3f, I/O: command/status = 0x66, data = 0x62
[    5.091604] ACPI: EC: driver started in interrupt mode
[    5.091920] ACPI: No dock devices found.
[    5.092185] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    5.092510] pci 0000:00:03.0: reg 10 io port: [0x2000-0x20ff]
[    5.092657] pci 0000:00:03.2: reg 10 io port: [0x2180-0x21bf]
[    5.092676] pci 0000:00:03.2: reg 20 io port: [0x2140-0x217f]
[    5.092682] pci 0000:00:03.2: reg 24 io port: [0x2100-0x213f]
[    5.092714] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    5.092721] pci 0000:00:03.2: PME# disabled
[    5.092964] pci 0000:00:03.5: reg 10 32bit mmio: [0x93400000-0x9347ffff]
[    5.093102] pci 0000:00:04.0: reg 10 32bit mmio: [0x93488000-0x93488fff]
[    5.093146] pci 0000:00:04.0: supports D1 D2
[    5.093148] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    5.093153] pci 0000:00:04.0: PME# disabled
[    5.093194] pci 0000:00:04.1: reg 10 32bit mmio: [0x93489200-0x934892ff]
[    5.093248] pci 0000:00:04.1: supports D1 D2
[    5.093250] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    5.093253] pci 0000:00:04.1: PME# disabled
[    5.093301] pci 0000:00:06.0: reg 10 32bit mmio: [0x93487000-0x93487fff]
[    5.093346] pci 0000:00:06.0: supports D1 D2
[    5.093348] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    5.093352] pci 0000:00:06.0: PME# disabled
[    5.093394] pci 0000:00:06.1: reg 10 32bit mmio: [0x93489100-0x934891ff]
[    5.093446] pci 0000:00:06.1: supports D1 D2
[    5.093448] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    5.093453] pci 0000:00:06.1: PME# disabled
[    5.093501] pci 0000:00:08.0: reg 10 32bit mmio: [0x93480000-0x93483fff]
[    5.093546] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    5.093549] pci 0000:00:08.0: PME# disabled
[    5.093634] pci 0000:00:0a.0: reg 10 32bit mmio: [0x93486000-0x93486fff]
[    5.093639] pci 0000:00:0a.0: reg 14 io port: [0x21e0-0x21e7]
[    5.093645] pci 0000:00:0a.0: reg 18 32bit mmio: [0x93489000-0x934890ff]
[    5.093650] pci 0000:00:0a.0: reg 1c 32bit mmio: [0x93489300-0x9348930f]
[    5.093686] pci 0000:00:0a.0: supports D1 D2
[    5.093687] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    5.093693] pci 0000:00:0a.0: PME# disabled
[    5.093734] pci 0000:00:0b.0: reg 10 io port: [0x21d8-0x21df]
[    5.093738] pci 0000:00:0b.0: reg 14 io port: [0x21ec-0x21ef]
[    5.093743] pci 0000:00:0b.0: reg 18 io port: [0x21d0-0x21d7]
[    5.093749] pci 0000:00:0b.0: reg 1c io port: [0x21e8-0x21eb]
[    5.093754] pci 0000:00:0b.0: reg 20 io port: [0x21c0-0x21cf]
[    5.093760] pci 0000:00:0b.0: reg 24 32bit mmio: [0x93484000-0x93485fff]
[    5.093855] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    5.093858] pci 0000:00:10.0: PME# disabled
[    5.094130] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    5.094139] pci 0000:00:15.0: PME# disabled
[    5.094442] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    5.094450] pci 0000:00:16.0: PME# disabled
[    5.094577] pci 0000:00:09.0: transparent bridge
[    5.094582] pci 0000:00:09.0: bridge 32bit mmio: [0x93300000-0x933fffff]
[    5.094631] pci 0000:02:00.0: reg 10 32bit mmio: [0x92000000-0x92ffffff]
[    5.094643] pci 0000:02:00.0: reg 14 64bit mmio: [0x80000000-0x8fffffff]
[    5.094655] pci 0000:02:00.0: reg 1c 64bit mmio: [0x90000000-0x91ffffff]
[    5.094662] pci 0000:02:00.0: reg 24 io port: [0x1000-0x107f]
[    5.094669] pci 0000:02:00.0: reg 30 32bit mmio: [0x93000000-0x9301ffff]
[    5.094751] pci 0000:00:10.0: bridge io port: [0x1000-0x1fff]
[    5.094754] pci 0000:00:10.0: bridge 32bit mmio: [0x92000000-0x930fffff]
[    5.094759] pci 0000:00:10.0: bridge 64bit mmio pref: [0x80000000-0x91ffffff]
[    5.095031] pci 0000:03:00.0: reg 10 64bit mmio: [0x93200000-0x93203fff]
[    5.095115] pci 0000:03:00.0: supports D1 D2
[    5.095116] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    5.095122] pci 0000:03:00.0: PME# disabled
[    5.095235] pci 0000:00:15.0: bridge 32bit mmio: [0x93200000-0x932fffff]
[    5.095328] pci 0000:04:00.0: reg 10 64bit mmio: [0x93100000-0x93100fff]
[    5.095408] pci 0000:04:00.0: supports D1 D2
[    5.095410] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    5.095415] pci 0000:04:00.0: PME# disabled
[    5.095522] pci 0000:00:16.0: bridge 32bit mmio: [0x93100000-0x931fffff]
[    5.095586] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    5.095897] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    5.151130] SCSI subsystem initialized
[    5.151166] libata version 3.00 loaded.
[    5.151220] usbcore: registered new interface driver usbfs
[    5.151230] usbcore: registered new interface driver hub
[    5.151252] usbcore: registered new device driver usb
[    5.151359] ACPI: WMI: Mapper loaded
[    5.151361] PCI: Probing PCI hardware
[    5.151849] PCI: Discovered primary peer bus ff [IRQ]
[    5.151855] pci 0000:00:03.1: default IRQ router [10de:0aa4]
[    5.152683] Bluetooth: Core ver 2.15
[    5.152705] NET: Registered protocol family 31
[    5.152707] Bluetooth: HCI device and connection manager initialized
[    5.152710] Bluetooth: HCI socket layer initialized
[    5.152712] NetLabel: Initializing
[    5.152713] NetLabel:  domain hash size = 128
[    5.152714] NetLabel:  protocols = UNLABELED CIPSOv4
[    5.152726] NetLabel:  unlabeled traffic allowed by default
[    5.152769] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    5.152773] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    5.161450] pnp: PnP ACPI init
[    5.161459] ACPI: bus type pnp registered
[    5.164438] pnp: PnP ACPI: found 8 devices
[    5.164440] ACPI: ACPI bus type pnp unregistered
[    5.164449] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    5.164455] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    5.164461] system 00:06: ioport range 0x400-0x47f has been reserved
[    5.164463] system 00:06: ioport range 0x480-0x4ff has been reserved
[    5.164466] system 00:06: ioport range 0x500-0x57f has been reserved
[    5.164468] system 00:06: ioport range 0x580-0x5ff has been reserved
[    5.164470] system 00:06: ioport range 0x800-0x87f has been reserved
[    5.164476] system 00:06: ioport range 0x880-0x8ff has been reserved
[    5.164479] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    5.164481] system 00:06: ioport range 0x295-0x296 has been reserved
[    5.169258] AppArmor: AppArmor Filesystem Enabled
[    5.169335] pci 0000:00:09.0: PCI bridge, secondary bus 0000:01
[    5.169336] pci 0000:00:09.0:   IO window: disabled
[    5.169342] pci 0000:00:09.0:   MEM window: 0x93300000-0x933fffff
[    5.169345] pci 0000:00:09.0:   PREFETCH window: disabled
[    5.169350] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
[    5.169352] pci 0000:00:10.0:   IO window: 0x1000-0x1fff
[    5.169357] pci 0000:00:10.0:   MEM window: 0x92000000-0x930fffff
[    5.169360] pci 0000:00:10.0:   PREFETCH window: 0x00000080000000-0x00000091ffffff
[    5.169365] pci 0000:00:15.0: PCI bridge, secondary bus 0000:03
[    5.169366] pci 0000:00:15.0:   IO window: disabled
[    5.169380] pci 0000:00:15.0:   MEM window: 0x93200000-0x932fffff
[    5.169388] pci 0000:00:15.0:   PREFETCH window: disabled
[    5.169397] pci 0000:00:16.0: PCI bridge, secondary bus 0000:04
[    5.169399] pci 0000:00:16.0:   IO window: disabled
[    5.169412] pci 0000:00:16.0:   MEM window: 0x93100000-0x931fffff
[    5.169421] pci 0000:00:16.0:   PREFETCH window: disabled
[    5.169431] pci 0000:00:09.0: enabling device (0000 -> 0002)
[    5.169440] pci 0000:00:09.0: setting latency timer to 64
[    5.169448] pci 0000:00:10.0: setting latency timer to 64
[    5.169473] pci 0000:00:15.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[    5.169482] pci 0000:00:15.0: setting latency timer to 64
[    5.169510] pci 0000:00:16.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[    5.169519] pci 0000:00:16.0: setting latency timer to 64
[    5.169525] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    5.169527] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    5.169529] pci_bus 0000:01: resource 1 mem: [0x93300000-0x933fffff]
[    5.169531] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    5.169533] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    5.169535] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    5.169538] pci_bus 0000:02: resource 1 mem: [0x92000000-0x930fffff]
[    5.169540] pci_bus 0000:02: resource 2 pref mem [0x80000000-0x91ffffff]
[    5.169542] pci_bus 0000:03: resource 1 mem: [0x93200000-0x932fffff]
[    5.169544] pci_bus 0000:04: resource 1 mem: [0x93100000-0x931fffff]
[    5.169546] pci_bus 0000:ff: resource 0 io:  [0x00-0xffff]
[    5.169548] pci_bus 0000:ff: resource 1 mem: [0x000000-0xffffffffffffffff]
[    5.169576] NET: Registered protocol family 2
[    5.169690] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    5.170011] Switched to high resolution mode on CPU 0
[    5.170398] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    5.172275] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    5.172776] TCP: Hash tables configured (established 262144 bind 65536)
[    5.172779] TCP reno registered
[    5.172893] NET: Registered protocol family 1
[    5.172959] Trying to unpack rootfs image as initramfs...
[    5.337930] Freeing initrd memory: 7691k freed
[    5.341735] Scanning for low memory corruption every 60 seconds
[    5.341875] audit: initializing netlink socket (disabled)
[    5.341893] type=2000 audit(1270045760.340:1): initialized
[    5.350426] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    5.351661] VFS: Disk quotas dquot_6.5.2
[    5.351708] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    5.352197] fuse init (API version 7.12)
[    5.352274] msgmni has been set to 3459
[    5.352446] alg: No test for stdrng (krng)
[    5.352456] io scheduler noop registered
[    5.352458] io scheduler anticipatory registered
[    5.352460] io scheduler deadline registered
[    5.352497] io scheduler cfq registered (default)
[    5.370203] pci 0000:02:00.0: Boot video device
[    5.370350] pcieport-driver 0000:00:15.0: device [10de:0ac6] has invalid IRQ; check vendor BIOS
[    5.370596]   alloc irq_desc for 16 on node 0
[    5.370597]   alloc kstat_irqs on node 0
[    5.370624] pcieport-driver 0000:00:15.0: irq 16 for MSI/MSI-X
[    5.370649] pcieport-driver 0000:00:15.0: setting latency timer to 64
[    5.370905] pcieport-driver 0000:00:16.0: device [10de:0ac7] has invalid IRQ; check vendor BIOS
[    5.371148]   alloc irq_desc for 17 on node 0
[    5.371149]   alloc kstat_irqs on node 0
[    5.371171] pcieport-driver 0000:00:16.0: irq 17 for MSI/MSI-X
[    5.371196] pcieport-driver 0000:00:16.0: setting latency timer to 64
[    5.371410] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    5.371430] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    5.371549] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    5.371552] ACPI: Power Button [PWRF]
[    5.371607] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    5.371609] ACPI: Power Button [PWRB]
[    5.371646] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    5.371648] ACPI: Sleep Button [SLPB]
[    5.372442] ACPI: SSDT 000000007fec9c98 00238 (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
[    5.372818] ACPI: SSDT 000000007fec8c18 002AD (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
[    5.373179] Monitor-Mwait will be used to enter C-1 state
[    5.373197] Monitor-Mwait will be used to enter C-2 state
[    5.373214] Monitor-Mwait will be used to enter C-3 state
[    5.373220] Marking TSC unstable due to TSC halts in idle
[    5.373240] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    5.373260] processor LNXCPU:00: registered as cooling_device0
[    5.373263] ACPI: Processor [CPU0] (supports 8 throttling states)
[    5.377769] Linux agpgart interface v0.103
[    5.377777] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    5.378781] brd: module loaded
[    5.379166] loop: module loaded
[    5.379222] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    5.379343] ahci 0000:00:0b.0: version 3.0
[    5.379389]   alloc irq_desc for 18 on node 0
[    5.379391]   alloc kstat_irqs on node 0
[    5.379400] ahci 0000:00:0b.0: irq 18 for MSI/MSI-X
[    5.379459] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3 impl IDE mode
[    5.379462] ahci 0000:00:0b.0: flags: 64bit ncq sntf pm led pmp pio slum part 
[    5.379466] ahci 0000:00:0b.0: setting latency timer to 64
[    5.379607] scsi0 : ahci
[    5.379676] scsi1 : ahci
[    5.379722] scsi2 : ahci
[    5.379765] scsi3 : ahci
[    5.379806] scsi4 : ahci
[    5.379849] scsi5 : ahci
[    5.379962] ata1: SATA max UDMA/133 abar m8192@0x93484000 port 0x93484100 irq 18
[    5.379965] ata2: SATA max UDMA/133 abar m8192@0x93484000 port 0x93484180 irq 18
[    5.379967] ata3: DUMMY
[    5.379968] ata4: DUMMY
[    5.379969] ata5: DUMMY
[    5.379970] ata6: DUMMY
[    5.380700] Fixed MDIO Bus: probed
[    5.380728] PPP generic driver version 2.4.2
[    5.380806] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.380975] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    5.380978] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    5.381004] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    5.381030] ehci_hcd 0000:00:04.1: debug port 1
[    5.381035] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    5.381042] ehci_hcd 0000:00:04.1: irq 10, io mem 0x93489200
[    5.400022] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    5.400103] usb usb1: configuration #1 chosen from 1 choice
[    5.400127] hub 1-0:1.0: USB hub found
[    5.400133] hub 1-0:1.0: 7 ports detected
[    5.400214] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    5.400217] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    5.400245] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    5.400272] ehci_hcd 0000:00:06.1: debug port 1
[    5.400278] ehci_hcd 0000:00:06.1: cache line size of 32 is not supported
[    5.400284] ehci_hcd 0000:00:06.1: irq 5, io mem 0x93489100
[    5.420020] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    5.420083] usb usb2: configuration #1 chosen from 1 choice
[    5.420107] hub 2-0:1.0: USB hub found
[    5.420112] hub 2-0:1.0: 5 ports detected
[    5.420166] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.420204] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    5.420207] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    5.420234] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    5.420245] ohci_hcd 0000:00:04.0: irq 11, io mem 0x93488000
[    5.482064] usb usb3: configuration #1 chosen from 1 choice
[    5.482087] hub 3-0:1.0: USB hub found
[    5.482094] hub 3-0:1.0: 7 ports detected
[    5.482159] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    5.482162] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    5.482188] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    5.482199] ohci_hcd 0000:00:06.0: irq 7, io mem 0x93487000
[    5.542062] usb usb4: configuration #1 chosen from 1 choice
[    5.542086] hub 4-0:1.0: USB hub found
[    5.542094] hub 4-0:1.0: 5 ports detected
[    5.542137] uhci_hcd: USB Universal Host Controller Interface driver
[    5.542218] PNP: No PS/2 controller found. Probing ports directly.
[    5.543079] i8042.c: No controller found.
[    5.543120] mice: PS/2 mouse device common for all mice
[    5.543211] rtc_cmos 00:07: RTC can wake from S4
[    5.543240] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    5.543281] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    5.543377] device-mapper: uevent: version 1.0.3
[    5.543441] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    5.543480] device-mapper: multipath: version 1.1.0 loaded
[    5.543483] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.543611] cpuidle: using governor ladder
[    5.543659] cpuidle: using governor menu
[    5.543997] TCP cubic registered
[    5.544103] NET: Registered protocol family 10
[    5.544472] lo: Disabled Privacy Extensions
[    5.544725] NET: Registered protocol family 17
[    5.544740] Bluetooth: L2CAP ver 2.13
[    5.544742] Bluetooth: L2CAP socket layer initialized
[    5.544745] Bluetooth: SCO (Voice Link) ver 0.6
[    5.544747] Bluetooth: SCO socket layer initialized
[    5.544770] Bluetooth: RFCOMM TTY layer initialized
[    5.544773] Bluetooth: RFCOMM socket layer initialized
[    5.544774] Bluetooth: RFCOMM ver 1.11
[    5.545206] PM: Resume from disk failed.
[    5.545217] registered taskstats version 1
[    5.545312]   Magic number: 2:721:486
[    5.545422] rtc_cmos 00:07: setting system clock to 2010-03-31 14:29:21 UTC (1270045761)
[    5.545425] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.545426] EDD information not available.
[    5.910036] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.910047] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.910393] ata1.00: ATA-8: FUJITSU MHZ2160BH G1, 00810009, max UDMA/100
[    5.910396] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.910869] ata1.00: configured for UDMA/100
[    5.915721] ata2.00: ATAPI: OPTIARC DVD RW AD-5670S, 2AHI, max UDMA/100, ATAPI AN
[    5.921222] ata2.00: configured for UDMA/100
[    5.930112] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2160B 0081 PQ: 0 ANSI: 5
[    5.930208] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.930240] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    5.930278] sd 0:0:0:0: [sda] Write Protect is off
[    5.930281] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.930305] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.930410]  sda:
[    5.945664] scsi 1:0:0:0: CD-ROM            OPTIARC  DVD RW AD-5670S  2AHI PQ: 0 ANSI: 5
[    5.967839] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[    5.967842] Uniform CD-ROM driver Revision: 3.20
[    5.967903] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.967934] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    6.000044] usb 3-5: new low speed USB device using ohci_hcd and address 2
[    6.047417]  sda1 sda2 sda3 sda4 sda5 sda6
[    6.047682] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.047699] Freeing unused kernel memory: 664k freed
[    6.047908] Write protecting the kernel read-only data: 7596k
[    6.242096] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    6.242118] forcedeth 0000:00:0a.0: setting latency timer to 64
[    6.256134] usb 3-5: configuration #1 chosen from 1 choice
[    6.290596] ohci1394 0000:04:00.0: setting latency timer to 64
[    6.293701] usbcore: registered new interface driver hiddev
[    6.293746] usbcore: registered new interface driver usbhid
[    6.293748] usbhid: v2.6:USB HID core driver
[    6.313117] apple 0003:05AC:8242.0001: hiddev96,hidraw0: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:04.0-5/input0
[    6.321314] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr d4:9a:20:bc:e4:42
[    6.321318] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    6.352074] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[7]  MMIO=[93100000-931007ff]  Max Packet=[4096]  IR/IT contexts=[8/8]
[    6.520035] usb 2-4: new high speed USB device using ehci_hcd and address 3
[    6.679140] usb 2-4: configuration #1 chosen from 1 choice
[    6.679998] hub 2-4:1.0: USB hub found
[    6.680064] hub 2-4:1.0: 3 ports detected
[    7.070013] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    7.410059] usb 4-1: configuration #1 chosen from 1 choice
[    7.420041] hub 4-1:1.0: USB hub found
[    7.430010] hub 4-1:1.0: 3 ports detected
[    7.602037] usb 2-4.2: new low speed USB device using ehci_hcd and address 4
[    7.700096] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[d49a20fffebce442]
[    7.820056] usb 2-4.2: configuration #1 chosen from 1 choice
[    7.830282] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:06.1/usb2/2-4/2-4.2/2-4.2:1.0/input/input4
[    7.830335] apple 0003:05AC:0221.0002: input,hidraw1: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:06.1-4.2/input0
[    7.850058] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:06.1/usb2/2-4/2-4.2/2-4.2:1.1/input/input5
[    7.850104] apple 0003:05AC:0221.0003: input,hidraw2: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:06.1-4.2/input1
[    7.980010] usb 2-4.3: new low speed USB device using ehci_hcd and address 5
[    8.166122] usb 2-4.3: configuration #1 chosen from 1 choice
[    8.169417] input: Mitsumi Electric Apple Optical USB Mouse as /devices/pci0000:00/0000:00:06.1/usb2/2-4/2-4.3/2-4.3:1.0/input/input6
[    8.169475] apple 0003:05AC:0304.0004: input,hidraw3: USB HID v1.10 Mouse [Mitsumi Electric Apple Optical USB Mouse] on usb-0000:00:06.1-4.3/input0
[    8.252047] usb 4-1.1: new full speed USB device using ohci_hcd and address 3
[    8.429115] usb 4-1.1: configuration #1 chosen from 1 choice
[    8.449893] PM: Starting manual resume from disk
[    8.449896] PM: Resume from partition 8:6
[    8.449897] PM: Checking hibernation image.
[    8.450124] PM: Resume from disk failed.
[    8.471301] EXT4-fs (sda5): barriers enabled
[    8.495281] kjournald2 starting: pid 444, dev sda5:8, commit interval 5 seconds
[    8.495304] EXT4-fs (sda5): delayed allocation enabled
[    8.495307] EXT4-fs: file extents enabled
[    8.499994] EXT4-fs: mballoc enabled
[    8.501980] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    8.512547] usb 4-1.2: new full speed USB device using ohci_hcd and address 4
[    8.637123] usb 4-1.2: configuration #1 chosen from 1 choice
[    8.646276] input: HID 05ac:820a as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1.2/4-1.2:1.0/input/input7
[    8.646332] generic-usb 0003:05AC:820A.0005: input,hidraw4: USB HID v1.11 Keyboard [HID 05ac:820a] on usb-0000:00:06.0-1.2/input0
[    8.732049] usb 4-1.3: new full speed USB device using ohci_hcd and address 5
[    8.857112] usb 4-1.3: configuration #1 chosen from 1 choice
[    8.866251] input: HID 05ac:820b as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1.3/4-1.3:1.0/input/input8
[    8.866316] generic-usb 0003:05AC:820B.0006: input,hidraw5: USB HID v1.11 Mouse [HID 05ac:820b] on usb-0000:00:06.0-1.3/input0
[    9.156068] type=1505 audit(1270045765.104:2): operation="profile_load" pid=476 name=/usr/share/gdm/guest-session/Xsession
[    9.158000] type=1505 audit(1270045765.104:3): operation="profile_load" pid=477 name=/sbin/dhclient3
[    9.158625] type=1505 audit(1270045765.104:4): operation="profile_load" pid=477 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.158967] type=1505 audit(1270045765.104:5): operation="profile_load" pid=477 name=/usr/lib/connman/scripts/dhclient-script
[    9.217692] type=1505 audit(1270045765.164:6): operation="profile_load" pid=478 name=/usr/bin/evince
[    9.227823] type=1505 audit(1270045765.174:7): operation="profile_load" pid=478 name=/usr/bin/evince-previewer
[    9.233836] type=1505 audit(1270045765.184:8): operation="profile_load" pid=478 name=/usr/bin/evince-thumbnailer
[    9.253324] type=1505 audit(1270045765.204:9): operation="profile_load" pid=480 name=/usr/lib/cups/backend/cups-pdf
[   18.458556] udev: starting version 147
[   18.472954] Adding 3574388k swap on /dev/sda6.  Priority:-1 extents:1 across:3574388k 
[   18.517888] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.521975] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x2140
[   18.521991] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2100
[   18.651117] lp: driver loaded but no devices found
[   18.677139] EXT4-fs (sda5): internal journal on sda5:8
[   18.794791] nvidia: module license 'NVIDIA' taints kernel.
[   18.794796] Disabling lock debugging due to kernel taint
[   19.121743] lib80211: common routines for IEEE802.11 drivers
[   19.121746] lib80211_crypt: registered algorithm 'NULL'
[   19.144806] wl 0000:03:00.0: power state changed by ACPI to D0
[   19.145014] wl 0000:03:00.0: setting latency timer to 64
[   19.175463] applesmc: Apple Macmini detected:
[   19.175466] applesmc:  - Model without accelerometer
[   19.175468] applesmc:  - Model without light sensors and backlight
[   19.175469] applesmc:  - Model with 2 temperature sensors
[   19.175510] applesmc: device successfully initialized.
[   19.176047] applesmc: 1 fans found.
[   19.176073] applesmc: driver successfully loaded.
[   19.197573] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.198987] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   19.199091] usbcore: registered new interface driver btusb
[   19.203965] lib80211_crypt: registered algorithm 'TKIP'
[   19.204256] eth1: Broadcom BCM4328 802.11 Wireless Controller 5.10.91.9
[   19.223678] udev: renamed network interface eth1 to eth2
[   19.241362] HDA Intel 0000:00:08.0: setting latency timer to 64
[   19.404126] nvidia 0000:02:00.0: setting latency timer to 64
[   19.404274] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   19.434974]   alloc irq_desc for 19 on node 0
[   19.434977]   alloc kstat_irqs on node 0
[   19.434985] forcedeth 0000:00:0a.0: irq 19 for MSI/MSI-X
[   19.481418] __ratelimit: 6 callbacks suppressed
[   19.481421] type=1505 audit(1270045775.434:12): operation="profile_replace" pid=1025 name=/usr/share/gdm/guest-session/Xsession
[   19.482844] type=1505 audit(1270045775.434:13): operation="profile_replace" pid=1026 name=/sbin/dhclient3
[   19.483469] type=1505 audit(1270045775.434:14): operation="profile_replace" pid=1026 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   19.483813] type=1505 audit(1270045775.434:15): operation="profile_replace" pid=1026 name=/usr/lib/connman/scripts/dhclient-script
[   19.486697] type=1505 audit(1270045775.434:16): operation="profile_replace" pid=1027 name=/usr/bin/evince
[   19.512024] type=1505 audit(1270045775.464:17): operation="profile_replace" pid=1027 name=/usr/bin/evince-previewer
[   19.517989] type=1505 audit(1270045775.464:18): operation="profile_replace" pid=1027 name=/usr/bin/evince-thumbnailer
[   19.529083] type=1505 audit(1270045775.474:19): operation="profile_replace" pid=1046 name=/usr/lib/cups/backend/cups-pdf
[   19.529818] type=1505 audit(1270045775.474:20): operation="profile_replace" pid=1046 name=/usr/sbin/cupsd
[   19.537625] type=1505 audit(1270045775.484:21): operation="profile_replace" pid=1052 name=/usr/sbin/tcpdump
[   20.250683] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.250686] Bluetooth: BNEP filters: protocol multicast
[   20.255624] Bridge firewalling registered
[   20.267705] usb 4-1.2: USB disconnect, address 4
[   20.370103] ppdev: user-space parallel port driver
[   20.440795] usb 4-1.3: USB disconnect, address 5
[   20.580041] hda_codec: Unknown model for ALC889A, trying auto-probe from BIOS...
[   20.620105] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input9
[   21.088382] CPU0 attaching NULL sched-domain.
[   21.088424] CPU0 attaching NULL sched-domain.
[   22.429974] usplash:402 freeing invalid memtype ffffffff91000000-ffffffff91e00000
[   24.082962] CPU0 attaching NULL sched-domain.
[   24.083004] CPU0 attaching NULL sched-domain.
[   29.680023] eth0: no IPv6 routers present
[   30.280013] eth2: no IPv6 routers present
chris@chris-desktop:~$

---

### Post by Legolas17 on 2010-03-31
had also updated to latest kernel 2.6.31-20-generic

sometimes after several reboots it shows me 2 cores but using ubuntu is sluggish and slow.
most of the times i still get only 1 core.

---

### Post by linuxopjemac on 2010-03-31
dmesg above shows 1 core indeed...weird that you sometimes have one, sometimes 2.

I have no experience in booting with grub-efi. I only know its existence by reading posts about it. I still use rEFIt the old fashioned way.

---

### Post by Legolas17 on 2010-03-31
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=aa16806c-c858-45a2-8787-9bdd4a401bcb ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006e64f000 (usable)
[    0.000000]  BIOS-e820: 000000006e64f000 - 000000006e651000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006e651000 - 000000006e652000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006e652000 - 000000006e654000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006e654000 - 000000006e6ae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006e6ae000 - 000000006e8af000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006e8af000 - 000000006f000000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006f000000 - 000000007f000000 (reserved)
[    0.000000]  BIOS-e820: 000000007f000000 - 000000007fec5000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fec5000 - 000000007fec7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fec7000 - 000000007fec8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fec8000 - 000000007feca000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007feca000 - 000000007fecd000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fecd000 - 000000007fedf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fedf000 - 000000007fef9000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef9000 - 000000007feff000 (reserved)
[    0.000000]  BIOS-e820: 000000007feff000 - 000000007ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000093400000 - 0000000093401000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x6e64f max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 disabled
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000006e64f000 (usable)
[    0.000000]  modified: 000000006e64f000 - 000000006e651000 (ACPI NVS)
[    0.000000]  modified: 000000006e651000 - 000000006e652000 (ACPI data)
[    0.000000]  modified: 000000006e652000 - 000000006e654000 (ACPI NVS)
[    0.000000]  modified: 000000006e654000 - 000000006e6ae000 (ACPI data)
[    0.000000]  modified: 000000006e6ae000 - 000000006e8af000 (ACPI NVS)
[    0.000000]  modified: 000000006e8af000 - 000000006f000000 (ACPI data)
[    0.000000]  modified: 000000006f000000 - 000000007f000000 (reserved)
[    0.000000]  modified: 000000007f000000 - 000000007fec5000 (ACPI data)
[    0.000000]  modified: 000000007fec5000 - 000000007fec7000 (ACPI NVS)
[    0.000000]  modified: 000000007fec7000 - 000000007fec8000 (ACPI data)
[    0.000000]  modified: 000000007fec8000 - 000000007feca000 (ACPI NVS)
[    0.000000]  modified: 000000007feca000 - 000000007fecd000 (ACPI data)
[    0.000000]  modified: 000000007fecd000 - 000000007fedf000 (ACPI NVS)
[    0.000000]  modified: 000000007fedf000 - 000000007fef9000 (ACPI data)
[    0.000000]  modified: 000000007fef9000 - 000000007feff000 (reserved)
[    0.000000]  modified: 000000007feff000 - 000000007ff00000 (ACPI data)
[    0.000000]  modified: 0000000093400000 - 0000000093401000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000006e64f000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 006e600000 page 2M
[    0.000000]  006e600000 - 006e64f000 page 4k
[    0.000000] kernel direct mapping tables up to 6e64f000 @ 8000-c000
[    0.000000] RAMDISK: 3786d000 - 37feff7a
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 APPLE )
[    0.000000] ACPI: XSDT 000000007feee1c0 0007C (v01 APPLE   Apple00 000000AD      01000013)
[    0.000000] ACPI: FACP 000000007feec000 000F4 (v04 APPLE   Apple00 000000AD Loki 0000005F)
[    0.000000] ACPI: DSDT 000000007fedf000 05150 (v01 APPLE   Macmini 00030001 INTL 20061109)
[    0.000000] ACPI: FACS 000000007fecd000 00040
[    0.000000] ACPI: HPET 000000007feeb000 00038 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: APIC 000000007feea000 00068 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: APIC 000000007fee9000 00068 (v02 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: MCFG 000000007fee8000 0003C (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: ASF! 000000007fee7000 000A5 (v32 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SBST 000000007fee6000 00030 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: ECDT 000000007fee5000 00053 (v01 APPLE   Apple00 00000001 Loki 0000005F)
[    0.000000] ACPI: SSDT 000000007fec7000 004DC (v01  APPLE    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 000000007fecc000 000A5 (v01 SataRe  SataPri 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 000000007fecb000 0009F (v01 SataRe  SataSec 00001000 INTL 20061109)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000006e64f000
[    0.000000] Bootmem setup node 0 0000000000000000-000000006e64f000
[    0.000000]   NODE_DATA [000000000000a000 - 000000000000efff]
[    0.000000]   bootmap [000000000000f000 -  000000000001cccf] pages e
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 006e64f000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e8c8c]    TEXT DATA BSS ==> [0001000000 - 00019e8c8c]
[    0.000000]   #3 [003786d000 - 0037feff7a]          RAMDISK ==> [003786d000 - 0037feff7a]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00019e9000 - 00019e91fd]              BRK ==> [00019e9000 - 00019e91fd]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]  [ffffea0000000000-ffffea00019fffff] PMD -> [ffff880001e00000-ffff8800037fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0006e64f
[    0.000000] On node 0 totalpages: 452073
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 101 pages reserved
[    0.000000]   DMA zone: 3837 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6127 pages used for memmap
[    0.000000]   DMA32 zone: 441952 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 93401000 (gap: 93401000:5cbff000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019fb000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 445789
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=aa16806c-c858-45a2-8787-9bdd4a401bcb ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1763412k/1808700k available (5327k kernel code, 408k absent, 44880k reserved, 3014k data, 664k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2254.944 MHz processor.
[    0.000015] spurious 8259A interrupt: IRQ7.
[    0.001611] Console: colour VGA+ 80x25
[    0.001613] console [tty0] enabled
[    0.010000] allocated 18350080 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4509.88 BogoMIPS (lpj=22549440)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring enabled (TM2)
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.013267] Setting APIC routing to flat
[    0.013656] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.113661] CPU0: Intel(R) Core(TM)2 Duo CPU     P7550  @ 2.26GHz stepping 0a
[    0.120000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 4510.63 BogoMIPS (lpj=22553177)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.271536] CPU1: Intel(R) Core(TM)2 Duo CPU     P7550  @ 2.26GHz stepping 0a
[    0.271549] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.280022] Brought up 2 CPUs
[    0.280025] Total of 2 processors activated (9020.52 BogoMIPS).
[    0.280093] CPU0 attaching sched-domain:
[    0.280096]  domain 0: span 0-1 level MC
[    0.280098]   groups: 0 1
[    0.280103] CPU1 attaching sched-domain:
[    0.280105]  domain 0: span 0-1 level MC
[    0.280106]   groups: 1 0
[    0.280180] Booting paravirtualized kernel on bare hardware
[    0.280195] regulator: core version 0.5
[    0.280195] Time: 15:31:58  Date: 03/31/10
[    0.280195] NET: Registered protocol family 16
[    0.280222] ACPI: bus type pci registered
[    0.280496] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 255
[    0.280499] PCI: MCFG area at f0000000 reserved in E820
[    0.280501] PCI: updated MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.281812] PCI: Using MMCONFIG at f0000000 - f3ffffff
[    0.281813] PCI: Using configuration type 1 for base access
[    0.282552] bio: create slab <bio-0> at 0
[    0.282552] ACPI: EC: EC description table is found, configuring boot EC
[    0.282552] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.301849] ACPI: BIOS _OSI(Linux) query ignored
[    0.302369] ACPI: Interpreter enabled
[    0.302371] ACPI: (supports S0 S3 S4 S5)
[    0.302390] ACPI: Using IOAPIC for interrupt routing
[    0.311269] ACPI: EC: GPE = 0x3f, I/O: command/status = 0x66, data = 0x62
[    0.311271] ACPI: EC: driver started in interrupt mode
[    0.311581] ACPI: No dock devices found.
[    0.311844] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.312079] pci 0000:00:03.0: reg 10 io port: [0x2000-0x20ff]
[    0.312176] pci 0000:00:03.2: reg 10 io port: [0x2180-0x21bf]
[    0.312189] pci 0000:00:03.2: reg 20 io port: [0x2140-0x217f]
[    0.312193] pci 0000:00:03.2: reg 24 io port: [0x2100-0x213f]
[    0.312215] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    0.312221] pci 0000:00:03.2: PME# disabled
[    0.312380] pci 0000:00:03.5: reg 10 32bit mmio: [0x93400000-0x9347ffff]
[    0.312468] pci 0000:00:04.0: reg 10 32bit mmio: [0x93488000-0x93488fff]
[    0.312497] pci 0000:00:04.0: supports D1 D2
[    0.312499] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.312502] pci 0000:00:04.0: PME# disabled
[    0.312529] pci 0000:00:04.1: reg 10 32bit mmio: [0x93489200-0x934892ff]
[    0.312563] pci 0000:00:04.1: supports D1 D2
[    0.312564] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.312568] pci 0000:00:04.1: PME# disabled
[    0.312599] pci 0000:00:06.0: reg 10 32bit mmio: [0x93487000-0x93487fff]
[    0.312627] pci 0000:00:06.0: supports D1 D2
[    0.312629] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.312632] pci 0000:00:06.0: PME# disabled
[    0.312659] pci 0000:00:06.1: reg 10 32bit mmio: [0x93489100-0x934891ff]
[    0.312692] pci 0000:00:06.1: supports D1 D2
[    0.312694] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.312698] pci 0000:00:06.1: PME# disabled
[    0.312729] pci 0000:00:08.0: reg 10 32bit mmio: [0x93480000-0x93483fff]
[    0.312758] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.312761] pci 0000:00:08.0: PME# disabled
[    0.312816] pci 0000:00:0a.0: reg 10 32bit mmio: [0x93486000-0x93486fff]
[    0.312821] pci 0000:00:0a.0: reg 14 io port: [0x21e0-0x21e7]
[    0.312825] pci 0000:00:0a.0: reg 18 32bit mmio: [0x93489000-0x934890ff]
[    0.312829] pci 0000:00:0a.0: reg 1c 32bit mmio: [0x93489300-0x9348930f]
[    0.312852] pci 0000:00:0a.0: supports D1 D2
[    0.312854] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.312858] pci 0000:00:0a.0: PME# disabled
[    0.312884] pci 0000:00:0b.0: reg 10 io port: [0x21d8-0x21df]
[    0.312888] pci 0000:00:0b.0: reg 14 io port: [0x21ec-0x21ef]
[    0.312892] pci 0000:00:0b.0: reg 18 io port: [0x21d0-0x21d7]
[    0.312896] pci 0000:00:0b.0: reg 1c io port: [0x21e8-0x21eb]
[    0.312900] pci 0000:00:0b.0: reg 20 io port: [0x21c0-0x21cf]
[    0.312905] pci 0000:00:0b.0: reg 24 32bit mmio: [0x93484000-0x93485fff]
[    0.312964] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.312967] pci 0000:00:10.0: PME# disabled
[    0.313162] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.313169] pci 0000:00:15.0: PME# disabled
[    0.313390] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.313397] pci 0000:00:16.0: PME# disabled
[    0.313485] pci 0000:00:09.0: transparent bridge
[    0.313489] pci 0000:00:09.0: bridge 32bit mmio: [0x93300000-0x933fffff]
[    0.313523] pci 0000:02:00.0: reg 10 32bit mmio: [0x92000000-0x92ffffff]
[    0.313532] pci 0000:02:00.0: reg 14 64bit mmio: [0x80000000-0x8fffffff]
[    0.313541] pci 0000:02:00.0: reg 1c 64bit mmio: [0x90000000-0x91ffffff]
[    0.313547] pci 0000:02:00.0: reg 24 io port: [0x1000-0x107f]
[    0.313552] pci 0000:02:00.0: reg 30 32bit mmio: [0x93000000-0x9301ffff]
[    0.313609] pci 0000:00:10.0: bridge io port: [0x1000-0x1fff]
[    0.313612] pci 0000:00:10.0: bridge 32bit mmio: [0x92000000-0x930fffff]
[    0.313616] pci 0000:00:10.0: bridge 64bit mmio pref: [0x80000000-0x91ffffff]
[    0.313862] pci 0000:03:00.0: reg 10 64bit mmio: [0x93200000-0x93203fff]
[    0.313916] pci 0000:03:00.0: supports D1 D2
[    0.313918] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.313922] pci 0000:03:00.0: PME# disabled
[    0.313996] pci 0000:00:15.0: bridge 32bit mmio: [0x93200000-0x932fffff]
[    0.314061] pci 0000:04:00.0: reg 10 64bit mmio: [0x93100000-0x93100fff]
[    0.314116] pci 0000:04:00.0: supports D1 D2
[    0.314118] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.314122] pci 0000:04:00.0: PME# disabled
[    0.314193] pci 0000:00:16.0: bridge 32bit mmio: [0x93100000-0x931fffff]
[    0.314241] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.314549] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.368956] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.369189] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.369420] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.369650] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.369886] ACPI: PCI Interrupt Link [Z003] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.370122] ACPI: PCI Interrupt Link [Z004] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.370351] ACPI: PCI Interrupt Link [Z005] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.370580] ACPI: PCI Interrupt Link [Z006] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.370811] ACPI: PCI Interrupt Link [Z007] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.371041] ACPI: PCI Interrupt Link [Z008] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.371270] ACPI: PCI Interrupt Link [Z009] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.371499] ACPI: PCI Interrupt Link [Z00A] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.371727] ACPI: PCI Interrupt Link [Z00B] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.371957] ACPI: PCI Interrupt Link [Z00C] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.372186] ACPI: PCI Interrupt Link [Z00D] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.372415] ACPI: PCI Interrupt Link [Z00E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.372644] ACPI: PCI Interrupt Link [Z00F] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.372872] ACPI: PCI Interrupt Link [Z00G] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.373102] ACPI: PCI Interrupt Link [Z00H] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.373330] ACPI: PCI Interrupt Link [Z00I] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.373558] ACPI: PCI Interrupt Link [Z00J] (IRQs 16 17 18 19 20 21 22 23) *7
[    0.373788] ACPI: PCI Interrupt Link [Z00K] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.374022] ACPI: PCI Interrupt Link [Z00L] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.374252] ACPI: PCI Interrupt Link [Z00M] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.374482] ACPI: PCI Interrupt Link [Z00N] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.374712] ACPI: PCI Interrupt Link [Z00O] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.374942] ACPI: PCI Interrupt Link [Z00P] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.375172] ACPI: PCI Interrupt Link [Z00Q] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.375402] ACPI: PCI Interrupt Link [Z00R] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.375633] ACPI: PCI Interrupt Link [Z00S] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.375863] ACPI: PCI Interrupt Link [Z00T] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.376093] ACPI: PCI Interrupt Link [Z00U] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.376322] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *15
[    0.376551] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.376779] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.377013] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *14
[    0.377248] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *15
[    0.377482] ACPI: PCI Interrupt Link [LGPU] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.377710] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.377940] ACPI: PCI Interrupt Link [LSI0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.378173] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.378403] ACPI: PCI Interrupt Link [Z000] (IRQs 16 17 18 19 20 21 22 23) *7
[    0.378636] ACPI: PCI Interrupt Link [Z001] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.378870] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *14
[    0.379037] SCSI subsystem initialized
[    0.379054] libata version 3.00 loaded.
[    0.379054] usbcore: registered new interface driver usbfs
[    0.379054] usbcore: registered new interface driver hub
[    0.379054] usbcore: registered new device driver usb
[    0.379054] ACPI: WMI: Mapper loaded
[    0.379054] PCI: Using ACPI for IRQ routing
[    0.400005] Bluetooth: Core ver 2.15
[    0.400018] NET: Registered protocol family 31
[    0.400018] Bluetooth: HCI device and connection manager initialized
[    0.400018] Bluetooth: HCI socket layer initialized
[    0.400018] NetLabel: Initializing
[    0.400018] NetLabel:  domain hash size = 128
[    0.400018] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.400029] NetLabel:  unlabeled traffic allowed by default
[    0.400069] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.400074] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.440009] pnp: PnP ACPI init
[    0.440018] ACPI: bus type pnp registered
[    0.442996] pnp: PnP ACPI: found 8 devices
[    0.442999] ACPI: ACPI bus type pnp unregistered
[    0.443008] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.443014] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.443019] system 00:06: ioport range 0x400-0x47f has been reserved
[    0.443021] system 00:06: ioport range 0x480-0x4ff has been reserved
[    0.443023] system 00:06: ioport range 0x500-0x57f has been reserved
[    0.443026] system 00:06: ioport range 0x580-0x5ff has been reserved
[    0.443028] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.443030] system 00:06: ioport range 0x880-0x8ff has been reserved
[    0.443033] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.443036] system 00:06: ioport range 0x295-0x296 has been reserved
[    0.447695] AppArmor: AppArmor Filesystem Enabled
[    0.447754] pci 0000:00:09.0: PCI bridge, secondary bus 0000:01
[    0.447756] pci 0000:00:09.0:   IO window: disabled
[    0.447760] pci 0000:00:09.0:   MEM window: 0x93300000-0x933fffff
[    0.447763] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.447766] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
[    0.447769] pci 0000:00:10.0:   IO window: 0x1000-0x1fff
[    0.447772] pci 0000:00:10.0:   MEM window: 0x92000000-0x930fffff
[    0.447775] pci 0000:00:10.0:   PREFETCH window: 0x00000080000000-0x00000091ffffff
[    0.447779] pci 0000:00:15.0: PCI bridge, secondary bus 0000:03
[    0.447781] pci 0000:00:15.0:   IO window: disabled
[    0.447791] pci 0000:00:15.0:   MEM window: 0x93200000-0x932fffff
[    0.447798] pci 0000:00:15.0:   PREFETCH window: disabled
[    0.447805] pci 0000:00:16.0: PCI bridge, secondary bus 0000:04
[    0.447807] pci 0000:00:16.0:   IO window: disabled
[    0.447817] pci 0000:00:16.0:   MEM window: 0x93100000-0x931fffff
[    0.447824] pci 0000:00:16.0:   PREFETCH window: disabled
[    0.447833] pci 0000:00:09.0: enabling device (0000 -> 0002)
[    0.447839] pci 0000:00:09.0: setting latency timer to 64
[    0.447844] pci 0000:00:10.0: setting latency timer to 64
[    0.448188] ACPI: PCI Interrupt Link [Z00F] enabled at IRQ 23
[    0.448191]   alloc irq_desc for 23 on node 0
[    0.448192]   alloc kstat_irqs on node 0
[    0.448197] pci 0000:00:15.0: PCI INT A -> Link[Z00F] -> GSI 23 (level, low) -> IRQ 23
[    0.448205] pci 0000:00:15.0: setting latency timer to 64
[    0.448540] ACPI: PCI Interrupt Link [Z00J] enabled at IRQ 22
[    0.448542]   alloc irq_desc for 22 on node 0
[    0.448544]   alloc kstat_irqs on node 0
[    0.448547] pci 0000:00:16.0: PCI INT A -> Link[Z00J] -> GSI 22 (level, low) -> IRQ 22
[    0.448555] pci 0000:00:16.0: setting latency timer to 64
[    0.448561] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.448563] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.448565] pci_bus 0000:01: resource 1 mem: [0x93300000-0x933fffff]
[    0.448567] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.448569] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.448572] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.448574] pci_bus 0000:02: resource 1 mem: [0x92000000-0x930fffff]
[    0.448576] pci_bus 0000:02: resource 2 pref mem [0x80000000-0x91ffffff]
[    0.448578] pci_bus 0000:03: resource 1 mem: [0x93200000-0x932fffff]
[    0.448580] pci_bus 0000:04: resource 1 mem: [0x93100000-0x931fffff]
[    0.448607] NET: Registered protocol family 2
[    0.448722] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.449380] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.451143] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.451611] TCP: Hash tables configured (established 262144 bind 65536)
[    0.451614] TCP reno registered
[    0.451720] NET: Registered protocol family 1
[    0.451784] Trying to unpack rootfs image as initramfs...
[    0.501584] Switched to high resolution mode on CPU 1
[    0.510022] Switched to high resolution mode on CPU 0
[    0.614424] Freeing initrd memory: 7691k freed
[    0.617738] Scanning for low memory corruption every 60 seconds
[    0.617873] audit: initializing netlink socket (disabled)
[    0.617889] type=2000 audit(1270049518.610:1): initialized
[    0.626431] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.627685] VFS: Disk quotas dquot_6.5.2
[    0.627731] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.628227] fuse init (API version 7.12)
[    0.628296] msgmni has been set to 3459
[    0.628482] alg: No test for stdrng (krng)
[    0.628494] io scheduler noop registered
[    0.628496] io scheduler anticipatory registered
[    0.628498] io scheduler deadline registered
[    0.628529] io scheduler cfq registered (default)
[    0.640152] pci 0000:02:00.0: Boot video device
[    0.640472]   alloc irq_desc for 24 on node 0
[    0.640474]   alloc kstat_irqs on node 0
[    0.640494] pcieport-driver 0000:00:15.0: irq 24 for MSI/MSI-X
[    0.640514] pcieport-driver 0000:00:15.0: setting latency timer to 64
[    0.640882]   alloc irq_desc for 25 on node 0
[    0.640883]   alloc kstat_irqs on node 0
[    0.640900] pcieport-driver 0000:00:16.0: irq 25 for MSI/MSI-X
[    0.640919] pcieport-driver 0000:00:16.0: setting latency timer to 64
[    0.641084] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.641104] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.641230] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.641234] ACPI: Power Button [PWRF]
[    0.641282] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.641284] ACPI: Power Button [PWRB]
[    0.641321] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.641324] ACPI: Sleep Button [SLPB]
[    0.642127] ACPI: SSDT 000000007fec9c98 00238 (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
[    0.642505] ACPI: SSDT 000000007fec8c18 002AD (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
[    0.642865] Monitor-Mwait will be used to enter C-1 state
[    0.642888] Monitor-Mwait will be used to enter C-2 state
[    0.642906] Monitor-Mwait will be used to enter C-3 state
[    0.642913] Marking TSC unstable due to TSC halts in idle
[    0.642931] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.642952] processor LNXCPU:00: registered as cooling_device0
[    0.642955] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.643276] ACPI: SSDT 000000007fec9f18 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
[    0.643582] ACPI: SSDT 000000007fec8f18 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
[    0.644069] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.644086] processor LNXCPU:01: registered as cooling_device1
[    0.644089] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.648588] Linux agpgart interface v0.103
[    0.648596] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.649593] brd: module loaded
[    0.649966] loop: module loaded
[    0.650024] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.650163] ahci 0000:00:0b.0: version 3.0
[    0.650507] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 21
[    0.650511]   alloc irq_desc for 21 on node 0
[    0.650513]   alloc kstat_irqs on node 0
[    0.650518] ahci 0000:00:0b.0: PCI INT A -> Link[LSI0] -> GSI 21 (level, low) -> IRQ 21
[    0.650544]   alloc irq_desc for 26 on node 0
[    0.650546]   alloc kstat_irqs on node 0
[    0.650551] ahci 0000:00:0b.0: irq 26 for MSI/MSI-X
[    0.650606] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3 impl IDE mode
[    0.650609] ahci 0000:00:0b.0: flags: 64bit ncq sntf pm led pmp pio slum part 
[    0.650612] ahci 0000:00:0b.0: setting latency timer to 64
[    0.650779] scsi0 : ahci
[    0.650856] scsi1 : ahci
[    0.650903] scsi2 : ahci
[    0.650953] scsi3 : ahci
[    0.651001] scsi4 : ahci
[    0.651051] scsi5 : ahci
[    0.651165] ata1: SATA max UDMA/133 abar m8192@0x93484000 port 0x93484100 irq 26
[    0.651168] ata2: SATA max UDMA/133 abar m8192@0x93484000 port 0x93484180 irq 26
[    0.651170] ata3: DUMMY
[    0.651171] ata4: DUMMY
[    0.651172] ata5: DUMMY
[    0.651173] ata6: DUMMY
[    0.651877] Fixed MDIO Bus: probed
[    0.651905] PPP generic driver version 2.4.2
[    0.651980] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.652355] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
[    0.652358]   alloc irq_desc for 20 on node 0
[    0.652359]   alloc kstat_irqs on node 0
[    0.652363] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 20 (level, low) -> IRQ 20
[    0.652371] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.652374] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.652404] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.652428] ehci_hcd 0000:00:04.1: debug port 1
[    0.652432] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    0.652445] ehci_hcd 0000:00:04.1: irq 20, io mem 0x93489200
[    0.670018] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.670084] usb usb1: configuration #1 chosen from 1 choice
[    0.670112] hub 1-0:1.0: USB hub found
[    0.670119] hub 1-0:1.0: 7 ports detected
[    0.670518] ACPI: PCI Interrupt Link [Z001] enabled at IRQ 19
[    0.670520]   alloc irq_desc for 19 on node 0
[    0.670522]   alloc kstat_irqs on node 0
[    0.670525] ehci_hcd 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 19 (level, low) -> IRQ 19
[    0.670533] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    0.670535] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    0.670560] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.670582] ehci_hcd 0000:00:06.1: debug port 1
[    0.670586] ehci_hcd 0000:00:06.1: cache line size of 32 is not supported
[    0.670598] ehci_hcd 0000:00:06.1: irq 19, io mem 0x93489100
[    0.690014] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    0.690064] usb usb2: configuration #1 chosen from 1 choice
[    0.690088] hub 2-0:1.0: USB hub found
[    0.690094] hub 2-0:1.0: 5 ports detected
[    0.690143] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.690503] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    0.690505]   alloc irq_desc for 18 on node 0
[    0.690507]   alloc kstat_irqs on node 0
[    0.690510] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    0.690518] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.690521] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.690549] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.690566] ohci_hcd 0000:00:04.0: irq 18, io mem 0x93488000
[    0.752061] usb usb3: configuration #1 chosen from 1 choice
[    0.752082] hub 3-0:1.0: USB hub found
[    0.752089] hub 3-0:1.0: 7 ports detected
[    0.752485] ACPI: PCI Interrupt Link [Z000] enabled at IRQ 17
[    0.752487]   alloc irq_desc for 17 on node 0
[    0.752489]   alloc kstat_irqs on node 0
[    0.752493] ohci_hcd 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 17 (level, low) -> IRQ 17
[    0.752501] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    0.752504] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    0.752529] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    0.752546] ohci_hcd 0000:00:06.0: irq 17, io mem 0x93487000
[    0.812059] usb usb4: configuration #1 chosen from 1 choice
[    0.812081] hub 4-0:1.0: USB hub found
[    0.812089] hub 4-0:1.0: 5 ports detected
[    0.812133] uhci_hcd: USB Universal Host Controller Interface driver
[    0.812215] PNP: No PS/2 controller found. Probing ports directly.
[    0.813083] i8042.c: No controller found.
[    0.813124] mice: PS/2 mouse device common for all mice
[    0.813215] rtc_cmos 00:07: RTC can wake from S4
[    0.813247] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.813295] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.813389] device-mapper: uevent: version 1.0.3
[    0.813457] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.813518] device-mapper: multipath: version 1.1.0 loaded
[    0.813521] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.813723] cpuidle: using governor ladder
[    0.813818] cpuidle: using governor menu
[    0.814158] TCP cubic registered
[    0.814266] NET: Registered protocol family 10
[    0.814639] lo: Disabled Privacy Extensions
[    0.814896] NET: Registered protocol family 17
[    0.814911] Bluetooth: L2CAP ver 2.13
[    0.814913] Bluetooth: L2CAP socket layer initialized
[    0.814916] Bluetooth: SCO (Voice Link) ver 0.6
[    0.814918] Bluetooth: SCO socket layer initialized
[    0.814943] Bluetooth: RFCOMM TTY layer initialized
[    0.814946] Bluetooth: RFCOMM socket layer initialized
[    0.814947] Bluetooth: RFCOMM ver 1.11
[    0.815578] PM: Resume from disk failed.
[    0.815589] registered taskstats version 1
[    0.815684]   Magic number: 2:380:539
[    0.815806] rtc_cmos 00:07: setting system clock to 2010-03-31 15:31:59 UTC (1270049519)
[    0.815809] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.815810] EDD information not available.
[    0.992619] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    1.002585] Clocksource tsc unstable (delta = -177188260 ns)
[    1.149580] usb 1-3: configuration #1 chosen from 1 choice
[    1.149784] hub 1-3:1.0: USB hub found
[    1.149906] hub 1-3:1.0: 3 ports detected
[    1.180122] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.180135] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.180541] ata1.00: ATA-8: FUJITSU MHZ2160BH G1, 00810009, max UDMA/100
[    1.180545] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.181121] ata1.00: configured for UDMA/100
[    1.186419] ata2.00: ATAPI: OPTIARC DVD RW AD-5670S, 2AHI, max UDMA/100, ATAPI AN
[    1.191965] ata2.00: configured for UDMA/100
[    1.200205] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2160B 0081 PQ: 0 ANSI: 5
[    1.200308] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.200340] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.200377] sd 0:0:0:0: [sda] Write Protect is off
[    1.200380] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.200400] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.200503]  sda:
[    1.215689] scsi 1:0:0:0: CD-ROM            OPTIARC  DVD RW AD-5670S  2AHI PQ: 0 ANSI: 5
[    1.238340] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[    1.238343] Uniform CD-ROM driver Revision: 3.20
[    1.238428] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.238476] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.275875]  sda1 sda2 sda3 sda4 sda5 sda6
[    1.276190] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.276233] Freeing unused kernel memory: 664k freed
[    1.276438] Write protecting the kernel read-only data: 7596k
[    1.362578] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.362978] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 16
[    1.362983]   alloc irq_desc for 16 on node 0
[    1.362985]   alloc kstat_irqs on node 0
[    1.362991] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 16 (level, low) -> IRQ 16
[    1.362995] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.390064] ohci1394 0000:04:00.0: PCI INT A -> Link[Z00J] -> GSI 22 (level, low) -> IRQ 22
[    1.390071] ohci1394 0000:04:00.0: setting latency timer to 64
[    1.441405] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr d4:9a:20:bc:e4:42
[    1.441409] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    1.452193] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[93100000-931007ff]  Max Packet=[4096]  IR/IT contexts=[8/8]
[    1.730092] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    1.966113] usb 4-1: configuration #1 chosen from 1 choice
[    1.969093] hub 4-1:1.0: USB hub found
[    1.972054] hub 4-1:1.0: 3 ports detected
[    2.310032] usb 4-4: new low speed USB device using ohci_hcd and address 3
[    2.540091] usb 4-4: configuration #1 chosen from 1 choice
[    2.546919] usbcore: registered new interface driver hiddev
[    2.546966] usbcore: registered new interface driver usbhid
[    2.546968] usbhid: v2.6:USB HID core driver
[    2.554268] input: Mitsumi Electric Apple Optical USB Mouse as /devices/pci0000:00/0000:00:06.0/usb4/4-4/4-4:1.0/input/input4
[    2.554330] apple 0003:05AC:0304.0001: input,hidraw0: USB HID v1.10 Mouse [Mitsumi Electric Apple Optical USB Mouse] on usb-0000:00:06.0-4/input0
[    2.790106] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[d49a20fffebce442]
[    2.890029] usb 3-5: new low speed USB device using ohci_hcd and address 2
[    3.119087] usb 3-5: configuration #1 chosen from 1 choice
[    3.138088] apple 0003:05AC:8242.0002: hiddev96,hidraw1: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:04.0-5/input0
[    3.214603] usb 1-3.2: new low speed USB device using ehci_hcd and address 4
[    3.337065] usb 1-3.2: configuration #1 chosen from 1 choice
[    3.341331] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:04.1/usb1/1-3/1-3.2/1-3.2:1.0/input/input5
[    3.341380] apple 0003:05AC:0221.0003: input,hidraw2: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:04.1-3.2/input0
[    3.345096] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:04.1/usb1/1-3/1-3.2/1-3.2:1.1/input/input6
[    3.345160] apple 0003:05AC:0221.0004: input,hidraw3: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:04.1-3.2/input1
[    3.432096] usb 4-1.1: new full speed USB device using ohci_hcd and address 4
[    3.594213] PM: Starting manual resume from disk
[    3.594217] PM: Resume from partition 8:6
[    3.594218] PM: Checking hibernation image.
[    3.594414] PM: Resume from disk failed.
[    3.599651] EXT4-fs (sda5): barriers enabled
[    3.608183] usb 4-1.1: configuration #1 chosen from 1 choice
[    3.623620] kjournald2 starting: pid 457, dev sda5:8, commit interval 5 seconds
[    3.623743] EXT4-fs (sda5): delayed allocation enabled
[    3.623746] EXT4-fs: file extents enabled
[    3.628428] EXT4-fs: mballoc enabled
[    3.628439] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    3.712098] usb 4-1.2: new full speed USB device using ohci_hcd and address 5
[    3.837113] usb 4-1.2: configuration #1 chosen from 1 choice
[    3.847357] input: HID 05ac:820a as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1.2/4-1.2:1.0/input/input7
[    3.847413] generic-usb 0003:05AC:820A.0005: input,hidraw4: USB HID v1.11 Keyboard [HID 05ac:820a] on usb-0000:00:06.0-1.2/input0
[    3.932097] usb 4-1.3: new full speed USB device using ohci_hcd and address 6
[    4.057182] usb 4-1.3: configuration #1 chosen from 1 choice
[    4.067356] input: HID 05ac:820b as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1.3/4-1.3:1.0/input/input8
[    4.067420] generic-usb 0003:05AC:820B.0006: input,hidraw5: USB HID v1.11 Mouse [HID 05ac:820b] on usb-0000:00:06.0-1.3/input0
[    4.308846] type=1505 audit(1270049522.984:2): operation="profile_load" pid=490 name=/usr/share/gdm/guest-session/Xsession
[    4.310912] type=1505 audit(1270049522.994:3): operation="profile_load" pid=491 name=/sbin/dhclient3
[    4.311569] type=1505 audit(1270049522.994:4): operation="profile_load" pid=491 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.311911] type=1505 audit(1270049522.994:5): operation="profile_load" pid=491 name=/usr/lib/connman/scripts/dhclient-script
[    4.368244] type=1505 audit(1270049523.044:6): operation="profile_load" pid=492 name=/usr/bin/evince
[    4.378376] type=1505 audit(1270049523.054:7): operation="profile_load" pid=492 name=/usr/bin/evince-previewer
[    4.384358] type=1505 audit(1270049523.064:8): operation="profile_load" pid=492 name=/usr/bin/evince-thumbnailer
[    4.403856] type=1505 audit(1270049523.084:9): operation="profile_load" pid=494 name=/usr/lib/cups/backend/cups-pdf
[   13.626541] udev: starting version 147
[   13.634497] Adding 3574388k swap on /dev/sda6.  Priority:-1 extents:1 across:3574388k 
[   13.652398] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.659729] lib80211: common routines for IEEE802.11 drivers
[   13.659732] lib80211_crypt: registered algorithm 'NULL'
[   13.662356] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.662361] Disabling lock debugging due to kernel taint
[   13.681874] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x2140
[   13.681892] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2100
[   13.682184] wl 0000:03:00.0: power state changed by ACPI to D0
[   13.682388] wl 0000:03:00.0: PCI INT A -> Link[Z00F] -> GSI 23 (level, low) -> IRQ 23
[   13.682393] wl 0000:03:00.0: setting latency timer to 64
[   13.768675] lib80211_crypt: registered algorithm 'TKIP'
[   13.768898] lp: driver loaded but no devices found
[   13.910901] applesmc: Apple Macmini detected:
[   13.910904] applesmc:  - Model without accelerometer
[   13.910905] applesmc:  - Model without light sensors and backlight
[   13.910907] applesmc:  - Model with 2 temperature sensors
[   13.910946] applesmc: device successfully initialized.
[   13.911484] applesmc: 1 fans found.
[   13.911508] applesmc: driver successfully loaded.
[   13.934704] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.985392] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   13.985492] usbcore: registered new interface driver btusb
[   13.994741] eth1: Broadcom BCM4328 802.11 Wireless Controller 5.10.91.9
[   13.995321] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   13.995326] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[   13.995357] HDA Intel 0000:00:08.0: setting latency timer to 64
[   14.010172] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 22
[   14.010178] nvidia 0000:02:00.0: PCI INT A -> Link[LGPU] -> GSI 22 (level, low) -> IRQ 22
[   14.010186] nvidia 0000:02:00.0: setting latency timer to 64
[   14.010408] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   14.025429] udev: renamed network interface eth1 to eth2
[   14.119868] EXT4-fs (sda5): internal journal on sda5:8
[   14.292719] __ratelimit: 6 callbacks suppressed
[   14.292722] type=1505 audit(1270049532.974:12): operation="profile_replace" pid=1003 name=/usr/share/gdm/guest-session/Xsession
[   14.294863] type=1505 audit(1270049532.974:13): operation="profile_replace" pid=1005 name=/sbin/dhclient3
[   14.295497] type=1505 audit(1270049532.974:14): operation="profile_replace" pid=1005 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.295840] type=1505 audit(1270049532.974:15): operation="profile_replace" pid=1005 name=/usr/lib/connman/scripts/dhclient-script
[   14.299004] type=1505 audit(1270049532.974:16): operation="profile_replace" pid=1006 name=/usr/bin/evince
[   14.309155] type=1505 audit(1270049532.984:17): operation="profile_replace" pid=1006 name=/usr/bin/evince-previewer
[   14.315097] type=1505 audit(1270049532.994:18): operation="profile_replace" pid=1006 name=/usr/bin/evince-thumbnailer
[   14.323722] type=1505 audit(1270049533.004:19): operation="profile_replace" pid=1010 name=/usr/lib/cups/backend/cups-pdf
[   14.324459] type=1505 audit(1270049533.004:20): operation="profile_replace" pid=1010 name=/usr/sbin/cupsd
[   14.326632] type=1505 audit(1270049533.004:21): operation="profile_replace" pid=1011 name=/usr/sbin/tcpdump
[   14.389589]   alloc irq_desc for 27 on node 0
[   14.389592]   alloc kstat_irqs on node 0
[   14.389601] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[   15.078112] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.078115] Bluetooth: BNEP filters: protocol multicast
[   15.083487] Bridge firewalling registered
[   15.119099] usb 4-1.2: USB disconnect, address 5
[   15.142864] ppdev: user-space parallel port driver
[   15.340292] hda_codec: Unknown model for ALC889A, trying auto-probe from BIOS...
[   15.348036] usb 4-1.3: USB disconnect, address 6
[   15.388861] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input9
[   16.841451] usplash:415 freeing invalid memtype ffffffff91000000-ffffffff91e00000
[   24.740037] eth2: no IPv6 routers present
[   25.310020] eth0: no IPv6 routers present

---

### Post by Legolas17 on 2010-03-31
so and this time the config when it works on 2 cores.
I also use rEfit 1.4.

---

### Post by realzippy on 2010-03-31
You have a fake CPU...   ;)

---

### Post by Legolas17 on 2010-04-01
Seems so. But the heaviest about it is that it works with windows!
But i love Ubuntu.

---

### Post by Legolas17 on 2010-04-02
Little update: god it working with Ubuntu 9.04.
Now what are the differences betwen 9.04 and 9.10?

---

### Post by linuxopjemac on 2010-04-02
good for you, stay with 9.04 then! I have no idea what is the difference. Anyone ?

---

