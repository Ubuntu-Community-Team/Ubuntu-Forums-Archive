---
title: "Running Diablo 2 error"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by ignorance on 2006-04-03
Well i got it installed and can watch a part of the intro but then it quitst with this given error.

```
Unhandeld Violation: Acces_violation (C0000005)
```

this is the fragement of wine

```
christophe@Winkill:~/.wine/drive_c/Program/Diablo$ fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 2069BB68 in module game
fixme:dbghelp:sffip_cb NIY on 'C:\Projects\Diablo2\Release\D2Glide.pdb'
fixme:dbghelp:sffip_cb NIY on 'C:\Projects\Diablo2\Release\D2Win.pdb'
fixme:dbghelp:sffip_cb NIY on 'C:\Projects\Diablo2\Release\D2Sound.pdb'
fixme:dbghelp:sffip_cb NIY on 'C:\Projects\Diablo2\Release\D2MCPClient.pdb'
fixme:dbghelp:sffip_cb NIY on 'C:\Projects\Diablo2\Release\D2Launch.pdb'
fixme:dbghelp:sffip_cb NIY on 'C:\Projects\Diablo2\Release\D2gfx.pdb'
fixme:dbghelp:sffip_cb NIY on 'C:\Projects\Diablo2\Release\D2Net.pdb'
fixme:dbghelp:sffip_cb NIY on 'C:\Projects\Diablo2\Release\D2Lang.pdb'
fixme:dbghelp:sffip_cb NIY on 'C:\Projects\Diablo2\Release\D2CMP.pdb'
fixme:dbghelp:sffip_cb NIY on 'C:\Projects\Diablo2\Release\Bnclient.pdb'
fixme:dbghelp:sffip_cb NIY on 'C:\Projects\Diablo2\Release\Fog.pdb'
fixme:dbghelp:sffip_cb NIY on 'D:\D2\Release\Storm.pdb'
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\ddraw.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image ntdll.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\opengl32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\dbghelp.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\msacm32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\wineoss.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\psapi.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\imagehlp.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\midimap.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\msacm.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\uxtheme.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\imm32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\winex11.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\winmm.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\dsound.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\ws2_32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\wsock32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\lz32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\version.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\winspool.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\comctl32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\iphlpapi.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\rpcrt4.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\ole32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\shlwapi.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\shell32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\comdlg32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\advapi32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\gdi32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\user32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\msvcrt.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\crtdll.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image kernel32.dll
fixme:winmm:MMDRV_Exit Closing while ll-driver open
wine: Unhandled page fault on read access to 0x71e19080 at address 0x6f9e4572 (thread 0017), starting debugger...
WineDbg starting on pid 0xa
Unhandled exception: page fault on read access to 0x71e19080 in 32-bit code (0x6f9e4572).
fixme:dbghelp:sffip_cb NIY on 'C:\Projects\Diablo2\Release\D2Sound.pdb'
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:117f GS:0033
 EIP:6f9e4572 ESP:7178ea34 EBP:7beadae0 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000001 EBX:00000000 ECX:71e19038 EDX:7f941de4
 ESI:71e19038 EDI:7db24f10
Stack dump:
0x7178ea34:  6f9e4bbf 6f9e2dd8 7db24f10 7fd70000
0x7178ea44:  7178eb48 7fcf2604 b7df6731 00000000
0x7178ea54:  00000000 00000000 00000000 00869330
0x7178ea64:  00045564 7178eb48 7fcd7629 00000000
0x7178ea74:  00000001 7fe3ae50 7178ea98 7178eb28
0x7178ea84:  7bef3ce4 7178eb28 6f9e2d80 00000000
022f: sel=117f base=7db24000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x6f9e4572 in d2sound (+0x4572) (0x6f9e4572)
0x6f9e4572: movl        0x48(%ecx),%edx
Modules:
Module  Address                 Debug info      Name (123 modules)
PE      0x00400000-0045c000     Deferred        game
PE      0x10000000-10041000     Deferred        binkw32
PE      0x60000000-6002e000     Deferred        ijl11
PE      0x6f870000-6f88a000     Deferred        d2glide
PE      0x6f900000-6f9d3000     Deferred        d2win
PE      0x6f9e0000-6f9f7000     Export          d2sound
PE      0x6fa50000-6fa65000     Deferred        d2mcpclient
PE      0x6fa70000-6fa9e000     Deferred        d2launch
PE      0x6faa0000-6fac1000     Deferred        d2gfx
PE      0x6fc30000-6fc3d000     Deferred        d2net
PE      0x6fc40000-6fc55000     Deferred        d2lang
PE      0x6fe10000-6ff18000     Deferred        d2cmp
PE      0x6ff20000-6ff3f000     Deferred        bnclient
PE      0x6ff60000-6ffa6000     Deferred        fog
PE      0x6ffb0000-6fff5000     Deferred        storm
ELF     0x72545000-725c0000     Deferred        ddraw<elf>
  \-PE  0x72560000-725c0000     \               ddraw
ELF     0x7396f000-73977000     Deferred        libxrender.so.1
ELF     0x7be86000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
PE      0x7bf60000-7bf7a000     Deferred        smackw32
ELF     0x7bf8a000-7c000000     Deferred        libglu.so.1
ELF     0x7c20a000-7c2a0000     Deferred        opengl32<elf>
  \-PE  0x7c240000-7c2a0000     \               opengl32
PE      0x7c2a0000-7c2c3000     Deferred        glide3x
ELF     0x7cac1000-7cb00000     Deferred        dbghelp<elf>
  \-PE  0x7cad0000-7cb00000     \               dbghelp
ELF     0x7d789000-7d7ad000     Deferred        msacm32<elf>
  \-PE  0x7d790000-7d7ad000     \               msacm32
ELF     0x7d7ad000-7d7f0000     Deferred        wineoss<elf>
  \-PE  0x7d7c0000-7d7f0000     \               wineoss
ELF     0x7da3b000-7da50000     Deferred        psapi<elf>
  \-PE  0x7da40000-7da50000     \               psapi
ELF     0x7da6d000-7da84000     Deferred        imagehlp<elf>
  \-PE  0x7da70000-7da84000     \               imagehlp
ELF     0x7da84000-7da99000     Deferred        midimap<elf>
  \-PE  0x7da90000-7da99000     \               midimap
ELF     0x7da99000-7dab0000     Deferred        msacm<elf>
  \-PE  0x7daa0000-7dab0000     \               msacm
ELF     0x7db35000-7db81000     Deferred        libgcrypt.so.11
ELF     0x7db81000-7dbe3000     Deferred        libgnutls.so.11
ELF     0x7dbe3000-7dc00000     Deferred        libcups.so.2
ELF     0x7dc40000-7dc50000     Deferred        libtasn1.so.2
ELF     0x7dc5b000-7dc5f000     Deferred        libgpg-error.so.0
ELF     0x7dc9b000-7dccc000     Deferred        uxtheme<elf>
  \-PE  0x7dca0000-7dccc000     \               uxtheme
ELF     0x7dcea000-7dd06000     Deferred        imm32<elf>
  \-PE  0x7dcf0000-7dd06000     \               imm32
ELF     0x7dd06000-7dd22000     Deferred        ximcp.so.2
ELF     0x7dd22000-7dd2b000     Deferred        librt.so.1
ELF     0x7dd33000-7dd37000     Deferred        libxfixes.so.3
ELF     0x7ddf1000-7e688000     Deferred        fglrx_dri.so
ELF     0x7e688000-7e727000     Deferred        libgl.so.1
ELF     0x7e727000-7e7e7000     Deferred        libx11.so.6
ELF     0x7e7e7000-7e7f4000     Deferred        libxext.so.6
ELF     0x7e7f4000-7e80d000     Deferred        libice.so.6
ELF     0x7e80d000-7e88c000     Deferred        winex11<elf>
  \-PE  0x7e820000-7e88c000     \               winex11
ELF     0x7e88c000-7e8ab000     Deferred        libexpat.so.1
ELF     0x7e8ab000-7e8d9000     Deferred        libfontconfig.so.1
ELF     0x7e8d9000-7e8ed000     Deferred        libz.so.1
ELF     0x7e8ed000-7e957000     Deferred        libfreetype.so.6
ELF     0x7e957000-7e9de000     Deferred        winmm<elf>
  \-PE  0x7e960000-7e9de000     \               winmm
ELF     0x7e9de000-7ea2f000     Deferred        dsound<elf>
  \-PE  0x7e9f0000-7ea2f000     \               dsound
ELF     0x7ea2f000-7ea58000     Deferred        ws2_32<elf>
  \-PE  0x7ea40000-7ea58000     \               ws2_32
ELF     0x7ea58000-7ea71000     Deferred        wsock32<elf>
  \-PE  0x7ea60000-7ea71000     \               wsock32
ELF     0x7ea71000-7ea85000     Deferred        lz32<elf>
  \-PE  0x7ea80000-7ea85000     \               lz32
ELF     0x7ea85000-7ea9e000     Deferred        version<elf>
  \-PE  0x7ea90000-7ea9e000     \               version
ELF     0x7ea9e000-7eac8000     Deferred        winspool<elf>
  \-PE  0x7eab0000-7eac8000     \               winspool
ELF     0x7eac8000-7eb7d000     Deferred        comctl32<elf>
  \-PE  0x7ead0000-7eb7d000     \               comctl32
ELF     0x7eb7d000-7eb9b000     Deferred        iphlpapi<elf>
  \-PE  0x7eb80000-7eb9b000     \               iphlpapi
ELF     0x7eb9b000-7ebe3000     Deferred        rpcrt4<elf>
  \-PE  0x7ebb0000-7ebe3000     \               rpcrt4
ELF     0x7ebe3000-7ec6f000     Deferred        ole32<elf>
  \-PE  0x7ec00000-7ec6f000     \               ole32
ELF     0x7ec6f000-7ecc7000     Deferred        shlwapi<elf>
  \-PE  0x7ec80000-7ecc7000     \               shlwapi
ELF     0x7ecc7000-7ed93000     Deferred        shell32<elf>
  \-PE  0x7ece0000-7ed93000     \               shell32
ELF     0x7ed93000-7ee2b000     Deferred        comdlg32<elf>
  \-PE  0x7eda0000-7ee2b000     \               comdlg32
ELF     0x7ee2b000-7ee69000     Deferred        advapi32<elf>
  \-PE  0x7ee40000-7ee69000     \               advapi32
ELF     0x7ef4f000-7f852000     Deferred        gdi32<elf>
  \-PE  0x7ef90000-7f852000     \               gdi32
ELF     0x7f852000-7f974000     Deferred        user32<elf>
  \-PE  0x7f870000-7f974000     \               user32
ELF     0x7f974000-7f9d6000     Deferred        msvcrt<elf>
  \-PE  0x7f980000-7f9d6000     \               msvcrt
ELF     0x7f9d6000-7f9f0000     Deferred        crtdll<elf>
  \-PE  0x7f9e0000-7f9f0000     \               crtdll
ELF     0x7fb00000-7fb09000     Deferred        libxcursor.so.1
ELF     0x7fc51000-7fd50000     Deferred        kernel32<elf>
  \-PE  0x7fc70000-7fd50000     \               kernel32
ELF     0x7fd54000-7fd57000     Deferred        libxrandr.so.2
ELF     0x7fd57000-7fd5b000     Deferred        libxdmcp.so.6
ELF     0x7fd5b000-7fd60000     Deferred        libxxf86vm.so.1
ELF     0x7fd62000-7fd65000     Deferred        libxau.so.6
ELF     0x7fd65000-7fd70000     Deferred        libgcc_s.so.1
ELF     0x7fe81000-7fe8c000     Deferred        libnss_files.so.2
ELF     0x7fe8c000-7fe96000     Deferred        libnss_nis.so.2
ELF     0x7fe96000-7feac000     Deferred        libnsl.so.1
ELF     0x7feac000-7feb6000     Deferred        libnss_compat.so.2
ELF     0x7feb6000-7febb000     Deferred        libxxf86dga.so.1
ELF     0x7febb000-7fec2000     Deferred        libsm.so.6
ELF     0x7fec4000-7fec6000     Deferred        xlcutf8load.so.2
ELF     0x7fec6000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7dca000-b7dce000     Deferred        libdl.so.2
ELF     0xb7dce000-b7efc000     Deferred        libc.so.6
ELF     0xb7efc000-b7f0f000     Deferred        libpthread.so.0
ELF     0xb7f1b000-b7f35000     Deferred        libwine.so.1
ELF     0xb7f37000-b7f4d000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) C:\Program\Diablo\Game.exe
        0000001a   15
        00000017    0 <==
0000000f
        00000010    0
0000000a (D) C:\Program\Diablo\Game.exe
        0000000e    1
        0000000d    0
        0000000c    0
        0000000b    0

```

---

### Post by ignorance on 2006-04-03
k, i got it running but it's very laggy and the screenresolution and position aren't correct so anyone got a solution or who can tell me how to uninstall a videodriver?

I installed ATI-driver with the next ati-driver-installer-8.23.7-i386.run.

---

### Post by ignorance on 2006-04-03
it works.

---

### Post by flarkit on 2006-04-04
Can you give a little more info please? I'd like to try and get Diablo2 working under WinE too sometime.

;)

---

### Post by ignorance on 2006-04-04
Well when you feel ready to install it just leave me a msg and i'll answer.

---

### Post by Everlost on 2006-07-22
Sorry for bringing up an old thread but I was wondering how you got past the access_violation error. I have got the same broblem and have not been able to find a sollution.

---

### Post by ~LoKe on 2006-09-05
Bump.  I've got the same problem.

---

