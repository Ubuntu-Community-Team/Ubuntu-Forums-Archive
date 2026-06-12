---
title: "realplayer/internet explorer and wine"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by pennyminstrel on 2006-08-07
I've been trying to get Realplayer to work in firefox so I can listen to Radio 4 without success so I decided to try a different tack and install the windows version to run through wine. But when I looked to see which exe to put into wine there were so many and I didn't have a clue which was the right one so I thought maybe it would be easier to install Internet Explorer and see if it would work that way

I've managed to install wine ok and and dowload IE into the fake c drive. 

I typed the following into a terminal:
wine /home/penny.wine/c/Program Files/Internet Explorer/IEXPLORE.EXE

and got
 wine: cannot find '/home/penny/.wine/drive_c/Program'

so I thought maybe I should do it without the spaces:
 wine /home/penny/.wine/drive_c/ProgramFiles/InternetExplorer/IEXPLORE.EXE

This time I got 
wine: cannot find cannot find 
'/home/penny/.wine/drive_c/ProgramFiles/InternetExplorer/IEXPLORE.EXE'

Can anybody tell me what I'm doing wrong?

Penny

---

### Post by darrenm on 2006-08-07
yup easy. put " around the path :)

---

### Post by darrenm on 2006-08-07
longer explanation. Linux being a proper operating system takes lots of fields on the command line as arguments therefore spaces in paths/filenames are not allowed.

You can however put double quotes " around the paths/filenames 
or
you can escape the spaces by putting a \ before them. That tells the command line to ignore the next character and use it as is; in this case a space.

Hope this makes sense :)

---

### Post by pennyminstrel on 2006-08-08
Armed with this info and having had another look at the RealPlayer directory and decided I'd found the right exe. I had another go at running Realplayer through wine. Everthign seemed to go fine, but the program didn't open up. Here's what showed in the terminal:

penny@penny-desktop:~$ winecfg
penny@penny-desktop:~$ wine /home/penny/.wine/'drive_c'/'Program Files'/Real/RealPlayer/realplay.exe
AddCheckpointList 004390A0 to manager 00438C58
AddCheckpointList 00425830 to manager 00438C58
AddCheckpointList 00412408 to manager 00438C58
AddCheckpointList 0044C4D0 to manager 00438C58
Got Request for zip://C:\Program Files\Real\RealPlayer\normal.vs?file=datacachelayout.xmb
Trying to open C:\Program Files\Real\RealPlayer\normal.vs
Trying to open datacachelayout.xmbSUCCESS
datacachelayout.xmb transmitted in whole
datacachelayout.xmb transmitted in whole
Got Request for zip://C:\Program Files\Real\RealPlayer\normal.vs?file=normal.xmbTrying to open C:\Program Files\Real\RealPlayer\normal.vs
Trying to open normal.xmbSUCCESS
normal.xmb transmitted in whole
normal.xmb transmitted in whole
Got Request for images.xmb
Trying to open images.xmbSUCCESS
images.xmb transmitted in whole
images.xmb transmitted in whole
Got Request for images.xmb
Trying to open images.xmbSUCCESS
images.xmb transmitted in whole
images.xmb transmitted in whole
Got Request for images.xmb
Trying to open images.xmbSUCCESS
images.xmb transmitted in whole
images.xmb transmitted in whole
Got Request for images.xmb
Trying to open images.xmbSUCCESS
images.xmb transmitted in whole
images.xmb transmitted in whole
Got Request for images.xmb
Trying to open images.xmbSUCCESS
images.xmb transmitted in whole
images.xmb transmitted in whole
Got Request for sharedlayouts.xmb
Trying to open sharedlayouts.xmbSUCCESS
sharedlayouts.xmb transmitted in whole
sharedlayouts.xmb transmitted in whole
Got Request for sharedlayouts.xmb
Trying to open sharedlayouts.xmbSUCCESS
sharedlayouts.xmb transmitted in whole
sharedlayouts.xmb transmitted in whole
Got Request for admodules.xmb
Trying to open admodules.xmbSUCCESS
admodules.xmb transmitted in whole
admodules.xmb transmitted in whole
fixme:system:SystemParametersInfoW Unimplemented action: 8192 (SPI_GETFOREGROUNDLOCKTIMEOUT)
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\ole32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\iphlpapi.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\lz32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\winex11.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\imm32.dll
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file dll\comctl32.dbg ("")
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\oleaut32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\uxtheme.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\wineoss.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\msacm32.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\msacm32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\midimap.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\psapi.dll
wine: Unhandled page fault on read access to 0x7f185a4f at address 0x6227860b (thread 0014), starting debugger...
WineDbg starting on pid 0x13
Unhandled exception: page fault on read access to 0x7f185a4f in 32-bit code (0x6227860b).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:6227860b ESP:0033efd0 EBP:0033f000 EFLAGS:00210a87(   - 00     ROISP1C)
 EAX:00405a4d EBX:0033f03c ECX:7ed80000 EDX:00000000
 ESI:7ed80000 EDI:7f185a4f
