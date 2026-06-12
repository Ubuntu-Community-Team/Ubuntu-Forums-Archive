---
title: "Dreamweaver 8 under WINE (Gutsy)"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by kasio on 2007-10-25
Using WINE 0.9.7 in a fresh install of Gutsy, I managed to install Dreamweaver 8 fine.

When I start it from the menu, It loads up the loading screen, gets to 'Initializing Files' and then it closes.

When I run it from the terminal, I get this output:
```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:win:EnumDisplayDevicesW ((null),0,0x34f7b0,0x00000000), stub!
fixme:shell:SHGetFileInfoW set icon to shell size, stub
wine: Call from 0x7b843f50 to unimplemented function shell32.dll.SHGetIconOverlayIndexW, aborting
wine: Unimplemented function shell32.dll.SHGetIconOverlayIndexW called at address 0x7b843f50 (thread 0009), starting debugger...
Unhandled exception: unimplemented function shell32.dll.SHGetIconOverlayIndexW called in 32-bit code (0x7b843fc8).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b843fc8 ESP:0034b924 EBP:0034b988 EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82ee9d EBX:7b8b0888 ECX:00000000 EDX:030d1f50
 ESI:030d1f50 EDI:7e8ae620
Stack dump:
0x0034b924:  0034b9ac 00000008 001440b0 00110014
0x0034b934:  80000100 00000001 00000000 7b843f50
0x0034b944:  00000002 7e907d00 7e908182 0034b9b4
0x0034b954:  0034b984 7bc43151 7bc8c604 00144220
0x0034b964:  000000f0 7bc320df 00000000 7bc8443c
0x0034b974:  0034b984 7bc431e2 7bc8c604 7b8b0888
Backtrace:
=>1 0x7b843fc8 RaiseException+0x78() in kernel32 (0x0034b988)
  2 0x7e907c61 in shell32 (+0x67c61) (0x0034b9b8)
  3 0x7e8ae63b in shell32 (+0xe63b) (0x0034bc04)
  4 0x5a50b517 in fsshext.8.0.0812.00 (+0xb517) (0x0034bc48)
  5 0x5a50ba33 in fsshext.8.0.0812.00 (+0xba33) (0x0034bc5c)
  6 0x5a5090d2 in fsshext.8.0.0812.00 (+0x90d2) (0x0034bc74)
  7 0x7e8d7db4 SHCoCreateInstance+0x2d4() in shell32 (0x0034c174)
  8 0x7e8f9a5e in shell32 (+0x59a5e) (0x0034c5f4)
  9 0x7e8fa3e5 SHELL32_BindToChild+0xc5() in shell32 (0x0034c8b4)
  10 0x7e8e90ed in shell32 (+0x490ed) (0x0034c8f4)
  11 0x7e8f9e1f SHELL32_GetDisplayNameOfChild+0x9f() in shell32 (0x0034ca54)
  12 0x7e8e9c31 in shell32 (+0x49c31) (0x0034cb94)
  13 0x009e33b4 in dreamweaver (+0x1e33b4) (0x0034d084)
  14 0x0000014b (0x0001008e)
  15 0x00000000 (0x00000000)
0x7b843fc8 RaiseException+0x78 in kernel32: movl        0xfffffffc(%ebp),%ebx
Modules:
Module  Address                 Debug info      Name (132 modules)
PE        350000-  421000       Deferred        libeay32
PE        430000-  457000       Deferred        ssleay32
PE        460000-  562000       Deferred        mfc71u
PE        800000- 1609000       Export          dreamweaver
PE      10000000-10283000       Deferred        fireworks library
PE      12000000-121ae000       Deferred        xerces-c_2_6
PE      13000000-13191000       Deferred        mmxptresources
PE      30000000-30020000       Deferred        libcurl
PE      30100000-30120000       Deferred        coretypes
PE      30800000-3083b000       Deferred        mmnotes
PE      30900000-30912000       Deferred        netio
PE      30e00000-3113e000       Deferred        resources
PE      31400000-3141c000       Deferred        swffile
PE      32100000-32181000       Deferred        workspace
PE      4a800000-4a893000       Deferred        icuuc30
PE      4ad00000-4b52d000       Deferred        icudt30
PE      5a500000-5a52f000       Export          fsshext.8.0.0812.00
PE      70d00000-70ea0000       Deferred        gdiplus
PE      78130000-781cb000       Deferred        msvcr80
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf5f000-7c000000       Deferred        comdlg32<elf>
  \-PE  7bf70000-7c000000       \               comdlg32
ELF     7c180000-7c1a0000       Deferred        mlang<elf>
  \-PE  7c190000-7c1a0000       \               mlang
ELF     7c2b1000-7c302000       Deferred        libgcrypt.so.11
ELF     7c302000-7c312000       Deferred        libtasn1.so.3
ELF     7c312000-7c340000       Deferred        libcrypt.so.1
PE      7c340000-7c396000       Deferred        msvcr71
PE      7c3a0000-7c41b000       Deferred        msvcp71
ELF     7c426000-7c42a000       Deferred        libgpg-error.so.0
ELF     7c42a000-7c49a000       Deferred        libgnutls.so.13
ELF     7c49a000-7c4bf000       Deferred        libk5crypto.so.3
ELF     7c4bf000-7c547000       Deferred        libkrb5.so.3
ELF     7c547000-7c570000       Deferred        libgssapi_krb5.so.2
ELF     7c570000-7c5a5000       Deferred        libcups.so.2
ELF     7c5a5000-7c5ba000       Deferred        midimap<elf>
  \-PE  7c5b0000-7c5ba000       \               midimap
ELF     7c5ba000-7c5e1000       Deferred        msacm32<elf>
  \-PE  7c5c0000-7c5e1000       \               msacm32
ELF     7c5e1000-7c5f9000       Deferred        msacm32<elf>
  \-PE  7c5f0000-7c5f9000       \               msacm32
ELF     7c5f9000-7c6bf000       Deferred        libasound.so.2
ELF     7c6d0000-7c706000       Deferred        winealsa<elf>
  \-PE  7c6e0000-7c706000       \               winealsa
ELF     7d30c000-7d314000       Deferred        libkrb5support.so.0
ELF     7d358000-7d38a000       Deferred        uxtheme<elf>
  \-PE  7d360000-7d38a000       \               uxtheme
ELF     7d38a000-7d38f000       Deferred        libxfixes.so.3
ELF     7d38f000-7d398000       Deferred        libxcursor.so.1
ELF     7d398000-7d39e000       Deferred        libxrandr.so.2
ELF     7d3a8000-7d3aa000       Deferred        libkeyutils.so.1
ELF     7d3aa000-7d3ad000       Deferred        libcom_err.so.2
ELF     7d95d000-7d95f000       Deferred        libnvidia-tls.so.1
ELF     7d95f000-7e1e5000       Deferred        libglcore.so.1
ELF     7e1e5000-7e271000       Deferred        libgl.so.1
ELF     7e271000-7e276000       Deferred        libxdmcp.so.6
ELF     7e276000-7e279000       Deferred        libxau.so.6
ELF     7e279000-7e36a000       Deferred        libx11.so.6
ELF     7e36a000-7e378000       Deferred        libxext.so.6
ELF     7e378000-7e37d000       Deferred        libxxf86vm.so.1
ELF     7e37d000-7e395000       Deferred        libice.so.6
ELF     7e395000-7e39d000       Deferred        libsm.so.6
ELF     7e39d000-7e3a5000       Deferred        libxrender.so.1
ELF     7e3ae000-7e43a000       Deferred        winex11<elf>
  \-PE  7e3c0000-7e43a000       \               winex11
ELF     7e4b9000-7e4d9000       Deferred        libexpat.so.1
ELF     7e4d9000-7e504000       Deferred        libfontconfig.so.1
ELF     7e504000-7e519000       Deferred        libz.so.1
ELF     7e519000-7e589000       Deferred        libfreetype.so.6
ELF     7e589000-7e5af000       Deferred        odbc32<elf>
  \-PE  7e590000-7e5af000       \               odbc32
ELF     7e5af000-7e5c3000       Deferred        msimg32<elf>
  \-PE  7e5c0000-7e5c3000       \               msimg32
ELF     7e5c3000-7e62b000       Deferred        msvcrt<elf>
  \-PE  7e5d0000-7e62b000       \               msvcrt
ELF     7e62b000-7e658000       Deferred        ws2_32<elf>
  \-PE  7e630000-7e658000       \               ws2_32
ELF     7e658000-7e672000       Deferred        wsock32<elf>
  \-PE  7e660000-7e672000       \               wsock32
ELF     7e672000-7e710000       Deferred        oleaut32<elf>
  \-PE  7e680000-7e710000       \               oleaut32
ELF     7e710000-7e745000       Deferred        winspool<elf>
  \-PE  7e720000-7e745000       \               winspool
ELF     7e745000-7e7d3000       Deferred        winmm<elf>
  \-PE  7e750000-7e7d3000       \               winmm
ELF     7e7d3000-7e891000       Deferred        comctl32<elf>
  \-PE  7e7e0000-7e891000       \               comctl32
ELF     7e891000-7e994000       Export          shell32<elf>
  \-PE  7e8a0000-7e994000       \               shell32
ELF     7e994000-7e9ed000       Deferred        shlwapi<elf>
  \-PE  7e9a0000-7e9ed000       \               shlwapi
ELF     7e9ed000-7ea0d000       Deferred        mpr<elf>
  \-PE  7e9f0000-7ea0d000       \               mpr
ELF     7ea0d000-7ea57000       Deferred        wininet<elf>
  \-PE  7ea20000-7ea57000       \               wininet
ELF     7ea57000-7ea74000       Deferred        imm32<elf>
  \-PE  7ea60000-7ea74000       \               imm32
ELF     7ea74000-7ea88000       Deferred        lz32<elf>
  \-PE  7ea80000-7ea88000       \               lz32
ELF     7ea88000-7eaa2000       Deferred        version<elf>
  \-PE  7ea90000-7eaa2000       \               version
ELF     7eaa2000-7eab5000       Deferred        libresolv.so.2
ELF     7eac6000-7eae4000       Deferred        iphlpapi<elf>
  \-PE  7ead0000-7eae4000       \               iphlpapi
ELF     7eae4000-7eb3d000       Deferred        rpcrt4<elf>
  \-PE  7eaf0000-7eb3d000       \               rpcrt4
ELF     7eb3d000-7ebde000       Deferred        ole32<elf>
  \-PE  7eb50000-7ebde000       \               ole32
ELF     7ebde000-7ebf3000       Deferred        psapi<elf>
  \-PE  7ebe0000-7ebf3000       \               psapi
ELF     7ebf3000-7ec3d000       Deferred        dbghelp<elf>
  \-PE  7ec00000-7ec3d000       \               dbghelp
ELF     7ec3d000-7ec86000       Deferred        advapi32<elf>
  \-PE  7ec50000-7ec86000       \               advapi32
ELF     7ec86000-7ed21000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed21000       \               gdi32
ELF     7ed21000-7ee5f000       Deferred        user32<elf>
  \-PE  7ed40000-7ee5f000       \               user32
ELF     7ef9d000-7efa8000       Deferred        libnss_files.so.2
ELF     7efa8000-7efb2000       Deferred        libnss_nis.so.2
ELF     7efb2000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7efef000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d54000-b7d58000       Deferred        libdl.so.2
ELF     b7d58000-b7ea2000       Deferred        libc.so.6
ELF     b7ea2000-b7eba000       Deferred        libpthread.so.0
ELF     b7ecb000-b7fdf000       Deferred        libwine.so.1
ELF     b7fe1000-b7ffd000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Macromedia\Dreamweaver 8\Dreamweaver.exe
        0000000d    0
        00000009    0 <==
wine: Call from 0x7b843f50 to unimplemented function shell32.dll.SHInvokePrinterCommandA, aborting
wine: Call from 0x7b843f50 to unimplemented function shell32.dll.SHInvokePrinterCommandW, aborting

```

I have managed to install Flash 8 after Dreamweaver fine and it works beautifully!

Any help would be thanked.

---

### Post by kasio on 2007-10-25
*bump*

P.S. Is buming legal?

---

### Post by Marc Hoffman on 2007-10-25
I was able to install Dreamweaver 8 under WINE with no problems. I have also heard that wine-doors is a good to go. Download the .deb from their site and you are good to go. Good luck. Incidently do you know where I can download a trial version of Flash 8? I need it to complete an IT course but dont want the hassle of getting the newest version to work in ubuntu.

---

### Post by kasio on 2007-10-25
The Adobe Website will probaly have it. try the ftp server (ftp.adobe.com).

I will try wine doors, but I am still thinking about the shprint error.

---

### Post by JohnJackson on 2008-05-05
I am currently having the same problem as in the original post, except using wine 0.9.61 and Ubuntu 8.04. Was a fix for this found?

Thanks

---

### Post by sOnIc on 2008-06-13
Same here :(

---

### Post by ene_dene on 2008-06-13
Is there any good free alternative for Dreamweaver for Linux?

---

### Post by jspolen on 2008-06-13
l

---

