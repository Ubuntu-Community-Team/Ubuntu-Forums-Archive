---
title: "program files problem..."
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-07-16
when i try to do...

```

cd /home/link/.wine/drive_c/Program Files/KeyChamp 2.0

```

to see if this program will run in wine, it says "Program Files" isn't a directory.  i remember doing something in the past to make it recognize the space, but i forget what it was.  would someone care to enlighten me?

---

### Post by jordanmthomas on 2007-07-16
either put it in quotes or put a \ (escape character)
```
cd [COLOR="Red"]"[/COLOR]/home/link/.wine/drive_c/Program Files/KeyChamp 2.0[COLOR="Red"]"[/COLOR]
```
or
```
cd /home/link/.wine/drive_c/Program[COLOR="Red"]\[/COLOR] Files/KeyChamp[COLOR="Red"]\[/COLOR] 2.0
```

when you put a space, bash sees it as "next item"
ie.
```
nano /etc/somefile
```
it knows nano and /etc/somefile are two different words.

---

### Post by locke.dragon on 2007-07-16
cool!  thanks.  worked like a charm.  well...  everything except the program.  :P

```

locke@aperturescience:~$ cd "/home/link/.wine/drive_c/Program Files/KeyChamp 2.0"
locke@aperturescience:~/.wine/drive_c/Program Files/KeyChamp 2.0$ wine keychamp.exe
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
wine: Unhandled page fault on write access to 0x00da1000 at address 0xb7db934c (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00da1000 in 32-bit code (0xb7db934c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7db934c ESP:0033f080 EBP:0033f0ec EFLAGS:00010206(   - 00      - RIP1)
 EAX:001a9610 EBX:7ea4e9d4 ECX:00012c00 EDX:00000000
 ESI:00c71048 EDI:00da1000
Stack dump:
0x0033f080:  7ea4b4a7 00cc0000 00b90048 0012c000
0x0033f090:  000001e0 00b90020 ffffffff ffffffff
0x0033f0a0:  00000000 0033f0e4 00000068 00163b80
0x0033f0b0:  0000ffff 00ffffff 7bc29ec1 0033f1d4
0x0033f0c0:  00000000 00000001 7b8b0888 0000030c
0x0033f0d0:  7ffdc0cc 7b88cb4b 00b90048 00000001
Backtrace:
=>1 0xb7db934c memcpy+0x1c() in libc.so.6 (0x0033f0ec)
  2 0x00423fd4 in keychamp (+0x23fd4) (0x0033f1fc)
  3 0x00424d2e in keychamp (+0x24d2e) (0x0033f4b0)
  4 0x004235c4 in keychamp (+0x235c4) (0x0033f4e0)
  5 0x004239f6 in keychamp (+0x239f6) (0x0033f588)
  6 0x00423c23 in keychamp (+0x23c23) (0x0033f5a4)
  7 0x00423c86 in keychamp (+0x23c86) (0x0033f5c4)
  8 0x004250ba in keychamp (+0x250ba) (0x0033f620)
  9 0x7ecdb15a WINPROC_wrapper+0x1a() in user32 (0x0033f650)
  10 0x7ecdb8ee in user32 (+0xab8ee) (0x0033f690)
  11 0x7ecdf84a CallWindowProcA+0x5a() in user32 (0x0033f6d0)
  12 0x7eca7d59 in user32 (+0x77d59) (0x0033f740)
  13 0x7ecab8a2 SendMessageTimeoutA+0x202() in user32 (0x0033f7b0)
  14 0x7ecab960 SendMessageA+0x50() in user32 (0x0033f7f0)
  15 0x7e439e97 X11DRV_CreateWindow+0xb77() in winex11 (0x0033f9b0)
  16 0x7ecd4d53 in user32 (+0xa4d53) (0x0033fc10)
  17 0x7ecd6602 CreateWindowExA+0x102() in user32 (0x0033fd90)
  18 0x00423da9 in keychamp (+0x23da9) (0x0033fdf8)
  19 0x00423f5b in keychamp (+0x23f5b) (0x0033fe04)
  20 0x00449de9 in keychamp (+0x49de9) (0x0033fe48)
  21 0x0046b8e7 in keychamp (+0x6b8e7) (0x0033ff08)
  22 0x7b874e7e in kernel32 (+0x54e7e) (0x0033ffe8)
  23 0xb7ebaaf7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xb7db934c memcpy+0x1c in libc.so.6: repe movsl (%esi),%es:(%edi)
Modules:
Module  Address                 Debug info      Name (91 modules)
PE        400000-  968000       Export          keychamp
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7b9b5000-7ba2a000       Deferred        wineps<elf>
  \-PE  7b9e0000-7ba2a000       \               wineps
ELF     7ba2a000-7ba7b000       Deferred        libgcrypt.so.11
ELF     7ba7b000-7ba90000       Deferred        libtasn1.so.3
ELF     7ba90000-7bb00000       Deferred        libgnutls.so.13
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bca1000-7bccf000       Deferred        libcrypt.so.1
ELF     7bccf000-7bd00000       Deferred        libcups.so.2
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf05000-7bf1b000       Deferred        iccvid<elf>
  \-PE  7bf10000-7bf1b000       \               iccvid
ELF     7bfce000-7c000000       Deferred        uxtheme<elf>
  \-PE  7bfe0000-7c000000       \               uxtheme
ELF     7c58f000-7c593000       Deferred        libgpg-error.so.0
ELF     7c593000-7c5a8000       Deferred        midimap<elf>
  \-PE  7c5a0000-7c5a8000       \               midimap
ELF     7c5a8000-7c5c0000       Deferred        msacm32<elf>
  \-PE  7c5b0000-7c5c0000       \               msacm32
ELF     7c5c0000-7c685000       Deferred        libasound.so.2
ELF     7c685000-7c6b7000       Deferred        winealsa<elf>
  \-PE  7c690000-7c6b7000       \               winealsa
ELF     7c6b9000-7c6be000       Deferred        libxfixes.so.3
ELF     7c6be000-7c6c7000       Deferred        libxcursor.so.1
ELF     7c6c7000-7c6e4000       Deferred        imm32<elf>
  \-PE  7c6d0000-7c6e4000       \               imm32
ELF     7c6e4000-7c6ea000       Deferred        libxrandr.so.2
ELF     7c6ea000-7c6f2000       Deferred        libxrender.so.1
ELF     7dff4000-7e24a000       Deferred        i915_dri.so
ELF     7e24a000-7e253000       Deferred        libdrm.so.2
ELF     7e253000-7e2b3000       Deferred        libgl.so.1
ELF     7e2b3000-7e2b8000       Deferred        libxdmcp.so.6
ELF     7e2b8000-7e2bb000       Deferred        libxau.so.6
ELF     7e2bb000-7e3ac000       Deferred        libx11.so.6
ELF     7e3ac000-7e3ba000       Deferred        libxext.so.6
ELF     7e3ba000-7e3bf000       Deferred        libxxf86vm.so.1
ELF     7e3bf000-7e3d7000       Deferred        libice.so.6
ELF     7e3d7000-7e3e0000       Deferred        libsm.so.6
ELF     7e3e0000-7e469000       Export          winex11<elf>
  \-PE  7e3f0000-7e469000       \               winex11
ELF     7e530000-7e550000       Deferred        libexpat.so.1
ELF     7e550000-7e57b000       Deferred        libfontconfig.so.1
ELF     7e57b000-7e58f000       Deferred        libz.so.1
ELF     7e58f000-7e5fa000       Deferred        libfreetype.so.6
ELF     7e5fa000-7e62d000       Deferred        winspool<elf>
  \-PE  7e600000-7e62d000       \               winspool
ELF     7e62d000-7e6ce000       Deferred        comdlg32<elf>
  \-PE  7e640000-7e6ce000       \               comdlg32
ELF     7e6ce000-7e727000       Deferred        shlwapi<elf>
  \-PE  7e6e0000-7e727000       \               shlwapi
ELF     7e727000-7e825000       Deferred        shell32<elf>
  \-PE  7e740000-7e825000       \               shell32
ELF     7e825000-7e845000       Deferred        mpr<elf>
  \-PE  7e830000-7e845000       \               mpr
ELF     7e845000-7e858000       Deferred        libresolv.so.2
ELF     7e858000-7e876000       Deferred        iphlpapi<elf>
  \-PE  7e860000-7e876000       \               iphlpapi
ELF     7e876000-7e8cf000       Deferred        rpcrt4<elf>
  \-PE  7e880000-7e8cf000       \               rpcrt4
ELF     7e8cf000-7e96e000       Deferred        ole32<elf>
  \-PE  7e8e0000-7e96e000       \               ole32
ELF     7e96e000-7ea2b000       Deferred        comctl32<elf>
  \-PE  7e980000-7ea2b000       \               comctl32
ELF     7ea2b000-7ea52000       Deferred        msvfw32<elf>
  \-PE  7ea30000-7ea52000       \               msvfw32
ELF     7ea52000-7ea5e000       Deferred        libgcc_s.so.1
ELF     7eb58000-7ec18000       Deferred        gdi32<elf>
  \-PE  7eb70000-7ec18000       \               gdi32
ELF     7ec18000-7ed55000       Export          user32<elf>
  \-PE  7ec30000-7ed55000       \               user32
ELF     7ed55000-7ede3000       Deferred        winmm<elf>
  \-PE  7ed60000-7ede3000       \               winmm
ELF     7ede3000-7ee09000       Deferred        msacm32<elf>
  \-PE  7edf0000-7ee09000       \               msacm32
ELF     7ee09000-7ee43000       Deferred        avifil32<elf>
  \-PE  7ee10000-7ee43000       \               avifil32
ELF     7ee43000-7ee8b000       Deferred        advapi32<elf>
  \-PE  7ee50000-7ee8b000       \               advapi32
ELF     7ef9d000-7efa8000       Deferred        libnss_files.so.2
ELF     7efa8000-7efb2000       Deferred        libnss_nis.so.2
ELF     7efb2000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7eff0000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d46000-b7d4a000       Deferred        libdl.so.2
ELF     b7d4a000-b7e8b000       Export          libc.so.6
ELF     b7e8c000-b7ea3000       Deferred        libpthread.so.0
ELF     b7eb3000-b7fc7000       Export          libwine.so.1
ELF     b7fc9000-b7fe4000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\KeyChamp 2.0\keychamp.exe
        00000009    0 <==
locke@aperturescience:~/.wine/drive_c/Program Files/KeyChamp 2.0$ 

```

anyone wanna help me fix it?  ;)  lol.  jk.  i'll just install it on my dreaded windoze partition.  (i HATE HATE HATE windoze.  it's so slow and cumbersome!!!  urg!)

---

