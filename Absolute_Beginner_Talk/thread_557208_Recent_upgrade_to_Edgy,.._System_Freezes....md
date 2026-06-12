---
title: "Recent upgrade to Edgy,.. System Freezes..."
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by naiya on 2007-09-22
Hi,
I recently installed Edgy. My system is freezing if I have more than one program running. How do I check resources and troubleshoot this? I only have this OS on my laptop...
Thanks!
Naiya

---

### Post by Linux_Man on 2007-09-22
Make sure its not running off of the live-cd first. Second go to system then administration then process monitor, from there you can check the CPU and see what all is running. Also is this an upgrade from an earlier version of Ubuntu or a clean install?

---

### Post by naiya on 2007-09-22
Nope, not running from live CD. It's a clean install. I did have Dapper previoously, but the upgrade went askew. Luckily I backed up all my stuff, and I was able to figure out how to get my wireless card to work. 

I wonder if somehow I did something incorrectly with partitions... I will take a look at what you suggested.

---

### Post by Pumalite on 2007-09-22
Post specs.
Post:
sudo fdisk -lu

---

### Post by Linux_Man on 2007-09-22
Did you make sure to give it swap space? Also post your specs of your computer, you can find them from the system tab of system monitor, because if its an underpowered processor or not enough ram it could cause those problems.

---

### Post by naiya on 2007-09-22
Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    37576034    18787986   83  Linux
/dev/hda2        37576035    39070079      747022+   5  Extended
/dev/hda5        37576098    39070079      746991   82  Linux swap / Solaris

---

### Post by naiya on 2007-09-22
> **Linux_Man said:**
> Did you make sure to give it swap space? 

Probably not - I don't know what that is.
How do I check?

---

### Post by Linux_Man on 2007-09-22
You do have swap space in your fdisk log. So thats not the problem.

---

### Post by Pumalite on 2007-09-22
hda5 is swap. What about your specs: processor, memory, graphics?

---

### Post by naiya on 2007-09-22
Hmmm... I don't have a system tab in 'System Monitor', just resources, processes & cpu usage... where else might I find the specs you're looking for...?

---

### Post by naiya on 2007-09-22
I mean 'processes resources & devices'...

---

### Post by Pumalite on 2007-09-22
Check System>Preferences>Hardware Information

---

### Post by PmDematagoda on 2007-09-22
Try Applications>System Tools>Sysinfo

Edit: You beat me again Pumalite, damn:)

---

### Post by ryanVickers on 2007-09-22
Is it possible you did an update to it with the update manager and not a clean install?  This usually results in pathetic failure - It's a good idea but doesn't work yet :)

---

### Post by naiya on 2007-09-22
odd - I have neither of those in those menus.... I have nothing under Applications>System Tools... except add/remove programs.

Can this info be found via terminal?

---

### Post by PmDematagoda on 2007-09-22
> **naiya said:**
> odd - I have neither of those in those menus.... I have nothing under Applications>System Tools... except add/remove programs.

Can this info be found via terminal?

That's weird, could you post a screen shot of your Applications>System Tools> ?

---

### Post by ryanVickers on 2007-09-22
Chances are whatever your looking for should actually be in System > Administration (or) Preferences

Just a guess :p

---

### Post by Pumalite on 2007-09-22
At the Terminal run:

sudo lshw

Post results.

---

### Post by naiya on 2007-09-22
> **ryanVickers said:**
> Is it possible you did an update to it with the update manager and not a clean install?  This usually results in pathetic failure - It's a good idea but doesn't work yet :)

Actually that's what I tried first, and yes it failed horribly. So I made a clean install from a disk. Everything works, just one thing at a time.

For a while, I had an issue with dependencies (gnome-cups-manager and python netcdf would not update) I thought it might be those that were causing the problem, but that problem was solved with aptitude... and still my system freezes. A hint though, I do notice that there is some weird 'graphic dissolving' of an icon when i click on it - and it precedes a crash...

---

### Post by naiya on 2007-09-22
naiya@ubuntunaiya:~$ sudo lshw
Password:
IDE

---

### Post by naiya on 2007-09-22
'IDE' is all it says..

---

### Post by Pumalite on 2007-09-22
Let me show you what it 'should' say(or something similar):

