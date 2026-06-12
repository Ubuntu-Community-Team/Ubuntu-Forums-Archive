---
title: "NForce 430 MCP 61"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Ashrael on 2007-03-30
Hi, i've installed ubuntu on a NForce 430 MCP61 chipset motherboard. 

This is the lspci output:

$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 03ea (rev a1)
00:01.0 ISA bridge: nVidia Corporation Unknown device 03e0 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 03eb (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 03f5 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 03f4 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 03f1 (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 03f2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 03f3 (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 03ec (rev a2)
00:08.0 IDE interface: nVidia Corporation Unknown device 03f6 (rev a2)
00:09.0 PCI bridge: nVidia Corporation Unknown device 03e8 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation Unknown device 03d1 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


It gives an awfull lot of unknowns doesn't it.. So i decided to try PCLOS, awesome distro! Bit too windowslike for me, but anyhoo.. It does detect a lot more hardware for now... this is what i found in PCLOS:


AGP controllers:k8 [athlon64/opteron]

Identification
Vendor: &#8206;Advanced Micro Devices
Description: &#8206;K8 [Athlon64/Opteron] Miscellaneous Control
Media class: &#8206;BRIDGE_HOST
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;24
PCI function #: &#8206;3
Vendor ID: &#8206;0x1022
Device ID: &#8206;0x1103
Sub vendor ID: &#8206;0xffff
Sub device ID: &#8206;0xffff
Misc
Module: &#8206;amd64-agp
===
videocard

Identification
Vendor: &#8206;nVidia Corporation

Description: &#8206;GeForce 6100 nForce 405

Media class: &#8206;DISPLAY_VGA

Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;13
PCI function #: &#8206;0
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03d1
Sub vendor ID: &#8206;0x1849
Sub device ID: &#8206;0x03d1
Misc
Module: &#8206;unknown
===
processors

Identification
Processor ID: &#8206;1
Vendor: &#8206;AuthenticAMD
Model name: &#8206;AMD Athlon(tm) 64 Processor 3200+
Cpuid family: &#8206;15
Model: &#8206;95
Model stepping: &#8206;2
Connection
Vendor ID: &#8206;0x0000
Device ID: &#8206;0x0000
Sub vendor ID: &#8206;0x0000
Sub device ID: &#8206;0x0000
Performances
Frequency (MHz): &#8206;2000.000
Cache size: &#8206;512 KB
Bogomips: &#8206;4022.50
Bugs
Fdiv bug: &#8206;No
Coma bug: &#8206;No
F00f bug: &#8206;No
===
Sata controller

Identification
Vendor: &#8206;nVidia Corporation
Description: &#8206;MCP61 SATA Controller
Media class: &#8206;STORAGE_IDE
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;8
PCI function #: &#8206;0
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03f6
Sub vendor ID: &#8206;0x1849
Sub device ID: &#8206;0x03f6
Misc
Module: &#8206;sata_nv

(e)ide sata controller

Identification
Vendor: &#8206;nVidia Corporation
Description: &#8206;MCP61 IDE
Media class: &#8206;STORAGE_IDE
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;6
PCI function #: &#8206;0
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03ec
Sub vendor ID: &#8206;0x1849
Sub device ID: &#8206;0x03ec
Misc
Module: &#8206;amd74xx
===
USB controllers

Identification
Vendor: &#8206;nVidia Corporation

Description: &#8206;MCP61 USB Controller

Media class: &#8206;SERIAL_USB
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;2
PCI function #: &#8206;0
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03f1
Sub vendor ID: &#8206;0x1849
Sub device ID: &#8206;0x03f1
Misc
Module: &#8206;usb-ohci

Identification
Vendor: &#8206;nVidia Corporation
Description: &#8206;MCP61 USB Controller
Media class: &#8206;SERIAL_USB
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;2
PCI function #: &#8206;1
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03f2
Sub vendor ID: &#8206;0x1849
Sub device ID: &#8206;0x03f2
Misc
Module: &#8206;ehci-hcd

USB ports

Identification
Vendor: &#8206;Linux 2.6.18.6.tex1 ehci_hcd
Description: &#8206;EHCI Host Controller
Media class: &#8206;Hub|Unused
Connection
Bus: &#8206;USB
Bus PCI #: &#8206;2
PCI device #: &#8206;1
Vendor ID: &#8206;0x0000
Device ID: &#8206;0x0000
Sub vendor ID: &#8206;0x0000
Sub device ID: &#8206;0x0000
Misc
Module: &#8206;hub

Identification
Vendor: &#8206;Linux 2.6.18.6.tex1 ohci_hcd
Description: &#8206;OHCI Host Controller
Media class: &#8206;Hub|Unused
Connection
Bus: &#8206;USB
Bus PCI #: &#8206;1
PCI device #: &#8206;1
Vendor ID: &#8206;0x0000
Device ID: &#8206;0x0000
Sub vendor ID: &#8206;0x0000
Sub device ID: &#8206;0x0000
Misc
Module: &#8206;hub

SMBus contollers

Identification
Vendor: &#8206;nVidia Corporation
Description: &#8206;MCP61 SMBus
Media class: &#8206;SERIAL_SMBUS
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;1
PCI function #: &#8206;1
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03eb
Sub vendor ID: &#8206;0x1849
Sub device ID: &#8206;0x03eb
===
Bridge And Systems Controllers
=
MCP memory controller

Identification
Vendor: &#8206;nVidia Corporation
Description: &#8206;MCP61 Memory Controller
Media class: &#8206;MEMORY_RAM
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;0
PCI function #: &#8206;0
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03ea
Sub vendor ID: &#8206;0x1849
Sub device ID: &#8206;0x03ea
=
MCP61 LPC bridge

Identification
Vendor: &#8206;nVidia Corporation
Description: &#8206;MCP61 LPC Bridge
Media class: &#8206;BRIDGE_ISA
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;1
PCI function #: &#8206;0
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03e0
Sub vendor ID: &#8206;0x1849
Sub device ID: &#8206;0x03e0
=
MCP61 memory controller  #(no2)

Identification
Vendor: &#8206;nVidia Corporation
Description: &#8206;MCP61 Memory Controller
Media class: &#8206;MEMORY_RAM
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;1
PCI function #: &#8206;2
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03f5
Sub vendor ID: &#8206;0x1849
Sub device ID: &#8206;0x03eb
=
MCP61 PCI bridge

Identification
Vendor: &#8206;nVidia Corporation
Description: &#8206;MCP61 PCI bridge
Media class: &#8206;BRIDGE_PCI
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;4
PCI function #: &#8206;0
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03f3
Sub vendor ID: &#8206;0xffff
Sub device ID: &#8206;0xffff

=
MCP61 PCI express bridge

Identification
Vendor: &#8206;nVidia Corporation
Description: &#8206;MCP61 PCI Express bridge
Media class: &#8206;BRIDGE_PCI
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;9
PCI function #: &#8206;0
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03e8
Sub vendor ID: &#8206;0xffff
Sub device ID: &#8206;0xffff

=
MCP61 express bridge    #(no2)

Identification
Vendor: &#8206;nVidia Corporation
Description: &#8206;MCP61 PCI Express bridge
Media class: &#8206;BRIDGE_PCI
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;11
PCI function #: &#8206;0
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03e9
Sub vendor ID: &#8206;0xffff
Sub device ID: &#8206;0xffff

=
MCP61 PCI express bridge   #(no3)

Identification
Vendor: &#8206;nVidia Corporation
Description: &#8206;MCP61 PCI Express bridge
Media class: &#8206;BRIDGE_PCI
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;12
PCI function #: &#8206;0
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03e9
Sub vendor ID: &#8206;0xffff
Sub device ID: &#8206;0xffff

=
K8 [athlon/opteron] hypertransport

Identification
Vendor: &#8206;Advanced Micro Devices
Description: &#8206;K8 [Athlon64/Opteron] HyperTransport Technology Configuration
Media class: &#8206;BRIDGE_HOST
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;24
PCI function #: &#8206;0
Vendor ID: &#8206;0x1022
Device ID: &#8206;0x1100
Sub vendor ID: &#8206;0xffff
Sub device ID: &#8206;0xffff

=
K8 [Ath/Opt] Adress map

Identification
Vendor: &#8206;Advanced Micro Devices
Description: &#8206;K8 [Athlon64/Opteron] Address Map
Media class: &#8206;BRIDGE_HOST
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;24
PCI function #: &#8206;1
Vendor ID: &#8206;0x1022
Device ID: &#8206;0x1101
Sub vendor ID: &#8206;0xffff
Sub device ID: &#8206;0xffff

=
K8 [ath/opt] DRAM controller

Identification
Vendor: &#8206;Advanced Micro Devices
Description: &#8206;K8 [Athlon64/Opteron] DRAM Controller
Media class: &#8206;BRIDGE_HOST
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;24
PCI function #: &#8206;2
Vendor ID: &#8206;0x1022
Device ID: &#8206;0x1102
Sub vendor ID: &#8206;0xffff
Sub device ID: &#8206;0xffff

=
UNKNOWN/OTHERS

MCP61 SMU
Identification
Vendor: &#8206;nVidia Corporation
Description: &#8206;MCP61 SMU
Media class: &#8206;PROCESSOR_CO
Connection
Bus: &#8206;PCI
Bus PCI #: &#8206;0
PCI device #: &#8206;1
PCI function #: &#8206;3
Vendor ID: &#8206;0x10de
Device ID: &#8206;0x03f4
Sub vendor ID: &#8206;0x1849
Sub device ID: &#8206;0x03f4
Misc
Module: &#8206;unknown

I don't understand all of it, for instance: why do lots of item have either a known or an unknow module, and others not?
I am guessing that there must be more people who've got this problem...
Maybe we can help each other.....

I'll keep digging....and posting...

---

### Post by octaedro7 on 2007-07-04
Not really
This is Kubuntu feisty
her's my lspci:
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

Cannot record audio though

---

