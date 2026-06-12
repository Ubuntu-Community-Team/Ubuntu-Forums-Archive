---
title: "Rock Band Drums"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Nexios on 2008-03-15
I found a neat program for Windows that let's you use the Rock Band drum set as an electric set [http://andrewrudson.com/drummachine/main.php](http://andrewrudson.com/drummachine/main.php) . Unfortunately, there's no Linux support that I know of (I'm running 7.04, Gutsy was given me trouble). I have WINE installed, so I loaded the install file for the program and Wine did its thing. The install went fine, but when I click on the desktop icon a window appears, the disappears. I tried opening the terminal and entering

wine '/home/sean/.wine/drive_c/Program Files/Drum Machine/DrumMachine.exe'

As I understand it (n00b here), that's the command that tells wine to execute the .exe file. Anyways, the same thing happens with the window, but the terminal scrolls out with this:

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on ATI IXP Modem, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x24a5ec,0x00000000), stub!
wine: Call from 0x7b840f60 to unimplemented function d3dx9_36.dll.D3DXCreateSprite, aborting
wine: Unimplemented function d3dx9_36.dll.D3DXCreateSprite called at address 0x7b840f60 (thread 0009), starting debugger...
Unhandled exception: unimplemented function d3dx9_36.dll.D3DXCreateSprite called in 32-bit code (0x7b840fda).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b840fda ESP:0024a950 EBP:0024a9b4 EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82c131 EBX:7b8ac8a0 ECX:00000000 EDX:0024a9cc
 ESI:0024a9cc EDI:00010024
Stack dump:
0x0024a950:  0024a9cc 00000008 7bc32e87 80000100
0x0024a960:  00000001 00000000 7b840f60 00000002
0x0024a970:  7e84a428 7e84acba 0024a980 00000000
0x0024a980:  00139e10 00000001 005a4628 00000008
0x0024a990:  ffffffff 10007a1f 001385d8 0000009f
0x0024a9a0:  3f800000 00010024 7b840f6a 00000001
Backtrace:
=>1 0x7b840fda RaiseException+0x7a() in kernel32 (0x0024a9b4)
  2 0x7e84a3d5 in d3dx9_36 (+0xa3d5) (0x0024a9d4)
  3 0x7e848b6c in d3dx9_36 (+0x8b6c) (0xffffffff)
0x7b840fda RaiseException+0x7a in kernel32: subl        $4,%esp
Modules:
Module  Address                 Debug info      Name (97 modules)
PE        340000-  3ca000       Deferred        audiere
PE        400000-  45c000       Deferred        drummachine
PE      10000000-1002b000       Deferred        graphite
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d4d2000-7d4de000       Deferred        libgcc_s.so.1
ELF     7d4de000-7d4e7000       Deferred        librt.so.1
ELF     7d5a1000-7df0e000       Deferred        fglrx_dri.so
ELF     7df0e000-7dfae000       Deferred        libgl.so.1
ELF     7dfae000-7dfcb000       Deferred        imm32<elf>
  \-PE  7dfb0000-7dfcb000       \               imm32
ELF     7dfcb000-7dfdf000       Deferred        midimap<elf>
  \-PE  7dfd0000-7dfdf000       \               midimap
ELF     7dfdf000-7e005000       Deferred        msacm32<elf>
  \-PE  7dff0000-7e005000       \               msacm32
ELF     7e005000-7e01c000       Deferred        msacm32<elf>
  \-PE  7e010000-7e01c000       \               msacm32
ELF     7e01c000-7e0e1000       Deferred        libasound.so.2
ELF     7e0e1000-7e116000       Deferred        winealsa<elf>
  \-PE  7e0f0000-7e116000       \               winealsa
ELF     7e116000-7e167000       Deferred        libgcrypt.so.11
ELF     7e167000-7e17c000       Deferred        libtasn1.so.3
ELF     7e17c000-7e1aa000       Deferred        libcrypt.so.1
ELF     7e1aa000-7e21a000       Deferred        libgnutls.so.13
ELF     7e21a000-7e24b000       Deferred        libcups.so.2
ELF     7e2a9000-7e2db000       Deferred        uxtheme<elf>
  \-PE  7e2b0000-7e2db000       \               uxtheme
ELF     7e2db000-7e2e0000       Deferred        libxfixes.so.3
ELF     7e2e0000-7e2e9000       Deferred        libxcursor.so.1
ELF     7e2e9000-7e2ef000       Deferred        libxrandr.so.2
ELF     7e2ef000-7e2f7000       Deferred        libxrender.so.1
ELF     7e2f7000-7e2fc000       Deferred        libxdmcp.so.6
ELF     7e2fc000-7e2ff000       Deferred        libxau.so.6
ELF     7e2ff000-7e3f0000       Deferred        libx11.so.6
ELF     7e3f0000-7e3fe000       Deferred        libxext.so.6
ELF     7e3fe000-7e403000       Deferred        libxxf86vm.so.1
ELF     7e403000-7e41b000       Deferred        libice.so.6
ELF     7e41b000-7e424000       Deferred        libsm.so.6
ELF     7e42a000-7e42e000       Deferred        libgpg-error.so.0
ELF     7e430000-7e4be000       Deferred        winex11<elf>
  \-PE  7e440000-7e4be000       \               winex11
ELF     7e52c000-7e54c000       Deferred        libexpat.so.1
ELF     7e54c000-7e577000       Deferred        libfontconfig.so.1
ELF     7e583000-7e597000       Deferred        libz.so.1
ELF     7e597000-7e602000       Deferred        libfreetype.so.6
ELF     7e602000-7e68e000       Deferred        winmm<elf>
  \-PE  7e610000-7e68e000       \               winmm
