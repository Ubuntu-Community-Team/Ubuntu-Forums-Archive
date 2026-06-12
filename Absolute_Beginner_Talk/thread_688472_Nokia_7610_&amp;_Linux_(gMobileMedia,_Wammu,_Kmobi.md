---
title: "Nokia 7610 &amp; Linux (gMobileMedia, Wammu, Kmobile Tools &amp; gNokii)"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by msayed2004 on 2008-02-05
Hi everybody;
Beside some games Nokia PC Suit forced me to keep WinXP installed , now I am trying to find a way to get rid of windows for ever. :-D

Currently I am looking for a method to deal with my phone ([COLOR=Sienna]Nokia 7610[/COLOR], by USB cable or BlueTooth), although I can transfer files but what about other tasks like backing up & restoring Contacts, TODOs, Calendar, Bookmarks, .......etc

Using [COLOR=Blue]gMobileMedia[/COLOR] : I can connect it only by the cable (found no help to use the BlueTooth) but I get this message :
[INDENT][COLOR=Red]Your phone model or your phone configuration is not supported at this time.[/COLOR]
[/INDENT]Using [COLOR=Blue]Wammu[/COLOR] : I can connect (also using cable only and it hangs if I tried the BlueTooth :confused: ) and I always get one of the following errors on any attempt to retrieve anything (except info) :
[INDENT][COLOR=Red]Error while communicating with phone

Description: Unknown error.
Function: GetNextMemory
Error code: 27[/COLOR]
[/INDENT]or
[INDENT][COLOR=Red]Error while communicating with phone

Your phone doesn't support this function.[/COLOR]
[/INDENT]Using [COLOR=Blue]KMobile Tools[/COLOR] : I get nothing! [-(

Using [COLOR=Blue]gNokii[/COLOR] : it just hangs forever! ](*,)
---
Searching Google and this forum I get nothing except unanswered topics.

Any help or mentioning another application will be  appreciated. :-D

Thanks.

---

### Post by Presto123 on 2008-02-08
Best I can say is to attempt to run your Nokia Suite through Wine. I have had no success with this issue for my E61, but maybe, JUST MAYBE it will work for you.

Wine is in the Add/Remove application and you can pop your Suite CD in like you were installing to Windoze. I'll keep my fingers crossed for you.

---

### Post by msayed2004 on 2008-02-10
Thanks Presto123 for you reply.

> **Presto123 said:**
> Best I can say is to attempt to run your Nokia Suite through Wine. I have had no success with this issue for my E61, but maybe, JUST MAYBE it will work for you.Negative, it fail to install on wine (Take a look at Wine Application DB).

After providing msvcp60.dll for it, I had this :
```
fixme:win:SetLayeredWindowAttributes (0x2002e,0x00000000,255,2): stub!
fixme:process:IsWow64Process (0xffffffff 0x34f07c) stub!
wine: Call from 0x41cf57 to unimplemented function GDI32.dll.RemoveFontMemResourceEx, aborting
wine: Unimplemented function GDI32.dll.RemoveFontMemResourceEx called at address 0x41cf57 (thread 000e), starting debugger...
Unhandled exception: unimplemented function GDI32.dll.RemoveFontMemResourceEx called in 32-bit code (0x7bc42cfc).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc42cfc ESP:0034e1cc EBP:0034e230 EFLAGS:00000206(   - 00      - -IP1)
 EAX:0045ee30 EBX:7bc8443c ECX:00132c58 EDX:0034e6d4
 ESI:0034e1d8 EDI:0034efac
Stack dump:
0x0034e1cc:  00000000 00000000 00000000 80000100
0x0034e1dc:  00000001 00000000 0041cf57 00000002
0x0034e1ec:  0045ef1c 0045ee30 00000000 00000000
0x0034e1fc:  00000000 00000000 00000000 00c72b1b
0x0034e20c:  7bc8443c 0034e4b8 00000001 7bc721fd
0x0034e21c:  7bc72bf0 7bc721f0 0041c768 00000000
Backtrace:
=>1 0x7bc42cfc stub_entry_point+0x4c(dll=0x45ef1c, name=0x45ee30) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:189] in ntdll (0x0034e230)
  2 0x0041cf57 in nokia_pc_suit (+0x1cf57) (0x00000002)
  3 0x00000000 (0x00000000)
0x7bc42cfc stub_entry_point+0x4c [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:189] in ntdll: subl     $4,%esp
Unable to open file '/build/buildd/wine-0.9.46/dlls/ntdll/loader.c'
Modules:
Module  Address                 Debug info      Name (79 modules)
PE        400000-  4b0000       Export          nokia_pc_suit
PE      780c0000-78121000       Deferred        msvcp60
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Dwarf           ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cbce000-7cc00000       Deferred        uxtheme<elf>
  \-PE  7cbe0000-7cc00000       \               uxtheme
ELF     7cc00000-7cc1d000       Deferred        imm32<elf>
  \-PE  7cc10000-7cc1d000       \               imm32
ELF     7cc1d000-7cc25000       Deferred        libxrender.so.1
ELF     7e078000-7e2c1000       Deferred        i915_dri.so
ELF     7e2c1000-7e2cb000       Deferred        libdrm.so.2
ELF     7e2cb000-7e2d0000       Deferred        libxfixes.so.3
ELF     7e2d0000-7e2d3000       Deferred        libxdamage.so.1
ELF     7e2d3000-7e334000       Deferred        libgl.so.1
ELF     7e334000-7e339000       Deferred        libxdmcp.so.6
ELF     7e339000-7e33c000       Deferred        libxau.so.6
ELF     7e33c000-7e42d000       Deferred        libx11.so.6
ELF     7e42d000-7e43b000       Deferred        libxext.so.6
ELF     7e43b000-7e453000       Deferred        libice.so.6
ELF     7e453000-7e45b000       Deferred        libsm.so.6
ELF     7e45f000-7e468000       Deferred        libxcursor.so.1
ELF     7e468000-7e46e000       Deferred        libxrandr.so.2
ELF     7e46e000-7e4f9000       Deferred        winex11<elf>
  \-PE  7e480000-7e4f9000       \               winex11
ELF     7e5a3000-7e5c3000       Deferred        libexpat.so.1
ELF     7e5c3000-7e5ee000       Deferred        libfontconfig.so.1
ELF     7e5ee000-7e603000       Deferred        libz.so.1
ELF     7e603000-7e673000       Deferred        libfreetype.so.6
ELF     7e673000-7e6db000       Deferred        msvcrt<elf>
  \-PE  7e680000-7e6db000       \               msvcrt
ELF     7e6db000-7e6ef000       Deferred        lz32<elf>
  \-PE  7e6e0000-7e6ef000       \               lz32
ELF     7e6ef000-7e709000       Deferred        version<elf>
  \-PE  7e700000-7e709000       \               version
ELF     7e709000-7e7a7000       Deferred        oleaut32<elf>
  \-PE  7e720000-7e7a7000       \               oleaut32
ELF     7e7a7000-7e7c8000       Deferred        cabinet<elf>
  \-PE  7e7b0000-7e7c8000       \               cabinet
ELF     7e7c8000-7e7e8000       Deferred        mpr<elf>
  \-PE  7e7d0000-7e7e8000       \               mpr
ELF     7e7e8000-7e832000       Deferred        wininet<elf>
  \-PE  7e7f0000-7e832000       \               wininet
ELF     7e832000-7e86d000       Deferred        urlmon<elf>
  \-PE  7e840000-7e86d000       \               urlmon
ELF     7e86d000-7e90c000       Deferred        msi<elf>
  \-PE  7e880000-7e90c000       \               msi
ELF     7e90c000-7e91f000       Deferred        libresolv.so.2
ELF     7e91f000-7e924000       Deferred        libxxf86vm.so.1
ELF     7e932000-7e950000       Deferred        iphlpapi<elf>
  \-PE  7e940000-7e950000       \               iphlpapi
ELF     7e950000-7e9a9000       Deferred        rpcrt4<elf>
  \-PE  7e960000-7e9a9000       \               rpcrt4
ELF     7e9a9000-7ea4a000       Deferred        ole32<elf>
  \-PE  7e9c0000-7ea4a000       \               ole32
ELF     7ea4a000-7eb08000       Deferred        comctl32<elf>
  \-PE  7ea50000-7eb08000       \               comctl32
ELF     7eb08000-7eb61000       Deferred        shlwapi<elf>
  \-PE  7eb20000-7eb61000       \               shlwapi
ELF     7eb61000-7ec64000       Deferred        shell32<elf>
  \-PE  7eb70000-7ec64000       \               shell32
ELF     7ec64000-7ecad000       Deferred        advapi32<elf>
  \-PE  7ec70000-7ecad000       \               advapi32
ELF     7ecad000-7ed48000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed48000       \               gdi32
ELF     7ed48000-7ee86000       Deferred        user32<elf>
  \-PE  7ed60000-7ee86000       \               user32
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efed000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d12000-b7d1b000       Deferred        libnss_compat.so.2
ELF     b7d1c000-b7d20000       Deferred        libdl.so.2
ELF     b7d20000-b7e6a000       Deferred        libc.so.6
ELF     b7e6b000-b7e83000       Deferred        libpthread.so.0
ELF     b7e96000-b7faa000       Deferred        libwine.so.1
ELF     b7fac000-b7fc8000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f 
        00000011    0
        00000010    0
0000000d (D) H:\Desktop\NOKIA_PC_Suit.exe
        00000014    0
        00000013    0
        00000012    0
        0000000e    0 <==
wine: Call from 0x41cf57 to unimplemented function GDI32.dll.RemoveFontMemResourceEx, aborting
wine: Call from 0x41cf57 to unimplemented function GDI32.dll.RemoveFontMemResourceEx, aborting
```Then I have to kill it because it hang :confused:

---

### Post by Kivech on 2008-02-27
I have the same problem with my Nokia N73 in Wammu: same error message as well.

Although it is listed twice as being supported by Wammu, I don't get beyond connecting to my phone.

I'd be very interested as well in any potential solutions.

Kivech

---

### Post by mgrajeshvkm on 2008-05-10
hi,

I have tha same problem with wine.....it hang my computer..Any one plz Help US.

---

### Post by wevsler on 2008-05-10
Hey I never tried this myself but most Nokia phones support the SyncML protocol. So using something like OpenSync should allow you to get contacts and calendar from the phone to the PC.
[http://www.opensync.org/](http://www.opensync.org/) 

good luck

---

### Post by hihihi on 2008-05-17
i had some problems on how to understand how to connenct my mobile phone via bluetooth to wammu, but i got it to work and i just got all my contacts and sms on my laptop.
iupiiieee

now first of all:
if u want to browse your mobile phone and u use gnome, than it is very easy to do that without gmobilemedia:

u have to install various libs and applets:
	$ sudo apt-get install bluetooth gnome-bluetooth
and the obex libs, too &#8594; synaptic-manager
(obexpushd, etc..)

than u should do 
$ sudo hciconfig hci0 reset
this makes my internal bluetooth device be recognized by my system.
than 
$ bluetooth-applet
and on sys-tray a icon appears on which u click with the right mouse,
u get a drop-down-menu where u can browse device...

this is not meant as a how to, there are tons of them on the net,
but i hope i could point u to some good direction.
there are some things to configure by hand before all gets automated but after that its just amazing...

 good luck there...

---

### Post by MDMatrakas on 2008-05-21
> **mgrajeshvkm said:**
> hi,

I have tha same problem with wine.....it hang my computer..Any one plz Help US.

Hi,

I was triing other softwares on Wine, and found out that it do not support USB conections, so PCSuit will not work on it.

---

