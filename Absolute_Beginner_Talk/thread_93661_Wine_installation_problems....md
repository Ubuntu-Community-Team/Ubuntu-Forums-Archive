---
title: "Wine installation problems..."
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by Todd_Z on 2005-11-22
I'm installing a windows program [for Basic Stamps] and i get the following error:

```

fixme:msi:MsiInstallProductW L"C:\\windows\\temp\\_isfb6\\BASIC Stamp Editor v2.2.msi" (null)
fixme:msi:ACTION_HandleStandardAction UNHANDLED Standard Action L"ValidateProductID"
fixme:msi:ACTION_HandleStandardAction UNHANDLED Standard Action L"IsolateComponents"
fixme:msi:ACTION_HandleStandardAction UNHANDLED Standard Action L"MigrateFeatureStates"
wine: Unhandled exception (thread 000b), starting debugger...
WineDbg starting on pid 0xa
Unhandled exception: page fault on read access to 0x004d0000 in 32-bit code (0x7f9cd28e).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7f9cd28e ESP:7fb0eb8c EBP:7fb0eba8 EFLAGS:00210212(   - 00      - RIA1)
 EAX:7fb0ec30 EBX:7fa09720 ECX:00000134 EDX:004d0000
 ESI:00000000 EDI:004d0002
Stack dump:
0x7fb0eb8c:  7fb0eba8 7f735a8d 00010062 00000000
0x7fb0eb9c:  7fa09720 00000000 004d0000 7fb0ec40
0x7fb0ebac:  7f9d0a49 00010062 7fb0ec20 0000001c
0x7fb0ebbc:  7f9ee242 7bebd476 7fda0000 7fda0000
0x7fb0ebcc:  00000000 7fe16d30 000000f0 7fa09720
0x7fb0ebdc:  7fe1a5b0 00000011 7fb0ec18 7f9f559a
0200: sel=1007 base=b7f53000 limit=00001f97 32-bit rw-
Backtrace:
=>1 0x7f9cd28e in msi (+0x1d28e) (0x7fb0eba8)
  2 0x7f9d0a49 in msi (+0x20a49) (0x7fb0ec40)
  3 0x7f9cd780 in msi (+0x1d780) (0x7fb0ec6c)
  4 0x7f9e2b73 MSI_IterateRecords+0xc1 in msi (0x7fb0ec98)
  5 0x7f9ce669 in msi (+0x1e669) (0x7fb0ed88)
  6 0x7f738727 WINPROC_wrapper+0x17 in user32 (0x7fb0edac)
  7 0x7f739234 in user32 (+0x99234) (0x7fb0ede8)
  8 0x7f73f143 CallWindowProcW+0x487 in user32 (0x7fb0f2a4)
  9 0x7f709787 in user32 (+0x69787) (0x7fb0f2fc)
  10 0x7f70d560 SendMessageTimeoutW+0x180 in user32 (0x7fb0f354)
  11 0x7f70d5ba SendMessageW+0x50 in user32 (0x7fb0f380)
  12 0x7e9828c3 X11DRV_CreateWindow+0x5ce in winex11.drv (0x7fb0f46c)
  13 0x7f733da8 in user32 (+0x93da8) (0x7fb0f5c4)
  14 0x7f7350d8 CreateWindowExW+0x8c in user32 (0x7fb0f81c)
  15 0x7f9cd4c7 msi_dialog_run_message_loop+0xc0 in msi (0x7fb0f864)
  16 0x7f9d1955 in msi (+0x21955) (0x7fb0f88c)
  17 0x7f9d2023 ACTION_DialogBox+0x8e in msi (0x7fb0f8b0)
  18 0x7f9bad2f ACTION_PerformUIAction+0xcf in msi (0x7fb0f8dc)
  19 0x7f9bb146 in msi (+0xb146) (0x7fb0f904)
  20 0x7f9e2b73 MSI_IterateRecords+0xc1 in msi (0x7fb0f930)
  21 0x7f9bf5b8 ACTION_DoTopLevelINSTALL+0x40c in msi (0x7fb0f994)
  22 0x7f9ddb43 MsiInstallProductW+0x10d in msi (0x7fb0fdd8)
  23 0x7fb2bd14 main+0x37a in msiexec (0x7fb0fea0)
  24 0x7fb2b197 in msiexec (+0xb197) (0x7fb0ff20)
  25 0x7fcf8e63 in kernel32 (+0x48e63) (0x7fb0fff4)
  26 0xb7f34c45 wine_switch_to_stack+0x11 in libwine.so.1 (0x00000000)
0x7f9cd28e: cmpw        $123,0x0(%edx)
Modules:
Module  Address                 Debug info      Name (72 modules)
ELF     0x7be87000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e66f000-7e6b1000     Deferred        riched20<elf>
  \-PE  0x7e680000-7e6b1000     \               riched20
ELF     0x7e797000-7e7a0000     Deferred        libxcursor.so.1
ELF     0x7e7ac000-7e7c9000     Deferred        imm32<elf>
  \-PE  0x7e7b0000-7e7c9000     \               imm32
ELF     0x7e7c9000-7e7e5000     Deferred        ximcp.so.2
ELF     0x7e7e5000-7e84b000     Deferred        libgl.so.1
ELF     0x7e84b000-7e90b000     Deferred        libx11.so.6
ELF     0x7e90b000-7e918000     Deferred        libxext.so.6
ELF     0x7e918000-7e931000     Deferred        libice.so.6
ELF     0x7e931000-7e9b3000     Export          winex11.drv<elf>
  \-PE  0x7e940000-7e9b3000     \               winex11.drv
ELF     0x7e9b3000-7e9d2000     Deferred        libexpat.so.1
ELF     0x7e9d2000-7ea00000     Deferred        libfontconfig.so.1
ELF     0x7ea00000-7ea14000     Deferred        libz.so.1
ELF     0x7ea14000-7ea7e000     Deferred        libfreetype.so.6
ELF     0x7ea7e000-7ea92000     Deferred        lz32<elf>
  \-PE  0x7ea80000-7ea92000     \               lz32
ELF     0x7ea92000-7eaad000     Deferred        version<elf>
  \-PE  0x7eaa0000-7eaad000     \               version
ELF     0x7eaad000-7eb42000     Deferred        oleaut32<elf>
  \-PE  0x7ead0000-7eb42000     \               oleaut32
ELF     0x7eb42000-7eb6b000     Deferred        cabinet<elf>
  \-PE  0x7eb50000-7eb6b000     \               cabinet
ELF     0x7eb6b000-7ec2a000     Deferred        comctl32<elf>
  \-PE  0x7eb80000-7ec2a000     \               comctl32
ELF     0x7ec2a000-7ec4b000     Deferred        iphlpapi<elf>
  \-PE  0x7ec30000-7ec4b000     \               iphlpapi
ELF     0x7ec4b000-7ec95000     Deferred        rpcrt4<elf>
  \-PE  0x7ec60000-7ec95000     \               rpcrt4
ELF     0x7ed7b000-7f67e000     Deferred        gdi32<elf>
  \-PE  0x7edc0000-7f67e000     \               gdi32
ELF     0x7f67e000-7f7aa000     Export          user32<elf>
  \-PE  0x7f6a0000-7f7aa000     \               user32
ELF     0x7f7aa000-7f7eb000     Deferred        advapi32<elf>
  \-PE  0x7f7c0000-7f7eb000     \               advapi32
ELF     0x7f7eb000-7f875000     Deferred        ole32<elf>
  \-PE  0x7f800000-7f875000     \               ole32
ELF     0x7f875000-7f8d1000     Deferred        shlwapi<elf>
  \-PE  0x7f890000-7f8d1000     \               shlwapi
ELF     0x7f8d1000-7f997000     Deferred        shell32<elf>
  \-PE  0x7f8f0000-7f997000     \               shell32
ELF     0x7f997000-7fa10000     Export          msi<elf>
  \-PE  0x7f9b0000-7fa10000     \               msi
ELF     0x7fb11000-7fb19000     Deferred        libxrender.so.1
ELF     0x7fb19000-7fb30000     Export          msiexec<elf>
  \-PE  0x7fb20000-7fb30000     \               msiexec
ELF     0x7fb31000-7fb38000     Deferred        libdrm.so.1
ELF     0x7fb38000-7fb3d000     Deferred        libxxf86vm.so.1
ELF     0x7fc85000-7fd90000     Export          kernel32<elf>
  \-PE  0x7fcb0000-7fd90000     \               kernel32
ELF     0x7fd92000-7fd95000     Deferred        libxrandr.so.2
ELF     0x7fd95000-7fd99000     Deferred        libxdmcp.so.6
ELF     0x7fd99000-7fda0000     Deferred        libsm.so.6
ELF     0x7feb1000-7feb4000     Deferred        libxau.so.6
ELF     0x7feb4000-7febf000     Deferred        libgcc_s.so.1
ELF     0x7febf000-7fed4000     Deferred        libnsl.so.1
ELF     0x7fed4000-7fedd000     Deferred        libnss_compat.so.2
ELF     0x7fee3000-7fee7000     Deferred        libxfixes.so.3
ELF     0x7fee7000-7fee9000     Deferred        xlcutf8load.so.2
ELF     0x7fee9000-7ff0b000     Deferred        libm.so.6
ELF     0x7ff0b000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7de1000-b7deb000     Deferred        libnss_files.so.2
ELF     0xb7dec000-b7def000     Deferred        libdl.so.2
ELF     0xb7def000-b7f1d000     Deferred        libc.so.6
ELF     0xb7f1e000-b7f30000     Deferred        libpthread.so.0
ELF     0xb7f30000-b7f49000     Export          libwine.so.1
ELF     0xb7f4a000-b7f53000     Deferred        libnss_nis.so.2
ELF     0xb7f58000-b7f6e000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) C:\windows\system\msiexec.exe
        0000000b    0 <==
00000008
        00000009    0
WineDbg terminated on pid 0xa

```

Any ideas?

---

### Post by nikopol on 2005-11-22
Not sure what's wrong there - it could be that Basic Stamps doesn't work with Wine (which is often the case sadly) - I didn't find it in the supported app db ([http://appdb.winehq.org/](http://appdb.winehq.org/))

Have you tried the linux version BTW?
[http://bstamp.sourceforge.net/](http://bstamp.sourceforge.net/)

---

