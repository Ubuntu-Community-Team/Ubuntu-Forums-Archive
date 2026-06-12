---
title: "wireles doesnt work"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Bigadada_saba on 2007-04-28
after upgrading to 7.04 from edgy my atheros wierles card doesnt work  and doent even appear in network settings window
  can eny body help me with the installation of  my atheros wierles card im running a acer aspire 3620.

---

### Post by deadgobby on 2007-04-28
MMM please run this command in the terminal and please post the results

  sudo lshw

Gobby

---

### Post by Bigadada_saba on 2007-04-28
here it is.

description: Notebook
    product: Aspire 3620
    vendor: Acer
    version: 0100
    serial: LXAA60518461505EE92000
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=normal chassis=notebook uuid=626D1A60-CBDB-11DA-9D77-D2A33241A9A4
  *-core
       description: Motherboard
       product: Garda-910
       vendor: Acer
       physical id: 0
       version: Rev
       serial: LXAA60518461505EE92000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: V1.04 (02/24/2006)
          size: 104KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: U1
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MB
             capacity: 1MB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM Synchronous
             physical id: 0
             slot: M1
             size: 1GB
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             physical id: 1
             slot: M2
             size: 1GB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:b0080000-b00fffff ioport:1800-1807 iomemory:c0000000-cfffffff iomemory:b0000000-b003ffff irq:22
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: iomemory:8c000000-8c07ffff
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1820-183f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1840-185f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1860-187f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1880-189f irq:21
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:b0040000-b00403ff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network:0 UNCLAIMED
                description: Ethernet controller
                product: AR5005G 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 5
                bus info: pci@06:05.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=80 maxlatency=28 mingnt=10
                resources: iomemory:b0100000-b010ffff irq:10
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@06:07.0
                logical name: eth0
                version: 10
                serial: 00:0a:e4:fc:3b:10
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.14 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: ioport:3000-30ff iomemory:b0110000-b01100ff irq:23
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 9
                bus info: pci@06:09.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:b0111000-b0111fff irq:16
              *-storage
                   description: FLASH
                   vendor: HITACHI
                   physical id: 0
                   version: 5.0
                   slot: Socket 0
                   resources: irq:3
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:1c00-1cff ioport:18c0-18ff iomemory:b0040800-b00409ff iomemory:b0040400-b00404ff irq:17
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=0
             resources: ioport:2400-24ff ioport:2000-207f irq:17
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:1810-181f irq:22
           *-disk
                description: SCSI Disk
                product: WDC WD800UE-22HC
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 09.0
                serial: WD-WXE606654430
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 35GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 39GB
                   capabilities: primary
           *-cdrom
                description: DVD writer
                product: DVD-RW DVR-K16RA
                vendor: PIONEER
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.16
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:20a0-20bf irq:11
     *-scsi
          physical id: 1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=pata_pcmcia
        *-disk
             description: SCSI Disk
             product: Hitachi XX.V.3.5
             vendor: ATA
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: Rev
             serial: X0815 20051220115531
             size: 488MB
             capabilities: removable
             configuration: ansiversion=5
           *-disc
                physical id: 0
                logical name: /dev/sdb
                size: 488MB
                capabilities: partitioned partitioned:dos
              *-volume
                   description: FAT16 partition
                   physical id: 1
                   logical name: /dev/sdb1
                   capacity: 487MB
                   capabilities: primary bootable

---

### Post by Bigadada_saba on 2007-04-28
i get the message when i try to acces my wireless

Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device

---

### Post by deadgobby on 2007-04-28
Enter this command and post back

  lspci -v

---

### Post by Bigadada_saba on 2007-04-28
dont worry i loeded the restricted drivers and it started working. thanks

---

### Post by deadgobby on 2007-04-28
cool!!!

---

### Post by sugarden on 2007-11-08
wher you findi  ?
t

---

