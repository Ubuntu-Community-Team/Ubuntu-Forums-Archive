---
title: "why does my computer freeze?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by shedokan on 2008-02-08
my computer freezes after 20 min of using.
any thing I can do to help you helping me?

here is the output:

lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
```

sudo lshw:
```

ubuntu-desktop            
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: MS-7255
       vendor: Micro-Star
       physical id: 0
       version: 1.2
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080013 (08/25/2006)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot ieee1394boot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.10
          serial: 0000-0F4A-0000-0000-0000-0000
          slot: CPU 1
          size: 3200MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc up pni monitor ds_cpl est cid cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KB
             capacity: 16KB
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
          physical id: 27
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: DIMM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-pci:0
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-system UNCLAIMED
             description: PIC
             product: P4M890 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G71 [GeForce 7300 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-pci:2
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-storage
             description: RAID bus controller
             product: VT8237A SATA 2-Port Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=sata_via latency=128 module=sata_via
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=VIA_IDE latency=32 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom:0
                   description: IDE CD-ROM
                   product: ASUS CD-S520/A4
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 1.32
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                   configuration: mode=udma2 status=nodisc
              *-cdrom:1
                   description: DVD writer
                   product: TSSTcorpCD/DVDW TS-H552B
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: TS04
                   serial: TS-H552BFirmware
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma2 status=nodisc
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD1600JB-00REA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 20.00K20
                   serial: WD-WCANMA517897
                   size: 149GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@1.0,1
                      logical name: /dev/hdc1
                      capacity: 93GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux swap / Solaris partition
                      physical id: 2
                      bus info: ide@1.0,2
                      logical name: /dev/hdc2
                      capacity: 956MB
                      capabilities: primary nofs
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=128 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-14-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: /dev/usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=128 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-14-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: /dev/usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=128 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-14-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: /dev/usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=128 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-14-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: /dev/usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=128 module=ehci_hcd
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.22-14-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: /dev/usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: maxpower=0mA slots=8 speed=480.0MB/s
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:16:17:de:0b:31
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.123.119 latency=128 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
        *-pci:3
             description: PCI bridge
             product: VT8237A Host Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-multimedia
                description: Audio device
                product: VIA High Definition Audio Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:4
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht subtractive_decode bus_master cap_list
     *-pci:1
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: P4M890 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=128
```

thanks.:popcorn:

---

### Post by dstew on 2008-02-08
What kind of computer is it? Do you get any error messages? What do you have to do to get it going again?

---

### Post by shedokan on 2008-02-09
> **dstew said:**
> What kind of computer is it? Do you get any error messages? What do you have to do to get it going again?

it's a normal computer, no just freezes and I need to press the restart button to get it going again.

---

### Post by Joeb454 on 2008-02-09
What are you doing when it freezes?

Do you have a graphics card installed?

---

### Post by randy78 on 2008-02-09
Are you using Compiz?

Try disabling ALL Desktop Effects settings if you are, and see if that makes a difference.

---

### Post by shedokan on 2008-02-09
now it's not freezing but from time to time it does.

---

### Post by badmedic on 2008-02-09
What are your power management settings?

Go to 'System > Preferences > Power Management' and see if your computer is set to put the computer to sleep. If so, maybe that is related to the issue? 

Sorry this isn't an answer, just another direction to look for the potential source of the issue.

---

### Post by sports fan Matt on 2008-02-09
What are the specs of your computer?  How much memory do you have in your computer?  If its not enough (bare minnium 256 mb) your computer will freeze and act all wierded out...

---

### Post by shedokan on 2008-02-11
I don't know exactly but I have 526mb and nvidia driver msi motherboard.

---

### Post by jan quark on 2008-02-11
pls run the following terminal commands and post the output

this should be done at the very beginning of the post :)

```
lspci
```

```
sudo lshw
```

---

### Post by shedokan on 2008-02-12
here is the output:

lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
```

sudo lshw:
```

ubuntu-desktop            
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: MS-7255
       vendor: Micro-Star
       physical id: 0
       version: 1.2
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080013 (08/25/2006)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot ieee1394boot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.10
          serial: 0000-0F4A-0000-0000-0000-0000
          slot: CPU 1
          size: 3200MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc up pni monitor ds_cpl est cid cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KB
             capacity: 16KB
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
          physical id: 27
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: DIMM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-pci:0
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-system UNCLAIMED
             description: PIC
             product: P4M890 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G71 [GeForce 7300 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-pci:2
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-storage
             description: RAID bus controller
             product: VT8237A SATA 2-Port Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=sata_via latency=128 module=sata_via
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=VIA_IDE latency=32 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom:0
                   description: IDE CD-ROM
                   product: ASUS CD-S520/A4
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 1.32
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                   configuration: mode=udma2 status=nodisc
              *-cdrom:1
                   description: DVD writer
                   product: TSSTcorpCD/DVDW TS-H552B
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: TS04
                   serial: TS-H552BFirmware
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma2 status=nodisc
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD1600JB-00REA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 20.00K20
                   serial: WD-WCANMA517897
                   size: 149GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@1.0,1
                      logical name: /dev/hdc1
                      capacity: 93GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux swap / Solaris partition
                      physical id: 2
                      bus info: ide@1.0,2
                      logical name: /dev/hdc2
                      capacity: 956MB
                      capabilities: primary nofs
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=128 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-14-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: /dev/usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=128 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-14-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: /dev/usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=128 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-14-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: /dev/usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=128 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-14-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: /dev/usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=128 module=ehci_hcd
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.22-14-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: /dev/usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: maxpower=0mA slots=8 speed=480.0MB/s
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:16:17:de:0b:31
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.123.119 latency=128 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
        *-pci:3
             description: PCI bridge
             product: VT8237A Host Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-multimedia
                description: Audio device
                product: VIA High Definition Audio Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:4
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht subtractive_decode bus_master cap_list
     *-pci:1
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: P4M890 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=128
```

---

