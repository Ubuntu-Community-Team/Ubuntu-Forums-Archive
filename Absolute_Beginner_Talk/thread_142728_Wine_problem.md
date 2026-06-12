---
title: "Wine problem"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-03-11
I'm trying to run Picasa under Wine
I have followed the instructions [here]("http://www.psychocats.net/linux/wine") but could not create a launcher that works
I ran it in terminal and this is what I got
```
kitty@localhost:~$ wine /home/kitty/picasa2/picasa2.exe
fixme:ole:CoResumeClassObjects stub
fixme:urlmon:CoInternetGetSession (0, 0x7fa7d4a4, 0): stub
fixme:urlmon:URLMON_DllGetClassObject {79eac9e2-baf9-11ce-8c82-00aa004ba90b}: no class found.
wine: Unhandled exception (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00608fe9).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:00608fe9 ESP:7fa7d494 EBP:7fa7fe94 EFLAGS:00210212(   - 00      - RIA1)
 EAX:00000000 EBX:797c25f4 ECX:797c3550 EDX:00000000
 ESI:007f547c EDI:797c25f0
Stack dump:
0x7fa7d494:  00000000 007f547c 00000000 797c3550
0x7fa7d4a4:  00000000 005dbbe6 7beff980 00000000

0x7fa7d4b4:  00000000 7fda001c 0051566e 7beff980
0x7fa7d4c4:  00000000 7fd48ff4 00000000 00000000
0x7fa7d4d4:  b7fca860 00000000 b7e403f4 7c06b170
0x7fa7d4e4:  00000000 00000000 00000000 00000000
0200: sel=1007 base=b7fb0000 limit=00001f97 32-bit rw-
Backtrace:
=>1 0x00608fe9 in picasa2 (+0x208fe9) (0x7fa7fe94)
  2 0x00620652 EntryPoint+0xe0 in picasa2 (0x7fa7ff20)
  3 0x7fd08e63 in kernel32 (+0x48e63) (0x7fa7fff4)
  4 0xb7f8fc45 wine_switch_to_stack+0x11 in libwine.so.1 (0x00000000)
0x00608fe9: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (107 modules)
PE      0x00400000-0083e000     Export          picasa2
PE      0x10000000-10a43000     Deferred        picasai18n
PE      0x79480000-7957a000     Deferred        expwebsites.yti
ELF     0x798b1000-798b9000     Deferred        libxrender.so.1
ELF     0x7be87000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
PE      0x7bfc0000-7bff7000     Deferred        ytitivo.yti
PE      0x7c580000-7c5a9000     Deferred        cdvdr.yti
ELF     0x7c794000-7c7f6000     Deferred        libgnutls.so.11
ELF     0x7c7f6000-7c813000     Deferred        libcups.so.2
ELF     0x7c824000-7c870000     Deferred        libgcrypt.so.11
ELF     0x7c870000-7c880000     Deferred        libtasn1.so.2
ELF     0x7c9d3000-7c9e8000     Deferred        midimap<elf>
  \-PE  0x7c9e0000-7c9e8000     \               midimap
ELF     0x7c9e8000-7ca01000     Deferred        msacm.drv<elf>
  \-PE  0x7c9f0000-7ca01000     \               msacm.drv
ELF     0x7ca01000-7ca44000     Deferred        wineoss.drv<elf>
  \-PE  0x7ca10000-7ca44000     \               wineoss.drv
ELF     0x7ca62000-7ca6b000     Deferred        libxcursor.so.1
ELF     0x7ca79000-7ca95000     Deferred        ximcp.so.2
ELF     0x7e297000-7e49a000     Deferred        i915_dri.so
ELF     0x7e49a000-7e4a1000     Deferred        libdrm.so.1
ELF     0x7e4a1000-7e507000     Deferred        libgl.so.1
ELF     0x7e507000-7e589000     Deferred        winex11.drv<elf>
  \-PE  0x7e520000-7e589000     \               winex11.drv
ELF     0x7e589000-7e5a8000     Deferred        libexpat.so.1
ELF     0x7e5a8000-7e5d6000     Deferred        libfontconfig.so.1
ELF     0x7e5d6000-7e5ea000     Deferred        libz.so.1
ELF     0x7e5ea000-7e654000     Deferred        libfreetype.so.6
ELF     0x7e654000-7e66d000     Deferred        wintrust<elf>
  \-PE  0x7e660000-7e66d000     \               wintrust
ELF     0x7e66d000-7e72d000     Deferred        libx11.so.6
ELF     0x7e72d000-7e73a000     Deferred        libxext.so.6
ELF     0x7e73a000-7e753000     Deferred        libice.so.6
ELF     0x7e753000-7e75a000     Deferred        libsm.so.6
ELF     0x7e75a000-7e7d2000     Deferred        ddraw<elf>
  \-PE  0x7e780000-7e7d2000     \               ddraw
ELF     0x7e7d2000-7e7ef000     Deferred        imm32<elf>
  \-PE  0x7e7e0000-7e7ef000     \               imm32
ELF     0x7e7ef000-7e884000     Deferred        oleaut32<elf>
  \-PE  0x7e810000-7e884000     \               oleaut32
ELF     0x7e884000-7e8af000     Deferred        winspool.drv<elf>
  \-PE  0x7e890000-7e8af000     \               winspool.drv
ELF     0x7e8af000-7e93f000     Deferred        comdlg32<elf>
  \-PE  0x7e8c0000-7e93f000     \               comdlg32
ELF     0x7e93f000-7e968000     Deferred        cabinet<elf>
  \-PE  0x7e950000-7e968000     \               cabinet
ELF     0x7e968000-7e990000     Deferred        urlmon<elf>
  \-PE  0x7e980000-7e990000     \               urlmon
ELF     0x7e990000-7ea56000     Deferred        shell32<elf>
  \-PE  0x7e9b0000-7ea56000     \               shell32
ELF     0x7ea56000-7eab2000     Deferred        shlwapi<elf>
  \-PE  0x7ea70000-7eab2000     \               shlwapi
ELF     0x7eab2000-7ead1000     Deferred        mpr<elf>
  \-PE  0x7eac0000-7ead1000     \               mpr
ELF     0x7ead1000-7eb15000     Deferred        wininet<elf>
  \-PE  0x7eae0000-7eb15000     \               wininet
ELF     0x7eb15000-7eb40000     Deferred        ws2_32<elf>
  \-PE  0x7eb20000-7eb40000     \               ws2_32
ELF     0x7eb40000-7eb61000     Deferred        iphlpapi<elf>
  \-PE  0x7eb50000-7eb61000     \               iphlpapi
ELF     0x7eb61000-7ebab000     Deferred        rpcrt4<elf>
  \-PE  0x7eb80000-7ebab000     \               rpcrt4
ELF     0x7ebab000-7ec35000     Deferred        ole32<elf>
  \-PE  0x7ebc0000-7ec35000     \               ole32
ELF     0x7ec35000-7ecf4000     Deferred        comctl32<elf>
  \-PE  0x7ec40000-7ecf4000     \               comctl32
ELF     0x7ecf4000-7ed19000     Deferred        msvfw32<elf>
  \-PE  0x7ed00000-7ed19000     \               msvfw32
ELF     0x7ed19000-7ed5a000     Deferred        advapi32<elf>
  \-PE  0x7ed30000-7ed5a000     \               advapi32
ELF     0x7ee40000-7f743000     Deferred        gdi32<elf>
  \-PE  0x7ee90000-7f743000     \               gdi32
ELF     0x7f743000-7f86f000     Deferred        user32<elf>
  \-PE  0x7f760000-7f86f000     \               user32
ELF     0x7f86f000-7f8ef000     Deferred        winmm<elf>
  \-PE  0x7f880000-7f8ef000     \               winmm
ELF     0x7f8ef000-7f912000     Deferred        msacm32<elf>
  \-PE  0x7f900000-7f912000     \               msacm32
ELF     0x7f912000-7f951000     Deferred        avifil32<elf>
  \-PE  0x7f920000-7f951000     \               avifil32
ELF     0x7f951000-7f965000     Deferred        lz32<elf>
  \-PE  0x7f960000-7f965000     \               lz32
ELF     0x7f965000-7f980000     Deferred        version<elf>
  \-PE  0x7f970000-7f980000     \               version
ELF     0x7fa80000-7fa85000     Deferred        libxxf86vm.so.1
ELF     0x7fa85000-7fa90000     Deferred        libgcc_s.so.1
ELF     0x7fc95000-7fda0000     Export          kernel32<elf>
  \-PE  0x7fcc0000-7fda0000     \               kernel32
ELF     0x7feb3000-7febd000     Deferred        libnss_files.so.2
ELF     0x7febd000-7fed2000     Deferred        libnsl.so.1
ELF     0x7fed2000-7fedb000     Deferred        libnss_compat.so.2
ELF     0x7fede000-7fee2000     Deferred        libgpg-error.so.0
ELF     0x7fee2000-7fee6000     Deferred        libxfixes.so.3
ELF     0x7fee6000-7fee9000     Deferred        libxrandr.so.2
ELF     0x7fee9000-7ff0b000     Deferred        libm.so.6
ELF     0x7ff0b000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7e40000-b7e42000     Deferred        xlcutf8load.so.2
ELF     0xb7e42000-b7e46000     Deferred        libxdmcp.so.6
ELF     0xb7e47000-b7e4a000     Deferred        libdl.so.2
ELF     0xb7e4a000-b7f78000     Deferred        libc.so.6
ELF     0xb7f79000-b7f8b000     Deferred        libpthread.so.0
ELF     0xb7f8b000-b7fa4000     Export          libwine.so.1
ELF     0xb7fa4000-b7fa7000     Deferred        libxau.so.6
ELF     0xb7fa7000-b7fb0000     Deferred        libnss_nis.so.2
ELF     0xb7fb5000-b7fcb000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\kitty\picasa2\picasa2.exe
        00000009    0 <==
WineDbg terminated on pid 0x8

```

