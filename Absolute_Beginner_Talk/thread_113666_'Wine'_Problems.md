---
title: "'Wine' Problems"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-01-06
I'm trying to install wine but get problems all the time whilst executing it.
I *think* I installed wine from the the wine website ([http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)) and followed the example using synaptic. I installed it. But when I try to run it from the terminal, I keep getting the following error and the terminal freezes. Doesn't continue. (It's pretty long)

jaygo333@Ubuntu:~$ wine
wine: creating configuration directory '/home/jaygo333/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ec3913f (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7ec3913f).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7ec3913f ESP:7faffc8c EBP:7faffcc8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c0f2f00 ECX:b7f8f900 EDX:7c018c90
 ESI:7c018c90 EDI:7c018c90
Stack dump:
0x7faffc8c:  7c018c90 7ec6e9a0 7c018c90 7ec37ab6
0x7faffc9c:  7c018c90 7c018c90 7ed3f7d0 7c0f1868
0x7faffcac:  7ec94883 7c018c90 7c0f186c 00000001
0x7faffcbc:  7ede05cc 7ede93d8 00000001 7faffcdc
0x7faffccc:  7edace34 7c018c90 7ede05cc 7beffc3c
0x7faffcdc:  7faffe10 7edc2541 7beb382e 7faffdac
0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ec3913f in libgl.so.1 (+0x3613f) (0x7ec3913f)
  2 0x7edace34 X11DRV_GDI_Finalize+0x24 in winex11 (0x7edace34)
  3 0x7edc2541 DllMain+0x41 in winex11 (0x7edc2541)
  4 0x7edd0f58 in winex11 (+0x50f58) (0x7edd0f58)
  5 0x7bec00b5 call_dll_entry_point+0x15 in ntdll (0x7bec00b5)
  6 0x7bec0e6a in ntdll (+0x20e6a) (0x7bec0e6a)
  7 0x7bec1124 in ntdll (+0x21124) (0x7bec1124)
  8 0x7fcdc729 ExitProcess+0x19 in kernel32 (0x7fcdc729)
  9 0x7fb1ea4c in rundll32 (+0xea4c) (0x7fb1ea4c)
  10 0x7fcddc67 in kernel32 (+0x4dc67) (0x7fcddc67)
  11 0xb7fa8c17 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7fa8c17)
0x7ec3913f: movl        0x0(%eax),%eax
Modules:
Module  Address                 Debug info      Name (94 modules)
ELF     0x7be8c000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7d9da000-7d9f0000     Deferred        advpack<elf>
  \-PE  0x7d9e0000-7d9f0000     \               advpack
ELF     0x7db29000-7db7e000     Deferred        shlwapi<elf>
  \-PE  0x7db40000-7db7e000     \               shlwapi
ELF     0x7db7e000-7dc3d000     Deferred        shell32<elf>
  \-PE  0x7db90000-7dc3d000     \               shell32
ELF     0x7dc3d000-7dc6d000     Deferred        uxtheme<elf>
  \-PE  0x7dc40000-7dc6d000     \               uxtheme
ELF     0x7dc6d000-7dd1c000     Deferred        comctl32<elf>
  \-PE  0x7dc80000-7dd1c000     \               comctl32
ELF     0x7dd1c000-7dd67000     Deferred        dsound<elf>
  \-PE  0x7dd30000-7dd67000     \               dsound
ELF     0x7dd67000-7ddc0000     Deferred        quartz<elf>
  \-PE  0x7dd80000-7ddc0000     \               quartz
ELF     0x7ded6000-7deeb000     Deferred        midimap<elf>
  \-PE  0x7dee0000-7deeb000     \               midimap
ELF     0x7deeb000-7df02000     Deferred        msacm<elf>
  \-PE  0x7def0000-7df02000     \               msacm
ELF     0x7df02000-7df44000     Deferred        wineoss<elf>
  \-PE  0x7df10000-7df44000     \               wineoss
ELF     0x7df66000-7df8a000     Deferred        msvfw32<elf>
  \-PE  0x7df70000-7df8a000     \               msvfw32
ELF     0x7df8a000-7e017000     Deferred        oleaut32<elf>
  \-PE  0x7dfa0000-7e017000     \               oleaut32
ELF     0x7e017000-7e09d000     Deferred        ole32<elf>
  \-PE  0x7e030000-7e09d000     \               ole32
ELF     0x7e09d000-7e11e000     Deferred        winmm<elf>
  \-PE  0x7e0b0000-7e11e000     \               winmm
ELF     0x7e11e000-7e140000     Deferred        msacm32<elf>
  \-PE  0x7e130000-7e140000     \               msacm32
ELF     0x7e25b000-7e26f000     Deferred        avicap32<elf>
  \-PE  0x7e260000-7e26f000     \               avicap32
ELF     0x7e26f000-7e295000     Deferred        devenum<elf>
  \-PE  0x7e280000-7e295000     \               devenum
