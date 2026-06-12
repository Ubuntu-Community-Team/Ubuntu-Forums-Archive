---
title: "dvd burning"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-06-29
i can't burn dvd-r i bought a new dvd-r and i can't burn it 
i am not sure does my burner support it not sure the difference between dvd +r or dvd -r
plz help
how can i burn the new dvd i bought dvd -r

---

### Post by Digitallysick on 2007-06-29
When you go to where your dives are listed what does it say? mine says CD-RW/DVD+_RW (has a + and _) it burns both, most of the newer ones burn both. What are you trying to burn, and what program are you useing?

---

### Post by Zzl1xndd on 2007-06-29
> **Digitallysick said:**
> When you go to where your dives are listed what does it say? mine says CD-RW/DVD+_RW (has a + and _) it burns both, most of the newer ones burn both. What are you trying to burn, and what program are you useing?

Also it is often written on the front of the drive.

---

### Post by zerobinary on 2007-06-30
mine on the front only write dvdr/rw not sure how do i check it
```
Executing 'genisoimage -gui -V GnomeBaker data disk -A GnomeBaker -p zerobinary -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-zerobinary/gnomebaker-2TBIUT | builtin_dd of=/dev/hdb obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
/dev/hdb: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=0h failed with SK=2h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type
```
try to burn it with nero and gnomebaker still no goal
for nero
```
i got this 
session fixation error
sony dvd rw dw-d22a\h0 t1
could not perform end of disc at once
burn process failed at 4x (5540kb/s)
disc recording process finished 
```

---

### Post by 67GTA on 2007-06-30
Need more info. What is the manufacturer/model of the burner? There are many formats, and  some burners do not support every format. You need to make sure what formats your burner supports first. If it supports DVD-R, then we can rule that out. I personally hate Gnomebaker. I have never been able to burn much with it. I would suggest trying K3B.

---

### Post by zerobinary on 2007-06-30
but i know nothing about my model
how to i check it
k3b error 
```
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
SONY CD-RW  CRX300E KYS2 (/dev/hda, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

SONY DVD RW DW-D22A BYS2 (/dev/hdb, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]
Burned media
-----------------------
DVD-R Sequential

K3bIsoImager
-----------------------
mkisofs print size result: 831942 (1703817216 bytes)
Pipe throughput: 4274176 bytes read, 4269824 bytes written.

Used versions
-----------------------
mkisofs: 1.1.2
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdb obs=32k seek=0'
:-[ PERFORM OPC failed with SK=2h/ASC=30h/ACQ=05h]: Wrong medium type
/dev/hdb: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=0h failed with SK=2h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hdb=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:831942 -speed=4 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
831942
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.06% done, estimate finish Fri Jun 29 21:47:07 2007
  0.12% done, estimate finish Fri Jun 29 21:47:07 2007
  0.18% done, estimate finish Fri Jun 29 21:47:07 2007
  0.24% done, estimate finish Fri Jun 29 21:47:07 2007

mkisofs calculate size command:
-----------------------
/usr/bin/X11/genisoimage -gui -graft-points -print-size -quiet -volid witch hunter robin -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-zerobinary/k3bnncNob.tmp -rational-rock -hide-list /tmp/kde-zerobinary/k3b4xCCTa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-zerobinary/k3bZghnoc.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-zerobinary/k3bBwuALb.tmp 

mkisofs command:
-----------------------
/usr/bin/X11/genisoimage -gui -graft-points -volid witch hunter robin -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-zerobinary/k3bNadsmb.tmp -rational-rock -hide-list /tmp/kde-zerobinary/k3b69wina.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-zerobinary/k3bTQl6pc.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-zerobinary/k3bcjvSbb.tmp 
```

---

### Post by 67GTA on 2007-06-30
If you don't have a box or paperwork with it you will have to pull it out and look at it. We need to be sure of what formats it supports before we start trying to diagnose anything. Is this a laptop or desktop?

---

### Post by 67GTA on 2007-06-30
You can try to run "sudo lshw" in a terminal and look for "cdrom". It may have the model number listed if it is not generic.

---

### Post by thelinuxguy on 2007-06-30
What is the model of your dvd writer?

*Edit - Never mind...I was looking at an older version of the thread.

---

