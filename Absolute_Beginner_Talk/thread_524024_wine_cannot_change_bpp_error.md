---
title: "wine cannot change bpp error"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by andyho on 2007-08-12
Hello all.. trying to get one of my kids games to install on my puter with Wine, it's Jumpstart First Grade, but I keep getting 

fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16

Which I don't quite get because it is changing the screen resolution.. sometimes it'll go back to my default resolution, sometimes it hangs and I have to log out and then it goes back to normal. I checked Wine HQ and they have Jumpstart Preschool and another listed with an older version of Wine. Any ideas?!? :confused: Thanks!!

:EDIT: a while later.. while installing a My Little Pony game, I get all this.... WAAAY CONFUSED NOW! Will NO games work, err maybe it's just these kids games no one really plays! ;)

andyho@andyho-ubuntu:~$ wine /media/cdrom0/pony.exe
wine: Unhandled page fault on write access to 0x00000008 at address 0x7e7e46cb (thread 0025), starting debugger...
Unhandled exception: page fault on write access to 0x00000008 in 32-bit code (0x7e7e46cb).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e7e46cb ESP:0034f634 EBP:0034f65c EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000000 EBX:7e7ff168 ECX:00110020 EDX:00000006
 ESI:00000000 EDI:00000000
Stack dump:
0x0034f634:  00000001 00000000 0034f67c 7b88c730
0x0034f644:  7ee4cb20 7ee31b24 0005003c 7ee31b24
0x0034f654:  0005003c 0005003c 0034f6dc 00409593
0x0034f664:  00000000 00000000 0005003c 7edf0e01
0x0034f674:  ffffffe6 0016dd80 0034f68c 7ee01260
0x0034f684:  7ee4cb20 7ee31b24 0034f74c 7bc32691
Backtrace:
=>1 0x7e7e46cb joyGetPosEx+0x5b() in winmm (0x0034f65c)
  2 0x00409593 in pony (+0x9593) (0x0034f6dc)
  3 0x7ee0ce3e in user32 (+0x9ce3e) (0x0034f71c)
  4 0x7ee12523 WINPROC_call_window+0xd3() in user32 (0x0034f75c)
  5 0x7edd8f8c in user32 (+0x68f8c) (0x0034f7cc)
  6 0x7eddcb82 in user32 (+0x6cb82) (0x0034f82c)
  7 0x7eddcf9e SendMessageA+0x4e() in user32 (0x0034f86c)
  8 0x7e3f9a02 X11DRV_CreateWindow+0x472() in winex11 (0x0034fa2c)
  9 0x7ee062f3 in user32 (+0x962f3) (0x0034fc8c)
  10 0x7ee07ba2 CreateWindowExA+0x102() in user32 (0x0034fe0c)
  11 0x0040953c in pony (+0x953c) (0x0034ff08)
  12 0x7b874c7e in kernel32 (+0x54c7e) (0x0034ffe8)
  13 0xb7e089a7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7e7e46cb joyGetPosEx+0x5b in winmm: movl      $0x0,0x8(%esi)
Modules:
Module  Address                 Debug info      Name (88 modules)
PE        400000-  4b3000       Export          pony
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cb03000-7cb18000       Deferred        midimap<elf>
  \-PE  7cb10000-7cb18000       \               midimap
ELF     7cb18000-7cb30000       Deferred        msacm32<elf>
  \-PE  7cb20000-7cb30000       \               msacm32
ELF     7cb30000-7cb6c000       Deferred        wineoss<elf>
  \-PE  7cb40000-7cb6c000       \               wineoss
ELF     7cb6c000-7cbbd000       Deferred        libgcrypt.so.11
ELF     7cbbd000-7cbd2000       Deferred        libtasn1.so.3
ELF     7cbd2000-7cc00000       Deferred        libcrypt.so.1
ELF     7cc00000-7cc70000       Deferred        libgnutls.so.13
ELF     7cc70000-7cca1000       Deferred        libcups.so.2
ELF     7cca1000-7ccb5000       Deferred        winejoystick<elf>
  \-PE  7ccb0000-7ccb5000       \               winejoystick
ELF     7cf8a000-7cfbc000       Deferred        uxtheme<elf>
  \-PE  7cf90000-7cfbc000       \               uxtheme
ELF     7cfbc000-7cfc5000       Deferred        libxcursor.so.1
ELF     7cfc5000-7cfcd000       Deferred        libxrender.so.1
ELF     7cfd0000-7cfd4000       Deferred        libgpg-error.so.0
ELF     7d85b000-7d85d000       Deferred        libnvidia-tls.so.1
ELF     7d85d000-7e1cf000       Deferred        libglcore.so.1
ELF     7e1cf000-7e263000       Deferred        libgl.so.1
ELF     7e263000-7e268000       Deferred        libxdmcp.so.6
ELF     7e268000-7e26b000       Deferred        libxau.so.6
ELF     7e26b000-7e35c000       Deferred        libx11.so.6
ELF     7e35c000-7e36a000       Deferred        libxext.so.6
ELF     7e36a000-7e382000       Deferred        libice.so.6
ELF     7e382000-7e38b000       Deferred        libsm.so.6
ELF     7e38b000-7e390000       Deferred        libxfixes.so.3
ELF     7e390000-7e396000       Deferred        libxrandr.so.2
ELF     7e39f000-7e429000       Export          winex11<elf>
  \-PE  7e3b0000-7e429000       \               winex11
