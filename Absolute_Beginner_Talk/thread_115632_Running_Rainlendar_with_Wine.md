---
title: "Running Rainlendar with Wine"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by NittanyLionTX on 2006-01-10
Hey all, I am extremely new to Linux and Ubuntu.  I've been trying to install Wine and get a Calendar program called Rainlendar up and running on my computer.  I think I have installed wine correctly, but I still can't get Rainlendar to work.  Instead, I keep receiving this error message in terminal:

joseph@ubuntu:~$ wine "C:\Program Files\Rainlendar\Rainlendar.exe"
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\Rainlendar\\Rainlendar.dll") not found
err:module:import_dll Library Rainlendar.dll (which is needed by L"C:\\Program Files\\Rainlendar\\Rainlendar.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Rainlendar\\Rainlendar.exe" failed, status c0000135

and I'm not really sure what that means, or what I can do about it.

P.S. Thank you everyone for your help and for developing Ubuntu!!


Alright, since looking over the error I realized I was missing a .dll file, and os I went and downloaded it.  After moving to my false C: drive's Rainlendar folder, I tried to run Rainlendar again with wine and recieved the following message:

[email]joseph@ubuntu:~/.wine[/email]/drive_c/Program Files/Rainlendar$ wine Rainlendar.exe
wine: Unhandled page fault on read access to 0x33363130 at address 0x33363130 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x33363130 in 32-bit code (0x33363130).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:33363130 ESP:7fb0db94 EBP:30333438 EFLAGS:00010286(   - 00      -RISP1)
 EAX:ffffffff EBX:36343037 ECX:7fb0db1c EDX:7fb0db94
 ESI:38353536 EDI:31363636
Stack dump:
0x7fb0db94:  33383583 30393130 35393436 37383535
0x7fb0dba4:  37303431 35333531 36313539 32313137
0x7fb0dbb4:  38313231 31353337 32333931 38303934
0x7fb0dbc4:  32333133 30393333 34333938 36383633
0x7fb0dbd4:  31383839 38393730 30373733 31343237
0x7fb0dbe4:  35323039 36333136 37303539 34363534
0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
Backtrace:
wine: Unhandled page fault on read access to 0x00000008 at address 0x7fae3637 (thread 000b), starting debugger...
WineDbg starting on pid 0xa
Unhandled exception: page fault on read access to 0x00000008 in 32-bit code (0x7fae3637).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7fae3637 ESP:7fabefd8 EBP:7fabefe8 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000028 EBX:7fb0b12c ECX:00000000 EDX:7fb0bd40
 ESI:00000000 EDI:00000000
Stack dump:
0x7fabefd8:  00000000 7fb0d800 7fb0b12c 7fb0d7e4
0x7fabefe8:  7fabeffc 7faf005a 00000028 00000000
0x7fabeff8:  7fb0b12c 7fabf018 7faf3716 00000000
0x7fabf008:  7fabf858 7fb0b12c 7fabf858 00000000
0x7fabf018:  7fabf90c 7faf3eb5 7fabf0c8 00000000
0x7fabf028:  7fabf0e8 b7e52d89 005c0072 0053004d
0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7fae3637 in winedbg (+0x3637) (0x7fae3637)
  2 0x7faf005a memory_to_linear_addr+0x2a in winedbg (0x7faf005a)
  3 0x7faf3716 in winedbg (+0x13716) (0x7faf3716)
  4 0x7faf3eb5 in winedbg (+0x13eb5) (0x7faf3eb5)
  5 0x7faf4145 stack_backtrace+0x55 in winedbg (0x7faf4145)
  6 0x7faf69a0 in winedbg (+0x169a0) (0x7faf69a0)
  7 0x7faf778e in winedbg (+0x1778e) (0x7faf778e)
  8 0x7faf8483 main+0x3b3 in winedbg (0x7faf8483)
  9 0x7fafcdfa in winedbg (+0x1cdfa) (0x7fafcdfa)
  10 0x7fccdc67 in kernel32 (+0x4dc67) (0x7fccdc67)
  11 0xb7f6fc17 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f6fc17)
0x7fae3637: movl        0x8(%esi),%eax
Modules:
Module  Address                 Debug info      Name (24 modules)
ELF     0x7be8c000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7f922000-7f95e000     Deferred        advapi32<elf>
  \-PE  0x7f930000-7f95e000     \               advapi32
ELF     0x7f95e000-7f973000     Deferred        psapi<elf>
  \-PE  0x7f960000-7f973000     \               psapi
ELF     0x7f973000-7f9b0000     Deferred        dbghelp<elf>
  \-PE  0x7f980000-7f9b0000     \               dbghelp
ELF     0x7facc000-7fb10000     Export          winedbg<elf>
  \-PE  0x7fae0000-7fb10000     \               winedbg
ELF     0x7fc64000-7fd60000     Export          kernel32<elf>
  \-PE  0x7fc80000-7fd60000     \               kernel32
