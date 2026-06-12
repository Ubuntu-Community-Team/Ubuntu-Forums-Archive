---
title: "Problems with Wine"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by knives on 2006-02-09
I'm not sure if this is the correct place to be putting this problem, but I consider myself a bit of a nub and have only just started on linux (ubuntu breezy), hence "Absolute Beginners Talk".

Basically, Installed Wine using the Automatix script, used winecfg to detect drives etc etc, finally got it to read the cdrom setup for visual basic 6, the beautiful little setup box came up introducing me to setup, pressed next only to have this bunch of onlygodknowswhat to appear in the terminal and the setup to disappear:


wine: Unhandled page fault on read access to 0x00000000 at address 0x411b79 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00411b79).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:00411b79 ESP:7fb0b3f0 EBP:00000000 EFLAGS:00010216(   - 00      -RIAP1)
 EAX:7efaacbe EBX:ffffff31 ECX:7fb0bb24 EDX:000010e6
 ESI:00000000 EDI:0000004e
Stack dump:
0x00000000:  00000000 00000000 00000000 00000000
0x00000010:  00000000 00000000 00000000 00000000
0x00000020:  00000000 00000000 00000000 00000000
0x00000030:  00000000 00000000 00000000 00000000
0x00000040:  00000000 00000000 00000000 00000000
0x00000050:  00000000 00000000 00000000 00000000
0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x00411b79 in setup (+0x11b79) (0x00411b79)
0x00411b79: cmpb        $0x0,0x0(%esi)
Modules:
Module  Address                 Debug info      Name (72 modules)
PE      0x00400000-0048c000     Export          setup
ELF     0x7be87000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e1c9000-7e20c000     Deferred        riched20<elf>
  \-PE  0x7e1e0000-7e20c000     \               riched20
ELF     0x7e20c000-7e220000     Deferred        riched32<elf>
  \-PE  0x7e210000-7e220000     \               riched32
ELF     0x7e842000-7e873000     Deferred        uxtheme<elf>
  \-PE  0x7e850000-7e873000     \               uxtheme
ELF     0x7e8b7000-7e8c0000     Deferred        libxcursor.so.1
ELF     0x7e8cb000-7e8e7000     Deferred        imm32<elf>
  \-PE  0x7e8d0000-7e8e7000     \               imm32
ELF     0x7e8e7000-7e903000     Deferred        ximcp.so.2
ELF     0x7e903000-7e906000     Deferred        libxrandr.so.2
ELF     0x7e906000-7e90e000     Deferred        libxrender.so.1
ELF     0x7e90e000-7e915000     Deferred        libdrm.so.1
ELF     0x7e915000-7e97b000     Deferred        libgl.so.1
ELF     0x7e97b000-7e97f000     Deferred        libxdmcp.so.6
ELF     0x7e97f000-7ea3f000     Deferred        libx11.so.6
ELF     0x7ea3f000-7ea4c000     Deferred        libxext.so.6
ELF     0x7ea4c000-7ea65000     Deferred        libice.so.6
ELF     0x7ea65000-7eae4000     Deferred        winex11<elf>
  \-PE  0x7ea70000-7eae4000     \               winex11
ELF     0x7eae4000-7eb03000     Deferred        libexpat.so.1
ELF     0x7eb03000-7eb31000     Deferred        libfontconfig.so.1
ELF     0x7eb31000-7eb45000     Deferred        libz.so.1
ELF     0x7eb45000-7ebaf000     Deferred        libfreetype.so.6
ELF     0x7ebaf000-7ebcd000     Deferred        mpr<elf>
  \-PE  0x7ebc0000-7ebcd000     \               mpr
ELF     0x7ebcd000-7ebeb000     Deferred        iphlpapi<elf>
  \-PE  0x7ebd0000-7ebeb000     \               iphlpapi
ELF     0x7ebeb000-7ec33000     Deferred        rpcrt4<elf>
  \-PE  0x7ec00000-7ec33000     \               rpcrt4
ELF     0x7ec33000-7ecbd000     Deferred        ole32<elf>
  \-PE  0x7ec50000-7ecbd000     \               ole32
ELF     0x7ecbd000-7ed14000     Deferred        shlwapi<elf>
  \-PE  0x7ecd0000-7ed14000     \               shlwapi
ELF     0x7ed14000-7edd7000     Deferred        shell32<elf>
  \-PE  0x7ed30000-7edd7000     \               shell32
ELF     0x7edd7000-7edeb000     Deferred        lz32<elf>
  \-PE  0x7ede0000-7edeb000     \               lz32
ELF     0x7edeb000-7ee04000     Deferred        version<elf>
  \-PE  0x7edf0000-7ee04000     \               version
ELF     0x7ee04000-7ee41000     Deferred        advapi32<elf>
  \-PE  0x7ee10000-7ee41000     \               advapi32
ELF     0x7ef27000-7f82a000     Deferred        gdi32<elf>
  \-PE  0x7ef70000-7f82a000     \               gdi32
ELF     0x7f82a000-7f94c000     Deferred        user32<elf>
  \-PE  0x7f840000-7f94c000     \               user32
ELF     0x7f94c000-7fa00000     Deferred        comctl32<elf>
  \-PE  0x7f960000-7fa00000     \               comctl32
ELF     0x7fb10000-7fb15000     Deferred        libxxf86vm.so.1
ELF     0x7fb15000-7fb20000     Deferred        libgcc_s.so.1
ELF     0x7fb23000-7fb28000     Deferred        libxxf86dga.so.1
ELF     0x7fc70000-7fd70000     Deferred        kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe81000-7fe88000     Deferred        libsm.so.6
ELF     0x7fe88000-7fe92000     Deferred        libnss_files.so.2
ELF     0x7fe92000-7fe9b000     Deferred        libnss_nis.so.2
ELF     0x7fe9b000-7feb0000     Deferred        libnsl.so.1
ELF     0x7feb0000-7feb9000     Deferred        libnss_compat.so.2
ELF     0x7febe000-7fec2000     Deferred        libxfixes.so.3
ELF     0x7fec2000-7fec4000     Deferred        xlcutf8load.so.2
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7d8e000-b7d91000     Deferred        libdl.so.2
ELF     0xb7d91000-b7ebf000     Deferred        libc.so.6
ELF     0xb7ebf000-b7ed1000     Deferred        libpthread.so.0
ELF     0xb7ed1000-b7eeb000     Deferred        libwine.so.1
ELF     0xb7eeb000-b7eee000     Deferred        libxau.so.6
ELF     0xb7ef9000-b7f0f000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\setup.exe
        00000009    0 <==
WineDbg terminated on pid 0x8


At this point I am completely clueless as I am used to the GUI installers of windows that pop up with a little box saying "sorry, you screwed up nub".:evil: 
Any pointers as to what is going on/how to fix this would be greatly appreciated...

---

### Post by JNowka on 2006-02-09
Just a guess but have you used winetools?  if not go download it.  follow the instructions, and it will download alot of required windows files.  These will help you run alot more programs than with just the basic wine.

---

### Post by knives on 2006-02-10
*Sigh* Alas!

I installed winetools, went through and installed the core windows files and SP2 and the windows installer, tried to wine the setup again and ended with the same result:***see bunch of unintelligible code above***

I'm not sure as to wether I just got further into solving the problem...which parts of winetools should I have installed?
Thanks for helping...

---

