---
title: "Asus p8h67-m pro memory cache l3 disabled"
date: 2011-08-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by fernoppix on 2011-08-04
I've recently bought this mainboard with an intel  i5 2500, everything works but when I check the hardware I see that  memory cache L3 is disabled. I have an Ubuntu 11.04 and I test it with  lshw and dmidecode commands. This is the output of dmidecode:
Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1-Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 256 KB
    Maximum Size: 256 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2-Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 1024 KB
    Maximum Size: 1024 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L3-Cache
    Configuration: Disabled, Not Socketed, Level 3
    Operational Mode: Unknown
    Location: Internal
    Installed Size: 6144 KB
    Maximum Size: 6144 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: None
    System Type: Unified
    Associativity: Other


I've  contacted with the store when I've bought the mainboard and they say me  that's a Linux problem , not hardware. They say me that I try to  install a Windows for check the system. I think Linux it isn't the  problem because I've tryed with other distros, memtest86... without  solution. I don't find any options in BIOS for enabling/disabling memory  cache.

Thanks and sorry for my english

---

### Post by Smika on 2013-01-18
Same issue here. Do you have the solution?

---