What's wrong?

---

### Post by bluevoodoo1 on 2006-03-11
Hmm... I don't have picasa, but I'll throw some ideas out. So you have installed it correctly then? Hmm... is there a picasa folder in your .wine/c_drive/Program\ Files folder? It should have created one (or something similar). For me, I use one program with wine and to launch it the command is...

wine .wine/drive_c/Program\ Files/Finale\ 2003/FINALE.EXE

so I guess my question is... Is there a picasa folder in your Program Files folder than contains some kind of picasa.exe file?

(so something like this, but not exactly)
wine .wine/drive_c/Program\ Files/picasa/picasa.exe

also, the version of wine in the repos is not the most up-to-date. If you're thinking that wine is the culprit, you could try [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) that page for more info.

---

### Post by noswal on 2006-03-11
I installed wine yesterday, had problems but found this easier than typing a whole command line, was to to just type   winefile  in termimal, it  launches a java based windows explorer, then just going to the correct drive/folder and the actual .exe it launches, as it would in windose. Although not all my windows programs work yet, still early days I guess

---

### Post by bluevoodoo1 on 2006-03-11
[QUOTE=noswal]I installed wine yesterday, had problems but found this easier than typing a whole command line, was to to just type   winefile  in termimal, it  launches a java based windows explorer, then just going to the correct drive/folder and the actual .exe it launches, as it would in windose. Although not all my windows programs work yet, still early days I guess[/QUOTE]


