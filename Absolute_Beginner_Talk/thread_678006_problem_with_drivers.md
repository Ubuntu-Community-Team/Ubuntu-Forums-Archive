---
title: "problem with drivers"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by makenshi on 2008-01-25
I am currently having problems with drivers for my wireless networking card. I have a Fujitsu scaleo H PC and I have just installed Ubuntui Linux onto it, I have managed to locate frivers for almost all of the hardware but wy wireless card remains a mystery. I do not know what it is called and the specification simply says 54 MBit (IEEE 802.11b/g). I have located drivers on the installation CD however they are currently in a setup.exe file and I have no way of running this type of file. Is there anyway I can extract the files from within the setup file or run the exe file.

I am a noob so please be kind, and thanks for any help you can provide

---

### Post by UltraMathMan on 2008-01-25
Could you post the output of ```
lspci -v
``` That might give some more info on the wireless card.

---

### Post by makenshi on 2008-01-25
wasn't sure which bits you need so posted the whole thing:

>  00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at e400 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 50
        Memory at d3104000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        Memory at feb00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8166
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=256]
        Memory at d3103000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at d800 [size=16]
        Memory at d3102000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at c400 [size=16]
        Memory at d3101000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=128
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d3000000-d30fffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 816a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 233
        Memory at d3100000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b000 [size=8]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: d0000000-d2ffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cff00000
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0162 (rev a1) (prog-if 00 [VGA])
        Subsystem: LeadTek Research Inc. Unknown device 5a39
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at d0000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at d1000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at d2000000 [disabled] [size=128K]
        Capabilities: <access denied>

05:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. A8V Deluxe
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 58
        Memory at d3010000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at a000 [size=128]
        Capabilities: <access denied>

05:04.0 Communication controller: Conexant HSF 56k Data/Fax Modem
        Subsystem: Conexant Unknown device 2000
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at d3000000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at a400 [size=8]
        Capabilities: <access denied>


If it matter I am using an older version of ubuntu version6.10 edgy eft, it came with lubuntu linux for dummies and thought I should stick with it for now at least until I learn what I'm doing since the book teachs from the earlier version

---

