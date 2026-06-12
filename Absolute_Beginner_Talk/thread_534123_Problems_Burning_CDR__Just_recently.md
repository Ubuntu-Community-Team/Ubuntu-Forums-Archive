---
title: "Problems Burning CDR  Just recently"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by mep on 2007-08-24
Hello,

Running 7.04 Ubuntu and I have had my DVD/CDR installed for 4 months.  Its a Pioneer 212D SATA and I have a DG965OT Intel board..

Anyhow I have always used Yuden CDR media and never a problem with doing CDR but just the other day I now cant burn a CDR at all ??  I even tried my BenQ external USB and it gave same error..  Cant burn an iso at all..  Very frustrating as all I have done it updated whatever Ubuntu has asked..

Now I can burn DVD but no CDR in machine at all

Get an error that says use slower speed which I have done and still no burning on CDR

This has got me as i have had no problems what so ever.. ???

This just started the other day too..

-mep

---

### Post by very_japi on 2007-08-26
Post the output of 
```
sudo lshw
```
```
dmesg
```
and your /etc/fstab

... might find something weird.

---

### Post by mep on 2007-08-26
Here is response:  Thanks hope this can help me

```
mike-desktop
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=desktop uuid=4EC8E22A-6ED6-11DB-937A-00E0188FF8D8
  *-core
       description: Motherboard
       product: DG965OT
       vendor: Intel Corporation
       physical id: 0
       version: AAD63733-203
       serial: BQOT6450048L
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 15.6.2
          serial: 0000-0F62-0000-0000-0000-0000
          slot: LGA 775
          size: 3GHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx cid cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 1
             slot: Unknown
             size: 16KB
             capacity: 16KB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 2
             slot: Unknown
             size: 2MB
             capacity: 2MB
             capabilities: asynchronous internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 3
          version: MQ96510J.86A.1699.2007.0729.2026 (07/29/2007)
          size: 64KB
          capacity: 960KB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 0x4F435A32353333313032345644432D4B2020
             vendor: 0x7F7F7F7FB0000000
             physical id: 0
             serial: 0x00000000
             slot: J1MY
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 0x4F435A323533333531325620202020202020
             vendor: 0x7F7F7F7FB0000000
             physical id: 1
             serial: 0x00000000
             slot: J2MY
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 0x4F435A32353333313032345644432D4B2020
             vendor: 0x7F7F7F7FB0000000
             physical id: 2
             serial: 0x00000000
             slot: J3MY
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 0x4F435A323533333531325620202020202020
             vendor: 0x7F7F7F7FB0000000
             physical id: 3
             serial: 0x00000000
             slot: J4MY
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: iomemory:95000000-95ffffff iomemory:80000000-8fffffff iomemory:94000000-94ffffff irq:16
        *-communication UNCLAIMED
             description: Communication controller
             product: 82P965/G965 HECI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@00:03.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: iomemory:96225900-9622590f irq:11
        *-network
             description: Ethernet interface
             product: 82566DC Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@00:19.0
             logical name: eth0
             version: 02
             serial: 00:16:76:e1:92:0b
             size: 100MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=1.1-0 ip=192.168.0.104 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
             resources: iomemory:96200000-9621ffff iomemory:96224000-96224fff ioport:20c0-20df irq:20
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:20a0-20bf irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: USB Reader
                   physical id: 2
                   bus info: usb@3:2
                   logical name: scsi5
                   version: 1.00
                   serial: 9205291
                   capabilities: usb-1.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
                 *-disk:0
                      description: SCSI Disk
                      product: USB SD Reader
                      vendor: Generic
                      physical id: 0.0.0
                      bus info: scsi@5:0.0.0
                      logical name: /dev/sdc
                      version: 1.00
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdc
                 *-disk:1
                      description: SCSI Disk
                      product: USB CF Reader
                      vendor: Generic
                      physical id: 0.0.1
                      bus info: scsi@5:0.0.1
                      logical name: /dev/sdd
                      version: 1.01
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdd
                 *-disk:2
                      description: SCSI Disk
                      product: USB SM Reader
                      vendor: Generic
                      physical id: 0.0.2
                      bus info: scsi@5:0.0.2
                      logical name: /dev/sde
                      version: 1.02
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sde
                 *-disk:3
                      description: SCSI Disk
                      product: USB MS Reader
                      vendor: Generic
                      physical id: 0.0.3
                      bus info: scsi@5:0.0.3
                      logical name: /dev/sdf
                      version: 1.03
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdf
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:2080-209f irq:22
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Printer
                   product: Samsung ML-1610 Series
                   vendor: Samsung Electronics Co., Ltd.
                   physical id: 1
                   bus info: usb@4:1
                   version: 1.00
                   serial: 3961BKEY600656Z.
                   capabilities: usb-1.10 bidirectional
                   configuration: driver=usblp maxpower=2mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:96225400-962257ff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:96220000-96223fff irq:23
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-ide
                description: IDE interface
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@03:00.0
                logical name: scsi6
                version: b1
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list scsi-host
                configuration: driver=pata_marvell latency=0
                resources: ioport:1018-101f ioport:1024-1027 ioport:1010-1017 ioport:1020-1023 ioport:1000-100f iomemory:96100000-961001ff irq:17
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:5
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:2060-207f irq:21
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:2040-205f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:2020-203f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:96225000-962253ff irq:21
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: USB 2.0 Storage Device
                   physical id: 3
                   bus info: usb@2:3
                   logical name: scsi4
                   version: 1.12
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=0mA speed=480.0MB/s
                 *-cdrom
                      description: DVD writer
                      product: DVD DD EW162I
                      vendor: BENQ
                      physical id: 0.0.0
                      bus info: scsi@4:0.0.0
                      logical name: /dev/scd2
                      logical name: /dev/sr2
                      version: 47L9
                      capabilities: removable audio cd-r cd-rw dvd dvd-r
                    *-disc
                         physical id: 0
                         logical name: /dev/scd2
        *-pci:6
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-multimedia
                description: Multimedia video controller
                product: iTVC16 (CX23416) MPEG-2 Encoder
                vendor: Internext Compression Inc
                physical id: 1
                bus info: pci@07:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128
                resources: iomemory:90000000-93ffffff irq:23
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@07:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: iomemory:96004000-960047ff iomemory:96000000-96003fff irq:19
        *-isa
             description: ISA bridge
             product: 82801HH (ICH8DH) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:2438-243f ioport:244c-244f ioport:2430-2437 ioport:2448-244b ioport:2410-241f ioport:2400-240f irq:19
           *-disk:0
                description: SCSI Disk
                product: WDC WD2000JD-22H
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 08.0
                serial: WD-WMALL1103322
                size: 186GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux swap / Solaris partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 2000MB
                   capabilities: primary nofs
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 97GB
                   capabilities: primary bootable
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 86GB
                   capabilities: primary
           *-disk:1
                description: SCSI Disk
                product: WDC WD1200JD-00G
                vendor: ATA
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/sdb
                version: 02.0
                serial: WD-WMAES4104679
                size: 111GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume
                   description: Extended partition
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   size: 111GB
                   capacity: 111GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 46GB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 64GB
        *-serial
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: iomemory:96225800-962258ff ioport:2000-201f irq:22
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:2428-242f ioport:2444-2447 ioport:2420-2427 ioport:2440-2443 ioport:20f0-20ff ioport:20e0-20ef irq:19
           *-cdrom:0
                description: DVD writer
                product: DVD-RW  DVR-212D
                vendor: PIONEER
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.09
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/scd0
           *-cdrom:1
                description: DVD writer
                product: DVD-RW  DVR-212D
                vendor: PIONEER
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.09
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
```