ELF     0x7e295000-7e2b3000     Deferred        iphlpapi<elf>
  \-PE  0x7e2a0000-7e2b3000     \               iphlpapi
ELF     0x7e2b3000-7e2f7000     Deferred        rpcrt4<elf>
  \-PE  0x7e2c0000-7e2f7000     \               rpcrt4
ELF     0x7e2f7000-7e30b000     Deferred        lz32<elf>
  \-PE  0x7e300000-7e30b000     \               lz32
ELF     0x7e30b000-7e323000     Deferred        version<elf>
  \-PE  0x7e310000-7e323000     \               version
ELF     0x7e323000-7e375000     Deferred        setupapi<elf>
  \-PE  0x7e330000-7e375000     \               setupapi
ELF     0x7e443000-7e44c000     Deferred        libxcursor.so.1
ELF     0x7e44c000-7e467000     Deferred        imm32<elf>
  \-PE  0x7e450000-7e467000     \               imm32
ELF     0x7e467000-7e483000     Deferred        ximcp.so.2
ELF     0x7e483000-7e48b000     Deferred        libxrender.so.1
ELF     0x7e49a000-7ec03000     Deferred        libglcore.so.1
ELF     0x7ec03000-7ec82000     Export          libgl.so.1
ELF     0x7ec82000-7ed42000     Deferred        libx11.so.6
ELF     0x7ed42000-7ed4f000     Deferred        libxext.so.6
ELF     0x7ed4f000-7ed54000     Deferred        libxxf86vm.so.1
ELF     0x7ed54000-7ed6d000     Deferred        libice.so.6
ELF     0x7ed6d000-7edea000     Export          winex11<elf>
  \-PE  0x7ed80000-7edea000     \               winex11
ELF     0x7edea000-7ee09000     Deferred        libexpat.so.1
ELF     0x7ee09000-7ee37000     Deferred        libfontconfig.so.1
ELF     0x7ee37000-7ee4b000     Deferred        libz.so.1
ELF     0x7ee4b000-7eeb5000     Deferred        libfreetype.so.6
ELF     0x7eeb5000-7eef1000     Deferred        advapi32<elf>
  \-PE  0x7eec0000-7eef1000     \               advapi32
ELF     0x7efd7000-7f8d7000     Deferred        gdi32<elf>
  \-PE  0x7f020000-7f8d7000     \               gdi32
ELF     0x7f8d7000-7f9f0000     Deferred        user32<elf>
  \-PE  0x7f8f0000-7f9f0000     \               user32
ELF     0x7fb00000-7fb05000     Deferred        libxxf86dga.so.1
ELF     0x7fb05000-7fb0c000     Deferred        libsm.so.6
ELF     0x7fb0c000-7fb20000     Export          rundll32<elf>
  \-PE  0x7fb10000-7fb20000     \               rundll32
ELF     0x7fb21000-7fb2c000     Deferred        libgcc_s.so.1
ELF     0x7fc74000-7fd70000     Export          kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe80000-7fe84000     Deferred        libxdmcp.so.6
ELF     0x7fe84000-7fe8e000     Deferred        libnss_files.so.2
ELF     0x7fe8e000-7fe97000     Deferred        libnss_nis.so.2
ELF     0x7fe97000-7feac000     Deferred        libnsl.so.1
ELF     0x7feac000-7feb5000     Deferred        libnss_compat.so.2
ELF     0x7feb9000-7febd000     Deferred        libxfixes.so.3
ELF     0x7febd000-7febf000     Deferred        xlcutf8load.so.2
ELF     0x7febf000-7fec2000     Deferred        libxrandr.so.2
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7e51000-b7e53000     Deferred        libnvidia-tls.so.1
ELF     0xb7e61000-b7e64000     Deferred        libdl.so.2
ELF     0xb7e64000-b7f92000     Deferred        libc.so.6
ELF     0xb7f92000-b7fa4000     Deferred        libpthread.so.0
ELF     0xb7fa4000-b7fbe000     Export          libwine.so.1
ELF     0xb7fbe000-b7fc1000     Deferred        libxau.so.6
ELF     0xb7fd0000-b7fe6000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\rundll32.exe
        00000009    0 <==
WineDbg terminated on pid 0x8

What did I do wrong. I want to use wine to istall some of my games from windows but can't open it. 
I've tried Cedega but don't know how to install it. I have the .deb file for cedega but don't know what to do with it. Any help here also wanted.

Does anybody know how to fix this?
Any Help Greatly Welcome.1?1

:confused:h34r: Jaygo333 :confused:h34r:

---

### Post by Qrk on 2006-01-06
First of all, you need to configure it. Use synaptic to install winetools. This is graphical setup program that should solve some of your problems. 

First run **winecfg** in a terminal, to configure wine graphically. Then run **winetools** to install the basic windows system that wine needs to run most windows programs. 

With both of them together, wine isn't very hard at all.

