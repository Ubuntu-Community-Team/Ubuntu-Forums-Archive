---
title: "?Wireless/PCI? Driver issues"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by rich86 on 2007-06-08
Hi, i decided to take the plunge and install ubuntu yesterday, i tried to get wireless working on the LiveCD but failed to i installed to see if that improved my chances.
First off i tried installing the linux drivers from Realtek (the chipmaker of card) [its a unbranded cheapo card] and i got a load of errors i didn't really understand:
```
richard@richards:/media/RICHARD'S/temp/new/rtl8185_linux_26.1010.0531.2006$ ./makedrv
ieee80211/
ieee80211/ieee80211_tx.c
ieee80211/Modules.symvers
ieee80211/ieee80211_softmac_wx.c
ieee80211/LICENSE
ieee80211/ieee80211_rx.c
ieee80211/ieee80211_crypt_tkip.c
ieee80211/ieee80211_crypt.h
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_module.c
ieee80211/Makefile
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/ieee80211.h
ieee80211/ieee80211_softmac.c
ieee80211/README
ieee80211/ieee80211_wx.c
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211_crypt.c
rtl818x-0.1/
rtl818x-0.1/r8180_wx.h
rtl818x-0.1/r8180_wx.c
rtl818x-0.1/r8180_rtl8225.h
rtl818x-0.1/r8180_rtl8255.h
rtl818x-0.1/AUTHORS
rtl818x-0.1/r8180_max2820.c
rtl818x-0.1/r8180.h
rtl818x-0.1/r8180_max2820.h
rtl818x-0.1/tags
rtl818x-0.1/r8180_sa2400.h
rtl818x-0.1/r8180_93cx6.c
rtl818x-0.1/ieee80211.h
rtl818x-0.1/r8180_gct.c
rtl818x-0.1/r8180_gct.h
rtl818x-0.1/.r8180_core.o.d
rtl818x-0.1/r8180_rtl8225.c.old
rtl818x-0.1/Modules.symvers
rtl818x-0.1/CHANGES
rtl818x-0.1/LICENSE
rtl818x-0.1/r8180_93cx6.h
rtl818x-0.1/README.master
rtl818x-0.1/r8180_hw.h
rtl818x-0.1/README
rtl818x-0.1/r8180_pm.c
rtl818x-0.1/r8180_sa2400.c
rtl818x-0.1/COPYING
rtl818x-0.1/README.adhoc
rtl818x-0.1/r8180_rtl8225.c
rtl818x-0.1/.tmp_versions/
rtl818x-0.1/.tmp_versions/r8180.mod
rtl818x-0.1/INSTALL
rtl818x-0.1/r8180_rtl8255.c
rtl818x-0.1/r8180_core.c
rtl818x-0.1/r8180_pm.h
rtl818x-0.1/Makefile
rtl818x-0.1/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /media/RICHARD'S/temp/new/rtl8185_linux_26.1010.0531.2006/ieee80211/tmp
/bin/sh: Syntax error: Unterminated quoted string
make: *** [clean] Error 2
make -C /lib/modules/2.6.20-15-generic/build M=/media/RICHARD'S/temp/new/rtl8185_linux_26.1010.0531.2006/ieee80211 CC=gcc modules
/bin/sh: Syntax error: Unterminated quoted string
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /media/RICHARD'S/temp/new/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/tmp
/bin/sh: Syntax error: Unterminated quoted string
make: *** [clean] Error 2
make -C /lib/modules/2.6.20-15-generic/build M=/media/RICHARD'S/temp/new/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1 CC=gcc modules
/bin/sh: Syntax error: Unterminated quoted string
make: *** [modules] Error 2
```

then i tried using the windows drivers and Ndiswrapper GUI which i downloaded from windows. When i selected the inf file and selected install nothing happened and still no wireless.
I took a few screen dumps of the hardware pages and i am not sure what the icons mean, does it mean a load of the drivers for other things arn't installed??