Stack dump:
0x0033efd0:  80004005 007039a0 00494d28 7ffdcc00
0x0033efe0:  7ffdcbf8 0033f054 00703000 003c003a
0x0033eff0:  7ffdcc00 7eed426c 007039a0 7ed80000
0x0033f000:  0033f028 6227872d 7ed80000 7edf3f3c
0x0033f010:  00000001 0033f020 0033f038 0033f03c
0x0033f020:  622c6d38 62233c40 0033f05c 62233981
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x6227860b in rpap3260 (+0x5860b) (0x6227860b)
  2 0x6227872d in rpap3260 (+0x5872d) (0x6227872d)
  3 0x62233981 in rpap3260 (+0x13981) (0x62233981)
  4 0x6222211f in rpap3260 (+0x211f) (0x6222211f)
  5 0x00401ea3 in realplay (+0x1ea3) (0x00401ea3)
  6 0x0040cf06 in realplay (+0xcf06) (0x0040cf06)
  7 0x7efbcd5c LdrInitializeThunk+0x548 in ntdll (0x7efbcd5c)
  8 0x7ee99105 in kernel32 (+0x49105) (0x7ee99105)
  9 0xb7e4d283 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7e4d283)
0x6227860b: movb        0x2(%eax,%esi,1),%al
Modules:
Module  Address                 Debug info      Name (84 modules)
PE      400000-481000   Export          realplay
PE      60080000-60087000       Deferred        pnrs3260
PE      603e0000-6040a000       Deferred        objb3201
PE      60a20000-60a68000       Deferred        pncrt
PE      60b00000-60b0a000       Deferred        pxcb3210
PE      61040000-610a9000       Deferred        uisy3201
PE      61400000-6140d000       Deferred        rpms3260
PE      61460000-614da000       Deferred        rpmn3260
PE      615f0000-616a4000       Deferred        rpcontrols1
PE      62090000-6210c000       Deferred        rpcl3260
PE      62220000-62302000       Export          rpap3260
PE      62fd0000-62ffb000       Deferred        zipf3260
PE      63380000-63401000       Deferred        imgrender
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e2c6000-7e2db000       Deferred        midimap<elf>
  \-PE  7e2d0000-7e2db000       \               midimap
ELF     7e301000-7e319000       Deferred        msacm32<elf>
  \-PE  7e310000-7e319000       \               msacm32
ELF     7e319000-7e355000       Deferred        wineoss<elf>
  \-PE  7e320000-7e355000       \               wineoss
ELF     7e387000-7e3b8000       Deferred        uxtheme<elf>
  \-PE  7e390000-7e3b8000       \               uxtheme
ELF     7e3b8000-7e440000       Deferred        winmm<elf>
  \-PE  7e3c0000-7e440000       \               winmm
ELF     7e440000-7e4d1000       Deferred        oleaut32<elf>
  \-PE  7e450000-7e4d1000       \               oleaut32
ELF     7e4d1000-7e593000       Deferred        comctl32<elf>
  \-PE  7e4e0000-7e593000       \               comctl32
ELF     7e593000-7e5e9000       Deferred        shlwapi<elf>
  \-PE  7e5a0000-7e5e9000       \               shlwapi
ELF     7e5e9000-7e6c7000       Deferred        shell32<elf>
  \-PE  7e600000-7e6c7000       \               shell32
ELF     7e6c9000-7e6cd000       Deferred        libxfixes.so.3
ELF     7e6cd000-7e6d6000       Deferred        libxcursor.so.1
ELF     7e6d6000-7e6f2000       Deferred        imm32<elf>
  \-PE  7e6e0000-7e6f2000       \               imm32
ELF     7e6f2000-7e6fa000       Deferred        libxrender.so.1
ELF     7e6fa000-7e701000       Deferred        libdrm.so.2
ELF     7e701000-7e767000       Deferred        libgl.so.1
ELF     7e767000-7e84d000       Deferred        libx11.so.6
ELF     7e84d000-7e85a000       Deferred        libxext.so.6
ELF     7e85a000-7e85f000       Deferred        libxxf86vm.so.1
ELF     7e85f000-7e864000       Deferred        libxxf86dga.so.1
ELF     7e864000-7e87c000       Deferred        libice.so.6
ELF     7e87c000-7e8ff000       Deferred        winex11<elf>
  \-PE  7e890000-7e8ff000       \               winex11
