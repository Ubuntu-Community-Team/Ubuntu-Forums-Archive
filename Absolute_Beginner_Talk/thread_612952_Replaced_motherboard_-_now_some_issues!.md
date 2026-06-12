---
title: "Replaced motherboard - now some issues!"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Griffiss on 2007-11-14
Hi

I just installed a new motherboard and now getting some dodgy behaviour.

i) there is no sound, 

ii) networking originally didn't work but seems to have changed its mind after a couple of reboots, 

iii) a couple of times starting up, after the Ubuntu loading screen, I just got a blank screen - no cursor and no response from keyboard (pressed ctrl+alt+backspace)

iv) once starting up i got a message saying the graphics card was not properly recognised and the resolution on the login screen is lower.

How can I sort these out? Do I need to dpkg-reconfigure something? Load drivers again?

Here is my lshw (don't know what is or isn't useful so I've included the lot, apologies for the length of it):

```
description: Computer
    product: P4i65G
    version: 1.00
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P4i65G
       physical id: 0
       version: 1.00
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.30 (09/08/2006)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@0
          version: 15.2.7
          slot: mPGA478
          size: 2394MHz
          capacity: 2394MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1-Cache
             size: 8KB
             capacity: 8KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2-cache
             size: 512KB
             capacity: 512KB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 6
             slot: L3-cache
             capabilities: internal
     *-memory
          description: System memory
          physical id: 1
          size: 511MB
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: b2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32 module=emu10k1_gp
           *-network:0
                description: Wireless interface
                product: Marvell W8300 802.11 Adapter
                vendor: Marvell Technology Group Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: wlan0
                version: 07
                serial: 00:11:d8:4a:2d:92
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+mrv8k51 driverversion=1.45+ASUS,12/24/2003,2.2.0.20 ip=192.168.0.2 latency=32 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11b
           *-communication UNCLAIMED
                description: Communication controller
                product: HCF 56k Data/Fax Modem
                vendor: Conexant
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 89
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
           *-network:1 DISABLED
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth1
                version: 10
                serial: 00:19:66:31:a4:21
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
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
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
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
           *-disk:0
                description: SCSI Disk
                product: WDC WD400BB-00DE
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCAD16427818
                size: 37GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 37GB
                   capabilities: primary bootable
           *-disk:1
                description: SCSI Disk
                product: WDC WD3200JB-00K
                vendor: ATA
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 08.0
                serial: WD-WCAMR3584217
                size: 298GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   capacity: 88GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   size: 1474MB
                   capacity: 1474MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 1474MB
                      capabilities: nofs
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.1.0,3
                   logical name: /dev/sdb3
                   capacity: 208GB
                   capabilities: primary
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SH-S202J
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom2
                logical name: /dev/dvd2
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SB00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
```

---

### Post by NT4usB on 2007-11-14
First off, edit your post and wrap the specs in code quotes so it'll shrink up a bit. Type:
`[`code`]` (without the ticks `` of course) before the first line. Do the same at the end but put /code in the brackets. `[`/code`]`

Your sig says you use 7.10 so we'll assume that's what's on this box.
Since I'm not in front of mine atm, I can only suggest some general stuff. 

You should be able to find your sound card under preferences? Or double click the speaker and select the card. Also unmute the master and pcm (and ?)

look at /var/logs/Xorg.log should point out the things that are breaking in X and giving the black screen.

sudo dpkg-reconfigure -phigh xserver-xorg might fix the video. I edit xorg.conf direct so I dunno...

More later...

---

### Post by Duck2006 on 2007-11-14
It may be worth just doing a reinstall.

---

### Post by Griffiss on 2007-11-15
Thanks for the replies. Turns out that the sound and wireless problems were caused by highly embarrasing senior moments (but I'm only 24!!). I had plugged my speakers into the motherboard's audio output rather than my soundcard => fixed; and I hadn't screwed the antenna back onto my wireless card => fixed. I think it's probably fair to say I'm not the most practically minded person.

So the only thing that remains is the strange resolution at login. 

Not getting the blackscreen any more either - I did change the driver to nvidia so maybe that sorted that out?

---

### Post by kpkeerthi on 2007-11-15
sudo dpkg-reconfigure xserver-xorg

---

### Post by Griffiss on 2007-11-15
I did the sudo dpkg-reconfigure xserver-xorg and that seems to have fixed it, apart from the display being shifted 16 pixels to the right, but this was easily taken care of by my monitor. Thanks!

---

