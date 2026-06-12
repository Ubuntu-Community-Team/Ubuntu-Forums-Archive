---
title: "Internet not working."
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by polyz on 2008-04-14
I have openSUSE on this computer and just installed ubuntu 6.06 LTS for my other computer (very old and 7.04 wouldn't work on it). So after installation the internet didn't work. I have the internet plugged from my onboard internet jack thingy to my D-Link (linux compatible) router... I know the router should be working since i tried switching with this pc's cable. I tried different cables so I know it's not the cable. It's something on the computer. Also I have an old internet card in there which i tried to use after i found that the onboard wasn't working. both don't work.

It's very unusual...


thanks
-Polyz


(Going for dinner after posting this - will be back ~20mins)

---

### Post by PetePete on 2008-04-14
can you post the results of the command:
ifconfig

and 
sudo lshw

(the latter to ensure that the nic is actually registered and functional)

---

### Post by polyz on 2008-04-14
> **PetePete said:**
> can you post the results of the command:
ifconfig

and 
sudo lshw

(the latter to ensure that the nic is actually registered and functional)

thank god I had a flash drive handy to copy & paste into word pad and transfer to this computer!!!

here it is: (this is my old crappy computer BTW so don't make fun of the crappyness)





mike@mike-desktop:~$
mike@mike-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D3:C1:AA:E0
          inet6 addr: fe80::213:d3ff:fec1:aae0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:14490 (14.1 KiB)
          Interrupt:217 Base address:0x2800

eth2      Link encap:Ethernet  HWaddr 00:48:54:1A:94:17
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0xc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2940 (2.8 KiB)  TX bytes:2940 (2.8 KiB)

mike@mike-desktop:~$
mike@mike-desktop:~$ sudo lshw
mike-desktop
    description: Desktop Computer
    product: MS-7191
    vendor: MSI
    version: 1.0
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: MS-7191
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012 (11/22/2005)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.15.2
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KB
             capacity: 128KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KB
             capacity: 512KB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM SDRAM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM SDRAM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@01:05.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f0000000-f7ffffff ioport:d800-d8ff iomemory:feaf0000-feafffff irq:10
        *-ide:0
             description: IDE interface
             product: ATI 437A Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=sata_sil
             resources: ioport:b800-b807 ioport:b400-b403 ioport:b000-b007 ioport:a800-a803 ioport:a400-a40f iomemory:fe9fbc00-fe9fbdff irq:185
        *-ide:1
             description: IDE interface
             product: ATI 4379 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@00:12.0
             logical name: scsi2
             logical name: scsi3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=sata_sil
             resources: ioport:a000-a007 ioport:9800-9803 ioport:9400-9407 ioport:9000-9003 ioport:8800-880f iomemory:fe9fb800-fe9fb9ff irq:193
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:fe9fa000-fe9fafff irq:209
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-26-386 ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:fe9f9000-fe9f9fff irq:209
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-26-386 ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:fe9f8000-fe9f8fff irq:209
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-26-386 ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: DataTraveler 2.0
                   vendor: Kingston
                   physical id: 1
                   bus info: usb@3:1
                   logical name: scsi5
                   version: 2.00
                   serial: 899000000000000000000025
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: DataTraveler 2.0
                      vendor: Kingston
                      physical id: 0.0.0
                      bus info: scsi@5:0.0.0
                      logical name: /dev/sda
                      version: 1.00
                      size: 988MB
                      capabilities: removable
                      configuration: ansiversion=2
                    *-disc
                         physical id: 0
                         logical name: /dev/sda
                         size: 988MB
                         capabilities: partitioned partitioned:dos
                       *-volume
                            description: FAT16 partition
                            physical id: 1
                            logical name: /dev/sda1
                            capacity: 987MB
                            capabilities: primary
        *-serial UNCLAIMED
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@00:14.0
             version: 81
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             resources: ioport:b00-b0f iomemory:20100000-201003ff
        *-ide:2
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller ATI
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ATIIXP_IDE
             resources: ioport:ff00-ff0f irq:201
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   description: ATA Disk
                   product: ST340810A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 3.39
                   serial: 5FB9QZS2
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 36GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 1286MB
                      capabilities: extended partitioned partitioned:extended
              *-cdrom
                   description: DVD reader
                   product: SAMSUNG DVD-ROM SD-612
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: bp05
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdb
        *-multimedia
             description: Multimedia controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:fe9e8000-fe9ebfff irq:201
        *-isa UNCLAIMED
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@02:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:c1:aa:e0
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full link=yes multicast=yes port=MII speed=100MB/s
                resources: ioport:e400-e4ff iomemory:febff800-febff8ff irq:217
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@02:01.0
                logical name: eth2
                version: 10
                serial: 00:48:54:1a:94:17
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
                resources: ioport:e800-e8ff iomemory:febffc00-febffcff irq:177
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@02:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:febff000-febff7ff ioport:e000-e07f irq:177
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration          vendor: Advanced Micro Devices [AMD]
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
mike@mike-desktop:~$
mike@mike-desktop:~$

---

### Post by polyz on 2008-04-14
bump.

---

### Post by polyz on 2008-04-14
bump?

---

### Post by louieb on 2008-04-14
Try to get an IP address via DHCP from you router.
```
sudo dhclient
```

Looks like that should work. Post the output if it doesn't. 
Also post the output of** ifconfig** if it is different after running **dhclient.**

---

### Post by polyz on 2008-04-14
> **louieb said:**
> Try to get an IP address via DHCP from you router.
```
sudo dhclient
```

Looks like that should work. Post the output if it doesn't. 
Also post the output of** ifconfig** if it is different after running **dhclient.**

sorry for long wait - no one was replying.

mike@mike-desktop:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:13:d3:c1:aa:e0
Sending on   LPF/eth0/00:13:d3:c1:aa:e0
Listening on LPF/eth2/00:48:54:1a:94:17
Sending on   LPF/eth2/00:48:54:1a:94:17
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
mike@mike-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D3:C1:AA:E0
          inet6 addr: fe80::213:d3ff:fec1:aae0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:10728 (10.4 KiB)
          Interrupt:217 Base address:0x6800

eth2      Link encap:Ethernet  HWaddr 00:48:54:1A:94:17
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0x4c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

mike@mike-desktop:~$

---

### Post by superprash2003 on 2008-04-14
is eth0 or eth2 connected to the router?

---

### Post by louieb on 2008-04-14
i guess you tried running dhclient with the wire plugged into one port then the other. Most routers are set up to be a DHCP server.

Kinda hard to think both NICs are bad. alto that is the only reason I've ever had trouble making a wired connection. Ubuntu sees both NICs and has there hardware (MAC) address. 

kinda out of ideas here. one more thing to try.
```
sudo ifdown eth0
```
then
```
sudo ifup eth0
```

try it with eth2 also. 
Kinda puzzled - more that once I've used some old NIC bought a swap meet and haven't run into one that did't work

---

### Post by polyz on 2008-04-14
> **superprash2003 said:**
> is eth0 or eth2 connected to the router?

etho0 i think (the onboard one) is currently connected to my D-Link router which is connected to the modem or what ever its called which is connected to the wall. Also I have fairly slow internet speed.

:confused:

still not working.

---

