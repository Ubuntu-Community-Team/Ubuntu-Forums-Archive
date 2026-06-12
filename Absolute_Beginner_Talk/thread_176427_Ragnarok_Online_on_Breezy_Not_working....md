---
title: "Ragnarok Online on Breezy? Not working..."
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Raavea on 2006-05-14
Okies, so I used automatix to install wine, I ran wincfg.

 Then I attempted to install kro-Sakray. That ran mostly okay, I think.
 Then I installed the AnimaRO patch, to play on their server.

 I got this, but I don't have the stuff it said after installing sakray - it was something about trying to read "" and kde packages and fixme, that much I recall;
```
aavea@bernardette:~/Desktop$ wine aminaro.exe
fixme:advapi:CheckTokenMembership ((nil) 0x7fdbb118 0x7faefe1c) stub!
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\unins000.exe") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\adata.grf") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\allow.txt") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\AnimaExe.exe") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\AnimaPatch.exe") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\AnimaRO.exe") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\AnimaRO.url") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\apatch.inf") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\binkw32.dll") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\cps.dll") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\foxdye.ini") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\granny2.dll") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\ijl15.dll") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\Mp3dec.asi") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\Mss32.dll") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\Mssfast.m3d") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\npkcrypt.dll") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\npkcusb.sys") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\npkpdb.dll") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\patch.txt") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\pclient.dll") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\pclient.ini") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\pclient2.dll") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\sakray.exe") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\Setup.exe") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\spatch.inf") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\PatchClient\\beginner.bmp") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\PatchClient\\center.bmp") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\PatchClient\\exit.bmp") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\PatchClient\\home.bmp") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\PatchClient\\skin.bmp") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\PatchClient\\start.bmp") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\PatchClient\\Thumbs.db") stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Gravity\\RO\\PatchClient\\withgm.bmp") stub
raavea@bernardette:~/Desktop$ wine: Unhandled page fault on read access to 0x0040160f at address 0x40160f (thread 000f), starting debugger...
WineDbg starting on pid 0xe
Unhandled exception: page fault on read access to 0x0040160f in 32-bit code (0x0040160f).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:0040160f ESP:7faefe74 EBP:7faeff08 EFLAGS:00010206(   - 00      - RIP1)
 EAX:0040160f EBX:7fce2b44 ECX:7fce2b44 EDX:004168c2
 ESI:0041d004 EDI:7beff4e0
Stack dump:
0x7faefe74:  00411ebe 00000000 00411dec 0041d000
0x7faefe84:  0041d058 0041d05c 0041d070 00411616
0x7faefe94:  7beff4e0 0041157e 7fce2b44 c0000005
0x7faefea4:  00180016 7fec2c00 7fce2b44 0041157e
0x7faefeb4:  7beff4e0 7faefed8 7fca0364 7fec2c00
0x7faefec4:  00000000 00000000 0000000b 00000000
Backtrace:
=>1 0x0040160f in animapatch (+0x160f) (0x0040160f)
  2 0x7fcad01f in kernel32 (+0x4d01f) (0x7fcad01f)
  3 0xb7eec637 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7eec637)
0x0040160f: testb       $0x1,0x00422cd8
Modules:
Module  Address                 Debug info      Name (78 modules)
PE      0x00400000-0042a000     Export          animapatch
PE      0x21100000-2115d000     Deferred        mss32
ELF     0x7be82000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7be90000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7ddee000-7de05000     Deferred        msacm32<elf>
  \-PE  0x7ddf0000-7de05000     \               msacm32
ELF     0x7de05000-7de49000     Deferred        wineoss<elf>
  \-PE  0x7de20000-7de49000     \               wineoss
ELF     0x7de49000-7ded0000     Deferred        winmm<elf>
  \-PE  0x7de50000-7ded0000     \               winmm
ELF     0x7e6c9000-7e75c000     Deferred        oleaut32<elf>
  \-PE  0x7e6e0000-7e75c000     \               oleaut32
ELF     0x7e75c000-7e770000     Deferred        olepro32<elf>
  \-PE  0x7e760000-7e770000     \               olepro32
PE      0x7e770000-7e78a000     Deferred        pclient
ELF     0x7e833000-7e864000     Deferred        uxtheme<elf>
  \-PE  0x7e840000-7e864000     \               uxtheme
ELF     0x7e882000-7e88b000     Deferred        libxcursor.so.1
ELF     0x7e88b000-7e8a7000     Deferred        imm32<elf>
  \-PE  0x7e890000-7e8a7000     \               imm32
ELF     0x7e8a7000-7e8c3000     Deferred        ximcp.so.2
ELF     0x7e8c3000-7e8cb000     Deferred        libxrender.so.1
ELF     0x7e8cb000-7e931000     Deferred        libgl.so.1
ELF     0x7e931000-7e9f1000     Deferred        libx11.so.6
ELF     0x7e9f1000-7ea0a000     Deferred        libice.so.6
ELF     0x7ea0a000-7ea89000     Deferred        winex11<elf>
  \-PE  0x7ea20000-7ea89000     \               winex11
ELF     0x7ea89000-7eaa8000     Deferred        libexpat.so.1
ELF     0x7eaa8000-7ead6000     Deferred        libfontconfig.so.1
ELF     0x7ead6000-7eaea000     Deferred        libz.so.1
ELF     0x7eaea000-7eb54000     Deferred        libfreetype.so.6
ELF     0x7eb54000-7ec09000     Deferred        comctl32<elf>
  \-PE  0x7eb60000-7ec09000     \               comctl32
ELF     0x7ec09000-7ecdf000     Deferred        shell32<elf>
  \-PE  0x7ec20000-7ecdf000     \               shell32
ELF     0x7ecdf000-7ecfd000     Deferred        iphlpapi<elf>
  \-PE  0x7ecf0000-7ecfd000     \               iphlpapi
ELF     0x7ecfd000-7ed48000     Deferred        rpcrt4<elf>
  \-PE  0x7ed10000-7ed48000     \               rpcrt4
ELF     0x7ed48000-7edd8000     Deferred        ole32<elf>
  \-PE  0x7ed60000-7edd8000     \               ole32
ELF     0x7edd8000-7ee32000     Deferred        shlwapi<elf>
  \-PE  0x7edf0000-7ee32000     \               shlwapi
ELF     0x7ee32000-7ee70000     Deferred        advapi32<elf>
  \-PE  0x7ee40000-7ee70000     \               advapi32
ELF     0x7ef56000-7f85b000     Deferred        gdi32<elf>
  \-PE  0x7efa0000-7f85b000     \               gdi32
ELF     0x7f85b000-7f97e000     Deferred        user32<elf>
  \-PE  0x7f880000-7f97e000     \               user32
ELF     0x7f97e000-7f99d000     Deferred        mpr<elf>
  \-PE  0x7f990000-7f99d000     \               mpr
ELF     0x7f99d000-7f9e0000     Deferred        wininet<elf>
  \-PE  0x7f9b0000-7f9e0000     \               wininet
ELF     0x7faf3000-7fafa000     Deferred        libdrm.so.1
ELF     0x7fc42000-7fd40000     Export          kernel32<elf>
  \-PE  0x7fc60000-7fd40000     \               kernel32
ELF     0x7fd43000-7fd50000     Deferred        libxext.so.6
ELF     0x7fd53000-7fd57000     Deferred        libxfixes.so.3
ELF     0x7fd57000-7fd5b000     Deferred        libxdmcp.so.6
ELF     0x7fd5b000-7fd60000     Deferred        libxxf86vm.so.1
ELF     0x7fe73000-7fe7e000     Deferred        libgcc_s.so.1
ELF     0x7fe7e000-7fe89000     Deferred        libnss_files.so.2
ELF     0x7fe89000-7fe93000     Deferred        libnss_nis.so.2
ELF     0x7fe93000-7fea9000     Deferred        libnsl.so.1
ELF     0x7fea9000-7feb3000     Deferred        libnss_compat.so.2
ELF     0x7feb3000-7feb6000     Deferred        libxrandr.so.2
ELF     0x7feb6000-7febb000     Deferred        libxxf86dga.so.1
ELF     0x7febb000-7fec2000     Deferred        libsm.so.6
ELF     0x7fec4000-7fec6000     Deferred        xlcutf8load.so.2
ELF     0x7fec6000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7d93000-b7d97000     Deferred        libdl.so.2
ELF     0xb7d97000-b7ec5000     Deferred        libc.so.6
ELF     0xb7ec5000-b7ed8000     Deferred        libpthread.so.0
ELF     0xb7ed8000-b7edb000     Deferred        libxau.so.6
ELF     0xb7ee7000-b7f01000     Export          libwine.so.1
ELF     0xb7f03000-b7f19000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e (D) C:\Gravity\RO\AnimaPatch.exe
        00000011    0
        00000010    0
        0000000f    0 <==
0000000a
        0000000b    0

```

What's going wrong, anyone...?

And how do I uninstall them if all else fails. I installed to C: 'cause it was in the list so I thought it would work (I have a c: which also has ubuntu on it...) But I have an inkling that this is the problem..

---

