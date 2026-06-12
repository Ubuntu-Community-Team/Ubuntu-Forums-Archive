---
title: "No sound"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by CAD-MAN on 2007-09-27
Hi,

Just installed Ubuntu Gutsy (Yes, I know its not quite finished, but the Feisty CD wouldn't work on my laptop), and it is running perfectly, apart from one thing: It doesn't seem to be able to recognise my laptop's speakers.

I get the following error when I try to use the volume controller on the top panel:

```
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
```


Im completely new to Linux, but have been on the forums for a while, so may know what you're talking about, or I may not. So please be specific and newb-friendly if you choose to try and help me out with this :)

Thanks :)

---

### Post by madoracle on 2007-09-27
Go into terminal and run alsamixer, see if your speakers are unmuted and the volume turned up.

---

### Post by CAD-MAN on 2007-09-27
> **madoracle said:**
> Go into terminal and run alsamixer, see if your speakers are unmuted and the volume turned up.

Sorry, I wouldn't know how to do that :( As I said, im a newb, and the only thing that I know how to do in the terminal is installing programs. Could you please elaborate?

Thanks

---

### Post by madoracle on 2007-09-27
Okay, no worries. Open a terminal and type 'alsamixer'

If it returns an error, post it. Otherwise use the right arrow to go from speaker to speaker and make sure none have MM at the base of them, if they do hit the 'm' key to unmute. And press the up arrow to turn them up.

---

### Post by Haegin on 2007-09-27
Click Applications and go into Accessories then select Terminal. A window with a short textual prompt will appear. This is the terminal and your new best friend. It can be amazingly powerful and is much faster than the GUI when you know what you are doing.

For now you don't need to do much. Just type
```

alsamixer

```
and press enter. Normally stuff people put in the code boxes above is for entry into the terminal or some form of output (like how you were using it). If it is for entry into the terminal then it is assumed you press enter (normally after each line).

