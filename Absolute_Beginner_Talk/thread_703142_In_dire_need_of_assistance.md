---
title: "In dire need of assistance"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Hiddengecko on 2008-02-21
Well, dire is an exaggeration. But noobs get to exaggerate, right?

Anyway, having heard how awesome/efficient/powerful Ubuntu Linux is, I decided that since I am taking a Linux class I should install it. After a lot of errors and struggles with partitioning correctly, the infamous GRUB 17, and drivers, I made it. I am officially making this post from Linux at last.

Still, I am having a few problems.

- I cant (sic) use apostrophes or quote marks currently. Its (sic) annoying for a grammar nerd such as myself, it damages my credibility and makes me look like an idiot. 

-I need to know how to access my other NTFS hard drives, I have heard some rather cryptic advice on this via google, but the solution eludes me.

-I need to know how to run windows applications, particularly games. I have heard of WINE, though I have not used it yet, and I have also heard of a WINE-like program designed with games in mind. Enlighten me, please. :)

-The GUI is a bit annoying. In the Linux class I am in, the lab computers use Fedora 6--its interface is very like windows in the shortcuts and stuff, but Ubuntu seems to lack things like Ctrl + C and such. Also on this note, I have seen a lot of hype on Ubuntus (sic) ability to use a Vista-esque 3d desktop, turning the tabbed desktop thing into a cube, as well as having some nice themes and additions like animated background images. Sounds nice. Making your computer look cool is pretty important if you&#341;e (<-see what it did with the apostrophe there?) a gamenerd like me.

Any help would be appreciated, but please--do try to avoid the terminal if you can. Since I was born in 1990, my first OS was Windows 3.1. I have used GUIs my entire life, and texting just isnt (sic) my thing. I consider myself fairly decent with Windows and PCs in general (I have built this machine from the ground up) but seeing as today is the first time I have used any distribution of Linux without someone guiding me through everything step-by-step, I am more than a little confused.

---

### Post by jan quark on 2008-02-21
> I cant (sic) use apostrophes or quote marks currently. Its (sic) annoying for a grammar nerd such as myself, it damages my credibility and makes me look like an idiot.

go to system > preferences > keyboard
perhaps changing the layout will help


> I need to know how to access my other NTFS hard drives, I have heard some rather cryptic advice on this via google, but the solution eludes me.

time for the terminal
c'mon you are using linux now. you cannot deny the existence of the terminal completely and some tasks have to be done with it. not the daily yada tasks, but mounting a ntfs partition for sure. cryptic is everything in the beginning, but becomes clear with experience.

> Any help would be appreciated, but please--do try to avoid the terminal if you can. Since I was born in 1990, my first OS was Windows 3.1. I have used GUIs my entire life, and texting just isnt (sic) my thing.

please run these terminal commands and post the output:

```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```


> need to know how to run windows applications, particularly games. I have heard of WINE, though I have not used it yet, and I have also heard of a WINE-like program designed with games in mind

