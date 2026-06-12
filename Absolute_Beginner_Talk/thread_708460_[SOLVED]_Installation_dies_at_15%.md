---
title: "[SOLVED] Installation dies at 15%"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2008-02-26
I finally decided to upgrade from 6.06 LTS to 7.10. (Actually an update made the decision for me by killing my wireless and a couple  of other things, but that's it's own story/nightmare?)

Anyways, I waited the four to six weeks for my 7.10 disks to arrive from Canonical, and once they arrived, I went to install it.

I had problems with gparted due to a bug that locks the thing in a loop because of it looking for a nonexistent floppy drive. Got past that and re-partitioned my 20 gig HD as follows: 6 gig for /, 500MB for swap, and 11(+) gigs for /home. Then, when I clicked the install, it went through OK until it started to actually install. It got to 15% and hung for about two hours. I started over again, and after researching, found someones post about increasing swap to about 900MB solving an identical problem. 

I went through it again and made the swap 902 MB. However, it has evidently hung at 15% again. It's been an hour and the cd drive is working, but nothing is happening with the install box other than it going two shades of grey. 

I'm going to leave it alone for a while and split and stack some firewood while it does it's thing. If anybody has any ideas (other than another type of disk, I don't have a burner that functions.) I would appreciate it. Otherwise I'll have to go back to windows, 'cause I need this thing, and cannot wait until another batch of CD's  arrives...

---

### Post by SOULRiDER on 2008-02-26
Did you checkt he CD for defects? I remember when I was installing it would lock at 86% and it was because of issues witht he disc.

Also, posting your system specs wouldnt hurt at all, so please do.

---

### Post by xeth_delta on 2008-02-26
There could be one of several reasons for you issue. Problems with the discs or some compatibility issue the installer has with your system configuration. I would recommend you to download the alternate CD from the Ubuntu website (not the regular desktop one) and try installing from that one. Look at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), check the alternet desktop cd box below the "Start Download" green button.

---

### Post by Papa-san on 2008-02-26
It's still hung...
Locked up tight. Had to hold the power button down to shut it off.
I checked it for defects and it came up good. I also did the memory test and everything passed.
I'm using an older Dell latitude c-610. 

I'll post this now and once the 20 minute live session boot-up finishes, I'll post lshw. 

xeth... I cannot burn a CD. I have to order them from Canonical. I'll get it in a month or so..

---

### Post by xeth_delta on 2008-02-26
> **Papa-san said:**
> It's still hung...
Locked up tight. Had to hold the power button down to shut it off.
I checked it for defects and it came up good. I also did the memory test and everything passed.
I'm using an older Dell latitude c-610. 

I'll post this now and once the 20 minute live session boot-up finishes, I'll post lshw. 

xeth... I cannot burn a CD. I have to order them from Canonical. I'll get it in a month or so..

I see. I wonder if it is possible to install from the safe graphics mode.

---

### Post by Papa-san on 2008-02-26
I've tried it both ways, but I don't see any difference between the two methods. They both have a resolution higher than I am supposed to go. I used the F4 key and tried to put in a 600x800 16 and it didn't make any change either. still came up in the high resolution.

