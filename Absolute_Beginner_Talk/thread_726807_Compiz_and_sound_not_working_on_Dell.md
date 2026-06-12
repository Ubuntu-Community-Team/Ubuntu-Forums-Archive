---
title: "Compiz and sound not working on Dell"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by DJRhubarb on 2008-03-17
I have just purchased a new Dell 1720 laptop and am running Vista and Gutsy parallel.

C2D 2.00 GHz
3GB RAM
250GB HDD
GeForce 8600m GT

I am not new to Ubuntu but I'm no expert so I need a bit of help.:confused:

1.The sound does not work, it's telling me I need a GStreamer plugin, I don't know what I need but I have tried looking for it on Synaptic manager. 

2.Compiz Fusion does not work, I have installed it but the Desktop Effects menu does not show in Preferences and I can't enable Custom Effects, the Restricted Drivers Manager is enabled,I have however run Compiz on previous computers.

Thanks

---

### Post by bluefrog on 2008-03-17
don't know about parallels.

without parallels on 1720, you will need the restricted drivers for your graphic card (I assume you have Nvidia) and you will need linux-backport-modules for the sound.

James Dupin

---

### Post by jan quark on 2008-03-17
can you please post the result of these terminal commands
```

sudo lshw
lspci
```

---

### Post by DJRhubarb on 2008-03-17
description: Portable Computer
    product: Inspiron 1720
    vendor: Dell Inc.
    serial: H8DVT1S
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-3800-1044-8056-C8C04F543153
  *-core
       description: Motherboard
       product: 0UK437
       vendor: Dell Inc.
       physical id: 0
       serial: .H8DVT1S.CN4864381M1465.
       slot: @
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A06 (01/14/2008)
          size: 64KB
          capacity: 960KB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          slot: Microprocessor
          size: 2401MHz
          capacity: 2401MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KB
             capacity: 32KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 3MB
             capacity: 3MB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
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
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 3GB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: M4 70T5663CZ3-CE6
             vendor: CE00000000000000
             physical id: 0
             serial: 47352127
             slot: DIMM_A
             size: 2GB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: M4 70T2864QZ3-CE6
             vendor: CE00000000000000
             physical id: 1
             serial: 53325102
             slot: DIMM_B
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8600M GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Contoller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress cap_list
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 02
                serial: 00:1c:bf:c9:7b:63
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.0.138 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:1d:09:c6:3f:c6
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:03:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.4
                bus info: pci@0000:03:01.4
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD writer
                product: DVD+-RW TS-L632H
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D300
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: SCSI Disk
                product: FUJITSU MHY2250B
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 0085
                serial: K432T81273LN
                size: 232GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Dell Utility partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 78MB
                   capabilities: primary
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 10GB
                   capabilities: primary
              *-volume:2
                   description: HPFS/NTFS partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 207GB
                   capabilities: primary bootable
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   size: 15GB
                   capacity: 15GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2559MB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 12GB
                      capabilities: bootable
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 588MB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-battery
       product: DELL TM97881
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 52000mWh
       configuration: voltage=11.1V

---

### Post by DJRhubarb on 2008-03-17
and the second one:
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
rhubarb@rhubarb-laptop:~$

---

### Post by DJRhubarb on 2008-03-17
The Restricted Drivers for Nvidia grphics card were already enabled, that's what is the problem.

---