it's a good start
[http://www.winehq.org/](http://www.winehq.org/)

> I have seen a lot of hype on Ubuntus (sic) ability to use a Vista-esque 3d desktop, turning the tabbed desktop thing into a cube, as well as having some nice themes and additions like animated background images.

you mean compiz-fusion and emerald ...

compiz is preinstalled with gutsy. when your graphic card is set up correctly the effects should work for you

please post also the results of these terminal commands

```
lspci
```
```

sudo lshw 
```

---

### Post by some_random_noob on 2008-02-21
**Emulation:**

Install "wine" via synaptic. It is a free application which can *sometimes* run Windows games/programs. [***Wine site here (Clicky) ***]("http://www.winehq.org/"). There is also Cedegar, which is a paid-for application which is more advanced (If you're really desperate to play Windows-exclusive games). 

**Visual effects**
I don't know much about this myself. But there is a customization forum on this site, and if you google "beryl" or "compiz fusion" or "how to do the cube thing in ubuntu" I'm sure you'll find heaps of stuff.

By the way, ctrl + c DOES work. As for the grammar problems... that's just weird. You type in an apostrophe and it shows up wrong? I'm probably the wrong person to ask sorry :(

---

### Post by tangibleorange on 2008-02-21
> **Hiddengecko said:**
> 
Also on this note, I have seen a lot of hype on Ubuntus (sic) ability to use a Vista-esque 3d desktop, turning the tabbed desktop thing into a cube, as well as having some nice themes and additions like animated background images. Sounds nice. Making your computer look cool is pretty important if you&#341;e (<-see what it did with the apostrophe there?) a gamenerd like me.

Assuming desktop effects (Compiz Fusion) work for you (You can check by right-clicking anywhere on the desktop, selecting "Edit Desktop Background". and going to the "Effects" tab. You can then configure them to your liking with the CCSM tool:

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Hiddengecko on 2008-02-21
Thanks for the advice and the promt reply! I do understand the importance of the Terminal, but I view it more like I would the Windows regedit. Painful, but important. Also, allow me to apologize for the spammy nature of the following post.
```

> 
Mount:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/hdd on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=todd)
todd@ubuntu:~$ 

> sudo fdisk -l
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd388d388

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4865     1646662+   5  Extended
/dev/hda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d3982d4

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x008a0089

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9728    78140128+   7  HPFS/NTFS

> cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a1916dc1-c7e2-4b12-96cb-979704024f18 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=761a0129-4771-4d5c-87cc-7bc8414d7393 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

> lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8T890 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.1 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.3 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:09.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
todd@ubuntu:~$ 

> sudo lshw
ubuntu                    
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-00E0-00004CF118AD
  *-core
       description: Motherboard
       product: K8T890-8237
       physical id: 0
       slot: Internal Cache
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (03/14/2006)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
          slot: Socket 939
          size: 2GHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm cmp_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back
     *-cpu:1
          description: CPU
          vendor: AMD
          physical id: 5
          bus info: cpu@1
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
          slot: Socket 939
          size: 2GHz
          capacity: 3GHz
          clock: 200MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             width: 64 bits
        *-bank:2
             description: DIMM
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: K8T890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64 latency=8 module=amd64_agp
        *-system UNCLAIMED
             description: PIC
             product: K8T890 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: [K8T890 North / VT8237 South] PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: K8T890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8600 GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-pci:2
             description: PCI bridge
             product: K8T890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: K8T890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: K8T890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:5
             description: PCI bridge
             product: K8T890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-network:0
             description: Wireless interface
             product: AR2413 802.11bg NIC
             vendor: Atheros Communications, Inc.
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: wifi0
             version: 01
             serial: 00:13:46:e3:44:79
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) ip=192.168.0.100 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=32 module=sata_via
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=VIA_IDE latency=32 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: WDC WD400BB-53AUA1
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 18.20D18
                   serial: WMA6R1178872
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 35GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 1608MB
                      capacity: 1608MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 1608MB
                         capabilities: nofs
              *-disk:1
                   description: ATA Disk
                   product: ST3200826A
                   vendor: Seagate
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 3.03
                   serial: 3ND2T8WK
                   size: 186GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 186GB
                      capabilities: primary bootable
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD800BB-55JKC0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 05.01C05
                   serial: WD-WCAMD7201419
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: smart=on
                 *-volume
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@1.0,1
                      logical name: /dev/hdc1
                      capacity: 74GB
                      capabilities: primary bootable
              *-cdrom
                   description: DVD-RAM writer
                   product: Optiarc DVD RW AD-7170A
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 1.02
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma4 status=ready
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:e0:4c:f1:18:ad
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=9 mingnt=8 module=via_rhine multicast=yes port=MII speed=10MB/s
     *-pci:1
          description: Host bridge
          product: K8T890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8T890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8T890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8T890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8T890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 107
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 108
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 109
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
```

---

### Post by loboc on 2008-02-21
> **Hiddengecko said:**
> Well, dire is an exaggeration. But noobs get to exaggerate, right?

Anyway, having heard how awesome/efficient/powerful Ubuntu Linux is, I decided that since I am taking a Linux class I should install it. After a lot of errors and struggles with partitioning correctly, the infamous GRUB 17, and drivers, I made it. I am officially making this post from Linux at last.

Still, I am having a few problems.

- I cant (sic) use apostrophes or quote marks currently. Its (sic) annoying for a grammar nerd such as myself, it damages my credibility and makes me look like an idiot. 

>>> That advice above was good I dont know what keyboard options you selected during the install to mess that up 

-I need to know how to access my other NTFS hard drives, I have heard some rather cryptic advice on this via google, but the solution eludes me.

>>>run synaptic the package manager and search for ntfs-3g 

-I need to know how to run windows applications, particularly games. I have heard of WINE, though I have not used it yet, and I have also heard of a WINE-like program designed with games in mind. Enlighten me, please. :)

>>>run synaptic the package manager and search for wine 

>>>Mine works out of the box for most things 


-The GUI is a bit annoying. In the Linux class I am in, the lab computers use Fedora 6--its interface is very like windows in the shortcuts and stuff, but Ubuntu seems to lack things like Ctrl + C and such. Also on this note, I have seen a lot of hype on Ubuntus (sic) ability to use a Vista-esque 3d desktop, turning the tabbed desktop thing into a cube, as well as having some nice themes and additions like animated background images. Sounds nice. Making your computer look cool is pretty important if you&#341;e (<-see what it did with the apostrophe there?) a gamenerd like me.

>>>ctrl c its probally the same thing as your apostrrophe issues, 

>>>(BTW most times highlighting copies middle click pastes) also see this 

>>>[http://ubuntuforums.org/showthread.php?t=701877](http://ubuntuforums.org/showthread.php?t=701877)

>>>run synaptic the package manager and search for compiz-gnome for 3d effects

Any help would be appreciated, but please--do try to avoid the terminal if you can. Since I was born in 1990, my first OS was Windows 3.1. I have used GUIs my entire life, and texting just isnt (sic) my thing. I consider myself fairly decent with Windows and PCs in general (I have built this machine from the ground up) but seeing as today is the first time I have used any distribution of Linux without someone guiding me through everything step-by-step, I am more than a little confused.

Google is your Friend. Learn the CLI (google CLI to start)

---

### Post by some_random_noob on 2008-02-21
Wow... that terminal output really spammed this page. Click reply, and look above the box where you type your response. Click on the "hash" icon and then put your text within the "code" tags ;)

---

### Post by amingv on 2008-02-21
> **Hiddengecko said:**
> -The GUI is a bit annoying. In the Linux class I am in, the lab computers use Fedora 6--its interface is very like windows in the shortcuts and stuff[...]

<shameless_promotion_for_KDE>
In your class, they probably use KDE. It's another desktop environment for Linux, the Ubuntu project has a KDE edition, called Kubuntu. If the idea pleases you (and after you settle down and feel at ease on Ubuntu) you can try it. I'm sure you'll find it at the very least a good learning experience.
</shameless_promotion_for_KDE>

---

### Post by Hiddengecko on 2008-02-21
Yes, I know all about google searching. :p
But the assistance I get there tends to be a lot less conclusive, with one person or persons claiming the fix worked and a bunch more saying that it did not.

Also, flash refuses to install. I have that x86 64 bug or whatever it is, Ima go google that now.

And no, in my class they use Gnome. I've heard (Hey, it worked, though it took some fudging) that KDE is better than Gnome, though.

---

### Post by jan quark on 2008-02-21
you can use the code brackets     #     to make larger output more readable

to mount your windows partitions run this in terminal, which is far more than the regedit in windows:

creating a mount point
```

sudo mkdir /media/windows1
```

```
sudo mkdir /media/windows2
```


mounting the partitions into the mount points
```

sudo mount /dev/hdb1 /media/windows1 -t ntfs -o nls=utf8,umask=000
```

```
sudo mount /dev/hdc1 /media/windows2 -t ntfs -o nls=utf8,umask=000
```



please run also this command and post the output
```

ls /dev/disk/by-uuid/ -alh
```

---

### Post by Hiddengecko on 2008-02-21
> **some_random_noob said:**
> Wow... that terminal output really spammed this page. Click reply, and look above the box where you type your response. Click on the "hash" icon and then put your text within the "code" tags ;)

Ah, yes, thank you!

```
total 0
drwxr-xr-x 2 root root 120 2008-02-20 16:00 .
drwxr-xr-x 6 root root 120 2008-02-20 16:00 ..
lrwxrwxrwx 1 root root  10 2008-02-20 16:00 5C9C2A5C9C2A30C6 -> ../../hdc1
lrwxrwxrwx 1 root root  10 2008-02-20 16:00 761a0129-4771-4d5c-87cc-7bc8414d7393 -> ../../hda5
lrwxrwxrwx 1 root root  10 2008-02-20 16:00 883CD00C3CCFF2EC -> ../../hdb1
lrwxrwxrwx 1 root root  10 2008-02-20 16:00 a1916dc1-c7e2-4b12-96cb-979704024f18 -> ../../hda1
todd@ubuntu:~$ 

```

I still get the unable to mount error when I attempt to open any of the NTFS drives.

---

### Post by hyper_ch on 2008-02-21
On the next thread use a descriptive thread title and not a generic "help needed".

We know that you need help, otherwise you wouldn't post here.

---

### Post by Hiddengecko on 2008-02-21
> **hyper_ch said:**
> On the next thread use a descriptive thread title and not a generic "help needed".

We know that you need help, otherwise you wouldn't post here.

But it IS generic help on several issues, and this area is labeled as absolute newbie talk. Otherwise I would agree with you. At any rate, I will try to avoid such generic titles in the future.

---

### Post by jan quark on 2008-02-21
hm perhaps you need some drivers
install this and try the mounting commands one more time

```
sudo apt-get install ntfs-3g ntfsprogs
```

---

### Post by hyper_ch on 2008-02-21
> **Hiddengecko said:**
> But it IS generic help on several issues, and this area is labeled as absolute newbie talk. Otherwise I would agree with you. At any rate, I will try to avoid such generic titles in the future.

Well, using just a "need help" or "noob" here is considered (at least by me) as very lazy and unrespectful to those that intent to help and such things should not be encouraged. You may have a problem with your ATi card. I don't have one so I cannot help at all... so I won't click a thread that's about ATi... instead I can use my time to try and help others and hence not wasting it for generic things that would make it clear with a descriptive title that i have no clue about that issue.

If you have several issues, make several threads.

---

### Post by roscal on 2008-02-21
"And no, in my class they use Gnome. I've heard (Hey, it worked, though it took some fudging) that KDE is better than Gnome, though."

heeheheheheh , I like Kde.
:guitar:

---

