---
title: "Linux hates me"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by sdrawkcaBdepyTI on 2007-06-04
It seems like I've been having a lot of really bad luck with installing Dapper Drake in a dual boot with Windows XP on my system. My ethernet card and all of my USB ports are not being recognized by the system, and now I can't even log in anymore because ubuntu has stopped recognizing my keyboard (I'm logged on XP right now). I tried lshw and got the following:

brian-desktop
    description: Desktop Computer
    product: RC663AA-ABA a1640n
    vendor: HP Pavilion 061
    version: 0nx1114RE101BUCKE00
    serial: MXF6400J56 NA680
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=desktop uuid=80DBED2C-3EC1-1110-AD35-DCB6513D7263
  *-core
       description: Motherboard
       product: Buckeye
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.05
       serial: MS1C69S31700307
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.07 (08/31/2006)
          size: 128KB
          capacity: 960KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: Socket 775
          size: 1866MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: d
             slot: L2 Cache
             size: 2MB
             capacity: 2MB
             capabilities: synchronous internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: f
             slot: L3 Cache
             capabilities: synchronous internal varies
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
     *-cpu:1
          description: CPU
          product: ( )
          vendor: Intel
          physical id: 5
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: Socket 775
          size: 1866MHz
          capacity: 3800MHz
          clock: 266MHz
          capabilities: vmx ht
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: c
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: e
             slot: L2 Cache
             size: 2MB
             capacity: 2MB
             capabilities: synchronous internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 10
             slot: L3 Cache
             capabilities: synchronous internal varies
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GB
             width: 64 bits
             clock: 533MHz (1.87617ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
        *-bank:2
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GB
             width: 64 bits
             clock: 533MHz (1.87617ns)
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
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
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 02
             size: 256MB
             width: 64 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:fdd00000-fddfffff iomemory:e0000000-efffffff ioport:ff00-ff07 irq:137
        *-network UNCLAIMED
             description: Ethernet controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@00:19.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:fdfc0000-fdfdffff iomemory:fdfff000-fdffffff ioport:fe00-fe1f irq:153
        *-usb:0 UNCLAIMED
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci
             resources: ioport:fd00-fd1f
        *-usb:1 UNCLAIMED
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci
             resources: ioport:fc00-fc1f
        *-usb:2 UNCLAIMED
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci cap_list
             resources: iomemory:fdffe000-fdffe3ff
        *-multimedia
             description: Multimedia controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:fdff4000-fdff7fff irq:161
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3 UNCLAIMED
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci
             resources: ioport:fb00-fb1f
        *-usb:4 UNCLAIMED
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci
             resources: ioport:fa00-fa1f
        *-usb:5 UNCLAIMED
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci
             resources: ioport:f900-f91f
        *-usb:6 UNCLAIMED
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci cap_list
             resources: iomemory:fdffd000-fdffd3ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant
                physical id: 0
                bus info: pci@03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:fdee0000-fdeeffff ioport:df00-df07
           *-firewire UNCLAIMED
                description: FireWire (IEEE 1394)
                product: FW323
                vendor: Agere Systems
                physical id: 1
                bus info: pci@03:01.0
                version: 70
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                resources: iomemory:fdeff000-fdefffff
        *-isa UNCLAIMED
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-storage
             description: RAID bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             logical name: scsi3
             logical name: scsi4
             logical name: scsi5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list emulated scsi-host
             configuration: driver=ahci
             resources: ioport:f800-f807 ioport:f700-f703 ioport:f600-f607 ioport:f500-f503 ioport:f400-f41f iomemory:fdffc000-fdffc7ff irq:193
           *-disk
                description: SCSI Disk
                product: WDC WD2500JS-60N
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WCANK5982365
                size: 232GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 166GB
                   capabilities: primary bootable
              *-volume:1
                   description: W95 FAT32 (LBA) partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 8848MB
                   capabilities: primary
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 55GB
                   capabilities: primary
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 2431MB
                   capabilities: extended partitioned partitioned:extended
           *-cdrom
                description: DVD-RAM writer
                product: CD/DVDW TS-H653L
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0314
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: iomemory:fdffb000-fdffb0ff ioport:500-51f irq:145


Anyway, I'd really like to make a move to linux, but I'm not very good with it yet and have no idea how to fix this type of problem. Please help!!!! 


Thanks in advance,
Brian

---

### Post by daimaru on 2007-06-04
just posting since no one else has answered yet. y dapper? why dont u try if if works with feisty? maybe all will be good then. i mean higher numbers :) 7.04 = more compatible. at least one would assume.

---

### Post by Rocket2DMn on 2007-06-04
I agree with daimaru
I mean, you ARE running a Core 2 @ 1.86ghz with 2 gigs of RAM.  Best to stay up to date at the start, esp. if your hardware can handle it.

---

### Post by steveneddy on 2007-06-04
That's a mighty long list.

Use Feisty.

---

### Post by Marious on 2007-06-04
YAY FEISTY. As the other have said, not sure why you have issues with Dapper but I would most definably make the move to Feisty, it gets better everyday. If anything d/l the Live CD and give it a try it should not have the issues you are listing, makes no sense that it does, the fact that it does not recognize the keyboard is kind of strange, but it does happen, and it should be recognizing all your hardware, I have issues when it comes to an external hard drive I have but it probably because it's on one of those external hard drive cases that are from over sea's and they seem to have issues sometimes. Does it boot to Grub? and doe the issue occur when it boots to Dapper? Any issues with the mouse? Is either device connected via USB or PS/2? As you will see many times it helps if you provide more info, the more info the better. Dont give up on Linux its a great system, I am also new to it and everyday I love it more.

Marious

---

### Post by Songwind on 2007-06-05
Out of curiosity, does it work with a Live CD?

If the Live CD works, then you've problem got a configuration problem on your system.  If the Live CD has the same problems, that makes it more likely to be a compatibility issue.

---

### Post by sdrawkcaBdepyTI on 2007-06-06
Thanks for all the advice! I ended up trying Feisty and everything seems to work now - firewire, usb, ethernet, palm synch. The system is so fast!! :D

---

### Post by xfile087 on 2007-06-26
Just wanted to say i've been looking for a command like lshw for a while now - i'm a bit of a n00b so thanks and i'm glad it's all working now!

---

