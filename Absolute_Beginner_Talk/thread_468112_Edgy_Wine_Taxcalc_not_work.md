---
title: "Edgy Wine Taxcalc not work"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by rpaco on 2007-06-08
I have installed WIne (3 times now) and tried to use Winetools but after installation they just disappeared with no executable files showing anywhere, and unable to find any instructions for Winetools I gave up on it.  SO I found another app called WIneDoors, this worked ok and set up Wine for me. And I have a few Windows apps showing in the "Applications>Wine-wine>wine-Programs>" menu. 

I have also installed **Taxcalc**, **this was the only reason to use wine** (there  is no Linux version of Taxcalc) I did this by buying and downloading the TaxCalc.exe file from the relevant site and running the executable in File Browser using wine .  This went exactly like a windows installation (I had to get libjack.something first and install that too which was no prob with apt-get).

Now I have taxcalc in the "wine-Programs" sub menu BUT it won't work, nothing happens when I click on it.
I have also gone direct via the file browser to Taxcalc.exe file and double clicked it, again nothing seems to happen.

Have also tried to run  in a terminal but always get Cannot find c:/Program or whichever path I type whether in Linux or windows style.
I have a traditional windows setup in my home directory with taxcalc @ /home/rpa/.wine/drive_c/Program Files/TaxCalc 2007/TaxCalc.exe

I get this>>
rpa@rpaco-pc:~$ wine c:/Program Files/TaxCalc 2007/TaxCalc.exe
wine: cannot find 'c:/Program'
rpa@rpaco-pc:~$ wine /home/rpa/.wine/drive_c/Program Files/TaxCalc 2007/TaxCalc.exe
wine: cannot find '/home/rpa/.wine/drive_c/Program'
rpa@rpaco-pc:~$ wine /.wine/drive_c/Program Files/TaxCalc 2007/TaxCalc.exe
wine: cannot find '/.wine/drive_c/Program'

I am sure I am doing something stupid, but can someone please tell me what it is.

I need this (taxcalc) to do (prepare) my income tax submission, otherwise I have to do it live online which is best not done if it can be avoided.

Any ideas please.

---

### Post by machoo02 on 2007-06-09
The terminal does not like the spaces that you have in the path to the executable.  Try ```
wine "~/.wine/drive_c/Program Files/TaxCalc 2007/TaxCalc.exe"
``` or ```
wine ~/.wine/drive_c/Program\ Files/TaxCalc\ 2007/TaxCalc.exe
```

