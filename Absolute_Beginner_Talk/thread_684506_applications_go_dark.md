---
title: "applications go dark"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by loza on 2008-02-01
Hi all

A very weird thing has started to happen on my Gutsy 7.10 laptop.

Every no and then when I'm switching between directories in nautilus nothing happens, the mouse still moves ok but the window that has focus slowly goes dark - like grayed out for some reason.

The only thing to do then is to force a quit.

I have notice this happens in firefox too and other apps.

Do I have a virus?
Or is it my processes going to sleep for some reason?
Is my installation of 7.10 broken?

Any advice would be greatly appreciated.

thanks

loza

---

### Post by jan quark on 2008-02-01
what are your specs? rocessor ? ram? graphic?

pls post the result of the following commands

```
lspci
```

```
lshw
```


are you running compiz?

---

### Post by Fizzzy on 2008-02-01
I may be wrong, but i'm pretty sure that is the equivilent of a window going out of focus in Vista, it means it's not responding.
I would first assume it would be your computer specs, or if your trying to do a big task.
I may be completely wrong about this, but i'm pretty sure that would be the problem.

---

### Post by LostMagix on 2008-02-01
I am thinking it is most like your compiz crash handler, mine does the same thing.


Does it happen with many windows/programs open or is it at random....

---

### Post by loza on 2008-02-01
Hi there

The lspci command yields the following:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)


And the lshw yields the following (there's rather a lot!):

    description: Notebook
    product: Satellite PRO L10
    vendor: TOSHIBA
    version: PSL15E-00D003EN
    serial: 65048769W
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific chassis=notebook uuid=20BA6DA7-BB48-D811-BEB2-00C09FA3329E
  *-core
       description: Motherboard
       product: Satellite PRO L10
       vendor: TOSHIBA
       physical id: 0
       version: Rev 1.0
       serial: 65048769W
       slot: No Jumper On This Platform.
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V2.00 (04/13/2005)
          size: 107KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: uFCPGA2
          size: 1400MHz
          capacity: 1400MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MB
             capacity: 1MB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 1GB
          capacity: 3GB
        *-bank:0
             description: DIMM SRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM 0
             size: 512MB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM 1
             size: 512MB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-system:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-system:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-pcmcia
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:c0:9f:a3:32:9e
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.72 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-network:1 UNCLAIMED
                description: Ethernet controller
                product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
                vendor: Linksys, A Division of Cisco Systems
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=32 mingnt=32
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: Hitachi HTS54161
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SB4O
                serial: SB0444SJK2KGVE
                size: 149GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 85GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 1027MB
                   capabilities: primary
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 61GB
                   capabilities: primary
              *-volume:3
                   description: Linux swap / Solaris partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 1906MB
                   capabilities: primary nofs
           *-cdrom
                description: DVD reader
                product: UJDA760 DVD/CDRW
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.51
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@2:2.1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: DVD-RAM writer
             product: DVD Writer 1040d
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom2
             logical name: /dev/dvd2
             logical name: /dev/scd1
             logical name: /dev/sr1
             version: EH24
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: status=open
  *-battery
       description: Lithium Ion Battery
       product: Sanyo
       vendor: Sanyo
       physical id: 1
       slot: Right Side
       capacity: 4400mWh
       configuration: voltage=14.8V


Do you think my harddrive is on the way out??

many thanks for the reply so quick.

loza

---

### Post by jan quark on 2008-02-01
next time put the output in code bracket 
its this hash mark on the writing panel :)

```
like that code
```

your specs are allright

do you use the compiz app for displaying additional eye-candy ?

---

### Post by loza on 2008-02-01
Thanks! Sorry about the code thing! :)

I have the Visual Effects set to Normal - do you think I should switch them off and see how that goes?

Kind regards

loza

---

### Post by jan quark on 2008-02-01
it's definitely worth a try

---

### Post by loza on 2008-02-01
Thanks for you help (Sooooo quick!) :)

I shall give that a try and see what happens!

kind regards and thank you very much

loza

---

### Post by loza on 2008-02-01
Things seem to be running much more quickly and a directory I was trying to access is now reachable!

Thank you very much jan quark!

kind regards

loza

---

### Post by jan quark on 2008-02-01
if this problem does not occur again pls mark this thread as solved to help other users with a similar problem to find the answer quicker

you can do this using the thread tools at the top of the page
thank you

---

