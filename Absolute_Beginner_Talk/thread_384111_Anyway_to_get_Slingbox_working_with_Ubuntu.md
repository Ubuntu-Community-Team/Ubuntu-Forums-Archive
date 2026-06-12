---
title: "Anyway to get Slingbox working with Ubuntu?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by diargasm on 2007-03-14
Any easy walkthrough that wont risk damaging my computer?

---

### Post by orkim on 2007-03-14
I looked into this at one point (a year ago or so) but wasn't able to find anything that was going to work under Linux.  As far as I know this is not supported by any sort of driver or anything yet.  I would imagine that the V4L stuff would be where you might soon see support for this device.

Sorry to be the bearer of bad news.

-orkim

---

### Post by Mach1US on 2007-06-07
You can try this guide
[http://www.slingcommunity.com/article/17253/How-To-Run-SlingPlayer-on-Linux-OS/](http://www.slingcommunity.com/article/17253/How-To-Run-SlingPlayer-on-Linux-OS/)
I have got it up and running , just need to figure out the audio driver problem.
if any body knows  the fix for that issue please post to this thread , will be much appreciated . ):P

---

### Post by msharp on 2007-12-07
yeah i had the same prob found my answer here
[[COLOR="Blue"]cyberpunkcafe's slingplayer on linux guide[/COLOR]]("http://www.cyberpunkcafe.com/page.php?74")
:guitar:

---

### Post by Christobevii3 on 2008-01-23
I get this error output when I try to run slingplayer after installing...

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:create_server class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:CoGetClassObject no class object {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} could be created for context 0x5
err:ole:CoGetClassObject class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:create_server class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:CoGetClassObject no class object {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} could be created for context 0x5
err:ole:CoGetClassObject class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:create_server class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:CoGetClassObject no class object {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} could be created for context 0x5
err:ole:CoGetClassObject class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:create_server class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:CoGetClassObject no class object {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} could be created for context 0x5
err:ole:CoGetClassObject class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:create_server class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:CoGetClassObject no class object {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} could be created for context 0x5
err:ole:CoGetClassObject class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:create_server class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:CoGetClassObject no class object {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} could be created for context 0x5
err:ole:CoGetClassObject class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:create_server class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:CoGetClassObject no class object {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} could be created for context 0x5
err:ole:CoGetClassObject class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:create_server class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:CoGetClassObject no class object {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} could be created for context 0x5
err:ole:CoGetClassObject class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:create_server class {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} not registered
err:ole:CoGetClassObject no class object {cb8555cc-9128-11d1-ad9b-00c04fd8fdff} could be created for context 0x5
fixme:win:EnumDisplayDevicesW ((null),0,0x337bd4,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x14bd88)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x155f40)->((nil),00001008)
err:ddraw:IDirectDrawImpl_QueryInterface (0x155f40) The App is requesting a D3D device, but a non-OpenGL surface type was choosen. Prepare for trouble!
err:ddraw:IDirectDrawImpl_QueryInterface  (0x155f40) You may want to contact wine-devel for help
err:ddraw:IDirectDrawImpl_QueryInterface (0x155f40)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x14d8b8): No interface found
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1620c8,0x00000010,0x3381c4) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1620c8,0x00000020,0x3381c4) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1620c8,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1620c8,0x00000020,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1620c8,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1620c8,0x00000020,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1620c8,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1620c8,0x00000020,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1620c8,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1620c8,0x00000020,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1620c8,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1620c8,0x00000020,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1620c8,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1620c8,0x00000020,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x1620c8,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x1620c8,0x00000020,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x167560,0x00000010,0x336f70) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x167560,0x00000020,0x336f70) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x167560,0x00000010,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x167560,0x00000020,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x167560,0x00000010,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x167560,0x00000020,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x167560,0x00000010,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x167560,0x00000020,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x167560,0x00000010,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x167560,0x00000020,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x167560,0x00000010,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x167560,0x00000020,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x167560,0x00000010,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x167560,0x00000020,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x167560,0x00000010,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x167560,0x00000020,0x336f58) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x15f560,0x00000010,0x3381c4) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x15f560,0x00000020,0x3381c4) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x15f560,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x15f560,0x00000020,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x15f560,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x15f560,0x00000020,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x15f560,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x15f560,0x00000020,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x15f560,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x15f560,0x00000020,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x15f560,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x15f560,0x00000020,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x15f560,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x15f560,0x00000020,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x00000021,0x15f560,0x00000010,0x3380c8) stub
fixme:ntdll:NtQuerySystemInformation (0x0000002d,0x15f560,0x00000020,0x3380c8) stub
err:ole:OLEPictureImpl_LoadPNG Trying to load PNG picture, but PNG supported not compiled in.
wine: Call from 0x7b8440c0 to unimplemented function gdiplus.dll.GdipDrawImageRectI, aborting
wine: Unimplemented function gdiplus.dll.GdipDrawImageRectI called at address 0x7b8440c0 (thread 0014), starting debugger...
Unhandled exception: unimplemented function gdiplus.dll.GdipDrawImageRectI called in 32-bit code (0x7b844138).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b844138 ESP:00337bd8 EBP:00337c3c EFLAGS:00200212(   - 00      - -IA1)
 EAX:7b82ee9d EBX:7b8b0888 ECX:00000000 EDX:00166358
 ESI:00166358 EDI:00000000