The backslash ('\') character tells the terminal shell to ignore the next character in the search string.  Also, check out the [Wine Application Database]("http://appdb.winehq.org") for any tips/tricks for running your program

---

### Post by rpaco on 2007-06-11
Ok thanks tried that and got this:

Well it wont let me post it hers because it says I have used 9 images although I have actually use none at all. So how do i get round that one?

---

### Post by rpaco on 2007-06-12
Well I have now tried winecfg as well as the original setup via wine-doors and I get this error:

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture. 
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

I guess something is missing, please give me a hefty shove ( a clue or a hint is too subtle for me)

Sorry I can't find how to turn smilies on or off so it's still there.

---

### Post by rpaco on 2007-06-14
Well I have got a little further now and can get different error messages as follows, sorry it's rather long:
```
rpa@rpaco-pc:~$ wine ~/.wine/drive_c/Program\ Files/TaxCalc\ 2007/TaxCalc.exe
fixme:shdocvw:PersistStreamInit_InitNew (0x173d30)
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x173d30)
fixme:shdocvw:OleObject_Close (0x173d30)->(1)
wine: Unhandled illegal instruction at address 0x134863d (thread 0009), starting debugger...
Unhandled exception: illegal instruction in 32-bit code (0x0134863d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0134863d ESP:0033eb50 EBP:0033eb6c EFLAGS:00210282(   - 00      - RIS1)
 EAX:ffff8e91 EBX:7d2adfc8 ECX:00110020 EDX:01349264
 ESI:00173d30 EDI:00173d30
Stack dump:
0x0033eb50:  7d29c1d7 01349264 01120000 00000000
0x0033eb60:  7d00317e 7d2adfc8 00000000 0033eb9c
0x0033eb70:  7d2a3f64 00173d30 01348cec 01348cf0
0x0033eb80:  0033eb64 00445f12 0033ebac 7d005e3c
0x0033eb90:  7c1d74a6 01348bf8 01348cec 0033ebbc
0x0033eba0:  7c1742bc 00173d30 01348bf8 01348bf8
Backtrace:
=>1 0x0134863d (0x0033eb6c)
  2 0x7d2a3f64 in shdocvw (+0x13f64) (0x0033eb9c)
  3 0x7c1742bc in mfc71 (+0x342bc) (0x0033ebbc)
  4 0x0043905c in taxcalc (+0x3905c) (0x0033ec64)
  5 0x7c1adb30 in mfc71 (+0x6db30) (0x0033ecf0)
  6 0x7c1a9f01 in mfc71 (+0x69f01) (0x0033ed10)
  7 0x7c1ac5a9 in mfc71 (+0x6c5a9) (0x0033ed70)
  8 0x7c1ac639 in mfc71 (+0x6c639) (0x0033ed90)
  9 0x7c1d74df in mfc71 (+0x974df) (0x0033edbc)
  10 0x7ed86dfa WINPROC_wrapper+0x1a() in user32 (0x0033edec)
  11 0x7ed8758e in user32 (+0xa758e) (0x0033ee2c)
  12 0x7ed8bc5b in user32 (+0xabc5b) (0x0033f2fc)
  13 0x7ed8c7fa CallWindowProcW+0xaa() in user32 (0x0033f33c)
  14 0x7ed53ac8 in user32 (+0x73ac8) (0x0033f3ac)
  15 0x7ed57820 SendMessageTimeoutW+0x1a0() in user32 (0x0033f41c)
  16 0x7ed57890 SendMessageW+0x50() in user32 (0x0033f45c)
  17 0x7ed7dc09 WIN_DestroyWindow+0x119() in user32 (0x0033f4fc)
  18 0x7ed7db4c WIN_DestroyWindow+0x5c() in user32 (0x0033f59c)
  19 0x7ed802b4 DestroyWindow+0x2c4() in user32 (0x0033f5dc)
  20 0x7c1abefe in mfc71 (+0x6befe) (0x0033f618)
  21 0x004209a0 in taxcalc (+0x209a0) (0x01348178)
  22 0x00000001 (0x00957758)
  23 0x004176a0 in taxcalc (+0x176a0) (0x004175c0)
  24 0xccccc300 (0x957720b8)
  25 0x00000000 (0x00000000)
0x0134863d: mov 0x0(%ecx,%eax,1),
Modules:
Module  Address                 Debug info      Name (84 modules)
PE        340000-  39e000       Deferred        libxslt
PE        400000-  b1c000       Export          taxcalc
PE        b20000-  ef3000       Deferred        pdfgen
PE      10000000-100eb000       Deferred        libxml2
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c140000-7c246000       Export          mfc71
PE      7c3c0000-7c43c000       Deferred        msvcp71
PE      7d000000-7d058000       Deferred        msvcr71
ELF     7d27e000-7d2b8000       Export          shdocvw<elf>
  \-PE  7d290000-7d2b8000       \               shdocvw
ELF     7d2dc000-7d30e000       Deferred        uxtheme<elf>
  \-PE  7d2e0000-7d30e000       \               uxtheme
ELF     7d531000-7d54e000       Deferred        imm32<elf>
  \-PE  7d540000-7d54e000       \               imm32
ELF     7d54e000-7d56c000       Deferred        ximcp.so.2
ELF     7d56c000-7d574000       Deferred        libxrender.so.1
ELF     7d574000-7dd37000       Deferred        libglcore.so.1
ELF     7de41000-7de46000       Deferred        libxfixes.so.3
ELF     7de46000-7de4f000       Deferred        libxcursor.so.1
ELF     7de4f000-7de51000       Deferred        xlcutf8load.so.2
ELF     7de51000-7de54000       Deferred        libxrandr.so.2
ELF     7e395000-7e41a000       Deferred        libgl.so.1
ELF     7e41a000-7e41f000       Deferred        libxdmcp.so.6
ELF     7e41f000-7e4e8000       Deferred        libx11.so.6
ELF     7e4e8000-7e4f5000       Deferred        libxext.so.6
ELF     7e4f5000-7e4fa000       Deferred        libxxf86vm.so.1
ELF     7e4fa000-7e512000       Deferred        libice.so.6
ELF     7e512000-7e5a1000       Deferred        winex11<elf>
  \-PE  7e520000-7e5a1000       \               winex11
ELF     7e5a1000-7e5bf000       Deferred        libexpat.so.1
ELF     7e5bf000-7e5ee000       Deferred        libfontconfig.so.1
ELF     7e5ee000-7e602000       Deferred        libz.so.1
ELF     7e602000-7e66c000       Deferred        libfreetype.so.6
ELF     7e66c000-7e706000       Deferred        oleaut32<elf>
  \-PE  7e680000-7e706000       \               oleaut32
ELF     7e706000-7e75b000       Deferred        rpcrt4<elf>
  \-PE  7e710000-7e75b000       \               rpcrt4
ELF     7e75b000-7e7f9000       Deferred        ole32<elf>
  \-PE  7e770000-7e7f9000       \               ole32
ELF     7e7f9000-7e80c000       Deferred        libresolv.so.2
ELF     7e80c000-7e82a000       Deferred        iphlpapi<elf>
  \-PE  7e810000-7e82a000       \               iphlpapi
ELF     7e82a000-7e856000       Deferred        ws2_32<elf>
  \-PE  7e830000-7e856000       \               ws2_32
ELF     7e856000-7e8bb000       Deferred        msvcrt<elf>
  \-PE  7e870000-7e8bb000       \               msvcrt
ELF     7e8bb000-7e978000       Deferred        comctl32<elf>
  \-PE  7e8c0000-7e978000       \               comctl32
ELF     7e978000-7ea74000       Deferred        shell32<elf>
  \-PE  7e990000-7ea74000       \               shell32
ELF     7ea74000-7eacd000       Deferred        shlwapi<elf>
  \-PE  7ea80000-7eacd000       \               shlwapi
ELF     7eacd000-7eb14000       Deferred        advapi32<elf>
  \-PE  7eae0000-7eb14000       \               advapi32
ELF     7eb14000-7eb1f000       Deferred        libgcc_s.so.1
ELF     7eb21000-7eb23000       Deferred        libnvidia-tls.so.1
ELF     7eb23000-7eb2c000       Deferred        libsm.so.6
ELF     7ec0b000-7ecc6000       Deferred        gdi32<elf>
  \-PE  7ec20000-7ecc6000       \               gdi32
ELF     7ecc6000-7ee01000       Export          user32<elf>
  \-PE  7ece0000-7ee01000       \               user32
ELF     7ee01000-7ee21000       Deferred        mpr<elf>
  \-PE  7ee10000-7ee21000       \               mpr
ELF     7ee21000-7ee6a000       Deferred        wininet<elf>
  \-PE  7ee30000-7ee6a000       \               wininet
ELF     7ee6a000-7ee7e000       Deferred        lz32<elf>
  \-PE  7ee70000-7ee7e000       \               lz32
ELF     7ee7e000-7ee98000       Deferred        version<elf>
  \-PE  7ee80000-7ee98000       \               version
ELF     7efa2000-7efad000       Deferred        libnss_files.so.2
ELF     7efad000-7efb7000       Deferred        libnss_nis.so.2
ELF     7efb7000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff3000       Deferred        libm.so.6
ELF     7eff3000-7eff6000       Deferred        libxau.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ce4000-b7ce8000       Deferred        libdl.so.2
ELF     b7ce8000-b7e1c000       Deferred        libc.so.6
ELF     b7e1c000-b7e2f000       Deferred        libpthread.so.0
ELF     b7e3c000-b7f50000       Deferred        libwine.so.1
ELF     b7f52000-b7f6d000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\TaxCalc 2007\TaxCalc.exe
        00000009    0 <==
rpa@rpaco-pc:~$ 

```

---