Hmmm interesting. I like the command line because you can see any potential errors. You can also right click on an .exe file and open it with wine (from the list or choose custom and type in wine). I'll have to check out winefile.

EDIT: Wow! winefile is great! Never knew about that!

---

### Post by seshomaru samma on 2006-03-12
[QUOTE=bluevoodoo1]Hmm... I don't have picasa, but I'll throw some ideas out. So you have installed it correctly then? Hmm... is there a picasa folder in your .wine/c_drive/Program\ Files folder? It should have created one (or something similar). For me, I use one program with wine and to launch it the command is...

wine .wine/drive_c/Program\ Files/Finale\ 2003/FINALE.EXE

so I guess my question is... Is there a picasa folder in your Program Files folder than contains some kind of picasa.exe file?

(so something like this, but not exactly)
wine .wine/drive_c/Program\ Files/picasa/picasa.exe

also, the version of wine in the repos is not the most up-to-date. If you're thinking that wine is the culprit, you could try [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) that page for more info.[/QUOTE]

I have used the excellent winefile tip and I don't have a Picasa file in 'programs'-see attachment.

(btw- how do I cd there with the terminal? )
In that case I would like to reinstall wine, but do I need to uninstall it first? and if yes, how?

---

### Post by seshomaru samma on 2006-03-12
I just updated Wine and reinstalled Picasa
I now have Picasa in Wine's Program Files
Yet it still wont run ,and if I run it from the terminal I still get the same error as before...