Edit:
If you followed the wine website, you shouldn't need to add anything else to your sources. But if not add:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

### Post by Jaygo333 on 2006-01-06
[QUOTE=Qrk]First of all, you need to configure it. Use synaptic to install winetools. This is graphical setup program that should solve some of your problems. 

First run **winecfg** in a terminal, to configure wine graphically. Then run **winetools** to install the basic windows system that wine needs to run most windows programs. 

With both of them together, wine isn't very hard at all.

Edit:
If you followed the wine website, you shouldn't need to add anything else to your sources. But if not add:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/[/QUOTE]

Imanaged to install wintools and run winecfg properly.
When I run winetools, I get the graphical user interface but halfway get the same error.I just manage to install the base system and when it's setting up, get the error.
HEre's the last command I ran:

jaygo333@Ubuntu:~$ sudo winecfg
Password:
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
jaygo333@Ubuntu:~$ winetools
detecting Wine version... done.
Drive C: is /home/jaygo333/.wine/drive_c
Wine 0.9.5
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.5".
Calls to wine are executed as  "wine".
Config is /home/jaygo333/.wine/winetools.log.
Choice is Base setup
Choice is Create a Fake Windows drive with checked=F
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ec3913f (thread 0009), starting debugger...
WineDbg starting on pid 0x8

Then it continues with the same error and the same problem. 
Help.1?1

:(h34r: Jaygo333 :(h34r:

---

### Post by Drew32 on 2006-01-07
why dont you install Wine from the Universe

"Sudo apt-get install wine"

thats what i did and it installs and configs right
or at least it did for me.

---

### Post by dschaller on 2006-01-07
I'm having *exactly* the same problem as the original poster. Apparently 0.9.5 in Ubuntu simply does not work? Can someone write who has gotten 0.9.5 to work? I even tried building from source and had the same trouble.

---

### Post by MighMoS on 2006-01-07
[QUOTE=dschaller]I'm having *exactly* the same problem as the original poster. Apparently 0.9.5 in Ubuntu simply does not work? Can someone write who has gotten 0.9.5 to work? I even tried building from source and had the same trouble.[/QUOTE]
I've installed 0.9.5 from wine's repositories and I was able to install Warcraft III just fine.

---

### Post by R3linquish3r on 2006-01-07
when i first installed wine and ran winecfg it ran fine. i selected alsa as my sound, now hwen i try to open winecfg i get this error:

> ed@ubuntu:~$ winecfg
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
ALSA lib pcm_dsnoop.c:563:(snd_pcm_dsnoop_open) unable to open slave
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  13
  Current serial number in output stream:  14
ed@ubuntu:~$

---

### Post by The Pinny Parlour on 2006-01-07
What is wine? in the linux sense

---

### Post by Jaygo333 on 2006-01-07
[QUOTE=The Pinny Parlour]What is wine? in the linux sense[/QUOTE]

It's a windows(bleH) Emulator. Let's you run windows(bleH) programs in it as if its windows(bleH) whilst in actual linux. I wnt it for my windows(bleH) Games.

Has anybody actually gotten wine to work? Post here how you did it. 
Faast

:mad:h34r: Jaygo333 :mad:h34r:

---

### Post by nalmeth on 2006-01-07
> It's a windows(bleH) Emulator

Actually (donning a w(h)ine developers hat) its refered to as a windows compatibility layer. :p 

Jokes aside, it is sweet, and I think it does a standup job considering the undertaking.

> Has anybody actually gotten wine to work? Post here how you did it. 

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

I don't have my sources.list in front of me right now, so I thought I would refer you to this. You could of course add these lines directly to your /etc/apt/sources.list and sudo apt-get install wine.

---

### Post by Jaygo333 on 2006-01-08
[QUOTE=nalmeth]Actually (donning a w(h)ine developers hat) its refered to as a windows compatibility layer. :p 

Jokes aside, it is sweet, and I think it does a standup job considering the undertaking.



[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

I don't have my sources.list in front of me right now, so I thought I would refer you to this. You could of course add these lines directly to your /etc/apt/sources.list and sudo apt-get install wine.[/QUOTE]

I tried the website first and installed from the insturctions they offered to use synaptic. It instals poperly *I Think* frm synaptics but when I try to install it and run, taht's when I get the problem posted above. 
The webstie above is the first thing I tried before coming here.

still:confused: h34r: Jaygo333 still:confused:h34r:

---

### Post by nalmeth on 2006-01-09
Oh, are you just trying to execute wine on its own?

To use wine you need to have it run an exe. In the terminal, go to the directory where the exe is, and type
```
wine whatever.exe
```

---

### Post by WebMania on 2006-12-11
Installed Wine under 6.10. fine working with some Windows apps. BUT I do not get any Internet connection under Wine. Any Windows apps tells me that I have no network..... Ubuntu works fine and fast with my Internet modem. Where or better, how to enable network connections for applications running in Wine. Please any advise is welcome. ](*,) :confused:

---