pumalite@pumalite-desktop:~$ sudo lshw
Password:
pumalite-desktop          
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: none
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=64923F33-7E7D-DA11-ABCF-C8E63BACDB5B
  *-core
       description: Motherboard
       product: P4P800SE
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: Rev 2.xx
       serial: MB-1234567890
       slot: DIMM B2
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080009 (11/19/2005)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: CPU 1
          size: 3200MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KB
             capacity: 16KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MB
             capacity: 1MB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 36
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM DDR Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM DDR Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: e0000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e0000000-efffffff
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: GeForce 7600 GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a2
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: iomemory:fd000000-fdffffff iomemory:c0000000-cfffffff iomemory:fc000000-fcffffff irq:16
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:eec0-eedf irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef00-ef1f irq:17
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
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef20-ef3f irq:18
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
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef40-ef5f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:febff800-febffbff irq:20
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
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network:0
                description: Ethernet interface
                product: 88E8001 Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 5
                bus info: pci@02:05.0
                logical name: eth0
                version: 13
                serial: 00:15:f2:a6:36:14
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.9 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
                resources: iomemory:feafc000-feafffff ioport:d800-d8ff irq:19
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: a
                bus info: pci@02:0a.0
                logical name: eth1
                version: 10
                serial: 00:08:a1:19:e7:52
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.132 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: ioport:d400-d4ff iomemory:feafbc00-feafbcff irq:19
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
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
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
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
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:fc00-fc0f iomemory:88100000-881003ff irq:18
           *-disk:0
                description: SCSI Disk
                product: ST3250820A
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 9QE21DVA
                size: 232GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 227GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 5938MB
                   capacity: 5938MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5938MB
                      capabilities: nofs
           *-disk:1
                description: SCSI Disk
                product: ST3250820A
                vendor: ATA
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 3.AA
                serial: 9QE21DJJ
                size: 232GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   capacity: 10001MB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   capacity: 1004MB
                   capabilities: primary nofs
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.1.0,3
                   logical name: /dev/sdb3
                   capacity: 222GB
                   capabilities: primary
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-H44N
                vendor: HL-DT-ST
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: RB01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
           *-disk:2
                description: SCSI Disk
                product: ST3250820A
                vendor: ATA
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/sdc
                version: 3.AA
                serial: 9QE21J1H
                size: 232GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sdc1
                   capacity: 227GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.1.0,2
                   logical name: /dev/sdc2
                   size: 5938MB
                   capacity: 5938MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdc5
                      capacity: 5938MB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400-41f irq:10
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:e800-e8ff ioport:ee80-eebf iomemory:febff400-febff5ff iomemory:febff000-febff0ff irq:21
pumalite@pumalite-desktop:~$ 

Try again.

---

### Post by naiya on 2007-09-22
wow... i did. same thing. 
see screenshot attached...

before 'IDE' comes up it briefly flashes 'PCI' then 'IDE'... nothing else.

---

### Post by Pumalite on 2007-09-22
Something is wrong, but I don't know what. Better save /home and data and do a clean install.

---

### Post by naiya on 2007-09-22
ok. after a restart (and closing the CD drive properly)
I get:

naiya@ubuntunaiya:~$ sudo lshw
Password:
ubuntunaiya
    description: Portable Computer
    product: Latitude C610
    vendor: Dell Computer Corporation
    serial: 9NYJF31
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-4E00-1059-804A-B9C04F463331
  *-core
       description: Motherboard
       product: Latitude C610
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A16 (05/16/2003)
          size: 64KB
          capacity: 448KB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect pcmciaboot int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile Intel(R) Pentium(R) III CPU - M  1200MHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.11.4
          slot: Microprocessor
          size: 798MHz
          capacity: 1333MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KB
             capacity: 32KB
             capabilities: internal varies unified
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KB
             capacity: 512KB
             clock: 66MHz (15ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 256MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM_A
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: DIMM_B
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: d0000000
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          resources: iomemory:d0000000-dfffffff
        *-pci:0
             description: PCI bridge
             product: 82830 830 Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Radeon Mobility M6 LY
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master vga_palette cap_list
                resources: iomemory:e0000000-e7ffffff ioport:c000-c0ff iomemory:fcff0000-fcffffff irq:11
        *-usb
             description: USB Controller
             product: 82801CA/CAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf80-bf9f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-29-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth0
                version: 78
                serial: 00:0b:db:db:70:06
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=3c59x driverversion=LK1.1.19 duplex=half link=no multicast=yes port=MII speed=10MB/s
                resources: ioport:ec80-ecff iomemory:f8fffc00-f8fffc7f irq:11
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1420
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:f8000000-f8000fff irq:11
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1420
                vendor: Texas Instruments
                physical id: 1.1
                bus info: pci@02:01.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:f8001000-f8001fff irq:11
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:bfa0-bfaf iomemory:25000000-250003ff irq:11
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: IC25N020ATCS04-0
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: CA2OA72A
                   serial: CSH204DMGAK0MF
                   size: 18GB
                   capacity: 18GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 17GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 729MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: IDE CD-ROM
                   product: SAMSUNG CD-ROM SN-124
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: q008
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:d800-d8ff ioport:dc80-dcbf irq:5
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             resources: ioport:d400-d4ff ioport:dc00-dc7f irq:5
     *-network
          description: Wireless interface
          product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 1
          bus info: pci@03:00.0
          logical name: wlan0
          version: 02
          serial: 00:14:bf:41:65:ab
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper ip=192.168.2.4 link=yes multicast=yes wireless=IEEE 802.11g
          resources: iomemory:f4000000-f4001fff irq:11
  *-battery
       product: CGR-B/838
       vendor: Panasonic
       physical id: 1
       slot: Left Module Bay
       capacity: 59200mWh
       configuration: voltage=14.8V
naiya@ubuntunaiya:~$

---

### Post by naiya on 2007-09-23
what should i look for?

---

### Post by Pumalite on 2007-09-23
You have low memory and complicated graphics (ATI). In that system I would run: Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
It would be easy to install and it would run fast in your system.

---

### Post by naiya on 2007-09-24
thanks - i'll do it.
appreciate the help...

---

