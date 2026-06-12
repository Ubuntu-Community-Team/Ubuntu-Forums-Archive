---
title: "Dark Ages"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by Spoken on 2008-04-15
I'm trying to get one of my favorite windows games to work through wine.  when i try to run it through wine i get this error.  THE WINE DATABASE HAS NOTHING ABOUT THIS GAME!  IS THERE ANYTHING IN THE CODE SPECIFIALLY THAT TELLS ME WHATS WRONG?  I'm a noob.

NOTICE: These are the error messages i get with compiz fusion turned OFF!!

[Dark Ages (the game i want to get to work)]("http://www.darkages.com")

===============================================
Here is the error i get RIGHT AFTER i try to INSTALL
==================================================
```

fixme:spoolsv:serv_main (0 (nil))
fixme:shell:IShellLinkA_fnGetPath (0x188a08): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:IShellLinkA_fnGetPath (0x188a08): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\KRU\\Dark Ages\\thidchk.dll") not found
fixme:shell:DllCanUnloadNow stub
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\KRU\\Dark Ages\\Launch.dll") not found
admin@dell:~$ 

```
======================================
Here is the error i get after i try to LAUNCH
======================================
```

fixme:spoolsv:serv_main (0 (nil))
wine: Unhandled page fault on read access to 0x00000010 at address 0x7dad36f5 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000010 in 32-bit code (0x7dad36f5).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7dad36f5 ESP:0033ee84 EBP:0033ee88 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:7c0e1688 ECX:7c1a2600 EDX:00000005
 ESI:0033ef30 EDI:7ddf019d
Stack dump:
0x0033ee84:  7de0ec54 0033f178 7dd69f1f 7c0e1688
0x0033ee94:  00008620 7c1a2600 7ddf0104 7de0f8b0
0x0033eea4:  b7e2f8ac 00000300 00000021 00000001
0x0033eeb4:  7dc994c0 b7e2e541 7c0a4c48 7c0e1688
0x0033eec4:  79800000 0033eef8 7daae906 7dc994c0
0x0033eed4:  b7e2f8ac b7e2e541 0033f050 000003c0
Backtrace:
=>1 0x7dad36f5 in i965_dri.so (+0x856f5) (0x0033ee88)
  2 0x7dd69f1f IWineD3DImpl_FillGLCaps+0x86dc() in wined3d (0x0033f178)
  3 0x7dd73549 InitAdapters+0x1f9a() in wined3d (0x0033f638)
  4 0x7dde282a WineDirect3DCreate+0x22() in wined3d (0x0033f668)
  5 0x7ed70266 in ddraw (+0x20266) (0x0033f6c8)
  6 0x7ed7085b DirectDrawCreate+0xbd() in ddraw (0x0033f718)
  7 0x0058e7e1 in darkages (+0x18e7e1) (0x0033f7a8)
  8 0x0058e9c2 in darkages (+0x18e9c2) (0x0033fe70)
  9 0x0064fcb7 in darkages (+0x24fcb7) (0x0033ff08)
  10 0x7b86f7fa in kernel32 (+0x4f7fa) (0x0033ffe8)
  11 0xb7e5c27b wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7dad36f5: movl        0x10(%eax),%eax
Modules:
Module  Address                 Debug info      Name (115 modules)
PE        340000-  38e000       Deferred        scskapplink
PE        400000-  928000       Export          darkages
PE      10000000-10057000       Deferred        binkw32
PE      21100000-2115d000       Deferred        mss32
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7da4e000-7dca5000       Export          i965_dri.so
ELF     7dca5000-7dcaf000       Deferred        libdrm.so.2
ELF     7dcaf000-7dcb2000       Deferred        libxdamage.so.1
ELF     7dcb2000-7dd13000       Deferred        libgl.so.1
ELF     7dd13000-7de13000       Export          wined3d<elf>
  \-PE  7dd30000-7de13000       \               wined3d
ELF     7de13000-7de64000       Deferred        libgcrypt.so.11
ELF     7de64000-7de68000       Deferred        libgpg-error.so.0
ELF     7de68000-7de78000       Deferred        libtasn1.so.3
ELF     7de78000-7de7a000       Deferred        libkeyutils.so.1
ELF     7de7a000-7de82000       Deferred        libkrb5support.so.0
ELF     7de82000-7deb0000       Deferred        libcrypt.so.1
ELF     7deb0000-7df20000       Deferred        libgnutls.so.13
ELF     7df20000-7df45000       Deferred        libk5crypto.so.3
ELF     7df45000-7dfcd000       Deferred        libkrb5.so.3
ELF     7dfcd000-7dff6000       Deferred        libgssapi_krb5.so.2
ELF     7dff6000-7e02b000       Deferred        libcups.so.2
ELF     7e06f000-7e072000       Deferred        libcom_err.so.2
ELF     7e082000-7e0b4000       Deferred        uxtheme<elf>
  \-PE  7e090000-7e0b4000       \               uxtheme
ELF     7e0b4000-7e0da000       Deferred        msacm32<elf>
  \-PE  7e0c0000-7e0da000       \               msacm32
ELF     7e0da000-7e0f1000       Deferred        msacm32<elf>
  \-PE  7e0e0000-7e0f1000       \               msacm32
ELF     7e0f1000-7e1b7000       Deferred        libasound.so.2
ELF     7e1cd000-7e202000       Deferred        winealsa<elf>
  \-PE  7e1e0000-7e202000       \               winealsa
ELF     7e202000-7e20b000       Deferred        libxcursor.so.1
ELF     7e20b000-7e210000       Deferred        libxfixes.so.3
ELF     7e210000-7e213000       Deferred        libxcomposite.so.1
ELF     7e213000-7e219000       Deferred        libxrandr.so.2
ELF     7e219000-7e221000       Deferred        libxrender.so.1
ELF     7e221000-7e226000       Deferred        libxdmcp.so.6
ELF     7e226000-7e229000       Deferred        libxau.so.6
ELF     7e229000-7e31a000       Deferred        libx11.so.6
ELF     7e31a000-7e328000       Deferred        libxext.so.6
ELF     7e328000-7e32d000       Deferred        libxxf86vm.so.1
ELF     7e32d000-7e345000       Deferred        libice.so.6
ELF     7e345000-7e34d000       Deferred        libsm.so.6
ELF     7e34d000-7e361000       Deferred        midimap<elf>
  \-PE  7e350000-7e361000       \               midimap
ELF     7e363000-7e3f1000       Deferred        winex11<elf>
  \-PE  7e370000-7e3f1000       \               winex11
ELF     7e486000-7e4a6000       Deferred        libexpat.so.1
ELF     7e4a6000-7e4d1000       Deferred        libfontconfig.so.1
ELF     7e4d1000-7e4e6000       Deferred        libz.so.1
ELF     7e4e6000-7e556000       Deferred        libfreetype.so.6
ELF     7e56c000-7e5a2000       Deferred        winspool<elf>
  \-PE  7e570000-7e5a2000       \               winspool
ELF     7e5a2000-7e5b6000       Deferred        lz32<elf>
  \-PE  7e5b0000-7e5b6000       \               lz32
ELF     7e5b6000-7e5cf000       Deferred        version<elf>
  \-PE  7e5c0000-7e5cf000       \               version
ELF     7e5cf000-7e633000       Deferred        setupapi<elf>
  \-PE  7e5e0000-7e633000       \               setupapi
ELF     7e633000-7e6d4000       Deferred        oleaut32<elf>
  \-PE  7e640000-7e6d4000       \               oleaut32
ELF     7e6d4000-7e793000       Deferred        comctl32<elf>
  \-PE  7e6e0000-7e793000       \               comctl32
ELF     7e793000-7e89b000       Deferred        shell32<elf>
  \-PE  7e7a0000-7e89b000       \               shell32
ELF     7e89b000-7e8f2000       Deferred        shlwapi<elf>
  \-PE  7e8b0000-7e8f2000       \               shlwapi
ELF     7e8f2000-7e913000       Deferred        mpr<elf>
  \-PE  7e900000-7e913000       \               mpr
ELF     7e913000-7e960000       Deferred        wininet<elf>
  \-PE  7e920000-7e960000       \               wininet
ELF     7e960000-7e9a8000       Deferred        dbghelp<elf>
  \-PE  7e970000-7e9a8000       \               dbghelp
ELF     7e9a8000-7e9bf000       Deferred        imagehlp<elf>
  \-PE  7e9b0000-7e9bf000       \               imagehlp
ELF     7e9bf000-7e9de000       Deferred        imm32<elf>
  \-PE  7e9d0000-7e9de000       \               imm32
ELF     7e9de000-7ea6a000       Deferred        winmm<elf>
  \-PE  7e9f0000-7ea6a000       \               winmm
ELF     7ea6a000-7eac8000       Deferred        rpcrt4<elf>
  \-PE  7ea80000-7eac8000       \               rpcrt4
ELF     7eac8000-7eb61000       Deferred        gdi32<elf>
  \-PE  7eae0000-7eb61000       \               gdi32
ELF     7eb61000-7eca1000       Deferred        user32<elf>
  \-PE  7eb80000-7eca1000       \               user32
ELF     7eca1000-7ed41000       Deferred        ole32<elf>
  \-PE  7ecb0000-7ed41000       \               ole32
ELF     7ed41000-7ed96000       Export          ddraw<elf>
  \-PE  7ed50000-7ed96000       \               ddraw
ELF     7ed96000-7ede5000       Deferred        advapi32<elf>
  \-PE  7eda0000-7ede5000       \               advapi32
ELF     7ede5000-7edf8000       Deferred        libresolv.so.2
ELF     7edf9000-7ee0e000       Deferred        psapi<elf>
  \-PE  7ee00000-7ee0e000       \               psapi
ELF     7ee0e000-7ee2c000       Deferred        iphlpapi<elf>
  \-PE  7ee10000-7ee2c000       \               iphlpapi
ELF     7ee2c000-7ee57000       Deferred        ws2_32<elf>
  \-PE  7ee30000-7ee57000       \               ws2_32
ELF     7ee57000-7ee70000       Deferred        wsock32<elf>
  \-PE  7ee60000-7ee70000       \               wsock32
ELF     7ef8f000-7ef9a000       Deferred        libnss_files.so.2
ELF     7ef9a000-7efa4000       Deferred        libnss_nis.so.2
ELF     7efa4000-7efbc000       Deferred        libnsl.so.1
ELF     7efbc000-7efc5000       Deferred        libnss_compat.so.2
ELF     7efc5000-7efea000       Deferred        libm.so.6
ELF     b7cd8000-b7cdc000       Deferred        libdl.so.2
ELF     b7cdc000-b7e26000       Deferred        libc.so.6
ELF     b7e27000-b7e3f000       Deferred        libpthread.so.0
ELF     b7e55000-b7f69000       Export          libwine.so.1
ELF     b7f6b000-b7f87000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\KRU\Dark Ages\Darkages.exe
        00000009    0 <==
0000000c 
        00000017    0
        00000016    0
        00000011    0
        00000010    0
        0000000e    0
        0000000d    0
00000012 
        00000015    0
        00000014    0
        00000013    0
0000001c 
        0000001e    0
        0000001d    0
Backtrace:
=>1 0x7dad36f5 in i965_dri.so (+0x856f5) (0x0033ee88)
  2 0x7dd69f1f IWineD3DImpl_FillGLCaps+0x86dc() in wined3d (0x0033f178)
  3 0x7dd73549 InitAdapters+0x1f9a() in wined3d (0x0033f638)
  4 0x7dde282a WineDirect3DCreate+0x22() in wined3d (0x0033f668)
  5 0x7ed70266 in ddraw (+0x20266) (0x0033f6c8)
  6 0x7ed7085b DirectDrawCreate+0xbd() in ddraw (0x0033f718)
  7 0x0058e7e1 in darkages (+0x18e7e1) (0x0033f7a8)
  8 0x0058e9c2 in darkages (+0x18e9c2) (0x0033fe70)
  9 0x0064fcb7 in darkages (+0x24fcb7) (0x0033ff08)
  10 0x7b86f7fa in kernel32 (+0x4f7fa) (0x0033ffe8)
  11 0xb7e5c27b wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

---

### Post by 3rdalbum on 2008-04-15
Looks like it's a problem with the Direct 3D support. If you're running Compiz, turn it off. But generally when you get a big error message like that (a "stack trace") it just means that Wine crashed due to something not being supported.

---

### Post by Spoken on 2008-04-15
well, i turned compiz off, and i got a different effor message, what do i do now lol :P

---

### Post by Dr Small on 2008-04-15
Post the different error message (and wrap it in code tags, please :) ).

---

### Post by Spoken on 2008-04-17
.

---

### Post by Spoken on 2008-04-17
:confused:

---

### Post by Spoken on 2008-04-17
:confused:

---

### Post by Faud on 2008-04-17
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5255](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5255)

Is this the game ? If it is then it will work in WINE. What he means by code tags is [code ] type message here [/code ] (without the breaks) so it looks like ```
type message here
```
Soo, please post the new error message that you get when you try and launch the game w/compiz off. Also you can ignore the fixme messages as they are not error and you can leave them off of your post.
Also there is a WINE specific forum here on Ubuntu forums. You may get better support there.

---

### Post by Spoken on 2008-04-17
thats not the game.  click the link that i have on my first post.

and these errors are with compiz off.

---

### Post by Faud on 2008-04-17
Sorry Im at work and cant see any gaming sites, what kind of game is it and I'll see if I can get some research done

---

### Post by Spoken on 2008-04-17
its a mmorg, the company that runs it is "kru interactive"

the website to the game is [http://www.darkages.com](http://www.darkages.com)

umm...idk what else to say to describe it.

---

### Post by Spoken on 2008-04-18
:guitar:

---

### Post by Spoken on 2008-04-18
:lolflag:

---

### Post by Spoken on 2008-04-18
:(

---

### Post by Spoken on 2008-04-18
so yea, im still having problems.  there is no way im the only one that has ever played this game lol. its a very popular game.  someone must know!

---

### Post by Spoken on 2008-04-18
:mad:

---

### Post by Kinst on 2008-04-19
Well it's complaining about MSVBVM60.DLL and MFC42.DLL, why don't you try finding the windows versions and setting them to native?

---

### Post by Spoken on 2008-04-19
well, i was waiting for someone to tell me something like that.  cause i have no clue what to do.

---

