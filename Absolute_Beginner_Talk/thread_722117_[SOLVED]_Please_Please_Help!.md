---
title: "[SOLVED] Please Please Help!"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by dylondadank on 2008-03-12
[http://www.arsgeek.com/?p=1313](http://www.arsgeek.com/?p=1313)

was following all these instructions so i could get my 3d cube working. 

not a good idea, so now my screen resolution cannot be changed from 800x600 
and i really cant stand it, i need help getting everything back too how it was before i did all of that.

---

### Post by ibizatunes on 2008-03-12
what graphics card do you have?
have u enable restricted drivers? system > admin > restricted drivers
have u enable 3d effect > system > preference > themes > *cant remember the next tab option* > select enable 
and see if it works then?

---

### Post by dylondadank on 2008-03-12
the themes tab isnt there anymore that the emeral theme manager is there. and i dont know what graphics card i have, and yes, the restricted driver is enabled

---

### Post by jan quark on 2008-03-12
post the results of these terminal commands

```
lspci
```

```
sudo lshw
```

you can also try to reconfigure the xserver
```
sudo dpkg-reconfigure -plow xserver-xorg 
startx
```

---

### Post by dylondadank on 2008-03-12
dylan@chaos:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Communication controller: Conexant HSF 56k Data/Fax Modem


dylan@chaos:~$ sudo lshw
[sudo] password for dylan:
chaos                     
    description: Desktop Computer
    product: EX321AA-ABA SR1930NX NA630
    vendor: Compaq Presario 061
    version: 0nx1411RE101ALTAI00
    serial: CNH6220YW4
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=desktop uuid=8011C4EA-E75C-1110-AC1F-E03C26EE6599
  *-core
       description: Motherboard
       product: Altair
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.00
       serial: 123456789000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.02 (05/03/2006)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          slot: Socket 775
          size: 3066MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 16KB
             capacity: 16KB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: b
             slot: L2 Cache
             size: 1MB
             capacity: 1MB
             capabilities: synchronous internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: d
             slot: L3 Cache
             capabilities: synchronous internal varies
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
     *-cpu:1 DISABLED
          description: CPU
          vendor: Null
          physical id: 5
          bus info: cpu@1
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          slot: Socket 775
          size: 18EHz
          capabilities: ht
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-cache:0 DISABLED
          description: L1 cache
          physical id: a
          slot: L1 Cache
          capabilities: synchronous internal data
     *-cache:1 DISABLED
          description: L2 cache
          physical id: c
          slot: L2 Cache
          capabilities: synchronous internal unified
     *-cache:2 DISABLED
          description: L3 cache
          physical id: e
          slot: L3 Cache
          capabilities: synchronous internal varies
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 512MB
          capacity: 1GB
        *-bank:0
             description: DIMM DDR 200 MHz (5.0 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MB
             width: 64 bits
             clock: 200MHz (5.0ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
     *-pci
          description: Host bridge
          product: Radeon Xpress 200 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 64 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm msi vga bus_master cap_list
                configuration: latency=64 mingnt=8
        *-ide:0
             description: IDE interface
             product: 437A Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-ide:1
             description: IDE interface
             product: 4379 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=sata_sil latency=64 module=sata_sil
           *-disk
                description: SCSI Disk
                product: SAMSUNG SP2004C
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: VM10
                serial: S07GJ1LL220844
                size: 186GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 93GB
                   capabilities: primary
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 2572MB
                   capacity: 2572MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1286MB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1286MB
                      capabilities: nofs
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 89GB
                   capabilities: primary bootable
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 81
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:2
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=64 module=atiixp
           *-ide
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD writer
                   product: TSSTcorpCD/DVDW TS-H552L
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 0614
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma2 status=nodisc
        *-multimedia
             description: Audio device
             product: SB450 HDA Audio
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:17:31:b0:8d:3a
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.3 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
     *-scsi
          physical id: 1
          bus info: usb@1:4
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: USB SD Reader
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: USB CF Reader
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
             version: 1.01
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: USB SM Reader
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
             version: 1.02
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: USB MS Reader
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
             version: 1.03
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sde

---

### Post by ibizatunes on 2008-03-12
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 
envy may download newer drivers.....

---

### Post by Arkenzor on 2008-03-12
Ah, so you have an ATI card. These can't be handled like most other models because they use another acceleration method (xgl instead of aiglx). 
(Also, that guide is a bit outdated. Remember that the Linux world evolves quickly, and guides for previous versions of Ubuntu often won't help much with the current one)

You should try following [this guide](https://help.ubuntu.com/community/CompositeManager/CompizFusionATI?highlight=%28ATI%29) from the Ubuntu wiki.


EDIT: Didn't see someone answering before me.
But I don't really get the point of using an automated script like Envy when the manual procedure is simple and you can easily find guides to it. It only means you'll learn less, and end up posting "Envy doesn't work" instead of "I was a that point in that guide when I got this error message" if things don't work. In which case do you think it'll be easier for people to help?

(This said, Envy downloads the newest drivers, which usually aren't immediately included in the standard Ubuntu updates. So if the current driver doesn't work you can try and see if the latest version has your problem fixed.)

---

### Post by prshah on 2008-03-12
> **dylondadank said:**
> [http://www.arsgeek.com/?p=1313](http://www.arsgeek.com/?p=1313)

was following all these instructions so i could get my 3d cube working. 

not a good idea, so now my screen resolution cannot be changed from 800x600 
and i really cant stand it, i need help getting everything back too how it was before i did all of that.

Switch to a virtual terminal with Ctrl+Alt+F1, then login with your (same) username and passowrd.
Then run the below commands:

```

sudo mv /etc/X11/xorg.conf .
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf

```

This make a copy of your current xorg config to your home directory. Then it takes an older, hopefully working xorf conf and replaes the current one.

Then switch back to your X screen with Ctrl+Alt+F7, then press Ctrl+Alt+BkSpace to restart your server.

If it doesnt work, you can restore the config you had earlier by copying back the xorg.conf in your home directory to /etc/X11 with

```

cd && sudo rm /etc/X11/xorg.conf && sudo mv xorg.conf /etc/X11

```

Pls pay special attention to the case (uppercase, lowercase) of the commands,

If you post your results here, we can help further either with Beryl config or with solving your resolution problems.


Cheers,
PRShah

---