---

### Post by bluevoodoo1 on 2006-03-12
I just downloaded it and it worked perfectly. 

Here is what I did. I dowloaded the file picasa2-current.exe to my home folder. Then I right clicked on it and selected "open with wine." This opened the program setup. Then it installed. I navigated over to .wine/drive_c/Program\ Files/Picasa2 and right-clicked on Picasa2.exe and selected "open with wine" (if that's not there, select 'open with other application' and click on "use a custom command" and type in "wine" 

If you want to open it with wine in the terminal the path should be...
```

wine .wine/drive_c/Program\ Files/Picasa2/Picasa2.exe
```

---

### Post by seshomaru samma on 2006-03-13
Strange I followed your instructions but I still get the same error message.
I suspect it might be due to the fact that google forces me to download a Chinese version of picasa -that might confuse Wine. 
How do you navigate to Wine's C folder?
I have a Wine file in usr/bin but not a directory.

---

### Post by bluevoodoo1 on 2006-03-13
[QUOTE=seshomaru samma]Strange I followed your instructions but I still get the same error message.
I suspect it might be due to the fact that google forces me to download a Chinese version of picasa -that might confuse Wine. 
How do you navigate to Wine's C folder?
I have a Wine file in usr/bin but not a directory.[/QUOTE]

.wine is a hidden folder in your home folder. In Nautilus, hit Ctrl+h or go to View > Show hidden files. Then the path is..

.wine/drive_c/Program\ Files/Picasa2/Picasa2.exe

---

### Post by seshomaru samma on 2006-03-14
Thanks, Picasa is there alright but when I click 'Open with Wine'  nothing happens.
BTW- how can I see these hidden files with the terminal?

---

### Post by bluevoodoo1 on 2006-03-14
[QUOTE=seshomaru samma]Thanks, Picasa is there alright but when I click 'Open with Wine'  nothing happens.
BTW- how can I see these hidden files with the terminal?[/QUOTE]


you can just type the name of the folder to navigate to it (even if it's hidden)

cd .wine

will bring you to 
```
bluevoodoo1@ubuntu:~/.wine$
```

It's probably better that you open picasa from the terminal so you can see any potential errors. (That's probably what is happening because nothing has happened when you clicked on it).

You can also have Nautilus open when you do this so you can see the exact path/names of folders. 

so back at ~/$ navigate over to Picasa and try to open it...

```
wine .wine/drive_c/Program\ Files/Picasa2/PICASA2.exe
```

The path or name of your .exe file might not be the same, and there are a few .exe files there. Use nautilus to help you, or "cd" to each folder one at a time and use "ls" to get the folders (if you want to do it cimpletely in the terminal)

---

### Post by seshomaru samma on 2006-03-15
Thanks , I actualy meant how do you see hidden files in the terminal
but I learned that it's :
```
ls -a

```
Anyway - I still get the same error as in my first post when I run it from the terminal.

Is your Picasa in English?

---

### Post by bluevoodoo1 on 2006-03-15
[QUOTE=seshomaru samma]Is your Picasa in English?[/QUOTE]

Yes.

---

