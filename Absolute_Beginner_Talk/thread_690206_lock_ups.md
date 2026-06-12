---
title: "lock ups"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by nikef on 2008-02-07
Hi all
my gusty g 7.10 keeps locking up

the only thing i can use is awn.it has my amsn,firefox and stuff on,i can use all of them

but i can not do anything else ,please can some1 help me,i can not use this pc like this,it locks up within minutes of putting the pc on :confused:

---

### Post by nikef on 2008-02-07
when i try to open appearance prefences the box is just empty and i can not close it :confused:

---

### Post by jan quark on 2008-02-07
what are your specs? graphic card, ram, cpu,...

did you have installed some applications in the past days?

are you running compiz? did shutting the effects off stop the lock ups?

---

### Post by fiddledd on 2008-02-07
Not really enough info (and you'd probably lose me if there was :) ). I can only suggest things like:

Have you installed anything, Updates etc, just before you had the lockups,
Have you tried uninstalling AWN
Do you have these problems right after login, or after running certain programs?

Erm.. there's more, but you can see what I'm getting at.

EDIT:
yet again my slow typing = late posting :)

---

### Post by nikef on 2008-02-07
> **jan quark said:**
> what are your specs? graphic card, ram, cpu,...

did you have installed some applications in the past days?

are you running compiz? did shutting the effects off stop the lock ups?

i am not sure of full spec of pc

i have tried to uninstall  compiz on the pc,but i think it still on,not sure how to turn it off  :confused:

as for applications i did install something but i have removed them ,cant remember if it started after an update though

also noticed that the start up tone,plays twice 

thanks for helping me

---

### Post by nikef on 2008-02-07
> **fiddledd said:**
> Not really enough info (and you'd probably lose me if there was :) ). I can only suggest things like:

Have you installed anything, Updates etc, just before you had the lockups,
Have you tried uninstalling AWN
Do you have these problems right after login, or after running certain programs?

Erm.. there's more, but you can see what I'm getting at.

EDIT:
yet again my slow typing = late posting :)


Hi and thanks

i did install some items,but i uninstalled again 
no i have not uninstall awn ,i will try 2 

after i have started up,it locks up after i have use the applications,places system a few times,and then i have to do a hard re-boot 

thanks for helping me

---

### Post by nikef on 2008-02-07
just clicked on applications to open up terminal and it has locked up again :confused:

---

### Post by jan quark on 2008-02-07
try to run this in terminal and post the output

```
lspci
```

```
sudo lshw
```

---

### Post by nikef on 2008-02-07
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
02:01.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
02:07.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
trish@trish-desktop:~$                   


description: Mini Tower Computer
    product: SCENIC P300
    vendor: FUJITSU SIEMENS
    version: SCEP
    serial: YBEM096223
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=normal chassis=mini-tower uuid=7E35D595-50DC-11D7-A847-F78890F01E80
  *-core
       description: Motherboard
       product: D1451
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: S26361-D1451
       serial: 11291810
       slot: Primary IDE
     *-firmware
          description: BIOS
          vendor: FUJITSU SIEMENS // Phoenix Technologies Ltd.
          physical id: 0
          version: 4.06  Rev. 1.02.1451 (02/17/2003)
          size: 103KB
          capacity: 320KB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.1.3
          slot: CPU
          size: 1800MHz
          capacity: 2800MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 8KB
             capacity: 20KB
             capabilities: burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 128KB
             capacity: 512KB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 768MB
          capacity: 2GB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM-1
             size: 256MB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM-2
             size: 512MB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
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
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: NC100 Network Everywhere Fast Ethernet 10/100
                vendor: ADMtek
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 11
                serial: 00:30:05:41:18:77
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.65 latency=64 maxlatency=128 mingnt=64 module=tulip multicast=yes
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k HSFi Modem
                vendor: Conexant
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: Maxtor 6E040L0
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: NAR6
                serial: E16KGFPE
                size: 38GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 24GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 13GB
                   capabilities: primary
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 635MB
                   capacity: 635MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 635MB
                      capabilities: nofs
           *-cdrom:0
                description: SCSI CD-ROM
                product: CD-ROM LTN486S
                vendor: LITEON
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: YIS2
                capabilities: removable audio
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: DVD writer
                product: DVD_RW ND-3540A
                vendor: _NEC
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.01
                serial: [_NEC    DVD_RW ND-3540A 1.0105031600
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
     *-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: DCP-115C
             vendor: Brother
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
             configuration: ansiversion=2
           *-disc
                physical id: 0
                logical name: /dev/sdb
trish@trish-desktop:~$          

                                            

here is what you asked for

thanks

---

### Post by nikef on 2008-02-07
It has locked up again,i cant do anything  :confused: will have to do a hard re boot  :confused:

how can i uninstall AWN through the konsole as i have this open now and it works

---

### Post by jan quark on 2008-02-07
to remove awn via console try

list all packages with

```
dpkg -l
```

then remove the package you want with

```
sudo dpkg -r packagename
```

---

### Post by nikef on 2008-02-07
Hi ,i got an error 

trish@trish-desktop:~$ sudo dpkg -r awn
[sudo] password for trish:
dpkg - warning: ignoring request to remove awn which isn't installed.
trish@trish-desktop:~$   



i tried to remove awn but it says its not installed 

 looking in systematic,just before the lock up

and it shows its not installed in there either :confused:

---

### Post by nikef on 2008-02-08
Ok 

i managed to work in failsafe gnome

i removed compiz 

and pressed  alt and f2 together and added metacity--replace 

i have also managed to remove AWN 

i am still getting the problems when i go back to normal gnome,is there any1 that may be able to shed some light on this  :confused:

---

