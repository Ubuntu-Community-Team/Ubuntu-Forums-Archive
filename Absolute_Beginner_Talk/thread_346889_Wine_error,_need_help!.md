---
title: "Wine error, need help!"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Copperteeth on 2007-01-26
hello, i was going to install steam so i can play counterstike (i know how to make it work so no problems there) and since i reformatted i had to install wine again. Anyway i went to run winecfg and i am returned this message in terminal:

```
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7db35c7 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7db35c7).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7db35c7 ESP:0033ed98 EBP:0033edc8 EFLAGS:00210257(   - 00     RIZAP1C)
 EAX:00000047 EBX:7e57d53c ECX:7e401f13 EDX:00000000
 ESI:00000047 EDI:7e575859
Stack dump:
0x0033ed98:  5f5f09c8 7e401eff 7e5751b2 7e401e60
0x0033eda8:  0033edc8 7e5435d4 7e401e60 7e575243
0x0033edb8:  7e544afd 7e57d53c 7e5751b2 7e401e60
0x0033edc8:  0033ee48 7e545636 00000000 7e575859
0x0033edd8:  0033ee34 7e57507c 00000000 7c01cf28
0x0033ede8:  00000050 00000048 7c01f4d8 7c01e440
Backtrace:
=>1 0xb7db35c7 strstr+0x27() in libc.so.6 (0x0033edc8)
  2 0x7e545636 in winex11 (+0x35636) (0x0033ee48)
  3 0x7e5459c6 X11DRV_setup_opengl_visual+0x66() in winex11 (0x0033eed8)
  4 0x7e559fdf in winex11 (+0x49fdf) (0x0033f028)
  5 0x7e56a6b3 in winex11 (+0x5a6b3) (0x0033f048)
  6 0x7bc37de5 call_dll_entry_point+0x15() in ntdll (0x0033f068)
  7 0x7bc390dc in ntdll (+0x290dc) (0x0033f118)
  8 0x7bc3957d in ntdll (+0x2957d) (0x0033f158)
  9 0x7bc3b487 LdrLoadDll+0x87() in ntdll (0x0033f188)
  10 0x7b861aeb in kernel32 (+0x41aeb) (0x0033f3d8)
  11 0x7b861d00 LoadLibraryExW+0x50() in kernel32 (0x0033f408)
  12 0x7b861e23 LoadLibraryExA+0x43() in kernel32 (0x0033f428)
  13 0x7b861e5d LoadLibraryA+0x2d() in kernel32 (0x0033f448)
  14 0x7e9bcbc0 DRIVER_load_driver+0x1c0() in gdi32 (0x0033f5b8)
  15 0x7e9b85d0 CreateDCW+0x60() in gdi32 (0x0033f868)
  16 0x7ea81bd0 CreateIconFromResourceEx+0x420() in user32 (0x0033f908)
  17 0x7ea82567 in user32 (+0x32567) (0x0033f968)
  18 0x7ea82aab LoadImageW+0x3fb() in user32 (0x0033fa08)
  19 0x7ea83196 LoadImageA+0x56() in user32 (0x0033fae8)
  20 0x7ea83434 LoadCursorA+0x44() in user32 (0x0033fb18)
  21 0x7ea7920f in user32 (+0x2920f) (0x0033fb38)
  22 0x7ea7925d CLASS_RegisterBuiltinClasses+0x1d() in user32 (0x0033fb48)
  23 0x7eaed3f2 in user32 (+0x9d3f2) (0x0033fbc8)
  24 0x7eb01343 in user32 (+0xb1343) (0x0033fbe8)
  25 0x7bc37de5 call_dll_entry_point+0x15() in ntdll (0x0033fc08)
  26 0x7bc390dc in ntdll (+0x290dc) (0x0033fcb8)
  27 0x7bc3957d in ntdll (+0x2957d) (0x0033fcf8)
  28 0x7bc394c2 in ntdll (+0x294c2) (0x0033fd38)
  29 0x7bc394c2 in ntdll (+0x294c2) (0x0033fd78)
  30 0x7bc394c2 in ntdll (+0x294c2) (0x0033fdb8)
  31 0x7bc394c2 in ntdll (+0x294c2) (0x0033fdf8)
  32 0x7bc394c2 in ntdll (+0x294c2) (0x0033fe38)
  33 0x7bc3c131 LdrInitializeThunk+0x371() in ntdll (0x0033ff08)
  34 0x7b87037a in kernel32 (+0x5037a) (0x0033ffe8)
  35 0xb7ea6587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xb7db35c7 strstr+0x27 in libc.so.6: movzbl     0x0(%edx),%eax
Modules:
Module  Address                 Debug info      Name (61 modules)
ELF     7b800000-7b91c000       Export          kernel32<elf>
  \-PE  7b820000-7b91c000       \               kernel32
ELF     7bc00000-7bc83000       Export          ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d9b8000-7d9c1000       Deferred        librt.so.1
ELF     7da8c000-7e36b000       Deferred        fglrx_dri.so
ELF     7e36b000-7e40b000       Deferred        libgl.so.1
ELF     7e40b000-7e4d4000       Deferred        libx11.so.6
ELF     7e4d4000-7e4e1000       Deferred        libxext.so.6
ELF     7e4e1000-7e4f9000       Deferred        libice.so.6
ELF     7e4f9000-7e586000       Export          winex11<elf>
  \-PE  7e510000-7e586000       \               winex11
ELF     7e586000-7e5a4000       Deferred        libexpat.so.1
ELF     7e5a4000-7e5d3000       Deferred        libfontconfig.so.1
ELF     7e5d3000-7e5e7000       Deferred        libz.so.1
ELF     7e5e7000-7e651000       Deferred        libfreetype.so.6
ELF     7e651000-7e683000       Deferred        uxtheme<elf>
  \-PE  7e660000-7e683000       \               uxtheme
ELF     7e683000-7e711000       Deferred        winmm<elf>
  \-PE  7e690000-7e711000       \               winmm
ELF     7e711000-7e743000       Deferred        winspool<elf>
  \-PE  7e720000-7e743000       \               winspool
ELF     7e743000-7e803000       Deferred        comctl32<elf>
  \-PE  7e750000-7e803000       \               comctl32
ELF     7e803000-7e816000       Deferred        libresolv.so.2
ELF     7e816000-7e834000       Deferred        iphlpapi<elf>
  \-PE  7e820000-7e834000       \               iphlpapi
ELF     7e834000-7e888000       Deferred        rpcrt4<elf>
  \-PE  7e840000-7e888000       \               rpcrt4
ELF     7e888000-7e893000       Deferred        libgcc_s.so.1
ELF     7e896000-7e89b000       Deferred        libxdmcp.so.6
ELF     7e89b000-7e8a4000       Deferred        libsm.so.6
ELF     7e983000-7ea39000       Export          gdi32<elf>
  \-PE  7e9a0000-7ea39000       \               gdi32
ELF     7ea39000-7eb71000       Export          user32<elf>
  \-PE  7ea50000-7eb71000       \               user32
ELF     7eb71000-7ebb7000       Deferred        advapi32<elf>
  \-PE  7eb80000-7ebb7000       \               advapi32
ELF     7ebb7000-7ec50000       Deferred        ole32<elf>
  \-PE  7ebd0000-7ec50000       \               ole32
ELF     7ec50000-7eca8000       Deferred        shlwapi<elf>
  \-PE  7ec60000-7eca8000       \               shlwapi
ELF     7eca8000-7ed9a000       Deferred        shell32<elf>
  \-PE  7ecc0000-7ed9a000       \               shell32
ELF     7ed9a000-7ee3a000       Deferred        comdlg32<elf>
  \-PE  7eda0000-7ee3a000       \               comdlg32
ELF     7ee3a000-7ee94000       Deferred        winecfg<elf>
  \-PE  7ee40000-7ee94000       \               winecfg
ELF     7ef9e000-7efa9000       Deferred        libnss_files.so.2
ELF     7efa9000-7efb3000       Deferred        libnss_nis.so.2
ELF     7efb3000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7efef000       Deferred        libm.so.6
ELF     7efef000-7eff2000       Deferred        libxau.so.6
ELF     7eff2000-7eff7000       Deferred        libxxf86vm.so.1
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d42000-b7d46000       Deferred        libdl.so.2
ELF     b7d46000-b7e7a000       Export          libc.so.6
ELF     b7e7b000-b7e8e000       Deferred        libpthread.so.0
ELF     b7e9f000-b7fb0000       Export          libwine.so.1
ELF     b7fb2000-b7fcd000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\winecfg.exe
        00000009    0 <==

```

to make a long story short, i cant run .exe files and i cant run winecfg to setup wine so it will work. Any help?

---