ELF     0x7fe83000-7fe8d000     Deferred        libnss_files.so.2
ELF     0x7fe8d000-7fe96000     Deferred        libnss_nis.so.2
ELF     0x7fe96000-7feab000     Deferred        libnsl.so.1
ELF     0x7feab000-7feb4000     Deferred        libnss_compat.so.2
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7e27000-b7e2a000     Deferred        libdl.so.2
ELF     0xb7e2a000-b7f58000     Deferred        libc.so.6
ELF     0xb7f59000-b7f6b000     Deferred        libpthread.so.0
ELF     0xb7f6b000-b7f85000     Export          libwine.so.1
ELF     0xb7f98000-b7fae000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) C:\windows\system\winedbg.exe
        0000000b    0 <==
00000008
        00000009    0
WineDbg terminated on pid 0xa
[email]joseph@ubuntu:~/.wine[/email]/drive_c/Program Files/Rainlendar$ clear

[email]joseph@ubuntu:~/.wine[/email]/drive_c/Program Files/Rainlendar$ wine Rainlendar.exe
wine: Unhandled page fault on write access to 0x9ba99dc2 at address 0x7feea999 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on write access to 0x9ba99dc2 in 32-bit code (0x7feea999).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7feea999 ESP:7fb0da04 EBP:7fb0da68 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000032 EBX:7ffdfad8 ECX:0000024e EDX:7ff9f0a0
 ESI:7fb0db1c EDI:9ba99da4
Stack dump:
0x7fb0da04:  7fb0db1c 7fb0db1c 7fb0db1c 7fb0dd6b
0x7fb0da14:  ffffffff 7fb0db1c ffffffff 00000000
0x7fb0da24:  00000000 00000000 00000000 00000000
0x7fb0da34:  1007131d 00000000 7e9967b5 7f000000
0x7fb0da44:  00000000 7fdd2310 00000000 7e994080
0x7fb0da54:  100632a9 ffffffff 7fd12600 0000024e
0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7feea999 wine_cp_mbstowcs+0x2d9 in libwine_unicode.so.1 (0x7feea999)
  2 0x7fccb18a MultiByteToWideChar+0x11a in kernel32 (0x7fccb18a)
  3 0x7e9a584e in msvcrt (+0x2584e) (0x7e9a584e)
  4 0x7e9a7e71 in msvcrt (+0x27e71) (0x7e9a7e71)
0x7feea999 wine_cp_mbstowcs+0x2d9 in libwine_unicode.so.1: movw %ax,0x1e(%edi)
Modules:
Module  Address                 Debug info      Name (94 modules)
PE      0x00400000-0041d000     Deferred        rainlendar
PE      0x780c0000-78121000     Deferred        msvcp60
ELF     0x7be8c000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e2f5000-7e341000     Deferred        libgcrypt.so.11
ELF     0x7e341000-7e3a3000     Deferred        libgnutls.so.11
ELF     0x7e3a3000-7e3c0000     Deferred        libcups.so.2
ELF     0x7e46b000-7e49b000     Deferred        uxtheme<elf>
  \-PE  0x7e470000-7e49b000     \               uxtheme
ELF     0x7e49b000-7e4b0000     Deferred        midimap<elf>
  \-PE  0x7e4a0000-7e4b0000     \               midimap
ELF     0x7e5c0000-7e5c4000     Deferred        libgpg-error.so.0
ELF     0x7e5c4000-7e5e6000     Deferred        msacm32<elf>
  \-PE  0x7e5d0000-7e5e6000     \               msacm32
ELF     0x7e5e6000-7e5fd000     Deferred        msacm<elf>
  \-PE  0x7e5f0000-7e5fd000     \               msacm
ELF     0x7e5fd000-7e63f000     Deferred        wineoss<elf>
  \-PE  0x7e610000-7e63f000     \               wineoss
ELF     0x7e65d000-7e666000     Deferred        libxcursor.so.1
ELF     0x7e666000-7e676000     Deferred        libtasn1.so.2
ELF     0x7e676000-7e691000     Deferred        imm32<elf>
  \-PE  0x7e680000-7e691000     \               imm32
ELF     0x7e691000-7e6ad000     Deferred        ximcp.so.2
ELF     0x7e6ad000-7e6b5000     Deferred        libxrender.so.1
ELF     0x7e6b5000-7e6bc000     Deferred        libdrm.so.1
ELF     0x7e6bc000-7e722000     Deferred        libgl.so.1
ELF     0x7e722000-7e7e2000     Deferred        libx11.so.6
ELF     0x7e7e2000-7e7ef000     Deferred        libxext.so.6
ELF     0x7e7ef000-7e808000     Deferred        libice.so.6
ELF     0x7e808000-7e885000     Deferred        winex11<elf>
  \-PE  0x7e820000-7e885000     \               winex11
