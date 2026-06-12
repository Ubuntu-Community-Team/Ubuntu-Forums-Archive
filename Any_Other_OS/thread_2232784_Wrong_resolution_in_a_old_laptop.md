---
title: "Wrong resolution in a old laptop"
date: 2014-07-04
forum: Any Other OS
---

### Post by leillo1975 on 2014-07-04
Hello

I'm trying to install any ubuntu based distribution in a old Laptop, but I have problems with resolution.

When I launch LiveCD to install, the resolution are correct (1024*768), but when I finish installation, I reboot the computer and the resolution change to a ridiculous 640*480, located in the upper left of the screen.

The very, very old laptop is a Airis 755II0 and when I do a "lshw", the graphics card is an Intel 82845G/GL with driver i915

I attached a photo

Sorry, my english is bad. Thanks a lot

---

### Post by sudodus on 2014-07-04
Which version of Ubuntu are you trying, based on 12.04 LTS or newer?

If a newer version, maybe UXA acceleration will help. See this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics)

It makes it easier to give relevant help, if you specify your computer

- [Airis 755II0 (but I have problems finding the detailed specs)]
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Finally, you can find valuable tips at this link
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by kc1di on 2014-07-04
we need to know what your video card is in order to be of help. 
can you go to a terminal and type the following command and post the output here.

```
lspci -v
```

---

### Post by Bucky Ball on 2014-07-04
*Thread moved to **Multimedia & Video**.*

Now you have a photo attached. ;)

I have attached that one for you. Please use 'Adv Reply' or 'Go Advanced' and use the paperclip icon to attach large pictures. Thanks.

What flavour are you using, and as requested by sudodus, which release? Can't tell by the picture. Get to 'Settings' or its equivalent and look for 'Monitor Settings' or 'Display' or 'Screen'. Set the resolution there if it gives you the correct one. Experiment.

PS: Your English is fine.

---

### Post by leillo1975 on 2014-07-08
I tryed a lot of "solutions" that I searched in this forums, but none worked. I tryed to add a parameter in the GRUB ( i915.modeset=0 / 1 ), but it didn't fix the problem. 

I tryed other non based Ubuntu distributions, like PCLinuxOS or Manjaro, but I have the same situation

Finally I installed Debian Testing and IT WORKS!!!, but the wifi adapter was no detected. Then I try Linux Mint Debian Edition, and it worked well, with correct resolution and wifi.

If you want I can make "lspci -v", but the results are in LMDE, not in Ubuntu based

---

### Post by Bucky Ball on 2014-07-08
Hmm, you mention nothing about any of the advice you were given to try in Ubuntu or the results.

> If you want I can make "lspci -v", but the results are in LMDE, not in Ubuntu based 

Neither OS is supported in the main support areas of these forums (although feel free to post about other OSs in the 'Other OS' sections of the forum for support or discussion). ;)

I advise you mark this thread as solved to help others using Thread Tools at the top right of the page. Good luck.

---

### Post by leillo1975 on 2014-07-09
At this point the problem is not solved in Ubuntu so I think that I should not mark this thread as SOLVED, but if you want I wiil do it

---

### Post by Bucky Ball on 2014-07-09
*Thread moved to **Other OS/Distro Support**.*

> **leillo1975 said:**
> At this point the problem is not solved in Ubuntu so I think that I should not mark this thread as SOLVED, but if you want I wiil do it

You haven't mentioned anything about using Ubuntu, only Ubuntu derivatives and Debian. 

[QUOTE=Bucky Ball]Neither OS is supported in the main support areas of these forums (although feel free to post about other OSs in the 'Other OS' sections of the forum for support or discussion).[/QUOTE]

As you are not using any Ubuntu release/flavour supported here and the problem is not solved so you are still after support, I have moved the thread to the appropriate section of the forums. Good luck.

---

### Post by leillo1975 on 2014-07-09
I wrote this in the first post of this thread

> **leillo1975 said:**
> Hello

I'm trying to install any ubuntu based distribution in a old Laptop, but I have problems with resolution.



I tryed Lubuntu and Xubuntu. I think that this are supported flavours. Linux Lite and ElementaryOS are the last of the Ubuntu based distributions that I tested with the same problem. I think that this is a Ubuntu related problem, but I'm not administrator, I did not command.

---

### Post by sudodus on 2014-07-09
Do you still want help to get an Ubuntu flavour work in your computer? In that case maybe UXA acceleration will help. See this link

[https://wiki.ubuntu.com/Lubuntu/Adva...Intel_graphics]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics")

It makes it easier to give relevant help, if you specify your computer

- [Airis 755II0 (but I have problems finding the detailed specs)]
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by leillo1975 on 2014-07-10
> **sudodus said:**
> Which version of Ubuntu are you trying, based on 12.04 LTS or newer?

If a newer version, maybe UXA acceleration will help. See this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics)

It makes it easier to give relevant help, if you specify your computer

- [Airis 755II0 (but I have problems finding the detailed specs)]
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Finally, you can find valuable tips at this link
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]


I installed **Xubuntu 14.04** and I maked the changes in xorg, but the screen now is in black.