ELF     7e8ff000-7e91e000       Deferred        libexpat.so.1
ELF     7e91e000-7e94c000       Deferred        libfontconfig.so.1
ELF     7e94c000-7e960000       Deferred        libz.so.1
ELF     7e960000-7e9c9000       Deferred        libfreetype.so.6
ELF     7e9c9000-7e9dd000       Deferred        lz32<elf>
  \-PE  7e9d0000-7e9dd000       \               lz32
ELF     7e9dd000-7e9f6000       Deferred        version<elf>
  \-PE  7e9e0000-7e9f6000       \               version
ELF     7e9f6000-7ea15000       Deferred        iphlpapi<elf>
  \-PE  7ea00000-7ea15000       \               iphlpapi
ELF     7ea15000-7ea64000       Deferred        rpcrt4<elf>
  \-PE  7ea20000-7ea64000       \               rpcrt4
ELF     7ea64000-7ea6e000       Deferred        libgcc_s.so.1
ELF     7eb43000-7ebf5000       Deferred        gdi32<elf>
  \-PE  7eb60000-7ebf5000       \               gdi32
ELF     7ebf5000-7ed27000       Deferred        user32<elf>
  \-PE  7ec10000-7ed27000       \               user32
ELF     7ed27000-7ed6a000       Deferred        advapi32<elf>
  \-PE  7ed30000-7ed6a000       \               advapi32
ELF     7ed6a000-7edfb000       Deferred        ole32<elf>
  \-PE  7ed80000-7edfb000       \               ole32
ELF     7ee2e000-7ef2f000       Export          kernel32<elf>
  \-PE  7ee50000-7ef2f000       \               kernel32
ELF     7ef2f000-7ef39000       Deferred        libnss_files.so.2
ELF     7ef39000-7ef42000       Deferred        libnss_nis.so.2
ELF     7ef42000-7ef57000       Deferred        libnsl.so.1
ELF     7ef57000-7ef60000       Deferred        libnss_compat.so.2
ELF     7ef60000-7ef82000       Deferred        libm.so.6
ELF     7ef82000-7f000000       Export          ntdll<elf>
  \-PE  7ef90000-7f000000       \               ntdll
ELF     b7cf1000-b7cf4000       Deferred        libxrandr.so.2
ELF     b7cf6000-b7cf9000       Deferred        libdl.so.2
ELF     b7cf9000-b7e28000       Deferred        libc.so.6
ELF     b7e28000-b7e3a000       Deferred        libpthread.so.0
ELF     b7e3b000-b7e3e000       Deferred        libxau.so.6
ELF     b7e3e000-b7e46000       Deferred        libsm.so.6
ELF     b7e46000-b7f56000       Export          libwine.so.1
ELF     b7f59000-b7f6f000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000013 (D) C:\Program Files\Real\RealPlayer\realplay.exe
        00000015    0
        00000014    0 <==
0000000e
        00000010    0
        0000000f    0
0000000a
        0000000b    0
penny@penny-desktop:~$


Am I still missing something?

Penny

ps had another go at running internet explorer which seemed like it ws going to play ball but failed at the end but I won't complicate matters with the details of that as well.

---

### Post by Jagot on 2006-08-08
This is by far and away the best method of installing IE in Linux:

[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

---

### Post by mssever on 2006-08-08
RealPlayer might not work with wine (most programs don't, unfortunately). However, there is a Linux version of RealPlayer that you can get from [Automatix]("http://www.ubuntuforums.org/showthread.php?t=190025"). I use it a lot and it's decent.

When it comes to running Internet Explorer under wine, I've had great success with [IEs4Linux]("http://www.tatanka.com.br/ies4linux/index-en.html"). Although, you probably shouldn't make a habit of using IE to browse...

---

### Post by mssever on 2006-08-08
Just remembered something else. I've learned that with wine it often helps to cd to the program's directory before starting it.

---

### Post by Jagot on 2006-08-08
The Linux version of Real Player is in fact in Canonical's commercial repository as well so you don't even have to use Automatix.  Here's a guide to enabling it:

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-b75a0c6c7e357640731529980d3f3ad3614b9a76](https://help.ubuntu.com/community/Repositories/Ubuntu#head-b75a0c6c7e357640731529980d3f3ad3614b9a76)

---

