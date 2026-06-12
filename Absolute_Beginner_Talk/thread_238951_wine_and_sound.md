---
title: "wine and sound"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by kepos on 2006-08-18
i downloaded latest wine and install it.

but when i try to open CounterStrike it says:

[INDENT]kepos@Assimilator-linux:~/.wine/drive_c/Counter$ wine hl.exe -game cstrike
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7db9da0 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7db9da0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:b7db9da0 ESP:0033f778 EBP:0033f77c EFLAGS:00010202(   - 00      - -RI1)
 EAX:00188858 EBX:7d7cef90 ECX:00188857 EDX:00000000
 ESI:00188858 EDI:8876017c
Stack dump:
0x0033f778:  00188830 0033f9ec 7d765cca 00188858
0x0033f788:  00000000 0033f7ac 7efb6825 00000390
0x0033f798:  0000ffff 0033f7ec 7efb6e1e 7ec06900
0x0033f7a8:  00001030 00110000 00161740 00000000
0x0033f7b8:  00001020 00110038 7eff5288 00110000
0x0033f7c8:  001615d8 0033f7ec 7efb74c8 00161480
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0xb7db9da0 strcpy+0x20 in libc.so.6 (0xb7db9da0)
  2 0x7d765cca IWineD3DImpl_FillGLCaps+0x6e in wined3d (0x7d765cca)
  3 0x7d769a90 in wined3d (+0x39a90) (0x7d769a90)
  4 0x7de7424e in ddraw (+0x2424e) (0x7de7424e)
  5 0x7de74e11 DirectDrawCreate+0xf0 in ddraw (0x7de74e11)
  6 0x01da2a7e in hl (+0x9a2a7e) (0x01da2a7e)
  7 0x01da1c30 in hl (+0x9a1c30) (0x01da1c30)
  8 0x01da0237 in hl (+0x9a0237) (0x01da0237)
  9 0x01da03c0 in hl (+0x9a03c0) (0x01da03c0)
  10 0x01401b0d in hl (+0x1b0d) (0x01401b0d)
  11 0x014038f1 in hl (+0x38f1) (0x014038f1)
  12 0x7eea3a6f in kernel32 (+0x53a6f) (0x7eea3a6f)
  13 0xb7ea6287 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7ea6287)
0xb7db9da0 strcpy+0x20 in libc.so.6: movzbl     0x0(%edx),%eax
Modules:
Module  Address                 Debug info      Name (102 modules)
PE      550000-564000   Deferred        dbg
PE      c70000-cc8000   Deferred        vgui
PE      1400000-3516000 Export          hl
PE      10000000-1001f000       Deferred        filesystem_stdio
PE      20000000-2034f000       Deferred        steam
PE      21100000-2115e000       Deferred        mss32
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d6ae000-7d724000       Deferred        libglu.so.1
ELF     7d724000-7d7d0000       Export          wined3d<elf>
  \-PE  7d730000-7d7d0000       \               wined3d
ELF     7d864000-7d8f6000       Deferred        oleaut32<elf>
  \-PE  7d870000-7d8f6000       \               oleaut32
ELF     7d928000-7d959000       Deferred        uxtheme<elf>
  \-PE  7d930000-7d959000       \               uxtheme
ELF     7d959000-7da1b000       Deferred        comctl32<elf>
  \-PE  7d960000-7da1b000       \               comctl32
ELF     7da1b000-7db01000       Deferred        shell32<elf>
  \-PE  7da30000-7db01000       \               shell32
ELF     7db01000-7db57000       Deferred        shlwapi<elf>
  \-PE  7db10000-7db57000       \               shlwapi
ELF     7db57000-7db6b000       Deferred        mswsock<elf>
  \-PE  7db60000-7db6b000       \               mswsock
ELF     7db6b000-7db7f000       Deferred        lz32<elf>
  \-PE  7db70000-7db7f000       \               lz32
ELF     7db7f000-7db98000       Deferred        version<elf>
  \-PE  7db90000-7db98000       \               version
ELF     7db98000-7dbad000       Deferred        midimap<elf>
  \-PE  7dba0000-7dbad000       \               midimap
ELF     7dbd3000-7dbeb000       Deferred        msacm32<elf>
  \-PE  7dbe0000-7dbeb000       \               msacm32
ELF     7dbeb000-7dc39000       Deferred        libxt.so.6
ELF     7dc39000-7dc4d000       Deferred        libaudio.so.2
ELF     7dc4d000-7dc64000       Deferred        winenas<elf>
  \-PE  7dc50000-7dc64000       \               winenas
ELF     7dc64000-7dc84000       Deferred        libaudiofile.so.0
ELF     7dc84000-7dc8e000       Deferred        libesd.so.0
ELF     7dc8e000-7dca8000       Deferred        wineesd<elf>
  \-PE  7dc90000-7dca8000       \               wineesd