ELF     7e4a3000-7e4c3000       Deferred        libexpat.so.1
ELF     7e4c3000-7e4ee000       Deferred        libfontconfig.so.1
ELF     7e4ee000-7e502000       Deferred        libz.so.1
ELF     7e502000-7e56d000       Deferred        libfreetype.so.6
ELF     7e56d000-7e5b6000       Deferred        dsound<elf>
  \-PE  7e580000-7e5b6000       \               dsound
ELF     7e5b6000-7e60b000       Deferred        ddraw<elf>
  \-PE  7e5c0000-7e60b000       \               ddraw
ELF     7e60b000-7e61e000       Deferred        libresolv.so.2
ELF     7e61e000-7e63c000       Deferred        iphlpapi<elf>
  \-PE  7e630000-7e63c000       \               iphlpapi
ELF     7e63c000-7e695000       Deferred        rpcrt4<elf>
  \-PE  7e650000-7e695000       \               rpcrt4
ELF     7e695000-7e734000       Deferred        ole32<elf>
  \-PE  7e6a0000-7e734000       \               ole32
ELF     7e734000-7e75b000       Deferred        msvfw32<elf>
  \-PE  7e740000-7e75b000       \               msvfw32
ELF     7e75b000-7e795000       Deferred        avifil32<elf>
  \-PE  7e760000-7e795000       \               avifil32
ELF     7e795000-7e7bb000       Deferred        msacm32<elf>
  \-PE  7e7a0000-7e7bb000       \               msacm32
ELF     7e7bb000-7e849000       Export          winmm<elf>
  \-PE  7e7d0000-7e849000       \               winmm
ELF     7e849000-7e87d000       Deferred        winspool<elf>
  \-PE  7e850000-7e87d000       \               winspool
ELF     7e87d000-7e93a000       Deferred        comctl32<elf>
  \-PE  7e890000-7e93a000       \               comctl32
ELF     7e93a000-7e993000       Deferred        shlwapi<elf>
  \-PE  7e950000-7e993000       \               shlwapi
ELF     7e993000-7ea96000       Deferred        shell32<elf>
  \-PE  7e9a0000-7ea96000       \               shell32
ELF     7ea96000-7eb37000       Deferred        comdlg32<elf>
  \-PE  7eaa0000-7eb37000       \               comdlg32
ELF     7eb37000-7eb7f000       Deferred        advapi32<elf>
  \-PE  7eb40000-7eb7f000       \               advapi32
ELF     7eb7f000-7eb8b000       Deferred        libgcc_s.so.1
ELF     7ec75000-7ec7a000       Deferred        libxxf86vm.so.1
ELF     7ec89000-7ed49000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed49000       \               gdi32
ELF     7ed49000-7ee87000       Export          user32<elf>
  \-PE  7ed70000-7ee87000       \               user32
ELF     7ef99000-7efa4000       Deferred        libnss_files.so.2
ELF     7efa4000-7efae000       Deferred        libnss_nis.so.2
ELF     7efae000-7efc5000       Deferred        libnsl.so.1
ELF     7efc5000-7efec000       Deferred        libm.so.6
ELF     b7c86000-b7c8f000       Deferred        libnss_compat.so.2
ELF     b7c90000-b7c94000       Deferred        libdl.so.2
ELF     b7c94000-b7dd5000       Deferred        libc.so.6
ELF     b7dd6000-b7ded000       Deferred        libpthread.so.0
ELF     b7e01000-b7f15000       Export          libwine.so.1
ELF     b7f17000-b7f32000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000024 (D) E:\pony.exe
        00000025    0 <==
0000000a
        0000000c    0
        0000000b    0
00000008
        0000000d    0
        00000009    0

---

### Post by andyho on 2007-08-12
Ok... so I more or less somewhat have JS 1st Grade working.. I have quicktime running and it'll play.. glitchy as all can be, but it IS playing. If I try to run it without quicktime running, it gives me an error that the records aren't saved properly and then shuts down? Is this making any sense?!? I'm thinking maybe if I convert it to an iso and then mount it as a virtual drive it might play better?

---

### Post by andyho on 2007-08-13
wow... no one's encountered these problems?! :(

---

### Post by syssyphus on 2007-08-22
I just installed jumpstart artist, and it is working good... the audio is a little choppy sometimes, but definitely playable.

---