Stack dump:
0x00337bd8:  00337c60 00000008 7eda7764 000003e0
0x00337be8:  80000100 00000001 00000000 7b8440c0
0x00337bf8:  00000002 7e6d9c20 7e6da63c 7ed5f409
0x00337c08:  7e6e1110 00337c5c 7e6d732d 00000000
0x00337c18:  000003e0 00000000 00000000 00000000
0x00337c28:  00000000 027f0c7f 027f0c7f 00000000
Backtrace:
=>1 0x7b844138 RaiseException+0x78(code=0x80000100, flags=0x1, nbargs=0x2, args=0x337c60) [/build/buildd/wine-0.9.46/dlls/kernel32/except.c:85] in kernel32 (0x00337c3c)
  2 0x7e6d9bc1 __wine_spec_unimplemented_stub+0x41(module=0x7e6d9c20, function=0x7e6da63c) [/build/buildd/wine-0.9.46/dlls/winecrt0/stub.c:36] in gdiplus (0x00337c6c)
  3 0x7e6cad57 in gdiplus (+0xad57) (0x00667740)
  4 0x00667800 (0x101489ac)
  5 0x100d38d0 in sbcore (+0xd38d0) (0x100d3880)
  6 0x748b5610 (0x245c8b53)
  7 0x00000000 (0x00000000)
0x7b844138 RaiseException+0x78 [/build/buildd/wine-0.9.46/dlls/kernel32/except.c:85] in kernel32: movl  0xfffffffc(%ebp),%ebx
Unable to open file '/build/buildd/wine-0.9.46/dlls/kernel32/except.c'
Modules:
Module  Address                 Debug info      Name (113 modules)
PE        350000-  375000       Deferred        sbil
PE        380000-  393000       Deferred        zlib1
PE        400000-  428000       Deferred        slingplayer
PE       1420000- 14a7000       Deferred        sbds.ax
PE       14b0000- 14c7000       Deferred        smst
PE       8120000- 8180000       Deferred        wmadmod
PE       8900000- 89d5000       Deferred        wmvdmod
PE       9200000- 9237000       Deferred        qasf
PE      10000000-108a7000       Export          sbcore
PE      35500000-35659000       Deferred        quartz
PE      74980000-74a8e000       Deferred        msxml3
PE      757f0000-75822000       Deferred        qcap
ELF     7b800000-7b929000       Dwarf           kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d8f3000-7d90b000       Deferred        msdmo<elf>
  \-PE  7d900000-7d90b000       \               msdmo
ELF     7dbb7000-7dc97000       Deferred        wined3d<elf>
  \-PE  7dbd0000-7dc97000       \               wined3d
ELF     7dc97000-7dcec000       Deferred        ddraw<elf>
  \-PE  7dca0000-7dcec000       \               ddraw
ELF     7dcec000-7dd13000       Deferred        msvfw32<elf>
  \-PE  7dcf0000-7dd13000       \               msvfw32
ELF     7de24000-7de39000       Deferred        midimap<elf>
  \-PE  7de30000-7de39000       \               midimap
ELF     7de39000-7de60000       Deferred        msacm32<elf>
  \-PE  7de40000-7de60000       \               msacm32
ELF     7de60000-7de78000       Deferred        msacm32<elf>
  \-PE  7de70000-7de78000       \               msacm32
ELF     7de78000-7deb2000       Deferred        wineoss<elf>
  \-PE  7de80000-7deb2000       \               wineoss
ELF     7deb2000-7df40000       Deferred        winmm<elf>
  \-PE  7dec0000-7df40000       \               winmm
ELF     7e210000-7e242000       Deferred        uxtheme<elf>
  \-PE  7e220000-7e242000       \               uxtheme
ELF     7e242000-7e24b000       Deferred        libxcursor.so.1
ELF     7e24b000-7e268000       Deferred        imm32<elf>
  \-PE  7e250000-7e268000       \               imm32
ELF     7e268000-7e26e000       Deferred        libxrandr.so.2
ELF     7e26e000-7e276000       Deferred        libxrender.so.1
ELF     7e276000-7e279000       Deferred        libxinerama.so.1
ELF     7e279000-7e283000       Deferred        libdrm.so.2
ELF     7e283000-7e288000       Deferred        libxfixes.so.3
ELF     7e288000-7e28b000       Deferred        libxdamage.so.1
ELF     7e28b000-7e290000       Deferred        libxxf86vm.so.1
ELF     7e290000-7e2f1000       Deferred        libgl.so.1
ELF     7e2f1000-7e2f6000       Deferred        libxdmcp.so.6
ELF     7e2f6000-7e2f9000       Deferred        libxau.so.6
ELF     7e2f9000-7e3ea000       Deferred        libx11.so.6
ELF     7e3ea000-7e3f8000       Deferred        libxext.so.6
ELF     7e410000-7e49f000       Deferred        winex11<elf>
  \-PE  7e420000-7e49f000       \               winex11
