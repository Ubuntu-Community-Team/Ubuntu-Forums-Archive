---
title: "Install Direct X 9 on Wine?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by AuroraManson on 2007-11-06
Hey everyone I'm trying to play World of Warcraft on Wine and its keeps crashing with ERROR #132 (0x85100084) Fatal Exception. I'm on gutsy gibbon and have followed the instructions at [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)  it worked on Fiesty Fawn before (however choppily), but it keeps freezing in d3d mode when the game loads into my character's world.  In OpenGL mode my models are seriously out of wack.  D3d seems smoother and looks a hell of a lot better besides it not loading/crashing.   I looked the error up a little bit and it suggested it may be a graphical issue with Direct X I know that wine comes with some capabilities but would feel better if there was some sort of update I could make it do, or a patch I could download but I just can't find it.  Also how do I look up my video card and make sure that Ubuntu is using the most updated version?

Thanks

---

### Post by Hospadar on 2007-11-06
Try having a look at wine's graphics settings.  You don't actually install directX, one of the main functions of wine is to implement the directx interface, as there's no way to run the native directx binaries. 
type in winecfg from a terminal and you'll get at all of wine's settings.

Also make sure you are running at leas XP compatability (this option is also available in winecfg)

---

### Post by AuroraManson on 2007-11-06
Yep I have configured it already for windows xp.  I think ive seen other threads that talk about patching it but haven't found any direct instructions.  Thanks for your reply

---

### Post by inversekinetix on 2007-11-06
Don't you have to add entries to wine's registry in the d3d section?  I know you have to do that for Oblivion to use d3d.

---

### Post by AuroraManson on 2007-11-06
got a link?

