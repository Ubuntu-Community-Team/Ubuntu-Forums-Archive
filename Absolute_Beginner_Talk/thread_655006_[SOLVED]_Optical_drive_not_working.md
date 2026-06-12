---
title: "[SOLVED] Optical drive not working"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2007-12-31
Any idea why my folks' optical drives wouldn't be working? They're running 7.10 on a desktop machine; one drive is a cheap-o DVD-ROM (not a writer), and the other is a cheap-o CD-RW drive. At first, I thought the problem would be a driver of some sort, but that doesn't really make sense to me.

The DVD drive will read things (I think), but - if memory serves - only sporadically. The CD-RW won't work at all. There's power to it, but discs don't spin up, and Ubuntu doesn't recognize the drive or anything in it.

Help! :)

---

### Post by p_quarles on 2007-12-31
Well, if you're near their computer, or can relay instructions to them, the following information would be helpful:
```
cat /etc/fstab
```
and 
```
sudo lshw
```

---

### Post by doctorbighands on 2007-12-31
Awesome! I'll be near their computer in just a little while. More info to come, I guess...

---

### Post by doctorbighands on 2008-01-17
Okay, here's the info. I still need help with this one!!

"cat /etc/fstab" produces:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b3bda1b4-c722-4e2d-9b08-8ea27b69586e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=ce310aaa-cb97-4090-a2cb-c5b3d08f8786 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```


"sudo lshw" produces: (it's a LOT!)
```
mills-desktop             
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: nVidia-nForce2
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F3 (08/02/2004)
          size: 128KB
          capacity: 192KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm)
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 1GHz
          capacity: 3200MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 512MB
          capacity: 1536MB
        *-bank:0
             description: DIMM 65535 MHz (0.0 ns) [empty]
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             clock: 1110MHz (0.9ns)
        *-bank:1
             description: DIMM 65535 MHz (0.0 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 256MB
             clock: 1110MHz (0.9ns)
        *-bank:2
             description: DIMM 65535 MHz (0.0 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: h
             size: 256MB
             clock: 1110MHz (0.9ns)
     *-pci
          description: Host bridge
          product: nForce2 AGP (different version?)
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia module=nvidia_agp
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nForce2 ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: isa ht bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce2 SMBus (MCP)
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
        *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: nForce2 Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: a1
             serial: 00:0f:ea:3b:1a:01
             capacity: 100MB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
        *-multimedia
             description: Multimedia audio controller
             product: nForce2 AC97 Audio Controler (MCP)
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: USR5660A (USR265660A, USR5660A-BP) 56K PCI Faxmodem
                vendor: U.S. Robotics
                physical id: a
                bus info: pci@0000:01:0a.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
        *-ide
             description: IDE interface
             product: nForce2 IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3 module=amd74xx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk:0
                   description: ATA Disk
                   product: ST3500630A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 3.AAF
                   serial: 9QG3EYYG
                   size: 465GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 464GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 1474MB
                      capacity: 1474MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 1474MB
                         capabilities: nofs
              *-disk:1
                   description: ATA Disk
                   product: WDC WD300AB-00BPA1
                   vendor: Western Digital
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 18.20D18
                   serial: WD-WMA6W1432695
                   size: 27GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 27GB
                      capabilities: primary
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD reader
                   product: Pioneer DVD-ROM ATAPIModel DVD-115 0111
                   vendor: Pioneer
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: E1.11
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio dvd
                   configuration: mode=udma2 status=nodisc
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: GeForce 6200 A-LE
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
     *-scsi:0
          physical id: 1
          bus info: usb@3:3
          logical name: scsi0
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0128
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sda
     *-scsi:1
          physical id: 2
          bus info: usb@3:2
          logical name: scsi1
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: iPod
             vendor: Apple
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 1.62
             serial: 8K729GZ4V9K8
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:11:a3:02:c9:12
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.107 multicast=yes wireless=IEEE 802.11b/g
```

Any help is MUCH appreciated, as usual!

---

### Post by p_quarles on 2008-01-17
Well, according to the output of the second command, the kernel isn't even able to detect the presence of the second drive (the r/w). You say it has power, so obviously the power cable is connected correctly, but what about the IDE cable? Any chance it's just loose, or upside down?

---

### Post by doctorbighands on 2008-01-17
Upon opening the case, I was reminded of the importance of having an IDE cable plugged into the back of the drive (rather than hanging loose) when I want the drive to communicate with my mobo.

I'm ashamed of myself...  :lolflag:

---

### Post by p_quarles on 2008-01-17
> **doctorbighands said:**
> Upon opening the case, I was reminded of the importance of having an IDE cable plugged into the back of the drive (rather than hanging loose) when I want the drive to communicate with my mobo.

I'm ashamed of myself...  :lolflag:
Yep. That is fairly necessary. :D

Glad you got it working.

---