ELF     7e68e000-7e6a1000       Deferred        libresolv.so.2
ELF     7e6ad000-7e6cb000       Deferred        iphlpapi<elf>
  \-PE  7e6b0000-7e6cb000       \               iphlpapi
ELF     7e6cb000-7e729000       Deferred        rpcrt4<elf>
  \-PE  7e6e0000-7e729000       \               rpcrt4
ELF     7e729000-7e7c9000       Deferred        ole32<elf>
  \-PE  7e740000-7e7c9000       \               ole32
ELF     7e7c9000-7e7ff000       Deferred        dinput<elf>
  \-PE  7e7d0000-7e7ff000       \               dinput
ELF     7e7ff000-7e817000       Deferred        dinput8<elf>
  \-PE  7e800000-7e817000       \               dinput8
ELF     7e817000-7e836000       Deferred        d3dx8<elf>
  \-PE  7e820000-7e836000       \               d3dx8
ELF     7e836000-7e851000       Export          d3dx9_36<elf>
  \-PE  7e840000-7e851000       \               d3dx9_36
ELF     7e851000-7e86a000       Deferred        d3dx9_34<elf>
  \-PE  7e860000-7e86a000       \               d3dx9_34
ELF     7e86a000-7e960000       Deferred        wined3d<elf>
  \-PE  7e880000-7e960000       \               wined3d
ELF     7e960000-7e990000       Deferred        d3d9<elf>
  \-PE  7e970000-7e990000       \               d3d9
ELF     7e990000-7e9c5000       Deferred        winspool<elf>
  \-PE  7e9a0000-7e9c5000       \               winspool
ELF     7e9c5000-7ea84000       Deferred        comctl32<elf>
  \-PE  7e9d0000-7ea84000       \               comctl32
ELF     7ea84000-7eace000       Deferred        advapi32<elf>
  \-PE  7ea90000-7eace000       \               advapi32
ELF     7eace000-7eb64000       Deferred        gdi32<elf>
  \-PE  7eae0000-7eb64000       \               gdi32
ELF     7eb64000-7ec9e000       Deferred        user32<elf>
  \-PE  7eb80000-7ec9e000       \               user32
ELF     7ec9e000-7ecf4000       Deferred        shlwapi<elf>
  \-PE  7ecb0000-7ecf4000       \               shlwapi
ELF     7ecf4000-7edf9000       Deferred        shell32<elf>
  \-PE  7ed00000-7edf9000       \               shell32
ELF     7edf9000-7ee99000       Deferred        comdlg32<elf>
  \-PE  7ee00000-7ee99000       \               comdlg32
ELF     7efab000-7efb6000       Deferred        libnss_files.so.2
ELF     7efb6000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff4000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7ca5000-b7cae000       Deferred        libnss_compat.so.2
ELF     b7caf000-b7cb3000       Deferred        libdl.so.2
ELF     b7cb3000-b7df4000       Deferred        libc.so.6
ELF     b7df5000-b7e0c000       Deferred        libpthread.so.0
ELF     b7e18000-b7f2c000       Deferred        libwine.so.1
ELF     b7f2e000-b7f49000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Drum Machine\DrumMachine.exe
        00000009    0 <==
0000000a 
        0000000b    0
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
00000010 
        00000012    0
        00000011    0
Backtrace:
=>1 0x7b840fda RaiseException+0x7a() in kernel32 (0x0024a9b4)
  2 0x7e84a3d5 in d3dx9_36 (+0xa3d5) (0x0024a9d4)
  3 0x7e848b6c in d3dx9_36 (+0x8b6c) (0xffffffff)
wine: Call from 0x7b840f60 to unimplemented function d3dx9_36.dll.D3DXCreateTeapot, aborting
wine: Call from 0x7b840f60 to unimplemented function d3dx9_36.dll.D3DXCreateTextA, aborting

Which doesn't tell me a thing. I would appreciate it if someone could decode this for me, or point out the painfully obvious fault I must have made. Any suggestions are welcome.

Feisty 7.04
HP Pavillion dv8310ca
2.0GHz AMD Turion 64
ATI Radaon Xpress 200m
1GB RAM

---

### Post by Joeb454 on 2008-03-15
Looks like an error with ALSA (looking at the first few lines anyway :)) and some Direct 3D / DirectX dll's :)

---

### Post by kellemes on 2008-03-15
There are a hole lot of issues, can't say I have a fix for this I'm afraid.
I couldn't find it at [WineHQ]("http://appdb.winehq.org/"). My guess is that it's not going to work.
If this program is real important to you, you can try to run it in a vm like [Virtualbox]("https://help.ubuntu.com/community/VirtualBox"), although it seems to strongly depend on a capable videocard (something a vm doesn't really offer), still worth the try.
Or well.. go dual-boot.
Sorry for not helping here ;-)

---

### Post by Nexios on 2008-03-15
OK, thanks anyways, I'll just keep fiddlin' with it.

---

### Post by T-56 on 2008-04-10
I came across this link in search of the same sort of functionality

[http://www.perlmonks.org/index.pl?node_id=679581]("http://www.perlmonks.org/index.pl?node_id=679581")

---

### Post by oki-vino on 2008-04-12
How does that work? I'm really new to linux. How do I get this rock_band_drums.pl thing?  I want to use my rock band (xbox) pads for Hydrogen or similar programs.

---