This is a description of the Computer:

[http://www.airissupport.com/bdc/Ficheros%20Asociados/PORTATILES/N618%20-%20N619%20-%20N620/Ficha%20T%C3%A9cnica%20(N618-N619-N620).pdf](http://www.airissupport.com/bdc/Ficheros%20Asociados/PORTATILES/N618%20-%20N619%20-%20N620/Ficha%20T%C3%A9cnica%20(N618-N619-N620).pdf)

I make an "lspci -v" in **Xubuntu 14.04** and this are the results:

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
	Subsystem: Uniwill Computer Corp Device 9000
	Flags: bus master, fast devsel, latency 0
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Uniwill Computer Corp Device 9000
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915

00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Uniwill Computer Corp Device 9011
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at df20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Uniwill Computer Corp Device 9011
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at df40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Uniwill Computer Corp Device 9011
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at df80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Uniwill Computer Corp Device 9110
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at dff7bc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=05, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: dfd00000-dfdfffff
	Prefetchable memory behind bridge: 40000000-43ffffff

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel driver in use: lpc_ich

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Uniwill Computer Corp Device 9011
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4
	I/O ports at 0170 [size=8]
	I/O ports at 0374
	I/O ports at ffa0 [size=16]
	Memory at 44000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
	Subsystem: Uniwill Computer Corp Device 9011
	Flags: medium devsel
	I/O ports at 0540 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: Uniwill Computer Corp Device 9011
	Flags: medium devsel, IRQ 17
	I/O ports at e000 [size=256]
	I/O ports at e100 [size=64]
	Memory at 44000400 (32-bit, non-prefetchable) [size=512]
	Memory at 44000600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
	Subsystem: Uniwill Computer Corp Device 4007
	Flags: medium devsel, IRQ 17
	I/O ports at e200 [size=256]
	I/O ports at e300 [size=128]
	Capabilities: <access denied>

01:03.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
	Subsystem: Uniwill Computer Corp Device 3000
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 17
	Memory at 48000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 40000000-43ffffff (prefetchable)
	Memory window 1: 4c000000-4fffffff
	I/O window 0: 0000c000-0000c0ff
	I/O window 1: 0000c400-0000c4ff
	16-bit legacy interface ports at 0001
	Capabilities: <access denied>
	Kernel driver in use: yenta_cardbus

01:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

01:0c.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at 0000
	Memory at <ignored> (32-bit, non-prefetchable)
	Expansion ROM at <ignored>
	Capabilities: <access denied>
```

---

### Post by sudodus on 2014-07-10
Please tell also about 

- CPU
- RAM (size)
(- graphics chip/card:  Intel Corporation 82845G)
- wifi chip/card - if you have wifi

For example, you can run the following commands and attach the file** lshw.txt** or cut and paste its content and put it within code tagss.

```
sudo -s
lshw -sanitize > lshw.txt
exit
```

Or extract the relevant information and post it.

---

### Post by leillo1975 on 2014-07-10
> **sudodus said:**
> Please tell also about 

- CPU
- RAM (size)
(- graphics chip/card:  Intel Corporation 82845G)
- wifi chip/card - if you have wifi

For example, you can run the following commands and attach the file** lshw.txt** or cut and paste its content and put it within code tagss.

```
sudo -s
lshw -sanitize > lshw.txt
exit
```

Or extract the relevant information and post it.


This is the result of the commands:

```
computer
    description: Notebook
    product: jjA
    vendor: INFINITY
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
    configuration: boot=normal chassis=notebook cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1.05
          date: 09/05/2003
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: CPU 1
          size: 2666MHz
          capacity: 2666MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 8KiB
             capacity: 8KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:c0000000-cfffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0000000-d7ffffff memory:dff80000-dfffffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:df20(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:df40(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:df80(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:dff7bc00-dff7bfff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:dfd00000-dfdfffff memory:40000000-43ffffff
           *-pcmcia
                description: CardBus bridge
                product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 3
                bus info: pci@0000:01:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: irq:17 memory:48000000-48000fff ioport:c000(size=256) ioport:c400(size=256) memory:40000000-43ffffff memory:4c000000-4fffffff
           *-firewire UNCLAIMED
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: a
                bus info: pci@0000:01:0a.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci cap_list
                configuration: latency=64 maxlatency=32
                resources: memory:dfdff800-dfdfffff ioport:cc00(size=128)
           *-network UNCLAIMED
                description: Ethernet controller
                product: DP83815 (MacPhyter) Ethernet Controller
                vendor: National Semiconductor Corporation
                physical id: c
                bus info: pci@0000:01:0c.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=255 mingnt=255
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:44000000-440003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:540(size=32)
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:e000(size=256) ioport:e100(size=64) memory:44000400-440005ff memory:44000600-440006ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:e200(size=256) ioport:e300(size=128)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: FUJITSU MHS2040A
             vendor: Fujitsu
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 8004
             serial: [REMOVED]
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000250a8
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 14GiB
                capacity: 14GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-07-10 10:08:06 filesystem=ext4 lastmountpoint=/ modified=2014-07-10 17:11:26 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-07-10 17:11:26 state=mounted
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: [REMOVED]
                size: 2050MiB
                capacity: 2050MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /home
                version: 1.0
                serial: [REMOVED]
                size: 20GiB
                capacity: 20GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-07-10 10:08:19 filesystem=ext4 lastmountpoint=/home modified=2014-07-10 17:14:33 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2014-07-10 17:14:33 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: CD-RW  CRX830E
             vendor: SONY
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: JYK1
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@4:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
     *-scsi:3
          physical id: 5
          bus info: usb@1:4
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdc
             size: 3821MiB (4007MB)
             capabilities: partitioned partitioned:dos
             configuration: sectorsize=512 signature=00008c47
           *-volume
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/leo/4GB
                version: FAT32
                serial: [REMOVED]
                size: 3821MiB
                capacity: 3821MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=4GB mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
```

---

### Post by sudodus on 2014-07-10
Extracted from lshw.txt

Intel(R) Pentium(R) 4 CPU 2.66GHz
RAM - 1 GB
VGA compatible controller: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
ATA disk - 40 GB
USB pendrive - 4 GB

This is an old computer, and I think Lubuntu 14.04 LTS is the best alternative for it.

I'll be back with more details ...

---

### Post by sudodus on 2014-07-10
I think UXA acceleration will help (in Lubuntu 14.04 LTS). See this link

[https://wiki.ubuntu.com/Lubuntu/Adva...Intel_graphics]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics")

Edit (or create) **/etc/X11/xorg.conf** as follows: (there should be a ***tab*** before each line except the first and the last). 

```
Section "Device"
        Identifier "Intel Graphics"
        Driver "intel"
        Option "AccelMethod" "uxa"
EndSection
```

Restart X (reboot, restart your display manager, whatever). Colors are back to the way they used to be and flash works.

Alternatives to Lubuntu are

-Xubuntu 12.04 LTS (supported until April 2015, not very long from now) or
-Xubuntu 14.04 LTS (supported until April 2017)

---

### Post by leillo1975 on 2014-07-11
> **sudodus said:**
> I think UXA acceleration will help (in Lubuntu 14.04 LTS). See this link

[https://wiki.ubuntu.com/Lubuntu/Adva...Intel_graphics]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics")

Edit (or create) **/etc/X11/xorg.conf** as follows: (there should be a ***tab*** before each line except the first and the last). 

```
Section "Device"
        Identifier "Intel Graphics"
        Driver "intel"
        Option "AccelMethod" "uxa"
EndSection
```

Restart X (reboot, restart your display manager, whatever). Colors are back to the way they used to be and flash works.

Alternatives to Lubuntu are

-Xubuntu 12.04 LTS (supported until April 2015, not very long from now) or
-Xubuntu 14.04 LTS (supported until April 2017)


I've already tried that, and all I've got is a black screen

---

### Post by sudodus on 2014-07-11
If no luck with a 14.04 LTS flavour, I suggest that you try something else.

Have you tried ***Xubuntu 12.04 LTS*** ?

You can also try some community re-spin of Ubuntu 12.04 LTS (promising support until April 2017).

[I][B]Bento, Bodhi, LXLE

[/B][/I]or ***Knoppix*** which is known to be good at recognizing hardware,

or some ultra-light distro for example ***Wary Puppy, Tiny Core*** or ***DSL***.

---

### Post by leillo1975 on 2014-07-11
I tryed Xubuntu 12.04 with the same results. Linux Mint Debian Edition works well.

---

### Post by sudodus on 2014-07-11
If you are happy with Linux Mint Debian Edition, I'm happy too. Use whichever linux distro or version that runs well. If not quite happy, continue testing some of the other alternatives.

Linux Mint Debian is a rolling release, with advantages and disadvantages. See this link

[http://www.linuxmint.com/download_lmde.php](http://www.linuxmint.com/download_lmde.php)

> **How does LMDE compare to the Ubuntu-based editions?**

              Pros:
     
[LIST]
[*]             You don&#8217;t need to ever re-install the system. New versions of software and updates are continuously brought to you. 
[*]             It&#8217;s faster and more responsive than Ubuntu-based editions. 
[/LIST]
              Cons:
     
[LIST]
[*]             LMDE requires a deeper knowledge and experience with Linux, dpkg and APT. 
[*]             Debian is a less user-friendly/desktop-ready base than Ubuntu. Expect some rough edges. 
[/LIST]


---

### Post by leillo1975 on 2014-07-11
I prefer a Ubuntu flavour or based distro, because is more freindly and easy to use and manage, but this PC is only to use for projecting simple presentations.

If someone comes up with something, do not hesitate to post it

---

### Post by sudodus on 2014-07-11
You can try one of the community re-spins of Ubuntu 12.04 LTS (promising support until April 2017).

***Bento, Bodhi, LXLE***

---

### Post by Bucky Ball on 2014-07-11
If the machine is only going to be used for simple presentations, I would personally do a minimal install, add the lightweight desktop environment of your choice (xfce4 or lxde or one of the others sudodus mentions) and the apps you need to do the presentation. With a lightweight DE that should fly.

---

