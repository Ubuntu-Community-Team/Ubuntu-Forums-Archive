---
title: "Tiny, unreadable text on boot &amp; virtual console"
date: 2013-09-14
forum: Any Other OS
---

### Post by 64bitiso on 2013-09-14
Hi all. I am running Linux Mint 15 x64, on an Asus P5LD2/VM motherboard (integrated Intel GPU), and when I boot up AND when I enter virtual console (CTRL+ALT+F1, F2 etc) I see TINY, squashed text:

[ATTACH=CONFIG]246235[/ATTACH]

I've tried various GRUB lines to no avail - if anyone could help, I'd appreciate it massively, and thank you :)


Current /etc/default/grub:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=20
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768x16
GRUB_TERMINAL=console


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"

```


lshw, lspci & dmidecode output:

```
user
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3128MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cfe00000-cfe7ffff ioport:8800(size=8) memory:d0000000-dfffffff memory:cfe80000-cfebffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:41 memory:cfef8000-cfefbfff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:c8000000-c81fffff ioport:c8200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) memory:cff00000-cfffffff ioport:c8400000(size=2097152)
           *-network
                description: Ethernet interface
                product: 82573L Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 00
                serial: 00:18:f3:85:ed:29
                capacity: 1Gbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k firmware=0.5-7 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:40 memory:cffe0000-cfffffff ioport:d800(size=32)
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:9000(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:9400(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:9800(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:a000(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:cfeffc00-cfefffff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:c000(size=4096)
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: NM10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:b800(size=8) ioport:b400(size=4) ioport:b000(size=8) ioport:a800(size=4) ioport:a400(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: CD-RW  CRX850E
             vendor: SONY
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 5YK3
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5.1.1
       logical name: wlan1
       serial: 7c:dd:90:41:43:d7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.8.0-19-generic firmware=0.29 ip=192.168.1.62 link=yes multicast=yes wireless=IEEE 802.11bgn
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 004 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 005: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 006: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003 / Trust Optical USB MultiColour Mouse MI-2330
# dmidecode 2.11
SMBIOS 2.4 present.
66 structures occupying 2298 bytes.
Table at 0x000F04E0.


Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 1401   
    Release Date: 06/01/2007
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 512 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 8.10


Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Viglen
    Product Name: VIG580S
    Version: 00:18:F3:85:ED:29
    Serial Number: 1878573
    UUID: 6CD8B5A1-74FE-D511-9358-A8202BC03CAD
    Wake-up Type: Power Switch
    SKU Number: To Be Filled By O.E.M.
    Family: To Be Filled By O.E.M.


Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: P5LD2-VM
    Version: Rev 1.xx
    Serial Number: MB-1234567890
    Asset Tag: To Be Filled By O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To Be Filled By O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0


Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
    Manufacturer: Chassis Manufacture
    Type: Desktop
    Lock: Present
    Version: Chassis Version
    Serial Number: Chassis Serial Number
    Asset Tag: NONE
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000001
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0


Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: LGA 775
    Type: Central Processor
    Family: Celeron
    Manufacturer: Intel            
    ID: 49 0F 00 00 FF FB EB BF
    Signature: Type 0, Family 15, Model 4, Stepping 9
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        DS (Debug store)
        ACPI (ACPI supported)
        MMX (MMX technology supported)
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        HTT (Multi-threading)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: Intel(R) Celeron(R) CPU 3.06GHz                     
    Voltage: 1.3 V
    External Clock: 133 MHz
    Max Speed: 3800 MHz
    Current Speed: 3066 MHz
    Status: Populated, Enabled
    Upgrade: Other
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: 0x0007
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.


Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1-Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 16 kB
    Maximum Size: 16 kB
    Supported SRAM Types:
        Pipeline Burst
    Installed SRAM Type: Pipeline Burst
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: 8-way Set-associative


Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2-Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 256 kB
    Maximum Size: 256 kB
    Supported SRAM Types:
        Pipeline Burst
    Installed SRAM Type: Pipeline Burst
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 4-way Set-associative


Handle 0x0007, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L3-Cache
    Configuration: Disabled, Not Socketed, Level 3
    Operational Mode: Unknown
    Location: Internal
    Installed Size: 0 kB
    Maximum Size: 0 kB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unknown
    Associativity: Unknown


Handle 0x0008, DMI type 5, 24 bytes
Memory Controller Information
    Error Detecting Method: None
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 1024 MB
    Maximum Total Memory Size: 4096 MB
    Supported Speeds:
        70 ns
        60 ns
        50 ns
    Supported Memory Types:
        DIMM
        SDRAM
    Memory Module Voltage: 3.3 V
    Associated Memory Slots: 4
        0x0009
        0x000A
        0x000B
        0x000C
    Enabled Error Correcting Capabilities:
        None


Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM0
    Bank Connections: 1 5
    Current Speed: 37 ns
    Type: DIMM SDRAM
    Installed Size: 1024 MB (Double-bank Connection)
    Enabled Size: 1024 MB (Double-bank Connection)
    Error Status: OK


Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM1
    Bank Connections: 1 5
    Current Speed: 37 ns
    Type: DIMM SDRAM
    Installed Size: 1024 MB (Double-bank Connection)
    Enabled Size: 1024 MB (Double-bank Connection)
    Error Status: OK


Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM2
    Bank Connections: 1 5
    Current Speed: 37 ns
    Type: DIMM SDRAM
    Installed Size: 1024 MB (Double-bank Connection)
    Enabled Size: 1024 MB (Double-bank Connection)
    Error Status: OK


Handle 0x000C, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM3
    Bank Connections: 1 5
    Current Speed: 37 ns
    Type: DIMM SDRAM
    Installed Size: 256 MB (Single-bank Connection)
    Enabled Size: 256 MB (Single-bank Connection)
    Error Status: OK


Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS2Mouse
    Internal Connector Type: None
    External Reference Designator: PS2Mouse
    External Connector Type: PS/2
    Port Type: Mouse Port


Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Keyboard
    Internal Connector Type: None
    External Reference Designator: Keyboard
    External Connector Type: PS/2
    Port Type: Keyboard Port


Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB1
    Internal Connector Type: None
    External Reference Designator: USB1
    External Connector Type: Access Bus (USB)
    Port Type: USB


Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB2
    Internal Connector Type: None
    External Reference Designator: USB2
    External Connector Type: Access Bus (USB)
    Port Type: USB


Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB3
    Internal Connector Type: None
    External Reference Designator: USB3
    External Connector Type: Access Bus (USB)
    Port Type: USB


Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB4
    Internal Connector Type: None
    External Reference Designator: USB4
    External Connector Type: Access Bus (USB)
    Port Type: USB


Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB5
    Internal Connector Type: None
    External Reference Designator: USB5
    External Connector Type: Access Bus (USB)
    Port Type: USB


Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB6
    Internal Connector Type: None
    External Reference Designator: USB6
    External Connector Type: Access Bus (USB)
    Port Type: USB


Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB7
    Internal Connector Type: None
    External Reference Designator: USB7
    External Connector Type: Access Bus (USB)
    Port Type: USB


Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB8
    Internal Connector Type: None
    External Reference Designator: USB8
    External Connector Type: Access Bus (USB)
    Port Type: USB


Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: LPT 1
    Internal Connector Type: None
    External Reference Designator: LPT 1
    External Connector Type: DB-25 male
    Port Type: Parallel Port ECP/EPP


Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: COM A
    Internal Connector Type: None
    External Reference Designator: COM A
    External Connector Type: DB-9 male
    Port Type: Serial Port 16550A Compatible


Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: LINE IN
    Internal Connector Type: None
    External Reference Designator: Line IN
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port


Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: LINE OUT
    Internal Connector Type: None
    External Reference Designator: Line OUT
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port


Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: MIC IN
    Internal Connector Type: None
    External Reference Designator: MIC IN
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port


Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Back Surround L/R
    Internal Connector Type: None
    External Reference Designator: Back Surround L/R
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port


Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Side Surround L/R
    Internal Connector Type: None
    External Reference Designator: Side Surround L/R
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port


Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Center/LFE
    Internal Connector Type: None
    External Reference Designator: Center/LFE
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port


Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SPDIF OUT
    Internal Connector Type: None
    External Reference Designator: SPDIF OUT
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port


Handle 0x0020, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: GbE LAN
    Internal Connector Type: None
    External Reference Designator: GbE LAN
    External Connector Type: RJ-45
    Port Type: Network Port


Handle 0x0021, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: ITE IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other


Handle 0x0022, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SB IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other


Handle 0x0023, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SB SATA1
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other


Handle 0x0024, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SB SATA2
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other


Handle 0x0025, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SB SATA3
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other


Handle 0x0026, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SB SATA4
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other


Handle 0x0027, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: CD
    Internal Connector Type: On Board Sound Input From CD-ROM
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Audio Port


Handle 0x0028, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: FP AUD
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other


Handle 0x0029, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: FLOPPY
    Internal Connector Type: On Board Floppy
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other


Handle 0x002A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: CHASSIS FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other


Handle 0x002B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: CPU FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other


Handle 0x002C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: POWER FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other


Handle 0x002D, DMI type 9, 13 bytes
System Slot Information
    Designation: PCIEX16
    Type: 32-bit PCI-X
    Current Usage: Available
    Length: Short
    ID: 0
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported


Handle 0x002E, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI 1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 5
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported


Handle 0x002F, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI 2
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 6
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported


Handle 0x0030, DMI type 9, 13 bytes
System Slot Information
    Designation: PCIEX1 1
    Type: 32-bit PCI-X
    Current Usage: Available
    Length: Short
    ID: 3
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported


Handle 0x0031, DMI type 10, 6 bytes
On Board Device Information
    Type: Ethernet
    Status: Enabled
    Description: To Be Filled By O.E.M.


Handle 0x0032, DMI type 11, 5 bytes
OEM Strings
    String 1: To Be Filled By O.E.M.
    String 2: To Be Filled By O.E.M.
    String 3: To Be Filled By O.E.M.
    String 4: To Be Filled By O.E.M.


Handle 0x0033, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Abbreviated
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1


Handle 0x0034, DMI type 15, 35 bytes
System Event Log
    Area Length: 4 bytes
    Header Start Offset: 0x0000
    Header Length: 2 bytes
    Data Start Offset: 0x0002
    Access Method: Indexed I/O, one 16-bit index port, one 8-bit data port
    Access Address: Index 0x046A, Data 0x046C
    Status: Invalid, Not Full
    Change Token: 0x00000000
    Header Format: No Header
    Supported Log Type Descriptors: 6
    Descriptor 1: End of log
    Data Format 1: OEM-specific
    Descriptor 2: End of log
    Data Format 2: OEM-specific
    Descriptor 3: End of log
    Data Format 3: OEM-specific
    Descriptor 4: End of log
    Data Format 4: OEM-specific
    Descriptor 5: End of log
    Data Format 5: OEM-specific
    Descriptor 6: End of log
    Data Format 6: OEM-specific


Handle 0x0035, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 1 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4


Handle 0x0036, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000C7FFFFFF
    Range Size: 3200 MB
    Physical Array Handle: 0x0035
    Partition Width: 4


Handle 0x0037, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0035
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: <OUT OF SPEC>
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0


Handle 0x0038, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 1 GB
    Physical Device Handle: 0x0037
    Memory Array Mapped Address Handle: 0x0036
    Partition Row Position: 1
    Interleaved Data Depth: 1


Handle 0x0039, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0035
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: <OUT OF SPEC>
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1


Handle 0x003A, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00040000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 1 GB
    Physical Device Handle: 0x0039
    Memory Array Mapped Address Handle: 0x0036
    Partition Row Position: 1
    Interleaved Data Depth: 1


Handle 0x003B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0035
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: <OUT OF SPEC>
    Set: None
    Locator: DIMM2
    Bank Locator: BANK2
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz
    Manufacturer: Manufacturer2
    Serial Number: SerNum2
    Asset Tag: AssetTagNum2
    Part Number: PartNum2


Handle 0x003C, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00080000000
    Ending Address: 0x000BFFFFFFF
    Range Size: 1 GB
    Physical Device Handle: 0x003B
    Memory Array Mapped Address Handle: 0x0036
    Partition Row Position: 1
    Interleaved Data Depth: 1


Handle 0x003D, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0035
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 256 MB
    Form Factor: <OUT OF SPEC>
    Set: None
    Locator: DIMM3
    Bank Locator: BANK3
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz
    Manufacturer: Manufacturer3
    Serial Number: SerNum3
    Asset Tag: AssetTagNum3
    Part Number: PartNum3


Handle 0x003E, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x000C0000000
    Ending Address: 0x000CFFFFFFF
    Range Size: 256 MB
    Physical Device Handle: 0x003D
    Memory Array Mapped Address Handle: 0x0036
    Partition Row Position: 1
    Interleaved Data Depth: 1


Handle 0x003F, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected


Handle 0x0040, DMI type 129, 8 bytes
OEM-specific Type
    Header and Data:
        81 08 40 00 01 01 02 01
    Strings:
        Intel_ASF
        Intel ASF_001


Handle 0x0041, DMI type 127, 4 bytes
End Of Table



```

---

### Post by Bashing-om on 2013-09-14
64bitiso; Hi !

What pops to mind is an unsupported graphics mode:
reference:
> 

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768x16
GRUB_TERMINAL=console


Did you heed the advisory to check the output of "vbeinfo" - from the grub prompt ?
also with "GRUB_TERMINAL=console" as I am sure you are aware, will have to manually start the GUI interface.

[INDENT]hey, it's a thought
[/INDENT]

---

### Post by 64bitiso on 2013-09-14
Hello! Thank you for replying :)

Yes, I ran vbeinfo, and the mode you quoted is one of those listed in the vbeinfo returned scan. Also, you say I need to "startx" manually? Nope, not so.

:)

---

### Post by sisco311 on 2013-09-14
Moved to **Other OS/Distro Support**.

---

### Post by Bashing-om on 2013-09-14
64bitiso; That suggest to me that you are not booting the grub that you think you are.
> 
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

How many hard disk are installed and what operating systems do you presently have installed ?
 #To see what drive grub2 uses see this:
```

sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
##verification by UUID:
sudo grub-probe -t fs_uuid /boot/grub

```

else: going to be a learning experience !

[INDENT][INDENT]a need to know
[/INDENT][/INDENT]

---

### Post by 64bitiso on 2013-09-14
> **Bashing-om said:**
> 64bitiso; That suggest to me that you are not booting the grub that you think you are.

How many hard disk are installed and what operating systems do you presently have installed ?
 #To see what drive grub2 uses see this:
```




[COLOR=#ff0000]sudo debconf-show grub-pc
[/COLOR][COLOR=#ff8c00]sudo grub-probe -t device /boot/grub
[/COLOR]##verification by UUID:
[COLOR=#008000]sudo grub-probe -t fs_uuid /boot/grub
[/COLOR]
```

else: going to be a learning experience ![INDENT][INDENT]a need to know
[/INDENT]
[/INDENT]




[COLOR=#ff0000]sudo debconf-show grub-pc[/COLOR]
[COLOR=#ff0000]  grub-pc/kopt_extracted: false[/COLOR]
[COLOR=#ff0000]  grub2/kfreebsd_cmdline:[/COLOR]
[COLOR=#ff0000]  grub2/device_map_regenerated:[/COLOR]
[COLOR=#ff0000]* grub-pc/install_devices: /dev/disk/by-id/ata-Maxtor_6Y080M0_Y2A7ZRFE[/COLOR]
[COLOR=#ff0000]  grub-pc/postrm_purge_boot_grub: false[/COLOR]
[COLOR=#ff0000]  grub-pc/install_devices_failed_upgrade: true[/COLOR]
[COLOR=#ff0000]  grub-pc/disk_description:[/COLOR]
[COLOR=#ff0000]  grub2/linux_cmdline:[/COLOR]
[COLOR=#ff0000]  grub-pc/install_devices_empty: false[/COLOR]
[COLOR=#ff0000]  grub2/kfreebsd_cmdline_default: quiet splash[/COLOR]
[COLOR=#ff0000]  grub-pc/partition_description:[/COLOR]
[COLOR=#ff0000]  grub-pc/install_devices_failed: false[/COLOR]
[COLOR=#ff0000]  grub-pc/install_devices_disks_changed:[/COLOR]
[COLOR=#ff0000]  grub2/linux_cmdline_default: quiet splash[/COLOR]
[COLOR=#ff0000]  grub-pc/chainload_from_menu.lst: true[/COLOR]
[COLOR=#ff0000]  grub-pc/hidden_timeout: true[/COLOR]
[COLOR=#ff0000]  grub-pc/mixed_legacy_and_grub2: true[/COLOR]
[COLOR=#ff0000]  grub-pc/timeout: 10[/COLOR]


[COLOR=#ff8c00]/dev/sda1


[/COLOR][COLOR=#008000]bc31ab0a-725a-46c8-ae50-697c427c0cda


[/COLOR]Hello :)

** 1 drive, one partition, Linux Mint 15 x64

---

### Post by Bashing-om on 2013-09-14
64bitiso; Humm..
That totally blows my theory away .. huh ?
Have you done:
```

sudo update-grub

```
after making the changes to the /etc/default/grub config file ? For the changes to take effect.

else:
[INDENT][INDENT]we are going to be learning together
[/INDENT][/INDENT]

---

### Post by 64bitiso on 2013-09-14
> **Bashing-om said:**
> 64bitiso; Humm..
That totally blows my theory away .. huh ?
Have you done:
```

sudo update-grub

```
after making the changes to the /etc/default/grub config file ? For the changes to take effect.

else:[INDENT][INDENT]we are going to be learning together
[/INDENT]
[/INDENT]



Yes, I did that. I'd not forget something so obvious (usually, LOL)

---

### Post by Bashing-om on 2013-09-14
64bitiso; Well, Presently I have no explanation !

So, let's take a gander at:
```

cat /boot/grub/grub.cfg

```
and see what is being parsed.
Maybe figure out what is not happening.

[INDENT][INDENT]open season on learning
[/INDENT][/INDENT]

---

### Post by 64bitiso on 2013-09-14
> **Bashing-om said:**
> 64bitiso; Well, Presently I have no explanation !

So, let's take a gander at:
```

cat /boot/grub/grub.cfg

```
and see what is being parsed.
Maybe figure out what is not happening.
[INDENT][INDENT]open season on learning
[/INDENT]
[/INDENT]



Don't worry - I've now wiped the system in order to try another re-install and see if I can work this out myself, but thank you very much for all your time. Thankfully it is a spare machine, non-critical! :D


Take care!

---

### Post by Bashing-om on 2013-09-14
64bitiso; (re-)install is always one sure fix ! ..Works every time.

cheers

---

### Post by 64bitiso on 2013-09-14
> **Bashing-om said:**
> 64bitiso; (re-)install is always one sure fix ! ..Works every time.

cheers

He he, yes - it *can *be ^____^

I'll update you all with the solution, as/when it is reached.

God bless you, thx :)

---

