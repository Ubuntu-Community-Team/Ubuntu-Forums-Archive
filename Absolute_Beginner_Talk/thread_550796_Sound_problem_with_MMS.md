---
title: "Sound problem with MMS"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by OisinT on 2007-09-14
A few days ago I had a problem with all my sound being very crackly at high ranges and just sounding awful in general.  I followed a quick tip to get it working fine again.
It sounded great, but out of the blue my MMS player would say that it couldn't play files - saying plugins were incorrect or another programme was blocking the soundcard.
I have installed the latest version of ALSA and nothing seems to be working for me.
Strangely when I reinstalled ALSA, the slight crackle came back using VLC (as VLC seems to play audio fine)... it is just MMS that seems to be having the problems.
My sound card is the ALC882

```
oisint1                   
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2046MB
     *-cpu
          product: Intel(R) Pentium(R) D CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2400MHz
          capacity: 2400MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl vmx est cid cx16 xtpr lahf_lm cpufreq
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 81
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G70 [GeForce 7600 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: iomemory:fa000000-faffffff iomemory:e0000000-efffffff iomemory:fb000000-fbffffff ioport:df00-df7f irq:16
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:fdff8000-fdffbfff irq:16
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff00-ff1f irq:23
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: USB RECEIVER
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@1:1
                   version: 25.10
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=70mA speed=1.5MB/s
              *-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: eHome Infrared Transceiver
                   vendor: Philips
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.00
                   serial: PH00Su1n
                   capabilities: usb-1.10
                   configuration: maxpower=100mA speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:fe00-fe1f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Keyboard
                   product: HID compliant keyboard
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.80
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:fd00-fd1f irq:18
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
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:fc00-fc1f irq:16
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
                   description: Mass storage device
                   product: USB Reader
                   physical id: 1
                   bus info: usb@4:1
                   version: 1.00
                   serial: 2004888
                   capabilities: usb-1.10 scsi
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:fdfff000-fdfff3ff irq:23
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@02:01.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=32
                resources: iomemory:fdeff000-fdeff7ff ioport:ef00-ef7f irq:20
           *-network:0 UNCLAIMED
                description: Ethernet controller
                product: AR5006X 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 3
                bus info: pci@02:03.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=168 maxlatency=28 mingnt=10
                resources: iomemory:fdee0000-fdeeffff irq:19
           *-multimedia
                description: Multimedia controller
                product: SAA7133/SAA7135 Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 4
                bus info: pci@02:04.0
                version: d1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=84
                resources: iomemory:fdefe000-fdefe7ff irq:16
           *-network:1
                description: Ethernet interface
                product: 82801G (ICH7 Family) LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@02:08.0
                logical name: eth0
                version: 01
                serial: 00:17:31:f0:2b:af
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=89.100.163.65 latency=32 maxlatency=56 mingnt=8 multicast=yes
                resources: iomemory:fdefd000-fdefdfff ioport:ee00-ee3f irq:20
        *-isa
             description: ISA bridge
             product: 82801GH (ICH7DH) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:fb00-fb0f irq:18
           *-cdrom:0
                description: DVD-RAM writer
                product: DVDRRW GSA-H20L
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: S742
                serial: [HL-DT-STDVDRRW GSA-H20L S74206/05/04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/scd0
           *-cdrom:1
                description: DVD reader
                product: DROM6216
                vendor: IDE-DVD
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: HD08
                capabilities: removable audio dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-storage
             description: RAID bus controller
             product: 82801GR/GH (ICH7 Family) Serial ATA Storage Controller RAID
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi2
             logical name: scsi3
             logical name: scsi4
             logical name: scsi5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list scsi-host
             configuration: driver=ahci latency=0
             resources: ioport:fa00-fa07 ioport:f900-f903 ioport:f800-f807 ioport:f700-f703 ioport:f600-f60f iomemory:fdffe000-fdffe3ff irq:19
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500-51f irq:255
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage

```

---

