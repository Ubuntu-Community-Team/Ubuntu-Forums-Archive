---
title: "A problem with Wine and Webpage Maker"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by _d5 on 2007-09-27
Hi,

I tried to install a piece of software called Webpage maker (a program with which you can make html pages). During the intallation (through Wine) everything was ok, but afterwards I am not able to start the program. I tried a few times - no result. The funny thing was that I nstalled Photoshop CS through wine and there were no problems, even though Photoshop is way more complicated than Webpage Maker, the Maker does not work.

Any ideas or suggestions?

Thank you in advnace!

EDIT: I restarted the system, and the Webpage Maker appeared at the Wine menu, but it still does not start...

---

### Post by hyper_ch on 2007-09-27
Each program is different so the "more complicated" approach doesn't bring you anywhere... when you start that software from the terminal have a look at the output it generates, that can give you a clue why it's not working.

---

### Post by _d5 on 2007-09-27
> **hyper_ch said:**
> Each program is different so the "more complicated" approach doesn't bring you anywhere... when you start that software from the terminal have a look at the output it generates, that can give you a clue why it's not working.



wine: could not load L"c:\\windows\\system32\\webpagemaker.exe": Module not found

This is the answer wich i get from the console after i type:

wine webpagemaker.exe

in it!

Any ideas?

---

### Post by hyper_ch on 2007-09-27
you need to use the correct path to the webpagemaker.exe or run it from the wepagemaker install folder.

---

### Post by _d5 on 2007-09-27
well i tried anything, even though i tried to enter the folder where Webpagemaker.exe is situated, i could not enter one of the parental folders the Program Files one, the cd command just do not work. I tried to get the exact path through the file browser, i got it, but after 

wine /home/d/.wine/drive_c/Program Files/Web Page Maker V2/WebPageMaker.exe

i get:

wine: cannot find '/home/d/.wine/drive_c/Program'

I think that the problem is in the damn space between the two words of the directory Program Files.

What to do?

I think that i will just give up. No Webpage Maker with Ubuntu!

I also tried to install MS Office XP, but the installation crashes! No MS Office with Ubuntu. The good thing is that Photoshop works.

---

### Post by hyper_ch on 2007-09-27
you use a "space" in that folder so you have to either parse it to:   Program\ Files or put the whole path into " "

What do you need Webpage Maker for?
What do you need Office XP for?

---

### Post by _d5 on 2007-09-27
I have just tried the tric with the quotes, it seems to work, so after:

wine "/home/d/.wine/drive_c/Program Files/Web Page Maker V2/WebPageMaker.exe"

I get:

wine: Unhandled page fault on read access to 0x00000000 at address 0x0000:0x0049e744 (thread 0009), starting debugger...
First chance exception: page fault on read access to 0x00000000 in 32-bit code (0x0049e744).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0049e744 ESP:0033fed4 EBP:0033feec EFLAGS:00210246(   - 00      -RIZP1)
 EAX:0033fee8 EBX:00686c00 ECX:0040285c EDX:00000000
 ESI:00679eac EDI:7ffdf000
Stack dump:
0x0033fed4:  0033fefc 0049e76b 0033feec 00686c00
0x0033fee4:  009597c4 00000000 0033ff08 00679ec8
0x0033fef4:  7b8ad908 00000018 0033ff2c 004046ec
0x0033ff04:  0033ff08 0033ffe8 7b87221e 7ffdf000
0x0033ff14:  00000000 00000000 00000000 00000000
0x0033ff24:  00000000 00000000 ffffffff 7b82df10
Backtrace:
=>1 0x0049e744 in webpagemaker (+0x9e744) (0x0033feec)
  2 0x00679ec8 in webpagemaker (+0x279ec8) (0x0033ff08)
  3 0x7b87221e in kernel32 (+0x5221e) (0x0033ffe8)
  4 0xb7e67897 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0049e744: movb        0x0(%edx),%dl
Modules:
Module  Address                 Debug info      Name (95 modules)
PE      340000-355000   Deferred        mousehook
PE      400000-737000   Export          webpagemaker
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7df2c000-7df40000       Deferred        olepro32<elf>
  \-PE  7df30000-7df40000       \               olepro32
ELF     7df45000-7df59000       Deferred        msimg32<elf>
  \-PE  7df50000-7df59000       \               msimg32
ELF     7df59000-7df6e000       Deferred        midimap<elf>
  \-PE  7df60000-7df6e000       \               midimap
ELF     7df6e000-7df86000       Deferred        msacm32<elf>
  \-PE  7df70000-7df86000       \               msacm32
ELF     7df86000-7dfc2000       Deferred        wineoss<elf>
  \-PE  7df90000-7dfc2000       \               wineoss
ELF     7e05f000-7e063000       Deferred        libgpg-error.so.0
ELF     7e063000-7e0b4000       Deferred        libgcrypt.so.11
ELF     7e0b4000-7e0c9000       Deferred        libtasn1.so.3
ELF     7e0c9000-7e0f7000       Deferred        libcrypt.so.1
ELF     7e103000-7e173000       Deferred        libgnutls.so.13
ELF     7e173000-7e1a4000       Deferred        libcups.so.2
ELF     7e1a4000-7e1d6000       Deferred        uxtheme<elf>
  \-PE  7e1b0000-7e1d6000       \               uxtheme
