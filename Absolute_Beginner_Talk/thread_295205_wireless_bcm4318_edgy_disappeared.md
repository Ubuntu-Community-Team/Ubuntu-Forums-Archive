---
title: "wireless bcm4318 edgy disappeared"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by fatneck on 2006-11-07
Hi all,

After following every single howto I could find to try and get wireless working, I'm again left with a fresh install of Edgy that has no wireless setting in System > Admin > Networking.

Anyone know a quick set of command lines to get this back?

I fear after more than a week struggling with this that I'm going back to XP - something that works out the box. Any help greatly appreciated!

Cheers

---

### Post by mattkirwan on 2006-11-07
Fatneck,
Hows it going? I have been using linux for a relatively short period of time now, firstly I would recommend trying to not get frustrated, there are far to many good things which come from ubuntu and indeed anything GNU/Linux. [Take a look at my first post on the ubuntu forums]("http://ubuntuforums.org/showthread.php?t=243050")

I guess your wireless is built into the laptop?

In a terminal type:

```
iwconfig
```

and then post the output here.

Matt
nawrik.com

---

### Post by fatneck on 2006-11-07
Hi - yes, the wireless is built in. The dodgy BCM4318 by all accounts, and the rev 2 of that to make matters worse.

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Cheers

---

### Post by mattkirwan on 2006-11-07
Click on System > Administration > Device Manager


In the window that opens, is there any reference to 'wireless' or your wireless card?

Also type in a terminal:

```
sudo lshw
```

type your password, and paste the output here.

---

### Post by fatneck on 2006-11-07
Here it is in device manager:

BCM4318 [AirForce One 54g] 802.11g

and here is the output:

