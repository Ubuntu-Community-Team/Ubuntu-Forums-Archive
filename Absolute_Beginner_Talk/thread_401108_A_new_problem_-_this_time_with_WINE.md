---
title: "A new problem - this time with WINE"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Murxidon on 2007-04-04
Ok, heh, I installed wine using the instructions given at WineHQ. But when I try to launch winecfg. I am greeted with this...

neil@Neil-PC:~$ winecfg
wine: Unhandled page fault on read access to 0x26000000 at address 0x26000000 (thread 0009), starting debugger...
neil@Neil-PC:~$ wincfg
bash: wincfg: command not found
neil@Neil-PC:~$ winecfg
wine: Unhandled page fault on read access to 0x63002000 at address 0x63002000 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x63002000 in 32-bit code (0x63002000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:63002000 ESP:0033f6cc EBP:0033f6e8 EFLAGS:00210202(   - 00      - -RI1)
 EAX:000000dc EBX:7e6f807f ECX:7e20f924 EDX:00000000
 ESI:7e2c032f EDI:7c10ebd1
Stack dump:
0x0033f6cc:  7e29c58e 0000002a 7e20f924 0033f6e8
0x0033f6dc:  7e1c7bca 7e29c579 7e2ca2fc 0033f728
0x0033f6ec:  7e28665f 00000026 00000000 00000000
0x0033f6fc:  b7cefbe0 b7ced9c0 b7dcbff4 0033f744
0x0033f70c:  7c10ebd1 0033f728 b7dc8923 0000000d
0x0033f71c:  7e2f8dd8 0033f744 7c10ebd1 0033f7d8
Backtrace:
=>1 0x63002000 (0x0033f6e8)
  2 0x7e28665f gnutls_global_init+0xdf() in libgnutls.so.13 (0x0033f728)
  3 0x7e2de2ff httpInitialize+0x5f() in libcups.so.2 (0x0033f7d8)
  4 0x7e2df365 httpConnectEncrypt+0x55() in libcups.so.2 (0x0033f918)
  5 0x7e2d8c8d cupsGetDests+0x3d() in libcups.so.2 (0x0033f938)
  6 0x7e8582e7 WINSPOOL_LoadSystemPrinters+0x9b7() in winspool (0x0033fd08)
  7 0x7e85895f in winspool (+0x1895f) (0x0033fd18)
  8 0x7e858a23 in winspool (+0x18a23) (0x0033fd38)
  9 0x7bc37e65 call_dll_entry_point+0x15() in ntdll (0x0033fd58)
  10 0x7bc39a2d in ntdll (+0x29a2d) (0x0033fde8)
  11 0x7bc3a20d in ntdll (+0x2a20d) (0x0033fe28)
  12 0x7bc3a152 in ntdll (+0x2a152) (0x0033fe68)
  13 0x7bc3a152 in ntdll (+0x2a152) (0x0033fea8)
  14 0x7bc3c21e LdrInitializeThunk+0x2be() in ntdll (0x0033ff08)
  15 0x7b87033a in kernel32 (+0x5033a) (0x0033ffe8)
  16 0xb7de0587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x63002000: -- no code accessible --
Modules:
Module  Address                 Debug info      Name (75 modules)
ELF     7b800000-7b924000       Export          kernel32<elf>
  \-PE  7b820000-7b924000       \               kernel32
ELF     7bc00000-7bc95000       Export          ntdll<elf>
  \-PE  7bc10000-7bc95000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e1bf000-7e1c3000       Deferred        libgpg-error.so.0
ELF     7e1c3000-7e211000       Deferred        libgcrypt.so.11
ELF     7e211000-7e224000       Deferred        libtasn1.so.3
ELF     7e224000-7e252000       Deferred        libcrypt.so.1
ELF     7e25c000-7e2cb000       Export          libgnutls.so.13
ELF     7e2cb000-7e2fa000       Export          libcups.so.2
ELF     7e329000-7e32e000       Deferred        libxfixes.so.3
ELF     7e32e000-7e337000       Deferred        libxcursor.so.1
ELF     7e337000-7e354000       Deferred        imm32<elf>
  \-PE  7e340000-7e354000       \               imm32
ELF     7e354000-7e372000       Deferred        ximcp.so.2
ELF     7e372000-7e374000       Deferred        xlcutf8load.so.2
ELF     7e374000-7e377000       Deferred        libxrandr.so.2
ELF     7e377000-7e37f000       Deferred        libxrender.so.1
ELF     7e37f000-7e382000       Deferred        libxinerama.so.1
ELF     7e382000-7e389000       Deferred        libdrm.so.2
ELF     7e389000-7e3f8000       Deferred        libgl.so.1
ELF     7e3f8000-7e3fd000       Deferred        libxdmcp.so.6
ELF     7e3fd000-7e400000       Deferred        libxau.so.6
ELF     7e400000-7e4c9000       Deferred        libx11.so.6
ELF     7e4c9000-7e4d6000       Deferred        libxext.so.6
ELF     7e4d6000-7e4db000       Deferred        libxxf86vm.so.1
ELF     7e4db000-7e4f3000       Deferred        libice.so.6
ELF     7e4f3000-7e582000       Deferred        winex11<elf>
  \-PE  7e500000-7e582000       \               winex11
ELF     7e582000-7e5a0000       Deferred        libexpat.so.1
ELF     7e5a0000-7e5cf000       Deferred        libfontconfig.so.1
ELF     7e5cf000-7e5e3000       Deferred        libz.so.1
ELF     7e5e3000-7e64d000       Deferred        libfreetype.so.6
ELF     7e64d000-7e67f000       Deferred        uxtheme<elf>
  \-PE  7e650000-7e67f000       \               uxtheme
ELF     7e67f000-7e70d000       Deferred        winmm<elf>
  \-PE  7e690000-7e70d000       \               winmm
ELF     7e70d000-7e720000       Deferred        libresolv.so.2
ELF     7e720000-7e73e000       Deferred        iphlpapi<elf>
  \-PE  7e730000-7e73e000       \               iphlpapi
ELF     7e73e000-7e793000       Deferred        rpcrt4<elf>
  \-PE  7e750000-7e793000       \               rpcrt4
ELF     7e793000-7e82e000       Deferred        ole32<elf>
  \-PE  7e7a0000-7e82e000       \               ole32
ELF     7e82e000-7e860000       Export          winspool<elf>
  \-PE  7e840000-7e860000       \               winspool
ELF     7e860000-7e91c000       Deferred        comctl32<elf>
  \-PE  7e870000-7e91c000       \               comctl32
ELF     7e91c000-7e961000       Deferred        advapi32<elf>
  \-PE  7e930000-7e961000       \               advapi32
ELF     7e961000-7e96c000       Deferred        libgcc_s.so.1
ELF     7e96d000-7e976000       Deferred        libsm.so.6
ELF     7ea55000-7eb0e000       Deferred        gdi32<elf>
  \-PE  7ea70000-7eb0e000       \               gdi32
ELF     7eb0e000-7ec48000       Deferred        user32<elf>
  \-PE  7eb30000-7ec48000       \               user32
ELF     7ec48000-7eca0000       Deferred        shlwapi<elf>
  \-PE  7ec60000-7eca0000       \               shlwapi
ELF     7eca0000-7ed9a000       Deferred        shell32<elf>
  \-PE  7ecb0000-7ed9a000       \               shell32
ELF     7ed9a000-7ee3a000       Deferred        comdlg32<elf>
  \-PE  7eda0000-7ee3a000       \               comdlg32
ELF     7ee3a000-7ee97000       Deferred        winecfg<elf>
  \-PE  7ee40000-7ee97000       \               winecfg
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efba000       Deferred        libnss_nis.so.2
ELF     7efba000-7efd0000       Deferred        libnsl.so.1
ELF     7efd0000-7eff6000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c83000-b7c87000       Deferred        libdl.so.2
ELF     b7c87000-b7dbb000       Deferred        libc.so.6
ELF     b7dbc000-b7dcf000       Deferred        libpthread.so.0
ELF     b7dd9000-b7eea000       Export          libwine.so.1
ELF     b7eec000-b7f07000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\winecfg.exe
        00000009    0 <==


I have no idea what this means, I just started using it today...

Erm.. Anyone know what's wrong?

Thanks... *Ashamed*

---

### Post by Kobalt on 2007-04-04
I advise you to install Wine through Synaptic (since it's in the repos) rather than compiling it yourself (if that's what you did), you'll probably get better results.
Before you go to Synaptic, remove the Wine you compiled with ```
sudo make uninstall
sudo make clean
```

---

### Post by xopher on 2007-04-04
What version of Wine? How did you install it?

Have you checked out: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

