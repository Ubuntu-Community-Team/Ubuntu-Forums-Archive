---
title: "cannot mount volume"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by lionround on 2007-10-09
I am trying to mount an external HDD, however I get the following error message:

Unable to mount volume

mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually/)

Does anyone know where Ubuntu stores the information about where hot swap drives are mounted and by what name?

If so, maybe I can edit that file.

---

### Post by Pumalite on 2007-10-09
Post:
lshw

---

### Post by lionround on 2007-10-09
ubuntu                    
    description: Notebook
    product: Satellite 2455
    vendor: TOSHIBA
    version: PS245U-075RSV
    serial: 23045129PU
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=user-requested chassis=notebook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=7AB34C00-74F4-11D4-800D-AAD223045129
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: $$T03234TW
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.10 (01/20/2003)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing vesa cdboot bootselect pcmciaboot edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: uFC-PGA Socket
          size: 2400MHz
          capacity: 2400MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 8KB
             capacity: 8KB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 512KB
             capacity: 512KB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 0
             size: 256MB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 1
             size: 256MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845 845 (Brookdale) Chipset Host Bridge
          vendor: Intel Corporation
          physical id: e0000000
          bus info: pci@00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e0000000-efffffff
        *-pci:0
             description: PCI bridge
             product: 82845 845 (Brookdale) Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 420 Go]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a3
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: iomemory:fd000000-fdffffff iomemory:dc000000-dfffffff iomemory:dbf80000-dbffffff irq:10
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:efe0-efff irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.20
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef80-ef9f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:18c0-18df irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:38000000-380003ff irq:11
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: LaCie d2 Drive USB2
                   vendor: LaCie
                   physical id: 1
                   bus info: usb@4:1
                   logical name: scsi6
                   version: 0.00
                   serial: 10000E0009ADF8C2
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=2mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: ST3250823A
                      vendor: SEAGATE
                      physical id: 0.0.0
                      bus info: scsi@6:0.0.0
                      logical name: /dev/sdb
                      version: 3.01
                      size: 232GB
                      capacity: 232GB
                      capabilities: 5400rpm partitioned partitioned:dos
                      configuration: ansiversion=2
                    *-volume
                         description: W95 FAT32 (LBA) partition
                         physical id: 1
                         bus info: scsi@6:0.0.0,1
                         logical name: /dev/sdb1
                         capacity: 232GB
                         capabilities: primary
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 7
                bus info: pci@02:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: iomemory:fce06000-fce067ff iomemory:fce00000-fce03fff irq:11
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 9
                bus info: pci@02:09.0
                logical name: eth0
                version: 10
                serial: 00:08:0d:73:a2:0b
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
                resources: ioport:ce00-ceff iomemory:fcefff00-fcefffff irq:11
           *-pcmcia:0
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b
                bus info: pci@02:0b.0
                version: 32
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=0 maxlatency=5
                resources: iomemory:fce04000-fce04fff irq:11
              *-network
                   description: 88W8300 802.11b Cardbus PC Card
                   product: 83
                   vendor: Marvell Semiconductor
                   physical id: 0
                   version: 01
                   slot: Socket 0
                   resources: irq:11
           *-pcmcia:1
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b.1
                bus info: pci@02:0b.1
                version: 32
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=0 maxlatency=5 mingnt=128
                resources: iomemory:fce05000-fce05fff irq:11
           *-system UNCLAIMED
                description: System peripheral
                product: SD TypA Controller
                vendor: Toshiba America Info Systems
                physical id: d
                bus info: pci@02:0d.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: iomemory:fce06800-fce069ff irq:255
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:bfa0-bfaf iomemory:38000400-380007ff irq:11
           *-disk
                description: SCSI Disk
                product: TOSHIBA MK6021GA
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: GA02
                serial: 236B1072T
                size: 55GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 27GB
                   capabilities: primary
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2659MB
                   capacity: 2659MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1474MB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1184MB
                      capabilities: nofs
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 25GB
                   capabilities: primary bootable
           *-cdrom
                description: DVD writer
                product: DVD-ROM SD-R6012
                vendor: TOSHIBA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1332
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:1000-10ff ioport:1880-18bf iomemory:38000800-380009ff iomemory:38000a00-38000aff irq:11
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=0
             resources: ioport:1400-14ff ioport:1800-187f irq:11
     *-network
          description: Wireless interface
          product: Marvell W8300 802.11 Adapter
          vendor: Marvell Technology Group Ltd.
          physical id: 1
          bus info: pci@03:00.0
          logical name: wlan0
          version: 07
          serial: 00:0d:88:f3:1a:7b
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=D-Link,12/21/2003,2.2.0.19 ip=192.168.0.103 latency=64 link=yes multicast=yes wireless=IEEE 802.11b
          resources: iomemory:3c000000-3c00ffff iomemory:3c010000-3c01ffff irq:11
  *-battery
       description: Lithium Ion Battery
       product: LPX45E
       vendor: TOSHIBA
       physical id: 1
       version: 01/17/03
       serial: 1200009383
       slot: 1st Battery
       configuration: voltage=10.8V

---

### Post by Pumalite on 2007-10-09
Is this a new hard drive? Have you format it? What's the format?

---

### Post by lionround on 2007-10-09
No, it is not new.  I have mounted it before.  It is a Lacie case with Seagate 250 gig. fat32.  It has about a gig of data on it (nothing major, just music).

---

### Post by Pumalite on 2007-10-09
If you are using 7.04 or later; it should hot mount.

---

### Post by lionround on 2007-10-09
I already knew that. What I need to know is where ubuntu stores the information about where it is GOING to mount a hot swap drive

---

### Post by Pumalite on 2007-10-09
In my system; from /media. It shows up as 'disk'. But I don't have to worry about that because the drive immediately appears in my Desktop and the folders open up automatically.

---

### Post by smilingfrog on 2007-10-09
I think it is stored int the /etc/fstab file.
Google that and look around.
I, too, am new and have no idea what I am doing, but that seemed to solve my mounting problems.

:)G

---

### Post by Pumalite on 2007-10-09
It's a bad idea to mount an USB drive through /etc/fstab.

---

### Post by Aleedee on 2007-11-26
I have the same problem, I can see my My Book in My Computer, but cannot access it. I'm a 3 days old Ubuntu newbie. Read several topics but could not figure it out. Help please. :(

---

### Post by Pumalite on 2007-11-26
Is My Book a 500 GB external hard drive with Microsoft software already installed?
'#  WD Backup&#8482; software &#8212; We've provided software that makes backing up your data as easy as possible. With a few simples steps you can back up all your data files or just save your picture and music files. You can also set scheduled backups, so you don't have to think about it again.
# Capacity gauge &#8212; See at a glance how much space is available on your drive.'

---

### Post by Aleedee on 2007-11-27
That message seems commercial to me, and it does not help me at all. And it is a 250 gigs, not 500. So, how can I mount this external disk?

---