Edit; I am currently reviewing this page
[http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

---

### Post by inversekinetix on 2007-11-06
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

dont know if that will help but it has a reg editing section

---

### Post by AuroraManson on 2007-11-06
Thanks

and just incase you guys need a larger error log file:

==============================================================================
World of WarCraft (build 7359)

Exe:      C:\Program Files\World of Warcraft\WoW.exe
(removed)
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0x80000101 (unknown exception) at 0073:FFFFE410




WoWBuild: 7359
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000000  EBX=00001C75  ECX=00001C75  EDX=00000006  ESI=00001C75
EDI=B7DC0FF4  EBP=0033ECF0  ESP=0033ECD4  EIP=FFFFE410  FLG=00000202
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

FFFFE410 0033ECF0 0000:00000000 <unknown>
B7CA7201 0033EE1C 0000:00000000 <unknown>
B7C9EB6E 0033EE60 0000:00000000 <unknown>
7DF08FBB 0033EE90 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7DF09D8D 0033EEB0 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7DF22A91 0033EEE0 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7DFAE243 0033EF30 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7DFAE674 0033EF50 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7DFA87EE 0033F120 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7DFAD064 0033F180 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7DFAE7A2 0033F1C0 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7DFA5F7B 0033F1F0 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7DFA6453 0033F340 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7DF9F0B1 0033F390 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7DF9F2F2 0033F3D0 0000:00000000 C:\Program Files\World of Warcraft\WoW.exe
7E76B5EE 0033F670 0001:0003A5EE c:\windows\system32\wined3d.dll
7E74FC8D 0033F6E0 0001:0001EC8D c:\windows\system32\wined3d.dll
7E80FE4E 0033F710 0001:0000EE4E c:\windows\system32\d3d9.dll
0058A77F 0033F744 0001:0018977F C:\Program Files\World of Warcraft\WoW.exe
00676C44 0033F818 0001:00275C44 C:\Program Files\World of Warcraft\WoW.exe
00676FA3 0033F8E4 0001:00275FA3 C:\Program Files\World of Warcraft\WoW.exe
00677CC9 0033FB04 0001:00276CC9 C:\Program Files\World of Warcraft\WoW.exe
0064BF76 0033FB48 0001:0024AF76 C:\Program Files\World of Warcraft\WoW.exe
006358C5 0033FB98 0001:002348C5 C:\Program Files\World of Warcraft\WoW.exe
0049D60D 0033FC24 0001:0009C60D C:\Program Files\World of Warcraft\WoW.exe
0042510A 0033FCAC 0001:0002410A C:\Program Files\World of Warcraft\WoW.exe
0042C397 0033FCC8 0001:0002B397 C:\Program Files\World of Warcraft\WoW.exe
0042C88C 0033FCE4 0001:0002B88C C:\Program Files\World of Warcraft\WoW.exe
0043BC00 0033FDB0 0001:0003AC00 C:\Program Files\World of Warcraft\WoW.exe
0042065B 0033FDE0 0001:0001F65B C:\Program Files\World of Warcraft\WoW.exe
0041DA99 0033FE54 0001:0001CA99 C:\Program Files\World of Warcraft\WoW.exe
0041EF41 0033FE6C 0001:0001DF41 C:\Program Files\World of Warcraft\WoW.exe
00405A88 0033FF08 0001:00004A88 C:\Program Files\World of Warcraft\WoW.exe
7B874F5E 0033FFE8 0001:00053F5E c:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

FFFFE410 <unknown module> <unknown symbol>+0 (0x00000006,0x0033ED90,0x00000000,0xB7DC2140)
B7CA7201              abort+257 (0x78CB0738,0xB7DA4F55,0x78CB0738,0xB7DA30F2)
B7C9EB6E              __assert_fail+238 (0x7E07BB66,0x7E07BB41,0x00000091,0x7E07BD67)
7DF08FBB              <unknown symbol>+0 (0x7BB00008,0x00000F10,0x00000004,0x0012BDA0)
7DF09D8D              intelWrapInlinePrimitive+29 (0x7BB00008,0x78AFFB18,0x78B00250,0x78B001F8)
7DF22A91              <unknown symbol>+0 (0x7BB00008,0x00000091,0x00000092,0x0000007D)
7DFAE243              <unknown symbol>+0 (0x7BB00008,0x00000000,0x00000004,0x00000030)
7DFAE674              _tnl_RenderClippedPolygon+68 (0x7BB00008,0x0033F0B0,0x00000004,0x0000006C)
7DFA87EE              <unknown symbol>+0 (0x0000007D,0x00000001,0x00000240,0x00000000)
7DFAD064              <unknown symbol>+0 (0x7BB00008,0x00000000,0x00000300,0x00000034)
7DFAE7A2              <unknown symbol>+0 (0x7BB00008,0x7C07855C,0x00000C00,0x7BB00008)
7DFA5F7B              _tnl_run_pipeline+299 (0x7BB00008,0x00000008,0xBA2DEB03,0x00000000)
7DFA6453              _tnl_draw_prims+979 (0x7BB00008,0x7BB3BCE8,0x0033F378,0x00000001)
7DF9F0B1              <unknown symbol>+0 (0x00000004,0x00000000,0x00000090,0x00000300)
7DF9F2F2              <unknown symbol>+0 (0x00000004,0x00000300,0x00001403,0x0A2206B8)
7E76B5EE wined3d.dll  drawPrimitive+2734 (0x0012BDA0,0x00000004,0x00000100,0x00000000)
7E74FC8D wined3d.dll  <unknown symbol>+0 (0x0012BDA0,0x00000004,0x00000000,0x00000091)
7E80FE4E d3d9.dll     <unknown symbol>+0 (0x0012B9D0,0x00000004,0x0001A21B,0x00000000)
0058A77F WoW.exe      <unknown symbol>+0 (0x00000001,0x0001A21B,0x00000001,0x1096025C)
00676C44 WoW.exe      <unknown symbol>+0 (0x00D3B568,0x07C38F88,0x1096025C,0x109603E8)
00676FA3 WoW.exe      <unknown symbol>+0 (0x00D3B568,0x00D50AE8,0x00648F81,0x0000000F)
00677CC9 WoW.exe      <unknown symbol>+0 (0x07CA0008,0x0124C218,0x07CA03F0,0x00573954)
0064BF76 WoW.exe      <unknown symbol>+0 (0x0049BB20,0x07CA0008,0x07BEAC08,0x00000000)
006358C5 WoW.exe      <unknown symbol>+0 (0x07CF7224,0x3F800000,0x00000000,0x00000000)
0049D60D WoW.exe      <unknown symbol>+0 (0x07CA0008,0x00000000,0x07CF7208,0x07CF7224)
0042510A WoW.exe      <unknown symbol>+0 (0x07CF7224,0x07CE6CE8,0x00000009,0x07CE6008)
0042C397 WoW.exe      <unknown symbol>+0 (0x02021688,0x08617020,0x08617008,0x00000000)
0042C88C WoW.exe      <unknown symbol>+0 (0x00000000,0x08617010,0x08617020,0x3F1CED92)
0043BC00 WoW.exe      <unknown symbol>+0 (0x00000000,0x00000000,0x01265008,0x00000000)
0042065B WoW.exe      <unknown symbol>+0 (0x01265008,0x00000011,0x00000000,0x0041EE69)
0041DA99 WoW.exe      <unknown symbol>+0 (0x00000001,0x00405A48,0x00000001,0x00000001)
0041EF41 WoW.exe      <unknown symbol>+0 (0x004095F9,0x00400000,0x00000000,0x00111ACC)
00405A88 WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B874F5E KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7DF09D7              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00DF6000  C:\Program Files\World of Warcraft\WoW.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B929000  c:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCA1000  c:\windows\system32\ntdll.dll
0x7BCC0000 - 0x7BCCE000  c:\windows\system32\psapi.dll
0x7BCE0000 - 0x7BD18000  c:\windows\system32\dbghelp.dll
0x7BD40000 - 0x7BD7A000  c:\windows\system32\dsound.dll
0x7BF40000 - 0x7BF63000  c:\windows\system32\uxtheme.dll
0x7BF90000 - 0x7BF98000  c:\windows\system32\midimap.dll
0x7BFA0000 - 0x7BFB0000  c:\windows\system32\msacm32.drv
0x7BFC0000 - 0x7BFEC000  c:\windows\system32\wineoss.drv
0x7E0F0000 - 0x7E16F000  c:\windows\system32\winex11.drv
0x7E2D0000 - 0x7E320000  c:\windows\system32\rpcrt4.dll
0x7E330000 - 0x7E3C1000  c:\windows\system32\ole32.dll
0x7E3D0000 - 0x7E3E8000  c:\windows\system32\msacm32.dll
0x7E400000 - 0x7E419000  c:\windows\system32\iphlpapi.dll
0x7E420000 - 0x7E446000  c:\windows\system32\ws2_32.dll
0x7E450000 - 0x7E505000  c:\windows\system32\comctl32.dll
0x7E520000 - 0x7E608000  c:\windows\system32\shell32.dll
0x7E620000 - 0x7E660000  c:\windows\system32\shlwapi.dll
0x7E670000 - 0x7E681000  c:\windows\system32\mpr.dll
0x7E690000 - 0x7E6CD000  c:\windows\system32\wininet.dll
0x7E6D0000 - 0x7E6EA000  c:\windows\system32\imm32.dll
0x7E6F0000 - 0x7E6FE000  c:\windows\system32\lz32.dll
0x7E700000 - 0x7E718000  c:\windows\system32\version.dll
0x7E730000 - 0x7E7F9000  c:\windows\system32\wined3d.dll
0x7E800000 - 0x7E828000  c:\windows\system32\d3d9.dll
0x7EB70000 - 0x7EBD4000  c:\windows\system32\opengl32.dll
0x7EBE0000 - 0x7EC1D000  c:\windows\system32\advapi32.dll
0x7EC30000 - 0x7ECB8000  c:\windows\system32\gdi32.dll
0x7ECD0000 - 0x7EDF6000  c:\windows\system32\user32.dll
0x7EE00000 - 0x7EE84000  c:\windows\system32\winmm.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = FFFFE410)