Here is dmesg:

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000008f000 end: 000000000008f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000008f000 size: 0000000000011000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007ec99000 end: 000000007ed99000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007ed99000 size: 000000000000d000 end: 000000007eda6000 type: 2
[    0.000000] copy_e820_map() start: 000000007eda6000 size: 0000000000070000 end: 000000007ee16000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007ee16000 size: 00000000000dc000 end: 000000007eef2000 type: 4
[    0.000000] copy_e820_map() start: 000000007eef2000 size: 0000000000001000 end: 000000007eef3000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007eef3000 size: 000000000000c000 end: 000000007eeff000 type: 3
[    0.000000] copy_e820_map() start: 000000007eeff000 size: 0000000000001000 end: 000000007ef00000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007ef00000 size: 0000000000100000 end: 000000007f000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
[    0.000000]  BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ed99000 (usable)
[    0.000000]  BIOS-e820: 000000007ed99000 - 000000007eda6000 (reserved)
[    0.000000]  BIOS-e820: 000000007eda6000 - 000000007ee16000 (usable)
[    0.000000]  BIOS-e820: 000000007ee16000 - 000000007eef2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007eef2000 - 000000007eef3000 (usable)
[    0.000000]  BIOS-e820: 000000007eef3000 - 000000007eeff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007eeff000 - 000000007ef00000 (usable)
[    0.000000]  BIOS-e820: 000000007ef00000 - 000000007f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 1135MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe660
[    0.000000] Entering add_active_range(0, 0, 519936) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   519936
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   519936
[    0.000000] On node 0 totalpages: 519936
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2270 pages used for memmap
[    0.000000]   HighMem zone: 288290 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 INTEL                                 ) @ 0x000fe020
[    0.000000] ACPI: RSDT (v001 INTEL  DG965OT  0x000006a3      0x01000013) @ 0x7eefd038
[    0.000000] ACPI: FADT (v001 INTEL  DG965OT  0x000006a3 MSFT 0x01000013) @ 0x7eefc000
[    0.000000] ACPI: MADT (v001 INTEL  DG965OT  0x000006a3 MSFT 0x01000013) @ 0x7eef6000
[    0.000000] ACPI: WDDT (v001 INTEL  DG965OT  0x000006a3 MSFT 0x01000013) @ 0x7eef5000
[    0.000000] ACPI: MCFG (v001 INTEL  DG965OT  0x000006a3 MSFT 0x01000013) @ 0x7eef4000
[    0.000000] ACPI: ASF! (v032 INTEL  DG965OT  0x000006a3 MSFT 0x01000013) @ 0x7eef3000
[    0.000000] ACPI: DSDT (v001 INTEL  DG965OT  0x000006a3 MSFT 0x01000013) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f000000:80f00000)
[    0.000000] Detected 2997.176 MHz processor.
[   18.321745] Built 1 zonelists.  Total pages: 515874
[   18.321749] Kernel command line: root=UUID=268dbad6-0863-4ae6-a0a4-77d5da1a64fc ro quiet splash
[   18.321905] mapped APIC to ffffd000 (fee00000)
[   18.321908] mapped IOAPIC to ffffc000 (fec00000)
[   18.321911] Enabling fast FPU save and restore... done.
[   18.321914] Enabling unmasked SIMD FPU exception support... done.
[   18.321922] Initializing CPU#0
[   18.321976] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   18.324134] Console: colour VGA+ 80x25
[   18.324393] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.324696] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.412544] Memory: 2049848k/2079744k available (1992k kernel code, 27600k reserved, 900k data, 328k init, 1161260k highmem)
[   18.412554] virtual kernel memory layout:
[   18.412555]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   18.412557]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.412558]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   18.412559]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   18.412560]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   18.412561]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   18.412562]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   18.412565] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.489660] Calibrating delay using timer specific routine.. 5999.50 BogoMIPS (lpj=11999000)
[   18.489702] Security Framework v1.0.0 initialized
[   18.489708] SELinux:  Disabled at boot.
[   18.489724] Mount-cache hash table entries: 512
[   18.489850] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e43d 00000000 00000001
[   18.489859] monitor/mwait feature present.
[   18.489861] using mwait in idle threads.
[   18.489867] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   18.489870] CPU: L2 cache: 2048K
[   18.489873] CPU: Physical Processor ID: 0
[   18.489875] CPU: Processor Core ID: 0
[   18.489877] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000e43d 00000000 00000001
[   18.489888] Compat vDSO mapped to ffffe000.
[   18.489891] Remapping vsyscall page to ffffe000
[   18.489906] Checking 'hlt' instruction... OK.
[   18.505714] SMP alternatives: switching to UP code
[   18.506054] Early unpacking initramfs... done
[   18.780058] ACPI: Core revision 20060707
[   18.781393] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.783932] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 02
[   18.783954] SMP alternatives: switching to SMP code
[   18.784041] Booting processor 1/1 eip 3000
[   18.794476] Initializing CPU#1
[   18.872922] Calibrating delay using timer specific routine.. 5994.53 BogoMIPS (lpj=11989079)
[   18.872931] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e43d 00000000 00000001
[   18.872937] monitor/mwait feature present.
[   18.872942] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   18.872944] CPU: L2 cache: 2048K
[   18.872947] CPU: Physical Processor ID: 0
[   18.872948] CPU: Processor Core ID: 1
[   18.872950] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000e43d 00000000 00000001
[   18.873401] CPU1: Intel(R) Pentium(R) D CPU 3.00GHz stepping 02
[   18.873435] Total of 2 processors activated (11994.03 BogoMIPS).
[   18.873581] ENABLING IO-APIC IRQs
[   18.873753] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   19.020650] checking TSC synchronization across 2 CPUs: passed.
[    0.003993] Brought up 2 CPUs
[    0.245898] migration_cost=843
[    0.246168] Booting paravirtualized kernel on bare hardware
[    0.246243] Time:  1:29:07  Date: 07/25/107
[    0.246273] NET: Registered protocol family 16
[    0.246361] EISA bus registered
[    0.246366] ACPI: bus type pci registered
[    0.248895] PCI: Using configuration type 1
[    0.248897] Setting up standard PCI resources
[    0.261747] ACPI: Interpreter enabled
[    0.261750] ACPI: Using IOAPIC for interrupt routing
[    0.262225] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.262234] PCI: Probing PCI hardware (bus 00)
[    0.262252] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.264258] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.264263] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[    0.264486] Boot video device is 0000:01:00.0
[    0.265199] PCI: Transparent bridge - 0000:00:1e.0
[    0.265289] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.271081] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.271843] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.272091] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.272333] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.272573] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.272823] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12)
[    0.273065] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.273311] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.273554] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.275236] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.275511] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.275758] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.276006] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.276256] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.277811] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.277821] pnp: PnP ACPI init
[    0.280958] pnp: PnP ACPI: found 12 devices
[    0.280962] PnPBIOS: Disabled by ACPI PNP
[    0.281009] PCI: Using ACPI for IRQ routing
[    0.281012] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.281114] NET: Registered protocol family 8
[    0.281117] NET: Registered protocol family 20
[    0.281203] pnp: 00:06: ioport range 0x500-0x53f has been reserved
[    0.281207] pnp: 00:06: ioport range 0x400-0x47f could not be reserved
[    0.281209] pnp: 00:06: ioport range 0x680-0x6ff has been reserved
[    0.281544] PCI: Failed to allocate mem resource #6:20000@90000000 for 0000:01:00.0
[    0.281588] PCI: Bridge: 0000:00:01.0
[    0.281590]   IO window: disabled.
[    0.281594]   MEM window: 94000000-95ffffff
[    0.281599]   PREFETCH window: 80000000-8fffffff
[    0.281604] PCI: Bridge: 0000:00:1c.0
[    0.281606]   IO window: disabled.
[    0.281611]   MEM window: disabled.
[    0.281615]   PREFETCH window: disabled.
[    0.281621] PCI: Bridge: 0000:00:1c.1
[    0.281625]   IO window: 1000-1fff
[    0.281630]   MEM window: 96100000-961fffff
[    0.281634]   PREFETCH window: disabled.
[    0.281640] PCI: Bridge: 0000:00:1c.2
[    0.281642]   IO window: disabled.
[    0.281647]   MEM window: disabled.
[    0.281651]   PREFETCH window: disabled.
[    0.281657] PCI: Bridge: 0000:00:1c.3
[    0.281659]   IO window: disabled.
[    0.281664]   MEM window: disabled.
[    0.281668]   PREFETCH window: disabled.
[    0.281674] PCI: Bridge: 0000:00:1c.4
[    0.281676]   IO window: disabled.
[    0.281681]   MEM window: disabled.
[    0.281685]   PREFETCH window: disabled.
[    0.281691] PCI: Bridge: 0000:00:1e.0
[    0.281693]   IO window: disabled.
[    0.281699]   MEM window: 96000000-960fffff
[    0.281703]   PREFETCH window: 90000000-93ffffff
[    0.281721] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.281727] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.281745] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[    0.281751] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.281768] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[    0.281774] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.281792] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.281797] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.281816] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[    0.281821] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.281838] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[    0.281844] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.281854] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.281888] NET: Registered protocol family 2
[    0.319426] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.319544] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.320117] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.320404] TCP: Hash tables configured (established 131072 bind 65536)
[    0.320407] TCP reno registered
[    0.331486] checking if image is initramfs... it is
[    0.866806] Freeing initrd memory: 6791k freed
[    0.867403] audit: initializing netlink socket (disabled)
[    0.867417] audit(1188005347.652:1): initialized
[    0.867529] highmem bounce pool size: 64 pages
[    0.867625] VFS: Disk quotas dquot_6.5.1
[    0.867644] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.867690] io scheduler noop registered
[    0.867694] io scheduler anticipatory registered
[    0.867696] io scheduler deadline registered
[    0.867710] io scheduler cfq registered (default)
[    0.868178] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.868220] assign_interrupt_mode Found MSI capability
[    0.868223] Allocate Port Service[0000:00:01.0:pcie00]
[    0.868323] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.868366] assign_interrupt_mode Found MSI capability
[    0.868369] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.868411] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.868516] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.868559] assign_interrupt_mode Found MSI capability
[    0.868561] Allocate Port Service[0000:00:1c.1:pcie00]
[    0.868602] Allocate Port Service[0000:00:1c.1:pcie02]
[    0.868709] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.868752] assign_interrupt_mode Found MSI capability
[    0.868754] Allocate Port Service[0000:00:1c.2:pcie00]
[    0.868792] Allocate Port Service[0000:00:1c.2:pcie02]
[    0.868898] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.868941] assign_interrupt_mode Found MSI capability
[    0.868943] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.868983] Allocate Port Service[0000:00:1c.3:pcie02]
[    0.869089] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.869132] assign_interrupt_mode Found MSI capability
[    0.869135] Allocate Port Service[0000:00:1c.4:pcie00]
[    0.869173] Allocate Port Service[0000:00:1c.4:pcie02]
[    0.869348] isapnp: Scanning for PnP cards...
[    1.220343] isapnp: No Plug & Play device found
[    1.248014] Real Time Clock Driver v1.12ac
[    1.248069] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.248189] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.248845] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.249046] mice: PS/2 mouse device common for all mice
[    1.249701] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.249849] input: Macintosh mouse button emulation as /class/input/input0
[    1.249892] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.249896] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.250102] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.253027] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.253032] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.253130] EISA: Probing bus 0 at eisa.0
[    1.253137] Cannot allocate resource for EISA slot 1
[    1.253139] Cannot allocate resource for EISA slot 2
[    1.253161] EISA: Detected 0 cards.
[    1.271785] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.283179] TCP cubic registered
[    1.283188] NET: Registered protocol family 1
[    1.283211] Starting balanced_irq
[    1.283226] Using IPI No-Shortcut mode
[    1.283297] ACPI: (supports S0 S3 S4 S5)
[    1.283340]   Magic number: 3:918:458
[    1.283554] Freeing unused kernel memory: 328k freed
[    1.285518] Time: tsc clocksource has been installed.
[    2.494769] Capability LSM initialized
[    2.532515] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.532535] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.532545] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.532553] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.904607] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[    2.904611] Copyright (c) 1999-2006 Intel Corporation.
[    2.904652] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 20
[    2.904665] PCI: Setting latency timer of device 0000:00:19.0 to 64
[    2.919456] usbcore: registered new interface driver usbfs
[    2.919479] usbcore: registered new interface driver hub
[    2.932040] usbcore: registered new device driver usb
[    2.951195] USB Universal Host Controller Interface driver v3.0
[    2.951941] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:16:76:e1:92:0b
[    3.022483] ieee1394: Initialized config rom entry `ip1394'
[    3.083927] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.083969] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[    3.083986] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    3.083990] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.084101] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.084131] ehci_hcd 0000:00:1a.7: debug port 1
[    3.084138] PCI: cache line size of 128 is not supported by device 0000:00:1a.7
[    3.084149] ehci_hcd 0000:00:1a.7: irq 18, io mem 0x96225400
[    3.088011] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.088104] usb usb1: configuration #1 chosen from 1 choice
[    3.088132] hub 1-0:1.0: USB hub found
[    3.088139] hub 1-0:1.0: 4 ports detected
[    3.193907] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[    3.193917] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.193921] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.193944] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.193976] ehci_hcd 0000:00:1d.7: debug port 1
[    3.193982] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    3.193990] ehci_hcd 0000:00:1d.7: irq 21, io mem 0x96225000
[    3.197869] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.197936] usb usb2: configuration #1 chosen from 1 choice
[    3.197962] hub 2-0:1.0: USB hub found
[    3.197969] hub 2-0:1.0: 6 ports detected
[    3.305746] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.305756] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    3.305759] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.305781] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.305807] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000020a0
[    3.305892] usb usb3: configuration #1 chosen from 1 choice
[    3.305920] hub 3-0:1.0: USB hub found
[    3.305926] hub 3-0:1.0: 2 ports detected
[    3.413479] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 22
[    3.413489] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    3.413493] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.413517] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.413543] uhci_hcd 0000:00:1a.1: irq 22, io base 0x00002080
[    3.413630] usb usb4: configuration #1 chosen from 1 choice
[    3.413659] hub 4-0:1.0: USB hub found
[    3.413665] hub 4-0:1.0: 2 ports detected
[    3.521419] ACPI: PCI Interrupt 0000:07:03.0[A] -> GSI 19 (level, low) -> IRQ 19
[    3.571112] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[96004000-960047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.571177] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
[    3.571191] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.571195] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.571222] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.571246] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00002060
[    3.571340] usb usb5: configuration #1 chosen from 1 choice
[    3.571366] hub 5-0:1.0: USB hub found
[    3.571373] hub 5-0:1.0: 2 ports detected
[    3.676945] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    3.676955] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.676959] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.676981] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.677004] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002040
[    3.677095] usb usb6: configuration #1 chosen from 1 choice
[    3.677122] hub 6-0:1.0: USB hub found
[    3.677128] hub 6-0:1.0: 2 ports detected
[    3.784738] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.784747] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.784751] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.784774] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.784797] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002020
[    3.784883] usb usb7: configuration #1 chosen from 1 choice
[    3.784909] hub 7-0:1.0: USB hub found
[    3.784916] hub 7-0:1.0: 2 ports detected
[    3.816597] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    3.898495] SCSI subsystem initialized
[    3.903738] libata version 2.20 loaded.
[    3.907337] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.907344] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.907370] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 19 (level, low) -> IRQ 19
[    3.907388] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.907449] ata1: SATA max UDMA/133 cmd 0x00012438 ctl 0x0001244e bmdma 0x00012410 irq 19
[    3.907479] ata2: SATA max UDMA/133 cmd 0x00012430 ctl 0x0001244a bmdma 0x00012418 irq 19
[    3.907488] scsi0 : ata_piix
[    3.962967] usb 2-3: configuration #1 chosen from 1 choice
[    4.077584] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    4.077589] ata1.00: ATA-6: WDC WD2000JD-22HBB0, 08.02D08, max UDMA/133
[    4.077593] ata1.00: 390721968 sectors, multi 16: LBA48 
[    4.089570] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    4.089574] ata1.00: configured for UDMA/133
[    4.089585] scsi1 : ata_piix
[    4.203846] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    4.257906] ATA: abnormal status 0x7F on port 0x00012437
[    4.268032] ATA: abnormal status 0x7F on port 0x00012437
[    4.281329] ata2.01: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    4.281333] ata2.01: ATA-6: WDC WD1200JD-00GBB0, 02.05D02, max UDMA/100
[    4.281336] ata2.01: 234441648 sectors, multi 16: LBA48 
[    4.281338] ata2.01: applying bridge limits
[    4.293335] ata2.01: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    4.293339] ata2.01: configured for UDMA/100
[    4.293443] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2000JD-22H 08.0 PQ: 0 ANSI: 5
[    4.293632] scsi 1:0:1:0: Direct-Access     ATA      WDC WD1200JD-00G 02.0 PQ: 0 ANSI: 5
[    4.293747] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[    4.293773] ACPI: PCI Interrupt 0000:00:1f.5[A] -> GSI 19 (level, low) -> IRQ 19
[    4.293790] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    4.293818] ata3: SATA max UDMA/133 cmd 0x00012428 ctl 0x00012446 bmdma 0x000120f0 irq 19
[    4.293843] ata4: SATA max UDMA/133 cmd 0x00012420 ctl 0x00012442 bmdma 0x000120f8 irq 19
[    4.293851] scsi2 : ata_piix
[    4.388770] usb 3-2: configuration #1 chosen from 1 choice
[    4.635008] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    4.778905] ata3.00: ATAPI, max UDMA/66
[    4.817865] usb 4-1: configuration #1 chosen from 1 choice
[    4.846748] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090270001bb2468]
[    4.950466] usbcore: registered new interface driver libusual
[    4.950633] ata3.00: configured for UDMA/66
[    4.950663] scsi3 : ata_piix
[    4.954151] Initializing USB Mass Storage driver...
[    4.954226] scsi4 : SCSI emulation for USB Mass Storage devices
[    4.954281] usb-storage: device found at 2
[    4.954284] usb-storage: waiting for device to settle before scanning
[    4.954326] scsi5 : SCSI emulation for USB Mass Storage devices
[    4.954369] usb-storage: device found at 2
[    4.954371] usb-storage: waiting for device to settle before scanning
[    4.954376] usbcore: registered new interface driver usb-storage
[    4.954379] USB Mass Storage support registered.
[    5.437632] ata4.00: ATAPI, max UDMA/66
[    5.609302] ata4.00: configured for UDMA/66
[    5.615289] scsi 2:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-212D 1.09 PQ: 0 ANSI: 5
[    5.621775] scsi 3:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-212D 1.09 PQ: 0 ANSI: 5
[    5.622110] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    5.622275] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    5.622311] ata5: PATA max UDMA/100 cmd 0x00011018 ctl 0x00011026 bmdma 0x00011000 irq 17
[    5.622326] scsi6 : pata_marvell
[    5.622385] BAR5:00:00 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:01 0D:00 0E:00 0F:00 
[    5.630430] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    5.630447] sda: Write Protect is off
[    5.630450] sda: Mode Sense: 00 3a 00 00
[    5.630470] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.630519] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    5.630531] sda: Write Protect is off
[    5.630534] sda: Mode Sense: 00 3a 00 00
[    5.630553] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.630556]  sda: sda1 sda2 sda3
[    5.651555] sd 0:0:0:0: Attached scsi disk sda
[    5.651619] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
[    5.651633] sdb: Write Protect is off
[    5.651636] sdb: Mode Sense: 00 3a 00 00
[    5.651656] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.651701] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
[    5.651716] sdb: Write Protect is off
[    5.651719] sdb: Mode Sense: 00 3a 00 00
[    5.651738] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.651741]  sdb: sdb1 < sdb5 sdb6 >
[    5.696981] sd 1:0:1:0: Attached scsi disk sdb
[    5.700775] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.700796] sd 1:0:1:0: Attached scsi generic sg1 type 0
[    5.700815] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    5.700836] scsi 3:0:0:0: Attached scsi generic sg3 type 5
[    5.731152] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    5.731157] Uniform CD-ROM driver Revision: 3.20
[    5.731208] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    5.761511] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    5.761553] sr 3:0:0:0: Attached scsi CD-ROM sr1
[    5.790946] ATA: abnormal status 0x8 on port 0x0001101f
[    5.893391] Attempting manual resume
[    5.893395] swsusp: Resume From Partition 8:1
[    5.893397] PM: Checking swsusp image.
[    5.893530] PM: Resume from disk failed.
[    5.930013] kjournald starting.  Commit interval 5 seconds
[    5.930020] EXT3-fs: mounted filesystem with ordered data mode.
[    9.944960] usb-storage: device scan complete
[    9.946709] scsi 4:0:0:0: CD-ROM            BENQ     DVD DD EW162I    47L9 PQ: 0 ANSI: 0
[    9.946730] usb-storage: device scan complete
[    9.949717] scsi 5:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    9.952721] scsi 5:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    9.955711] scsi 5:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    9.958705] scsi 5:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    9.961160] sr2: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    9.961201] sr 4:0:0:0: Attached scsi CD-ROM sr2
[    9.961241] sr 4:0:0:0: Attached scsi generic sg4 type 5
[   10.004631] sd 5:0:0:0: Attached scsi removable disk sdc
[   10.004666] sd 5:0:0:0: Attached scsi generic sg5 type 0
[   10.047542] sd 5:0:0:1: Attached scsi removable disk sdd
[   10.047577] sd 5:0:0:1: Attached scsi generic sg6 type 0
[   10.090457] sd 5:0:0:2: Attached scsi removable disk sde
[   10.090492] sd 5:0:0:2: Attached scsi generic sg7 type 0
[   10.133372] sd 5:0:0:3: Attached scsi removable disk sdf
[   10.133405] sd 5:0:0:3: Attached scsi generic sg8 type 0
[   14.787579] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[   14.795691] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[   14.795696] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   15.639522] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.641193] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.998987] Linux agpgart interface v0.102 (c) Dave Jones
[   16.025910] iTCO_vendor_support: vendor-support=0
[   16.049787] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   16.049882] iTCO_wdt: Found a ICH8DH TCO device (Version=2, TCOBASE=0x0460)
[   16.049928] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.065960] Linux video capture interface: v2.00
[   16.316047] nvidia: module license 'NVIDIA' taints kernel.
[   16.401527] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04E8 pid 0x3268
[   16.401541] usbcore: registered new interface driver usblp
[   16.401544] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   16.566806] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.566816] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   16.566947] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   16.581927] parport: PnPBIOS parport detected.
[   16.582007] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   16.598071] agpgart: Detected an Intel 965G Chipset.
[   16.614499] agpgart: AGP aperture is 256M @ 0x0
[   16.615300] input: PC Speaker as /class/input/input2
[   16.643587] NET: Registered protocol family 17
[   16.719658] ivtv:  ==================== START INIT IVTV ====================
[   16.719664] ivtv:  version 0.10.1 (tagged release) loading
[   16.719666] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   16.719668] ivtv:  In case of problems please include the debug info between
[   16.719671] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   16.719673] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   16.719781] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   16.719861] ACPI: PCI Interrupt 0000:07:01.0[A] -> GSI 22 (level, low) -> IRQ 23
[   16.719874] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   16.893711] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   16.893733] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   16.896761] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   17.394654] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   17.613857] ivtv0: Encoder revision: 0x02050032
[   17.613861] ivtv0: Recommended firmware version is 0x02060039.
[   17.675814] tveeprom 0-0050: Hauppauge model 26552, rev C268, serial# 7716817
[   17.675818] tveeprom 0-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   17.675822] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   17.675824] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   17.675826] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   17.675829] tveeprom 0-0050: has radio, has no IR receiver, has no IR transmitter
[   17.675832] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   17.699421] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   17.699457] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   17.703797] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   17.750678] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   22.585971] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   22.712276] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   22.776905] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   22.777110] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   22.777350] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   22.777456] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   22.777712] ivtv0: Registered device radio0 for encoder radio
[   22.777727] tuner 0-0061: type set to 47 (LG NTSC (TAPE series))
[   23.169601] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   23.169622] ivtv:  ====================  END INIT IVTV  ====================
[   23.291562] fuse init (API version 7.8)
[   23.308666] lp0: using parport0 (interrupt-driven).
[   23.336110] ACPI: PCI Interrupt 0000:00:1f.3[B] -> GSI 21 (level, low) -> IRQ 22
[   23.500704] Adding 2048248k swap on /dev/disk/by-uuid/145882b2-46d1-4b93-9c0a-f91b3236da5b.  Priority:-1 extents:1 across:2048248k
[  194.136603] EXT3 FS on sda2, internal journal
[  194.505489] NET: Registered protocol family 10
[  194.505591] lo: Disabled Privacy Extensions
[  194.605869] kjournald starting.  Commit interval 5 seconds
[  194.606256] EXT3 FS on sda3, internal journal
[  194.606262] EXT3-fs: mounted filesystem with ordered data mode.
[  194.614283] kjournald starting.  Commit interval 5 seconds
[  194.614744] EXT3 FS on sdb5, internal journal
[  194.614749] EXT3-fs: mounted filesystem with ordered data mode.
[  194.616328] kjournald starting.  Commit interval 5 seconds
[  194.616778] EXT3 FS on sdb6, internal journal
[  194.616782] EXT3-fs: mounted filesystem with ordered data mode.
[  200.862785] No dock devices found.
[  200.887680] input: Power Button (FF) as /class/input/input4
[  200.887830] ACPI: Power Button (FF) [PWRF]
[  200.888620] input: Sleep Button (CM) as /class/input/input5
[  200.888756] ACPI: Sleep Button (CM) [SLPB]
[  200.933533] ibm_acpi: ec object not found
[  200.985728] Using specific hotkey driver
[  201.132223] pcc_acpi: loading...
[  205.110208] eth0: no IPv6 routers present
[  205.596075] ppdev: user-space parallel port driver
[  206.847362] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  206.847368] apm: disabled - APM is not SMP safe.
[  208.121918] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  208.186184] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  208.186211] NFSD: starting 90-second grace period
[  208.894833] vboxdrv: Trying to deactivate NMI watchdog permanently...
[  208.894839] vboxdrv: Successfully done.
[  221.382648] eth0: no IPv6 routers present
[  226.664297] cramfs: wrong magic
[  226.666051] attempt to access beyond end of device
[  226.666057] sdb1: rw=0, want=4, limit=2
[  226.666247] EXT3-fs: unable to read superblock
[  274.456344] cdrom: This disc doesn't have any tracks I recognize!
[  338.893974] cdrom: This disc doesn't have any tracks I recognize!
[14437.435950] /dev/vmmon[22327]: Module vmmon: registered with major=10 minor=165
[14437.436245] /dev/vmmon[22327]: Module vmmon: initialized
[14437.475615] /dev/vmnet: open called by PID 22355 (vmnet-bridge)
[14437.475627] /dev/vmnet: hub 0 does not exist, allocating memory.
[14437.475639] /dev/vmnet: port on hub 0 successfully opened
[14437.475654] bridge-eth0: enabling the bridge
[14437.475660] bridge-eth0: up
[14437.475663] bridge-eth0: already up
[14437.475667] bridge-eth0: attached
[14437.481654] /dev/vmnet: open called by PID 22367 (vmnet-natd)
[14437.481887] /dev/vmnet: hub 8 does not exist, allocating memory.
[14437.482165] /dev/vmnet: port on hub 8 successfully opened
[14447.457704] /dev/vmnet: open called by PID 22389 (vmnet-netifup)
[14447.457719] /dev/vmnet: hub 1 does not exist, allocating memory.
[14447.457733] /dev/vmnet: port on hub 1 successfully opened
[14447.465351] /dev/vmnet: open called by PID 22398 (vmnet-netifup)
[14447.465364] /dev/vmnet: port on hub 8 successfully opened
[14447.491813] /dev/vmnet: open called by PID 22412 (vmnet-dhcpd)
[14447.491825] /dev/vmnet: port on hub 8 successfully opened
[14447.492713] /dev/vmnet: open called by PID 22410 (vmnet-dhcpd)
[14447.493006] /dev/vmnet: port on hub 1 successfully opened
[14457.736963] vmnet1: no IPv6 routers present
[14458.052353] vmnet8: no IPv6 routers present
[14839.358522] /dev/vmnet: open called by PID 22938 (vmware-vmx)
[14839.358579] device eth0 entered promiscuous mode
[14839.358587] audit(1188020215.109:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
[14839.358591] bridge-eth0: enabled promiscuous mode
[14839.358593] /dev/vmnet: port on hub 0 successfully opened
[14839.606702] /dev/vmmon[22951]: host clock rate change request 0 -> 19
[14847.926889] ISO 9660 Extensions: Microsoft Joliet Level 3
[14848.171657] ISO 9660 Extensions: RRIP_1991A
[14858.485402] device eth0 left promiscuous mode
[14858.485414] audit(1188020234.266:3): dev=eth0 prom=0 old_prom=256 auid=4294967295
[14858.485418] bridge-eth0: disabled promiscuous mode
[14858.498641] /dev/vmmon[22938]: host clock rate change request 19 -> 0
[14858.502720] vmmon: Had to deallocate locked 1268 pages from vm driver dd5ec000
[14858.506594] vmmon: Had to deallocate AWE 2469 pages from vm driver dd5ec000
[14858.787001] /dev/vmnet: open called by PID 22938 (vmware-vmx)
[14858.787057] device eth0 entered promiscuous mode
[14858.787065] audit(1188020234.570:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
[14858.787068] bridge-eth0: enabled promiscuous mode
[14858.787071] /dev/vmnet: port on hub 0 successfully opened
[14859.045132] /dev/vmmon[23010]: host clock rate change request 0 -> 19
[14878.700256] device eth0 left promiscuous mode
[14878.700267] audit(1188020254.524:5): dev=eth0 prom=0 old_prom=256 auid=4294967295
[14878.700270] bridge-eth0: disabled promiscuous mode
[14878.712676] /dev/vmmon[22938]: host clock rate change request 19 -> 0
[14878.715140] vmmon: Had to deallocate locked 1268 pages from vm driver dd5ec000
[14878.718988] vmmon: Had to deallocate AWE 2470 pages from vm driver dd5ec000
[14878.964334] /dev/vmnet: open called by PID 22938 (vmware-vmx)
[14878.964399] device eth0 entered promiscuous mode
[14878.964409] audit(1188020254.788:6): dev=eth0 prom=256 old_prom=0 auid=4294967295
[14878.964414] bridge-eth0: enabled promiscuous mode
[14878.964418] /dev/vmnet: port on hub 0 successfully opened
[14879.263372] /dev/vmmon[23056]: host clock rate change request 0 -> 19
[14891.784355] device eth0 left promiscuous mode
[14891.784366] audit(1188020267.632:7): dev=eth0 prom=0 old_prom=256 auid=4294967295
[14891.784370] bridge-eth0: disabled promiscuous mode
[14891.796656] /dev/vmmon[22938]: host clock rate change request 19 -> 0
[14891.799291] vmmon: Had to deallocate locked 1272 pages from vm driver eaf49000
[14891.803404] vmmon: Had to deallocate AWE 2406 pages from vm driver eaf49000
[14892.043299] /dev/vmnet: open called by PID 22938 (vmware-vmx)
[14892.043356] device eth0 entered promiscuous mode
[14892.043364] audit(1188020267.892:8): dev=eth0 prom=256 old_prom=0 auid=4294967295
[14892.043367] bridge-eth0: enabled promiscuous mode
[14892.043370] /dev/vmnet: port on hub 0 successfully opened
[14892.293043] /dev/vmmon[23084]: host clock rate change request 0 -> 19
[14912.009537] device eth0 left promiscuous mode
[14912.009548] audit(1188020287.893:9): dev=eth0 prom=0 old_prom=256 auid=4294967295
[14912.009552] bridge-eth0: disabled promiscuous mode
[14912.022113] /dev/vmmon[22938]: host clock rate change request 19 -> 0
[14912.026166] vmmon: Had to deallocate locked 1268 pages from vm driver eaf49000
[14912.030341] vmmon: Had to deallocate AWE 2469 pages from vm driver eaf49000
[14973.743628] /dev/vmnet: open called by PID 23192 (vmware-vmx)
[14973.743689] device eth0 entered promiscuous mode
[14973.743699] audit(1188020349.749:10): dev=eth0 prom=256 old_prom=0 auid=4294967295
[14973.743703] bridge-eth0: enabled promiscuous mode
[14973.743707] /dev/vmnet: port on hub 0 successfully opened
[14973.815694] /dev/vmmon[23204]: host clock rate change request 0 -> 19
[15007.649477] /dev/vmmon[23204]: host clock rate change request 19 -> 0
[15007.649605] /dev/vmmon[23204]: host clock rate change request 0 -> 1001
[15022.957391] /dev/vmmon[23204]: host clock rate change request 1001 -> 0
[15022.958028] /dev/vmmon[23204]: host clock rate change request 0 -> 1008
[15047.427669] /dev/vmmon[23204]: host clock rate change request 1008 -> 1009
[15058.048606] /dev/vmmon[23204]: host clock rate change request 1009 -> 1008
[15282.577430] /dev/vmmon[23204]: host clock rate change request 1008 -> 1009
[15292.558339] /dev/vmmon[23204]: host clock rate change request 1009 -> 1008
[15449.567625] device eth0 left promiscuous mode
[15449.567637] audit(1188020826.489:11): dev=eth0 prom=0 old_prom=256 auid=4294967295
[15449.567640] bridge-eth0: disabled promiscuous mode
[15449.720501] /dev/vmmon[23192]: host clock rate change request 1008 -> 0
[15449.758857] vmmon: Had to deallocate locked 111648 pages from vm driver efb4f000
[15449.763611] vmmon: Had to deallocate AWE 4093 pages from vm driver efb4f000
[16071.509209] /dev/vmnet: open called by PID 24339 (vmware-vmx)
[16071.509265] device eth0 entered promiscuous mode
[16071.509273] audit(1188021449.624:12): dev=eth0 prom=256 old_prom=0 auid=4294967295
[16071.509276] bridge-eth0: enabled promiscuous mode
[16071.509278] /dev/vmnet: port on hub 0 successfully opened
[16071.567226] /dev/vmmon[24351]: host clock rate change request 0 -> 19
[16116.512452] /dev/vmmon[24351]: host clock rate change request 19 -> 0
[16116.512562] /dev/vmmon[24351]: host clock rate change request 0 -> 1001
[16131.811611] /dev/vmmon[24351]: host clock rate change request 1001 -> 0
[16131.812690] /dev/vmmon[24351]: host clock rate change request 0 -> 993
[16156.590330] /dev/vmmon[24351]: host clock rate change request 993 -> 994
[16166.730888] /dev/vmmon[24351]: host clock rate change request 994 -> 993
[16471.290467] device eth0 left promiscuous mode
[16471.290478] audit(1188021850.176:13): dev=eth0 prom=0 old_prom=256 auid=4294967295
[16471.290481] bridge-eth0: disabled promiscuous mode
[16471.457870] /dev/vmmon[24339]: host clock rate change request 993 -> 0
[16471.500838] vmmon: Had to deallocate locked 127668 pages from vm driver d0538000
[16471.505328] vmmon: Had to deallocate AWE 4475 pages from vm driver d0538000
[17089.099536] /dev/vmnet: open called by PID 25414 (vmware-vmx)
[17089.099597] device eth0 entered promiscuous mode
[17089.099605] audit(1188022469.171:14): dev=eth0 prom=256 old_prom=0 auid=4294967295
[17089.099608] bridge-eth0: enabled promiscuous mode
[17089.099612] /dev/vmnet: port on hub 0 successfully opened
[17089.271112] /dev/vmmon[25424]: host clock rate change request 0 -> 19
[17132.641173] /dev/vmmon[25424]: host clock rate change request 19 -> 0
[17132.641282] /dev/vmmon[25424]: host clock rate change request 0 -> 1001
[17147.989604] /dev/vmmon[25424]: host clock rate change request 1001 -> 0
[17147.990637] /dev/vmmon[25424]: host clock rate change request 0 -> 997
[17148.011212] /dev/vmmon[25426]: host clock rate change request 997 -> 1993
[17175.624323] /dev/vmmon[25424]: host clock rate change request 1993 -> 1994
[17185.840590] /dev/vmmon[25426]: host clock rate change request 1994 -> 1993
[20848.606660] usb 1-1: new high speed USB device using ehci_hcd and address 4
[20848.740133] usb 1-1: configuration #1 chosen from 1 choice
[20848.740262] scsi7 : SCSI emulation for USB Mass Storage devices
[20848.740417] usb-storage: device found at 4
[20848.740420] usb-storage: waiting for device to settle before scanning
[20853.732823] usb-storage: device scan complete
[20853.733573] scsi 7:0:0:0: Direct-Access     Generic  USB Flash Disk   0.00 PQ: 0 ANSI: 2
[20853.735048] SCSI device sdg: 4030463 512-byte hdwr sectors (2064 MB)
[20853.735671] sdg: Write Protect is off
[20853.735675] sdg: Mode Sense: 00 00 00 00
[20853.735677] sdg: assuming drive cache: write through
[20853.738877] SCSI device sdg: 4030463 512-byte hdwr sectors (2064 MB)
[20853.739850] sdg: Write Protect is off
[20853.739855] sdg: Mode Sense: 00 00 00 00
[20853.739857] sdg: assuming drive cache: write through
[20853.739861]  sdg: sdg1
[20853.850086] sd 7:0:0:0: Attached scsi removable disk sdg
[20853.850141] sd 7:0:0:0: Attached scsi generic sg9 type 0
[21367.934327] /dev/vmmon[25424]: host clock rate change request 1993 -> 997
[21367.934487] /dev/vmmon[25426]: host clock rate change request 997 -> 0
[21367.950036] /dev/vmmon[25424]: host clock rate change request 0 -> 19
[21377.457121] /dev/vmmon[25424]: host clock rate change request 19 -> 1001
[21395.295142] /dev/vmmon[25424]: host clock rate change request 1001 -> 0
[21395.296101] /dev/vmmon[25424]: host clock rate change request 0 -> 998
[21395.323130] /dev/vmmon[25426]: host clock rate change request 998 -> 1995
[21422.595944] /dev/vmmon[25424]: host clock rate change request 1995 -> 1996
[21432.729117] /dev/vmmon[25426]: host clock rate change request 1996 -> 1995
[21614.433653] device eth0 left promiscuous mode
[21614.433665] audit(1188027003.205:15): dev=eth0 prom=0 old_prom=256 auid=4294967295
[21614.433669] bridge-eth0: disabled promiscuous mode
[21615.041496] /dev/vmmon[25414]: host clock rate change request 1995 -> 0
[21615.084230] vmmon: Had to deallocate locked 128516 pages from vm driver c328d000
[21615.089518] vmmon: Had to deallocate AWE 6612 pages from vm driver c328d000
[21631.587035] /dev/vmnet: open called by PID 30234 (vmware-vmx)
[21631.587096] device eth0 entered promiscuous mode
[21631.587103] audit(1188027020.386:16): dev=eth0 prom=256 old_prom=0 auid=4294967295
[21631.587106] bridge-eth0: enabled promiscuous mode
[21631.587111] /dev/vmnet: port on hub 0 successfully opened
[21632.110882] /dev/vmmon[30244]: host clock rate change request 0 -> 19
[21643.886992] /dev/vmmon[30244]: host clock rate change request 19 -> 0
[21643.887381] /dev/vmmon[30244]: host clock rate change request 0 -> 1001
[21659.243820] /dev/vmmon[30244]: host clock rate change request 1001 -> 0
[21659.244795] /dev/vmmon[30244]: host clock rate change request 0 -> 1007
[21659.265622] /dev/vmmon[30247]: host clock rate change request 1007 -> 2013
[21687.488015] /dev/vmmon[30244]: host clock rate change request 2013 -> 2014
[21698.303035] /dev/vmmon[30244]: host clock rate change request 2014 -> 2013
[21996.880739] device eth0 left promiscuous mode
[21996.880752] audit(1188027386.383:17): dev=eth0 prom=0 old_prom=256 auid=4294967295
[21996.880755] bridge-eth0: disabled promiscuous mode
[21996.991926] /dev/vmmon[30234]: host clock rate change request 2013 -> 0
[21997.019008] vmmon: Had to deallocate locked 77109 pages from vm driver c49c9000
[21997.024226] vmmon: Had to deallocate AWE 8096 pages from vm driver c49c9000
[23053.400919] loop: loaded (max 8 devices)
[23065.880182] ISO 9660 Extensions: Microsoft Joliet Level 3
[23065.880220] ISO 9660 Extensions: RRIP_1991A
[23134.975492] FAT: invalid media value (0x01)
[23134.975499] VFS: Can't find a valid FAT filesystem on dev sdg.
[23159.238887] FAT: invalid media value (0x01)
[23159.238894] VFS: Can't find a valid FAT filesystem on dev sdg.
[23680.786004] usb 1-1: USB disconnect, address 4
[23690.822520] usb 1-1: new high speed USB device using ehci_hcd and address 5
[23690.956083] usb 1-1: configuration #1 chosen from 1 choice
[23690.956202] scsi8 : SCSI emulation for USB Mass Storage devices
[23690.956351] usb-storage: device found at 5
[23690.956353] usb-storage: waiting for device to settle before scanning
[23695.944652] usb-storage: device scan complete
[23695.945406] scsi 8:0:0:0: Direct-Access     Generic  USB Flash Disk   0.00 PQ: 0 ANSI: 2
[23695.946755] SCSI device sdg: 4030463 512-byte hdwr sectors (2064 MB)
[23695.947379] sdg: Write Protect is off
[23695.947382] sdg: Mode Sense: 00 00 00 00
[23695.947385] sdg: assuming drive cache: write through
[23695.949499] SCSI device sdg: 4030463 512-byte hdwr sectors (2064 MB)
[23695.950123] sdg: Write Protect is off
[23695.950126] sdg: Mode Sense: 00 00 00 00
[23695.950128] sdg: assuming drive cache: write through
[23695.950130]  sdg: sdg1 sdg2
[23696.059504] sd 8:0:0:0: Attached scsi removable disk sdg
[23696.059551] sd 8:0:0:0: Attached scsi generic sg9 type 0
[23757.740755] usb 1-1: USB disconnect, address 5
[57474.894399] usb 1-1: new high speed USB device using ehci_hcd and address 6
[57475.027984] usb 1-1: configuration #1 chosen from 1 choice
[57475.028283] scsi9 : SCSI emulation for USB Mass Storage devices
[57475.028500] usb-storage: device found at 6
[57475.028505] usb-storage: waiting for device to settle before scanning
[57480.020553] usb-storage: device scan complete
[57480.021302] scsi 9:0:0:0: Direct-Access     Generic  USB Flash Disk   0.00 PQ: 0 ANSI: 2
[57480.022774] SCSI device sdg: 4030463 512-byte hdwr sectors (2064 MB)
[57480.023397] sdg: Write Protect is off
[57480.023400] sdg: Mode Sense: 00 00 00 00
[57480.023403] sdg: assuming drive cache: write through
[57480.025517] SCSI device sdg: 4030463 512-byte hdwr sectors (2064 MB)
[57480.026140] sdg: Write Protect is off
[57480.026143] sdg: Mode Sense: 00 00 00 00
[57480.026145] sdg: assuming drive cache: write through
[57480.026148]  sdg: sdg1 sdg2
[57480.135523] sd 9:0:0:0: Attached scsi removable disk sdg
[57480.135569] sd 9:0:0:0: Attached scsi generic sg9 type 0
[57549.319513] end_request: I/O error, dev sr1, sector 64
[57549.319520] Buffer I/O error on device sr1, logical block 8
[57551.531223] end_request: I/O error, dev sr1, sector 64
[57551.531230] Buffer I/O error on device sr1, logical block 8
[57553.898652] end_request: I/O error, dev sr1, sector 0
[57553.898660] Buffer I/O error on device sr1, logical block 0
[57556.566069] end_request: I/O error, dev sr1, sector 0
[57556.566076] Buffer I/O error on device sr1, logical block 0
[57558.039135] end_request: I/O error, dev sr1, sector 0
[57558.039142] Buffer I/O error on device sr1, logical block 0
[57616.844988] ISO 9660 Extensions: Microsoft Joliet Level 3
[57617.214154] ISO 9660 Extensions: RRIP_1991A
[57868.035966] usb 1-1: USB disconnect, address 6
[57879.170360] usb 1-1: new high speed USB device using ehci_hcd and address 7
[57879.303920] usb 1-1: configuration #1 chosen from 1 choice
[57879.304920] scsi10 : SCSI emulation for USB Mass Storage devices
[57879.306241] usb-storage: device found at 7
[57879.306245] usb-storage: waiting for device to settle before scanning
[57884.296481] usb-storage: device scan complete
[57884.297230] scsi 10:0:0:0: Direct-Access     Generic  USB Flash Disk   0.00 PQ: 0 ANSI: 2
[57884.298958] SCSI device sdg: 4030463 512-byte hdwr sectors (2064 MB)
[57884.299581] sdg: Write Protect is off
[57884.299585] sdg: Mode Sense: 00 00 00 00
[57884.299587] sdg: assuming drive cache: write through
[57884.301826] SCSI device sdg: 4030463 512-byte hdwr sectors (2064 MB)
[57884.302449] sdg: Write Protect is off
[57884.302453] sdg: Mode Sense: 00 00 00 00
[57884.302455] sdg: assuming drive cache: write through
[57884.302458]  sdg: sdg1 sdg2
[57884.411823] sd 10:0:0:0: Attached scsi removable disk sdg
[57884.411869] sd 10:0:0:0: Attached scsi generic sg9 type 0
[58831.184058] usb 1-1: USB disconnect, address 7
[58831.697239] Buffer I/O error on device sdg2, logical block 0
[58831.697246] lost page write due to I/O error on sdg2
[58975.504151] usb 1-1: new high speed USB device using ehci_hcd and address 8
[58975.637693] usb 1-1: configuration #1 chosen from 1 choice
[58975.637811] scsi11 : SCSI emulation for USB Mass Storage devices
[58975.637971] usb-storage: device found at 8
[58975.637974] usb-storage: waiting for device to settle before scanning
[58980.630373] usb-storage: device scan complete
[58980.631129] scsi 11:0:0:0: Direct-Access     Generic  USB Flash Disk   0.00 PQ: 0 ANSI: 2
[58980.632728] SCSI device sdg: 4030463 512-byte hdwr sectors (2064 MB)
[58980.633352] sdg: Write Protect is off
[58980.633356] sdg: Mode Sense: 00 00 00 00
[58980.633360] sdg: assuming drive cache: write through
[58980.635471] SCSI device sdg: 4030463 512-byte hdwr sectors (2064 MB)
[58980.636096] sdg: Write Protect is off
[58980.636100] sdg: Mode Sense: 00 00 00 00
[58980.636104] sdg: assuming drive cache: write through
[58980.636108]  sdg: sdg1 sdg2
[58980.743489] sd 11:0:0:0: Attached scsi removable disk sdg
[58980.743539] sd 11:0:0:0: Attached scsi generic sg9 type 0
[58981.440289] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[59058.766688] usb 1-1: USB disconnect, address 8
[63777.704656] cdrom: This disc doesn't have any tracks I recognize!
[64197.104911] cdrom: This disc doesn't have any tracks I recognize!
[64265.207244] cdrom: This disc doesn't have any tracks I recognize!
[133405.892577] scsi 11:0:0:0: rejecting I/O to dead device
[133405.892597] scsi 11:0:0:0: rejecting I/O to dead device
[157938.637919] cdrom: This disc doesn't have any tracks I recognize!
[163441.406590] UDF-fs: Partition marked readonly; forcing readonly mount
[163441.470244] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Sabayon Linux - x86-64', timestamp 2007/08/01 16:53 (1e5c)
[163710.937535] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163710.937543]     Additional sense: Medium not present
[163710.937549] end_request: I/O error, dev sr0, sector 0
[163710.937552] Buffer I/O error on device sr0, logical block 0
[163710.937557] Buffer I/O error on device sr0, logical block 1
[163710.937561] Buffer I/O error on device sr0, logical block 2
[163710.937564] Buffer I/O error on device sr0, logical block 3
[163710.937567] Buffer I/O error on device sr0, logical block 4
[163710.937571] Buffer I/O error on device sr0, logical block 5
[163710.937574] Buffer I/O error on device sr0, logical block 6
[163710.937577] Buffer I/O error on device sr0, logical block 7
[163710.948919] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163710.948924]     Additional sense: Medium not present
[163710.948929] end_request: I/O error, dev sr0, sector 0
[163710.948932] Buffer I/O error on device sr0, logical block 0
[163710.955409] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163710.955414]     Additional sense: Medium not present
[163710.955418] end_request: I/O error, dev sr0, sector 4
[163710.955421] Buffer I/O error on device sr0, logical block 1
[163710.966859] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163710.966863]     Additional sense: Medium not present
[163710.966868] end_request: I/O error, dev sr0, sector 0
[163710.973349] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163710.973353]     Additional sense: Medium not present
[163710.973358] end_request: I/O error, dev sr0, sector 0
[163710.984797] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163710.984802]     Additional sense: Medium not present
[163710.984806] end_request: I/O error, dev sr0, sector 4
[163710.991290] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163710.991294]     Additional sense: Medium not present
[163710.991299] end_request: I/O error, dev sr0, sector 0
[163711.002737] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.002742]     Additional sense: Medium not present
[163711.002746] end_request: I/O error, dev sr0, sector 4
[163711.003293] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.003297]     Additional sense: Medium not present
[163711.003301] end_request: I/O error, dev sr0, sector 0
[163711.008716] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.008720]     Additional sense: Medium not present
[163711.008725] end_request: I/O error, dev sr0, sector 4
[163711.105547] sr 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.105552]     Additional sense: Medium not present
[163711.105557] end_request: I/O error, dev sr1, sector 0
[163711.110957] sr 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.110962]     Additional sense: Medium not present
[163711.110966] end_request: I/O error, dev sr1, sector 0
[163711.111627] sr 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.111631]     Additional sense: Medium not present
[163711.111636] end_request: I/O error, dev sr1, sector 0
[163711.116935] sr 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.116939]     Additional sense: Medium not present
[163711.116944] end_request: I/O error, dev sr1, sector 0
[163711.117591] sr 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.117595]     Additional sense: Medium not present
[163711.117599] end_request: I/O error, dev sr1, sector 0
[163711.122912] sr 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.122917]     Additional sense: Medium not present
[163711.122921] end_request: I/O error, dev sr1, sector 0
[163711.189428] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.189440]     Additional sense: Medium not present
[163711.189447] end_request: I/O error, dev sr2, sector 0
[163711.211633] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.211642]     Additional sense: Medium not present
[163711.211647] end_request: I/O error, dev sr2, sector 0
[163711.233714] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.233722]     Additional sense: Medium not present
[163711.233728] end_request: I/O error, dev sr2, sector 0
[163711.255921] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.255930]     Additional sense: Medium not present
[163711.255938] end_request: I/O error, dev sr2, sector 0
[163711.278001] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.278010]     Additional sense: Medium not present
[163711.278016] end_request: I/O error, dev sr2, sector 0
[163711.300332] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163711.300340]     Additional sense: Medium not present
[163711.300345] end_request: I/O error, dev sr2, sector 0
[163791.625476] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.625483]     Additional sense: Medium not present
[163791.625489] end_request: I/O error, dev sr0, sector 0
[163791.625492] printk: 23 messages suppressed.
[163791.625495] Buffer I/O error on device sr0, logical block 0
[163791.625499] Buffer I/O error on device sr0, logical block 1
[163791.625503] Buffer I/O error on device sr0, logical block 2
[163791.625507] Buffer I/O error on device sr0, logical block 3
[163791.625510] Buffer I/O error on device sr0, logical block 4
[163791.625514] Buffer I/O error on device sr0, logical block 5
[163791.625517] Buffer I/O error on device sr0, logical block 6
[163791.625520] Buffer I/O error on device sr0, logical block 7
[163791.630879] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.630884]     Additional sense: Medium not present
[163791.630888] end_request: I/O error, dev sr0, sector 0
[163791.630891] Buffer I/O error on device sr0, logical block 0
[163791.631410] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.631414]     Additional sense: Medium not present
[163791.631419] end_request: I/O error, dev sr0, sector 4
[163791.631422] Buffer I/O error on device sr0, logical block 1
[163791.636857] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.636862]     Additional sense: Medium not present
[163791.636866] end_request: I/O error, dev sr0, sector 0
[163791.637384] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.637387]     Additional sense: Medium not present
[163791.637392] end_request: I/O error, dev sr0, sector 4
[163791.642837] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.642841]     Additional sense: Medium not present
[163791.642846] end_request: I/O error, dev sr0, sector 0
[163791.643361] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.643364]     Additional sense: Medium not present
[163791.643369] end_request: I/O error, dev sr0, sector 4
[163791.648816] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.648820]     Additional sense: Medium not present
[163791.648825] end_request: I/O error, dev sr0, sector 0
[163791.649339] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.649343]     Additional sense: Medium not present
[163791.649347] end_request: I/O error, dev sr0, sector 4
[163791.654796] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.654801]     Additional sense: Medium not present
[163791.654806] end_request: I/O error, dev sr0, sector 0
[163791.655329] sr 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.655333]     Additional sense: Medium not present
[163791.655337] end_request: I/O error, dev sr0, sector 4
[163791.752041] sr 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.752048]     Additional sense: Medium not present
[163791.752053] end_request: I/O error, dev sr1, sector 0
[163791.757444] sr 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.757448]     Additional sense: Medium not present
[163791.757453] end_request: I/O error, dev sr1, sector 0
[163791.758123] sr 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.758126]     Additional sense: Medium not present
[163791.758131] end_request: I/O error, dev sr1, sector 0
[163791.763423] sr 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.763428]     Additional sense: Medium not present
[163791.763433] end_request: I/O error, dev sr1, sector 0
[163791.764112] sr 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.764116]     Additional sense: Medium not present
[163791.764121] end_request: I/O error, dev sr1, sector 0
[163791.769398] sr 3:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.769403]     Additional sense: Medium not present
[163791.769408] end_request: I/O error, dev sr1, sector 0
[163791.841570] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.841581]     Additional sense: Medium not present
[163791.841589] end_request: I/O error, dev sr2, sector 0
[163791.863526] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.863534]     Additional sense: Medium not present
[163791.863540] end_request: I/O error, dev sr2, sector 0
[163791.885608] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.885615]     Additional sense: Medium not present
[163791.885620] end_request: I/O error, dev sr2, sector 0
[163791.907813] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.907820]     Additional sense: Medium not present
[163791.907826] end_request: I/O error, dev sr2, sector 0
[163791.929771] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.929778]     Additional sense: Medium not present
[163791.929784] end_request: I/O error, dev sr2, sector 0
[163791.952225] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[163791.952233]     Additional sense: Medium not present
[163791.952240] end_request: I/O error, dev sr2, sector 0
[164237.889947] cdrom: This disc doesn't have any tracks I recognize!
```


See error at end of dmesg is an attempt at a cdr burn.. :)

fstab:

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=268dbad6-0863-4ae6-a0a4-77d5da1a64fc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=421c3488-d392-4fda-8217-38c6a66b3950 /home           ext3    defaults        0       2
# /dev/sdb5
UUID=fb9f6119-1e05-48e8-8ceb-6fc85f109f44 /media/sdb5     ext3    defaults        0       2
# /dev/sdb6
UUID=aed6efe0-6284-48bc-83d3-ccad90f67dd6 /media/sdb6     ext3    defaults        0       2
# /dev/sda1
UUID=145882b2-46d1-4b93-9c0a-f91b3236da5b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

-mike

---

