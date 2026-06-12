---
title: "[SOLVED] How to access/run webcam built into computer"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by jwill1515 on 2008-02-15
It;s built into the HP Pavilion dv9205us

---

### Post by spiderbatdad on 2008-02-15
I've seen other posts on these onboard cams. usually Ubuntu detects webcams fairly easily...perhaps not so with builtin cams. It looks like you are going to need a driver...supposedly here: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

I do not know how to install the driver. I got the link to the driver here:[http://www.gus-mg.org/dig/dv9205us.html](http://www.gus-mg.org/dig/dv9205us.html)

---

### Post by jwill1515 on 2008-02-15
I don't see anything there to download.

---

### Post by LaRoza on 2008-02-15
See: [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

---

### Post by jwill1515 on 2008-02-15
Which one do I need?

---

### Post by spiderbatdad on 2008-02-15
post ```
sudo lshw
``` lets see if we can identify your builtin cam.

---

### Post by jwill1515 on 2008-02-15
vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Turion(tm) 64 X2 Mobile TL50
          slot: Socket S1
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KB
             capacity: 64KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 2GB
          capacity: 2GB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             vendor: F7F7F73800000000
             physical id: 0
             serial: 00000000
             slot: DIMM 1
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM 667 MHz (1.5 ns)
             vendor: F7F7F73800000000
             physical id: 1
             serial: 00000000
             slot: DIMM 2
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-network
             description: Wireless interface
             product: BCM94311MCG wlan mini-PCI
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@0000:03:00.0
             logical name: eth1
             version: 01
             serial: 00:1a:73:1d:ee:fb
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
     *-display
          description: VGA compatible controller
          product: C51 [Geforce 6150 Go]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP51 PMU
          vendor: nVidia Corporation
          physical id: a.3
          bus info: pci@0000:00:0a.3
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3 module=amd74xx
        *-ide
             description: IDE Channel 0
             physical id: 0
             bus info: ide@0
             logical name: ide0
             clock: 66MHz
           *-cdrom
                description: DVD-RAM writer
                product: HL-DT-ST DVDRAM GSA-4084N
                physical id: 0
                bus info: ide@0.0
                logical name: /dev/hda
                version: KQ09
                serial: KYG71345713
                capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          logical name: scsi0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: SCSI Disk
             product: TOSHIBA MK1234GS
             vendor: ATA
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: AH00
             serial: Z6TJFCHCS
             size: 111GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume:0
                description: HPFS/NTFS partition
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                capacity: 80GB
                capabilities: primary bootable
           *-volume:1
                description: HPFS/NTFS partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                capacity: 6769MB
                capabilities: primary
           *-volume:2
                description: Linux filesystem partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                capacity: 956MB
                capabilities: primary
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                size: 23GB
                capacity: 23GB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1906MB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 21GB
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
        *-firewire
             description: FireWire (IEEE 1394)
             product: R5C832 IEEE 1394 Controller
             vendor: Ricoh Co Ltd
             physical id: 5
             bus info: pci@0000:07:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
        *-system:0
             description: Generic system peripheral
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.1
             bus info: pci@0000:07:05.1
             version: 19
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci latency=64 module=sdhci
        *-system:1 UNCLAIMED
             description: System peripheral
             product: R5C843 MMC Host Controller
             vendor: Ricoh Co Ltd
             physical id: 5.2
             bus info: pci@0000:07:05.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-system:2 UNCLAIMED
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.3
             bus info: pci@0000:07:05.3
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-system:3 UNCLAIMED
             description: System peripheral
             product: xD-Picture Card Controller
             vendor: Ricoh Co Ltd
             physical id: 5.4
             bus info: pci@0000:07:05.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:16:36:e9:c0:9b
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
     *-scsi
          physical id: 6
          bus info: usb@2:7
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Mass Storage
             vendor: CMOTECH
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 2.31
             size: 66MB
             capabilities: removable
             configuration: ansiversion=6
           *-disc
                physical id: 0
                logical name: /dev/sdb
                size: 66MB
jwill1515@jwill1515-laptop:~$

---

### Post by spiderbatdad on 2008-02-15
This list is provided by easycam for linux. it shows the supported cams.
ID ok

ID 046d:0920 Logitech, Inc. QuickCam Express
ID 0ac8:301b Z-Star Microelectronics Corp. Sansun SN-510 WebCam
ID 04fc:0561 Sunplus Technology Co., Ltd
ID 041e:4028 Creative Technology, Ltd
ID 046d:0901 Logitech, Inc. ClickSmart 510 
ID 046d:0960 Logitech, Inc. ClickSmart 420
ID 041e:4036 Creative Technology, Ltd Webcam Live
ID 041e:401e Creative Technology, Ltd WebCam NX Pro
ID 046d:0900 Logitech, Inc. ClickSmart 310
ID 0c45:60c0 Microdia
ID 041e:401d Creative Technology, Ltd WebCam NX Ultra
[B]ID 041e:401c Creative Technology, Ltd WebCam NX [PD1110]
ID 0c45:602d Microdia[/B]
ID 046d:08a2 Logitech, Inc.
ID 041e:401f Creative Technology, Ltd Webcam Notebook
ID 093a:2468 Pixart Imaging, Inc.
ID 046d:08ad Logitech, Inc.
ID 093a:2468 Pixart Imaging, Inc. CIF Single Chip
ID 041e:403a Creative Technology, Ltd WebCam NX Pro 2
ID 041e:4034 Creative Technology, Ltd


Note the one called Microdia and the vendor/products number attached to it. I looked at your lsusb output.

shown here:jwill1515@jwill1515-laptop:~$ lsusb
Bus 002 Device 003: ID 03f0:5811 Hewlett-Packard
**Bus 002 Device 002: ID 0c45:62c0 Microdia**
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 16d8:6803
Bus 001 Device 001: ID 0000:0000 

So, it looks like easycam should work for you. Follow instructions on this page. [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)
Sorry to be so slow in responding; took me a while to find the info.

---

### Post by jwill1515 on 2008-02-16
jwill1515@jwill1515-laptop:~$  /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
jwill1515@jwill1515-laptop:~$ ./etc/apt/sources.list
bash: ./etc/apt/sources.list: No such file or directory
jwill1515@jwill1515-laptop:~$ gksu gedit /etc/apt/sources.list
jwill1515@jwill1515-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release.gpg                                
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources     
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources        
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release                              
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages                              
Err [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages                              
  404 Not Found
Fetched 5B in 9s (1B/s)                                                        
Failed to fetch [http://blognux.free.fr/debian/dists/unstable/main/binary-amd64/Packages.gz](http://blognux.free.fr/debian/dists/unstable/main/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
jwill1515@jwill1515-laptop:~$

and then I got

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://blognux.free.fr/debian/dists/unstable/main/binary-amd64/Packages.gz:](http://blognux.free.fr/debian/dists/unstable/main/binary-amd64/Packages.gz:) 404 Not Found

---

### Post by spiderbatdad on 2008-02-16
As you can see the blognuts site was not available. You can comment it out of your sources.list with a # at the beginning, or delete it entirely. I'm not familiar with that list, as I don't use 64bit. Other than that looks like it ran fine. Did you get the easycam package going for your builtin webcam?

---

### Post by jwill1515 on 2008-02-16
No, nothing yet.

jwill1515@jwill1515-laptop:~$ gksu gedit /etc/apt/sources.list

comes back with

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

---

### Post by jwill1515 on 2008-02-16
What I did was for easycam2. Should i try the same thing witheasycam1, which was also available.

---

### Post by jwill1515 on 2008-02-16
How about this. I found this from the site LaRoza directed me to and then I did a search for Micridia. I don't know which one of the two choices to make because of the following statement (This driver supports the Video4Linux2 API only. If you want an enhanced driver with support for both Video4Linux1 and Video4Linux2 (working with any application), install the generic SN9CXXX binary-only driver:)


sn9c1xx-1.48.tar.gz Popular  	Version: 1.48
Submitted Date:  2007/9/1
Description:
Video4Linux2 driver for SN9C101, SN9C102, SN9C103, SN9C105, SN9C120 PC Camera Controllers.

This driver supports the Video4Linux2 API only. If you want an enhanced driver with support for both Video4Linux1 and Video4Linux2 (working with any application), install the generic SN9CXXX binary-only driver:

[http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7)

---

### Post by jwill1515 on 2008-02-16
After much trial and error I finally got the webcam working with the Cheese program. Everything on the computer is working now. Thanks for the help.

---

### Post by handitard on 2008-03-26
> **jwill1515 said:**
> jwill1515@jwill1515-laptop:~$  /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
jwill1515@jwill1515-laptop:~$ ./etc/apt/sources.list
bash: ./etc/apt/sources.list: No such file or directory
jwill1515@jwill1515-laptop:~$ gksu gedit /etc/apt/sources.list
jwill1515@jwill1515-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release.gpg                                
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources     
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources        
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release                              
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages                              
Err [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages                              
  404 Not Found
Fetched 5B in 9s (1B/s)                                                        
Failed to fetch [http://blognux.free.fr/debian/dists/unstable/main/binary-amd64/Packages.gz](http://blognux.free.fr/debian/dists/unstable/main/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
jwill1515@jwill1515-laptop:~$

and then I got

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://blognux.free.fr/debian/dists/unstable/main/binary-amd64/Packages.gz:](http://blognux.free.fr/debian/dists/unstable/main/binary-amd64/Packages.gz:) 404 Not Found

What a tool:KS:KS:KS:KS:KS

---

