---
title: "Watchtower Library 2006 on Gutsy"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by colossus73 on 2007-09-29
Hi,

I installed and used WT library without ANY problem on Feisty. Then I upgraded to Gutsy and with the same wine version I get a segfault in wtlib.exe:

```
gt[~]$ ./.wt_script.sh 
fixme:font:WineEngCreateFontInstance Untranslated charset 228
fixme:font:WineEngCreateFontInstance Untranslated charset 228
wine: Unhandled page fault on read access to 0x00000000 at address 0x46fbfc (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0046fbfc).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0046fbfc ESP:0033f974 EBP:0033fa00 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:0046fbc0 ECX:00000000 EDX:0033f928
 ESI:00c98640 EDI:00c98640
Stack dump:
0x0033f974:  00000000 006ccd9e 00c98640 00c98640
0x0033f984:  00125908 0033f9a8 00766308 ffffffff
0x0033f994:  0033f9b4 006c4063 006ade74 006d217d
0x0033f9a4:  00c9976c 006d242e 00c99914 0001003c
0x0033f9b4:  00c9976c 006d5293 0001003c 7ed96190
0x0033f9c4:  0033fa14 00000040 0033fab4 0000002e
Backtrace:
=>1 0x0046fbfc in wtlib (+0x6fbfc) (0x0033fa00)
  2 0x006cb27d in mfc71u (+0x2b27d) (0x0033fa20)
  3 0x006cb31c in mfc71u (+0x2b31c) (0x0033fa80)
  4 0x006cb385 in mfc71u (+0x2b385) (0x0033faa0)
  5 0x006cb3c3 in mfc71u (+0x2b3c3) (0x0033facc)
  6 0x7ed9da1a WINPROC_wrapper+0x1a() in user32 (0x0033fafc)
  7 0x7ed9e12e call_window_proc+0x6e(hwnd=<register EDI not in topmost frame>, msg=0x2, wp=0x0, lp=0x0, result=0x33fb6c, arg=0x6cb38a) [/build/buildd/wine-0.9.45/dlls/user32/winproc.c:468] in user32 (0x0033fb3c)
  8 0x7eda3663 CallWindowProcW+0xa3(func=<register ESI not in topmost frame>, hwnd=0x1002a, msg=0x2, wParam=0x0, lParam=0x0) [/build/buildd/wine-0.9.45/dlls/user32/winproc.c:2334] in user32 (0x0033fb7c)
  9 0x33c03215 in wtctls12u (+0x3215) (0x00000000)
0x0046fbfc: movl        0x0(%ecx),%eax
Modules:
Module  Address                 Debug info      Name (132 modules)
PE        340000-  357000       Deferred        uretool12u
PE        370000-  37f000       Deferred        mfc71ita
PE        400000-  69e000       Export          wtlib
PE        6a0000-  7a2000       Export          mfc71u
PE      10000000-1000f000       Deferred        mepstool12u
PE      33000000-3309b000       Deferred        wtutil12u
PE      33200000-33212000       Deferred        wtres12u
PE      33400000-33439000       Deferred        wtmmutil12u
PE      33600000-33617000       Deferred        wtgui12u
PE      33a00000-33a1a000       Deferred        wtdas12u
PE      33c00000-33c4d000       Export          wtctls12u
PE      33e00000-33e13000       Deferred        wtcodec12u
PE      34000000-34025000       Deferred        wtappshare12u
PE      34200000-34299000       Deferred        ureutil12u
PE      34400000-34455000       Deferred        uresearch12u
PE      34800000-348f0000       Deferred        urectls12u
PE      34a00000-34abe000       Deferred        ureboimp12u
PE      34c00000-34c29000       Deferred        urebo12u
PE      34e00000-34e87000       Deferred        ureappshare12u
PE      35000000-35011000       Deferred        ure12u
PE      35400000-35410000       Deferred        mteccodec.wtplug12u
PE      35600000-3572a000       Deferred        mepsres.wtplug12u
PE      35800000-3585a000       Deferred        mepsgui12u
PE      35a00000-35a14000       Deferred        mepsdas.wtplug12u
PE      35c00000-35c86000       Deferred        mepsctls12u
PE      35e00000-35f43000       Deferred        mepscore12u
PE      36000000-36069000       Deferred        mepsbrowser12u
PE      36200000-3625d000       Deferred        mepsappshare12u
PE      5d360000-5d36e000       Deferred        mfc71enu
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
PE      7c3a0000-7c41b000       Deferred        msvcp71
ELF     7c89f000-7c8c6000       Deferred        msvfw32<elf>
  \-PE  7c8b0000-7c8c6000       \               msvfw32
ELF     7ccd1000-7cd17000       Deferred        riched20<elf>
  \-PE  7cce0000-7cd17000       \               riched20
ELF     7cd17000-7cd2b000       Deferred        riched32<elf>
  \-PE  7cd20000-7cd2b000       \               riched32
ELF     7cd2b000-7cd40000       Deferred        midimap<elf>
  \-PE  7cd30000-7cd40000       \               midimap
ELF     7cd40000-7cd67000       Deferred        msacm32<elf>
  \-PE  7cd50000-7cd67000       \               msacm32
ELF     7cd67000-7cd7f000       Deferred        msacm32<elf>
  \-PE  7cd70000-7cd7f000       \               msacm32
ELF     7cd7f000-7cdb9000       Deferred        wineoss<elf>
  \-PE  7cd90000-7cdb9000       \               wineoss
ELF     7cdb9000-7ce0a000       Deferred        libgcrypt.so.11
ELF     7ce0a000-7ce0e000       Deferred        libgpg-error.so.0
ELF     7ce0e000-7ce3c000       Deferred        libcrypt.so.1
ELF     7ce3c000-7ceac000       Deferred        libgnutls.so.13
ELF     7ceac000-7ced1000       Deferred        libk5crypto.so.3
ELF     7ced1000-7cf59000       Deferred        libkrb5.so.3
ELF     7cf59000-7cf82000       Deferred        libgssapi_krb5.so.2
ELF     7cf82000-7cfb7000       Deferred        libcups.so.2
ELF     7d30d000-7d31d000       Deferred        libtasn1.so.3
ELF     7d31d000-7d31f000       Deferred        libkeyutils.so.1
ELF     7d31f000-7d327000       Deferred        libkrb5support.so.0
ELF     7d327000-7d32a000       Deferred        libcom_err.so.2
ELF     7d357000-7d389000       Deferred        uxtheme<elf>
  \-PE  7d360000-7d389000       \               uxtheme
ELF     7d389000-7d38e000       Deferred        libxfixes.so.3
ELF     7d38e000-7d397000       Deferred        libxcursor.so.1
ELF     7d397000-7d39d000       Deferred        libxrandr.so.2
ELF     7d39d000-7d3a5000       Deferred        libxrender.so.1
ELF     7d960000-7d962000       Deferred        libnvidia-tls.so.1
ELF     7d962000-7e1e8000       Deferred        libglcore.so.1
ELF     7e1e8000-7e274000       Deferred        libgl.so.1
ELF     7e274000-7e279000       Deferred        libxdmcp.so.6
ELF     7e279000-7e27c000       Deferred        libxau.so.6
ELF     7e27c000-7e36d000       Deferred        libx11.so.6
ELF     7e36d000-7e37b000       Deferred        libxext.so.6
ELF     7e37b000-7e380000       Deferred        libxxf86vm.so.1
ELF     7e380000-7e398000       Deferred        libice.so.6
ELF     7e398000-7e3a0000       Deferred        libsm.so.6
ELF     7e3ad000-7e438000       Deferred        winex11<elf>
  \-PE  7e3c0000-7e438000       \               winex11
ELF     7e463000-7e483000       Deferred        libexpat.so.1
ELF     7e483000-7e4ae000       Deferred        libfontconfig.so.1
ELF     7e4ae000-7e4c3000       Deferred        libz.so.1
ELF     7e4c3000-7e533000       Deferred        libfreetype.so.6
ELF     7e533000-7e547000       Deferred        lz32<elf>
  \-PE  7e540000-7e547000       \               lz32
ELF     7e547000-7e561000       Deferred        version<elf>
  \-PE  7e550000-7e561000       \               version
ELF     7e561000-7e57e000       Deferred        imm32<elf>
  \-PE  7e570000-7e57e000       \               imm32
ELF     7e57e000-7e61f000       Deferred        ole32<elf>
  \-PE  7e590000-7e61f000       \               ole32
ELF     7e61f000-7e6bd000       Deferred        oleaut32<elf>
  \-PE  7e630000-7e6bd000       \               oleaut32
ELF     7e6bd000-7e74b000       Deferred        winmm<elf>
  \-PE  7e6d0000-7e74b000       \               winmm
ELF     7e74b000-7e780000       Deferred        winspool<elf>
  \-PE  7e750000-7e780000       \               winspool
ELF     7e780000-7e821000       Deferred        comdlg32<elf>
  \-PE  7e790000-7e821000       \               comdlg32
ELF     7e821000-7e834000       Deferred        libresolv.so.2
ELF     7e834000-7e852000       Deferred        iphlpapi<elf>
  \-PE  7e840000-7e852000       \               iphlpapi
ELF     7e852000-7e8ab000       Deferred        rpcrt4<elf>
  \-PE  7e860000-7e8ab000       \               rpcrt4
ELF     7e8ab000-7e969000       Deferred        comctl32<elf>
  \-PE  7e8b0000-7e969000       \               comctl32
ELF     7e969000-7ea6c000       Deferred        shell32<elf>
  \-PE  7e980000-7ea6c000       \               shell32
ELF     7ea6c000-7eac5000       Deferred        shlwapi<elf>
  \-PE  7ea80000-7eac5000       \               shlwapi
ELF     7eac5000-7eb0d000       Deferred        advapi32<elf>
  \-PE  7ead0000-7eb0d000       \               advapi32
ELF     7eb0d000-7eb18000       Deferred        libgcc_s.so.1
ELF     7ec18000-7ecda000       Deferred        gdi32<elf>
  \-PE  7ec30000-7ecda000       \               gdi32
ELF     7ecda000-7ee18000       Dwarf           user32<elf>
  \-PE  7ed00000-7ee18000       \               user32
ELF     7ee18000-7ee38000       Deferred        mpr<elf>
  \-PE  7ee20000-7ee38000       \               mpr
ELF     7ee38000-7ee82000       Deferred        wininet<elf>
  \-PE  7ee40000-7ee82000       \               wininet
ELF     7efa1000-7efac000       Deferred        libnss_files.so.2
ELF     7efac000-7efb6000       Deferred        libnss_nis.so.2
ELF     7efb6000-7efce000       Deferred        libnsl.so.1
ELF     7efce000-7eff3000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d35000-b7d39000       Deferred        libdl.so.2
ELF     b7d39000-b7e83000       Deferred        libc.so.6
ELF     b7e84000-b7e9c000       Deferred        libpthread.so.0
ELF     b7ea9000-b7fbd000       Deferred        libwine.so.1
ELF     b7fbf000-b7fdb000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Watchtower\Watchtower Library 2006\i\wtlib.exe
        00000009    0 <==
gt[~]$ 
```

This is the script wt_script.sh:

```

#!/bin/sh

cd .wine/drive_c/Program\ Files/Watchtower/MEPSCommon
WINEDLLOVERRIDES=comctl32=n,b wine ~/.wine/drive_c/Program\ Files/Watchtower/Watchtower\ Library\ 2006/i/wtlib.exe
gt[~]$

```

Wine version is the same when WT was working: 0.9.45

Does anyone have a clue?

---

