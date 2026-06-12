---
title: "Early 2008 MacBook Trackpad working poorly after 16.10 upgrade"
date: 2017-04-25
forum: Apple Hardware Users
---

### Post by dancookhome on 2017-04-25
I'm new to Linux and after a successful conversion of an old Toshiba laptop I decided to make the switch on my old Mac. I initially installed 16.04 and I'm using rEFInd as a boot manager (although I have a single Ubuntu boot) but I was having a few issues with the Unity desktop only appearing half of the times I booted and with the system hanging when opening System Settings.

I thought I'd try an update to 16.10 to see if it helped. It's booting more quickly but I have a major issue with the trackpad which was perfect on 16.04. I can get the mouse pointer to move a little but it is very jumpy and only goes half way up the screen. I am able to open a the terminal via key commands so I'm hoping one of you command-line gurus will be able to suggest something. Many thanks!

---

### Post by mörgæs on 2017-04-26
Hi, welcome to the fora.

Let's see the hardware. Please copy ```
sudo lshw -sanitize > lshw.txt
``` to the command line and run it. After that post lshw.txt in CODE tags.

---

### Post by dancookhome on 2017-04-26
Hi

Thanks for helping me!

I've discovered a USB mouse works fine which has helped me greatly with this as I can copy and paste straight in. Here is lshw.txt:

```
computer    description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2016-10-10 00:20+0000X-Generator: Launchpad (build 18227)
    product: MacBook4,1 (System SKU#)
    vendor: Apple Inc.
    version: 1.0
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 smp vsyscall32
    configuration: boot=normal family=MacBook sku=System SKU# uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Mac-F22788A9
       vendor: Apple Inc.
       physical id: 0
       version: PVT
       serial: [REMOVED]
       slot: Part Component
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
          slot: U2E1
          size: 800MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf eagerfpu pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority dtherm cpufreq
        *-cache
             description: L1 cache
             physical id: 2
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
             configuration: level=1
     *-cache:0
          description: L1 cache
          physical id: 1
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
          configuration: level=1
     *-cpu:1
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 3
          bus info: cpu@1
          version: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
          slot: U2E1
          size: 2400MHz
          capacity: 2400MHz
          clock: 200MHz
          capabilities: cpufreq
        *-cache
             description: L1 cache
             physical id: 5
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
             configuration: level=1
     *-cache:1
          description: L1 cache
          physical id: 4
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 6
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: CT25664AC667.M16FH
             vendor: 0x7F7F7F7F7F9B0000
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: CT25664AC667.M16FH
             vendor: 0x7F7F7F7F7F9B0000
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-firmware
          description: BIOS
          vendor: Apple Inc.
          physical id: e
          version: MB41.88Z.00C1.B00.0802091535
          date: 02/09/08
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect acpi ieee1394boot smartbattery netboot
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:29 memory:d0100000-d01fffff memory:c0000000-cfffffff ioport:6110(size=8) memory:c0000-dffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:d0200000-d02fffff
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:60c0(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-46-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb:0
                   description: Bluetooth wireless interface
                   product: Bluetooth HCI
                   vendor: Apple, Inc.
                   physical id: 1
                   bus info: usb@3:1
                   version: 19.65
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb speed=12Mbit/s
              *-usb:1
                   description: Mouse
                   product: USB OPTICAL MOUSE
                   vendor: PIXART
                   physical id: 2
                   bus info: usb@3:2
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:60a0(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-46-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:21 memory:d0704c00-d0704fff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.8.0-46-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:30 memory:d0700000-d0703fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:d0600000-d06fffff ioport:d0800000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:d0500000-d05fffff ioport:d0000000(size=1048576)
           *-network
                description: Wireless interface
                product: BCM4321 802.11a/b/g/n
                vendor: Broadcom Limited
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wls4
                version: 03
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) ip=[REMOVED] latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:16 memory:d0500000-d0503fff memory:d0000000-d00fffff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:5000(size=4096) memory:d0400000-d04fffff ioport:d0a00000(size=2097152)
           *-network DISABLED
                description: Ethernet interface
                product: 88E8058 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: ens5
                version: 13
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:27 memory:d0400000-d0403fff ioport:5000(size=256) memory:d0420000-d043ffff
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:6080(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-46-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:6060(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-46-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6040(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.8.0-46-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 4.08
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb:0
                   description: Human interface device
                   product: IR Receiver
                   vendor: Apple Computer, Inc.
                   physical id: 1
                   bus info: usb@7:1
                   version: 0.16
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:1
                   description: Keyboard
                   product: Apple Internal Keyboard / Trackpad
                   vendor: Apple Computer
                   physical id: 2
                   bus info: usb@7:2
                   version: 0.07
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=40mA speed=12Mbit/s
        *-usb:6
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:d0704800-d0704bff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.8.0-46-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb
                   description: Video
                   product: Built-in iSight
                   vendor: Micron
                   physical id: 4
                   bus info: usb@2:4
                   version: 1.84
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=100mA speed=480Mbit/s
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:d0300000-d03fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW322/323 [TrueFire] 1394a Controller
                vendor: LSI Corporation
                physical id: 3
                bus info: pci@0000:04:03.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=248 maxlatency=24 mingnt=12
                resources: irq:19 memory:d0300000-d0300fff
        *-isa
             description: ISA bridge
             product: 82801HM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:21 ioport:6108(size=8) ioport:6124(size=4) ioport:6100(size=8) ioport:6120(size=4) ioport:60e0(size=16)
        *-storage
             description: SATA controller
             product: 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:28 ioport:60f8(size=8) ioport:611c(size=4) ioport:60f0(size=8) ioport:6118(size=4) ioport:6020(size=32) memory:d0704000-d07047ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d0705000-d07050ff ioport:efa0(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVDRW  GSA-S10N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: BP10
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=open
     *-scsi:1
          physical id: 5
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: FUJITSU MHY2160B
             vendor: Fujitsu
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 000D
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=00002a92
           *-volume:0 UNCLAIMED
                description: EFI GPT partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                capacity: 512MiB
                capabilities: primary nofs
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 144GiB
                capacity: 144GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2017-04-05 22:15:05 filesystem=ext4 lastmountpoint=/ modified=2017-04-26 21:23:13 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-04-26 21:23:24 state=mounted
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: [REMOVED]
                size: 4076MiB
                capacity: 4076MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
  *-battery
       product: Unknown
       vendor: Unknown
       physical id: 1
       version: Unknown
       serial: [REMOVED]
       slot: Unknown
```

---

### Post by mörgæs on 2017-04-27
With this hardware, especially the old Intel graphics processor, I would suggest a fresh install of X/Lubuntu, not Ubuntu.

16.10 is soon out of support so it's not relevant for a new install. Your choice is between 16.04.2 which might have more bugs but longer support time and 17.04 for which the opposite applies. Try both in a live boot an see if there is any difference. 

When you install best is to use a wired internet connection.

---

### Post by dancookhome on 2017-04-29
Before I saw your reply I went for broke and installed 17.04. It seems to have fixed the trackpad issue and runs quite well. I completely agree with you though, a lightweight distro might suit my old Mac better so I think a Lubuntu installation is on the cards!

---

### Post by mörgæs on 2017-04-29
Good, please post the results if/when you try Lubuntu 17.04.

---

### Post by ledlamp on 2017-05-03
> **dancookhome said:**
> Before I saw your reply I went for broke and installed 17.04. It seems to have fixed the trackpad issue and runs quite well. I completely agree with you though, a lightweight distro might suit my old Mac better so I think a Lubuntu installation is on the cards!
You can just install LXDE and select it at login; no need to erase and reinstall the whole OS again. And if there's a problem with LXDE you can switch back to Unity.

---

