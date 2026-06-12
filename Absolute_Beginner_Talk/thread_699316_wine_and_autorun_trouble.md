---
title: "wine and autorun trouble"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by fiestytom on 2008-02-17
i'm trying to run an autorun.exe file in the terminal with wine, and all i get is debugging messages...please help!!!

the messages are as follows:{

```
tom4@ubuntu:~$ wine /home/tom4/desktop/OBD2Scan/autorun.exe
fixme:shdocvw:PersistStreamInit_InitNew (0x16e818)
fixme:shdocvw:WebBrowser_QueryInterface (0x16e818)->({376bd3aa-3845-101b-84ed-08002b2ec713} 0x484210) interface not supported
fixme:shdocvw:OleControl_OnAmbientPropertyChange Unknown dispID -1
fixme:shdocvw:WebBrowser_get_Application (0x16e818)->(0x33f668)
fixme:shdocvw:OleObject_Close (0x16e818)->(1)
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b842690 (thread 0016), starting debugger...
First chance exception: 0xc0000025 in 32-bit code (0x7bc30d6c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc30d6c ESP:0033f454 EBP:0033f4b8 EFLAGS:00000282(   - 00      - -IS1)
 EAX:0033f460 EBX:7bc7b550 ECX:00110020 EDX:0033f838
 ESI:0033f838 EDI:0033f4c4
Stack dump:
0x0033f454:  00000001 7b8b9900 7b820000 c0000025
0x0033f464:  00000001 0033f838 0409fd7c 00000000
0x0033f474:  7b8b9928 7bc7b550 00000003 7b8b6640
0x0033f484:  0033f4f4 7bc4b130 00000000 00000001
0x0033f494:  00000002 0033f4e4 00000409 00000001
0x0033f4a4:  0409ebbc 00000000 7bc3a829 7bc30d20
Backtrace:
=>1 0x7bc30d6c __regs_RtlRaiseException+0x4c() in ntdll (0x0033f4b8)
  2 0x7bc68183 in ntdll (+0x58183) (0x0033f814)
  3 0x7bc30356 RtlRaiseException+0x6() in ntdll (0x0033f88c)
  4 0x0044744a in autorun (+0x4744a) (0x0033f8e4)
  5 0x0044747d in autorun (+0x4747d) (0x0033f92c)
  6 0x0044a555 in autorun (+0x4a555) (0x0033f96c)
  7 0x00451455 in autorun (+0x51455) (0x0033f998)
  8 0x00410ffc in autorun (+0x10ffc) (0x0033f9c4)
  9 0x0041122a in autorun (+0x1122a) (0x0033fa18)
  10 0x00411476 in autorun (+0x11476) (0x0033fa44)
  11 0x004113e4 in autorun (+0x113e4) (0x0033fa54)
  12 0x00413416 in autorun (+0x13416) (0x0033fa84)
  13 0x00411295 in autorun (+0x11295) (0x0033fae0)
  14 0x00411476 in autorun (+0x11476) (0x0033fb0c)
  15 0x004113b5 in autorun (+0x113b5) (0x0033fb28)
  16 0x00413416 in autorun (+0x13416) (0x0033fb58)
  17 0x0043b8e2 in autorun (+0x3b8e2) (0x0033fb78)
  18 0x004121e0 in autorun (+0x121e0) (0x0033fbe8)
  19 0x0040fe17 in autorun (+0xfe17) (0x0033fc08)
  20 0x0040dd14 in autorun (+0xdd14) (0x0033fc2c)
  21 0x0040debe in autorun (+0xdebe) (0x0033fd4c)
  22 0x0040df4f in autorun (+0xdf4f) (0x0033fd7c)
  23 0x0043b29e in autorun (+0x3b29e) (0x0033fed0)
  24 0x00442278 in autorun (+0x42278) (0x0033fef4)
  25 0x00457ecd in autorun (+0x57ecd) (0x0033ff08)
  26 0x7b87221e in kernel32 (+0x5221e) (0x0033ffe8)
  27 0xb7e12897 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc30d6c __regs_RtlRaiseException+0x4c in ntdll: subl $4,%esp
Modules:
Module  Address                 Debug info      Name (76 modules)
PE      400000-479000   Export          autorun
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Export          ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e284000-7e2be000       Deferred        shdocvw<elf>
  \-PE  7e290000-7e2be000       \               shdocvw
ELF     7e2be000-7e2d2000       Deferred        olepro32<elf>
  \-PE  7e2c0000-7e2d2000       \               olepro32
ELF     7e2eb000-7e31d000       Deferred        uxtheme<elf>
  \-PE  7e2f0000-7e31d000       \               uxtheme
ELF     7e31f000-7e324000       Deferred        libxfixes.so.3
ELF     7e324000-7e32d000       Deferred        libxcursor.so.1
ELF     7e32d000-7e34a000       Deferred        imm32<elf>
  \-PE  7e330000-7e34a000       \               imm32
ELF     7e34a000-7e350000       Deferred        libxrandr.so.2
ELF     7e350000-7e358000       Deferred        libxrender.so.1
ELF     7e358000-7e35b000       Deferred        libxinerama.so.1
ELF     7e35b000-7e364000       Deferred        libdrm.so.2
ELF     7e364000-7e3c4000       Deferred        libgl.so.1
ELF     7e3c4000-7e3c9000       Deferred        libxdmcp.so.6
ELF     7e3c9000-7e4ba000       Deferred        libx11.so.6
ELF     7e4ba000-7e4c8000       Deferred        libxext.so.6
ELF     7e4c8000-7e4cd000       Deferred        libxxf86vm.so.1
ELF     7e4cd000-7e4e5000       Deferred        libice.so.6
ELF     7e4e5000-7e4ee000       Deferred        libsm.so.6
ELF     7e4ee000-7e57c000       Deferred        winex11<elf>
  \-PE  7e500000-7e57c000       \               winex11
ELF     7e5f5000-7e615000       Deferred        libexpat.so.1
ELF     7e615000-7e640000       Deferred        libfontconfig.so.1
ELF     7e640000-7e654000       Deferred        libz.so.1
ELF     7e654000-7e6bf000       Deferred        libfreetype.so.6
ELF     7e6bf000-7e6d3000       Deferred        lz32<elf>
  \-PE  7e6d0000-7e6d3000       \               lz32
ELF     7e6d3000-7e6ec000       Deferred        version<elf>
  \-PE  7e6e0000-7e6ec000       \               version
ELF     7e6ec000-7e70b000       Deferred        mpr<elf>
  \-PE  7e6f0000-7e70b000       \               mpr
ELF     7e70b000-7e753000       Deferred        wininet<elf>
  \-PE  7e720000-7e753000       \               wininet
ELF     7e753000-7e789000       Deferred        urlmon<elf>
  \-PE  7e760000-7e789000       \               urlmon
ELF     7e789000-7e7e2000       Deferred        shlwapi<elf>
  \-PE  7e7a0000-7e7e2000       \               shlwapi
ELF     7e7e2000-7e8d7000       Deferred        shell32<elf>
  \-PE  7e7f0000-7e8d7000       \               shell32
ELF     7e8d7000-7e972000       Deferred        oleaut32<elf>
  \-PE  7e8f0000-7e972000       \               oleaut32
ELF     7e972000-7e985000       Deferred        libresolv.so.2
ELF     7e985000-7e9a3000       Deferred        iphlpapi<elf>
  \-PE  7e990000-7e9a3000       \               iphlpapi
ELF     7e9a3000-7e9f8000       Deferred        rpcrt4<elf>
  \-PE  7e9b0000-7e9f8000       \               rpcrt4
ELF     7e9f8000-7ea92000       Deferred        ole32<elf>
  \-PE  7ea10000-7ea92000       \               ole32
ELF     7ea92000-7ea9e000       Deferred        libgcc_s.so.1
ELF     7ea9e000-7eaa1000       Deferred        libxau.so.6
ELF     7eb94000-7ec51000       Deferred        gdi32<elf>
  \-PE  7ebb0000-7ec51000       \               gdi32
ELF     7ec51000-7ed8d000       Deferred        user32<elf>
  \-PE  7ec70000-7ed8d000       \               user32
ELF     7ed8d000-7ee49000       Deferred        comctl32<elf>
  \-PE  7eda0000-7ee49000       \               comctl32
ELF     7ee49000-7ee8f000       Deferred        advapi32<elf>
  \-PE  7ee60000-7ee8f000       \               advapi32
ELF     7efa1000-7efac000       Deferred        libnss_files.so.2
ELF     7efac000-7efb6000       Deferred        libnss_nis.so.2
ELF     7efb6000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff4000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ca3000-b7ca7000       Deferred        libdl.so.2
ELF     b7ca7000-b7de8000       Deferred        libc.so.6
ELF     b7de8000-b7dff000       Deferred        libpthread.so.0
ELF     b7e0b000-b7f1c000       Export          libwine.so.1
ELF     b7f1e000-b7f39000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000015 (D) Z:\home\tom4\desktop\OBD2Scan\autorun.exe
        00000016    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000009    0
tom4@ubuntu:~$ 

```
}
iv'e tried to install gecko, and i tested it with wine iexplore and it works...

i'm a noob, and have been trying at this for four hours already!!!!

i would be very grateful for any help!

thanx

---

### Post by Flyingjester on 2008-02-17
what app are you trying to get to run?

---