ELF     7dca8000-7dd5d000       Deferred        libasound.so.2
ELF     7dd5d000-7dd86000       Deferred        winealsa<elf>
  \-PE  7dd70000-7dd86000       \               winealsa
ELF     7dd86000-7ddc2000       Deferred        wineoss<elf>
  \-PE  7dd90000-7ddc2000       \               wineoss
ELF     7ddc2000-7de4a000       Deferred        winmm<elf>
  \-PE  7ddd0000-7de4a000       \               winmm
ELF     7de4a000-7de94000       Export          ddraw<elf>
  \-PE  7de50000-7de94000       \               ddraw
ELF     7de94000-7dee3000       Deferred        rpcrt4<elf>
  \-PE  7dea0000-7dee3000       \               rpcrt4
ELF     7dee3000-7df73000       Deferred        ole32<elf>
  \-PE  7def0000-7df73000       \               ole32
ELF     7df73000-7dfae000       Deferred        dinput<elf>
  \-PE  7df80000-7dfae000       \               dinput
ELF     7dfb0000-7dfb4000       Deferred        libxfixes.so.3
ELF     7dfb4000-7dfbd000       Deferred        libxcursor.so.1
ELF     7dfbd000-7dfd9000       Deferred        imm32<elf>
  \-PE  7dfc0000-7dfd9000       \               imm32
ELF     7dfd9000-7dfdc000       Deferred        libxrandr.so.2
ELF     7dfdc000-7dfe4000       Deferred        libxrender.so.1
ELF     7dfe6000-7e7a8000       Deferred        libglcore.so.1
ELF     7e7a8000-7e82d000       Deferred        libgl.so.1
ELF     7e82d000-7e830000       Deferred        libxau.so.6
ELF     7e830000-7e916000       Deferred        libx11.so.6
ELF     7e916000-7e923000       Deferred        libxext.so.6
ELF     7e923000-7e93b000       Deferred        libice.so.6
ELF     7e93b000-7e9bc000       Deferred        winex11<elf>
  \-PE  7e950000-7e9bc000       \               winex11
ELF     7e9bc000-7e9db000       Deferred        libexpat.so.1
ELF     7e9db000-7ea09000       Deferred        libfontconfig.so.1
ELF     7ea09000-7ea1d000       Deferred        libz.so.1
ELF     7ea1d000-7ea86000       Deferred        libfreetype.so.6
ELF     7ea86000-7ea90000       Deferred        libgcc_s.so.1
ELF     7eb65000-7ec17000       Deferred        gdi32<elf>
  \-PE  7eb80000-7ec17000       \               gdi32
ELF     7ec17000-7ed4a000       Deferred        user32<elf>
  \-PE  7ec30000-7ed4a000       \               user32
ELF     7ed4a000-7ed8e000       Deferred        advapi32<elf>
  \-PE  7ed60000-7ed8e000       \               advapi32
ELF     7ed8e000-7eda1000       Deferred        libresolv.so.2
ELF     7eda1000-7edc0000       Deferred        iphlpapi<elf>
  \-PE  7edb0000-7edc0000       \               iphlpapi
ELF     7edc0000-7edea000       Deferred        ws2_32<elf>
  \-PE  7edd0000-7edea000       \               ws2_32
ELF     7edea000-7ee04000       Deferred        wsock32<elf>
  \-PE  7edf0000-7ee04000       \               wsock32
ELF     7ee37000-7ef38000       Export          kernel32<elf>
  \-PE  7ee50000-7ef38000       \               kernel32
ELF     7ef38000-7ef42000       Deferred        libnss_files.so.2
ELF     7ef42000-7ef4b000       Deferred        libnss_nis.so.2
ELF     7ef4b000-7ef60000       Deferred        libnsl.so.1
ELF     7ef60000-7ef82000       Deferred        libm.so.6
ELF     7ef82000-7f000000       Deferred        ntdll<elf>
  \-PE  7ef90000-7f000000       \               ntdll
ELF     b7d40000-b7d42000       Deferred        libnvidia-tls.so.1
ELF     b7d42000-b7d4b000       Deferred        libnss_compat.so.2
ELF     b7d4d000-b7d50000       Deferred        libdl.so.2
ELF     b7d50000-b7e7f000       Export          libc.so.6
ELF     b7e7f000-b7e91000       Deferred        libpthread.so.0
ELF     b7e92000-b7e97000       Deferred        libxxf86vm.so.1
ELF     b7e97000-b7e9f000       Deferred        libsm.so.6
ELF     b7e9f000-b7faf000       Export          libwine.so.1
ELF     b7fb2000-b7fc8000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000b    0
00000008 (D) C:\Counter\hl.exe
        00000009    0 <==
[/INDENT]


any idea how to solve this?

---