Anyways, here is lshw: (sorry it's so long, but I didn't want to delete anything you might need to see...```
ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Portable Computer
    product: Latitude C610
    vendor: Dell Computer Corporation
    serial: CVMFG11
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-5600-104D-8046-C3C04F473131
  *-core
       description: Motherboard
       product: Latitude C610
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A16 (05/16/2003)
          size: 64KB
          capacity: 448KB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect pcmciaboot int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) III Mobile CPU      1000MHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.11.1
          slot: Microprocessor
          size: 997MHz
          capacity: 1333MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KB
             capacity: 32KB
             capabilities: internal varies unified
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KB
             capacity: 512KB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 256MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM_A
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: DIMM_B
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82830 830 Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Radeon Mobility M6 LY
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga bus_master vga_palette cap_list
                configuration: latency=32 mingnt=8
        *-usb
             description: USB Controller
             product: 82801CA/CAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network:0
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 78
                serial: 00:06:5b:e1:ba:40
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.48 latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1420 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1420 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-network:1 DISABLED
                description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth1
                version: 02
                serial: 00:90:4b:2c:52:6b
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=32 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: HITACHI_DK23DA-2
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 00J2
                serial: 11F4BS
                size: 18GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 6000MB
                   capabilities: primary
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 902MB
                   capabilities: primary nofs
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 11GB
                   capabilities: primary
           *-cdrom
                description: SCSI CD-ROM
                product: CD-ROM SN-124
                vendor: SAMSUNG
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: q008
                capabilities: removable audio
                configuration: ansiversion=5 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             configuration: latency=0
  *-battery
       product: CGR-B/838
       vendor: Panasonic
       physical id: 1
       slot: Left Module Bay
       capacity: 59200mWh
       configuration: voltage=14.8V
ubuntu@ubuntu:~$  
```

---

### Post by xeth_delta on 2008-02-26
Here is a suggestion that seems to havwe worked for some people. Boot from the CD, and when you are at the first Ubuntu menu press F6 for more options. I don't have a CD with me right now, so I cannot be very precise. There must be the option to add boot arguments for the kernel.
Add the option "noapic" without the quotes. Let us know if it works.

---

### Post by TeaSwigger on 2008-02-26
If it doesn't have enough RAM, it can't install. If I'm reading that right it looks like you only have 256mb (less in fact, since it has shared video memory), and I'm sorry to say that's not always enough for Gutsy's live CD. Some video cards can also be problematic. Even after install it may hang on boots, requiring you to lower the color depth during boot or drop usplash. You may need the alternate install CD, or do a server install and build up if you're adept enough at that sort of thing.

---

### Post by Papa-san on 2008-02-26
Well, thanks for trying! It didn't work... Hung at 15% again. I have a friend burning me a copy of the alternate CD, so I'm hoping that works...

The thing that frosts my technicalities is the fact that I just bought three new laptops... One for my wife and one for each of my daughters... They should be arriving next week... And none of them wants Ubuntu on theirs :(

I'll post how the alternate CD works.

---

### Post by xeth_delta on 2008-02-26
> **Papa-san said:**
> Well, thanks for trying! It didn't work... Hung at 15% again. I have a friend burning me a copy of the alternate CD, so I'm hoping that works...

The thing that frosts my technicalities is the fact that I just bought three new laptops... One for my wife and one for each of my daughters... They should be arriving next week... And none of them wants Ubuntu on theirs :(

I'll post how the alternate CD works.

It will most likely work. Just let us know how it goes.

---

### Post by Papa-san on 2008-02-27
Both copies he gave me have errors...

I'll just get 6.06 back on it and see if I can do the wireless without ndiswrapper. I'm guessing that is what killed it on both of the last kernel updates... The first time I managed to work around it, the last time, it was impossible. Maybe if I get the new kernel before I set up wireless... Hmmm.

Anywhoo...  Thanks for trying!

I'm guessing the memory thing is the issue with 7.10, so until I get more, I'll stick with familiar problems!

---

### Post by hyper_ch on 2008-02-27
you know, if it worked at some stage, you could revert back to that kernel.

---

### Post by SOULRiDER on 2008-02-27
Cant you ahve a friend download the disc for you?

---

### Post by Papa-san on 2008-02-27
> **hyper_ch said:**
> you know, if it worked at some stage, you could revert back to that kernel.

When the wireless quit due to the update, I applied a 'fix' 
( [http://ubuntuforums.org/showthread.php?t=706034](http://ubuntuforums.org/showthread.php?t=706034) )that messed up all the previous kernels... 

Anyway, I've re-formatted and installed 6.06 again. I have the update installed that killed me, so I am going to get the wireless working now, and it might work out cleanly...


EDIT: I ended up using an alternate install disk and installed it that way... Solved the issue, as it WAS a lack of memory.

---

