---
title: "Built-in webcam detection"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by futuroimperfetto on 2008-01-14
Hello,

I have an Asus Z96J with a built-in 1.3MP webcam. Unfortunately, this internal webcam is not detected by Gutsy and I cannot use it.

I tried to install a program called EasyCam ([https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)) but my webcam was probably not in the list of supported ones.

What should I do to make Gutsy detect it (if possible)?

Thank you

Cheers!

---

### Post by anaconda on 2008-01-14
what camera model is it?

If you don't know, you can type these commands on the terminal and search for the relevant lines and post them here, and someone can probably help you.. At least if your camera is supported.

Here are the commands
lsusb
lsusb -v
lshw
lspci
lspci -v

And usually the internal cameras are usb-cameras, so the "lsusb" should be enough..

once you find out what camera chip you have then you can search these forums with that info.

---

### Post by futuroimperfetto on 2008-01-14
Hi Anaconda,

thank you for your reply. I tried the commands you gave me, but I couldn't detect anything that seemed a webcam. I had this webcam added after I bought this laptop, but I know it works, because it is detected by the Windows partition of this laptop.

Now, if I type "lshw" I should see all the detected hardware of my laptop. Here is what I see in a terminal:

```

   description: Notebook
    product: Z96JS
    vendor: ASUSTeK Computer INC.
    version: 1.0
   description: Notebook
    product: Z96JS
    vendor: ASUSTeK Computer INC.
    version: 1.0
    serial: NB-1234567890
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: Z96JS
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.00
       serial: NB-0123456789
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012 (02/22/2006)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           T2600  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: Socket 478M
          size: 996MHz
          capacity: 2171MHz
          width: 32 bits
          clock: 167MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KB
             capacity: 32KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MB
             capacity: 2MB
             capabilities: internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: M56P [Radeon Mobility X1600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
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
             product: 82801G (ICH7 Family) PCI Express Port 2
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
                bus info: pci@0000:04:00.0
                logical name: eth1
                version: 02
                serial: 00:13:02:1a:a7:c4
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=no module=ipw3945 multicast=yes wireless=unassociated
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
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
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:06:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:06:01.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:06:01.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=0
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:06:01.3
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-network
                description: Ethernet interface
                product: RTL-8169 Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:06:07.0
                logical name: eth0
                version: 10
                serial: 00:17:31:03:67:49
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.11.2 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
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
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: ST980811AS
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AL
                serial: 5LY4PGTA
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 45GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 8189MB
                   capabilities: primary
              *-volume:2
                   description: Linux swap / Solaris partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 2047MB
                   capabilities: primary nofs
              *-volume:3
                   description: Linux filesystem partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 19GB
                   capabilities: primary
           *-cdrom
                description: DVD-RAM writer
                product: CD/DVDW TS-L632C
                vendor: TSSTcorp
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AS06
                serial: [TSSTcorpCD/DVDW TS-L632CAS0612/29/05A5C010
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
    serial: NB-1234567890
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: Z96JS
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.00
       serial: NB-0123456789
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012 (02/22/2006)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           T2600  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: Socket 478M
          size: 996MHz
          capacity: 2171MHz
          width: 32 bits
          clock: 167MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KB
             capacity: 32KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MB
             capacity: 2MB
             capabilities: internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: M56P [Radeon Mobility X1600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
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
             product: 82801G (ICH7 Family) PCI Express Port 2
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
                bus info: pci@0000:04:00.0
                logical name: eth1
                version: 02
                serial: 00:13:02:1a:a7:c4
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=no module=ipw3945 multicast=yes wireless=unassociated
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
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
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:06:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:06:01.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:06:01.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=0
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:06:01.3
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-network
                description: Ethernet interface
                product: RTL-8169 Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:06:07.0
                logical name: eth0
                version: 10
                serial: 00:17:31:03:67:49
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.11.2 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
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
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: ST980811AS
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AL
                serial: 5LY4PGTA
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 45GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 8189MB
                   capabilities: primary
              *-volume:2
                   description: Linux swap / Solaris partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 2047MB
                   capabilities: primary nofs
              *-volume:3
                   description: Linux filesystem partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 19GB
                   capabilities: primary
           *-cdrom
                description: DVD-RAM writer
                product: CD/DVDW TS-L632C
                vendor: TSSTcorp
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AS06
                serial: [TSSTcorpCD/DVDW TS-L632CAS0612/29/05A5C010
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
```

I'm probably wrong, but it doesn't look to me like any of the listed devices is a webcam. Otherwise, I'd ask you to point me which one that is (sorry, I really am a beginner).

If I'm not wrong, does this mean that Gutsy is not aware of it?

Otherwise, is there a command to tell Gutsy to refresh its list of hardware?

Thank you for your help

---

### Post by intel on 2008-01-15
post the output of the following command

#lsusb

its probably 174f:6a51 a Syntek webcam, I haven't heard any news of its support under your OS

---

### Post by kvonb on 2008-01-15
_-_

---

### Post by futuroimperfetto on 2008-01-20
Hi Intel,

 Sorry for the late reply. Here is the output of "lsusb".

```

Bus 005 Device 004: ID 0402:5602 ALi Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c00f Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Actually, I did type this command before under Anaconda's suggestion, but due to my inexperience it didn't seem to return anything useful.

Which one of the previous lines is referring to the webcam? Even if it's not supported, it is interesting for me to learn how to detect the correct line.:)

Thank you very much!

---

### Post by saliola on 2008-01-25
*First post*

There is an entry in LaunchPad on this topic.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/55567]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/55567")

Note especially that there is a project to create a driver, which is active, but slow. Here's the link.

[https://sourceforge.net/projects/m560x-driver/]("https://sourceforge.net/projects/m560x-driver/")

You should get in contact with them and tell them that you can help by testing the driver on your laptop.

--

---

