---
title: "How to get wine working?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by mcvos on 2006-07-30
I can't seem to get wine working. When I select a *.exe in my Windows partition, the right mouse menu shows "open in wine", but that doesn't seem to do anything other than add a sleeping wine-preloader process. I see I've got several running wine-preloader processes too, and I've got 3 wineprefixcreate processes. But nothing is happening.

When I type wine, winecfp or wineprefixcreate at the shell, I get this output, and then nothing, no shell prompt, as if it's waiting for something, but what?
```

mcv@rhovanion:~$ wineprefixcreate
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0x7f4ee4ff (thread 0009), starting debugger...
WineDbg starting on pid 0x8
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image C:\windows\rundll32.exe
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7f4ee4ff).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7f4ee4ff ESP:7fb8fc0c EBP:7fb8fc48 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c120a60 ECX:b7f6e320 EDX:7c069ef8
 ESI:7c069ef8 EDI:7c069ef8
Stack dump:
0x7fb8fc0c:  7c069ef8 7f5238e0 7c069ef8 7f4ecd56
0x7fb8fc1c:  7c069ef8 7c069ef8 7f617760 7c120a78
0x7fb8fc2c:  7f54c3f3 7c069ef8 7c120a7c 00000001
0x7fb8fc3c:  7f6bc60c 7f6c3a34 00000000 7fb8fc68
0x7fb8fc4c:  7f682ee8 7c069ef8 7f6bc60c 7fb8fc68
0x7fb8fc5c:  7f6bc60c 7f6bc60c 00000001 7fb8fdb8
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7f4ee4ff in libgl.so.1 (+0x304ff) (0x7f4ee4ff)
  2 0x7f682ee8 X11DRV_GDI_Finalize+0x28 in winex11 (0x7f682ee8)
  3 0x7f69af1a DllMain+0x41 in winex11 (0x7f69af1a)
  4 0x7f6ab442 in winex11 (+0x5b442) (0x7f6ab442)
  5 0x7ff9c0e5 call_dll_entry_point+0x15 in ntdll (0x7ff9c0e5)
  6 0x7ff9cea7 in ntdll (+0x1cea7) (0x7ff9cea7)
  7 0x7ff9d16f in ntdll (+0x1d16f) (0x7ff9d16f)
  8 0x7fc59c1c ExitProcess+0x1b in kernel32 (0x7fc59c1c)
  9 0x7fbade2f in rundll32 (+0xde2f) (0x7fbade2f)
  10 0x7fc5b311 in kernel32 (+0x4b311) (0x7fc5b311)
  11 0xb7f92ddb wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f92ddb)
0x7f4ee4ff: movl        0x0(%eax),%eax
Modules:
Module  Address                 Debug info      Name (91 modules)
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e2d7000-7e2f0000     Deferred        advpack<elf>
  \-PE  0x7e2e0000-7e2f0000     \               advpack
ELF     0x7e438000-7e493000     Deferred        shlwapi<elf>
  \-PE  0x7e450000-7e493000     \               shlwapi
ELF     0x7e493000-7e55f000     Deferred        shell32<elf>
  \-PE  0x7e4b0000-7e55f000     \               shell32
ELF     0x7e55f000-7e590000     Deferred        uxtheme<elf>
  \-PE  0x7e570000-7e590000     \               uxtheme
ELF     0x7e590000-7e650000     Deferred        comctl32<elf>
  \-PE  0x7e5a0000-7e650000     \               comctl32
ELF     0x7e650000-7e6a2000     Deferred        dsound<elf>
  \-PE  0x7e660000-7e6a2000     \               dsound
ELF     0x7e6a2000-7e700000     Deferred        quartz<elf>
  \-PE  0x7e6c0000-7e700000     \               quartz
ELF     0x7e81a000-7e82f000     Deferred        midimap<elf>
  \-PE  0x7e820000-7e82f000     \               midimap
ELF     0x7e82f000-7e847000     Deferred        msacm<elf>
  \-PE  0x7e840000-7e847000     \               msacm
ELF     0x7e847000-7e88b000     Deferred        wineoss<elf>
  \-PE  0x7e860000-7e88b000     \               wineoss
ELF     0x7e8b5000-7e8db000     Deferred        msvfw32<elf>
  \-PE  0x7e8c0000-7e8db000     \               msvfw32
ELF     0x7e8db000-7e971000     Deferred        oleaut32<elf>
  \-PE  0x7e8f0000-7e971000     \               oleaut32
ELF     0x7e971000-7ea02000     Deferred        ole32<elf>
  \-PE  0x7e990000-7ea02000     \               ole32
ELF     0x7ea02000-7ea8a000     Deferred        winmm<elf>
  \-PE  0x7ea10000-7ea8a000     \               winmm
ELF     0x7ea8a000-7eab0000     Deferred        msacm32<elf>
  \-PE  0x7ea90000-7eab0000     \               msacm32
ELF     0x7ebc5000-7ebd9000     Deferred        avicap32<elf>
  \-PE  0x7ebd0000-7ebd9000     \               avicap32
ELF     0x7ebd9000-7ec00000     Deferred        devenum<elf>
  \-PE  0x7ebf0000-7ec00000     \               devenum
ELF     0x7ec00000-7ec1f000     Deferred        iphlpapi<elf>
  \-PE  0x7ec10000-7ec1f000     \               iphlpapi
ELF     0x7ec1f000-7ec68000     Deferred        rpcrt4<elf>
  \-PE  0x7ec30000-7ec68000     \               rpcrt4
ELF     0x7ec68000-7ec7c000     Deferred        lz32<elf>
  \-PE  0x7ec70000-7ec7c000     \               lz32
ELF     0x7ec7c000-7ec95000     Deferred        version<elf>
  \-PE  0x7ec80000-7ec95000     \               version
ELF     0x7ec95000-7ecea000     Deferred        setupapi<elf>
  \-PE  0x7eca0000-7ecea000     \               setupapi
ELF     0x7ed44000-7ed48000     Deferred        libxfixes.so.3
ELF     0x7ed48000-7ed51000     Deferred        libxcursor.so.1
ELF     0x7ed51000-7ed6d000     Deferred        imm32<elf>
  \-PE  0x7ed60000-7ed6d000     \               imm32
ELF     0x7ed6d000-7f4be000     Deferred        libglcore.so.1
ELF     0x7f4be000-7f536000     Export          libgl.so.1
ELF     0x7f536000-7f61c000     Deferred        libx11.so.6
ELF     0x7f61c000-7f629000     Deferred        libxext.so.6
ELF     0x7f629000-7f641000     Deferred        libice.so.6
ELF     0x7f641000-7f6c4000     Export          winex11<elf>
  \-PE  0x7f650000-7f6c4000     \               winex11
ELF     0x7f6c4000-7f6e3000     Deferred        libexpat.so.1
ELF     0x7f6e3000-7f711000     Deferred        libfontconfig.so.1
ELF     0x7f711000-7f725000     Deferred        libz.so.1
ELF     0x7f725000-7f78e000     Deferred        libfreetype.so.6
ELF     0x7f78e000-7f7ce000     Deferred        advapi32<elf>
  \-PE  0x7f7a0000-7f7ce000     \               advapi32
ELF     0x7f8a3000-7f954000     Deferred        gdi32<elf>
  \-PE  0x7f8c0000-7f954000     \               gdi32
ELF     0x7f954000-7fa80000     Deferred        user32<elf>
  \-PE  0x7f970000-7fa80000     \               user32
ELF     0x7fb93000-7fb9b000     Deferred        libxrender.so.1
PE      0x7fb9b000-7fbb0000     Export          rundll32
PE      0x7fba0000-7fbb0000     Export          rundll32
ELF     0x7fbb1000-7fbb6000     Deferred        libxxf86vm.so.1
ELF     0x7fbb6000-7fbbb000     Deferred        libxxf86dga.so.1
ELF     0x7fbee000-7fcf0000     Export          kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe01000-7fe04000     Deferred        libxrandr.so.2
ELF     0x7fe04000-7fe0e000     Deferred        libgcc_s.so.1
ELF     0x7fe0e000-7fe18000     Deferred        libnss_files.so.2
ELF     0x7fe18000-7fe21000     Deferred        libnss_nis.so.2
ELF     0x7fe21000-7fe36000     Deferred        libnsl.so.1
ELF     0x7fe36000-7fe3f000     Deferred        libnss_compat.so.2
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4c000-7fe4e000     Deferred        libnvidia-tls.so.1
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Export          ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e3f000-b7e42000     Deferred        libdl.so.2
ELF     0xb7e42000-b7f71000     Deferred        libc.so.6
ELF     0xb7f71000-b7f83000     Deferred        libpthread.so.0
ELF     0xb7f83000-b7f86000     Deferred        libxau.so.6
ELF     0xb7f8e000-b7fa8000     Export          libwine.so.1
ELF     0xb7fab000-b7fc1000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\rundll32.exe
        00000009    0 <==

```