### Post by UltraMathMan on 2008-01-25
Hmmm, I don't see a wireless card listed, and you're right Fujitsu's specs are worthless. Try ```
sudo lshw
``` (Gives a detailed list of hardware) and post the output. You might also want to try contacting Fujitsu Tech Support and asking - they might be able to give you more info on the card model.

That aside if you can download the driver file for Windows, you might be able to get it working with ndiswrapper

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

-Hope this helps :)

---

### Post by makenshi on 2008-01-25
Update: found the drivers on windows and managed to install them using ndiswrapper, however it simply states that that driver is already installed, whenever I run ndiswrapper -l is displays x10hid : invalid driver! 

>         vendor: ASUSTek Computer INC. 
       physical id: 0 
       version: 1.00 
       serial: 123456789000 
     *-firmware 
          description: BIOS 
          vendor: Phoenix Technologies, LTD 
          physical id: 0 
          version: FUJITSU SIEMENS A8NE-FM 1011 (06/06/2006) 
          size: 128KB 
          capacity: 448KB 
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot 
     *-cpu:0 
          description: CPU 
          product: AMD Athlon(tm) 64 Processor 3500+ 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 3 
          bus info: cpu@0 
          version: AMD Athlon(tm) 64 Processor 3500+ 
          slot: Socket 939 
          size: 2200MHz 
          capacity: 3700MHz 
          width: 64 bits 
          clock: 201MHz 
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq 
        *-cache:0 
             description: L1 cache 
             physical id: b 
             slot: L1 Cache 
             size: 128KB 
             capacity: 128KB 
             capabilities: synchronous internal write-back data 
        *-cache:1 
             description: L2 cache 
             physical id: d 
             slot: L2 Cache 
             size: 512KB 
             capacity: 512KB 
             capabilities: synchronous internal write-back unified 
     *-cpu:1 DISABLED 
          description: CPU 
          vendor: Null 
          physical id: 5 
          bus info: cpu@1 
          version: Null 
          slot: Socket 939 
     *-cache:0 DISABLED 
          description: L1 cache 
          physical id: 4 
          slot: L1 Cache 
          capabilities: synchronous internal data 
     *-cache:1 DISABLED 
          description: L2 cache 
          physical id: c 
          slot: L2 Cache 
          capabilities: synchronous internal unified 
     *-memory:0 
          description: System Memory 
          physical id: 23 
          slot: System board or motherboard 
          size: 1536MB 
        *-bank:0 
             description: DIMM 
             physical id: 0 
             slot: A0 
             size: 512MB 
             width: 64 bits 
        *-bank:1 
             description: DIMM 
             physical id: 1 
             slot: A1 
             size: 512MB 
             width: 64 bits 
        *-bank:2 
             description: DIMM 
             physical id: 2 
             slot: A2 
             size: 256MB 
             width: 64 bits 
        *-bank:3 
             description: DIMM 
             physical id: 3 
             slot: A3 
             size: 256MB 
             width: 64 bits 
     *-memory:1 UNCLAIMED 
          description: Memory controller 
          product: CK804 Memory Controller 
          vendor: nVidia Corporation 
          physical id: e 
          bus info: pci@0000:00:00.0 
          version: a3 
          width: 32 bits 
          clock: 66MHz (15.2ns) 
          capabilities: ht bus_master cap_list 
          configuration: latency=0 
     *-isa 
          description: ISA bridge 
          product: CK804 ISA Bridge 
          vendor: nVidia Corporation 
          physical id: 1 
          bus info: pci@0000:00:01.0 
          version: f3 
          width: 32 bits 
          clock: 66MHz 
          capabilities: isa bus_master 
          configuration: latency=0 
     *-serial 
          description: SMBus 
          product: CK804 SMBus 
          vendor: nVidia Corporation 
          physical id: 1.1 
          bus info: pci@0000:00:01.1 
          version: a2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: pm cap_list 
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2 
     *-usb:0 
          description: USB Controller 
          product: CK804 USB Controller 
          vendor: nVidia Corporation 
          physical id: 2 
          bus info: pci@0000:00:02.0 
          version: a2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: pm ohci bus_master cap_list 
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd 
     *-usb:1 
          description: USB Controller 
          product: CK804 USB Controller 
          vendor: nVidia Corporation 
          physical id: 2.1 
          bus info: pci@0000:00:02.1 
          version: a3 
          width: 32 bits 
          clock: 66MHz 
          capabilities: debug pm ehci bus_master cap_list 
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd 
     *-multimedia 
          description: Multimedia audio controller 
          product: CK804 AC'97 Audio Controller 
          vendor: nVidia Corporation 
          physical id: f 
          bus info: pci@0000:00:04.0 
          version: a2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: pm bus_master cap_list 
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0 
     *-ide:0 
          description: IDE interface 
          product: CK804 IDE 
          vendor: nVidia Corporation 
          physical id: 6 
          bus info: pci@0000:00:06.0 
          version: f2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: ide pm bus_master cap_list 
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3 module=amd74xx 
        *-ide 
             description: IDE Channel 1 
             physical id: 1 
             bus info: ide@1 
             logical name: ide1 
             clock: 66MHz 
           *-cdrom:0 
                description: DVD reader 
                product: HL-DT-STDVD-ROM GDR8164B 
                physical id: 0 
                bus info: ide@1.0 
                logical name: /dev/hdc 
                version: 0F08 
                capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio dvd 
                configuration: mode=udma2 status=ready 
              *-disc 
                   physical id: 0 
                   logical name: /dev/hdc 
           *-cdrom:1 
                description: DVD-RAM writer 
                product: _NEC DVD_RW ND-4551A 
                physical id: 1 
                bus info: ide@1.1 
                logical name: /dev/hdd 
                version: 1-84 
                capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram 
                configuration: mode=udma2 status=nodisc 
     *-ide:1 
          description: IDE interface 
          product: CK804 Serial ATA Controller 
          vendor: nVidia Corporation 
          physical id: 7 
          bus info: pci@0000:00:07.0 
          version: f3 
          width: 32 bits 
          clock: 66MHz 
          capabilities: ide pm bus_master cap_list 
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv 
     *-ide:2 
          description: IDE interface 
          product: CK804 Serial ATA Controller 
          vendor: nVidia Corporation 
          physical id: 8 
          bus info: pci@0000:00:08.0 
          logical name: scsi2 
          version: f3 
          width: 32 bits 
          clock: 66MHz 
          capabilities: ide pm bus_master cap_list emulated 
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv 
        *-disk 
             description: SCSI Disk 
             product: WDC WD2500JS-55N 
             vendor: ATA 
             physical id: 0.0.0 
             bus info: scsi@2:0.0.0 
             logical name: /dev/sda 
             version: 10.0 
             serial: WD-WCANK2986818 
             size: 232GB 
             capabilities: partitioned partitioned:dos 
             configuration: ansiversion=5 
           *-volume:0 
                description: Linux filesystem partition 
                physical id: 1 
                bus info: scsi@2:0.0.0,1 
                logical name: /dev/sda1 
                capacity: 228GB 
                capabilities: primary bootable 
           *-volume:1 
                description: Extended partition 
                physical id: 2 
                bus info: scsi@2:0.0.0,2 
                logical name: /dev/sda2 
                size: 4424MB 
                capacity: 4424MB 
                capabilities: primary extended partitioned partitioned:extended 
              *-logicalvolume 
                   description: Linux swap / Solaris partition 
                   physical id: 5 
                   logical name: /dev/sda5 
                   capacity: 4424MB 
                   capabilities: nofs 
     *-pci:0 
          description: PCI bridge 
          product: CK804 PCI Bridge 
          vendor: nVidia Corporation 
          physical id: 9 
          bus info: pci@0000:00:09.0 
          version: f2 
          width: 32 bits 
          clock: 66MHz 
          capabilities: pci subtractive_decode bus_master 
        *-firewire 
             description: FireWire (IEEE 1394) 
             product: IEEE 1394 Host Controller 
             vendor: VIA Technologies, Inc. 
             physical id: 2 
             bus info: pci@0000:05:02.0 
             version: 80 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm ohci bus_master cap_list 
             configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394 
        *-communication UNCLAIMED 
             description: Communication controller 
             product: HSF 56k Data/Fax Modem 
             vendor: Conexant 
             physical id: 4 
             bus info: pci@0000:05:04.0 
             version: 00 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pm bus_master cap_list 
             configuration: latency=32 
     *-bridge 
          description: Ethernet interface 
          product: CK804 Ethernet Controller 
          vendor: nVidia Corporation 
          physical id: a 
          bus info: pci@0000:00:0a.0 
          logical name: eth0 
          version: f3 
          serial: 00:15:f2:f3:66:65 
          capacity: 100000000 
          width: 32 bits 
          clock: 66MHz 
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII 
     *-pci:1 
          description: PCI bridge 
          product: CK804 PCIE Bridge 
          vendor: nVidia Corporation 
          physical id: b 
          bus info: pci@0000:00:0b.0 
          version: f3 
          width: 32 bits 
          clock: 33MHz 
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
          configuration: driver=pcieport-driver 
     *-pci:2 
          description: PCI bridge 
          product: CK804 PCIE Bridge 
          vendor: nVidia Corporation 
          physical id: 100 
          bus info: pci@0000:00:0c.0 
          version: f3 
          width: 32 bits 
          clock: 33MHz 
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
          configuration: driver=pcieport-driver 
     *-pci:3 
          description: PCI bridge 
          product: CK804 PCIE Bridge 
          vendor: nVidia Corporation 
          physical id: d 
          bus info: pci@0000:00:0d.0 
          version: f3 
          width: 32 bits 
          clock: 33MHz 
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
          configuration: driver=pcieport-driver 
     *-pci:4 
          description: PCI bridge 
          product: CK804 PCIE Bridge 
          vendor: nVidia Corporation 
          physical id: 101 
          bus info: pci@0000:00:0e.0 
          version: a3 
          width: 32 bits 
          clock: 33MHz 
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list 
          configuration: driver=pcieport-driver 
        *-display 
             description: VGA compatible controller 
             product: NV44 [GeForce 6200SE TurboCache (TM)] 
             vendor: nVidia Corporation 
             physical id: 0 
             bus info: pci@0000:01:00.0 
             version: a1 
             width: 64 bits 
             clock: 33MHz 
             capabilities: pm msi pciexpress vga bus_master cap_list 
             configuration: latency=0 
     *-pci:5 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 102 
          bus info: pci@0000:00:18.0 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
     *-pci:6 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] Address Map 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 103 
          bus info: pci@0000:00:18.1 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
     *-pci:7 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] DRAM Controller 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 104 
          bus info: pci@0000:00:18.2 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
     *-pci:8 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] Miscellaneous Control 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 105 
          bus info: pci@0000:00:18.3 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
          configuration: driver=k8temp module=k8temp 
     *-scsi:0 
          physical id: 10 
          bus info: usb@2:7 
          logical name: scsi4 
          capabilities: emulated scsi-host 
          configuration: driver=usb-storage 
        *-disk:0 
             description: SCSI Disk 
             product: STORAGE DEVICE 
             vendor: Generic 
             physical id: 0.0.0 
             bus info: scsi@4:0.0.0 
             logical name: /dev/sdb 
             version: 9144 
             capabilities: removable 
           *-disc 
                physical id: 0 
                logical name: /dev/sdb 
        *-disk:1 
             description: SCSI Disk 
             product: STORAGE DEVICE 
             vendor: Generic 
             physical id: 0.0.1 
             bus info: scsi@4:0.0.1 
             logical name: /dev/sdc 
             version: 9144 
             capabilities: removable 
           *-disc 
                physical id: 0 
                logical name: /dev/sdc 
        *-disk:2 
             description: SCSI Disk 
             product: STORAGE DEVICE 
             vendor: Generic 
             physical id: 0.0.2 
             bus info: scsi@4:0.0.2 
             logical name: /dev/sdd 
             version: 9144 
             capabilities: removable 
           *-disc 
                physical id: 0 
                logical name: /dev/sdd 
        *-disk:3 
             description: SCSI Disk 
             product: STORAGE DEVICE 
             vendor: Generic 
             physical id: 0.0.3 
             bus info: scsi@4:0.0.3 
             logical name: /dev/sde 
             version: 9144 
             capabilities: removable 
           *-disc 
                physical id: 0 
                logical name: /dev/sde 
        *-disk:4 
             description: SCSI Disk 
             product: STORAGE DEVICE 
             vendor: Generic 
             physical id: 0.0.4 
             bus info: scsi@4:0.0.4 
             logical name: /dev/sdf 
             version: 9144 
             capabilities: removable 
           *-disc 
                physical id: 0 
                logical name: /dev/sdf 
     *-scsi:1 
          physical id: 11 
          bus info: usb@2:5 
          logical name: scsi5 
          capabilities: emulated scsi-host 
          configuration: driver=usb-storage 
        *-disk 
             description: SCSI Disk 
             product: JUMPDRIVE SPORT 
             vendor: LEXAR 
             physical id: 0.0.0 
             bus info: scsi@5:0.0.0 
             logical name: /dev/sdg 
             version: 1000 
             serial: 1000&#65533;#GENE 
             size: 61MB 
             capabilities: removable 
           *-disc 
                physical id: 0 
                logical name: /dev/sdg 
                size: 61MB 
                capabilities: partitioned partitioned:dos 
              *-volume 
                   description: FAT16 <32M partition 
                   physical id: 1 
                   logical name: /dev/sdg1 
                   capacity: 61MB 
                   capabilities: primary 


this has got me baffled as well as I cant see a wlan card in there however I have connected to my home wireless network using this computer without a usb receiver. have tried to contact fujitsu but am forced to resort to emailing them due to Cust support being closed at this late hour. 

As a possible side solution is there any way to share a connection through my windows vista laptop which can connect through wireless (prolly wrong place to ask tbh)

---