FFFFE410: 5D 5A 59 C3  90 90 90 90  90 90 90 90  90 90 90 90  ]ZY.............


Stack: 1024 bytes starting at (ESP = 0033ECD4)

* = addr               **                                         *           
0033ECD0: 01 00 00 00  F0 EC 33 00  06 00 00 00  75 1C 00 00  ......3.....u...
0033ECE0: 75 58 CA B7  F4 0F DC B7  90 ED 33 00  B0 66 C7 B7  uX........3..f..
0033ECF0: 1C EE 33 00  01 72 CA B7  06 00 00 00  90 ED 33 00  ..3..r........3.
0033ED00: 00 00 00 00  40 21 DC B7  98 8A 88 76  F4 0F DC B7  ....@!.....v....
0033ED10: 00 00 00 00  40 21 DC B7  90 8A 88 76  C0 6F CE B7  ....@!.....v.o..
0033ED20: 40 21 DC B7  95 00 00 00  F4 0F DC B7  95 00 00 00  @!..............
0033ED30: 38 03 CB 78  00 EE 33 00  7A BC CD B7  98 8A 88 76  8..x..3.z......v
0033ED40: 98 8A 88 76  94 00 00 00  38 03 CB 78  00 00 00 00  ...v....8..x....
0033ED50: 94 00 00 00  00 80 AD FB  98 8A 88 76  FD 8A 88 76  ...........v...v
0033ED60: 98 8A 88 76  98 8A 88 76  2C 8B 88 76  C4 8B 88 76  ...v...v,..v...v
0033ED70: C1 46 CE B7  C4 8B 88 76  00 00 00 00  00 00 00 00  .F.....v........
0033ED80: 00 00 00 00  00 00 00 00  00 00 00 00  E0 1B DC B7  ................
0033ED90: 20 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00   ...............
0033EDA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EDB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EDC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EDD0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EDE0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EDF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EE00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EE10: F4 0F DC B7  F2 30 DA B7  67 BD 07 7E  60 EE 33 00  .....0..g..~`.3.
0033EE20: 6E EB C9 B7  38 07 CB 78  55 4F DA B7  38 07 CB 78  n...8..xUO..8..x
0033EE30: F2 30 DA B7  41 BB 07 7E  91 00 00 00  67 BD 07 7E  .0..A..~....g..~
0033EE40: F2 30 DA B7  66 BB 07 7E  F2 30 DA B7  01 2C B9 BF  .0..f..~.0...,..
0033EE50: 38 07 CB 78  08 00 B0 7B  FF FF FF FF  04 00 00 00  8..x...{........
0033EE60: 90 EE 33 00  BB 8F F0 7D  66 BB 07 7E  41 BB 07 7E  ..3....}f..~A..~
0033EE70: 91 00 00 00  67 BD 07 7E  CC F2 33 00  C8 F2 33 00  ....g..~..3...3.
0033EE80: C4 F2 33 00  08 00 B0 7B  FF FF FF FF  04 00 00 00  ..3....{........
0033EE90: B0 EE 33 00  8D 9D F0 7D  08 00 B0 7B  10 0F 00 00  ..3....}...{....
0033EEA0: 04 00 00 00  A0 BD 12 00  16 00 00 00  08 01 00 00  ................
0033EEB0: E0 EE 33 00  91 2A F2 7D  08 00 B0 7B  18 FB AF 78  ..3..*.}...{...x
0033EEC0: 50 02 B0 78  F8 01 B0 78  DE 0C 70 3F  54 00 70 3F  P..x...x..p?T.p?
0033EED0: 23 FD 6F 3F  B0 F0 33 00  B8 F0 33 00  04 00 00 00  #.o?..3...3.....
0033EEE0: 30 EF 33 00  43 E2 FA 7D  08 00 B0 7B  91 00 00 00  0.3.C..}...{....
0033EEF0: 92 00 00 00  7D 00 00 00  05 00 00 00  58 87 07 7C  ....}.......X..|
0033EF00: 18 FB AF 78  40 F5 AF 78  50 02 B0 78  58 87 07 7C  ...x@..xP..xX..|
0033EF10: B0 F0 33 00  30 29 F2 7D  00 3F 48 3F  33 82 76 BB  ..3.0).}.?H?3.v.
0033EF20: 00 00 80 3F  58 87 07 7C  10 84 BA 76  7D 00 00 00  ...?X..|...v}...
0033EF30: 50 EF 33 00  74 E6 FA 7D  08 00 B0 7B  00 00 00 00  P.3.t..}...{....
0033EF40: 04 00 00 00  30 00 00 00  18 83 07 7C  B0 AF 97 40  ....0......|...@
0033EF50: 20 F1 33 00  EE 87 FA 7D  08 00 B0 7B  B0 F0 33 00   .3....}...{..3.
0033EF60: 04 00 00 00  6C 00 00 00  7D 00 00 00  00 00 00 00  ....l...}.......
0033EF70: 20 F1 33 00  7D 00 00 00  A0 C0 D2 BF  10 99 B5 7B   .3.}..........{
0033EF80: 10 99 B5 7B  39 D9 F5 7D  01 00 00 00  F4 0F DC B7  ...{9..}........
0033EF90: 40 21 DC B7  C8 77 31 76  D0 EF 33 00  00 88 CE B7  @!...w1v..3.....
0033EFA0: 40 21 DC B7  C8 77 31 76  F4 0F DC B7  40 21 DC B7  @!...w1v....@!..
0033EFB0: 41 D5 DC B7  08 00 B0 7B  01 00 00 00  18 83 07 7C  A......{.......|
0033EFC0: 30 B9 FB 7D  93 00 00 00  E0 8F B5 7B  B0 F0 33 00  0..}.......{..3.
0033EFD0: 4C F0 33 00  57 4F F6 7D  04 00 00 00  7D 00 00 00  L.3.WO.}....}...
0033EFE0: 04 00 00 00  00 64 53 77  B8 88 07 7C  AC E8 DC B7  .....dSw...|....
0033EFF0: 10 F0 33 00  FD 95 03 7E  01 00 00 00  00 44 00 00  ..3....~.....D..
0033F000: C2 00 00 00  02 00 00 00  B8 88 07 7C  20 F1 33 00  ...........| .3.
0033F010: 50 F1 33 00  78 CE FB 7D  40 00 0E 7E  00 00 00 00  P.3.x..}@..~....
0033F020: C2 00 00 00  1B 00 00 00  00 20 00 00  40 14 00 00  ......... ..@...
0033F030: D2 00 00 00  CA 00 00 00  C2 00 00 00  B0 34 05 00  .............4..
0033F040: 03 00 00 00  C8 00 00 00  C0 00 00 00  7D 00 00 00  ............}...
0033F050: 75 00 00 00  6C 00 00 00  7D 00 00 00  4C 88 07 7C  u...l...}...L..|
0033F060: 18 83 07 7C  E4 88 07 7C  08 00 B0 7B  00 00 00 00  ...|...|...{....
0033F070: 90 F0 33 00  E5 E2 F0 7D  08 00 B0 7B  08 00 00 00  ..3....}...{....
0033F080: 02 00 00 00  08 00 00 00  08 00 00 00  D0 2F C7 78  ............./.x
0033F090: 70 F1 33 00  04 6B F1 7D  00 20 EA 78  08 00 00 00  p.3..k.}. .x....
0033F0A0: 00 08 00 00  F4 F0 33 00  4B 64 18 40  08 00 B0 7B  ......3.Kd.@...{
0033F0B0: 7D 00 00 00  75 00 00 00  91 00 00 00  92 00 00 00  }...u...........
0033F0C0: 98 F5 AF 78  D8 F2 AF 78  7F E6 6F 3F  C4 F1 6F 3F  ...x...x..o?..o?
0033F0D0: 24 E0 6F 3F  18 8D BA 76  42 02 00 00  08 00 B0 7B  $.o?...vB......{


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x3
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3592

Percent memory used:    34
Total physical memory:  1050669056
Free Memory:            683753472
Page file:              -194134016
Total virtual memory:   2147352575

---

