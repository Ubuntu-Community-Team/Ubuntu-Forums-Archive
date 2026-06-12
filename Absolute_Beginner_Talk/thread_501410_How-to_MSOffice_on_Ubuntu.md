---
title: "How-to MSOffice on Ubuntu"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by tarek on 2007-07-15
Hi,

I followed the instructions in this how-to: [https://help.ubuntu.com/community/Microsoft_Office]("https://help.ubuntu.com/community/Microsoft_Office") the installation worked but when I open Word or Excel they startup and then close. They open for 1 sec.

Anybody experiencing the same problem?

Thanks,
TK

---

### Post by oilchangeguy on 2007-07-15
what version of office are you using? the guide says 2000 works best. and what's wrong with open office?

---

### Post by tarek on 2007-07-15
I'm using office 2000 and there's nothing wrong with OO :D I use it. However there's nothing wrong with using another Word processor :D

I have files formated in Word and don't quite look the same in OO. I need Office for old Access files too. I could use a virtual machine but since the how-to is available from Ubuntu I would like to be able run Office.

Thanks.

---

### Post by fluteflute on 2007-07-15
BTW, thats not an official howto - just one a Ubuntu fan created.

---

### Post by angryfirelord on 2007-07-15
Make sure you get the latest wine from the official wine repos instead of from the ubuntu repos.

When you try to start MS Office, what does the terminal put out?

---

### Post by tarek on 2007-07-15
I reinstalled wine using the repository from the website [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

Then I reinstalled office but this time I just installed Word.

Downloaded the DLLs from [http://www.dll-files.com/]("http://www.dll-files.com/") and add the libraries in winecfg.

When I run this command:
```
wine "C:\Program Files\Microsoft Office\Office\WINWORD.EXE"
```

I get the splash screen then it closes and I get this:
```

fixme:x11drv:X11DRV_GetDeviceCaps (0x30c): CAPS1 is unimplemented, will return 0
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:actctx:FindActCtxSectionStringW 00000001 (null) 7 L"Word.Document.8" 0x33ea80
wine: Unhandled page fault on read access to 0x00000000 at address 0x7723c77a (thread 0029), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7723c77a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7723c77a ESP:0033ea7c EBP:0033eac0 EFLAGS:00210212(   - 00      - RIA1)
 EAX:00000000 EBX:80004002 ECX:00000000 EDX:00000054
 ESI:0033eb48 EDI:0033ef90
Stack dump:
0x0033ea7c:  772bdb80 00000040 00000001 00000000
0x0033ea8c:  7b8b0888 00000000 00000000 00000000
0x0033ea9c:  00000000 00f00baa 00000000 771c1480
0x0033eaac:  772bb0dc 00000000 00001000 00000000
0x0033eabc:  771b4c58 0033eaf8 771ef4ed 0018fcc8
0x0033eacc:  00000000 0033ef90 771b456c 0033eb48
Backtrace:
=>1 0x7723c77a in ole32 (+0x8c77a) (0x0033eac0)
  2 0x771ef4ed in ole32 (+0x3f4ed) (0x0033eaf8)
  3 0x771ef4a0 in ole32 (+0x3f4a0) (0x0033eb40)
  4 0x308efded in mso9 (+0x2fded) (0x0033eb78)
  5 0x30044733 in winword (+0x44733) (0x0033f590)
  6 0x30044616 in winword (+0x44616) (0x0033fcf4)
  7 0x3003be4f in winword (+0x3be4f) (0x0033fe4c)
  8 0x30002bc7 in winword (+0x2bc7) (0x0033fe7c)
  9 0x30002a2d in winword (+0x2a2d) (0x0033ff08)
  10 0x7b874e7e in kernel32 (+0x54e7e) (0x0033ffe8)
  11 0xb7e12af7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7723c77a: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (68 modules)
PE      30000000-3086a000       Export          winword
PE      308c0000-30e19000       Export          mso9
PE      771b0000-772d1000       Export          ole32
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c8a8000-7c8f9000       Deferred        libgcrypt.so.11
ELF     7c8f9000-7c90e000       Deferred        libtasn1.so.3
ELF     7c90e000-7c93c000       Deferred        libcrypt.so.1
ELF     7c951000-7c9c1000       Deferred        libgnutls.so.13
ELF     7c9c1000-7c9f2000       Deferred        libcups.so.2
ELF     7ca98000-7caca000       Deferred        uxtheme<elf>
  \-PE  7caa0000-7caca000       \               uxtheme
ELF     7caca000-7cad3000       Deferred        libxcursor.so.1
ELF     7cad3000-7caf0000       Deferred        imm32<elf>
  \-PE  7cae0000-7caf0000       \               imm32
ELF     7d118000-7d11c000       Deferred        libgpg-error.so.0
ELF     7d11c000-7d122000       Deferred        libxrandr.so.2
ELF     7da75000-7da7e000       Deferred        librt.so.1
ELF     7da7e000-7da83000       Deferred        libxfixes.so.3
ELF     7da83000-7da8b000       Deferred        libxrender.so.1
ELF     7db4d000-7e4b8000       Deferred        fglrx_dri.so
ELF     7e4b8000-7e558000       Deferred        libgl.so.1
ELF     7e558000-7e55d000       Deferred        libxdmcp.so.6
ELF     7e55d000-7e560000       Deferred        libxau.so.6
ELF     7e560000-7e651000       Deferred        libx11.so.6
ELF     7e651000-7e65f000       Deferred        libxext.so.6
ELF     7e65f000-7e664000       Deferred        libxxf86vm.so.1
ELF     7e664000-7e67c000       Deferred        libice.so.6
ELF     7e67c000-7e685000       Deferred        libsm.so.6
ELF     7e685000-7e70e000       Deferred        winex11<elf>
  \-PE  7e690000-7e70e000       \               winex11
ELF     7e7b9000-7e7d9000       Deferred        libexpat.so.1
ELF     7e7d9000-7e804000       Deferred        libfontconfig.so.1
ELF     7e804000-7e86f000       Deferred        libfreetype.so.6
ELF     7e86f000-7e8a2000       Deferred        winspool<elf>
  \-PE  7e880000-7e8a2000       \               winspool
ELF     7e8a2000-7e95f000       Deferred        comctl32<elf>
  \-PE  7e8b0000-7e95f000       \               comctl32
ELF     7e95f000-7e9b8000       Deferred        shlwapi<elf>
  \-PE  7e970000-7e9b8000       \               shlwapi
ELF     7e9b8000-7eab6000       Deferred        shell32<elf>
  \-PE  7e9d0000-7eab6000       \               shell32
ELF     7eab6000-7eac9000       Deferred        libresolv.so.2
ELF     7eac9000-7eae7000       Deferred        iphlpapi<elf>
  \-PE  7ead0000-7eae7000       \               iphlpapi
ELF     7eae7000-7eb40000       Deferred        rpcrt4<elf>
  \-PE  7eaf0000-7eb40000       \               rpcrt4
ELF     7eb40000-7ec7d000       Deferred        user32<elf>
  \-PE  7eb60000-7ec7d000       \               user32
ELF     7ec7d000-7ec89000       Deferred        libgcc_s.so.1
ELF     7ec8a000-7ec9e000       Deferred        libz.so.1
ELF     7ed88000-7ee48000       Deferred        gdi32<elf>
  \-PE  7eda0000-7ee48000       \               gdi32
ELF     7ee48000-7ee90000       Deferred        advapi32<elf>
  \-PE  7ee50000-7ee90000       \               advapi32
ELF     7efa2000-7efad000       Deferred        libnss_files.so.2
ELF     7efad000-7efc4000       Deferred        libnsl.so.1
ELF     7efc4000-7efeb000       Deferred        libm.so.6
ELF     7efed000-7eff7000       Deferred        libnss_nis.so.2
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c99000-b7c9d000       Deferred        libdl.so.2
ELF     b7c9d000-b7dde000       Deferred        libc.so.6
ELF     b7ddf000-b7df6000       Deferred        libpthread.so.0
ELF     b7e0b000-b7f1f000       Export          libwine.so.1
ELF     b7f21000-b7f3c000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000002a 
        0000002c    0
        0000002b    0
00000028 (D) C:\Program Files\Microsoft Office\Office\WINWORD.EXE
        00000029    0 <==


```



I tried changing the libraries from *native* to *bultin* so this time Word stated and gave me the attached error message.

Thanks
TK

---