ELF     7e1d8000-7e1dd000       Deferred        libxfixes.so.3
ELF     7e1dd000-7e1e6000       Deferred        libxcursor.so.1
ELF     7e1e6000-7e1ec000       Deferred        libxrandr.so.2
ELF     7e1ec000-7e1f4000       Deferred        libxrender.so.1
ELF     7e1f4000-7e1f7000       Deferred        libxinerama.so.1
ELF     7e1f7000-7e200000       Deferred        libdrm.so.2
ELF     7e200000-7e260000       Deferred        libgl.so.1
ELF     7e260000-7e265000       Deferred        libxdmcp.so.6
ELF     7e265000-7e268000       Deferred        libxau.so.6
ELF     7e268000-7e359000       Deferred        libx11.so.6
ELF     7e359000-7e367000       Deferred        libxext.so.6
ELF     7e367000-7e36c000       Deferred        libxxf86vm.so.1
ELF     7e36c000-7e384000       Deferred        libice.so.6
ELF     7e384000-7e38d000       Deferred        libsm.so.6
ELF     7e38d000-7e41b000       Deferred        winex11<elf>
  \-PE  7e3a0000-7e41b000       \               winex11
ELF     7e48c000-7e4ac000       Deferred        libexpat.so.1
ELF     7e4ac000-7e4d7000       Deferred        libfontconfig.so.1
ELF     7e4d7000-7e4eb000       Deferred        libz.so.1
ELF     7e4eb000-7e556000       Deferred        libfreetype.so.6
ELF     7e556000-7e57c000       Deferred        msacm32<elf>
  \-PE  7e560000-7e57c000       \               msacm32
ELF     7e57c000-7e5b6000       Deferred        avifil32<elf>
  \-PE  7e580000-7e5b6000       \               avifil32
ELF     7e5b6000-7e5dd000       Deferred        msvfw32<elf>
  \-PE  7e5c0000-7e5dd000       \               msvfw32
ELF     7e5dd000-7e66c000       Deferred        winmm<elf>
  \-PE  7e5f0000-7e66c000       \               winmm
ELF     7e66c000-7e70c000       Deferred        comdlg32<elf>
  \-PE  7e670000-7e70c000       \               comdlg32
ELF     7e70c000-7e765000       Deferred        shlwapi<elf>
  \-PE  7e720000-7e765000       \               shlwapi
ELF     7e765000-7e85a000       Deferred        shell32<elf>
  \-PE  7e780000-7e85a000       \               shell32
ELF     7e85a000-7e88d000       Deferred        winspool<elf>
  \-PE  7e860000-7e88d000       \               winspool
ELF     7e88d000-7e8aa000       Deferred        imm32<elf>
  \-PE  7e890000-7e8aa000       \               imm32
ELF     7e8aa000-7e966000       Deferred        comctl32<elf>
  \-PE  7e8b0000-7e966000       \               comctl32
ELF     7e966000-7e97a000       Deferred        lz32<elf>
  \-PE  7e970000-7e97a000       \               lz32
ELF     7e97a000-7e993000       Deferred        version<elf>
  \-PE  7e980000-7e993000       \               version
ELF     7e993000-7e9a6000       Deferred        libresolv.so.2
ELF     7e9a6000-7e9c4000       Deferred        iphlpapi<elf>
  \-PE  7e9b0000-7e9c4000       \               iphlpapi
ELF     7e9c4000-7ea19000       Deferred        rpcrt4<elf>
  \-PE  7e9d0000-7ea19000       \               rpcrt4
ELF     7ea19000-7eab3000       Deferred        ole32<elf>
  \-PE  7ea30000-7eab3000       \               ole32
ELF     7eab3000-7eb4e000       Deferred        oleaut32<elf>
  \-PE  7ead0000-7eb4e000       \               oleaut32
ELF     7eb4e000-7eb94000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb94000       \               advapi32
ELF     7eb94000-7eba0000       Deferred        libgcc_s.so.1
ELF     7ec96000-7ed53000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed53000       \               gdi32
ELF     7ed53000-7ee8f000       Deferred        user32<elf>
  \-PE  7ed70000-7ee8f000       \               user32
ELF     7efa1000-7efac000       Deferred        libnss_files.so.2
ELF     7efac000-7efb6000       Deferred        libnss_nis.so.2
ELF     7efb6000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff4000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7cf8000-b7cfc000       Deferred        libdl.so.2
ELF     b7cfc000-b7e3d000       Deferred        libc.so.6
ELF     b7e3d000-b7e54000       Deferred        libpthread.so.0
ELF     b7e60000-b7f71000       Export          libwine.so.1
ELF     b7f73000-b7f8e000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Web Page Maker V2\WebPageMaker.exe
        00000009    0 <==

And obviously this is the moment, when I give up.

As an answer to your questions about Webpage Maker and MS Office:

Webpage Maker is an application, with which you can make a web site without entering a single piece of code etc. I havent writen anything with the keyboard and i managed to make the site of my previous employer ([www.plastics-bavaria.bg](www.plastics-bavaria.bg)). So this is why i need the damn WPM.

I do not need MS Office, but my girlfriend uses the same PC and she is used to the M$ Office and instead of shutting down Ubuntu and entering the Win i just want to have it here. This is the reason.

Thank you for the help, If you have any more ideas, i am eager to try them if not thank you a lot for the help.

---

### Post by hyper_ch on 2007-09-27
How about NVU ( [http://nvudev.com/screenshots.php](http://nvudev.com/screenshots.php)) or Kompozer ( [http://www.kompozer.net/screenshots.php](http://www.kompozer.net/screenshots.php) ) for making your html pages?

And why not using OpenOffice? You can alter it so that it saves files in M$ Office format if you want to.

---

### Post by _d5 on 2007-09-27
I will check the programs out.

Thank u 4 the help

---