here are the outputs from lshw and lspci:
```
richard@richards:/media/RICHARD'S/temp/new/rtl8185_linux_26.1010.0531.2006$ lshw
WARNING: you should run this program as super-user.
richards                  
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MB
     *-cpu
          product: AMD Sempron(tm) 2200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.8.1
          size: 1500MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: 741/741GX/M741 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: d0000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
          resources: iomemory:d0000000-d3ffffff
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: iomemory:ce000000-ceffffff iomemory:c0000000-c7ffffff irq:11
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: ioport:c00-c1f
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master scsi-host
             configuration: driver=pata_sis latency=128
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:ffa0-ffaf
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52
             resources: ioport:e800-e8ff ioport:ec00-ec7f irq:20
        *-usb:0
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:cffde000-cffdefff irq:17
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:cffdd000-cffddfff irq:16
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-15-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft Wireless Optical Mouse
                   vendor: Microsoft
                   physical id: 3
                   bus info: usb@1:3
                   version: 0.07
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: iomemory:cffdf000-cffdffff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: Flash Disk
                   vendor: USB
                   physical id: 2
                   bus info: usb@3:2
                   version: 2.00
                   capabilities: usb-2.00 scsi
                   configuration: driver=usb-storage maxpower=200mA speed=480.0MB/s
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@00:04.0
             logical name: eth0
             version: 90
             serial: 00:11:5b:8b:d0:45
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 multicast=yes
             resources: ioport:e400-e4ff iomemory:cffdc000-cffdcfff irq:19
        *-network:1 UNCLAIMED
             description: Ethernet controller
             product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@00:0b.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=64 maxlatency=64 mingnt=32
             resources: ioport:e000-e0ff iomemory:cffffc00-cffffdff irq:10
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage

richard@richards:/media/RICHARD'S/temp/new/rtl8185_linux_26.1010.0531.2006$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

richard@richards:/media/RICHARD'S/temp/new/rtl8185_linux_26.1010.0531.2006$ lspci -n
00:00.0 0600: 1039:0741 (rev 03)
00:01.0 0604: 1039:0003
00:02.0 0601: 1039:0963 (rev 25)
00:02.1 0c05: 1039:0016
00:02.5 0101: 1039:5513
00:02.7 0401: 1039:7012 (rev a0)
00:03.0 0c03: 1039:7001 (rev 0f)
00:03.1 0c03: 1039:7001 (rev 0f)
00:03.3 0c03: 1039:7002
00:04.0 0200: 1039:0900 (rev 90)
00:0b.0 0200: 10ec:8185 (rev 20)
01:00.0 0300: 10de:0322 (rev a1)

```

whats wrong and how do i get it working!! i don't and possibilities of connecting to a wired network here either, i have to keep switching between windows and ubuntu!
Many thanks in advance

---