### Post by thelinuxguy on 2007-06-30
Not a very encouraging one but look at response no 3 on this page: [http://www.computing.net/mac/wwwboard/forum/11302.html](http://www.computing.net/mac/wwwboard/forum/11302.html)

It suggests a firmware update. I can only say that if you do it, [COLOR="Red"]keep it as the last option and be careful[/COLOR]. I would suggest you move ahead with 67GTA's suggestions first.

Edit: And this: [http://forums.afterdawn.com/thread_view.cfm/1/312424](http://forums.afterdawn.com/thread_view.cfm/1/312424)

---

### Post by zerobinary on 2007-06-30
well i find this 
```
zerobinary@zerobinary:~$ sudo lshw
Password:
zerobinary                
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=58EF1ADC-8A69-DA11-9982-B6F5CD8658BA
  *-core
       description: Motherboard
       product: P4S800D-X
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1006.002 (06/15/2006)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: PGA 478
          size: 2400MHz
          capacity: 2400MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pni monitor ds_cpl cid xtpr
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
     *-memory
          description: System Memory
          physical id: 32
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MB
             width: 64 bits
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
     *-pci
          description: Host bridge
          product: 655 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: f8000000
          bus info: pci@00:00.0
          version: 50
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
          resources: iomemory:f8000000-fbffffff
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display:0
                description: VGA compatible controller
                product: RV350 AR [Radeon 9600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:e0000000-efffffff ioport:d000-d0ff iomemory:ff5f0000-ff5fffff irq:16
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AR [Radeon 9600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 00
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:d0000000-dfffffff iomemory:ff5e0000-ff5effff
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=SIS_IDE latency=128
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:ffa0-ffaf irq:16
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom:0
                   description: DVD reader
                   product: SONY CD-RW CRX300E
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: KYS2
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hda
              *-cdrom:1
                   description: DVD writer
                   product: SONY DVD RW DW-D22A
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: BYS2
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                 *-disc
                      physical id: 0
                      logical name: /dev/hdb
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52
             resources: ioport:e800-e8ff ioport:ec00-ec7f irq:23
        *-usb:0
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:ff6fe000-ff6fefff irq:19
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:ff6fd000-ff6fdfff irq:18
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:ff6fc000-ff6fcfff irq:17
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: Mouse
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.00
                   capabilities: usb-1.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: iomemory:ff6ff000-ff6fffff irq:20
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: USB Storage
                   physical id: 2
                   bus info: usb@4:2
                   logical name: scsi2
                   version: 96.01
                   serial: 000000009601
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=480.0MB/s
                 *-disk:0
                      description: SCSI Disk
                      product: STORAGE DEVICE
                      vendor: Generic
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sdb
                      version: 9601
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdb
                 *-disk:1
                      description: SCSI Disk
                      product: STORAGE DEVICE
                      vendor: Generic
                      physical id: 0.0.1
                      bus info: scsi@2:0.0.1
                      logical name: /dev/sdc
                      version: 9601
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdc
                 *-disk:2
                      description: SCSI Disk
                      product: STORAGE DEVICE
                      vendor: Generic
                      physical id: 0.0.2
                      bus info: scsi@2:0.0.2
                      logical name: /dev/sdd
                      version: 9601
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sdd
                 *-disk:3
                      description: SCSI Disk
                      product: STORAGE DEVICE
                      vendor: Generic
                      physical id: 0.0.3
                      bus info: scsi@2:0.0.3
                      logical name: /dev/sde
                      version: 9601
                      capabilities: removable
                    *-disc
                         physical id: 0
                         logical name: /dev/sde
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@00:04.0
             logical name: eth0
             version: 91
             serial: 00:15:f2:6e:05:2a
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.0.100 latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
             resources: ioport:e400-e4ff iomemory:ff6fb000-ff6fbfff irq:21
        *-storage
             description: RAID bus controller
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@00:05.0
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master emulated scsi-host
             configuration: driver=sata_sis latency=128
             resources: ioport:eff0-eff7 ioport:efe4-efe7 ioport:efa8-efaf ioport:efe0-efe3 ioport:ef90-ef9f irq:22
           *-disk
                description: SCSI Disk
                product: WDC WD740GD-00FL
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 33.0
                serial: WD-WMAKE2433092
                size: 69GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 243MB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 69GB
                   capacity: 69GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1474MB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux LVM Physical Volume partition
                      physical id: 6
                      logical name: /dev/sda6
                      serial: jZaQI2-NnNI-9SLp-v3lK-oLxv-vFhg-Ho6LvZ
                      size: 67GB
                      capacity: 67GB
                      capabilities: multi lvm2
        *-generic UNCLAIMED
             product: SB Audigy LS
             vendor: Creative Labs
             physical id: a
             bus info: pci@00:0a.0
             version: ff
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=255 maxlatency=247 mingnt=255
             resources: irq:255

```
they only say about dvd r never even mention dvd +r or -r

---

### Post by 67GTA on 2007-06-30
Is the DVD you are trying to burn dual layer?

---

### Post by 67GTA on 2007-06-30
Your model supports everything under the sun. Just for kicks try running "sudo k3b" in a terminal and see if it will let you burn it as root. Try another disc, that one maybe corrupted or have something already written on it. Other than that I'm not sure.

---

### Post by zerobinary on 2007-06-30
no but the disc is i am trying to burn is not 8 gb so this dvd -r should not be dual layer
my dvd burner don't burn dual layer dvd
k3b error
```
The Joliet extensions (which are needed for long filenames on Windows systems) restrict the length of the volume descriptior (the name of the filesystem) to 16 characters. The selected descriptor 'witch hunter robin' is longer than that. Do you want it to be cut or do you want to go back and change it manually?
```
still no goal
i try 3 of the disc i have purchase today
```
K3bDevice::Device) /dev/hdb: READ TRACK INFORMATION with real length 36 failed.
(K3bDevice::Device) /dev/hdbREAD TRACK INFORMATION for DVD-ROM failed.
DiskInfo:
Mediatype:       CD-ROM
Current Profile: No media
Disk state:      unknown
Empty:           0
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        00:00:01 (LBA 1) (2048 Bytes)
Remaining size:  00:00:00 (LBA 0) (0 Bytes)
Used Size:       00:00:01 (LBA 1) (2048 Bytes)
```
firmware update
```
http://dhc014.rpc1.org/indexOEM.htm#DW-D22A
```
```
Original RPC-2 Firmware version BYS3 for the SONY DVD RW DW-D22A



Flash in Windows using "LtnFW"



If the drive is not detected after a misflash, then flash in DOS with mtkflash (1.69 or higher)

Use this command: "mtkflash # w /b BYS3.bin"

Where # is replaced by one of the following numbers:

1 - Primary Master

2 - Primary Slave

3 - Secondary Master

4 - Secondary Slave



If using mtkflash 1.80.1, then do not include the "/b" flag. Use this command: "mtkflash # w BYS3.bin"
```
how do i flash it since we are not using window
is this download the right one 
```
-SONY DVD RW DW-D22A (OEM SOHW-1633S) 2.4X(+R DL) 16X(+R) 4X(+RW) & 8X(-R) 4X(-RW) & 48/24/48/16
bys3
```
or this
```
http://www.cdr.cz/?dvd_rekordery/sony/dru710a.html
bys6
for that i try to use wine to install it but i say unable to flash firmware
for crossover linux it even say no match drive detected
```
but the problem is i am not using window and how do i install that firmware
furthermore i am not sure am i getting the right firmware what is my model for it again

---

### Post by zerobinary on 2007-06-30
basically the problem right now is i find the firmware but i don't know how to flash it

---

### Post by cogadh on 2007-06-30
I've been unable to find a non-Windows version of Sony's firmware update utilities. You really shouldn't have to update your firmware at all, that drive should already support any DVD burning you are trying to do.

What exactly are you trying to do? It is possible, and far more likely, that you are having an application problem and not a firmware problem.

---

### Post by zerobinary on 2007-06-30
the issue is this with my old firmware bys2 i can't burn dvd -r 
but i can burn dvd r but the problem comes when i bought 75 dvd -r dvd and i can't burn it without the firmware
because i need to burn some data like 1.37 gb bigger than my usb so i can't very reinstall ubuntu and install window xp
and i have use 39% of my hdd my hdd is super small since i am using wd raptor 74 gb one whic h acutally has 69 gb

---

### Post by cogadh on 2007-07-01
According to Sony, that drive can already burn DVD-R, but only at a 8X maximum speed. That info may be based on the latest firmware, however. Since you cannot update the firmware via Windows on the machine you currently have the drive in, is it possible that you could move it to another machine with Windows and run the firmware flasher there?

---

### Post by zerobinary on 2007-07-01
no maybe i can if i can resize my hdd maybe then i have enough space to install window xp
maybe i should try using qparted in knoppix live cd great now i delted the boot section for my ubuntu what should i do

---

### Post by Computer-Geek on 2007-07-01
When it's said DVD-RW it means that it writes both DVD +R and -R.

Thanks!!

---

### Post by zerobinary on 2007-07-01
but i can't burn both 
that's y i ened firmware update

---

### Post by cotcot on 2007-07-01
When I read the error message of k3b it suggests to try another media type. k3b recognises your burner as a SONY... including the possibility to burner DVD-r.

So maybe (the make of) the dvd disk you use is wrong. You are not trying to write with a high speed on a low speed disk ? The disk shows 1X-4X or 1X-2X or ...

---

### Post by zerobinary on 2007-07-01
my disc is 1-16x i bought 75 of those

---

### Post by cogadh on 2007-07-01
Try buring at no higher than 8x, as I said, Sony claims that drive can burn that format, but at a max speed of 8x.

---

### Post by zerobinary on 2007-07-01
well i selected auto for burning speed i try even 1x still no goal

---

### Post by zerobinary on 2007-07-01
now i have installed window but how do i flash it

---

