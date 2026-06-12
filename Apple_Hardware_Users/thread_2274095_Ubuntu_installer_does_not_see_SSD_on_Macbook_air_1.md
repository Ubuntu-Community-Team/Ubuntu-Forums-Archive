---
title: "Ubuntu installer does not see SSD on Macbook air 11'' early 2015"
date: 2015-04-17
forum: Apple Hardware Users
---

### Post by JGrossholtz on 2015-04-17
[FONT=arial]Hello all,[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I bought the early 2015 11 inch macbook air with the folowing configuration :[/FONT]
[FONT=arial]- Broadwell core i7[/FONT]
[FONT=arial]- 8Gb RAM[/FONT]
[FONT=arial]- 128 Gb SSD[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I reduced the OS X partition to 50Gb and created an extFat partition I planed to format later during the ubuntu install process.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Then I installed rEFInd (after I tried rEFIt with no success). After a restart I was able to select OS X and to detect bootable usb sticks.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I prepared my USB stick on another computer and dd various Ubuntu images and Debian (Jessie). With Ubuntu 14.04 there where many texts missing in the install interface. [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]So I tried with ubuntu-mate 15.04 and the install process is stopped early when it check disk, connectivity etc... With debian the problem is more clear, the partitioning tool cannot see the SSD.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Here is the dmesg output :[/FONT]
```


[COLOR=#000000][FONT=arial]ubuntu-mate@ubuntu-mate:~$ dmesg [/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Initializing cgroup subsys cpuset[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Initializing cgroup subsys cpu[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Initializing cgroup subsys cpuacct[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Linux version 3.19.0-10-generic (buildd@brownie) (gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu10) ) #10-Ubuntu SMP Mon Mar 23 16:25:20 UTC 2015 (Ubuntu 3.19.0-10.10-generic 3.19.2)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu-[/FONT][/COLOR][COLOR=#000000][FONT=arial]mate.seed boot=casper quiet splash ---[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] KERNEL supported cpus:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   Intel GenuineIntel[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   AMD AuthenticAMD[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   Centaur CentaurHauls[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] e820: BIOS-provided physical RAM map:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x0000000000000000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000000057fff] usable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x0000000000058000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000000058fff] reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x0000000000059000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000000009ffff] usable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x00000000000a0000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000000bffff] reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x0000000000100000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008ad00fff] usable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x000000008ad01000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008ad48fff] ACPI NVS[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x000000008ad49000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008ad60fff] usable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x000000008ad61000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008ad8efff] ACPI data[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x000000008ad8f000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008ae39fff] usable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x000000008ae3a000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008ae8efff] reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x000000008ae8f000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008aecbfff] usable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x000000008aecc000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008aefefff] type 20[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x000000008aeff000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008afa9fff] usable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x000000008afaa000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008afdefff] reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x000000008afdf000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008affffff] usable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x000000008b000000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008fffffff] reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x00000000e00f8000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000e00f8fff] reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x00000000fed1c000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000fed1ffff] reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x00000000ffd70000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000ffd9ffff] reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BIOS-e820: [mem 0x0000000100000000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000026effffff] usable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] NX (Execute Disable) protection: active[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: EFI v1.10 by Apple[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi:  ACPI=0x8ad8e000  ACPI 2.0=0x8ad8e014  SMBIOS=0x8afae000 [/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem00: [Conventional Memory|attr=[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x080000000000000f] range=[0x0000000000000000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000000058000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem01: [Reserved           |attr=0x080000000000000f] range=[0x0000000000058000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000000059000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem02: [Conventional Memory|attr=[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x080000000000000f] range=[0x0000000000059000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000000a0000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem03: [Loader Data        |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000000100000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000014e5000) (19MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem04: [Conventional Memory|   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000014e5000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000002000000) (11MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem05: [Loader Data        |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000002000000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000033e5000) (19MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem06: [Conventional Memory|   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000033e5000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000003540e000) (800MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem07: [Loader Data        |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000003540e000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000369ff000) (21MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem08: [Conventional Memory|   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000369ff000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000586e2000) (540MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem09: [Loader Data        |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000586e2000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000075f12000) (472MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem10: [Loader Code        |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000075f12000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000076005000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem11: [Conventional Memory|   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000076005000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000760f6000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem12: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000760f6000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000076b78000) (10MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem13: [Loader Code        |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000076b78000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000076baa000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem14: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000076baa000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000076bb6000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem15: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000076bb6000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000076bc0000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem16: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000076bc0000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000785ba000) (25MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem17: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000785ba000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000785c2000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem18: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000785c2000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000785d1000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem19: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000785d1000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000785d3000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem20: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000785d3000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007860f000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem21: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007860f000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078623000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem22: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078623000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078628000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem23: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078628000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078629000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem24: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078629000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078632000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem25: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078632000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007863a000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem26: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007863a000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007863c000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem27: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007863c000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078644000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem28: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078644000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007864c000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem29: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007864c000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007864f000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem30: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007864f000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078650000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem31: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078650000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078652000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem32: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078652000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078653000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem33: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078653000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078659000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem34: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078659000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078665000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem35: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078665000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078666000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem36: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078666000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007867d000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem37: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007867d000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007867e000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem38: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007867e000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000786b3000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem39: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000786b3000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000786b6000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem40: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000786b6000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000786b7000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem41: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000786b7000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000786bf000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem42: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000786bf000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007875e000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem43: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007875e000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078956000) (1MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem44: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078956000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007895a000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem45: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007895a000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007896d000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem46: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007896d000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078996000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem47: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078996000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007899a000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem48: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007899a000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007899b000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem49: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007899b000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789a1000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem50: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789a1000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789a5000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem51: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789a5000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789ac000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem52: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789ac000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789ad000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem53: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789ad000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789b4000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem54: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789b4000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789b6000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem55: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789b6000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789bb000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem56: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789bb000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789bf000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem57: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789bf000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789e8000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem58: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789e8000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789ed000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem59: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789ed000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789f7000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem60: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789f7000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789f8000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem61: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789f8000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789f9000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem62: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789f9000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789fb000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem63: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789fb000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000789ff000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem64: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000789ff000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a03000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem65: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a03000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a10000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem66: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a10000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a12000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem67: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a12000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a15000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem68: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a15000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a18000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem69: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a18000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a34000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem70: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a34000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a39000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem71: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a39000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a40000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem72: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a40000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a43000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem73: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a43000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a46000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem74: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a46000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a47000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem75: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a47000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a52000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem76: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a52000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a54000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem77: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a54000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a58000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem78: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a58000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a59000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem79: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a59000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a6f000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem80: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a6f000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a71000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem81: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a71000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a72000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem82: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a72000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a74000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem83: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a74000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a82000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem84: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a82000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a88000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem85: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a88000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a99000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem86: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a99000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a9b000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem87: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a9b000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078a9f000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem88: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078a9f000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078aa4000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem89: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078aa4000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078aa6000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem90: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078aa6000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078aa7000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem91: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078aa7000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078ab3000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem92: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078ab3000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078ab4000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem93: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078ab4000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078ab8000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem94: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078ab8000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078aba000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem95: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078aba000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078ac4000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem96: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078ac4000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078ac6000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem97: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078ac6000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078aca000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem98: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078aca000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078acc000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem99: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078acc000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078acf000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem100: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078acf000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078ad6000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem101: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078ad6000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078ad8000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem102: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078ad8000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078ad9000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem103: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078ad9000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078adf000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem104: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078adf000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078ae0000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem105: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078ae0000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078ae4000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem106: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078ae4000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078af4000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem107: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078af4000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078afa000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem108: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078afa000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078afd000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem109: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078afd000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b01000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem110: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b01000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b04000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem111: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b04000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b08000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem112: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b08000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b0a000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem113: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b0a000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b10000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem114: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b10000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b11000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem115: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b11000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b37000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem116: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b37000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b39000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem117: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b39000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b3d000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem118: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b3d000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b42000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem119: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b42000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b51000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem120: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b51000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b53000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem121: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b53000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b55000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem122: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b55000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b56000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem123: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b56000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b57000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem124: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b57000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b59000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem125: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b59000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b5b000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem126: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b5b000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b5c000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem127: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b5c000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000078b5e000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem128: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000078b5e000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079325000) (7MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem129: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079325000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079328000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem130: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079328000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007932a000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem131: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007932a000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007932d000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem132: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007932d000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007932e000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem133: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007932e000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079345000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem134: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079345000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079346000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem135: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079346000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079360000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem136: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079360000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079364000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem137: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079364000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079365000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem138: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079365000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007936c000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem139: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007936c000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007936f000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem140: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007936f000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079370000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem141: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079370000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007937f000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem142: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007937f000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079380000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem143: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079380000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079381000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem144: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079381000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079384000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem145: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079384000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079385000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem146: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079385000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079386000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem147: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079386000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007938c000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem148: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007938c000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007938d000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem149: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007938d000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079393000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem150: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079393000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079398000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem151: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079398000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079399000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem152: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079399000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007939b000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem153: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007939b000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007939e000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem154: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007939e000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793a2000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem155: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793a2000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793a3000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem156: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793a3000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793a5000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem157: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793a5000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793a9000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem158: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793a9000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793ab000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem159: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793ab000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793af000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem160: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793af000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793b7000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem161: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793b7000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793b8000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem162: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793b8000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793b9000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem163: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793b9000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793ba000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem164: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793ba000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793bc000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem165: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793bc000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793c0000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem166: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793c0000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793c3000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem167: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793c3000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793c4000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem168: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793c4000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793c6000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem169: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793c6000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793cc000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem170: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793cc000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793d4000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem171: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793d4000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793d6000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem172: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793d6000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793d7000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem173: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793d7000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793dd000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem174: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793dd000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793df000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem175: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793df000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793e0000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem176: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793e0000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793e3000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem177: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793e3000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793e4000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem178: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793e4000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000793fd000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem179: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000793fd000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079410000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem180: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079410000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079455000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem181: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079455000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079467000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem182: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079467000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007946c000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem183: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007946c000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079470000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem184: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079470000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079473000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem185: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079473000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079476000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem186: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079476000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007947f000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem187: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007947f000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079480000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem188: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079480000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079481000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem189: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079481000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079483000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem190: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079483000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079484000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem191: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079484000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079485000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem192: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079485000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079497000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem193: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079497000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794a8000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem194: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794a8000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794b0000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem195: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794b0000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794b1000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem196: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794b1000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794b3000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem197: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794b3000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794b8000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem198: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794b8000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794c4000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem199: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794c4000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794c5000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem200: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794c5000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794c6000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem201: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794c6000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794c7000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem202: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794c7000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794ca000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem203: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794ca000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794cb000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem204: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794cb000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794cc000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem205: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794cc000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794d4000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem206: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794d4000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794d6000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem207: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794d6000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794da000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem208: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794da000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794df000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem209: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794df000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794e4000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem210: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794e4000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794e8000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem211: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794e8000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794ea000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem212: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794ea000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794ec000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem213: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794ec000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000794ee000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem214: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x00000000794ee000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079546000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem215: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079546000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079547000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem216: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079547000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079548000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem217: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079548000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007954a000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem218: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007954a000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007954b000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem219: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007954b000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007954c000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem220: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007954c000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007954e000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem221: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007954e000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079550000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem222: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079550000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079552000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem223: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079552000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000079553000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem224: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000079553000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007958a000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem225: [Boot Code          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007958a000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000007958b000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem226: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000007958b000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008ace9000) (279MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem227: [Conventional Memory|   |  |  |  |   |WB|WT|WC|UC] range=[0x000000008ace9000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008ad01000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem228: [ACPI Memory NVS    |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000008ad01000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008ad49000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem229: [Conventional Memory|   |  |  |  |   |WB|WT|WC|UC] range=[0x000000008ad49000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008ad61000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem230: [ACPI Reclaim Memory|   |  |  |  |   |WB|WT|WC|UC] range=[0x000000008ad61000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008ad8f000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem231: [Conventional Memory|   |  |  |  |   |WB|WT|WC|UC] range=[0x000000008ad8f000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008ae3a000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem232: [Runtime Data       |RUN|  |  |  |   |WB|WT|WC|UC] range=[0x000000008ae3a000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008ae8f000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem233: [Conventional Memory|   |  |  |  |   |WB|WT|WC|UC] range=[0x000000008ae8f000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008aecc000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem234: [Runtime Code       |RUN|  |  |  |   |WB|WT|WC|UC] range=[0x000000008aecc000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008aeff000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem235: [Conventional Memory|   |  |  |  |   |WB|WT|WC|UC] range=[0x000000008aeff000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008af9d000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem236: [Loader Data        |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000008af9d000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008afaa000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem237: [Reserved           |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000008afaa000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008afdf000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem238: [Boot Data          |   |  |  |  |   |WB|WT|WC|UC] range=[0x000000008afdf000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000008b000000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem239: [Conventional Memory|   |  |  |  |   |WB|WT|WC|UC] range=[0x0000000100000000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000026f000000) (5872MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem240: [Reserved           |RUN|  |  |  |   |  |  |  |  ] range=[0x00000000000a0000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000000c0000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem241: [Reserved           |RUN|  |  |  |   |  |  |  |  ] range=[0x000000008b000000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x0000000090000000) (80MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem242: [Memory Mapped I/O  |RUN|  |  |  |   |  |  |  |UC] range=[0x00000000e00f8000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000e00f9000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem243: [Memory Mapped I/O  |RUN|  |  |  |   |  |  |  |UC] range=[0x00000000fed1c000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000fed20000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] efi: mem244: [Memory Mapped I/O  |RUN|  |  |  |   |  |  |  |UC] range=[0x00000000ffd70000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x00000000ffda0000) (0MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] SMBIOS 2.7 present.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] DMI: Apple Inc. MacBookAir7,1/Mac-[/FONT][/COLOR][COLOR=#000000][FONT=arial]9F18E312C5C2BF0B, BIOS MBA71.88Z.0166.B00.1502131457 02/13/2015[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] AGP: No AGP bridge found[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] e820: last_pfn = 0x26f000 max_arch_pfn = 0x400000000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] MTRR default type: write-back[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] MTRR fixed ranges enabled:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   00000-9FFFF write-back[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   A0000-BFFFF uncachable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   C0000-DFFFF write-protect[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   E0000-FFFFF uncachable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] MTRR variable ranges enabled:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   0 base 00C0000000 mask 7FC0000000 uncachable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   1 base 00A0000000 mask 7FE0000000 uncachable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   2 base 0090000000 mask 7FF0000000 uncachable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   3 base 008C000000 mask 7FFC000000 uncachable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   4 base 008B000000 mask 7FFF000000 uncachable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   5 disabled[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   6 disabled[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   7 disabled[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   8 disabled[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   9 disabled[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  [/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] e820: last_pfn = 0x8b000 max_arch_pfn = 0x400000000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Scanning 1 areas for low memory corruption[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Using GB pages for direct mapping[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x00000000-0x000fffff] page 4k[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BRK [0x02fe5000, 0x02fe5fff] PGTABLE[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BRK [0x02fe6000, 0x02fe6fff] PGTABLE[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BRK [0x02fe7000, 0x02fe7fff] PGTABLE[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] init_memory_mapping: [mem 0x26ee00000-0x26effffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x26ee00000-0x26effffff] page 2M[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BRK [0x02fe8000, 0x02fe8fff] PGTABLE[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] init_memory_mapping: [mem 0x260000000-0x26edfffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x260000000-0x26edfffff] page 2M[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] init_memory_mapping: [mem 0x240000000-0x25fffffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x240000000-0x25fffffff] page 2M[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] init_memory_mapping: [mem 0x00100000-0x8ad00fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x00100000-0x001fffff] page 4k[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x00200000-0x3fffffff] page 2M[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x40000000-0x7fffffff] page 1G[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x80000000-0x8abfffff] page 2M[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x8ac00000-0x8ad00fff] page 4k[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] init_memory_mapping: [mem 0x8ad49000-0x8ad60fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x8ad49000-0x8ad60fff] page 4k[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] init_memory_mapping: [mem 0x8ad8f000-0x8ae39fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x8ad8f000-0x8ae39fff] page 4k[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] BRK [0x02fe9000, 0x02fe9fff] PGTABLE[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] init_memory_mapping: [mem 0x8ae8f000-0x8aecbfff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x8ae8f000-0x8aecbfff] page 4k[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] init_memory_mapping: [mem 0x8aeff000-0x8afa9fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x8aeff000-0x8afa9fff] page 4k[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] init_memory_mapping: [mem 0x8afdf000-0x8affffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x8afdf000-0x8affffff] page 4k[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] init_memory_mapping: [mem 0x100000000-0x23fffffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [mem 0x100000000-0x23fffffff] page 1G[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] RAMDISK: [mem 0x3540e000-0x369fefff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: Early table checksum verification disabled[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: RSDP 0x000000008AD8E014 000024 (v02 APPLE )[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: XSDT 0x000000008AD8E1C0 00009C (v01 APPLE  Apple00  00000000      01000013)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: FACP 0x000000008AD8C000 0000F4 (v05 APPLE  Apple00  00000000 Loki 0000005F)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: DSDT 0x000000008AD7E000 008892 (v03 APPLE  MacBookA 00070001 INTL 20140424)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: FACS 0x000000008AD06000 000040[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: HPET 0x000000008AD8B000 000038 (v01 APPLE  Apple00  00000001 Loki 0000005F)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: APIC 0x000000008AD8A000 0000BC (v02 APPLE  Apple00  00000001 Loki 0000005F)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: SBST 0x000000008AD88000 000030 (v01 APPLE  Apple00  00000001 Loki 0000005F)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: ECDT 0x000000008AD87000 000053 (v01 APPLE  Apple00  00000001 Loki 0000005F)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: SSDT 0x000000008AD7D000 00010B (v01 APPLE  SataAhci 00001000 INTL 20140424)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: SSDT 0x000000008AD7C000 000024 (v01 APPLE  SmcDppt  00001000 INTL 20140424)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: SSDT 0x000000008AD7B000 000032 (v01 APPLE  SsdtS3   00001000 INTL 20140424)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: SSDT 0x000000008AD78000 002B26 (v01 APPLE  PcieTbt  00001000 INTL 20140424)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: SSDT 0x000000008AD6B000 0000B8 (v01 APPLE  Sdxc     00001000 INTL 20140424)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: SSDT 0x000000008AD6A000 000A92 (v01 APPLE  Xhci     00001000 INTL 20140424)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: SSDT 0x000000008AD63000 0005F7 (v01 PmRef  Cpu0Ist  00003000 INTL 20140424)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: SSDT 0x000000008AD62000 000C17 (v01 CpuRef CpuSsdt  00003000 INTL 20140424)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: MCFG 0x000000008AD89000 00003C (v01 APPLE  Apple00  00000001 Loki 0000005F)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: DMAR 0x000000008AD61000 000088 (v01 APPLE  BDW      00000001 INTL 00000001)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: Local APIC address 0xfee00000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] No NUMA configuration found[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Faking a node at [mem 0x0000000000000000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]0x000000026effffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] NODE_DATA(0) allocated [mem 0x26eff9000-0x26effdfff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]  [ffffea0000000000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]ffffea0009bfffff] PMD -> [ffff880266600000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]ffff88026e5fffff] on node 0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Zone ranges:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   DMA      [mem 0x00001000-0x00ffffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   DMA32    [mem 0x01000000-0xffffffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   Normal   [mem 0x100000000-0x26effffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Movable zone start for each node[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Early memory node ranges[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   node   0: [mem 0x00001000-0x00057fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   node   0: [mem 0x00059000-0x0009ffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   node   0: [mem 0x00100000-0x8ad00fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   node   0: [mem 0x8ad49000-0x8ad60fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   node   0: [mem 0x8ad8f000-0x8ae39fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   node   0: [mem 0x8ae8f000-0x8aecbfff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   node   0: [mem 0x8aeff000-0x8afa9fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   node   0: [mem 0x8afdf000-0x8affffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   node   0: [mem 0x100000000-0x26effffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Initmem setup node 0 [mem 0x00001000-0x26effffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] On node 0 totalpages: 2072171[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   DMA zone: 64 pages used for memmap[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   DMA zone: 25 pages reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   DMA zone: 3998 pages, LIFO batch:0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   DMA32 zone: 8828 pages used for memmap[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   DMA32 zone: 564941 pages, LIFO batch:31[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   Normal zone: 23488 pages used for memmap[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]   Normal zone: 1503232 pages, LIFO batch:31[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Reserving Intel graphics stolen memory at 0x8c000000-0x8fffffff[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: PM-Timer IO Port: 0x1808[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: Local APIC address 0xfee00000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0xff] disabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0xff] disabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0xff] disabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0xff] disabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: IRQ0 used by override.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: IRQ9 used by override.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Using ACPI (MADT) for SMP configuration information[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000bffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0x000c0000-0x000fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0x8ad01000-0x8ad48fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0x8ad61000-0x8ad8efff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0x8ae3a000-0x8ae8efff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0x8aecc000-0x8aefefff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0x8afaa000-0x8afdefff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0x8b000000-0x8fffffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0x90000000-0xe00f7fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0xe00f8000-0xe00f8fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0xe00f9000-0xfed1bfff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xffd6ffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0xffd70000-0xffd9ffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PM: Registered nosave memory: [mem 0xffda0000-0xffffffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] e820: [mem 0x90000000-0xe00f7fff] available for PCI devices[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Booting paravirtualized kernel on bare hardware[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88026ec00000 s87040 r8192 d31744 u262144[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] pcpu-alloc: s87040 r8192 d31744 u262144 alloc=1*2097152[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 [/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2039766[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Policy zone: Normal[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu-[/FONT][/COLOR][COLOR=#000000][FONT=arial]mate.seed boot=casper quiet splash ---[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340 using standard form[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] AGP: Checking aperture...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] AGP: No AGP bridge found[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Calgary: detecting Calgary via BIOS EBDA area[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing![/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Memory: 7711572K/8288684K available (7989K kernel code, 1232K rwdata, 3748K rodata, 1408K init, 1300K bss, 577112K reserved, 0K cma-reserved)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Hierarchical RCU implementation.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] NR_IRQS:16640 nr_irqs:760 16[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]     Offload RCU callbacks from all CPUs[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000]     Offload RCU callbacks from CPUs: 0-7.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] Console: colour dummy device 80x25[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] console [tty0] enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] hpet clockevent registered[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] tsc: Fast TSC calibration using PIT[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000000] tsc: Detected 2200.053 MHz processor[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000031] Calibrating delay loop (skipped), value calculated using timer frequency.. 4400.10 BogoMIPS (lpj=8800212)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000034] pid_max: default: 32768 minimum: 301[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.000039] ACPI: Core revision 20141107[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.014010] ACPI: All ACPI Tables successfully acquired[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.018428] Security Framework initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.018444] AppArmor: AppArmor initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.018445] Yama: becoming mindful.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.018988] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.020633] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.021330] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.021340] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.021563] Initializing cgroup subsys memory[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.021568] Initializing cgroup subsys devices[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.021571] Initializing cgroup subsys freezer[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.021572] Initializing cgroup subsys net_cls[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.021574] Initializing cgroup subsys blkio[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.021576] Initializing cgroup subsys perf_event[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.021579] Initializing cgroup subsys net_prio[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.021580] Initializing cgroup subsys hugetlb[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.021606] CPU: Physical Processor ID: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.021607] CPU: Processor Core ID: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.021612] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.022697] mce: CPU supports 7 MCE banks[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.022709] CPU0: Thermal monitoring enabled (TM1)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.022719] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.023092] Freeing SMP alternatives memory: 32K (ffffffff81e96000 - ffffffff81e9e000)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.034492] ftrace: allocating 30035 entries in 118 pages[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.047918] dmar: Host address width 39[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.047921] dmar: DRHD base: 0x000000fed90000 flags: 0x0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.047926] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e1ff0505e[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.047928] dmar: DRHD base: 0x000000fed91000 flags: 0x1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.047932] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.047934] dmar: RMRR base: 0x0000008b800000 end: 0x0000008fffffff[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.048061] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.048062] HPET id 0 under DRHD base 0xfed91000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.048063] Queued invalidation will be enabled to support x2apic and Intr-remapping.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.048064] Your BIOS is broken and requested that x2apic be disabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]This will slightly decrease performance.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Use 'intremap=no_x2apic_optout' to override BIOS request.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.048271] Enabled IRQ remapping in xapic mode[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.048272] x2apic not enabled, IRQ remapping is in xapic mode[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.048894] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.088541] smpboot: CPU0: Intel(R) Core(TM) i7-5650U CPU @ 2.20GHz (fam: 06, model: 3d, stepping: 04)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.088548] TSC deadline timer enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.088575] Performance Events: PEBS fmt2+, generic architected perfmon, full-width counters, Intel PMU driver.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.088580] ... version:                3[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.088581] ... bit width:              48[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.088582] ... generic registers:      4[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.088583] ... value mask:             0000ffffffffffff[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.088584] ... max period:             0000ffffffffffff[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.088585] ... fixed-purpose events:   3[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.088585] ... event mask:             000000070000000f[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.089429] x86: Booting SMP configuration:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.089430] .... node  #0, CPUs:      #1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.103721] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.103805]  #2 #3[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.132438] x86: Booted up 1 node, 4 CPUs[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.132442] smpboot: Total of 4 processors activated (17600.42 BogoMIPS)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.137322] devtmpfs: initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.139657] evm: security.selinux[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.139659] evm: security.SMACK64[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.139659] evm: security.SMACK64EXEC[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.139660] evm: security.SMACK64TRANSMUTE[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.139661] evm: security.SMACK64MMAP[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.139662] evm: security.ima[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.139663] evm: security.capability[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.139715] PM: Registering ACPI NVS region [mem 0x8ad01000-0x8ad48fff] (294912 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.139876] pinctrl core: initialized pinctrl subsystem[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.139975] RTC time: 19:09:18, date: 04/16/15[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.140082] NET: Registered protocol family 16[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.141111] cpuidle: using governor ladder[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.145127] cpuidle: using governor menu[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.145181] ACPI: bus type PCI registered[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.145183] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.145254] PCI: MMCONFIG for domain 0000 [bus 00-9b] at [mem 0xe0000000-0xe9bfffff] (base 0xe0000000)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.145257] PCI: not using MMCONFIG[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.145258] PCI: Using configuration type 1 for base access[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.149541] ACPI: Added _OSI(Module Device)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.149543] ACPI: Added _OSI(Processor Device)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.149544] ACPI: Added _OSI(3.0 _SCP Extensions)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.149546] ACPI: Added _OSI(Processor Aggregator Device)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.151722] ACPI : EC: EC description table is found, configuring boot EC[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.157455] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.157836] ACPI: Dynamic OEM Table Load:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.157844] ACPI: SSDT 0xFFFF880264EC0800 0004F0 (v01 PmRef  Cpu0Cst  00003001 INTL 20140424)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.158659] ACPI: Dynamic OEM Table Load:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.158666] ACPI: SSDT 0xFFFF880264EC1000 00067C (v01 PmRef  ApIst    00003000 INTL 20140424)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.159525] ACPI: Dynamic OEM Table Load:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.159530] ACPI: SSDT 0xFFFF880264860600 000119 (v01 PmRef  ApCst    00003000 INTL 20140424)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.160688] ACPI: Interpreter enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.160696] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.160703] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.160720] ACPI: (supports S0 S3 S4 S5)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.160721] ACPI: Using IOAPIC for interrupt routing[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.160737] PCI: MMCONFIG for domain 0000 [bus 00-9b] at [mem 0xe0000000-0xe9bfffff] (base 0xe0000000)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.161171] PCI: MMCONFIG at [mem 0xe0000000-0xe9bfffff] reserved in ACPI motherboard resources[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.161371] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.168980] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.168985] acpi PNP0A08:00: _OSC: OS assumes control of [PCIeHotplug SHPCHotplug AER PCIeCapability][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169175] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-9b] only partially covers this bridge[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169284] PCI host bridge to bus 0000:00[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169287] pci_bus 0000:00: root bus resource [bus 00-ff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169288] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169290] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169292] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169293] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169294] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169296] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169297] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169299] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169300] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169301] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169303] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169304] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169305] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169307] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169308] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169310] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169311] pci_bus 0000:00: root bus resource [mem 0x90000000-0xfeafffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169312] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed44fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169320] pci 0000:00:00.0: [8086:1604] type 00 class 0x060000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169400] pci 0000:00:02.0: [8086:1626] type 00 class 0x030000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169418] pci 0000:00:02.0: reg 0x10: [mem 0xc0000000-0xc0ffffff 64bit][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169425] pci 0000:00:02.0: reg 0x18: [mem 0xb0000000-0xbfffffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169430] pci 0000:00:02.0: reg 0x20: [io  0x3000-0x303f][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169500] pci 0000:00:03.0: [8086:160c] type 00 class 0x040300[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169509] pci 0000:00:03.0: reg 0x10: [mem 0xc1610000-0xc1613fff 64bit][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169602] pci 0000:00:14.0: [8086:9cb1] type 00 class 0x0c0330[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169620] pci 0000:00:14.0: reg 0x10: [mem 0xc1600000-0xc160ffff 64bit][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169677] pci 0000:00:14.0: PME# supported from D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169704] pci 0000:00:14.0: System wakeup disabled by ACPI[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169741] pci 0000:00:15.0: [8086:9ce0] type 00 class 0x080102[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169757] pci 0000:00:15.0: reg 0x10: [mem 0xc161a000-0xc161afff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169882] pci 0000:00:15.4: [8086:9ce6] type 00 class 0x0c8000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.169898] pci 0000:00:15.4: reg 0x10: [mem 0xc1619000-0xc1619fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170023] pci 0000:00:16.0: [8086:9cba] type 00 class 0x078000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170043] pci 0000:00:16.0: reg 0x10: [mem 0xc161b100-0xc161b11f 64bit][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170111] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170175] pci 0000:00:1b.0: [8086:9ca0] type 00 class 0x040300[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170192] pci 0000:00:1b.0: reg 0x10: [mem 0xc1614000-0xc1617fff 64bit][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170249] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170274] pci 0000:00:1b.0: System wakeup disabled by ACPI[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170308] pci 0000:00:1c.0: [8086:9c90] type 01 class 0x060400[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170379] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170409] pci 0000:00:1c.0: System wakeup disabled by ACPI[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170442] pci 0000:00:1c.1: [8086:9c92] type 01 class 0x060400[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170515] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170545] pci 0000:00:1c.1: System wakeup disabled by ACPI[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170577] pci 0000:00:1c.2: [8086:9c94] type 01 class 0x060400[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170650] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170682] pci 0000:00:1c.2: System wakeup disabled by ACPI[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170714] pci 0000:00:1c.4: [8086:9c98] type 01 class 0x060400[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170780] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170809] pci 0000:00:1c.4: System wakeup disabled by ACPI[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170842] pci 0000:00:1c.5: [8086:9c9a] type 01 class 0x060400[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170914] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170945] pci 0000:00:1c.5: System wakeup disabled by ACPI[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.170983] pci 0000:00:1f.0: [8086:9cc3] type 00 class 0x060100[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.171140] pci 0000:00:1f.3: [8086:9ca2] type 00 class 0x0c0500[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.171154] pci 0000:00:1f.3: reg 0x10: [mem 0xc161b000-0xc161b0ff 64bit][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.171172] pci 0000:00:1f.3: reg 0x20: [io  0xefa0-0xefbf][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.171245] pci 0000:00:1f.6: [8086:9ca4] type 00 class 0x118000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.171274] pci 0000:00:1f.6: reg 0x10: [mem 0xc1618000-0xc1618fff 64bit][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.171467] pci 0000:00:1c.0: PCI bridge to [bus 01][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.171548] pci 0000:02:00.0: [14e4:1570] type 00 class 0x048000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.171570] pci 0000:02:00.0: reg 0x10: [mem 0xc1500000-0xc150ffff 64bit][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.171586] pci 0000:02:00.0: reg 0x18: [mem 0xa0000000-0xafffffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.171601] pci 0000:02:00.0: reg 0x20: [mem 0xc1400000-0xc14fffff 64bit][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.171690] pci 0000:02:00.0: supports D1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.171692] pci 0000:02:00.0: PME# supported from D0 D3hot[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.181131] pci 0000:00:1c.1: PCI bridge to [bus 02][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.181136] pci 0000:00:1c.1:   bridge window [mem 0xc1400000-0xc15fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.181140] pci 0000:00:1c.1:   bridge window [mem 0xa0000000-0xafffffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.181265] pci 0000:03:00.0: [14e4:43a0] type 00 class 0x028000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.181303] pci 0000:03:00.0: reg 0x10: [mem 0xc1200000-0xc1207fff 64bit][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.181330] pci 0000:03:00.0: reg 0x18: [mem 0xc1000000-0xc11fffff 64bit][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.181526] pci 0000:03:00.0: supports D1 D2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.181528] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.181576] pci 0000:03:00.0: System wakeup disabled by ACPI[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.193149] pci 0000:00:1c.2: PCI bridge to [bus 03][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.193154] pci 0000:00:1c.2:   bridge window [mem 0xc1000000-0xc12fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.193231] pci 0000:05:00.0: [8086:156b] type 01 class 0x060400[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.193350] pci 0000:05:00.0: supports D1 D2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.193351] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205110] pci 0000:00:1c.4: PCI bridge to [bus 05-9b][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205113] pci 0000:00:1c.4:   bridge window [io  0x4000-0x6fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205116] pci 0000:00:1c.4:   bridge window [mem 0xc1700000-0xcd7fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205121] pci 0000:00:1c.4:   bridge window [mem 0xcd800000-0xd97fffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205262] pci 0000:06:00.0: [8086:156b] type 01 class 0x060400[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205386] pci 0000:06:00.0: supports D1 D2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205387] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205466] pci 0000:06:03.0: [8086:156b] type 01 class 0x060400[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205588] pci 0000:06:03.0: supports D1 D2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205590] pci 0000:06:03.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205664] pci 0000:06:04.0: [8086:156b] type 01 class 0x060400[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205786] pci 0000:06:04.0: supports D1 D2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205788] pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205863] pci 0000:06:05.0: [8086:156b] type 01 class 0x060400[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205985] pci 0000:06:05.0: supports D1 D2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.205987] pci 0000:06:05.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.206064] pci 0000:06:06.0: [8086:156b] type 01 class 0x060400[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.206187] pci 0000:06:06.0: supports D1 D2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.206188] pci 0000:06:06.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.206281] pci 0000:05:00.0: PCI bridge to [bus 06-6b][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.206288] pci 0000:05:00.0:   bridge window [io  0x4000-0x5fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.206292] pci 0000:05:00.0:   bridge window [mem 0xc1700000-0xc97fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.206298] pci 0000:05:00.0:   bridge window [mem 0xcd800000-0xd57fffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.206389] pci 0000:07:00.0: [8086:156a] type 00 class 0x088000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.206410] pci 0000:07:00.0: reg 0x10: [mem 0xc1700000-0xc173ffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.206424] pci 0000:07:00.0: reg 0x14: [mem 0xc1740000-0xc1740fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.206584] pci 0000:07:00.0: supports D1 D2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.206586] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217115] pci 0000:06:00.0: PCI bridge to [bus 07][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217124] pci 0000:06:00.0:   bridge window [mem 0xc1700000-0xc17fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217218] pci 0000:06:03.0: PCI bridge to [bus 08-38][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217225] pci 0000:06:03.0:   bridge window [io  0x4000-0x4fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217229] pci 0000:06:03.0:   bridge window [mem 0xc1800000-0xc57fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217236] pci 0000:06:03.0:   bridge window [mem 0xcd800000-0xd17fffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217321] pci 0000:06:04.0: PCI bridge to [bus 39-69][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217327] pci 0000:06:04.0:   bridge window [io  0x5000-0x5fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217331] pci 0000:06:04.0:   bridge window [mem 0xc5800000-0xc97fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217338] pci 0000:06:04.0:   bridge window [mem 0xd1800000-0xd57fffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217420] pci 0000:06:05.0: PCI bridge to [bus 6a][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217496] pci 0000:06:06.0: PCI bridge to [bus 6b][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217689] pci 0000:04:00.0: [106b:2001] type 00 class 0x018002[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.217710] pci 0000:04:00.0: reg 0x10: [mem 0xc1300000-0xc1301fff 64bit][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.229190] pci 0000:00:1c.5: PCI bridge to [bus 04][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.229195] pci 0000:00:1c.5:   bridge window [mem 0xc1300000-0xc13fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230209] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230250] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230289] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230326] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230364] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230402] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230440] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230477] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230633] ACPI: Enabled 4 GPEs in block 00 to 7F[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230655] ACPI : EC: GPE = 0x4e, I/O: command/status = 0x66, data = 0x62[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230781] vgaarb: setting as boot device: PCI:0000:00:02.0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230783] vgaarb: device added: PCI:0000:00:02.0,decodes=io+[/FONT][/COLOR][COLOR=#000000][FONT=arial]mem,owns=io+mem,locks=none[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230787] vgaarb: loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230788] vgaarb: bridge control possible 0000:00:02.0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230821] pci 0000:07:00.0: BAR 0: assigned [mem 0xc1700000-0xc173ffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230829] pci 0000:07:00.0: BAR 1: assigned [mem 0xc1740000-0xc1740fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.230981] SCSI subsystem initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.231030] libata version 3.00 loaded.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.231054] ACPI: bus type USB registered[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.231070] usbcore: registered new interface driver usbfs[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.231078] usbcore: registered new interface driver hub[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.231095] usbcore: registered new device driver usb[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.231278] PCI: Using ACPI for IRQ routing[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.236834] PCI: pci_cache_line_size set to 64 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237112] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237113] e820: reserve RAM buffer [mem 0x8ad01000-0x8bffffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237115] e820: reserve RAM buffer [mem 0x8ad61000-0x8bffffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237117] e820: reserve RAM buffer [mem 0x8ae3a000-0x8bffffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237119] e820: reserve RAM buffer [mem 0x8aecc000-0x8bffffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237120] e820: reserve RAM buffer [mem 0x8afaa000-0x8bffffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237121] e820: reserve RAM buffer [mem 0x8b000000-0x8bffffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237123] e820: reserve RAM buffer [mem 0x26f000000-0x26fffffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237225] NetLabel: Initializing[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237227] NetLabel:  domain hash size = 128[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237227] NetLabel:  protocols = UNLABELED CIPSOv4[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237239] NetLabel:  unlabeled traffic allowed by default[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237299] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.237304] hpet0: 8 comparators, 64-bit 14.318180 MHz counter[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.239338] Switched to clocksource hpet[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.244845] AppArmor: AppArmor Filesystem Enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.244908] pnp: PnP ACPI init[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245070] system 00:00: [mem 0xfed00000-0xfed03fff] has been reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245074] system 00:00: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245113] system 00:01: [io  0xffff] has been reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245114] system 00:01: [io  0x1800-0x187f] has been reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245117] system 00:01: [io  0x0800-0x087f] has been reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245119] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245136] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245744] system 00:03: [mem 0xfed1c000-0xfed1ffff] has been reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245746] system 00:03: [mem 0xfed10000-0xfed17fff] has been reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245747] system 00:03: [mem 0xfed18000-0xfed18fff] has been reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245749] system 00:03: [mem 0xfed19000-0xfed19fff] has been reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245751] system 00:03: [mem 0xe0000000-0xefffffff] could not be reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245753] system 00:03: [mem 0xfed20000-0xfed3ffff] has been reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245755] system 00:03: [mem 0xfed90000-0xfed93fff] could not be reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245756] system 00:03: [mem 0xfed45000-0xfed8ffff] has been reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245758] system 00:03: [mem 0xff000000-0xffffffff] could not be reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245760] system 00:03: [mem 0xfee00000-0xfeefffff] has been reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245762] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245811] system 00:04: [mem 0x20000000-0x201fffff] could not be reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245813] system 00:04: [mem 0x40000000-0x401fffff] could not be reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245815] system 00:04: Plug and Play ACPI device, IDs PNP0c01 (active)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.245913] pnp: PnP ACPI: found 5 devices[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252256] pci 0000:06:00.0: bridge window [io  0x1000-0x0fff] to [bus 07] add_size 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252259] pci 0000:06:00.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 07] add_size 200000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252284] pci 0000:06:05.0: bridge window [io  0x1000-0x0fff] to [bus 6a] add_size 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252286] pci 0000:06:05.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 6a] add_size 200000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252288] pci 0000:06:05.0: bridge window [mem 0x00100000-0x000fffff] to [bus 6a] add_size 200000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252299] pci 0000:06:06.0: bridge window [io  0x1000-0x0fff] to [bus 6b] add_size 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252300] pci 0000:06:06.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 6b] add_size 200000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252302] pci 0000:06:06.0: bridge window [mem 0x00100000-0x000fffff] to [bus 6b] add_size 200000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252324] pci 0000:00:1c.0: PCI bridge to [bus 01][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252334] pci 0000:00:1c.1: PCI bridge to [bus 02][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252339] pci 0000:00:1c.1:   bridge window [mem 0xc1400000-0xc15fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252343] pci 0000:00:1c.1:   bridge window [mem 0xa0000000-0xafffffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252348] pci 0000:00:1c.2: PCI bridge to [bus 03][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252352] pci 0000:00:1c.2:   bridge window [mem 0xc1000000-0xc12fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252361] pci 0000:06:00.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252363] pci 0000:06:05.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252365] pci 0000:06:05.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252366] pci 0000:06:06.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252368] pci 0000:06:06.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252370] pci 0000:06:00.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252371] pci 0000:06:05.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252372] pci 0000:06:06.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252377] pci 0000:06:00.0: BAR 15: no space for [mem size 0x00200000 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252379] pci 0000:06:00.0: BAR 15: failed to assign [mem size 0x00200000 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252381] pci 0000:06:05.0: BAR 14: no space for [mem size 0x00200000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252382] pci 0000:06:05.0: BAR 14: failed to assign [mem size 0x00200000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252385] pci 0000:06:05.0: BAR 15: no space for [mem size 0x00200000 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252387] pci 0000:06:05.0: BAR 15: failed to assign [mem size 0x00200000 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252388] pci 0000:06:06.0: BAR 14: no space for [mem size 0x00200000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252390] pci 0000:06:06.0: BAR 14: failed to assign [mem size 0x00200000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252392] pci 0000:06:06.0: BAR 15: no space for [mem size 0x00200000 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252394] pci 0000:06:06.0: BAR 15: failed to assign [mem size 0x00200000 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252396] pci 0000:06:00.0: BAR 13: no space for [io  size 0x1000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252397] pci 0000:06:00.0: BAR 13: failed to assign [io  size 0x1000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252399] pci 0000:06:05.0: BAR 13: no space for [io  size 0x1000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252400] pci 0000:06:05.0: BAR 13: failed to assign [io  size 0x1000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252401] pci 0000:06:06.0: BAR 13: no space for [io  size 0x1000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252403] pci 0000:06:06.0: BAR 13: failed to assign [io  size 0x1000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252405] pci 0000:06:06.0: BAR 14: no space for [mem size 0x00200000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252407] pci 0000:06:06.0: BAR 14: failed to assign [mem size 0x00200000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252409] pci 0000:06:06.0: BAR 15: no space for [mem size 0x00200000 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252411] pci 0000:06:06.0: BAR 15: failed to assign [mem size 0x00200000 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252412] pci 0000:06:06.0: BAR 13: no space for [io  size 0x1000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252414] pci 0000:06:06.0: BAR 13: failed to assign [io  size 0x1000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252415] pci 0000:06:05.0: BAR 14: no space for [mem size 0x00200000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252417] pci 0000:06:05.0: BAR 14: failed to assign [mem size 0x00200000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252420] pci 0000:06:05.0: BAR 15: no space for [mem size 0x00200000 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252421] pci 0000:06:05.0: BAR 15: failed to assign [mem size 0x00200000 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252423] pci 0000:06:05.0: BAR 13: no space for [io  size 0x1000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252424] pci 0000:06:05.0: BAR 13: failed to assign [io  size 0x1000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252427] pci 0000:06:00.0: BAR 15: no space for [mem size 0x00200000 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252428] pci 0000:06:00.0: BAR 15: failed to assign [mem size 0x00200000 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252430] pci 0000:06:00.0: BAR 13: no space for [io  size 0x1000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252431] pci 0000:06:00.0: BAR 13: failed to assign [io  size 0x1000][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252433] pci 0000:06:00.0: PCI bridge to [bus 07][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252439] pci 0000:06:00.0:   bridge window [mem 0xc1700000-0xc17fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252449] pci 0000:06:03.0: PCI bridge to [bus 08-38][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252451] pci 0000:06:03.0:   bridge window [io  0x4000-0x4fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252457] pci 0000:06:03.0:   bridge window [mem 0xc1800000-0xc57fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252461] pci 0000:06:03.0:   bridge window [mem 0xcd800000-0xd17fffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252468] pci 0000:06:04.0: PCI bridge to [bus 39-69][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252470] pci 0000:06:04.0:   bridge window [io  0x5000-0x5fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252476] pci 0000:06:04.0:   bridge window [mem 0xc5800000-0xc97fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252480] pci 0000:06:04.0:   bridge window [mem 0xd1800000-0xd57fffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252487] pci 0000:06:05.0: PCI bridge to [bus 6a][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252501] pci 0000:06:06.0: PCI bridge to [bus 6b][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252514] pci 0000:05:00.0: PCI bridge to [bus 06-6b][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252517] pci 0000:05:00.0:   bridge window [io  0x4000-0x5fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252522] pci 0000:05:00.0:   bridge window [mem 0xc1700000-0xc97fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252526] pci 0000:05:00.0:   bridge window [mem 0xcd800000-0xd57fffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252533] pci 0000:00:1c.4: PCI bridge to [bus 05-9b][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252535] pci 0000:00:1c.4:   bridge window [io  0x4000-0x6fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252539] pci 0000:00:1c.4:   bridge window [mem 0xc1700000-0xcd7fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252542] pci 0000:00:1c.4:   bridge window [mem 0xcd800000-0xd97fffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252547] pci 0000:00:1c.5: PCI bridge to [bus 04][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252552] pci 0000:00:1c.5:   bridge window [mem 0xc1300000-0xc13fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252560] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252561] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252563] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252564] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252566] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252567] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252568] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252570] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252571] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252573] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252574] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252576] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252577] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252578] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252580] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252581] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252583] pci_bus 0000:00: resource 20 [mem 0x90000000-0xfeafffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252584] pci_bus 0000:00: resource 21 [mem 0xfed40000-0xfed44fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252586] pci_bus 0000:02: resource 1 [mem 0xc1400000-0xc15fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252588] pci_bus 0000:02: resource 2 [mem 0xa0000000-0xafffffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252589] pci_bus 0000:03: resource 1 [mem 0xc1000000-0xc12fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252591] pci_bus 0000:05: resource 0 [io  0x4000-0x6fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252592] pci_bus 0000:05: resource 1 [mem 0xc1700000-0xcd7fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252594] pci_bus 0000:05: resource 2 [mem 0xcd800000-0xd97fffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252595] pci_bus 0000:06: resource 0 [io  0x4000-0x5fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252597] pci_bus 0000:06: resource 1 [mem 0xc1700000-0xc97fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252598] pci_bus 0000:06: resource 2 [mem 0xcd800000-0xd57fffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252600] pci_bus 0000:07: resource 1 [mem 0xc1700000-0xc17fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252601] pci_bus 0000:08: resource 0 [io  0x4000-0x4fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252603] pci_bus 0000:08: resource 1 [mem 0xc1800000-0xc57fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252604] pci_bus 0000:08: resource 2 [mem 0xcd800000-0xd17fffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252606] pci_bus 0000:39: resource 0 [io  0x5000-0x5fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252607] pci_bus 0000:39: resource 1 [mem 0xc5800000-0xc97fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252609] pci_bus 0000:39: resource 2 [mem 0xd1800000-0xd57fffff 64bit pref][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252610] pci_bus 0000:04: resource 1 [mem 0xc1300000-0xc13fffff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252635] NET: Registered protocol family 2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252805] TCP established hash table entries: 65536 (order: 7, 524288 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.252942] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.253065] TCP: Hash tables configured (established 65536 bind 65536)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.253083] TCP: reno registered[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.253094] UDP hash table entries: 4096 (order: 5, 131072 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.253120] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.253172] NET: Registered protocol family 1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.253187] pci 0000:00:02.0: Video device with shadowed ROM[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.253499] PCI: CLS 256 bytes, default 64[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    0.253549] Trying to unpack rootfs image as initramfs...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.858853] Freeing initrd memory: 22468K (ffff88003540e000 - ffff8800369ff000)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.858887] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.858890] software IO TLB [mem 0x720f6000-0x760f6000] (64MB) mapped at [ffff8800720f6000-[/FONT][/COLOR][COLOR=#000000][FONT=arial]ffff8800760f5fff][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.859114] microcode: CPU0 sig=0x306d4, pf=0x40, revision=0x1d[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.859121] microcode: CPU1 sig=0x306d4, pf=0x40, revision=0x1d[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.859129] microcode: CPU2 sig=0x306d4, pf=0x40, revision=0x1d[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.859136] microcode: CPU3 sig=0x306d4, pf=0x40, revision=0x1d[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.859186] microcode: Microcode Update Driver: v2.00 <[/FONT][/COLOR][EMAIL="tigran@aivazian.fsnet.co.uk"]tigran@aivazian.fsnet.co.uk[/EMAIL][COLOR=#000000][FONT=arial]>, Peter Oruba[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.859214] Scanning for low memory corruption every 60 seconds[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.859555] futex hash table entries: 2048 (order: 5, 131072 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.859577] Initialise system trusted keyring[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.859595] audit: initializing netlink subsys (disabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.859609] audit: type=2000 audit(1429211362.852:1): initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.859896] HugeTLB registered 2 MB page size, pre-allocated 0 pages[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.861197] zpool: loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.861200] zbud: loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.861350] VFS: Disk quotas dquot_6.5.2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.861382] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.861801] fuse init (API version 7.23)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.861926] Key type big_key registered[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.862287] Key type asymmetric registered[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.862290] Asymmetric key parser 'x509' registered[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.862337] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.862371] io scheduler noop registered[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.862374] io scheduler deadline registered (default)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.862404] io scheduler cfq registered[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.863968] pci_hotplug: PCI Hot Plug PCI Core version: 0.5[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864038] pciehp 0000:06:00.0:pcie24: Slot #0 AttnBtn- AttnInd- PwrInd- PwrCtrl- MRL- Interlock- NoCompl+ LLActRep+[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864076] pciehp 0000:06:00.0:pcie24: service driver pciehp loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864085] pciehp 0000:06:03.0:pcie24: Slot #3 AttnBtn- AttnInd- PwrInd- PwrCtrl- MRL- Interlock- NoCompl+ LLActRep+[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864115] pciehp 0000:06:03.0:pcie24: service driver pciehp loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864123] pciehp 0000:06:04.0:pcie24: Slot #4 AttnBtn- AttnInd- PwrInd- PwrCtrl- MRL- Interlock- NoCompl+ LLActRep+[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864149] pciehp 0000:06:04.0:pcie24: service driver pciehp loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864158] pciehp 0000:06:05.0:pcie24: Slot #5 AttnBtn- AttnInd- PwrInd- PwrCtrl- MRL- Interlock- NoCompl+ LLActRep+[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864183] pciehp 0000:06:05.0:pcie24: service driver pciehp loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864192] pciehp 0000:06:06.0:pcie24: Slot #6 AttnBtn- AttnInd- PwrInd- PwrCtrl- MRL- Interlock- NoCompl+ LLActRep+[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864217] pciehp 0000:06:06.0:pcie24: service driver pciehp loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864221] pciehp: PCI Express Hot Plug Controller Driver version: 0.4[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864263] efifb: probing for efifb[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864280] efifb: framebuffer at 0xb0000000, mapped to 0xffffc9000ab00000, using 4224k, total 4224k[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864282] efifb: mode is 1366x768x32, linelength=5632, pages=1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864283] efifb: scrolling: redraw[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.864284] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.866614] Console: switching to colour frame buffer device 170x48[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.868866] fb0: EFI VGA frame buffer device[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.868876] intel_idle: MWAIT substates: 0x11142120[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.868877] intel_idle: v0.4 model 0x3D[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.868878] intel_idle: lapic_timer_reliable_states 0xffffffff[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.869149] ACPI: AC Adapter [ADP1] (off-line)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.869253] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:[/FONT][/COLOR][COLOR=#000000][FONT=arial]00/PNP0C0D:00/input/input0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.869532] ACPI: Lid Switch [LID0][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.869578] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:[/FONT][/COLOR][COLOR=#000000][FONT=arial]00/PNP0C0C:00/input/input1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.869582] ACPI: Power Button [PWRB][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.869615] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:[/FONT][/COLOR][COLOR=#000000][FONT=arial]00/PNP0C0E:00/input/input2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.869617] ACPI: Sleep Button [SLPB][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.869649] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:[/FONT][/COLOR][COLOR=#000000][FONT=arial]00/input/input3[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.869651] ACPI: Power Button [PWRF][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.869946] GHES: HEST is not enabled![/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.870038] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.871423] Linux agpgart interface v0.103[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.872530] brd: module loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873049] loop: module loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873226] libphy: Fixed MDIO Bus: probed[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873229] tun: Universal TUN/TAP device driver, 1.6[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873230] tun: (C) 1999-2004 Max Krasnyansky <[/FONT][/COLOR][EMAIL="maxk@qualcomm.com"]maxk@qualcomm.com[/EMAIL][COLOR=#000000][FONT=arial]>[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873266] PPP generic driver version 2.4.2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873409] xhci_hcd 0000:00:14.0: xHCI Host Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873415] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873493] xhci_hcd 0000:00:14.0: cache line size of 256 is not supported[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873559] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873561] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873563] usb usb1: Product: xHCI Host Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873564] usb usb1: Manufacturer: Linux 3.19.0-10-generic xhci-hcd[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873565] usb usb1: SerialNumber: 0000:00:14.0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873656] hub 1-0:1.0: USB hub found[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873667] hub 1-0:1.0: 11 ports detected[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873959] xhci_hcd 0000:00:14.0: xHCI Host Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873962] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873989] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873990] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873992] usb usb2: Product: xHCI Host Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873993] usb usb2: Manufacturer: Linux 3.19.0-10-generic xhci-hcd[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.873994] usb usb2: SerialNumber: 0000:00:14.0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874076] hub 2-0:1.0: USB hub found[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874083] hub 2-0:1.0: 4 ports detected[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874139] usb: failed to peer usb2-port2 and usb1-port1 by location (usb2-port2:none) (usb1-port1:usb2-port1)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874140] usb usb2-port2: failed to peer to usb1-port1 (-16)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874141] usb: port power management may be unreliable[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874184] usb: failed to peer usb2-port3 and usb1-port1 by location (usb2-port3:none) (usb1-port1:usb2-port1)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874185] usb usb2-port3: failed to peer to usb1-port1 (-16)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874258] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874263] ehci-pci: EHCI PCI platform driver[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874275] ehci-platform: EHCI generic platform driver[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874285] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874289] ohci-pci: OHCI PCI platform driver[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874299] ohci-platform: OHCI generic platform driver[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874307] uhci_hcd: USB Universal Host Controller Interface driver[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    4.874349] i8042: PNP: No PS/2 controller found. Probing ports directly.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.598144] usb 1-1: new high-speed USB device number 2 using xhci_hcd[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.729590] usb 1-1: New USB device found, idVendor=0930, idProduct=653e[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.729593] usb 1-1: New USB device strings: Mfr=0, Product=2, SerialNumber=3[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.729595] usb 1-1: Product: USB Flash Memory[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.729597] usb 1-1: SerialNumber: 04803170E3A07889[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.841916] usb 1-3: new full-speed USB device number 3 using xhci_hcd[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.906180] i8042: No controller found[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.906244] tsc: Refined TSC clocksource calibration: 2199.999 MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.906306] mousedev: PS/2 mouse device common for all mice[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.906485] rtc_cmos 00:02: RTC can wake from S4[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.906607] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.906633] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.906650] i2c /dev entries driver[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.906708] device-mapper: uevent: version 1.0.3[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.906762] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: [/FONT][/COLOR][EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[COLOR=#000000][FONT=arial][    5.906783] Intel P-state driver initializing.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.906869] Consider also installing thermald for improved thermal control.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.906875] ledtrig-cpu: registered to indicate activity on CPUs[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.906879] EFI Variables Facility v0.08 2004-May-17[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.970651] usb 1-3: New USB device found, idVendor=0a5c, idProduct=4500[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.970653] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.970654] usb 1-3: Product: BRCM20702 Hub[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.970656] usb 1-3: Manufacturer: Apple Inc.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.970724] usb 1-3: ep 0x81 - rounding interval to 1024 microframes, ep desc says 2040 microframes[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.970963] hub 1-3:1.0: USB hub found[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.971074] hub 1-3:1.0: 3 ports detected[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.972286] PCCT header not found.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.972288] ACPI PCC probe failed.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.972379] TCP: cubic registered[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.972463] NET: Registered protocol family 10[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.972660] NET: Registered protocol family 17[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.972671] Key type dns_resolver registered[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.972914] Loading compiled-in X.509 certificates[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.973620] Loaded X.509 cert 'Magrathea: Glacier signing key: 06375db608534c1d8060bf2563592f[/FONT][/COLOR][COLOR=#000000][FONT=arial]f3ea34beb3'[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.973642] registered taskstats version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.975236] Key type trusted registered[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.977952] Key type encrypted registered[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.977958] AppArmor: AppArmor sha1 policy hashing enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.977961] ima: No TPM chip found, activating TPM-bypass![/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.977973] evm: HMAC attrs: 0x1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.978868]   Magic number: 11:820:192[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.978921] acpi device:1e: hash matches[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.978982] rtc_cmos 00:02: setting system clock to 2015-04-16 19:09:24 UTC (1429211364)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.979030] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.979030] EDD information not available.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.979115] PM: Hibernation image not present or could not be loaded.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.979412] Freeing unused kernel memory: 1408K (ffffffff81d36000 - ffffffff81e96000)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.979413] Write protecting the kernel read-only data: 12288k[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.979597] Freeing unused kernel memory: 192K (ffff8800027d0000 - ffff880002800000)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.979680] Freeing unused kernel memory: 348K (ffff880002ba9000 - ffff880002c00000)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    5.989809] random: systemd-udevd urandom read with 17 bits of entropy available[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.013957] [drm] Initialized drm 1.1.0 20060810[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.038607] [drm] Memory usable by graphics device = 4096M[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.038611] checking generic (b0000000 420000) vs hw (b0000000 10000000)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.038613] fb: switching to inteldrmfb from EFI VGA[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.038630] Console: switching to colour dummy device 80x25[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.038696] [drm] Replacing VGA console driver[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.053767] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.053770] [drm] Driver supports precise vblank timestamp query.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.053872] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=[/FONT][/COLOR][COLOR=#000000][FONT=arial]io+mem,decodes=io+mem:owns=io+[/FONT][/COLOR][COLOR=#000000][FONT=arial]mem[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.081642] usb 1-5: new full-speed USB device number 4 using xhci_hcd[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.109533] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.109932] acpi device:02: registered as cooling_device4[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.109994] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:[/FONT][/COLOR][COLOR=#000000][FONT=arial]00/PNP0A08:00/LNXVIDEO:00/[/FONT][/COLOR][COLOR=#000000][FONT=arial]input/input4[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.110083] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.161605] [drm] GMBUS [i915 gmbus dpb] timed out, falling back to bit banging on pin 5[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.211443] usb 1-5: New USB device found, idVendor=05ac, idProduct=0290[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.211447] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.211449] usb 1-5: Product: Apple Internal Keyboard / Trackpad[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.211450] usb 1-5: Manufacturer: Apple Inc.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.211451] usb 1-5: SerialNumber: DQ651224ZREF94QA53D[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.215650] hidraw: raw HID events driver (C) Jiri Kosina[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.216595] usb-storage 1-1:1.0: USB Mass Storage device detected[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.217556] scsi host0: usb-storage 1-1:1.0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.217630] usbcore: registered new interface driver usb-storage[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.218543] usbcore: registered new interface driver uas[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.219172] usbcore: registered new interface driver usbhid[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.219174] usbhid: USB HID core driver[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.233552] [drm] GMBUS [i915 gmbus dpc] timed out, falling back to bit banging on pin 4[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.250012] fbcon: inteldrmfb (fb0) is primary device[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.281604] usb 1-3.1: new full-speed USB device number 5 using xhci_hcd[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.371025] usb 1-3.1: New USB device found, idVendor=05ac, idProduct=820a[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.371027] usb 1-3.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.371206] usb 1-3.1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.421235] apple 0003:05AC:0290.0001: hiddev0,hidraw0: USB HID v1.10 Device [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:14.0-5/input0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.421477] input: Apple Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:[/FONT][/COLOR][COLOR=#000000][FONT=arial]14.0/usb1/1-5/1-5:1.1/0003:[/FONT][/COLOR][COLOR=#000000][FONT=arial]05AC:0290.0002/input/input5[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.441449] usb 1-3.2: new full-speed USB device number 6 using xhci_hcd[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.477454] apple 0003:05AC:0290.0002: input,hiddev0,hidraw1: USB HID v1.10 Keyboard [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:14.0-5/input1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.530631] usb 1-3.2: New USB device found, idVendor=05ac, idProduct=820b[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.530632] usb 1-3.2: New USB device strings: Mfr=0, Product=0, SerialNumber=0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.530729] usb 1-3.2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.601197] usb 1-3.3: new full-speed USB device number 7 using xhci_hcd[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.691686] usb 1-3.3: New USB device found, idVendor=05ac, idProduct=828f[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.691688] usb 1-3.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.691689] usb 1-3.3: Product: Bluetooth USB Host Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.691690] usb 1-3.3: Manufacturer: Apple Inc.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.694469] input: HID 05ac:820a as /devices/pci0000:00/0000:00:[/FONT][/COLOR][COLOR=#000000][FONT=arial]14.0/usb1/1-3/1-3.1/1-3.1:1.0/[/FONT][/COLOR][COLOR=#000000][FONT=arial]0003:05AC:820A.0003/input/[/FONT][/COLOR][COLOR=#000000][FONT=arial]input6[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.749295] hid-generic 0003:05AC:820A.0003: input,hidraw2: USB HID v1.11 Keyboard [HID 05ac:820a] on usb-0000:00:14.0-3.1/input0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.749412] input: HID 05ac:820b as /devices/pci0000:00/0000:00:[/FONT][/COLOR][COLOR=#000000][FONT=arial]14.0/usb1/1-3/1-3.2/1-3.2:1.0/[/FONT][/COLOR][COLOR=#000000][FONT=arial]0003:05AC:820B.0004/input/[/FONT][/COLOR][COLOR=#000000][FONT=arial]input7[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.749662] hid-generic 0003:05AC:820B.0004: input,hidraw3: USB HID v1.11 Mouse [HID 05ac:820b] on usb-0000:00:14.0-3.2/input0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    6.905031] Switched to clocksource tsc[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.217065] scsi 0:0:0:0: Direct-Access              USB Flash Memory 5.00 PQ: 0 ANSI: 0 CCS[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.217346] sd 0:0:0:0: Attached scsi generic sg0 type 0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.217701] sd 0:0:0:0: [sda] 4028416 512-byte logical blocks: (2.06 GB/1.92 GiB)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.217931] sd 0:0:0:0: [sda] Write Protect is off[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.217934] sd 0:0:0:0: [sda] Mode Sense: 23 00 00 00[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.218062] sd 0:0:0:0: [sda] No Caching mode page found[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.218062] sd 0:0:0:0: [sda] Assuming drive cache: write through[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.221090]  sda: sda1 sda2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.221818] sd 0:0:0:0: [sda] Attached SCSI removable disk[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.576365] Console: switching to colour frame buffer device 170x48[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.578514] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.578515] i915 0000:00:02.0: registered panic notifier[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.803515] ISO 9660 Extensions: Microsoft Joliet Level 3[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.805718] ISO 9660 Extensions: RRIP_1991A[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    7.821973] squashfs: version 4.0 (2009/01/31) Phillip Lougher[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][    8.707363] random: nonblocking pool is initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.383747] systemd[1]: Inserted module 'autofs4'[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.504685] systemd[1]: systemd 219 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT -GNUTLS +ACL +XZ -LZ4 -SECCOMP +BLKID -ELFUTILS +KMOD -IDN)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.504776] systemd[1]: Detected architecture 'x86-64'.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.505583] systemd[1]: Set hostname to <ubuntu-mate>.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.505716] systemd[1]: Initializing machine ID from random generator.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.577439] systemd[1]: Unit type .busname is not supported on this system.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.588346] systemd[1]: Unit cdrom.mount is bound to inactive unit. Stopping, too.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.588358] systemd[1]: Mounted /.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.588437] systemd[1]: Mounted /rofs.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589344] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589352] systemd[1]: Starting Arbitrary Executable File Formats File System Automount Point.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589391] systemd[1]: Reached target Encrypted Volumes.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589396] systemd[1]: Starting Encrypted Volumes.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589418] systemd[1]: Reached target Swap.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589422] systemd[1]: Starting Swap.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589458] systemd[1]: Reached target Remote File Systems (Pre).[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589462] systemd[1]: Starting Remote File Systems (Pre).[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589494] systemd[1]: Started Forward Password Requests to Wall Directory Watch.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589498] systemd[1]: Starting Forward Password Requests to Wall Directory Watch.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589539] systemd[1]: Created slice Root Slice.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589544] systemd[1]: Starting Root Slice.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589593] systemd[1]: Listening on udev Control Socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589597] systemd[1]: Starting udev Control Socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589651] systemd[1]: Listening on Journal Socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589659] systemd[1]: Starting Journal Socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589696] systemd[1]: Listening on Journal Audit Socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589700] systemd[1]: Starting Journal Audit Socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589725] systemd[1]: Listening on udev Kernel Socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589729] systemd[1]: Starting udev Kernel Socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589755] systemd[1]: Listening on Delayed Shutdown Socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589760] systemd[1]: Starting Delayed Shutdown Socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589790] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589795] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589823] systemd[1]: Listening on LVM2 metadata daemon socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589827] systemd[1]: Starting LVM2 metadata daemon socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589898] systemd[1]: Created slice System Slice.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.589906] systemd[1]: Starting System Slice.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.590173] systemd[1]: Mounting POSIX Message Queue File System...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.590550] systemd[1]: Started Braille Device Support.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.590850] systemd[1]: Starting Braille Device Support...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.592200] systemd[1]: Starting Load Kernel Modules...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.592931] systemd[1]: Starting Create list of required static device nodes for the current kernel...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.601597] systemd[1]: Started Set Up Additional Binary Formats.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.602258] systemd[1]: Mounting Huge Pages File System...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.602816] systemd[1]: Starting Remount Root and Kernel File Systems...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.603164] systemd[1]: Starting udev Coldplug all Devices...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.603512] systemd[1]: Starting Nameserver information manager...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.603703] systemd[1]: Created slice system-getty.slice.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.603716] systemd[1]: Starting system-getty.slice.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.604161] systemd[1]: Starting Setup Virtual Console...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.604499] systemd[1]: Starting Uncomplicated firewall...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.605039] systemd[1]: Started Read required files in advance.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.605197] systemd[1]: Starting Read required files in advance...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.605694] systemd[1]: Mounting Debug File System...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.605780] systemd[1]: Listening on Device-mapper event daemon FIFOs.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.605790] systemd[1]: Starting Device-mapper event daemon FIFOs.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.606158] systemd[1]: Starting Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.606298] systemd[1]: Created slice User and Session Slice.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.606309] systemd[1]: Starting User and Session Slice.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.606341] systemd[1]: Reached target Slices.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.606348] systemd[1]: Starting Slices.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.606414] systemd[1]: Listening on Journal Socket (/dev/log).[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.606427] systemd[1]: Starting Journal Socket (/dev/log).[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.606474] systemd[1]: Listening on Syslog Socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.606485] systemd[1]: Starting Syslog Socket.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.606921] systemd[1]: Starting Journal Service...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.607744] systemd[1]: Mounted Debug File System.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.607874] systemd[1]: Mounted POSIX Message Queue File System.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.608046] systemd[1]: Mounted Huge Pages File System.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.677113] systemd[1]: Started Create list of required static device nodes for the current kernel.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.679671] systemd[1]: Started Remount Root and Kernel File Systems.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.683587] systemd[1]: Starting Various fixups to make systemd work better on Debian...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.684009] systemd[1]: Started Rebuild Hardware Database.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.684443] systemd[1]: Starting Load/Save Random Seed...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.684833] systemd[1]: Starting Create Static Device Nodes in /dev...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.685536] systemd[1]: Started Setup Virtual Console.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.686098] systemd[1]: Started Nameserver information manager.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.687377] systemd[1]: Started Load/Save Random Seed.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.689077] systemd[1]: Started Various fixups to make systemd work better on Debian.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.742163] systemd[1]: Started Uncomplicated firewall.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.751608] systemd[1]: Started udev Coldplug all Devices.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.752176] systemd[1]: Starting udev Wait for Complete Device Initialization...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.784653] systemd[1]: Started Create Static Device Nodes in /dev.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.785864] systemd[1]: Starting udev Kernel Device Manager...[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   14.956206] systemd[1]: Started Journal Service.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.058260] systemd-journald[815]: Received request to flush runtime journal from PID 1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.094411] lp: driver loaded but no devices found[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.117705] ppdev: user-space parallel port driver[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.268515] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.338923] ACPI: SBS HC: EC = 0xffff880264815cc0, offset = 0x20, query_bit = 0x10[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.427389] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT0] (battery present)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.448774] device-mapper: multipath: version 1.7.0 loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.573244] applesmc: key=612 fan=1 temp=33 index=33 acc=0 lux=2 kbd=1[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.589610] input: bcm5974 as /devices/pci0000:00/0000:00:[/FONT][/COLOR][COLOR=#000000][FONT=arial]14.0/usb1/1-5/1-5:1.2/input/[/FONT][/COLOR][COLOR=#000000][FONT=arial]input8[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.589795] usbcore: registered new interface driver bcm5974[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.597484] AVX2 version of gcm_enc/dec engaged.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.597486] AES CTR mode by8 optimization enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.709112] sound hdaudioC1D0: autoconfig: line_outs=1 (0x12/0x0/0x0/0x0/0x0) type:speaker[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.709116] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.709118] sound hdaudioC1D0:    hp_outs=1 (0x10/0x0/0x0/0x0/0x0)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.709119] sound hdaudioC1D0:    mono: mono_out=0x0[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.709121] sound hdaudioC1D0:    inputs:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.709123] sound hdaudioC1D0:      Internal Mic=0x1c[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.709125] sound hdaudioC1D0:      Mic=0x18[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.712202] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:[/FONT][/COLOR][COLOR=#000000][FONT=arial]03.0/sound/card0/input9[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.712268] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:[/FONT][/COLOR][COLOR=#000000][FONT=arial]03.0/sound/card0/input10[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.712329] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:[/FONT][/COLOR][COLOR=#000000][FONT=arial]03.0/sound/card0/input11[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.712510] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:[/FONT][/COLOR][COLOR=#000000][FONT=arial]1b.0/sound/card1/input12[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.712564] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:[/FONT][/COLOR][COLOR=#000000][FONT=arial]1b.0/sound/card1/input13[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.863382] intel_rapl: Found RAPL domain package[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.863386] intel_rapl: Found RAPL domain core[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.863387] intel_rapl: Found RAPL domain uncore[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   15.863389] intel_rapl: Found RAPL domain dram[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   16.614485] Bluetooth: Core ver 2.20[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   16.614498] NET: Registered protocol family 31[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   16.614499] Bluetooth: HCI device and connection manager initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   16.614511] Bluetooth: HCI socket layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   16.614513] Bluetooth: L2CAP socket layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   16.614523] Bluetooth: SCO socket layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   16.624542] usbcore: registered new interface driver btusb[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   16.739145] usb 1-3.1: USB disconnect, device number 5[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   16.955136] usb 1-3.2: USB disconnect, device number 6[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   17.661842] Bluetooth: BNEP (Ethernet Emulation) ver 1.3[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   17.661845] Bluetooth: BNEP filters: protocol multicast[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   17.661847] Bluetooth: BNEP socket layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   17.815294] Bluetooth: RFCOMM TTY layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   17.815305] Bluetooth: RFCOMM socket layer initialized[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   17.815310] Bluetooth: RFCOMM ver 1.11[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   23.616802] usb 2-2: new SuperSpeed USB device number 2 using xhci_hcd[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   23.638953] usb 2-2: New USB device found, idVendor=0b95, idProduct=1790[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   23.638956] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   23.638958] usb 2-2: Product: AX88179[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   23.638959] usb 2-2: Manufacturer: ASIX Elec. Corp.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   23.638961] usb 2-2: SerialNumber: 00000000000001[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   25.144134] ax88179_178a 2-2:1.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-2, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:0a:cd:27:0a:f2[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   25.144207] usbcore: registered new interface driver ax88179_178a[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   25.484834] cfg80211: Calling CRDA to update world regulatory domain[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   25.855117] cfg80211: World regulatory domain updated:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   25.855122] cfg80211:  DFS Master region: unset[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   25.855123] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   25.855126] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   25.855128] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   25.855131] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   25.855133] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   25.855136] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][   28.631488] ax88179_178a 2-2:1.0 eth0: ax88179 - Link status is: 1[/FONT][/COLOR]


```
[FONT=arial]
Of course I tried to see any partition with df, but I only saw my USB stick.
[/FONT]
[FONT=arial]I'm completely new with apple hardware so maybe I missed something regarding rEFInd or Apple partitioning tool...[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thanks for your help ![/FONT]

---

### Post by JGrossholtz on 2015-04-18
Here is some additional data :

lspci output :
```
ubuntu-mate@ubuntu-mate:~$ lspci 
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:15.0 DMA controller: Intel Corporation Wildcat Point-LP Serial IO DMA Controller (rev 03)
00:15.4 Serial bus controller [0c80]: Intel Corporation Wildcat Point-LP Serial IO GSPI Controller #1 (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.1 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #2 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1c.5 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #6 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)
02:00.0 Multimedia controller: Broadcom Corporation Device 1570
03:00.0 Network controller: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter (rev 03)
04:00.0 Mass storage controller: Apple Inc. Device 2001 (rev 01)
05:00.0 PCI bridge: Intel Corporation Device 156b
06:00.0 PCI bridge: Intel Corporation Device 156b
06:03.0 PCI bridge: Intel Corporation Device 156b
06:04.0 PCI bridge: Intel Corporation Device 156b
06:05.0 PCI bridge: Intel Corporation Device 156b
06:06.0 PCI bridge: Intel Corporation Device 156b
07:00.0 System peripheral: Intel Corporation Device 156a

```
lsusb output (I unplugged the live USB before launching this command) :


```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05ac:0290 Apple, Inc. 
Bus 001 Device 007: ID 05ac:828f Apple, Inc. 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

And ls /dev :
```
ubuntu-mate@ubuntu-mate:~$ ls /dev/ -la
total 0
drwxr-xr-x  19 root root        4340 Apr 18 10:51 .
drwxr-xr-x   1 root root         220 Apr 18 10:47 ..
crw-------   1 root root     10, 235 Apr 18 10:48 autofs
drwxr-xr-x   2 root root         580 Apr 18 10:51 block
drwxr-xr-x   2 root root          60 Apr 18 10:51 bsg
crw-------   1 root root     10, 234 Apr 18 10:48 btrfs-control
drwxr-xr-x   3 root root          60 Apr 18 10:47 bus
drwxr-xr-x   2 root root        3960 Apr 18 10:51 char
crw-------   1 root root      5,   1 Apr 18 10:48 console
lrwxrwxrwx   1 root root          11 Apr 18 10:47 core -> /proc/kcore
drwxr-xr-x   2 root root          60 Apr 18 10:47 cpu
crw-------   1 root root     10,  60 Apr 18 10:48 cpu_dma_latency
crw-------   1 root root     10, 203 Apr 18 10:48 cuse
drwxr-xr-x   6 root root         120 Apr 18 10:51 disk
drwxr-xr-x   2 root root         100 Apr 18 10:47 dri
crw-------   1 root root     10,  61 Apr 18 10:48 ecryptfs
crw-rw----   1 root video    29,   0 Apr 18 10:48 fb0
lrwxrwxrwx   1 root root          13 Apr 18 10:47 fd -> /proc/self/fd
crw-rw-rw-   1 root root      1,   7 Apr 18 10:48 full
crw-rw-rw-   1 root root     10, 229 Apr 18 10:48 fuse
crw-------   1 root root    251,   0 Apr 18 10:48 hidraw0
crw-------   1 root root    251,   1 Apr 18 10:48 hidraw1
crw-------   1 root root     10, 228 Apr 18 10:48 hpet
drwxr-xr-x   2 root root           0 Apr 18 10:48 hugepages
crw-------   1 root root     89,   0 Apr 18 10:48 i2c-0
crw-------   1 root root     89,   1 Apr 18 10:48 i2c-1
crw-------   1 root root     89,   2 Apr 18 10:48 i2c-2
crw-------   1 root root     89,   3 Apr 18 10:48 i2c-3
crw-------   1 root root     89,   4 Apr 18 10:48 i2c-4
crw-------   1 root root     89,   5 Apr 18 10:48 i2c-5
crw-------   1 root root     89,   6 Apr 18 10:48 i2c-6
crw-------   1 root root     89,   7 Apr 18 10:48 i2c-7
crw-------   1 root root     89,   8 Apr 18 10:48 i2c-8
lrwxrwxrwx   1 root root          25 Apr 18 10:48 initctl -> /run/systemd/initctl/fifo
lrwxrwxrwx   1 root root          14 Apr 18 10:47 .initramfs -> /run/initramfs
drwxr-xr-x   4 root root         360 Apr 18 10:48 input
crw-r--r--   1 root root      1,  11 Apr 18 10:48 kmsg
crw-rw----+  1 root root     10, 232 Apr 18 10:48 kvm
lrwxrwxrwx   1 root root          28 Apr 18 10:48 log -> /run/systemd/journal/dev-log
brw-rw----   1 root disk      7,   0 Apr 18 10:48 loop0
brw-rw----   1 root disk      7,   1 Apr 18 10:48 loop1
brw-rw----   1 root disk      7,   2 Apr 18 10:48 loop2
brw-rw----   1 root disk      7,   3 Apr 18 10:48 loop3
brw-rw----   1 root disk      7,   4 Apr 18 10:48 loop4
brw-rw----   1 root disk      7,   5 Apr 18 10:48 loop5
brw-rw----   1 root disk      7,   6 Apr 18 10:48 loop6
brw-rw----   1 root disk      7,   7 Apr 18 10:48 loop7
crw-rw----   1 root disk     10, 237 Apr 18 10:48 loop-control
drwxr-xr-x   2 root root          60 Apr 18 10:47 mapper
crw-------   1 root root     10, 227 Apr 18 10:48 mcelog
crw-------   1 root root    250,   0 Apr 18 10:48 mei0
crw-r-----   1 root kmem      1,   1 Apr 18 10:48 mem
crw-------   1 root root     10,  57 Apr 18 10:48 memory_bandwidth
drwxrwxrwt   2 root root          40 Apr 18 10:47 mqueue
drwxr-xr-x   2 root root          60 Apr 18 10:47 net
crw-------   1 root root     10,  59 Apr 18 10:48 network_latency
crw-------   1 root root     10,  58 Apr 18 10:48 network_throughput
crw-rw-rw-   1 root root      1,   3 Apr 18 10:48 null
crw-r-----   1 root kmem      1,   4 Apr 18 10:48 port
crw-------   1 root root    108,   0 Apr 18 10:48 ppp
crw-------   1 root root     10,   1 Apr 18 10:48 psaux
crw-rw-rw-   1 root tty       5,   2 Apr 18 10:52 ptmx
drwxr-xr-x   2 root root           0 Apr 18 10:47 pts
brw-rw----   1 root disk      1,   0 Apr 18 10:48 ram0
brw-rw----   1 root disk      1,   1 Apr 18 10:48 ram1
brw-rw----   1 root disk      1,  10 Apr 18 10:48 ram10
brw-rw----   1 root disk      1,  11 Apr 18 10:48 ram11
brw-rw----   1 root disk      1,  12 Apr 18 10:48 ram12
brw-rw----   1 root disk      1,  13 Apr 18 10:48 ram13
brw-rw----   1 root disk      1,  14 Apr 18 10:48 ram14
brw-rw----   1 root disk      1,  15 Apr 18 10:48 ram15
brw-rw----   1 root disk      1,   2 Apr 18 10:48 ram2
brw-rw----   1 root disk      1,   3 Apr 18 10:48 ram3
brw-rw----   1 root disk      1,   4 Apr 18 10:48 ram4
brw-rw----   1 root disk      1,   5 Apr 18 10:48 ram5
brw-rw----   1 root disk      1,   6 Apr 18 10:48 ram6
brw-rw----   1 root disk      1,   7 Apr 18 10:48 ram7
brw-rw----   1 root disk      1,   8 Apr 18 10:48 ram8
brw-rw----   1 root disk      1,   9 Apr 18 10:48 ram9
crw-rw-rw-   1 root root      1,   8 Apr 18 10:48 random
crw-rw-r--   1 root root     10,  62 Apr 18 10:48 rfkill
lrwxrwxrwx   1 root root           4 Apr 18 10:48 rtc -> rtc0
crw-------   1 root root    254,   0 Apr 18 10:48 rtc0
brw-rw----   1 root disk      8,  16 Apr 18 10:51 sdb
brw-rw----   1 root disk      8,  17 Apr 18 10:51 sdb1
brw-rw----   1 root disk      8,  18 Apr 18 10:51 sdb2
crw-rw----   1 root disk     21,   0 Apr 18 10:51 sg0
drwxrwxrwt   2 root root         240 Apr 18 10:50 shm
crw-------   1 root root     10, 231 Apr 18 10:48 snapshot
drwxr-xr-x   3 root root         280 Apr 18 10:48 snd
lrwxrwxrwx   1 root root          15 Apr 18 10:47 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root root          15 Apr 18 10:47 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root root          15 Apr 18 10:47 stdout -> /proc/self/fd/1
crw-rw-rw-   1 root tty       5,   0 Apr 18 10:48 tty
crw--w----   1 root tty       4,   0 Apr 18 10:48 tty0
crw--w----   1 root tty       4,   1 Apr 18 10:48 tty1
crw--w----   1 root tty       4,  10 Apr 18 10:48 tty10
crw--w----   1 root tty       4,  11 Apr 18 10:48 tty11
crw--w----   1 root tty       4,  12 Apr 18 10:48 tty12
crw--w----   1 root tty       4,  13 Apr 18 10:48 tty13
crw--w----   1 root tty       4,  14 Apr 18 10:48 tty14
crw--w----   1 root tty       4,  15 Apr 18 10:48 tty15
crw--w----   1 root tty       4,  16 Apr 18 10:48 tty16
crw--w----   1 root tty       4,  17 Apr 18 10:48 tty17
crw--w----   1 root tty       4,  18 Apr 18 10:48 tty18
crw--w----   1 root tty       4,  19 Apr 18 10:48 tty19
crw--w----   1 root tty       4,   2 Apr 18 10:48 tty2
crw--w----   1 root tty       4,  20 Apr 18 10:48 tty20
crw--w----   1 root tty       4,  21 Apr 18 10:48 tty21
crw--w----   1 root tty       4,  22 Apr 18 10:48 tty22
crw--w----   1 root tty       4,  23 Apr 18 10:48 tty23
crw--w----   1 root tty       4,  24 Apr 18 10:48 tty24
crw--w----   1 root tty       4,  25 Apr 18 10:48 tty25
crw--w----   1 root tty       4,  26 Apr 18 10:48 tty26
crw--w----   1 root tty       4,  27 Apr 18 10:48 tty27
crw--w----   1 root tty       4,  28 Apr 18 10:48 tty28
crw--w----   1 root tty       4,  29 Apr 18 10:48 tty29
crw--w----   1 root tty       4,   3 Apr 18 10:48 tty3
crw--w----   1 root tty       4,  30 Apr 18 10:48 tty30
crw--w----   1 root tty       4,  31 Apr 18 10:48 tty31
crw--w----   1 root tty       4,  32 Apr 18 10:48 tty32
crw--w----   1 root tty       4,  33 Apr 18 10:48 tty33
crw--w----   1 root tty       4,  34 Apr 18 10:48 tty34
crw--w----   1 root tty       4,  35 Apr 18 10:48 tty35
crw--w----   1 root tty       4,  36 Apr 18 10:48 tty36
crw--w----   1 root tty       4,  37 Apr 18 10:48 tty37
crw--w----   1 root tty       4,  38 Apr 18 10:48 tty38
crw--w----   1 root tty       4,  39 Apr 18 10:48 tty39
crw--w----   1 root tty       4,   4 Apr 18 10:48 tty4
crw--w----   1 root tty       4,  40 Apr 18 10:48 tty40
crw--w----   1 root tty       4,  41 Apr 18 10:48 tty41
crw--w----   1 root tty       4,  42 Apr 18 10:48 tty42
crw--w----   1 root tty       4,  43 Apr 18 10:48 tty43
crw--w----   1 root tty       4,  44 Apr 18 10:48 tty44
crw--w----   1 root tty       4,  45 Apr 18 10:48 tty45
crw--w----   1 root tty       4,  46 Apr 18 10:48 tty46
crw--w----   1 root tty       4,  47 Apr 18 10:48 tty47
crw--w----   1 root tty       4,  48 Apr 18 10:48 tty48
crw--w----   1 root tty       4,  49 Apr 18 10:48 tty49
crw--w----   1 root tty       4,   5 Apr 18 10:48 tty5
crw--w----   1 root tty       4,  50 Apr 18 10:48 tty50
crw--w----   1 root tty       4,  51 Apr 18 10:48 tty51
crw--w----   1 root tty       4,  52 Apr 18 10:48 tty52
crw--w----   1 root tty       4,  53 Apr 18 10:48 tty53
crw--w----   1 root tty       4,  54 Apr 18 10:48 tty54
crw--w----   1 root tty       4,  55 Apr 18 10:48 tty55
crw--w----   1 root tty       4,  56 Apr 18 10:48 tty56
crw--w----   1 root tty       4,  57 Apr 18 10:48 tty57
crw--w----   1 root tty       4,  58 Apr 18 10:48 tty58
crw--w----   1 root tty       4,  59 Apr 18 10:48 tty59
crw--w----   1 root tty       4,   6 Apr 18 10:48 tty6
crw--w----   1 root tty       4,  60 Apr 18 10:48 tty60
crw--w----   1 root tty       4,  61 Apr 18 10:48 tty61
crw--w----   1 root tty       4,  62 Apr 18 10:48 tty62
crw--w----   1 root tty       4,  63 Apr 18 10:48 tty63
crw--w----   1 root tty       4,   7 Apr 18 10:48 tty7
crw--w----   1 root tty       4,   8 Apr 18 10:48 tty8
crw--w----   1 root tty       4,   9 Apr 18 10:48 tty9
crw-------   1 root root      5,   3 Apr 18 10:48 ttyprintk
crw-rw----   1 root dialout   4,  64 Apr 18 10:48 ttyS0
crw-rw----   1 root dialout   4,  65 Apr 18 10:48 ttyS1
crw-rw----   1 root dialout   4,  74 Apr 18 10:48 ttyS10
crw-rw----   1 root dialout   4,  75 Apr 18 10:48 ttyS11
crw-rw----   1 root dialout   4,  76 Apr 18 10:48 ttyS12
crw-rw----   1 root dialout   4,  77 Apr 18 10:48 ttyS13
crw-rw----   1 root dialout   4,  78 Apr 18 10:48 ttyS14
crw-rw----   1 root dialout   4,  79 Apr 18 10:48 ttyS15
crw-rw----   1 root dialout   4,  80 Apr 18 10:48 ttyS16
crw-rw----   1 root dialout   4,  81 Apr 18 10:48 ttyS17
crw-rw----   1 root dialout   4,  82 Apr 18 10:48 ttyS18
crw-rw----   1 root dialout   4,  83 Apr 18 10:48 ttyS19
crw-rw----   1 root dialout   4,  66 Apr 18 10:48 ttyS2
crw-rw----   1 root dialout   4,  84 Apr 18 10:48 ttyS20
crw-rw----   1 root dialout   4,  85 Apr 18 10:48 ttyS21
crw-rw----   1 root dialout   4,  86 Apr 18 10:48 ttyS22
crw-rw----   1 root dialout   4,  87 Apr 18 10:48 ttyS23
crw-rw----   1 root dialout   4,  88 Apr 18 10:48 ttyS24
crw-rw----   1 root dialout   4,  89 Apr 18 10:48 ttyS25
crw-rw----   1 root dialout   4,  90 Apr 18 10:48 ttyS26
crw-rw----   1 root dialout   4,  91 Apr 18 10:48 ttyS27
crw-rw----   1 root dialout   4,  92 Apr 18 10:48 ttyS28
crw-rw----   1 root dialout   4,  93 Apr 18 10:48 ttyS29
crw-rw----   1 root dialout   4,  67 Apr 18 10:48 ttyS3
crw-rw----   1 root dialout   4,  94 Apr 18 10:48 ttyS30
crw-rw----   1 root dialout   4,  95 Apr 18 10:48 ttyS31
crw-rw----   1 root dialout   4,  68 Apr 18 10:48 ttyS4
crw-rw----   1 root dialout   4,  69 Apr 18 10:48 ttyS5
crw-rw----   1 root dialout   4,  70 Apr 18 10:48 ttyS6
crw-rw----   1 root dialout   4,  71 Apr 18 10:48 ttyS7
crw-rw----   1 root dialout   4,  72 Apr 18 10:48 ttyS8
crw-rw----   1 root dialout   4,  73 Apr 18 10:48 ttyS9
crw-------   1 root root     10, 239 Apr 18 10:48 uhid
crw-------   1 root root     10, 223 Apr 18 10:48 uinput
crw-rw-rw-   1 root root      1,   9 Apr 18 10:48 urandom
drwxr-xr-x   2 root root          80 Apr 18 10:47 usb
crw-rw----   1 root tty       7,   0 Apr 18 10:48 vcs
crw-rw----   1 root tty       7,   1 Apr 18 10:48 vcs1
crw-rw----   1 root tty       7,   2 Apr 18 10:48 vcs2
crw-rw----   1 root tty       7,   3 Apr 18 10:48 vcs3
crw-rw----   1 root tty       7,   4 Apr 18 10:48 vcs4
crw-rw----   1 root tty       7,   5 Apr 18 10:48 vcs5
crw-rw----   1 root tty       7,   6 Apr 18 10:48 vcs6
crw-rw----   1 root tty       7,   7 Apr 18 10:48 vcs7
crw-rw----   1 root tty       7, 128 Apr 18 10:48 vcsa
crw-rw----   1 root tty       7, 129 Apr 18 10:48 vcsa1
crw-rw----   1 root tty       7, 130 Apr 18 10:48 vcsa2
crw-rw----   1 root tty       7, 131 Apr 18 10:48 vcsa3
crw-rw----   1 root tty       7, 132 Apr 18 10:48 vcsa4
crw-rw----   1 root tty       7, 133 Apr 18 10:48 vcsa5
crw-rw----   1 root tty       7, 134 Apr 18 10:48 vcsa6
crw-rw----   1 root tty       7, 135 Apr 18 10:48 vcsa7
drwxr-xr-x   2 root root          60 Apr 18 10:48 vfio
crw-------   1 root root     10,  63 Apr 18 10:48 vga_arbiter
crw-------   1 root root     10, 137 Apr 18 10:48 vhci
crw-------   1 root root     10, 238 Apr 18 10:48 vhost-net
prw-r-----   1 root adm            0 Apr 18 10:48 xconsole
crw-rw-rw-   1 root root      1,   5 Apr 18 10:48 zero



```





Any idea about what I could even try ?

---

### Post by oldfred on 2015-04-18
Do not know Mac, but your Broadwell is very new.

You probably only have a chance of it working with 15.04. 
 Ubuntu 15.04 has the Linux 3.19 kernel, systemd 219, Mesa 10.5, X.Org Server 1.17, GCC 4.9


But 14.04.2 does have 3.16 kernel.

       Broadwell (future) fix for use with 14.04's 3.13 kernel. Fixes really in 3.15 kernel
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY](http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY)

 Dell XPS13 - New Broadwell, not yet fully supported Feb 2015
[http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/](http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/)
[http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly](http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly)

---

### Post by JGrossholtz on 2015-04-19
Thanks for you answer Oldfred. I also tried with Ubuntu 15.04 but it does not seems to work either. 

Does anyone knows a distro that is already including Linux 4.0 ? I guess this is my best chance now.

---

### Post by JGrossholtz on 2015-04-25
Hello again.

I still was not able to install any Linux distro on my early 2015 MBA but I discovered a few things.
- I tried with the newer Fedora 22 beta3, it includes a linux 4.0 rc5 kernel. It's not working either.
- As I'm learning a bit how to use OSX I found the system informations menu and saw an NVMExpress entry in there.

It appears that NVMExpress (NVMe) is replacing the Sata bus for SSD. I've also read online that NVMe is used for the first time on the Macbook air (and on the Macbook) for this early 2015 product update.

Back on a Linux live USB I cannot see any NVMe entry on dmesg. According to this interesting intel forum entry :[https://communities.intel.com/community/itpeernetwork/blog/2014/10/10/finding-your-new-intel-ssd-for-pcie-think-nvme-not-scsi](https://communities.intel.com/community/itpeernetwork/blog/2014/10/10/finding-your-new-intel-ssd-for-pcie-think-nvme-not-scsi) I should find nvme devices in /dev (no longer sdX devices !!). But I can not see anything like this.

Under OSX the SSD controler is called "APPLE SSD AP0128H" where could I find support for it ?

So if anyone has been able to install any Linux distro to the new macbook air or macbook could you please post here the outputs from the following commands :
- cat /proc/version
- dmesg
- ls -la /dev
- lsmod 


Thank you !!

---

### Post by alexx-todorov on 2015-05-02
Hi Julien,
I have successfully installed a RHEL 7.1 distro on MacBook Air 13" (early 2015) model. My hardware specs are now published on my blog:
[http://atodorov.org/blog/2015/04/26/installing-red-hat-enterprise-linux-7-on-macbook-air-2015/](http://atodorov.org/blog/2015/04/26/installing-red-hat-enterprise-linux-7-on-macbook-air-2015/)

I've also tried with Fedora 22 Beta and didn't have nay problems wrt. SSD disk.


What I see is different is that my disk controller is:
04:00.0 SATA controller: Samsung Electronics Co Ltd Device a801 (rev 01)

What comes to mind is that you're missing drivers for the 
04:00.0 Mass storage controller: Apple Inc. Device 2001 (rev 01)

Another thing which you also mention is the NVMe bus, which may not be working on Linux.

I don't think the issue is related to having an OS X partition. At least you should be able to see the disk and not read any file systems if that was the case.

Also try booting without reFIND or anything like that. Modern Linux distros support uEFI boot.

---

### Post by andre.willkowsky on 2015-12-08
Hi all,
i had the same problem with my macbook air 11", early 2015. With ubuntu 15.10 no ssd was found.

# lspci | grep storage
04:00.0 Mass storage controller: Apple Inc. PCI Express SSD (rev 01)

I could fix it by installing a linux kernel of version 4.4

uname -a
Linux andre-MacBookAir 4.4.0-040400rc4-generic #201512061930 SMP Mon Dec 7 00:32:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1979251")
fdisk -l then reports
Disk /dev/nvme0n1: 233,8 GiB, 251000193024 bytes, 61279344 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 7C916D8B-D187-44D7-A16F-F26EF8265AB4

Device            Start      End  Sectors   Size Type
/dev/nvme0n1p1        6    76805    76800   300M EFI System
/dev/nvme0n1p2    76806 16791250 16714445  63,8G Apple Core storage
/dev/nvme0n1p3 16791251 16949942   158692 619,9M Apple boot
/dev/nvme0n1p4 16949943 24814262  7864320    30G Linux filesystem
/dev/nvme0n1p5 24814263 35300022 10485760    40G Linux filesystem

the kernel i used is from
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc4-wily/linux-image-4.4.0-040400rc4-generic_4.4.0-040400rc4.201512061930_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc4-wily/linux-image-4.4.0-040400rc4-generic_4.4.0-040400rc4.201512061930_amd64.deb)

i installed it with dpkg -i linux-image-4.4.0-040400rc4-generic_4.4.0-040400rc4.201512061930_amd64.deb

The nvme module is compiled as a module in the package above, so copying the ubuntu installation from usb to /dev/nvme0n1p4 results in the same problem (missing ssd) after boot, but i think this can be fixed by providing the nvme module in the initrd ramdisk or build a the kernel with nvme support compiled in.

Greetings
Andre

---

### Post by ChrisHartley on 2016-02-02
andre.willkowsky - thank you for this, I'm in the same situation and you've put me on what I think is the right track for my 2015 11" MacbookAir (7,1). I installed regular 15.10 on a USB drive, upgraded the kernel to 4.4-rc8 from the Kernel Mainline PPA, rebooted still on USB with the new kernel and the SSD is now visible. I re-partitioned the SSD (dual booting with OSX) and used debootstrap to install on the new partition via chroot. I installed the same 4.4-rc8 kernel in the chrooted system, set up /etc/fstab to mount the OSX EFI partition as /boot/efi, installed grub-efi and ran update-grub. Tried to reboot but it looks like the nvm module isn't included in initrd so the kernel couldn't see the root fs on the SSD. Next step, like you referenced in your post, is to add nvm to /etc/initramfs-tools/modules and rerun update-initramfs. I believe this will, at long last, give me a working Linux install on my 2015 Macbook Air. 

Probably when 16.04 is released with 4.4 included by default all this will be unnecessary, as long as the maintainers include nvm in the kernel or in initrd.

---