### Post by rich86 on 2007-06-08
i also just tried manually installing the drivers using ndiswrapper but that failed, i got a dump from dmseg though (can't find any mention of the wlan card):
```
richard@richards:~$ sudo dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fed0000 end: 000000001ffd0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001ffd0000 size: 000000000000f000 end: 000000001ffdf000 type: 3
[    0.000000] copy_e820_map() start: 000000001ffdf000 size: 0000000000021000 end: 0000000020000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fffc0000 size: 0000000000040000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffd0000 - 000000001ffdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffdf000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 131024) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131024
[    0.000000]   HighMem    131024 ->   131024
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131024
[    0.000000] On node 0 totalpages: 131024
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125937 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f6750
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x08000427 MSFT 0x00000097) @ 0x1ffd0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x08000427 MSFT 0x00000097) @ 0x1ffd0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x08000427 MSFT 0x00000097) @ 0x1ffd0390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x08000427 MSFT 0x00000097) @ 0x1ffdf040
[    0.000000] ACPI: DSDT (v001   M863    M863G 0x00000000 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dffc0000)
[    0.000000] Detected 1499.836 MHz processor.
[   15.734114] Built 1 zonelists.  Total pages: 130001
[   15.734119] Kernel command line: root=UUID=28520748-a30f-4658-825a-f71a418d22f6 ro quiet splash
[   15.734336] mapped APIC to ffffd000 (fee00000)
[   15.734339] mapped IOAPIC to ffffc000 (fec00000)
[   15.734344] Enabling fast FPU save and restore... done.
[   15.734347] Enabling unmasked SIMD FPU exception support... done.
[   15.734362] Initializing CPU#0
[   15.734425] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   15.735841] Console: colour VGA+ 80x25
[   15.736288] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.736679] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.755574] Memory: 508352k/524096k available (1992k kernel code, 15192k reserved, 893k data, 328k init, 0k highmem)
[   15.755588] virtual kernel memory layout:
[   15.755590]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   15.755591]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.755593]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   15.755595]     lowmem  : 0xc0000000 - 0xdffd0000   ( 511 MB)
[   15.755597]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   15.755598]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   15.755600]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   15.755604] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.834325] Calibrating delay using timer specific routine.. 3001.43 BogoMIPS (lpj=6002870)
[   15.834384] Security Framework v1.0.0 initialized
[   15.834394] SELinux:  Disabled at boot.
[   15.834417] Mount-cache hash table entries: 512
[   15.834617] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[   15.834630] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.834633] CPU: L2 Cache: 256K (64 bytes/line)
[   15.834637] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[   15.834651] Compat vDSO mapped to ffffe000.
[   15.834659] Remapping vsyscall page to ffffe000
[   15.834672] Checking 'hlt' instruction... OK.
[   15.850470] SMP alternatives: switching to UP code
[   15.850808] Freeing SMP alternatives: 11k freed
[   15.851149] Early unpacking initramfs... done
[   16.269074] ACPI: Core revision 20060707
[   16.269892] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   16.271882] CPU0: AMD Sempron(tm) 2200+ stepping 01
[   16.271912] Total of 1 processors activated (3001.43 BogoMIPS).
[   16.272022] ENABLING IO-APIC IRQs
[   16.272211] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.417798] Brought up 1 CPUs
[   16.418140] Booting paravirtualized kernel on bare hardware
[   16.418233] Time: 11:42:47  Date: 05/08/107
[   16.418284] NET: Registered protocol family 16
[   16.418431] EISA bus registered
[   16.418438] ACPI: bus type pci registered
[   16.419670] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   16.419673] Setting up standard PCI resources
[   16.441117] ACPI: Interpreter enabled
[   16.441123] ACPI: Using IOAPIC for interrupt routing
[   16.441855] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.441862] PCI: Probing PCI hardware (bus 00)
[   16.442244] Enabling SiS 96x SMBus.
[   16.442779] Boot video device is 0000:01:00.0
[   16.442831] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.453589] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[   16.453908] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   16.454195] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[   16.454477] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[   16.454822] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 *7 10 11 12 14 15)
[   16.455116] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 7 10 11 12 14 15)
[   16.455404] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   16.455686] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[   16.455803] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.455822] pnp: PnP ACPI init
[   16.463216] pnp: PnP ACPI: found 12 devices
[   16.463223] PnPBIOS: Disabled by ACPI PNP
[   16.463316] PCI: Using ACPI for IRQ routing
[   16.463321] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.466192] NET: Registered protocol family 8
[   16.466195] NET: Registered protocol family 20
[   16.467335] PCI: Bridge: 0000:00:01.0
[   16.467339]   IO window: disabled.
[   16.467346]   MEM window: cde00000-cfefffff
[   16.467351]   PREFETCH window: bdd00000-cdcfffff
[   16.467403] NET: Registered protocol family 2
[   16.501768] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   16.501893] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   16.502165] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   16.502307] TCP: Hash tables configured (established 16384 bind 8192)
[   16.502311] TCP reno registered
[   16.513810] checking if image is initramfs... it is
[   17.303273] Freeing initrd memory: 7004k freed
[   17.303960] audit: initializing netlink socket (disabled)
[   17.303982] audit(1181302967.648:1): initialized
[   17.304139] VFS: Disk quotas dquot_6.5.1
[   17.304166] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.304236] io scheduler noop registered
[   17.304240] io scheduler anticipatory registered
[   17.304243] io scheduler deadline registered
[   17.304253] io scheduler cfq registered (default)
[   17.361052] isapnp: Scanning for PnP cards...
[   17.714161] isapnp: No Plug & Play device found
[   17.752420] Real Time Clock Driver v1.12ac
[   17.752490] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.752639] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.753789] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.754156] mice: PS/2 mouse device common for all mice
[   17.754950] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.755307] input: Macintosh mouse button emulation as /class/input/input0
[   17.755355] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.755361] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   17.755533] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   17.755783] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.755790] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.755960] EISA: Probing bus 0 at eisa.0
[   17.756002] EISA: Detected 0 cards.
[   17.786095] TCP cubic registered
[   17.786104] NET: Registered protocol family 1
[   17.786138] Using IPI No-Shortcut mode
[   17.786255] ACPI: (supports S0 S1 S3 S4 S5)
[   17.786312]   Magic number: 11:449:731
[   17.787051] Freeing unused kernel memory: 328k freed
[   17.788313] Time: tsc clocksource has been installed.
[   17.803781] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.096817] Capability LSM initialized
[   19.148073] ACPI: Processor [CPU1] (supports 8 throttling states)
[   19.846777] SCSI subsystem initialized
[   19.853475] libata version 2.20 loaded.
[   19.857440] pata_sis 0000:00:02.5: version 0.5.1
[   19.857569] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   19.857616] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   19.857641] scsi0 : pata_sis
[   19.891202] usbcore: registered new interface driver usbfs
[   19.891238] usbcore: registered new interface driver hub
[   19.891277] usbcore: registered new device driver usb
[   19.934179] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.957835] sis900.c: v1.08.10 Apr. 2 2006
[   20.052959] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   20.052967] ata1.00: ATA-7: WDC WD2500JB-00REA0, 20.00K20, max UDMA/100
[   20.052971] ata1.00: 488397168 sectors, multi 16: LBA48 
[   20.071271] Floppy drive(s): fd0 is 1.44M
[   20.083364] ata1.01: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   20.083373] ata1.01: ATA-7: WDC WD2500JB-00REA0, 20.00K20, max UDMA/100
[   20.083377] ata1.01: 488397168 sectors, multi 16: LBA48 
[   20.094223] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   20.094232] ata1.00: configured for UDMA/100
[   20.105282] FDC 0 is a post-1991 82077
[   20.106254] ata1.01: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   20.106262] ata1.01: configured for UDMA/100
[   20.106282] scsi1 : pata_sis
[   20.609536] ata2.00: ATAPI, max UDMA/66
[   20.609543] ata2.01: ATAPI, max MWDMA2
[   20.781375] ata2.00: configured for UDMA/66
[   20.953218] ata2.01: configured for PIO4
[   20.953427] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JB-00R 20.0 PQ: 0 ANSI: 5
[   20.953975] scsi 0:0:1:0: Direct-Access     ATA      WDC WD2500JB-00R 20.0 PQ: 0 ANSI: 5
[   20.955085] scsi 1:0:0:0: CD-ROM            DVDRW    DRW-3S163        BSG5 PQ: 0 ANSI: 5
[   20.956083] scsi 1:0:1:0: CD-ROM            COMPAQ   CD-ROM CRD-8484B 1.04 PQ: 0 ANSI: 5
[   20.962048] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   20.962073] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   20.962591] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   20.962622] ohci_hcd 0000:00:03.0: irq 16, io mem 0xcffdd000
[   20.989773] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   20.989802] sda: Write Protect is off
[   20.989805] sda: Mode Sense: 00 3a 00 00
[   20.989829] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.989935] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   20.989949] sda: Write Protect is off
[   20.989952] sda: Mode Sense: 00 3a 00 00
[   20.989972] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.989977]  sda: sda1 sda2 < sda5 >
[   21.007121] sd 0:0:0:0: Attached scsi disk sda
[   21.007367] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   21.007387] sdb: Write Protect is off
[   21.007390] sdb: Mode Sense: 00 3a 00 00
[   21.007412] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.007478] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   21.007492] sdb: Write Protect is off
[   21.007495] sdb: Mode Sense: 00 3a 00 00
[   21.007515] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.007519]  sdb: sdb1 sdb2 <<6>usb usb1: configuration #1 chosen from 1 choice
[   21.023081] hub 1-0:1.0: USB hub found
[   21.023099] hub 1-0:1.0: 3 ports detected
[   21.029654]  sdb5 sdb6 sdb7 >
[   21.059664] sd 0:0:1:0: Attached scsi disk sdb
[   21.065771] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.065803] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   21.065836] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[   21.065866] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   21.110486] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   21.110495] Uniform CD-ROM driver Revision: 3.20
[   21.110900] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   21.120923] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   21.121312] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   21.129033] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[   21.129058] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   21.129091] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   21.129119] ohci_hcd 0000:00:03.1: irq 17, io mem 0xcffde000
[   21.190885] usb usb2: configuration #1 chosen from 1 choice
[   21.190929] hub 2-0:1.0: USB hub found
[   21.190943] hub 2-0:1.0: 3 ports detected
[   21.296954] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 18
[   21.296976] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   21.297012] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[   21.297066] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[   21.297082] ehci_hcd 0000:00:03.3: irq 18, io mem 0xcffdf000
[   21.297092] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.297187] usb usb3: configuration #1 chosen from 1 choice
[   21.297224] hub 3-0:1.0: USB hub found
[   21.297238] hub 3-0:1.0: 6 ports detected
[   21.404860] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[   21.405798] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   21.415446] 0000:00:04.0: Using transceiver found at address 1 as default
[   21.416345] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 19, 00:11:5b:8b:d0:45.
[   21.553918] Attempting manual resume
[   21.553924] swsusp: Resume From Partition 8:23
[   21.553927] PM: Checking swsusp image.
[   21.554203] PM: Resume from disk failed.
[   21.595406] kjournald starting.  Commit interval 5 seconds
[   21.595426] EXT3-fs: mounted filesystem with ordered data mode.
[   21.983895] usb 1-3: new low speed USB device using ohci_hcd and address 3
[   22.209786] usb 1-3: configuration #1 chosen from 1 choice
[   29.526394] eth0: Media Link Off
[   30.694900] NET: Registered protocol family 17
[   31.624525] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   31.661077] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.663573] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.006077] Linux agpgart interface v0.102 (c) Dave Jones
[   32.010271] agpgart: Detected SiS 741 chipset
[   32.015590] agpgart: AGP aperture is 64M @ 0xd0000000
[   32.571903] input: PC Speaker as /class/input/input2
[   32.897320] usbcore: registered new interface driver hiddev
[   33.161567] input: Microsoft Microsoft Wireless Optical Mouseï¿½ 1.00 as /class/input/input3
[   33.162123] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouseï¿½ 1.00] on usb-0000:00:03.0-3
[   33.162150] usbcore: registered new interface driver usbhid
[   33.162156] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   33.290830] input: ImPS/2 Generic Wheel Mouse as /class/input/input4
[   33.301600] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 20
[   33.619624] intel8x0_measure_ac97_clock: measured 55896 usecs
[   33.619630] intel8x0: clocking to 48000
[   34.064326] fuse init (API version 7.8)
[   34.145565] lp: driver loaded but no devices found
[   34.195495] Adding 2096440k swap on /dev/disk/by-uuid/e7a0b29d-a342-9d87-7b50-3688067ed90b.  Priority:-1 extents:1 across:2096440k
[   34.368391] EXT3 FS on sdb6, internal journal
[   34.602287] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   34.636475] NTFS volume version 3.1.
[   34.678175] NTFS volume version 3.1.
[   34.725641] NTFS volume version 3.1.
[   34.761008] NTFS volume version 3.1.
[   38.726454] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   38.767471] usbcore: registered new interface driver ndiswrapper
[   40.347716] input: Power Button (FF) as /class/input/input5
[   40.354416] ACPI: Power Button (FF) [PWRF]
[   40.409439] input: Power Button (CM) as /class/input/input6
[   40.416102] ACPI: Power Button (CM) [PWRB]
[   40.494850] Using specific hotkey driver
[   40.595851] ibm_acpi: ec object not found
[   40.637792] No dock devices found.
[   40.819682] pcc_acpi: loading...
[   47.093187] ppdev: user-space parallel port driver
[   47.769693] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   47.769702] apm: overridden by ACPI.
[   63.304031] NET: Registered protocol family 10
[   63.304175] lo: Disabled Privacy Extensions
[   63.304267] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  334.894312] usbcore: deregistering interface driver ndiswrapper
[  558.237217] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[  558.249115] usbcore: registered new interface driver ndiswrapper
```
any ideas anyone????

---

