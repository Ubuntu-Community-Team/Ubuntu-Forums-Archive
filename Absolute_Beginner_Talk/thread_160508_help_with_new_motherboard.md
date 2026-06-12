---
title: "help with new motherboard"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by slipk487 on 2006-04-15
i need help with a new motherboard i just got its a msi and when i try and install ubuntu it freezes up at something hotplug subsystem and it does the same thing for the live cd too wat do i do about it

---

### Post by mrchrisblau on 2006-04-15
Does it have any error messages when it freezes or does it just freeze? What type of msi board is it? 64 bit proc? 32 bit? Do you have all the stuff on the motherboard connected correctly (IDE, SATA, Power, Graphics card, CPU fan, RAM, etc)? How long after turning on the power does the ubuntu install freeze? What part of the install process (or boot process in terms of the live CD)?

Do you have any other OSs around? Perhaps you could try to boot the install off one of those. This would show if the error is between ubuntu and your hardware or if it is just your hardware.

---

### Post by slipk487 on 2006-04-15
[QUOTE=mrchrisblau]Does it have any error messages when it freezes or does it just freeze? What type of msi board is it? 64 bit proc? 32 bit? Do you have all the stuff on the motherboard connected correctly (IDE, SATA, Power, Graphics card, CPU fan, RAM, etc)? How long after turning on the power does the ubuntu install freeze? What part of the install process (or boot process in terms of the live CD)?

Do you have any other OSs around? Perhaps you could try to boot the install off one of those. This would show if the error is between ubuntu and your hardware or if it is just your hardware.[/QUOTE]

its a 865GVM2 P4 2.66 ghz and yes everything is installed correctly and the install gets past the first reboot and when the ubuntu screen thing pops up with what it is loading it freezes up at the hotplug subsystem and the live cd gets to the same point and freezes

---

