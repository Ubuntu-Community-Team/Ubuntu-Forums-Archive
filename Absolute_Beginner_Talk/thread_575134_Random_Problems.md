---
title: "Random Problems"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by KIFIKA on 2007-10-13
I've been using ubuntu for a little over a year now, and every few months it seems to give me this problem till i do a clean install...its very inconvineant. 

1. it randomly slows down 
2. it will randomly freeze, seemingly unprovoked or with something simple as internet browsing

also, i have flash 9 but the youtube videos and pretty much antyhing that requires flash streams insanly slow and laggy.. i'm paying 60 bucks a month for high speed internet to avoid this, can anyone help? 

im not sure on my computer specs, nothing fancy though.  :\

---

### Post by Pumalite on 2007-10-13
Have you ran a memtest?
Post:
df -h
lshw

---

### Post by KIFIKA on 2007-10-13
> Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              38G  7.9G   28G  23% /
varrun                118M  104K  117M   1% /var/run
varlock               118M     0  118M   0% /var/lock
procbususb            118M   88K  118M   1% /proc/bus/usb
udev                  118M   88K  118M   1% /dev
devshm                118M     0  118M   0% /dev/shm
lrm                   118M   33M   85M  29% /lib/modules/2.6.20-16-generic/volatile
/dev/hdc              699M  699M     0 100% /media/cdrom0
padula@padula-desktop:~$ 



then i did sudo lshw, which made this long string of stuff happened, but nothing apparent | was anything imediate supposed to happen? or what?

---

### Post by Pumalite on 2007-10-13
Post the output of lshw.

---

### Post by KIFIKA on 2007-10-13
> padula-desktop            
    description: Desktop Computer
    product: 1234567890
    vendor: Uknown Chassis Manufacture
    version: 1234567890
    serial: 1234567890
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 062710 (07/15/97                        )
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Duron(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.3.1
          slot: Sockey-A
          size: 900MHz
          capacity: 1200MHz
          width: 32 bits
          clock: 66MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 128KB
             capacity: 1MB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 64KB
             capacity: 1MB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 239MB
     *-pci
          description: Host bridge
          product: 730 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: d0000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
          resources: iomemory:d0000000-d3ffffff
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 0.1
             bus info: pci@00:00.1
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=SIS_IDE latency=16
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:ff00-ff0f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: ST380011A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 3.16
                   serial: 3JV5L9PZ
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 73GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 682MB
                      capacity: 682MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 682MB
                         capabilities: nofs
              *-disk:1
                   description: ATA Disk
                   product: Maxtor 6E040L0
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: NAR61FA0
                   serial: E1RC0M0E
                   size: 38GB
                   capacity: 38GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 37GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.1,2
                      logical name: /dev/hdb2
                      size: 682MB
                      capacity: 682MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hdb5
                         capacity: 682MB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: SAMSUNG CDRW/DVD SM-348B
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: T502
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-isa
             description: ISA bridge
             product: SiS85C503/5513 (LPC Bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=sis630_smbus latency=0
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.1
             bus info: pci@00:01.1
             logical name: eth0
             version: 82
             serial: 00:07:95:36:4d:0a
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=71.232.172.171 latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
             resources: ioport:d400-d4ff iomemory:cfff7000-cfff7fff irq:5
        *-usb:0
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.3
             bus info: pci@00:01.3
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:cfffd000-cfffdfff irq:3
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.2
             bus info: pci@00:01.2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:cfffc000-cfffcfff irq:3
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-multimedia:0
             description: Multimedia audio controller
             product: SiS PCI Audio Accelerator
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.4
             bus info: pci@00:01.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Trident4DWaveAudio latency=64 maxlatency=24 mingnt=2
             resources: ioport:d800-d8ff iomemory:cfffe000-cfffefff irq:11
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master vga_palette
           *-display
                description: VGA compatible controller
                product: 630/730 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@01:00.0
                version: 31
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga cap_list
                configuration: latency=0
                resources: iomemory:c0000000-c7ffffff iomemory:cfee0000-cfefffff ioport:bc00-bc7f
        *-multimedia:1
             description: Multimedia video controller
             product: Bt878 Video Capture
             vendor: Brooktree Corporation
             physical id: b
             bus info: pci@00:0b.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=bttv latency=64 maxlatency=40 mingnt=16
             resources: iomemory:cfdfc000-cfdfcfff irq:5
        *-multimedia:2 UNCLAIMED
             description: Multimedia controller
             product: Bt878 Audio Capture
             vendor: Brooktree Corporation
             physical id: b.1
             bus info: pci@00:0b.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=64 maxlatency=255 mingnt=4
             resources: iomemory:cfdfd000-cfdfdfff irq:5


hmm :\

---

### Post by Pumalite on 2007-10-13
Plug in another stick of RAM

---

