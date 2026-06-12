---
title: "Please help me with running the action replay ds software on ubuntu"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ./&amp;/. on 2007-05-26
Hi,
I have wine installed on the latest version of ubuntu and i need some help configuring wine to work with the action replay ds software.
Here is the error:

sage@sage:~$ wine ActionReplayCodeManager
err:module:import_dll Library MFC71.DLL (which is needed by L"C:\\windows\\system32\\ActionReplayCodeManager.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\ActionReplayCodeManager.exe" failed, status c0000135

Please help

---

### Post by AAM on 2007-05-26
I can't claim to be an expert at WINE, but I would suggest that the missing DLL file is the problem (dah!), so if you get a copy of this and deliberately put it into the quasi-Windows directory in the same place as a Windows install, the message should disappear .... and then you'll probably get another one! (cheery fellow aren't I?) But that's the was it goes with WHINE ... I mean WINE!

---

### Post by ./&amp;/. on 2007-05-27
Well I got the missing .dll and put it in the path but now i have this long error.  If someone could please help me it would be very appreciated.

sage@sage:~$ wine ActionReplayCodeManager
wine: Unhandled page fault on read access to 0x45455246 at address 0x7e82e316 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x45455246 in 32-bit code (0x7e82e316).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e82e316 ESP:0033d204 EBP:0033d25c EFLAGS:00210217(   - 00      RIAP1C)
 EAX:45455246 EBX:7e84d24c ECX:00583870 EDX:45455246
 ESI:0019a088 EDI:00010032
Stack dump:
0x0033d204:  0000002c 00000000 0033d26c 7e82db91
0x0033d214:  00010032 00000000 0033d238 7c16e0c7
0x0033d224:  00000001 00000000 0033d9b8 0019a188
0x0033d234:  00000000 7bc29ba1 00000002 00000001
0x0033d244:  00000000 7b8ad908 00000002 7ede6b9c
0x0033d254:  00010032 00010032 0033d28c 7edc22ea
Backtrace:
=>1 0x7e82e316 in comctl32 (+0x7e316) (0x0033d25c)
  2 0x7edc22ea WINPROC_wrapper+0x1a() in user32 (0x0033d28c)
  3 0x7edc2a1e in user32 (+0xa2a1e) (0x0033d2cc)
  4 0x7edc5a5a WINPROC_CallProcAtoW+0x1ca() in user32 (0x0033d78c)
  5 0x7edc69e3 CallWindowProcA+0xc3() in user32 (0x0033d7cc)
  6 0x7c16fcdb in mfc71 (+0x2fcdb) (0x0033d7ec)
  7 0x7c16e0c7 in mfc71 (+0x2e0c7) (0x0033d808)
  8 0x7c16e14f in mfc71 (+0x2e14f) (0x0033d868)
  9 0x7c16e1b8 in mfc71 (+0x2e1b8) (0x0033d888)
  10 0x7c16e1f6 in mfc71 (+0x2e1f6) (0x0033d8b4)
  11 0x7edc22ea WINPROC_wrapper+0x1a() in user32 (0x0033d8e4)
  12 0x7edc2a1e in user32 (+0xa2a1e) (0x0033d924)
  13 0x7edc697a CallWindowProcA+0x5a() in user32 (0x0033d964)
  14 0x7ed8f319 in user32 (+0x6f319) (0x0033d9d4)
  15 0x7ed92ea2 SendMessageTimeoutA+0x202() in user32 (0x0033da44)
  16 0x7ed92f60 SendMessageA+0x50() in user32 (0x0033da84)
  17 0x004173b2 in actionreplaycodemanager (+0x173b2) (0x0033db20)
  18 0x7edc4198 in user32 (+0xa4198) (0x0033db60)
  19 0x7edc686a WINPROC_CallDlgProcA+0x5a() in user32 (0x0033dba0)
  20 0x7ed57cda DefDlgProcA+0x8a() in user32 (0x0033dbd0)
  21 0x7edc22ea WINPROC_wrapper+0x1a() in user32 (0x0033dc00)
  22 0x7edc2a1e in user32 (+0xa2a1e) (0x0033dc40)
  23 0x7edc697a CallWindowProcA+0x5a() in user32 (0x0033dc80)
  24 0x7c16fcdb in mfc71 (+0x2fcdb) (0x0033dca0)
  25 0x7c17146d in mfc71 (+0x3146d) (0x0033dd54)
  26 0x7c16e0b0 in mfc71 (+0x2e0b0) (0x0033dd74)
  27 0x7c16e14f in mfc71 (+0x2e14f) (0x0033ddd4)
  28 0x7c16e1b8 in mfc71 (+0x2e1b8) (0x0033ddf4)
  29 0x7c16e1f6 in mfc71 (+0x2e1f6) (0x0033de20)
  30 0x7edc22ea WINPROC_wrapper+0x1a() in user32 (0x0033de50)
  31 0x7edc2a1e in user32 (+0xa2a1e) (0x0033de90)
  32 0x7edc697a CallWindowProcA+0x5a() in user32 (0x0033ded0)
  33 0x0046e6c6 in actionreplaycodemanager (+0x6e6c6) (0x00583518)
  34 0x00000001 (0x004aa6d8)
  35 0x00487990 in actionreplaycodemanager (+0x87990) (0x00420d54)
  36 0x25ff0049 (0xb31425ff)
  37 0x00000000 (0x00000000)
0x7e82e316: cmpw        $0,0x0(%edx)
Modules:
Module  Address                 Debug info      Name (92 modules)
PE      400000-576000   Export          actionreplaycodemanager
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c140000-7c243000       Export          mfc71
PE      7c340000-7c396000       Deferred        msvcr71
ELF     7e104000-7e148000       Deferred        riched20<elf>
  \-PE  7e110000-7e148000       \               riched20
ELF     7e148000-7e15c000       Deferred        riched32<elf>
  \-PE  7e150000-7e15c000       \               riched32
ELF     7e15c000-7e170000       Deferred        msimg32<elf>
  \-PE  7e160000-7e170000       \               msimg32
ELF     7e170000-7e185000       Deferred        midimap<elf>
  \-PE  7e180000-7e185000       \               midimap
ELF     7e185000-7e1ab000       Deferred        msacm32<elf>
  \-PE  7e190000-7e1ab000       \               msacm32
ELF     7e1ab000-7e1c3000       Deferred        msacm32<elf>
  \-PE  7e1b0000-7e1c3000       \               msacm32
ELF     7e1c3000-7e1ff000       Deferred        wineoss<elf>
  \-PE  7e1d0000-7e1ff000       \               wineoss
ELF     7e227000-7e259000       Deferred        uxtheme<elf>
  \-PE  7e230000-7e259000       \               uxtheme
ELF     7e260000-7e265000       Deferred        libxfixes.so.3
ELF     7e265000-7e26e000       Deferred        libxcursor.so.1
ELF     7e26e000-7e28b000       Deferred        imm32<elf>
  \-PE  7e280000-7e28b000       \               imm32
ELF     7e28b000-7e291000       Deferred        libxrandr.so.2
ELF     7e291000-7e299000       Deferred        libxrender.so.1
ELF     7e299000-7e29c000       Deferred        libxinerama.so.1
ELF     7e29c000-7e2a5000       Deferred        libdrm.so.2
ELF     7e2a5000-7e305000       Deferred        libgl.so.1
ELF     7e305000-7e30a000       Deferred        libxdmcp.so.6
ELF     7e30a000-7e30d000       Deferred        libxau.so.6
ELF     7e30d000-7e3fe000       Deferred        libx11.so.6
ELF     7e3fe000-7e40c000       Deferred        libxext.so.6
ELF     7e40c000-7e411000       Deferred        libxxf86vm.so.1
ELF     7e411000-7e429000       Deferred        libice.so.6
ELF     7e429000-7e432000       Deferred        libsm.so.6
ELF     7e432000-7e4c0000       Deferred        winex11<elf>
  \-PE  7e440000-7e4c0000       \               winex11
ELF     7e53a000-7e55a000       Deferred        libexpat.so.1
ELF     7e55a000-7e585000       Deferred        libfontconfig.so.1
ELF     7e585000-7e599000       Deferred        libz.so.1
ELF     7e599000-7e604000       Deferred        libfreetype.so.6
ELF     7e604000-7e619000       Deferred        psapi<elf>
  \-PE  7e610000-7e619000       \               psapi
ELF     7e619000-7e662000       Deferred        dbghelp<elf>
  \-PE  7e620000-7e662000       \               dbghelp
ELF     7e662000-7e679000       Deferred        imagehlp<elf>
  \-PE  7e670000-7e679000       \               imagehlp
ELF     7e679000-7e708000       Deferred        winmm<elf>
  \-PE  7e690000-7e708000       \               winmm
ELF     7e708000-7e7a3000       Deferred        oleaut32<elf>
  \-PE  7e720000-7e7a3000       \               oleaut32
ELF     7e7a3000-7e85f000       Export          comctl32<elf>
  \-PE  7e7b0000-7e85f000       \               comctl32
ELF     7e85f000-7e954000       Deferred        shell32<elf>
  \-PE  7e870000-7e954000       \               shell32
ELF     7e954000-7e9ee000       Deferred        ole32<elf>
  \-PE  7e960000-7e9ee000       \               ole32
ELF     7e9ee000-7ea47000       Deferred        shlwapi<elf>
  \-PE  7ea00000-7ea47000       \               shlwapi
ELF     7ea47000-7ea5a000       Deferred        libresolv.so.2
ELF     7ea5a000-7ea78000       Deferred        iphlpapi<elf>
  \-PE  7ea60000-7ea78000       \               iphlpapi
ELF     7ea78000-7eacd000       Deferred        rpcrt4<elf>
  \-PE  7ea80000-7eacd000       \               rpcrt4
ELF     7eacd000-7eae1000       Deferred        lz32<elf>
  \-PE  7ead0000-7eae1000       \               lz32
ELF     7eae1000-7eafa000       Deferred        version<elf>
  \-PE  7eaf0000-7eafa000       \               version
ELF     7eafa000-7eb40000       Deferred        advapi32<elf>
  \-PE  7eb10000-7eb40000       \               advapi32
ELF     7eb40000-7eb4c000       Deferred        libgcc_s.so.1
ELF     7ec43000-7ed00000       Deferred        gdi32<elf>
  \-PE  7ec60000-7ed00000       \               gdi32
ELF     7ed00000-7ee3c000       Export          user32<elf>
  \-PE  7ed20000-7ee3c000       \               user32
ELF     7ee3c000-7ee98000       Deferred        setupapi<elf>
  \-PE  7ee50000-7ee98000       \               setupapi
ELF     7efaa000-7efb5000       Deferred        libnss_files.so.2
ELF     7efb5000-7efcc000       Deferred        libnsl.so.1
ELF     7efcc000-7eff3000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cb5000-b7cbe000       Deferred        libnss_compat.so.2
ELF     b7cbf000-b7cc3000       Deferred        libdl.so.2
ELF     b7cc3000-b7e04000       Deferred        libc.so.6
ELF     b7e04000-b7e1b000       Deferred        libpthread.so.0
ELF     b7e28000-b7f39000       Deferred        libwine.so.1
ELF     b7f3b000-b7f56000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\windows\system32\ActionReplayCodeManager.exe
        0000000e    0
        0000000d    0
        00000009    0 <==
sage@sage:~$ 
sage@sage:~$ 
sage@sage:~$ 
sage@sage:~$

---

### Post by ./&amp;/. on 2007-05-27
Please help.  At least someone here must know

---

### Post by Zuuswa on 2007-05-27
This really isnt the best place to look for your answer.  Wine is not shipped with, nor maintained by Ubuntu.  I would try heading over to the [http://appdb.winehq.org/](http://appdb.winehq.org/) (Wine application database) and searching for your problem there.

---

