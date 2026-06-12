---
title: "Powerbook G4 1.67 Mhz: Sound card not detected"
date: 2008-07-07
forum: Apple Hardware Users
---

### Post by LeSid on 2008-07-07
Hi

I installed Ubuntu using [the minimal method]("https://help.ubuntu.com/community/Installation/MinimalCD") and my computer's sound card is not detected. 

```
ubuntu:~$ sudo lshw
ubuntu                
    description: Computer
    product: PowerBook G4 15" 1.67/1.5GHz
    vendor: Copyright 1983-2004 Apple Computer, Inc. All Rights Reserved
    serial: SQ7W85XXXXXXXX
  *-core
       description: Motherboard
       physical id: 0
       clock: 166MHz
       capabilities: powerbook5_6 macrisc3 power_macintosh
     *-firmware
          product: OpenFirmware 3
          physical id: 0
          logical name: /proc/device-tree
          capabilities: bootinfo
     *-memory
          description: System memory
          physical id: 1
          size: 1GiB
        *-bank:0
             description: DDR SDRAM
             product: PC2700U-25330
             physical id: 0
             version: 0200,05 10,0C
             serial: XXX
             slot: SODIMM0/J25LOWER
             size: 512MiB
        *-bank:1
             description: DDR SDRAM
             product: PC2700U-25330
             physical id: 1
             version: 0200,05 10,0C
             serial: XXX
             slot: SODIMM1/J25UPPER
             size: 512MiB
     *-cpu
          description: CPU
          product: 7447A, altivec supported
          physical id: 2
          bus info: cpu@0
          version: 0.2 (pvr 8003 0102)
          size: 1666MHz
          capacity: 1666MHz
          clock: 166MHz
          capabilities: altivec performance-monitor cpufreq
        *-cache:0
             description: L1 Cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 Cache (unified)
             physical id: 1
             size: 512KiB
             clock: 1666MHz (0.6ns)
     *-pci:0
          description: Host bridge
          product: UniNorth 2 AGP
          vendor: Apple Computer Inc.
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-uninorth latency=16 module=uninorth_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: RV350 [Mobility Radeon 9600 M10]
             vendor: ATI Technologies Inc
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
             configuration: latency=255 mingnt=8
     *-pci:1
          description: Host bridge
          product: UniNorth 2 PCI
          vendor: Apple Computer Inc.
          physical id: 101
          bus info: pci@0001:10:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=16
        *-network
             description: Network controller
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 12
             bus info: pci@0001:10:12.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=b43-pci-bridge latency=16 module=ssb
        *-pcmcia
             description: CardBus bridge
             product: PCI1510 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 13
             bus info: pci@0001:10:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-generic
             product: KeyLargo/Intrepid Mac I/O
             vendor: Apple Computer Inc.
             physical id: 17
             bus info: pci@0001:10:17.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=macio latency=16
           *-ide
                description: IDE Channel 0
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD writer
                   product: MATSHITADVD-R UJ-845E
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: DMP2
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: status=open
        *-usb:0 UNCLAIMED
             description: USB Controller
             product: KeyLargo/Intrepid USB
             vendor: Apple Computer Inc.
             physical id: 19
             bus info: pci@0001:10:19.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci
             configuration: latency=0 maxlatency=86 mingnt=3
        *-usb:1
             description: USB Controller
             product: KeyLargo/Intrepid USB
             vendor: Apple Computer Inc.
             physical id: 1a
             bus info: pci@0001:10:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=16 maxlatency=86 mingnt=3 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 1b
             bus info: pci@0001:10:1b.0
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=16 maxlatency=42 mingnt=1 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 1b.1
             bus info: pci@0001:10:1b.1
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=16 maxlatency=42 mingnt=1 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: NEC Corporation
             physical id: 1b.2
             bus info: pci@0001:10:1b.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=16 maxlatency=34 mingnt=16 module=ehci_hcd
     *-pci:2
          description: Host bridge
          product: UniNorth 2 Internal PCI
          vendor: Apple Computer Inc.
          physical id: 102
          bus info: pci@0002:24:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=16
        *-generic
             product: UniNorth/Intrepid ATA/100
             vendor: Apple Computer Inc.
             physical id: d
             bus info: pci@0002:24:0d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ide-pmac latency=32
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: Hitachi HTS541080G9AT00
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: MB4AA5AJ
                   serial: XXX
                   size: 74GiB (80GB)
                   capacity: 74GiB (80GB)
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:mac
                   configuration: apm=off smart=on
                 *-volume:0
                      description: Apple partition map
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 31KiB
                 *-volume:1
                      description: Apple Bootstrap
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 974KiB
                      capacity: 977KiB
                      capabilities: bootable hfs initialized
                      configuration: created=2008-06-17 13:08:51 filesystem=hfs label=bootstrap modified=2008-06-17 13:20:08 state=clean
                 *-volume:2
                      description: Apple HFS
                      vendor: Mac OS X (journaled)
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      version: 4
                      serial: XXX
                      size: 60GiB
                      capacity: 60GiB
                      capabilities: journaled recover bootable osx hfsplus initialized
                      configuration: boot=osx checked=2005-04-28 07:42:31 created=2005-04-27 22:42:31 filesystem=hfsplus lastmountedby=HFSJ modified=2008-0
6-29 13:04:15 state=clean
                 *-volume:3
                      description: Apple Bootstrap
                      physical id: 4
                      bus info: ide@0.0,4
                      logical name: /dev/hda4
                      size: 974KiB
                      capacity: 977KiB
                      capabilities: bootable hfs initialized
                      configuration: created=2008-06-27 16:15:29 filesystem=hfs label=bootstrap modified=2008-06-28 00:53:37 state=clean
                 *-volume:4
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 5
                      bus info: ide@0.0,5
                      logical name: /dev/hda5
                      logical name: /
                      logical name: /dev/.static/dev
                      version: 1.0
                      serial: XXX
                      size: 13GiB
                      capacity: 13GiB
                      capabilities: journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                      configuration: created=2008-06-27 15:58:24 filesystem=ext3 modified=2008-06-29 13:05:10 mount.fstype=ext3 mount.options=rw,relatime,e
rrors=remount-ro,data=ordered mounted=2008-06-29 13:05:10 state=mounted
                 *-volume:5
                      description: Linux swap volume
                      physical id: 6
                      bus info: ide@0.0,6
                      logical name: /dev/hda6
                      version: 1
                      serial: XXX
                      size: 647MiB
                      capacity: 647MiB
                      capabilities: swap initialized
                      configuration: filesystem=swap pagesize=4096
                 *-volume:6
                      description: Apple Free
                      physical id: 7
                      bus info: ide@0.0,7
                      logical name: /dev/hda7
                      capacity: 128MiB
        *-firewire
             description: FireWire (IEEE 1394)
             product: UniNorth 2 FireWire
             vendor: Apple Computer Inc.
             physical id: e
             bus info: pci@0002:24:0e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=24 mingnt=12 module=ohci1394
        *-network
             description: Ethernet interface
             product: UniNorth 2 GMAC (Sun GEM)
             vendor: Apple Computer Inc.
             physical id: f
             bus info: pci@0002:24:0f.0
             logical name: eth0
             version: 80
             serial: XXX
             size: 10MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=half latency=16 link=no maxlatency=64 mingnt=64 module
=sungem multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: XXX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.133 multicast=yes wireless=IEEE 802.11g
```

Any advice? Thanks!

---