ELF     7e522000-7e542000       Deferred        libexpat.so.1
ELF     7e542000-7e56d000       Deferred        libfontconfig.so.1
ELF     7e56d000-7e582000       Deferred        libz.so.1
ELF     7e582000-7e5f2000       Deferred        libfreetype.so.6
ELF     7e60a000-7e61e000       Deferred        oleacc<elf>
  \-PE  7e610000-7e61e000       \               oleacc
ELF     7e61e000-7e632000       Deferred        lz32<elf>
  \-PE  7e620000-7e632000       \               lz32
ELF     7e632000-7e64c000       Deferred        version<elf>
  \-PE  7e640000-7e64c000       \               version
ELF     7e64c000-7e66c000       Deferred        mpr<elf>
  \-PE  7e650000-7e66c000       \               mpr
ELF     7e66c000-7e6b4000       Deferred        wininet<elf>
  \-PE  7e680000-7e6b4000       \               wininet
ELF     7e6b4000-7e6e7000       Dwarf           gdiplus<elf>
  \-PE  7e6c0000-7e6e7000       \               gdiplus
ELF     7e6e7000-7e784000       Deferred        oleaut32<elf>
  \-PE  7e700000-7e784000       \               oleaut32
ELF     7e784000-7e7dd000       Deferred        rpcrt4<elf>
  \-PE  7e790000-7e7dd000       \               rpcrt4
ELF     7e7dd000-7e87e000       Deferred        ole32<elf>
  \-PE  7e7f0000-7e87e000       \               ole32
ELF     7e87e000-7e8a0000       Deferred        oledlg<elf>
  \-PE  7e880000-7e8a0000       \               oledlg
ELF     7e8a0000-7e8d4000       Deferred        winspool<elf>
  \-PE  7e8b0000-7e8d4000       \               winspool
ELF     7e8d4000-7e992000       Deferred        comctl32<elf>
  \-PE  7e8e0000-7e992000       \               comctl32
ELF     7e992000-7e9eb000       Deferred        shlwapi<elf>
  \-PE  7e9a0000-7e9eb000       \               shlwapi
ELF     7e9eb000-7eaee000       Deferred        shell32<elf>
  \-PE  7ea00000-7eaee000       \               shell32
ELF     7eaee000-7eb8f000       Deferred        comdlg32<elf>
  \-PE  7eb00000-7eb8f000       \               comdlg32
ELF     7eb8f000-7ebf7000       Deferred        msvcrt<elf>
  \-PE  7eba0000-7ebf7000       \               msvcrt
ELF     7ebf7000-7ec24000       Deferred        ws2_32<elf>
  \-PE  7ec00000-7ec24000       \               ws2_32
ELF     7ec24000-7ecbf000       Deferred        gdi32<elf>
  \-PE  7ec40000-7ecbf000       \               gdi32
ELF     7ecbf000-7edfd000       Deferred        user32<elf>
  \-PE  7ece0000-7edfd000       \               user32
ELF     7edfd000-7ee10000       Deferred        libresolv.so.2
ELF     7ee14000-7ee28000       Deferred        userenv<elf>
  \-PE  7ee20000-7ee28000       \               userenv
ELF     7ee28000-7ee46000       Deferred        iphlpapi<elf>
  \-PE  7ee30000-7ee46000       \               iphlpapi
ELF     7ee46000-7ee8f000       Deferred        advapi32<elf>
  \-PE  7ee50000-7ee8f000       \               advapi32
ELF     7efae000-7efb9000       Deferred        libnss_files.so.2
ELF     7efb9000-7efc3000       Deferred        libnss_nis.so.2
ELF     7efc3000-7efe8000       Deferred        libm.so.6
ELF     7efe8000-7f000000       Deferred        libnsl.so.1
ELF     f7d03000-f7d0c000       Deferred        libnss_compat.so.2
ELF     f7d0d000-f7d11000       Deferred        libdl.so.2
ELF     f7d11000-f7e5b000       Deferred        libc.so.6
ELF     f7e5c000-f7e74000       Deferred        libpthread.so.0
ELF     f7e8c000-f7fa0000       Deferred        libwine.so.1
ELF     f7fa2000-f7fc0000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000013 (D) C:\Program Files\Sling Media\SlingPlayer\SlingPlayer.exe
        00000017    0
        00000016    0
        00000015    0
        00000014    0 <==
0000000a 
        0000000b    0
00000008 
        0000000e    0
        0000000d    0
        0000000c    0
wine: Call from 0x7b8440c0 to unimplemented function gdiplus.dll.GdipDrawImageRectRectI, aborting
wine: Call from 0x7b8440c0 to unimplemented function gdiplus.dll.GdipDrawLinesI, aborting
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x155f40)->((nil),00000008)

```

---

### Post by Mr. Electric Wizard on 2008-02-25
I am getting the same errors as above.
Anybody know how I can fix this?

---

