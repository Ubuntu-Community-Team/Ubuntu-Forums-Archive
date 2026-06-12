---
title: "warcraft wont start"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by yimmmy on 2008-02-16
ok i just installed WoW fine and i ran it the first time it was very glitchy so i shut it down and it asked me to update so i did and now when i try to run it its an instant crash when i run threw the terminal the errors... are  ```
   james@james-desktop:~$ wine "C:\Program Files\World of Warcraft\Launcher.exe"
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7d4f583 (thread 0012), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7d4f583).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7d4f583 ESP:0034ed8c EBP:0034eda8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:b7e24ff4 ECX:00000000 EDX:00000000
 ESI:00000033 EDI:00000000
Stack dump:
0x0034ed8c:  b7d4f2c5 00000000 0000008a 0000008a
0x0034ed9c:  7ea62588 00000033 7ea693cc 0034ee38
0x0034edac:  7ea2854c 00000000 0000008a 7c228350
0x0034edbc:  00000001 00000000 00000001 bf800048
0x0034edcc:  081573f7 08dfd210 7c228350 7c01f318
0x0034eddc:  0000008a 00000000 7c042728 0034ef38
Backtrace:
=>1 0xb7d4f583 strlen+0x33() in libc.so.6 (0x0034eda8)
  2 0x7ea2854c in winex11 (+0x3854c) (0x0034ee38)
  3 0x7ea2b296 X11DRV_setup_opengl_visual+0x3c() in winex11 (0x0034ef38)
  4 0x7ea3dd64 in winex11 (+0x4dd64) (0x0034f118)
  5 0x7ea4e9b4 in winex11 (+0x5e9b4) (0x0034f138)
  6 0x7bc4264d call_dll_entry_point+0x15() in ntdll (0x0034f158)
  7 0x7bc44b0a in ntdll (+0x34b0a) (0x0034f1e8)
  8 0x7bc44da4 in ntdll (+0x34da4) (0x0034f228)
  9 0x7bc47433 LdrLoadDll+0x67() in ntdll (0x0034f248)
  10 0x7b861f6a in kernel32 (+0x41f6a) (0x0034f4b8)
  11 0x7b862243 LoadLibraryExW+0x43() in kernel32 (0x0034f4d8)
  12 0x7b862322 LoadLibraryExA+0x43() in kernel32 (0x0034f4f8)
  13 0x7b862359 LoadLibraryA+0x2d() in kernel32 (0x0034f518)
  14 0x7ebe9439 in gdi32 (+0x29439) (0x0034f6a8)
  15 0x7ebe3164 CreateDCW+0x60() in gdi32 (0x0034f958)
  16 0x7ec90c25 CreateIconFromResourceEx+0x6c1() in user32 (0x0034fa28)
  17 0x7ec911e4 in user32 (+0x311e4) (0x0034fa98)
  18 0x7ec93b5a LoadImageW+0x45f() in user32 (0x0034fb38)
  19 0x7ec94348 LoadImageA+0x1c0() in user32 (0x0034fc38)
  20 0x7ec944fa LoadCursorA+0x55() in user32 (0x0034fc68)
  21 0x7ec8868e in user32 (+0x2868e) (0x0034fc98)
  22 0x7ec886e1 in user32 (+0x286e1) (0x0034fcb8)
  23 0x7ecfda96 in user32 (+0x9da96) (0x0034fd68)
  24 0x7ed11c74 in user32 (+0xb1c74) (0x0034fd88)
  25 0x7bc4264d call_dll_entry_point+0x15() in ntdll (0x0034fda8)
  26 0x7bc44b0a in ntdll (+0x34b0a) (0x0034fe38)
  27 0x7bc44da4 in ntdll (+0x34da4) (0x0034fe78)
  28 0x7bc44e29 in ntdll (+0x34e29) (0x0034feb8)
  29 0x7bc4772f LdrInitializeThunk+0x27a() in ntdll (0x0034ff08)
  30 0x7b86e6a2 in kernel32 (+0x4e6a2) (0x0034ffe8)
  31 0xb7e571cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xb7d4f583 strlen+0x33 in libc.so.6: movl       0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (45 modules)
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Export          ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d7ef000-7d7f8000       Deferred        librt.so.1
ELF     7d7f8000-7e81c000       Deferred        fglrx_dri.so
ELF     7e81c000-7e827000       Deferred        libgcc_s.so.1
ELF     7e827000-7e8a1000       Deferred        libgl.so.1
ELF     7e8a1000-7e8a6000       Deferred        libxdmcp.so.6
ELF     7e8a6000-7e8a9000       Deferred        libxau.so.6
ELF     7e8a9000-7e99a000       Deferred        libx11.so.6
ELF     7e99a000-7e9a8000       Deferred        libxext.so.6
ELF     7e9a8000-7e9ad000       Deferred        libxxf86vm.so.1
ELF     7e9ad000-7e9c5000       Deferred        libice.so.6
ELF     7e9c5000-7e9cd000       Deferred        libsm.so.6
ELF     7e9db000-7ea6a000       Export          winex11<elf>
  \-PE  7e9f0000-7ea6a000       \               winex11
ELF     7ead7000-7eaf7000       Deferred        libexpat.so.1
ELF     7eaf7000-7eb22000       Deferred        libfontconfig.so.1
ELF     7eb30000-7eb45000       Deferred        libz.so.1
ELF     7eb45000-7ebb5000       Deferred        libfreetype.so.6
ELF     7ebb5000-7ec4c000       Export          gdi32<elf>
  \-PE  7ebc0000-7ec4c000       \               gdi32
ELF     7ec4c000-7ed83000       Export          user32<elf>
  \-PE  7ec60000-7ed83000       \               user32
ELF     7ed83000-7edcd000       Deferred        advapi32<elf>
  \-PE  7ed90000-7edcd000       \               advapi32
ELF     7edcd000-7ede0000       Deferred        libresolv.so.2
ELF     7ede0000-7edfe000       Deferred        iphlpapi<elf>
  \-PE  7edf0000-7edfe000       \               iphlpapi
ELF     7edfe000-7ee5c000       Deferred        rpcrt4<elf>
  \-PE  7ee10000-7ee5c000       \               rpcrt4
ELF     7ee5c000-7ee74000       Deferred        explorer<elf>
  \-PE  7ee60000-7ee74000       \               explorer
ELF     7ee74000-7ee7f000       Deferred        libnss_files.so.2
ELF     7ee7f000-7ee97000       Deferred        libnsl.so.1
ELF     7ee97000-7eea0000       Deferred        libnss_compat.so.2
ELF     7efcd000-7eff2000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cdb000-b7cdf000       Deferred        libdl.so.2
ELF     b7cdf000-b7e29000       Export          libc.so.6
ELF     b7e2a000-b7e42000       Deferred        libpthread.so.0
ELF     b7e50000-b7f64000       Export          libwine.so.1
ELF     b7f66000-b7f82000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
        00000010    0
        00000009    0
0000000a 
        0000000b    0
00000011 (D) c:\windows\system32\explorer.exe
        00000012    0 <==
Backtrace:
=>1 0xb7d4f583 strlen+0x33() in libc.so.6 (0x0034eda8)
  2 0x7ea2854c in winex11 (+0x3854c) (0x0034ee38)
  3 0x7ea2b296 X11DRV_setup_opengl_visual+0x3c() in winex11 (0x0034ef38)
  4 0x7ea3dd64 in winex11 (+0x4dd64) (0x0034f118)
  5 0x7ea4e9b4 in winex11 (+0x5e9b4) (0x0034f138)
  6 0x7bc4264d call_dll_entry_point+0x15() in ntdll (0x0034f158)
  7 0x7bc44b0a in ntdll (+0x34b0a) (0x0034f1e8)
  8 0x7bc44da4 in ntdll (+0x34da4) (0x0034f228)
  9 0x7bc47433 LdrLoadDll+0x67() in ntdll (0x0034f248)
  10 0x7b861f6a in kernel32 (+0x41f6a) (0x0034f4b8)
  11 0x7b862243 LoadLibraryExW+0x43() in kernel32 (0x0034f4d8)
  12 0x7b862322 LoadLibraryExA+0x43() in kernel32 (0x0034f4f8)
  13 0x7b862359 LoadLibraryA+0x2d() in kernel32 (0x0034f518)
  14 0x7ebe9439 in gdi32 (+0x29439) (0x0034f6a8)
  15 0x7ebe3164 CreateDCW+0x60() in gdi32 (0x0034f958)
  16 0x7ec90c25 CreateIconFromResourceEx+0x6c1() in user32 (0x0034fa28)
  17 0x7ec911e4 in user32 (+0x311e4) (0x0034fa98)
  18 0x7ec93b5a LoadImageW+0x45f() in user32 (0x0034fb38)
  19 0x7ec94348 LoadImageA+0x1c0() in user32 (0x0034fc38)
  20 0x7ec944fa LoadCursorA+0x55() in user32 (0x0034fc68)
  21 0x7ec8868e in user32 (+0x2868e) (0x0034fc98)
  22 0x7ec886e1 in user32 (+0x286e1) (0x0034fcb8)
  23 0x7ecfda96 in user32 (+0x9da96) (0x0034fd68)
  24 0x7ed11c74 in user32 (+0xb1c74) (0x0034fd88)
  25 0x7bc4264d call_dll_entry_point+0x15() in ntdll (0x0034fda8)
  26 0x7bc44b0a in ntdll (+0x34b0a) (0x0034fe38)
  27 0x7bc44da4 in ntdll (+0x34da4) (0x0034fe78)
  28 0x7bc44e29 in ntdll (+0x34e29) (0x0034feb8)
  29 0x7bc4772f LdrInitializeThunk+0x27a() in ntdll (0x0034ff08)
  30 0x7b86e6a2 in kernel32 (+0x4e6a2) (0x0034ffe8)
  31 0xb7e571cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:shdocvw:PersistStreamInit_Load (0x133e80)->(0x34d8f8)
fixme:shdocvw:OleControl_FreezeEvents (0x133e80)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x133e80)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x134458): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x134438): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x134438): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x134438): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x134438): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1347c8): WIN32_FIND_DATA is not yet filled.
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on Brooktree Bt878, disabling mixer
fixme:system:SetProcessDPIAware stub!
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x133f18)->((null) 1 0x34a000 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x133f18)->((null) 25 2 0x34a028 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x133f18)->((null) 26 2 0x34a028 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x133f18)->(0x34a074)
fixme:shdocvw:ClOleCommandTarget_Exec (0x133f18)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34a188 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x134340)->(L"" L"" 0 0x34a104)
fixme:shdocvw:ClOleCommandTarget_Exec (0x133f18)->((null) 29 2 0x34d61c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x133f18)
fixme:shdocvw:ClientSite_GetContainer (0x133f18)->(0x34d460)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x133f18)->(0xb7e8a734)
fixme:shdocvw:ClOleCommandTarget_Exec (0x133f18)->((null) 25 2 0x34d374 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x133f18)->((null) 26 2 0x34d374 (nil))
fixme:iphlpapi:NotifyAddrChange (Handle 0x6ad849c8, overlapped 0x6ad849ac): stub
fixme:shdocvw:ClOleCommandTarget_Exec (0x133f18)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x133f18)->((null) 28 2 0x34d5b0 (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x133e80)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x14b348)->((nil))
fixme:shdocvw:OleObject_Close (0x133e80)->(1)
fixme:shell:DllCanUnloadNow stub
james@james-desktop:~$ 
  
```

---

### Post by JoshuaRL on 2008-02-16
Try completely uninstalling both WOW and Wine.  With Wine either use Synaptic or apt-get remove.  Then reinstall carefully, making sure you use whatever directions are on appdb.winehq.org

It wasn't WOW, but I had a Wine problem that was fixed that way.

I would also suggest getting the latest from Wine directly, by doing:

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```
followed by:
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list

```
And then to install:
```

sudo apt-get update
sudo apt-get install wine

```

---

### Post by yimmmy on 2008-02-16
alright im doing that as i type can you direct me to a tut that i can use to install WoW .

---

### Post by JoshuaRL on 2008-02-16
Sure:

[http://appdb.winehq.org/search_results.php?cx=013271970634691685804%3Abc-56dvxydi&cof=FORID%3A11&q=wow#977](http://appdb.winehq.org/search_results.php?cx=013271970634691685804%3Abc-56dvxydi&cof=FORID%3A11&q=wow#977)

Just look in that page for your version.

---

### Post by Faud on 2008-02-16
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

---

