---
title: "DVD's dont work in Ubuntu.. I have a DVD drive tho :\"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-02-26
I get the message 'There is probably no media in the drive".


I have a MATSHITA - DVD-RAM UJ-805S built in my laptop.. 

Why can't I read dvd's with it? 


Thanks,
Tom

---

### Post by timbounceback on 2008-02-26
run:
```
sudo lshw
```
and post the output

---

### Post by Tom--d on 2008-02-26
This is the out come 
```
laptop                    
    description: Computer
    product: EQUIUM A200
    vendor: TOSHIBA
    version: 
    serial: ************
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=oem-specific uuid=A9231FA0-953C-11DC-A70E-00A0D18D11F2
  *-core
       description: Motherboard
       product: SANTA ROSA CRB
       vendor: Intel Corporation
       physical id: 0
       version: Not Applicable
       serial: Not Applicable
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 1.60 (10/05/2007)
          size: 104KB
          capacity: 960KB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: U2E1
          size: 1467MHz
          capacity: 4096MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
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
             size: 1MB
             capacity: 4MB
             capabilities: burst internal write-back
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
          physical id: 9
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: SODIMM001
             vendor: Mfg 1
             physical id: 1
             serial: 1234-B1
             slot: M2
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Contoller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
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
             product: 82801H (ICH8 Family) PCI Express Port 1
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
             product: 82801H (ICH8 Family) PCI Express Port 2
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
             product: 82801H (ICH8 Family) PCI Express Port 3
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
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-850S
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.40
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: SCSI Disk
                product: TOSHIBA MK1237GS
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: DL13
                serial: X7VPTHTQT
                size: 111GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 107GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 4690MB
                   capacity: 4690MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4690MB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:16:44:7f:24:22
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.45+Realtek Semiconductor Corp. ip=****** link=yes multicast=yes wireless=IEEE 802.11g

```

---

### Post by timbounceback on 2008-02-26
Hmmm.... strange; it seems to be recognized. Oh, and although it probably doesn't have anything to do with your problem, you do have the codecs installed if it is a movie you are watching?

---

### Post by Tom--d on 2008-02-26
I have codecs but dont know which ones they are :S

Why, would they affect the DVD playback?

---

### Post by crjackson on 2008-02-26
> **Tom--d said:**
> I get the message 'There is probably no media in the drive".

I have a MATSHITA - DVD-RAM UJ-805S built in my laptop..
Why can't I read dvd's with it? 
Thanks,
Tom

Is this a data DVD or a Movie DVD?  Is it recordable media, if so which type?  If recordable media, was the session closed? Does the drive support the type of media you are trying to use?

---

### Post by t0p on 2008-02-26
The only thing that occurs to me is, you're trying to watch a movie dvd and you don't have the necessary codecs installed.  As Ubuntu sets great store on being Free, most codecs required for movie-watching are not included by default.

The easiest way I know of to get the required codecs is to install **vlc**.  You can do this via Synaptic - **System > Administration > Synaptic Package Manager**.  **vlc** is a movie player app, and when you install it, the codecs to watch a great many video types are also installed.

---

### Post by Tom--d on 2008-02-26
Yeah, im going to install vlc soon. 

Its any DVD. A data one or a film. It doesn't pick it up :\

Just comes up with that message.

---

### Post by darkworld on 2008-02-26
can you rht click, open the dvd icon and see the contents?

what does cat /etc/fstab give you?

---

### Post by Tom--d on 2008-02-26
tom@Laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5edcb49a-3b71-4ad0-a3fa-97254a283bc1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e31e78fc-2a08-42df-a820-8c3732aad753 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Tom--d on 2008-02-26
Ah.. just tryed out my only fools and horses DVD. That works :D but how do I get it to play in vlc player?

---

### Post by t0p on 2008-02-26
> **Tom--d said:**
> Ah.. just tryed out my only fools and horses DVD. That works :D but how do I get it to play in vlc player?

Open vlc.  Select **File > Open Disc**.  Then select **DVD** (as opposed to **DVD (menus)**).

Hope that helps!!

---

### Post by darkworld on 2008-02-26
pass. Never used VLC

But hey, ive been searching for the sticky that gave a lot of info on setting up DVD and media etc. Its vanished. I thought it used to head the beginners forum? Good if you can find it?

---

### Post by Tom--d on 2008-02-26
> **t0p said:**
> Open vlc.  Select **File > Open Disc**.  Then select **DVD** (as opposed to **DVD (menus)**).

Hope that helps!!

It doesn't work :\
MY dvd drive goes, vlc closes and then nothing.

How do you make it play in vlc automaticly? or a choice to play it. eg like windows auto play window.

---

### Post by Tom--d on 2008-02-27
No one??

---

### Post by darkworld on 2008-02-27
I still cant find the sticky I was trying to point you too, however i did find this [http://ubuntuforums.org/showthread.php?t=661833]("http://ubuntuforums.org/showthread.php?t=661833")
maybe some help in there.

---

### Post by Craigupdegrove on 2008-05-01
My Fstab gives me this. I can't get blank dvd's to mount, in order to be written to my fstab says this

craig@craig-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6bd95391-201c-49a9-ba85-448af94b00cc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a3c46381-02a0-4855-b1f8-3b71e8ea3df7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
craig@craig-laptop:~$ 


What is wrong?

---