ELF     0x7e885000-7e8a4000     Deferred        libexpat.so.1
ELF     0x7e8a4000-7e8d2000     Deferred        libfontconfig.so.1
ELF     0x7e8d2000-7e8e6000     Deferred        libz.so.1
ELF     0x7e8e6000-7e950000     Deferred        libfreetype.so.6
ELF     0x7e961000-7e964000     Deferred        libxrandr.so.2
ELF     0x7e964000-7e969000     Deferred        libxxf86vm.so.1
ELF     0x7e969000-7e9ca000     Export          msvcrt<elf>
  \-PE  0x7e980000-7e9ca000     \               msvcrt
ELF     0x7e9ca000-7ea57000     Deferred        oleaut32<elf>
  \-PE  0x7e9e0000-7ea57000     \               oleaut32
ELF     0x7ea57000-7ea7f000     Deferred        winspool<elf>
  \-PE  0x7ea60000-7ea7f000     \               winspool
ELF     0x7ea7f000-7eb11000     Deferred        comdlg32<elf>
  \-PE  0x7ea90000-7eb11000     \               comdlg32
ELF     0x7eb11000-7ebc0000     Deferred        comctl32<elf>
  \-PE  0x7eb20000-7ebc0000     \               comctl32
ELF     0x7ebc0000-7ec7f000     Deferred        shell32<elf>
  \-PE  0x7ebe0000-7ec7f000     \               shell32
ELF     0x7ec7f000-7ec9d000     Deferred        iphlpapi<elf>
  \-PE  0x7ec90000-7ec9d000     \               iphlpapi
ELF     0x7ec9d000-7ece1000     Deferred        rpcrt4<elf>
  \-PE  0x7ecb0000-7ece1000     \               rpcrt4
ELF     0x7ece1000-7ed67000     Deferred        ole32<elf>
  \-PE  0x7ed00000-7ed67000     \               ole32
ELF     0x7ed67000-7edbc000     Deferred        shlwapi<elf>
  \-PE  0x7ed80000-7edbc000     \               shlwapi
ELF     0x7edbc000-7edda000     Deferred        mpr<elf>
  \-PE  0x7edc0000-7edda000     \               mpr
ELF     0x7edda000-7ee1c000     Deferred        wininet<elf>
  \-PE  0x7ede0000-7ee1c000     \               wininet
ELF     0x7ee1c000-7ee9d000     Deferred        winmm<elf>
  \-PE  0x7ee30000-7ee9d000     \               winmm
ELF     0x7ee9d000-7eeb1000     Deferred        oleacc<elf>
  \-PE  0x7eea0000-7eeb1000     \               oleacc
ELF     0x7eeb1000-7eec5000     Deferred        msimg32<elf>
  \-PE  0x7eec0000-7eec5000     \               msimg32
ELF     0x7eec5000-7ef01000     Deferred        advapi32<elf>
  \-PE  0x7eed0000-7ef01000     \               advapi32
ELF     0x7efe7000-7f8e7000     Deferred        gdi32<elf>
  \-PE  0x7f030000-7f8e7000     \               gdi32
ELF     0x7f8e7000-7fa00000     Deferred        user32<elf>
  \-PE  0x7f900000-7fa00000     \               user32
ELF     0x7fb10000-7fb14000     Deferred        libxdmcp.so.6
ELF     0x7fb14000-7fb19000     Deferred        libxxf86dga.so.1
ELF     0x7fb19000-7fb20000     Deferred        libsm.so.6
ELF     0x7fb21000-7fb2c000     Deferred        libgcc_s.so.1
ELF     0x7fc74000-7fd70000     Export          kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe80000-7fe83000     Deferred        libxau.so.6
ELF     0x7fe83000-7fe8d000     Deferred        libnss_files.so.2
ELF     0x7fe8d000-7fe96000     Deferred        libnss_nis.so.2
ELF     0x7fe96000-7feab000     Deferred        libnsl.so.1
ELF     0x7feab000-7feb4000     Deferred        libnss_compat.so.2
ELF     0x7febe000-7fec2000     Deferred        libxfixes.so.3
ELF     0x7fec2000-7fec4000     Deferred        xlcutf8load.so.2
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Export          libwine_unicode.so.1
ELF     0xb7dfa000-b7dfd000     Deferred        libdl.so.2
ELF     0xb7dfd000-b7f2b000     Deferred        libc.so.6
ELF     0xb7f2c000-b7f3e000     Deferred        libpthread.so.0
ELF     0xb7f3e000-b7f58000     Deferred        libwine.so.1
ELF     0xb7f6b000-b7f81000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Rainlendar\Rainlendar.exe
        00000009    0 <==
WineDbg terminated on pid 0x8


And I have no idea what that means...

---

### Post by SnackySmores on 2006-09-09
great news!! forget about wine, rainy released a rainlendar version for linux! it works as good as the windows version :) 

check out the screenshot

---

