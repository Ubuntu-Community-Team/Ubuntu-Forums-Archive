---
title: "[SOLVED] How do I : GAIM"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-21
1) Is there a way to connect to my GTalk contacts through GAIM  or any other messengers ?
I hear about Jabber, will I have to create a new Jabber account for it, or can I use my Google accounts?

2) How do I voice chat with my yahoo and msn contacts that I have already added in GAIM ? How do I switch on my in built web-cam for my contacts ?



Thanks for your help guys !

---

### Post by boredandblogging.com on 2007-05-21
1) Here are instructions from google with Pidgin, I'd think they would work with Gaim as well: [http://www.google.com/support/talk/bin/answer.py?answer=24073](http://www.google.com/support/talk/bin/answer.py?answer=24073)

Your gmail account is a jabber account as well. 

2) no idea.

---

### Post by fakie_flip on 2007-05-21
1. Yes, a simple search on google or this forum could answer your question.

[http://www.google.com/support/talk/bin/answer.py?answer=24073](http://www.google.com/support/talk/bin/answer.py?answer=24073)

2. Amsn allows you to use your webcam with the msn protocol.

```
sudo apt-get install amsn
```

Kopete lets you use your webcam with MSN and 1 or 2 more protocols.

```
sudo apt-get install kopete
```

Gaim-vv (Gaim with Video and Voice) is supposed to let you have video and voice chat. I doubt it works 100% perfect at all. I have not tried it myself.

[http://gaim-vv.sourceforge.net/](http://gaim-vv.sourceforge.net/)

For voice chat in Linux, Skype is highly recommended. It will allow you to voice chat with people using Windows and Mac, not just Linux. Follow my instruction to get it.

```
echo 'deb http://download.skype.com/linux/repos/debian/ stable non-free' | sudo tee -a /etc/apt/sources.list
sudo apt-get update && sudo apt-get install skype
```

Teamspeak also allows you to use voice chat in Linux. It is mostly for gamers. I suggest you try Skype first before Teamspeak.

```
sudo apt-get install teamspeak-client
```

Lets see what information Linux shows about your webcam. What do you get from running these commands?

```
lspci
sudo lshw -enable usb
```

If you want even more apps for voice chat, try Wengo Phone.

```
sudo apt-get install wengophone
```

And try Ekiga. It is included with your system. I have not had much luck with it though. Click on Applications>Internet>Ekiga Softphone. Let me know if this helps.

---

### Post by Inxsible on 2007-05-21
My lspci :
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
 

```

My sudo lshw -enable usb :
```

          width: 64 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MB
             capacity: 2MB
             capabilities: burst external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 2GB
          capacity: 2GB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             physical id: 0
             slot: DIMM 1
             size: 1GB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM Synchronous 533 MHz (1.9 ns)
             physical id: 1
             slot: DIMM 2
             size: 1GB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G70 [GeForce Go 7600]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: iomemory:dd000000-ddffffff iomemory:c0000000-cfffffff iomemory:dc000000-dcffffff ioport:2000-207f irq:16
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:de300000-de303fff irq:21
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth1
                version: 02
                serial: 00:19:d2:ac:7b:2e
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
                resources: iomemory:d8000000-d8000fff irq:16
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 82573L Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@05:00.0
                logical name: eth0
                version: 00
                serial: 00:1b:24:18:a8:b8
                capacity: 1GB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair
                resources: iomemory:da000000-da01ffff ioport:5000-501f irq:18
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1800-181f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1820-183f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Optical USB Mouse
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@3:1
                   version: 3.40
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1840-185f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Bluetooth wireless interface
                   product: HP Integrated Module
                   vendor: Broadcom Corp
                   physical id: 2
                   bus info: usb@4:2
                   version: 1.00
                   capabilities: bluetooth usb-2.00
                   configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1860-187f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:de304000-de3043ff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb
                   description: Video
                   product: USB 2.0 Camera
                   vendor: Sonix Technology Co., Ltd.
                   physical id: 4
                   bus info: usb@1:4
                   version: 2.10
                   serial: SN0001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480.0MB/s
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 5
                bus info: pci@07:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: iomemory:de000000-de0007ff irq:16
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 5.1
                bus info: pci@07:05.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64
                resources: iomemory:de000800-de0008ff irq:17
           *-system:1 UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 5.2
                bus info: pci@07:05.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: iomemory:de000c00-de000cff irq:11
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 5.3
                bus info: pci@07:05.3
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: iomemory:de001000-de0010ff irq:11
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 5.4
                bus info: pci@07:05.4
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: iomemory:de001400-de0014ff irq:11
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
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
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:1880-188f irq:18
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-851S
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.50
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi2
             logical name: scsi3
             logical name: scsi4
             logical name: scsi5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated scsi-host
             configuration: driver=ahci latency=0
             resources: ioport:18c8-18cf ioport:18ac-18af ioport:18c0-18c7 ioport:18a8-18ab ioport:18b0-18bf iomemory:de304400-de3047ff irq:20
           *-disk
                description: SCSI Disk
                product: Hitachi HTS54161
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: SB4O
                serial: SB2404SJJ3RYWE
                size: 149GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 24GB
                   capabilities: primary bootable
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 24GB
                   capabilities: primary
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 71GB
                   capabilities: primary
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   size: 28GB
                   capacity: 28GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 8785MB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 19GB
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 980MB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18e0-18ff irq:4

```

---

### Post by loell on 2007-05-21
> **Inxsible said:**
> 1) Is there a way to connect to my GTalk contacts through GAIM  or any other messengers ?
I hear about Jabber, will I have to create a new Jabber account for it, or can I use my Google accounts?

2) How do I voice chat with my yahoo and msn contacts that I have already added in GAIM ? How do I switch on my in built web-cam for my contacts ?


short answers: ;)

[http://www.gizmoproject.com]("http://www.gizmoproject.com") for calling yahoo / msn / gtalk users.


webcam enable instant messengers are

[gyachi]("http://gyachi.sourceforge.net") = yahoo messaging client

amsn = msn client with webcam.

kopete = all around IM client

---

### Post by fakie_flip on 2007-05-21
Sorry, I meant to ask for the output of lsusb, not lspci. Have your webcam plugged in while you get the output of those commands. So far I can tell that your camera is made Sonix Technology Co., Ltd.

---

### Post by Inxsible on 2007-05-22
lsusb :

```

Bus 001 Device 003: ID 0c45:62c0 Microdia 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  

```

---

### Post by fakie_flip on 2007-05-22
[http://dollarunderscore.wordpress.com/2006/10/18/how-to-get-the-webcam-on-the-hp-dv2000-working/](http://dollarunderscore.wordpress.com/2006/10/18/how-to-get-the-webcam-on-the-hp-dv2000-working/)

---