The command you just ran launched a text based program which should come up with something like this:
[[img=http://img263.imageshack.us/img263/1395/alsamixerot0.th.png]](http://img263.imageshack.us/my.php?image=alsamixerot0.png)

The pic above shows my Audigy 2 Value card and shows the levels each channel is at. The MM under Tone shows that Tone is currently muted. Check that your sound is loud enough to hear and that important channels are not muted (you can toggle mute by using the arrow keys to select the channel and pressing 'M' on your keyboard).

If you get an error about your computer not finding any cards can you please post the error up here in a code block and (in seperate code blocks) post the output from `lspci -v` (run it in the terminal at the prompt) and `lshw`.

Hope this helps

---

### Post by CAD-MAN on 2007-09-27
Thanks for the replies :)

I typed that exact command in the terminal, and got the following:

```
alsamixer: function snd_ctl_open failed for default: No such device

```

Result of 'lspci -v':
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fa000000-feafffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f20 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 6f00 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01f1
        Flags: fast devsel, IRQ 21
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
        Memory behind bridge: f9f00000-f9ffffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: f9c00000-f9efffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 6f60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 6f40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Memory behind bridge: f9b00000-f9bfffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 6fa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 6eb0 [size=8]
        I/O ports at 6eb8 [size=4]
        I/O ports at 6ec0 [size=8]
        I/O ports at 6ec8 [size=4]
        I/O ports at 6ee0 [size=16]
        I/O ports at eff0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Dell Unknown device 01f1
        Flags: medium devsel, IRQ 10
        Memory at febfbf00 (32-bit, non-prefetchable) [size=256]
        I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at df00 [size=128]
        [virtual] Expansion ROM at fea00000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at f9bfe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at f9bfd800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at f9bfd400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9bfd500 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9bfd600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9bfd700 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1021
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

```


And the result of 'lshw':
```
WARNING: you should run this program as super-user.
joe-laptop                
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2025MB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.10
          serial: 0000-06FA-0000-0000-0000-0000
          size: 2001MHz
          capacity: 2001MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
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
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8600M GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Contoller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
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
             version: 02
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
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 02
                serial: 00:1b:77:a9:93:83
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.0.3 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11g
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
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
             version: 02
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
             version: 02
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
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:1c:23:8d:83:87
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 module=b44 multicast=yes
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:03:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.4
                bus info: pci@0000:03:01.4
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD writer
                product: DVD+-RW GSA-T11N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: A103
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage

```


Thanks for your help and patience :)

---

### Post by CAD-MAN on 2007-09-27
PS. I have one other problem: I want to copy over the bookmarks from Firefox on my old machine (dont really care about the rest of the profile).

I have put the bookmarks.html file onto my USB stick, but don't know where to put it now.

Im sure this will be a breeze for you people :) Thanks (and sorry for the off-topic-ness)

---

### Post by madoracle on 2007-09-27
```
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

I could be wrong but it looks like your controller is there and operational, the problem might be with alsamixer. Try:

sudo apt-get install alsamixer 

Or wait for a better reply than mine :D

For the bookmarks, in Firefox, go into:

Bookmarks - Organize Bookmarks - File - Import

Obviously make sure your usb stick is mounted first.

---

### Post by CAD-MAN on 2007-09-27
> **madoracle said:**
> ```
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

I could be wrong but it looks like your controller is there and operational, the problem might be with alsamixer. Try:

sudo apt-get install alsamixer 

Or wait for a better reply than mine :D

For the bookmarks, in Firefox, go into:

Bookmarks - Organize Bookmarks - File - Import

Obviously make sure your usb stick is mounted first.

Thanks madoracle.

I did sudo aptitude install alsamixer, but it couldn't find anything matching that name. The terminal instead recommended gnome-alsamixer, so I installed that instead.

I opened it, then clicked sound card properties, but the program keeps crashing...

Any other ideas?

---

### Post by CAD-MAN on 2007-09-27
Sorry for the bump - I'm desperate!

---

### Post by BobLand on 2007-09-27
CAD-MAN,
Try this link.  [URL="http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound"]
[COLOR="Red"]_Sound Problem Solutions Guide v0.5e_[/COLOR][/URL]

The procedure outlined on this thread usually applies to desktop machines and will work on laptops 50-50.  However, run through this procedure anyway because even if it doesn't work you will learn a lot about sound.

You are not alone with this problem.  Many users have issues with sound and many threads are written about it.  Search "no sound,"  "sound problems,"  "sound not working," "laptop sound,"  and the like.  This will yield many threads.

Unfortunately, you will have to read most to find out your problem can be solve with a few lines of configuration code.  Hang in there.  It will work!

bobland

---

### Post by CAD-MAN on 2007-09-28
Thanks for the link Bobland.

I've tried it, but it looks like I need Alsamixer. It doesn't appear to be installed on my system, and I haven't had any luck with looking on the internet for how to download it. I've downloaded a tar.gz file of Alsamixer, but I don't know what to do with it now! Sorry, I feel like a bit of an idiot asking how to install a program :oops:

Whilst following the guide (I got about half way before getting confused and stopping), I managed to get some beeps out of my speakers, but on restart, the sound is back to being non-existant.

I'll try again when I have Alsamixer (whatever Alsamixer is! - some kind of sound manager?) up and running.

Thanks for all of the help :D

---

### Post by BobLand on 2007-09-28
CAD-MAN,
Alsamixer is just what it says...a sound mixer.  The interface looks just like a sound mixing board.  Most of the time it is set correctly.  In rare instances the sliders are turned off.

At the terminal did you type Alsamixer or alsamixer.  Linux is case sensitive.  If you typed Alsamixer you'll get
```
bash: Alsamixer: command not found
```
The lower case should bring it up.  This is a standard program that is included with all installations.  You shouldn't have to install it.  If you do need to install it, reply back and I'll walk you through the steps.  It will seem weird, confusing and complex but after a while it's just another ho-hum.

Linux can be brutal for someone who has never worked in a terminal mode.  It's good to become familiar with the terminal.  Here's a list of tutorials to get you started.  Don't worry if you don't understand them but do look and try.  After a while you'll get it.

In no particular order (except for the first one)...
[http://linuxcommand.org/](http://linuxcommand.org/)
[http://www.yolinux.com/TUTORIALS/index.html](http://www.yolinux.com/TUTORIALS/index.html)
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
[http://www.ss64.com/bash](http://www.ss64.com/bash)
[http://linux.byexamples.com](http://linux.byexamples.com)

advanced tutorials to look at when you're more comfortable
[http://www.buzzsurf.com/surfatwork/](http://www.buzzsurf.com/surfatwork/)
[http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables](http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables)
[http://dmiessler.com/blogarchive/why-you-should-encrypt-all-of-your-google-activities-poc](http://dmiessler.com/blogarchive/why-you-should-encrypt-all-of-your-google-activities-poc)
[http://www.grymoire.com/Unix/Sed.html#uh-0](http://www.grymoire.com/Unix/Sed.html#uh-0)
[http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)

Use google with search strings like: linux, linux tutorials, linux commands, linux terminals, linux usage, linux installation, tar, bzip, gunzip, etc.  You'll get enough results to keep you busy for a year or two...

In the terminal type "man tar" without the quotes.  You will see a fairly terse description of what tar is and how to use it.  It will tell you every thing and much more about using it to extract and assemble files from the tar.  It's pretty much the standard tool for backing up files.  To leave the man page type q.

The tar assembles all of the program's components into a "package."  The gz compresses it so you have to untar it and uncompress it at the same time.  After reading the man page tar try the same with gunzip, man gunzip, then man bzip.  Use the man pages for any command.  It is the Linux dictionary.

Don't try to learn linux in a day or two.  It is a large deep program that will surprise you all the time, even after many years of usage.


Hope this helps,
bobland

---

### Post by CAD-MAN on 2007-09-28
The result of typing 'alsamixer' into the terminal:
```
alsamixer: function snd_ctl_open failed for default: No such device

```;

The result of typing 'Alsamixer', and 'AlsaMixer':
```
bash: AlsaMixer: command not found
```

I'm just guessing here, but it really looks to me as if 'Alsamixer' is not installed. I knew that I ran the risk of having problems by installing an uncompleted version of Gutsy, but I thought it would be worth the gamble! (for the most part it has, its just this sound problem thats annoying).

Thanks for the tutorials Bobland, I'll be sure to look through them and experiment :). I've been trying to get to grips with the terminal, and I know a little bit from my time here on the forums, but all I've really been doing is downloading programs with the terminal.

Oh, and I tried to set the ownership of a partition that I use to share music between Windows and Ubuntu, from root, to myself, but it didnt work.

I did sudo chown -R cadman /media/sda7

(I made the partition in Vista, and called it 'media', without realising that Ubuntu already has /media, so it is in media/sda7)

Thanks again for your help and patience

---

### Post by BobLand on 2007-09-29
I forgot to mention that quite a while ago, my alsamixer vanished.  I tried a few things but none worked.  I also noticed that it didn't affect my sound at all.  I've been running for a few months *without* alsamixer so, at this point, I'm thinking alsamixer is not your problem.

Setting permission on your partition wont help unless you make the correct entry in /etc/fstab.  Format the entry like the others.  Then run
```
sudo mount -a
```

Check /etc/mtab to make sure the entry is found there as well.  If not, make sure entry in /media is correct or that it exists.

As I recall this is something that should be part of gutsy, beta or not.  It should contain nttf-3 or something like that as well as an automatic samba link to any Windows file.

Try a bunch of things, but don't change your regular links in fstab and mtab.  In fact, before you mess around, backup both of them to something like fstab.2007.09.29 (today's date)
```
sudo cp /etc/fstab /etc/fstab.<your extension description>
```.
This is a good practice when ever you are going to change something.  Virtually any file that you modify that requires sudo should be backed up before proceeding.  Using a date as an extension will help you identify somthing that worked because you may want to try something different.  I have many versions of xorg.conf, including some that say xorg.conf.works.yyyymmdd.

If you have other hard disks with enough space, set up a sandbox to play in so you don't create a situation where you blow both up.  That is, in linux make a small ext3 partition and create an NTFS partition for Windows.  Boot into Windows to make sure the partition is valid and copy some files into it.

I had Windows2000 installed dual booting with Ubuntu.  I used Partition Magic to resize a Windows partion and it blew it up so badly, Windows would not install saying the disk was damaged.  That was a few months ago.  Since then I am 100% linux.

Sorry about my rambling on and on...
bobland

---

