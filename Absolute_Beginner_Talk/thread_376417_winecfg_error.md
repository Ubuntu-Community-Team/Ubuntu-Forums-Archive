---
title: "winecfg error"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by joeblow1102 on 2007-03-04
```
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7d78c53 (thread 0009), starting debugger...
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7cf3c53 (thread 000b), starting debugger...
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7d09c53 (thread 000d), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7d78c53).
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7d09c53).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7d78c53 ESP:0033edac EBP:0033edc8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:b7e3bff4 ECX:00000000 EDX:00000009
 ESI:00000033 EDI:00000000
Stack dump:
0x0033edac:  b7d78975 00000000 7c01b3e0 0033edc8
0x0033edbc:  7e57f53c 00000033 00000000 0033ee48
0x0033edcc:  7e547442 00000000 00000076 7c06d110
0x0033eddc:  00000001 7c01a860 00000000 00000000
0x0033edec:  00000000 7c06d110 7c01b3e0 00000076
0x0033edfc:  0033eefc 0033ee58 0033eef4 0033eed4
Backtrace:
=>1 0xb7d78c53 strlen+0x33() in libc.so.6 (0x0033edc8)
  2 0x7e547442 in winex11 (+0x37442) (0x0033ee48)
  3 0x7e547be0 X11DRV_setup_opengl_visual+0x130() in winex11 (0x0033ef28)
  4 0x7e55c17f in winex11 (+0x4c17f) (0x0033f078)
  5 0x7e56c7c3 in winex11 (+0x5c7c3) (0x0033f098)
  6 0x7bc38055 call_dll_entry_point+0x15() in ntdll (0x0033f0b8)
  7 0x7bc3934c in ntdll (+0x2934c) (0x0033f168)
  8 0x7bc397ed in ntdll (+0x297ed) (0x0033f1a8)
  9 0x7bc3b6f7 LdrLoadDll+0x87() in ntdll (0x0033f1d8)
  10 0x7b8618cb in kernel32 (+0x418cb) (0x0033f428)
  11 0x7b861ae0 LoadLibraryExW+0x50() in kernel32 (0x0033f458)
  12 0x7b861c03 LoadLibraryExA+0x43() in kernel32 (0x0033f478)
  13 0x7b861c3d LoadLibraryA+0x2d() in kernel32 (0x0033f498)
  14 0x7e9bacc0 DRIVER_load_driver+0x1c0() in gdi32 (0x0033f608)
  15 0x7e9b65b0 CreateDCW+0x60() in gdi32 (0x0033f8b8)
  16 0x7ea80e60 CreateIconFromResourceEx+0x420() in user32 (0x0033f958)
  17 0x7ea81877 in user32 (+0x31877) (0x0033f9d8)
  18 0x7ea82b1b LoadImageW+0x3fb() in user32 (0x0033fa78)
  19 0x7ea830b6 LoadImageA+0x56() in user32 (0x0033fb58)
  20 0x7ea835a7 LoadCursorA+0x97() in user32 (0x0033fb88)
  21 0x7ea7824f in user32 (+0x2824f) (0x0033fba8)
  22 0x7ea7829d CLASS_RegisterBuiltinClasses+0x1d() in user32 (0x0033fbb8)
  23 0x7eaecbd2 in user32 (+0x9cbd2) (0x0033fc38)
  24 0x7eb00b23 in user32 (+0xb0b23) (0x0033fc58)
  25 0x7bc38055 call_dll_entry_point+0x15() in ntdll (0x0033fc78)
  26 0x7bc3934c in ntdll (+0x2934c) (0x0033fd28)
  27 0x7bc397ed in ntdll (+0x297ed) (0x0033fd68)
  28 0x7bc39732 in ntdll (+0x29732) (0x0033fda8)
  29 0x7bc39732 in ntdll (+0x29732) (0x0033fde8)
  30 0x7bc39732 in ntdll (+0x29732) (0x0033fe28)
  31 0x7bc39732 in ntdll (+0x29732) (0x0033fe68)
  32 0x7bc39732 in ntdll (+0x29732) (0x0033fea8)
  33 0x7bc3c2ee LdrInitializeThunk+0x2be() in ntdll (0x0033ff08)
  34 0x7b87015a in kernel32 (+0x5015a) (0x0033ffe8)
  35 0xb7e6a5a7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xb7d78c53 strlen+0x33 in libc.so.6: movl       0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (68 modules)
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc94000       Export          ntdll<elf>
  \-PE  7bc10000-7bc94000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c84e000-7c853000       Deferred        libxfixes.so.3
ELF     7c853000-7c85c000       Deferred        libxcursor.so.1
ELF     7c85c000-7c864000       Deferred        libxrender.so.1
ELF     7c864000-7c881000       Deferred        imm32<elf>
  \-PE  7c870000-7c881000       \               imm32
ELF     7c881000-7c89f000       Deferred        ximcp.so.2
ELF     7c89f000-7c8a1000       Deferred        xlcutf8load.so.2
ELF     7d9bc000-7d9c5000       Deferred        librt.so.1
ELF     7da8e000-7e36d000       Deferred        fglrx_dri.so
ELF     7e36d000-7e40d000       Deferred        libgl.so.1
ELF     7e40d000-7e4d6000       Deferred        libx11.so.6
ELF     7e4d6000-7e4e3000       Deferred        libxext.so.6
ELF     7e4e3000-7e4fb000       Deferred        libice.so.6
ELF     7e4fb000-7e588000       Export          winex11<elf>
  \-PE  7e510000-7e588000       \               winex11
ELF     7e588000-7e5a6000       Deferred        libexpat.so.1
ELF     7e5a6000-7e5d5000       Deferred        libfontconfig.so.1
ELF     7e5d5000-7e5e9000       Deferred        libz.so.1
ELF     7e5e9000-7e653000       Deferred        libfreetype.so.6
ELF     7e653000-7e685000       Deferred        uxtheme<elf>
  \-PE  7e660000-7e685000       \               uxtheme
ELF     7e685000-7e713000       Deferred        winmm<elf>
  \-PE  7e690000-7e713000       \               winmm
ELF     7e713000-7e746000       Deferred        winspool<elf>
  \-PE  7e720000-7e746000       \               winspool
ELF     7e746000-7e802000       Deferred        comctl32<elf>
  \-PE  7e750000-7e802000       \               comctl32
ELF     7e802000-7e815000       Deferred        libresolv.so.2
ELF     7e815000-7e833000       Deferred        iphlpapi<elf>
  \-PE  7e820000-7e833000       \               iphlpapi
ELF     7e833000-7e888000       Deferred        rpcrt4<elf>
  \-PE  7e840000-7e888000       \               rpcrt4
ELF     7e888000-7e893000       Deferred        libgcc_s.so.1
ELF     7e894000-7e899000       Deferred        libxdmcp.so.6
ELF     7e899000-7e8a2000       Deferred        libsm.so.6
ELF     7e981000-7ea38000       Export          gdi32<elf>
  \-PE  7e9a0000-7ea38000       \               gdi32
ELF     7ea38000-7eb72000       Export          user32<elf>
  \-PE  7ea50000-7eb72000       \               user32
ELF     7eb72000-7ebb7000       Deferred        advapi32<elf>
  \-PE  7eb80000-7ebb7000       \               advapi32
ELF     7ebb7000-7ec50000       Deferred        ole32<elf>
  \-PE  7ebd0000-7ec50000       \               ole32
ELF     7ec50000-7eca8000       Deferred        shlwapi<elf>
  \-PE  7ec60000-7eca8000       \               shlwapi
ELF     7eca8000-7ed9c000       Deferred        shell32<elf>
  \-PE  7ecc0000-7ed9c000       \               shell32
ELF     7ed9c000-7ee3c000       Deferred        comdlg32<elf>
  \-PE  7eda0000-7ee3c000       \               comdlg32
ELF     7ee3c000-7ee96000       Deferred        winecfg<elf>
  \-PE  7ee40000-7ee96000       \               winecfg
ELF     7efa0000-7efab000       Deferred        libnss_files.so.2
ELF     7efab000-7efb5000       Deferred        libnss_nis.so.2
ELF     7efb5000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff1000       Deferred        libm.so.6
ELF     7eff4000-7eff7000       Deferred        libxau.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d00000-b7d05000       Deferred        libxxf86vm.so.1
ELF     b7d08000-b7d0c000       Deferred        libdl.so.2
ELF     b7d0c000-b7e40000       Export          libc.so.6
ELF     b7e41000-b7e54000       Deferred        libpthread.so.0
ELF     b7e63000-b7f74000       Export          libwine.so.1
ELF     b7f76000-b7f91000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000010 
        00000011    0
0000000c 
        0000000d    0
0000000a 
        0000000b    0
00000008 (D) c:\windows\system32\winecfg.exe
        00000009    0 <==
joeblow1102@Batman-Rulez:~$ Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7d09c53 ESP:0034eeac EBP:0034eec8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:b7dccff4 ECX:00000000 EDX:00000009
 ESI:00000033 EDI:00000000
Stack dump:
0x0034eeac:  b7d09975 00000000 7c0185b8 0034eec8
0x0034eebc:  7ea7c53c 00000033 00000000 0034ef48
0x0034eecc:  7ea44442 00000000 00000076 7c06a090
0x0034eedc:  00000001 7c017bd0 00000000 00000000
0x0034eeec:  00000000 7c06a090 7c0185b8 00000076
0x0034eefc:  0034effc 0034ef58 0034eff4 0034efd4
Backtrace:
=>1 0xb7d09c53 strlen+0x33() in libc.so.6 (0x0034eec8)
  2 0x7ea44442 in winex11 (+0x34442) (0x0034ef48)
  3 0x7ea44be0 X11DRV_setup_opengl_visual+0x130() in winex11 (0x0034f028)
  4 0x7ea5917f in winex11 (+0x4917f) (0x0034f178)
  5 0x7ea697c3 in winex11 (+0x597c3) (0x0034f198)
  6 0x7bc38055 call_dll_entry_point+0x15() in ntdll (0x0034f1b8)
  7 0x7bc3934c in ntdll (+0x2934c) (0x0034f268)
  8 0x7bc397ed in ntdll (+0x297ed) (0x0034f2a8)
  9 0x7bc3b6f7 LdrLoadDll+0x87() in ntdll (0x0034f2d8)
  10 0x7b8618cb in kernel32 (+0x418cb) (0x0034f528)
  11 0x7b861ae0 LoadLibraryExW+0x50() in kernel32 (0x0034f558)
  12 0x7b861c03 LoadLibraryExA+0x43() in kernel32 (0x0034f578)
  13 0x7b861c3d LoadLibraryA+0x2d() in kernel32 (0x0034f598)
  14 0x7ecb8cc0 DRIVER_load_driver+0x1c0() in gdi32 (0x0034f708)
  15 0x7ecb45b0 CreateDCW+0x60() in gdi32 (0x0034f9b8)
  16 0x7ed7ee60 CreateIconFromResourceEx+0x420() in user32 (0x0034fa58)
  17 0x7ed7f877 in user32 (+0x2f877) (0x0034fad8)
  18 0x7ed80b1b LoadImageW+0x3fb() in user32 (0x0034fb78)
  19 0x7ed810b6 LoadImageA+0x56() in user32 (0x0034fc58)
  20 0x7ed815a7 LoadCursorA+0x97() in user32 (0x0034fc88)
  21 0x7ed7624f in user32 (+0x2624f) (0x0034fca8)
  22 0x7ed7629d CLASS_RegisterBuiltinClasses+0x1d() in user32 (0x0034fcb8)
  23 0x7edeabd2 in user32 (+0x9abd2) (0x0034fd38)
  24 0x7edfeb23 in user32 (+0xaeb23) (0x0034fd58)
  25 0x7bc38055 call_dll_entry_point+0x15() in ntdll (0x0034fd78)
  26 0x7bc3934c in ntdll (+0x2934c) (0x0034fe28)
  27 0x7bc397ed in ntdll (+0x297ed) (0x0034fe68)
  28 0x7bc39732 in ntdll (+0x29732) (0x0034fea8)
  29 0x7bc3c2ee LdrInitializeThunk+0x2be() in ntdll (0x0034ff08)
  30 0x7b87015a in kernel32 (+0x5015a) (0x0034ffe8)
  31 0xb7dfb5a7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xb7d09c53 strlen+0x33 in libc.so.6: movl       0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (47 modules)
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc94000       Export          ntdll<elf>
  \-PE  7bc10000-7bc94000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cd4b000-7cd50000       Deferred        libxfixes.so.3
ELF     7cd50000-7cd59000       Deferred        libxcursor.so.1
ELF     7cd59000-7cd61000       Deferred        libxrender.so.1
ELF     7cd61000-7cd7e000       Deferred        imm32<elf>
  \-PE  7cd70000-7cd7e000       \               imm32
ELF     7cd7e000-7cd9c000       Deferred        ximcp.so.2
ELF     7cd9c000-7cd9e000       Deferred        xlcutf8load.so.2
ELF     7deb9000-7dec2000       Deferred        librt.so.1
ELF     7df8b000-7e86a000       Deferred        fglrx_dri.so
ELF     7e86a000-7e90a000       Deferred        libgl.so.1
ELF     7e90a000-7e9d3000       Deferred        libx11.so.6
ELF     7e9d3000-7e9e0000       Deferred        libxext.so.6
ELF     7e9e0000-7e9f8000       Deferred        libice.so.6
ELF     7e9f8000-7ea85000       Export          winex11<elf>
  \-PE  7ea10000-7ea85000       \               winex11
ELF     7ea85000-7eaa3000       Deferred        libexpat.so.1
ELF     7eaa3000-7ead2000       Deferred        libfontconfig.so.1
ELF     7ead2000-7eae6000       Deferred        libz.so.1
ELF     7eae6000-7eb50000       Deferred        libfreetype.so.6
ELF     7eb50000-7eb95000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb95000       \               advapi32
ELF     7eb95000-7eba0000       Deferred        libgcc_s.so.1
ELF     7ec7f000-7ed36000       Export          gdi32<elf>
  \-PE  7ec90000-7ed36000       \               gdi32
ELF     7ed36000-7ee70000       Export          user32<elf>
  \-PE  7ed50000-7ee70000       \               user32
ELF     7ee70000-7ee88000       Deferred        explorer<elf>
  \-PE  7ee80000-7ee88000       \               explorer
ELF     7ee88000-7ee93000       Deferred        libnss_files.so.2
ELF     7ee93000-7eea9000       Deferred        libnsl.so.1
ELF     7eea9000-7eeb2000       Deferred        libnss_compat.so.2
ELF     7eeb3000-7eeb8000       Deferred        libxdmcp.so.6
ELF     7eeb8000-7eec1000       Deferred        libsm.so.6
ELF     7efcb000-7eff1000       Deferred        libm.so.6
ELF     7eff3000-7eff6000       Deferred        libxau.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c91000-b7c96000       Deferred        libxxf86vm.so.1
ELF     b7c99000-b7c9d000       Deferred        libdl.so.2
ELF     b7c9d000-b7dd1000       Export          libc.so.6
ELF     b7dd2000-b7de5000       Deferred        libpthread.so.0
ELF     b7df4000-b7f05000       Export          libwine.so.1
ELF     b7f07000-b7f22000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c (D) c:\windows\system32\explorer.exe
        0000000d    0 <==
0000000a 
        0000000b    0
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7cf3c53).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7cf3c53 ESP:0034eeac EBP:0034eec8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:b7db6ff4 ECX:00000000 EDX:00000009
 ESI:00000033 EDI:00000000
Stack dump:
0x0034eeac:  b7cf3975 00000000 7c0185b8 0034eec8
0x0034eebc:  7ea7c53c 00000033 00000000 0034ef48
0x0034eecc:  7ea44442 00000000 00000076 7c06a090
0x0034eedc:  00000001 7c017bd0 00000000 00000000
0x0034eeec:  00000000 7c06a090 7c0185b8 00000076
0x0034eefc:  0034effc 0034ef58 0034eff4 0034efd4
Backtrace:
=>1 0xb7cf3c53 strlen+0x33() in libc.so.6 (0x0034eec8)
  2 0x7ea44442 in winex11 (+0x34442) (0x0034ef48)
  3 0x7ea44be0 X11DRV_setup_opengl_visual+0x130() in winex11 (0x0034f028)
  4 0x7ea5917f in winex11 (+0x4917f) (0x0034f178)
  5 0x7ea697c3 in winex11 (+0x597c3) (0x0034f198)
  6 0x7bc38055 call_dll_entry_point+0x15() in ntdll (0x0034f1b8)
  7 0x7bc3934c in ntdll (+0x2934c) (0x0034f268)
  8 0x7bc397ed in ntdll (+0x297ed) (0x0034f2a8)
  9 0x7bc3b6f7 LdrLoadDll+0x87() in ntdll (0x0034f2d8)
  10 0x7b8618cb in kernel32 (+0x418cb) (0x0034f528)
  11 0x7b861ae0 LoadLibraryExW+0x50() in kernel32 (0x0034f558)
  12 0x7b861c03 LoadLibraryExA+0x43() in kernel32 (0x0034f578)
  13 0x7b861c3d LoadLibraryA+0x2d() in kernel32 (0x0034f598)
  14 0x7ecb8cc0 DRIVER_load_driver+0x1c0() in gdi32 (0x0034f708)
  15 0x7ecb45b0 CreateDCW+0x60() in gdi32 (0x0034f9b8)
  16 0x7ed7ee60 CreateIconFromResourceEx+0x420() in user32 (0x0034fa58)
  17 0x7ed7f877 in user32 (+0x2f877) (0x0034fad8)
  18 0x7ed80b1b LoadImageW+0x3fb() in user32 (0x0034fb78)
  19 0x7ed810b6 LoadImageA+0x56() in user32 (0x0034fc58)
  20 0x7ed815a7 LoadCursorA+0x97() in user32 (0x0034fc88)
  21 0x7ed7624f in user32 (+0x2624f) (0x0034fca8)
  22 0x7ed7629d CLASS_RegisterBuiltinClasses+0x1d() in user32 (0x0034fcb8)
  23 0x7edeabd2 in user32 (+0x9abd2) (0x0034fd38)
  24 0x7edfeb23 in user32 (+0xaeb23) (0x0034fd58)
  25 0x7bc38055 call_dll_entry_point+0x15() in ntdll (0x0034fd78)
  26 0x7bc3934c in ntdll (+0x2934c) (0x0034fe28)
  27 0x7bc397ed in ntdll (+0x297ed) (0x0034fe68)
  28 0x7bc39732 in ntdll (+0x29732) (0x0034fea8)
  29 0x7bc3c2ee LdrInitializeThunk+0x2be() in ntdll (0x0034ff08)
  30 0x7b87015a in kernel32 (+0x5015a) (0x0034ffe8)
  31 0xb7de55a7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xb7cf3c53 strlen+0x33 in libc.so.6: movl       0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (47 modules)
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc94000       Export          ntdll<elf>
  \-PE  7bc10000-7bc94000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cd46000-7cd4b000       Deferred        libxfixes.so.3
ELF     7cd4b000-7cd54000       Deferred        libxcursor.so.1
ELF     7cd54000-7cd5c000       Deferred        libxrender.so.1
ELF     7cd5c000-7cd79000       Deferred        imm32<elf>
  \-PE  7cd60000-7cd79000       \               imm32
ELF     7cd79000-7cd97000       Deferred        ximcp.so.2
ELF     7cd97000-7cd99000       Deferred        xlcutf8load.so.2
ELF     7deb4000-7debd000       Deferred        librt.so.1
ELF     7df86000-7e865000       Deferred        fglrx_dri.so
ELF     7e865000-7e905000       Deferred        libgl.so.1
ELF     7e905000-7e90a000       Deferred        libxdmcp.so.6
ELF     7e90a000-7e9d3000       Deferred        libx11.so.6
ELF     7e9d3000-7e9e0000       Deferred        libxext.so.6
ELF     7e9e0000-7e9f8000       Deferred        libice.so.6
ELF     7e9f8000-7ea85000       Export          winex11<elf>
  \-PE  7ea10000-7ea85000       \               winex11
ELF     7ea85000-7eaa3000       Deferred        libexpat.so.1
ELF     7eaa3000-7ead2000       Deferred        libfontconfig.so.1
ELF     7ead2000-7eae6000       Deferred        libz.so.1
ELF     7eae6000-7eb50000       Deferred        libfreetype.so.6
ELF     7eb50000-7eb95000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb95000       \               advapi32
ELF     7eb95000-7eba0000       Deferred        libgcc_s.so.1
ELF     7ec7f000-7ed36000       Export          gdi32<elf>
  \-PE  7ec90000-7ed36000       \               gdi32
ELF     7ed36000-7ee70000       Export          user32<elf>
  \-PE  7ed50000-7ee70000       \               user32
ELF     7ee70000-7ee88000       Deferred        explorer<elf>
  \-PE  7ee80000-7ee88000       \               explorer
ELF     7ee88000-7ee93000       Deferred        libnss_files.so.2
ELF     7ee93000-7eea9000       Deferred        libnsl.so.1
ELF     7eea9000-7eeb2000       Deferred        libnss_compat.so.2
ELF     7eeb5000-7eeb8000       Deferred        libxau.so.6
ELF     7eeb8000-7eec1000       Deferred        libsm.so.6
ELF     7efcb000-7eff1000       Deferred        libm.so.6
ELF     7eff1000-7eff6000       Deferred        libxxf86vm.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c83000-b7c87000       Deferred        libdl.so.2
ELF     b7c87000-b7dbb000       Export          libc.so.6
ELF     b7dbc000-b7dcf000       Deferred        libpthread.so.0
ELF     b7dde000-b7eef000       Export          libwine.so.1
ELF     b7ef1000-b7f0c000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) c:\windows\system32\explorer.exe
        0000000b    0 <==


```

Can anybody here help me?  Thanks.

---

### Post by eljalill on 2007-03-11
In case you still need help, you could look here: [http://frankscorner.org/index.php?p=office](http://frankscorner.org/index.php?p=office)
or here:
[http://groups.google.com/group/comp....ws.wine/topics](http://groups.google.com/group/comp....ws.wine/topics) .

Hope you find it there!

---