So why isn't it working? What's going wrong? What should I have done instead?


mcv.

---

### Post by abowman on 2006-07-30
What program are you trying to run?
Did you check the [wine appdb]("http://appdb.winehq.org/") to see if others have had any luck with it?
Also, how did you install wine? Through synaptic?

---

### Post by Tomosaur on 2006-07-30
I don't think you're supposed to run things from your actual windows partition. Rather, install them in the virtual C:\ drive that Wine sets up. Reading and writing from an XP partition entails many unforeseen problems, try and avoid it if possible. I'd suggest install a small windows program using wine, then trying to run it and see if you get the same problem.

---

### Post by mcvos on 2006-07-30
I admit I was being a bit ambitious: I've tried to run Morrowind and Europa Universalis. But even then, shouldn't wineprefixcreate at some point finish whatever it's trying to do?

---

### Post by Tomosaur on 2006-07-30
Well for a start, you're going to need to install the correct graphics drivers or you won't get anywhere. I see this in your output:

"Xlib:  extension "GLX" missing on display ":0.0"."

Secondly, since the windows API is closed source - the people running wine have to create their own libraries to get things working. This is why they use a virtual c drive - to stop programs trying to use the windows API (which is what they'll do should you run them from your windows partition).

Aside from that, I'm not sure why wine would be running multiple times. How did you install it? Did you download from synaptic? Or did you get it off their website? If so, did you get a prebuilt package or did you compile from their CVS tree?

---

### Post by mcvos on 2006-07-30
I've already spent ages getting the correct graphics drivers to work. I've got a GeForce4 MX 440 which apparently needs some special treatment, but I did all of that, and I thought everything was working fine. Any idea what could still be wrong?

I installed wine through synaptic, and since I didn't have a .wine directory, I figured I still needed to run winecfg or wineprefixcreate by hand, but it doesn't finish for some reason. I do have a .wine directory now, though. Not sure if it was generated by wineprefixcreate or by the loki installer for Morrowind that I got from [http://liflg.org/?catid=7&gameid=38]("http://liflg.org/?catid=7&gameid=38")

---