### Post by mrchrisblau on 2006-04-15
I searched google a bit and found this:
[http://www.ubuntuforums.org/showthread.php?t=27672](http://www.ubuntuforums.org/showthread.php?t=27672)

That error is from a different ubuntu version but it might shed some light into what is going on with your box.

Sorry I can't be more helpful. ;)

---

### Post by slipk487 on 2006-04-15
didnt understand all of it but i cant even get it to finish the install

---

### Post by slipk487 on 2006-04-15
and the live cd doenst work eather

---

### Post by slipk487 on 2006-04-16
if this helps this is my system info

```
<<< System Summary >>>
--------------------------------------------------------------------------------
  < Processor >
    Model:                         Intel(R) Pentium(R) 4 CPU 2.66GHz
    Speed:                         2.67GHz
    Performance Rating:            PR2934 (estimated)
    Cores per Processor:           1 Unit(s)
    Threads per Core:              1 Unit(s)
    Internal Data Cache:           8kB Synchronous, Write-Thru, 4-way set, 64 
                                   byte line size
    L2 On-board Cache:             512kB ECC Synchronous, ATC, 8-way set, 64 
                                   byte line size, 2 lines per sector

  < Mainboard >
    Bus(es):                       ISA PCI IMB USB i2c/SMBus
    MP Support:                    1 Processor(s)
    MP APIC:                       Yes
    System BIOS:                   Phoenix Technologies, LTD 6.00 PG
    System:                        MICRO-STAR INTL, CO.,LTD. MS-7037
    Mainboard:                     MICRO-STAR INTL, CO.,LTD. MS-7037
    Total Memory:                  512MB DDR-SDRAM

  < Chipset 1 >
    Model:                         Intel Corporation 82865G/PE/P, 82848P DRAM 
                                   Controller / Host-Hub Interface
    Front Side Bus Speed:          4x 133MHz (532MHz data rate)
    Total Memory:                  512MB DDR-SDRAM
    Memory Bus Speed:              2x 166MHz (332MHz data rate)

  < Video System >
    Monitor/Panel:                 Default Monitor
    Monitor/Panel:                 Default Monitor
    Adapter:                       RADEON 9250 - Secondary
    Adapter:                       RADEON 9250 

  < Physical Storage Devices >
    Removable Drive:               Floppy disk drive
    Hard Disk:                     SAMSUNG SV0322A (3GB)
    Hard Disk:                     WDC AC26400R (6GB)
    CD-ROM/DVD:                    ATAPI CD-R/RW 12X8X32 (CD 32X Rd, 12X Wr)

  < Logical Storage Devices >
    1.44MB 3.5" (A:):              N/A
    Hard Disk (C:):                6GB (2.3GB, 38% Free Space) (NTFS)
    Warcraft iii (D:):             632MB (CDFS)

  < Peripherals >
    Serial/Parallel Port(s):       2 COM / 1 LPT
    USB Controller/Hub:            Intel(R) 82801EB USB Universal Host 
                                   Controller - 24D2
    USB Controller/Hub:            Intel(R) 82801EB USB Universal Host 
                                   Controller - 24D4
    USB Controller/Hub:            Intel(R) 82801EB USB Universal Host 
                                   Controller - 24D7
    USB Controller/Hub:            Intel(R) 82801EB USB2 Enhanced Host 
                                   Controller - 24DD
    USB Controller/Hub:            Intel(R) 82801EB USB Universal Host 
                                   Controller - 24DE
    USB Controller/Hub:            USB Root Hub
    USB Controller/Hub:            USB Root Hub
    USB Controller/Hub:            USB Root Hub
    USB Controller/Hub:            USB Root Hub
    USB Controller/Hub:            USB Root Hub
    USB Controller/Hub:            Generic USB Hub
    Keyboard:                      Standard 101/102-Key or Microsoft Natural PS/
                                   2 Keyboard
    Mouse:                         Logitech USB Cordless Mouse
    Human Interface:               Logitech USB Cordless Mouse

  < MultiMedia Device(s) >
    Device:                        Standard Game Port
    Device:                        Realtek AC'97 Audio

  < Power Management >
    AC Line Status:                On-Line

  < Operating System(s) >
    Windows System:                Microsoft Windows XP/2002 Home (Win32 x86) 
                                   5.01.2600 (Service Pack 2)

  < Network Services >
    Adapter:                       Realtek RTL8139/810x Family Fast Ethernet NIC

  < Performance Tips >
    Tip 2546:                      Large memory modules should be ECC/Parity.
    Tip 2:                         Double-click tip or press Enter while a tip 
                                   is selected for more information about the 
                                   tip.

<<< Mainboard Information >>>
--------------------------------------------------------------------------------

  < System >
    Manufacturer:                  MICRO-STAR INTL, CO.,LTD.
    Model:                         MS-7037
    Version:                       Ver 0A
    ID:                            FFFFFFFF-FFFFFFFF-FFFFFFFF-FFFFFFFF

  < Mainboard >
    Manufacturer:                  MICRO-STAR INTL, CO.,LTD.
    MP Support:                    1 Processor(s)
    MPS Version:                   1.40
    Model:                         MS-7037
    Version:                       Ver 0A
    System BIOS:                   12/23/2004-Springdale-G-6A79AM4VC-00
    Chipset:                       Intel 865/848 (Springdale)

  < System Memory Controller >
    Location:                      Mainboard
    Error Correction Capability:   None
    Number of Memory Slots:        4
    Maximum Installable Memory:    4GB
    Bank0/1 - A0:                  DIMM Synchronous SDRAM 512MB/64
    Bank2/3 - A1:                  Empty
    Bank4/5 - A2:                  Empty
    Bank6/7 - A3:                  Empty

  < Chipset 1 >
    Model:                         Intel Corporation 82865G/PE/P, 82848P DRAM 
                                   Controller / Host-Hub Interface
    Bus(es):                       ISA PCI IMB USB i2c/SMBus
    Front Side Bus Speed:          4x 133MHz (532MHz data rate)
    Maximum FSB Speed / Max Memory:4x 200MHz / 2x 200MHz
    Width:                         64-bit
    IO Queue Depth:                12 request(s)

  < Chipset 1 Hub Interface >
    Type:                          Hub-Interface
    Version:                       1.50
    Number of Ports:               3
    Width:                         8-bit
    Full Duplex:                   Yes
    Multiplier:                    2/1x

  < Logical/Chipset 1 Memory Banks >
    Bank 0:                        256MB DDR-SDRAM 2.5-3-3-7 1CMD
    Bank 1:                        256MB DDR-SDRAM 2.5-3-3-7 1CMD
    Channels:                      1
    Speed:                         2x 166MHz (332MHz data rate)
    Multiplier:                    5/4x
    Width:                         64-bit
    Refresh Rate:                  7.80µs
    Performance Acceleration Techn:Yes
    Power Save Mode:               No
    Fixed Hole Present:            No

  < APIC 1 >
    Version:                       2.00
    Multiplier:                    1/2x
    Maximum Interrupts:            24
    IRQ Handler Engaged:           Yes
    Enhanced Support:              Yes

  < Memory Module 1 >
    Manufacturer:                  Wintec
    Type:                          512MB DDR-SDRAM
    Technology:                    16x(32Mx8)
    Speed:                         PC2700U 2.5-3-3-7
    Date of Manufacture:           Wednesday, October 22, 2003
    Set Timing @ 167MHz:           2.5-3-3-7
    Set Timing @ 133MHz:           2.0-2-2-6

  < Environment Monitor 1 >
    Model:                         Winbond W83627(T)HF ISA
    Version:                       9.00
    Mainboard Specific Support:    No

  < Temperature Sensor(s) >
    Board Temperature:             24.0°C / 75.2°F td
    CPU Temperature:               29.0°C / 84.2°F
    Power / Aux Temperature:       14.0°C / 57.2°F

  < Cooling Device(s) >
    Auto Fan Speed Control:        No
    Chassis Fan Speed:             3184rpm
    CPU Fan Speed:                 2519rpm

  < Voltage Sensor(s) >
    CPU Voltage:                   2.80V
    Aux Voltage:                   1.06V
    +3.3V Voltage:                 3.31V
    +5V Voltage:                   5.03V
    +12V Voltage:                  15.50V
    -12V Voltage:                  -9.65V
    -5V Voltage:                   -7.71V
    Standby Voltage:               4.48V
    Battery Voltage:               3.07V

  < PCI Bus(es) on Hub 1 >
    Version:                       2.10
    Number of Bridges:             1
    PCI Bus 0:                     PCI (1/1x PCIClk)
    PCI Bus 1:                     PCI (1/1x PCIClk)

  < LPC Hub Controller 1 >
    Model:                         Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC 
                                   Interface Bridge
    ACPI Power Management Enabled: Yes
    Delayed Transaction Enabled:   Yes

  < LPC Hub Controller 2 >
    Model:                         Micro-Star International Co Ltd (MSI) 82801EB/
                                   ER (ICH5/ICH5R) SMBus Controller

  < USB Controller 1 >
    Model:                         Micro-Star International Co Ltd (MSI) 82801EB/
                                   ER (ICH5/ICH5R) USB UHCI Controller #1
    Version:                       1.10
    Interface:                     UHCI
    Channels:                      2
    Speed:                         48MHz
    Supported Speed(s):            Low (1.5Mbps) Full (12Mbps) 
    Legacy Emulation Enabled:      No

  < USB Controller 2 >
    Model:                         Micro-Star International Co Ltd (MSI) 82801EB/
                                   ER (ICH5/ICH5R) USB UHCI Controller #2
    Version:                       1.10
    Interface:                     UHCI
    Channels:                      2
    Speed:                         48MHz
    Supported Speed(s):            Low (1.5Mbps) Full (12Mbps) 
    Legacy Emulation Enabled:      No

  < USB Controller 3 >
    Model:                         Micro-Star International Co Ltd (MSI) 82801EB/
                                   ER (ICH5/ICH5R) USB UHCI Controller #3
    Version:                       1.10
    Interface:                     UHCI
    Channels:                      2
    Speed:                         48MHz
    Supported Speed(s):            Low (1.5Mbps) Full (12Mbps) 
    Legacy Emulation Enabled:      No

  < USB Controller 4 >
    Model:                         Micro-Star International Co Ltd (MSI) 82801EB/
                                   ER (ICH5/ICH5R) USB UHCI Controller #4
    Version:                       1.10
    Interface:                     UHCI
    Channels:                      2
    Speed:                         48MHz
    Supported Speed(s):            Low (1.5Mbps) Full (12Mbps) 
    Legacy Emulation Enabled:      No

  < USB Controller 5 >
    Model:                         Micro-Star International Co Ltd (MSI) 82801EB/
                                   ER (ICH5/ICH5R) USB 2.0 EHCI Controller
    Version:                       2.00
    Specification:                 1.00
    Interface:                     EHCI
    Channels:                      8
    Companion Controllers:         4
    Supported Speed(s):            Low (1.5Mbps) Full (12Mbps) High (480Mbps) 
    Addressing Support:            64-bit
    Legacy Emulation Enabled:      No

  < System SMBus Controller 1 >
    Model:                         Intel 801xx/63xx SMBus
    Version:                       0.02
    Specification:                 2.00
    Advanced TCO Mode Enabled:     No
    Slave Device Enabled:          Yes
    PEC Support:                   No
    Speed:                         100kHz

  < Expansion Slot(s) >
    PCI0 (1h):                     PCI 32-bit +5V PME Full-Length Used
    PCI1 (2h):                     PCI 32-bit +5V PME Full-Length Available 
                                   (Micro-Star International Co Ltd (MSI) 82865G 
                                   Integrated Graphics Device)
    PCI2 (3h):                     PCI 32-bit +5V PME Full-Length Available
    AGP (8h):                      AGP 32-bit +5V Full-Length Available

  < Port Connector >
    PRIMARY IDE:                   None - ATA / None
    SECONDARY IDE:                 None - ATA / None
    FDD:                           8251 FIFO - Floppy Disk / None
    COM1:                          Serial Port 16450 - 9 Pin Dual Inline / DB-9 
                                   pin male
    COM2:                          Serial Port 16450 - 9 Pin Dual Inline / DB-9 
                                   pin male
    LPT1:                          Parallel Port ECP/EPP - DB-25 pin female / DB-
                                   25 pin female
    Keyboard:                      Keyboard - PS/2 / PS/2
    PS/2 Mouse:                    Mouse - PS/2 / PS/2
    USB0:                          USB - None / None
    USB1:                          USB - None / None


<<< CPU & BIOS Information >>>
--------------------------------------------------------------------------------

<< CPU 1 [Processor 0, Core 0, Thread 0] >>
  < Processor >
    Model:                         Intel(R) Pentium(R) 4 CPU 2.66GHz
    Speed:                         2.67GHz
    Performance Rating:            PR2934 (estimated)
    Cores per Processor:           1 Unit(s)
    Threads per Core:              1 Unit(s)
    Package:                       FC µPGA478
    Rated Speed/FSB:               2660MHz / 4x 133MHz
    Multiplier:                    20/1x
    Minimum/Maximum Multiplier:    0/1x / 20/1x
    Generation:                    G8
    Name:                          P4N (Northwood) Pentium 4C 130nm 1.6-3.4GHz 
                                   1.475-1.575V
    Revision/Stepping:             2 / 7 (9)
    Stepping Mask:                 C1
    Microcode:                     MU0F2737
    Core Voltage Rating:           1.550V
    Maximum Physical / Virtual Add:36-bit / 32-bit
    Native Page Size:              4kB

  < Co-Processor (FPU) >
    Type:                          Built-in
    Revision/Stepping:             2 / 7 (9)

  < Processor Cache(s) >
    Internal Data Cache:           8kB Synchronous, Write-Thru, 4-way set, 64 
                                   byte line size
    Internal Trace Cache:          12kB Synchronous, Write-Thru, 8-way set, 64 
                                   byte line size
    L2 On-board Cache:             512kB ECC Synchronous, ATC, 8-way set, 64 
                                   byte line size, 2 lines per sector
    L2 Cache Multiplier:           1/1x  (2667MHz)

  < Upgradeability >
    Socket/Slot:                   Socket 478
    Upgrade Interface:             ZIF Socket
    Supported Speed(s):            3.07GHz+

  < Environment Monitor 1 >
    Model:                         Winbond W83627(T)HF ISA
    Version:                       9.00
    Mainboard Specific Support:    No

  < Power Rating(s) >
    CPU Core Power:                222W (estimated)
    CPU Cooling System Thermal Res:0.01°C/W (estimated)

  < Sensors >
    CPU Temperature:               29.0°C / 84.2°F
    Auto Fan Speed Control:        No
    CPU Fan Speed:                 2482rpm
    CPU Voltage:                   2.74V

  < Features >
    FPU - Co-Processor Built-in:   Yes
    VME - Virtual Mode Extensions: Yes
    DE - Debugging Extension:      Yes
    PSE - Page Size Extension:     Yes
    TSC - Time Stamp Counter:      Yes
    MSR - Model Specific Registers:Yes
    PAE - Physical Address Extensi:Yes
    MCE - Machine Check Exception: Yes
    CX8 - Compare & Exchange 8-byt:Yes
    APIC - Local APIC Built-in:    Yes
    SEP - Fast System Call:        Yes
    MTRR - Memory Type Range Regis:Yes
    PGE - Page Global Enable:      Yes
    MCA - Machine Check Architectu:Yes
    PAT - Page Attribute Table:    Yes
    PSE36 - 36-bit Page Size Exten:Yes
    PSN - Unique Serial Number:    No
    CLF - Cache Line Flush Support:Yes
    DS - Debug Trace & EMON Store: Yes
    ACPI - Software Clock Control: Yes
    (W)MMX Technology:             Yes
    FXSR - Fast Float Save & Resto:Yes
    SSE Technology:                Yes
    SSE2 Technology:               Yes
    SS - Self Snoop:               Yes
    HTT - Hyper-Threading Technolo:No
    TM - Thermal Monitor:          Yes
    PBE - Pending Break Enable:    Yes
    IA64 Technology:               No
    SSE3 Technology:               No
    MON - Monitor/MWait:           No
    DSCPL - CPL qualified Debug St:No
    VMX - Virtual Machine eXtensio:No
    EST - Enhanced SpeedStep Techn:No
    TM2 - Thermal Monitor 2:       No
    SSE4 Technology:               No
    CID - Context ID:              Yes
    CX16 - Compare & Exchange 16-b:No
    xTPR - Send Task Priority Mess:Yes
    DAZ - Denormals Are Zero:      Yes

  < Advanced Settings >
    Data Error Checking:           No
    Fast Strings:                  Yes
    x86 FPU Compatibility Mode:    No
    Prefetch Queue:                Yes
    Branch Trace Storage:          Yes
    Data Cache Active Mode:        Yes
    IO Queue Depth:                12 request(s)
    TM - Thermal Monitor:          Yes

  < Machine Check Architecture Settings >
    Number of Reporting Banks:     4 bank(s)
    Extended Machine Check Support:Yes
    Number of Extended Reporting B:12 bank(s)

  < PAT Settings >
    PAT 0:                         WB
    PAT 1:                         WC
    PAT 2:                         UC-
    PAT 3:                         UC
    PAT 4:                         WB
    PAT 5:                         WC
    PAT 6:                         UC-
    PAT 7:                         UC


<< System BIOS >>
  < General Information >
    Manufacturer:                  Phoenix Technologies, LTD
    Version:                       6.00 PG
    Date of Manufacture:           Thursday, December 23, 2004
    Plug & Play Version:           1.00
    SMBIOS/DMI Version:            2.20
    (EE)PROM Size:                 512kB

  < General Capabilities >
    Can be Updated/Flashed:        Yes
    Can be Shadowed:               Yes
    Is Socketed:                   Yes
    Supports Plug & Play:          Yes
    Supports ESCD:                 No
    Supports Enhanced Disk Drive:  Yes
    NEC PC-98 Spec Compatible:     No

  < Power Management Features >
    Supports APM:                  Yes
    Supports ACPI:                 Yes
    Supports Smart Battery:        No

  < Boot Features >
    Supports Selective Booting:    Yes
    Supports CD/DVD Boot:          Yes
    Supports PCMCIA/CardBus Boot:  No
    Supports LS-120 Boot:          Yes
    Supports ZIP Boot:             Yes
    Supports i2o Boot:             No
    Supports FireWire/1394 Boot:   No
```

---

### Post by erniewinner on 2006-04-16
hotplug subsystem? have you got anything plugged in your usb ports? if you have a lot of excess hardware try and remove it and add it back as things work... or disable stuff in the bios. i'm basically thinking the install doesn't like some hardware device... that would be my first step. :-k

---

### Post by indytim on 2006-04-16
I did notice that you are pretty light on HD (6G).  Looks like you've already got Win2000 installed on the drive. You might be max'd out on storage for Ubuntu to finish the install.  I'll defer to more experienced members of the community for additional analysis.

IndyTim

---

### Post by htinn on 2006-04-16
Those hard drives are old enough that it could be a case of waiting for retries on bad sectors. I would definitely do a low-level scan/format (if you haven't done one within the past year or so).

---

### Post by slipk487 on 2006-04-16
i have had ubuntu on it before and when i tryed to install it it froze up im not trying to duel boot i just want ubuntu and if frezzes up at the hot plug subsystem and i just have a mouse and a 4 port hub with nothing it it but ill unplug that and try it and i dont know how to do a low-level scan/format

---

### Post by slipk487 on 2006-04-16
is there anyother thing that i could do to get past the hotplug subsystem

---

### Post by codejunkie on 2006-04-16
[QUOTE=slipk487]is there anyother thing that i could do to get past the hotplug subsystem[/QUOTE]
i had problems with my msi motherboard doing the same thing, with more than one video card installed i also had to boot with ```
linux acpi=off
``` to keep it from rebooting  before the install completed, if you have more than one video card installed remove one and see if it finishes the install correctly, then add the other card. also if the motherboard has onboard video make sure it is completely disabled in the bios.

---

### Post by slipk487 on 2006-04-16
ya in my bios there is a way to disable the onboard graphic card and it is

---

### Post by codejunkie on 2006-04-16
[QUOTE=slipk487]ya in my bios there is a way to disable the onboard graphic card and it is[/QUOTE]
what kind of video card do you have agp or pci? i couldn't get my pci graphics card to work in mine, i had to use either onboard video or an agp card. you can also try pressing ctrl+c when you see *starting hotplug subsystem* to skip it, it might boot that way.

---

### Post by slipk487 on 2006-04-16
i tried the live cd with
```
live acpi=off
```
and it still froze at the hotplug subsystem

its a ATI Radeon 9250 PCI and i had it working fine on my old comp

---

### Post by codejunkie on 2006-04-16
[QUOTE=slipk487]i tried the live cd with
```
live acpi=off
```
and it still froze at the hotplug subsystem

its a ATI Radeon 9250 PCI and i had it working fine on my old comp[/QUOTE]
i'd say your in the same situation i was in, by removing the ati card from the system, and enabling the onboard video you should be able to finish the install and i doubt you'll have the starting hotplug subsystem freeze using the onboard video, but i never could get mine to work using a pci video card but it works fine using an agp card or the onboard video.

---

### Post by slipk487 on 2006-04-16
ill try that but before i couldnt use the ati at first but i could get past the hotplug subsystem but i havent even gotten ubuntu to work on this motherboard

---

### Post by slipk487 on 2006-04-16
i got it to work after enabling the intergrated but y would it frezze up when its disabled it didnt work so y would it do that and im getting ready to install ubuntu cuz i started it on the live cd

---

### Post by codejunkie on 2006-04-17
[QUOTE=slipk487]i got it to work after enabling the intergrated but y would it frezze up when its disabled it didnt work so y would it do that and im getting ready to install ubuntu cuz i started it on the live cd[/QUOTE]
i really have no idea why it would do that, is it also working with the ati card now.

---

### Post by slipk487 on 2006-04-17
dont know i just got it up and got to find the resticred modules for it and the ati control panel and then i need to reconfigure it and then ill let u know if i get it to work

---

### Post by slipk487 on 2006-04-17
i had to reinstall cuz there were broken pakeges and smp couldnt fix them and now i cant even get it to install

---

### Post by erniewinner on 2006-04-17
while i'm no expert... i'm sure hotplug system is not liking your usb/ mouse combo and any other usb devices you are using unplug that and give it a try... use a different/ ps2 mouse. i had a feeling you were using usb devices when "hotplug" got mentioned the first time and it shouldn't take a minute. (easier than opening the case!) :rolleyes:

---

### Post by coolclassic on 2006-04-17
How many usb ports do you have. Have you added extra i.e hub. if you have I would sudjest taking your ports down to original number for your board.

---

### Post by slipk487 on 2006-04-17
there is 4 on the back panel plus2 on the front panel but they dont work and i already took out the hub but the problem got fixed after i enabled the onboard video card and right now im trying to get ubuntu to install but i cant get it so and when i do get it to install it missing a bunch of stuff and when i install it in the spm it says it is already installed and configured and i dont know y its doing it and im trying to get it installed for the 4 time right now

---

### Post by slipk487 on 2006-04-17
[here is the motherboard that i have]("http://www.msicomputer.com/product/p_spec.asp?model=865GVM2-LS&class=mb")

---

### Post by htinn on 2006-04-17
You know, if you really want help, you're going to have to describe in detail what the *problem* is. We can't read your mind.

---

### Post by slipk487 on 2006-04-17
i can get it past the hotplug subsystem but during the installation the fails to install anything past the libaudio2 including it and sometimes it goes to the gui login screen and sometimes it doesnt but nothing works right so what could be done about this because ive tried it like 3 times and it doenst work right any of the times ive tried

---

### Post by slipk487 on 2006-04-17
i finally got everything working and in the process of getting my graphics card to work again and thxs for the help

---

### Post by slipk487 on 2006-04-18
never mind im getting random shutdowns and at times the the comp will just frezze and make a weird sound from the speakers and the screen gets all jacked up and i dont know y it is doing it and im going to try and reinstall it again

---

### Post by htinn on 2006-04-18
Something to keep in mind is that some motherboards tend to have a high failure rate (which can show up in the first week or two of use).

---

### Post by slipk487 on 2006-04-18
i got windows to work fine in it it just has problems with linux

---

