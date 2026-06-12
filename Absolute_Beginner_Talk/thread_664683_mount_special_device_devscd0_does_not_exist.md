---
title: "mount: special device /dev/scd0 does not exist"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by gofeddy on 2008-01-11
Hello,
         I have Ubuntu 7.10 installed in my PC system.I have a dual-boot system with XP installed as well.  I preveiously had a Samsung DVD Writer that was working just fine on my system. Then, it broke down and I brought a new Lite-On DVD Writer. Then I fixed it up and booted the system. But, when I insert any CD or DVD and try to access them, I get the following error:
**mount: special device /dev/scd0 does not exist**
Now, what could have happened suddenly to my device file? Any help....:(

---

### Post by schaumkeks on 2008-01-11
> **gofeddy said:**
> Hello,
         I have Ubuntu 7.10 installed in my PC system.I have a dual-boot system with XP installed as well.  I preveiously had a Samsung DVD Writer that was working just fine on my system. Then, it broke down and I brought a new Lite-On DVD Writer. Then I fixed it up and booted the system. But, when I insert any CD or DVD and try to access them, I get the following error:
**mount: special device /dev/scd0 does not exist**
Now, what could have happened suddenly to my device file? Any help....:(

Let's see what disk devices are known in your system via
```
sudo lshw -C disk
```

Bye, Sven

---

### Post by gofeddy on 2008-01-11
Ok. Here's the output of the command you requested......

  *-disk                  
       description: SCSI Disk
       product: ST3160812AS
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 5LS1HD61
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5

---

### Post by logos34 on 2008-01-11
linux isn't detecting it.  Reboot and go into the Bios to see if it's detected there.  If not, check your cables/connections, jumper, etc.

---

### Post by gofeddy on 2008-01-11
I did restart the sytem and checked to see if the Writer is being detected. It does indicate that the writer is detected. 
It says PATA Master   3M-MOSER CAER!DI-30A4Q
Also the CDROM is set to the highest priority. 
By the way, I also checked the connections and it seems proper.

---

### Post by logos34 on 2008-01-11
try 

**cdrecord --scanbus**

---

### Post by gofeddy on 2008-01-11
Well, here's the output:

Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
Linux sg driver version: 3.5.34
Using libscg version 'schily-0.9'.
scsibus3:
        3,0,0   300) 'ATA     ' 'ST3160812AS     ' '3.AA' Disk
        3,1,0   301) *
        3,2,0   302) *
        3,3,0   303) *
        3,4,0   304) *
        3,5,0   305) *
        3,6,0   306) *
        3,7,0   307) *
By the way, cdrecord had to be insalled by apt-get......before using it

---

### Post by logos34 on 2008-01-11
hmm...not showing up.  just the seagate sata.

Can you boot from and run a live cd (try ubuntu)?

---

### Post by gofeddy on 2008-01-12
Yeah, I can run a Live CD through it. But, later I decided to switch to Windows and check to see if it was working. And, it was just working perfectly. Then, I booted Ubuntu and to my surprise, the CDROM was accessible. There was also an icon on the Desktop. Then, again I restarted. Followed the same sequence...XP..and then Ubuntu, and this time there were 2 icons for the CD Drive on the Desktop. But, then when I restarted with Ubuntu without going into XP, the same error occured again:
**mount: special device /dev/scd0 does not exist**

Now, this is wierd.....

---

### Post by logos34 on 2008-01-12
sometimes I get the double cd icon too...logging out and back in again usually cures it.  

yeah, kinda odd situation...

Try commenting out (#) the existing line for the optical drive in /etc/fstab, which was put there for the samsung.  Try /dev/**hdc** or /dev/**hda** instead. (if you can get it to work again in linux, run  lshw -C disk, it will show which channel)

---

### Post by gofeddy on 2008-01-12
Do you mean to say, i should be commenting out /dev/scd0 and then add an new line with /dev/hdc below it...i am a little confused here.....This is my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=11b34458-cc74-4bba-800f-e12df94d82d4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=84C42A36C42A2ABE /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=6683b8ae-684f-43d2-8ef3-c2b6b9064d66 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Ok..so what do I change here? Sorry, I am still a n00b here....

---

### Post by logos34 on 2008-01-12
or just replace 'scd0' with 'hdc' in the same line (you can always change it back)

(remember to open as root. i.e. gksudo gedit /etc/fstab)

on second thought, not sure it's going to work because the existing symlinks in /dev for cd and dvd probably point to --> scd0

But did you get it to work again so as to check lshw?  Is it still being recognized as /dev/scd0?

Here's mine:
> 
 *-cdrom
       description: DVD writer
       product: ASUS DRW-1608P2
       physical id: 0
       bus info: ide@1.0
**       logical name: /dev/hdc**
       version: 1.41
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma4 status=ready
     *-disc
          physical id: 0
          logical name: /dev/hdc

It depends on the ata storage controller...sometimes ubuntu uses the libata driver scsi designation 'scd0', other times  it uses the standard IDE designation, hd_  (in my case I have it plugged into hdc, secondary master, which is the standard place on a board with 2 ide channels).

---

### Post by gofeddy on 2008-01-12
Here's my output for lshw....but cdrom description is not to be seen....

description: Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal uuid=EEF26DC4-6BE0-11DA-AF3C-000C6EF1EC46
  *-core
       description: Motherboard
       product: D915GLVG
       vendor: Intel Corporation
       physical id: 0
       version: AAC96367-306
       serial: FCVG55100920
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: VG91510A.86A.0048.2005.0722.1031 (07/22/2005)
          size: 64KB
          capacity: 448KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.3
          serial: 0000-0F43-0000-0000-0000-0000
          slot: J2E1
          size: 3GHz
          capacity: 3060MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl est cid cx16 xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 16KB
             capacity: 16KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 2MB
             capacity: 2MB
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 3c
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: SerNum1
             slot: J6G1
             size: 1GB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns) [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: SerNum2
             slot: J6G2
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR Synchronous 333 MHz (3.0 ns) [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 2
             serial: SerNum3
             slot: J6H1
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM DDR Synchronous 333 MHz (3.0 ns) [empty]
             product: PartNum4
             vendor: Manufacturer4
             physical id: 3
             serial: SerNum4
             slot: J6H2
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
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
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
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
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:05:08.0
                logical name: eth0
                version: 01
                serial: 00:16:76:00:08:fe
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.1.1 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: ST3160812AS
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 5LS1HD61
                size: 149GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 100GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 46GB
                   capabilities: primary
              *-volume:2
                   description: Linux swap / Solaris partition
                   physical id: 3
                   bus info: scsi@3:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 1906MB
                   capabilities: primary nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

I guess this info might be useful....its very detailed.....

---

### Post by gofeddy on 2008-01-12
Well, finally it seems like things have sorted out well. After changing /dev/scd0 to /dev/hdc it seems like the BIOS has finally detected the correct cdrom drive. 
Previously it was detecting the drive as MOSES CAER and now it is detecting it correctly as MOSER BAER..
So far I have restarted the sytem 3 times and all times the cdrom was accessible....so hopefully I get  no more problems....
Anyway thank you logos34 for your help....if there is a problem with this again....I will get back here.

---

### Post by logos34 on 2008-01-12
glad you got it working--but to be honest I'm even more puzzled now that you post the entire lshw.  I see you have an intel 915glv board (I have another machine with a similar board--915gav)...intel boards have only one ide channel/connector, so I would think you would need to use 'hda'.

Oh well, it functions, that's the important thing.  if it ain't broke...

---