description: Notebook
    product: HP Compaq nx6125 (PY418ET#ABU)
    vendor: Hewlett-Packard
    version: F.11
    serial: CND5290TCX
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=35953F6F-92FA-D911-1AA4-66990A267529
  *-core
       description: Motherboard
       product: 308B
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 45.26
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68DTT Ver. F.11 (08/29/2006)
          size: 128KB
          capacity: 960KB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 Mobile ML-28
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Turion(tm) 64 Mobile ML-28
          slot: U10
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: burst external write-back unified
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB
        *-bank:0
             description: SODIMM DDR Synchronous 333 MHz (3.0 ns)
             product: NT256D64SH8C0GM-6K
             vendor: 7F7F7F0B00000000
             physical id: 0
             serial: C1661503
             slot: DIMM #1
             size: 256MB
             width: 64 bits
             clock: 333MHz (3.003ns)
        *-bank:1
             description: SODIMM DDR Synchronous 333 MHz (3.0 ns)
             product: NT256D64SH8C0GM-6K
             vendor: 7F7F7F0B00000000
             physical id: 1
             serial: 186D150C
             slot: DIMM #2
             size: 256MB
             width: 64 bits
             clock: 333MHz (3.003ns)
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: ATI Radeon XPRESS 200M 5955 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@01:05.0
                version: 00
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:c0000000-cfffffff ioport:6000-60ff iomemory:d8300000-d830ffff irq:5
        *-pci:1
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:d8400000-d8400fff irq:225
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
              *-usb:0
                   description: Bluetooth wireless interface
                   product: HP integrated Bluetooth module
                   vendor: Broadcom
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.17
                   capabilities: bluetooth usb-1.10
                   configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
              *-usb:1
                   description: Mouse
                   product: Mouse
                   vendor: Belkin
                   physical id: 3
                   bus info: usb@1:3
                   version: 1.00
                   capabilities: usb-1.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:d8401000-d8401fff irq:225
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: Fingerprint Sensor
                   vendor: AuthenTec, Inc.
                   physical id: 1
                   bus info: usb@2:1
                   version: 6.21
                   capabilities: usb-1.10
                   configuration: maxpower=100mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:d8402000-d8402fff irq:225
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@00:14.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             resources: ioport:8200-820f iomemory:d8403000-d84033ff
        *-ide
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller ATI
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ATIIXP_IDE
             resources: ioport:7010-701f irq:217
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   description: ATA Disk
                   product: FUJITSU MHT2060AH PL
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 006C
                   serial: NP1WT562EAN5
                   size: 55GB
                   capacity: 55GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 39GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 7020MB
                      capabilities: primary
                 *-volume:2
                      description: Linux filesystem partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 9146MB
                      capabilities: primary
                 *-volume:3
                      description: Linux swap / Solaris partition
                      physical id: 4
                      bus info: ide@0.0,4
                      logical name: /dev/hda4
                      capacity: 1058MB
                      capabilities: primary nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD writer
                   product: HL-DT-ST DVD-RW GWA-4082N
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: CC10
                   serial: 08E02095CE23
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-isa UNCLAIMED
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
        *-pci:3
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
           *-network:0
                description: Ethernet interface
                product: NetXtreme BCM5788 Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@02:01.0
                logical name: eth0
                version: 03
                serial: 00:0f:b0:72:fe:1a
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.59.1 duplex=full firmware=5788-v3.26 ip=192.168.1.102 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: iomemory:d8000000-d800ffff irq:169
           *-network:1 UNCLAIMED
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@02:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                resources: iomemory:d8010000-d8011fff irq:5
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:d8012000-d8012fff irq:177
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@02:04.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:d8013000-d80137ff iomemory:d8014000-d8017fff irq:233
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 4.3
                bus info: pci@02:04.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1
                resources: iomemory:d8018000-d8019fff irq:233
           *-system
                description: Generic system peripheral
                product: PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
                vendor: Texas Instruments
                physical id: 4.4
                bus info: pci@02:04.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci
                resources: iomemory:d801a000-d801a0ff iomemory:d801b000-d801b0ff iomemory:d801c000-d801c0ff irq:233
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ATI IXP AC97 controller
             resources: iomemory:d8404000-d84040ff irq:209
        *-communication
             description: Modem
             product: ATI SB400 - AC'97 Modem Controller
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@00:14.6
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: generic bus_master cap_list
             configuration: driver=ATI IXP MC97 controller
             resources: iomemory:d8405000-d84050ff irq:209
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz

---

### Post by mattkirwan on 2006-11-07
From what I can see it has recognised your wireless card.

does the laptop have a switch to activate the wireless?

If so, turn it on and restart your computer. Make sure it is on when the computer is booting.

When your laptop has rebooted, with the wireless on.

Type:

```
sudo lshw
```
again and post the output.

---

### Post by fatneck on 2006-11-07
Yes it does, and I made sure it was on during reboot. Here is the output:

description: Notebook
    product: HP Compaq nx6125 (PY418ET#ABU)
    vendor: Hewlett-Packard
    version: F.11
    serial: CND5290TCX
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=35953F6F-92FA-D911-1AA4-66990A267529
  *-core
       description: Motherboard
       product: 308B
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 45.26
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68DTT Ver. F.11 (08/29/2006)
          size: 128KB
          capacity: 960KB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 Mobile ML-28
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Turion(tm) 64 Mobile ML-28
          slot: U10
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: burst external write-back unified
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB
        *-bank:0
             description: SODIMM DDR Synchronous 333 MHz (3.0 ns)
             product: NT256D64SH8C0GM-6K
             vendor: 7F7F7F0B00000000
             physical id: 0
             serial: C1661503
             slot: DIMM #1
             size: 256MB
             width: 64 bits
             clock: 333MHz (3.003ns)
        *-bank:1
             description: SODIMM DDR Synchronous 333 MHz (3.0 ns)
             product: NT256D64SH8C0GM-6K
             vendor: 7F7F7F0B00000000
             physical id: 1
             serial: 186D150C
             slot: DIMM #2
             size: 256MB
             width: 64 bits
             clock: 333MHz (3.003ns)
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: ATI Radeon XPRESS 200M 5955 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@01:05.0
                version: 00
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:c0000000-cfffffff ioport:6000-60ff iomemory:d8300000-d830ffff irq:5
        *-pci:1
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:d8400000-d8400fff irq:225
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
              *-usb:0
                   description: Bluetooth wireless interface
                   product: HP integrated Bluetooth module
                   vendor: Broadcom
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.17
                   capabilities: bluetooth usb-1.10
                   configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
              *-usb:1
                   description: Mouse
                   product: Mouse
                   vendor: Belkin
                   physical id: 3
                   bus info: usb@1:3
                   version: 1.00
                   capabilities: usb-1.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:d8401000-d8401fff irq:225
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-10-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: Fingerprint Sensor
                   vendor: AuthenTec, Inc.
                   physical id: 1
                   bus info: usb@2:1
                   version: 6.21
                   capabilities: usb-1.10
                   configuration: maxpower=100mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:d8402000-d8402fff irq:225
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@00:14.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             resources: ioport:8200-820f iomemory:d8403000-d84033ff
        *-ide
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller ATI
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ATIIXP_IDE
             resources: ioport:7010-701f irq:217
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   description: ATA Disk
                   product: FUJITSU MHT2060AH PL
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 006C
                   serial: NP1WT562EAN5
                   size: 55GB
                   capacity: 55GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 39GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 7020MB
                      capabilities: primary
                 *-volume:2
                      description: Linux filesystem partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 9146MB
                      capabilities: primary
                 *-volume:3
                      description: Linux swap / Solaris partition
                      physical id: 4
                      bus info: ide@0.0,4
                      logical name: /dev/hda4
                      capacity: 1058MB
                      capabilities: primary nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD writer
                   product: HL-DT-ST DVD-RW GWA-4082N
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: CC10
                   serial: 08E02095CE23
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-isa UNCLAIMED
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
        *-pci:3
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
           *-network:0
                description: Ethernet interface
                product: NetXtreme BCM5788 Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@02:01.0
                logical name: eth0
                version: 03
                serial: 00:0f:b0:72:fe:1a
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.59.1 duplex=full firmware=5788-v3.26 ip=192.168.1.102 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: iomemory:d8000000-d800ffff irq:169
           *-network:1 UNCLAIMED
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@02:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                resources: iomemory:d8010000-d8011fff irq:5
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:d8012000-d8012fff irq:177
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@02:04.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:d8013000-d80137ff iomemory:d8014000-d8017fff irq:233
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 4.3
                bus info: pci@02:04.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1
                resources: iomemory:d8018000-d8019fff irq:233
           *-system
                description: Generic system peripheral
                product: PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
                vendor: Texas Instruments
                physical id: 4.4
                bus info: pci@02:04.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci
                resources: iomemory:d801a000-d801a0ff iomemory:d801b000-d801b0ff iomemory:d801c000-d801c0ff irq:233
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ATI IXP AC97 controller
             resources: iomemory:d8404000-d84040ff irq:209
        *-communication
             description: Modem
             product: ATI SB400 - AC'97 Modem Controller
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@00:14.6
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: generic bus_master cap_list
             configuration: driver=ATI IXP MC97 controller
             resources: iomemory:d8405000-d84050ff irq:209
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz

BTW your photos make Scotland look pretty awesome.

---

### Post by mattkirwan on 2006-11-07
One more thing bfore asking for outside help!!!

Right click on the network monitor icon (next to the volume control at the top right)

select properties.

Under 'CONNECTION':

Name:

Rather than use the drop down menu, type:

eth1 - probably in place of 'lo' or 'eth0'


Does a wireless bar kick in at the bottom?

---

### Post by mattkirwan on 2006-11-07
Thankyou, it's not my photography, it's Scotland - it is a very beautiful place 

(very rare for an Englishman to say that!!!!)

---

### Post by fatneck on 2006-11-07
...especially after the last 6N!

Nope, no wireless bar kicks in and the STATUS under CONNECTION says: Error.

Thanks for your help anyway. I'm going to resinstall Edgy I think as there is nothing on here anyway. Then I will have a brand new install to play with, although I only reinstalled earlier this evening anyway.

Cheers.

---

### Post by andrinho on 2006-11-07
@fatneck:

I've got exactly the same laptop and I tried a lot of things to get the broadcom working. If you follow this howto it's going to be working in 5 minutes:
[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+wireless](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+wireless)

andrinho

---

### Post by fatneck on 2006-11-08
Followed the guide, including the new kernel needed for 64 bit and now I am left with no wireless choice in System > Admin > Networking. 

It seemed to run the script successfully however. I did this immediately after installing Edgy again.

XP is really beckoning now, or does anyone know of a linux distor that supports wireless out of the box?

---

