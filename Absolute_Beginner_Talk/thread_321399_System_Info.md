---
title: "System Info?"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by jwholcomb on 2006-12-18
Just converted one of my computers to Ubuntu. I like a lot of the features, but one thing I cannot find is the Linux equivalant of the System feature in WinXP tells you the chipset memory, etc. I am sure there is something in there I just cant find it.

Thanks in advance, JOHN

---

### Post by dbbolton on 2006-12-18
that's a good question. i tried to figure it out one day, and couldn't.

the closest thing i found are system monitor-type applications (analogous to task manager)

but, youre probably looking for something like control panel>system> general, right ?

---

### Post by invalid on 2006-12-18
I can't comment on graphical tools, if that is what you are searching for, but the files in /proc contain information related to your system.
For example```
cat /proc/cpuinfo
```will bring up relavent cpu information.

---

### Post by argie on 2006-12-18
System > Administration > Device Manager perhaps?

---

### Post by macogw on 2006-12-18
Yeah, Device Manager is the closest thing to that.  It actually gets considerably more detailed than Windows' System > Hardware does, though that doesn't make it any more understandable for most people since most of the info makes you go "o_O what?!"

---

### Post by Kazna on 2006-12-18
Go through Add/remove and search for [B]Sysinfo

[/B]It should be there. A useful utility for someone like me :Smile:

---

### Post by dbott67 on 2006-12-18
lshw (list hardware) is the command you're probably looking for:
```
dbott@thedrake:~$ sudo lshw
thedrake
    description: Tower Computer
    product: System Name
    vendor: System Manufacturer
    version: System Version
    serial: EVAL
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=tower
  *-core
       description: Motherboard
       product: <P4B>
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: xxxxxxxxxxx
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: ASUS P4B ACPI BIOS Revision 1008 (12/26/2001)
          size: 64KB
          capacity: 192KB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect soc ketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5p rintscreen int9keyboard int14serial int17printer int10video acpi usb agp
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.4
          slot: PGA 478
          size: 1800MHz
          capacity: 2400MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic  sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 8KB
             capacity: 32KB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 512KB
             capabilities: pipeline-burst synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 896MB
          capacity: 3GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 128MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 256MB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: DIMM 3
             size: 512MB
             width: 64 bits
        *-bank:3
             description: DIMM DRAM Synchronous [empty]
             physical id: 3
             slot: DDR 1
        *-bank:4
             description: DIMM DRAM Synchronous [empty]
             physical id: 4
             slot: DDR 2
     *-pci
          description: Host bridge
          product: 82845 845 (Brookdale) Chipset Host Bridge
          vendor: Intel Corporation
          physical id: f8000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f8000000-fbffffff
        *-pci:0
             description: PCI bridge
             product: 82845 845 (Brookdale) Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display:0
                description: VGA compatible controller
                product: RV350 AP [Radeon 9600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=fglrx_pci
                resources: iomemory:e0000000-efffffff ioport:d800-d8ff iomemory: bf800000-bf80ffff irq:217
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AP [Radeon 9600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 00
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                resources: iomemory:c0000000-cfffffff iomemory:bf000000-bf00ffff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: a
                bus info: pci@02:0a.0
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy
                resources: ioport:b800-b81f irq:169
           *-input
                description: Input device controller
                product: SB Live! MIDI/Game Port
                vendor: Creative Labs
                physical id: a.1
                bus info: pci@02:0a.1
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Emu10k1_gameport
                resources: ioport:b400-b407
           *-network
                description: Ethernet interface
                product: RTL8139 Ethernet
                vendor: D-Link System Inc
                physical id: b
                bus info: pci@02:0b.0
                logical name: eth0
                version: 10
                serial: 00:50:ba:c0:a7:55
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=8139too d riverversion=0.9.27 duplex=full ip=192.168.1.106 link=yes multicast=yes port=MII  speed=100MB/s
                resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:185
           *-usb:0
                description: USB Controller
                product: USB 1.1 Controller
                vendor: ALi Corporation
                physical id: d
                bus info: pci@02:0d.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci_hcd
                resources: iomemory:be000000-be000fff irq:169
              *-usbhost
                   product: OHCI Host Controller
                   vendor: Linux 2.6.15-27-386 ohci_hcd
                   physical id: 1
                   bus info: usb@3
                   logical name: usb3
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
           *-usb:1
                description: USB Controller
                product: USB 1.1 Controller
                vendor: ALi Corporation
                physical id: d.1
                bus info: pci@02:0d.1
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci_hcd
                resources: iomemory:bd800000-bd800fff irq:185
              *-usbhost
                   product: OHCI Host Controller
                   vendor: Linux 2.6.15-27-386 ohci_hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
           *-usb:2
                description: USB Controller
                product: USB 1.1 Controller
                vendor: ALi Corporation
                physical id: d.2
                bus info: pci@02:0d.2
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci_hcd
                resources: iomemory:bd000000-bd000fff irq:193
              *-usbhost
                   product: OHCI Host Controller
                   vendor: Linux 2.6.15-27-386 ohci_hcd
                   physical id: 1
                   bus info: usb@5
                   logical name: usb5
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
           *-usb:3
                description: USB Controller
                product: USB 2.0 Controller
                vendor: ALi Corporation
                physical id: d.3
                bus info: pci@02:0d.3
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: ehci bus_master cap_list
                configuration: driver=ehci_hcd
                resources: iomemory:bc800000-bc8000ff irq:201
              *-usbhost
                   product: EHCI Host Controller
                   vendor: Linux 2.6.15-27-386 ehci_hcd
                   physical id: 1
                   bus info: usb@6
                   logical name: usb6
                   version: 2.06
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/ s
                 *-usb
                      description: USB hub
                      vendor: Standard Microsystems Corp.
                      physical id: 6
                      bus info: usb@6:6
                      version: 0.01
                      capabilities: usb-2.00
                      configuration: driver=hub maxpower=2mA slots=4 speed=480.0 MB/s
                    *-usb
                         description: Mouse
                         product: USB Mouse
                         vendor: Logitech
                         physical id: 4
                         bus info: usb@6:6.4
                         version: 6.b4
                         capabilities: usb-1.10
                         configuration: driver=usbhid maxpower=100mA speed=1.5MB /s
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801BA IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:a800-a80f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: ST340016A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 3.05
                   serial: 3HS0Y8MT
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm partitioned  partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 14GB
                      capabilities: primary
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 19GB
                      capabilities: primary
                 *-volume:2
                      description: Linux swap / Solaris partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 3161MB
                      capabilities: primary nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD writer
                   product: LITE-ON DVDRW SOHW-1633S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: BS0C
                   capabilities: packet atapi cdrom removable nonmagnetic dma lb a iordy audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:a400-a41f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 12
             width: 32 bits
             clock: 33MHz
             resources: ioport:e800-e80f
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@00:1f.4
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:a000-a01f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:9800-98ff ioport:9400-943f irq:209

```
You can also just display a 'class' of hardware (network, video, etc.):
```
dbott@thedrake:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c0:a7:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.106 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:185

```

-Dave

---

### Post by macogw on 2006-12-18
There's also lspci.  If you add -v or -vvvvv (more v's = more info) you can find out more

---

