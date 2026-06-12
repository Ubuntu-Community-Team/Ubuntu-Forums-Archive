---
title: "Wine problems installing?"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by teamalpha on 2007-12-25
So, I enter wine setup.exe into terminal, and this is what i get
nitarshan@nitarshan-laptop:~/Desktop$ wine setup.exe
wine: Unhandled page fault on read access to 0x000000fc at address 0x41e48b (thread 0015), starting debugger...
Unhandled exception: page fault on read access to 0x000000fc in 32-bit code (0x0041e48b).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0041e48b ESP:0034e494 EBP:0034e4a0 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00582218 ECX:00000000 EDX:00000000
 ESI:00000000 EDI:0034e4c0
Stack dump:
0x0034e494:  0044c590 00001400 00582218 0034e4b4
0x0034e4a4:  004081af 00582218 00001400 0034e4c0
0x0034e4b4:  0034e4fc 00408037 00582218 00000000
0x0034e4c4:  0044c590 0034f608 00000000 004465c8
0x0034e4d4:  0000003c 00446558 00582180 00000081
0x0034e4e4:  00446564 0014344c 0044655c 00000002
Backtrace:
=>1 0x0041e48b in setup (+0x1e48b) (0x0034e4a0)
  2 0x004081af in setup (+0x81af) (0x0034e4b4)
  3 0x00408037 in setup (+0x8037) (0x0034e4fc)
  4 0x004064f3 in setup (+0x64f3) (0x0034e5c0)
  5 0x0040c383 in setup (+0xc383) (0x0034fe7c)
  6 0x00422b09 in setup (+0x22b09) (0x0034ff08)
  7 0x7b8759fe in kernel32 (+0x559fe) (0x0034ffe8)
  8 0xb7e178f7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0041e48b: cmpl        %eax,0xfc(%esi)
Modules:
Module  Address                 Debug info      Name (71 modules)
PE        400000-  470000       Export          setup
ELF     7b800000-7b92b000       Export          kernel32<elf>
  \-PE  7b820000-7b92b000       \               kernel32
ELF     7bc00000-7bca3000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca3000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c318000-7c353000       Deferred        rsaenh<elf>
  \-PE  7c320000-7c353000       \               rsaenh
ELF     7c353000-7c3b8000       Deferred        crypt32<elf>
  \-PE  7c360000-7c3b8000       \               crypt32
ELF     7c405000-7c437000       Deferred        uxtheme<elf>
  \-PE  7c410000-7c437000       \               uxtheme
ELF     7c437000-7c440000       Deferred        libxcursor.so.1
ELF     7c440000-7c45e000       Deferred        imm32<elf>
  \-PE  7c450000-7c45e000       \               imm32
ELF     7c45e000-7c461000       Deferred        libxcomposite.so.1
ELF     7c461000-7c467000       Deferred        libxrandr.so.2
ELF     7e271000-7e4ba000       Deferred        i915_dri.so
ELF     7e4ba000-7e4c4000       Deferred        libdrm.so.2
ELF     7e4c4000-7e4c9000       Deferred        libxfixes.so.3
ELF     7e4c9000-7e4cc000       Deferred        libxdamage.so.1
ELF     7e4cc000-7e52d000       Deferred        libgl.so.1
ELF     7e52d000-7e532000       Deferred        libxdmcp.so.6
ELF     7e532000-7e535000       Deferred        libxau.so.6
ELF     7e535000-7e626000       Deferred        libx11.so.6
ELF     7e626000-7e634000       Deferred        libxext.so.6
ELF     7e634000-7e639000       Deferred        libxxf86vm.so.1
ELF     7e639000-7e651000       Deferred        libice.so.6
ELF     7e651000-7e659000       Deferred        libsm.so.6
ELF     7e659000-7e661000       Deferred        libxrender.so.1
ELF     7e663000-7e6f0000       Deferred        winex11<elf>
  \-PE  7e670000-7e6f0000       \               winex11
ELF     7e776000-7e796000       Deferred        libexpat.so.1
ELF     7e796000-7e7c1000       Deferred        libfontconfig.so.1
ELF     7e7c1000-7e7d6000       Deferred        libz.so.1
ELF     7e7d6000-7e846000       Deferred        libfreetype.so.6
ELF     7e846000-7e8e7000       Deferred        oleaut32<elf>
  \-PE  7e860000-7e8e7000       \               oleaut32
ELF     7e8e7000-7e8fa000       Deferred        libresolv.so.2
ELF     7e904000-7e922000       Deferred        iphlpapi<elf>
  \-PE  7e910000-7e922000       \               iphlpapi
ELF     7e922000-7e97e000       Deferred        rpcrt4<elf>
  \-PE  7e930000-7e97e000       \               rpcrt4
ELF     7e97e000-7ea21000       Deferred        ole32<elf>
  \-PE  7e990000-7ea21000       \               ole32
ELF     7ea21000-7ea7a000       Deferred        shlwapi<elf>
  \-PE  7ea30000-7ea7a000       \               shlwapi
ELF     7ea7a000-7eb7f000       Deferred        shell32<elf>
  \-PE  7ea90000-7eb7f000       \               shell32
ELF     7eb7f000-7eb93000       Deferred        lz32<elf>
  \-PE  7eb90000-7eb93000       \               lz32
ELF     7eb93000-7ebad000       Deferred        version<elf>
  \-PE  7eba0000-7ebad000       \               version
ELF     7ebad000-7ebf9000       Deferred        advapi32<elf>
  \-PE  7ebc0000-7ebf9000       \               advapi32
ELF     7ebf9000-7ec92000       Deferred        gdi32<elf>
  \-PE  7ec10000-7ec92000       \               gdi32
ELF     7ec92000-7edcf000       Deferred        user32<elf>
  \-PE  7ecb0000-7edcf000       \               user32
ELF     7edcf000-7ee8d000       Deferred        comctl32<elf>
  \-PE  7ede0000-7ee8d000       \               comctl32
ELF     7efae000-7efb9000       Deferred        libnss_files.so.2
ELF     7efb9000-7efd1000       Deferred        libnsl.so.1
ELF     7efd1000-7eff6000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c95000-b7c9e000       Deferred        libnss_compat.so.2
ELF     b7c9f000-b7ca3000       Deferred        libdl.so.2
ELF     b7ca3000-b7ded000       Deferred        libc.so.6
ELF     b7dee000-b7e06000       Deferred        libpthread.so.0
ELF     b7e10000-b7f24000       Export          libwine.so.1
ELF     b7f26000-b7f42000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000014 (D) Z:\home\nitarshan\Desktop\setup.exe
        00000015    0 <==
0000000f 
        00000011    0
        00000010    0
0000000d 
        0000000e    0
Backtrace:
=>1 0x0041e48b in setup (+0x1e48b) (0x0034e4a0)
  2 0x004081af in setup (+0x81af) (0x0034e4b4)
  3 0x00408037 in setup (+0x8037) (0x0034e4fc)
  4 0x004064f3 in setup (+0x64f3) (0x0034e5c0)
  5 0x0040c383 in setup (+0xc383) (0x0034fe7c)
  6 0x00422b09 in setup (+0x22b09) (0x0034ff08)
  7 0x7b8759fe in kernel32 (+0x559fe) (0x0034ffe8)
  8 0xb7e178f7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)


Very Confusing, Any help?

---

### Post by mouseboyx on 2007-12-25
what are you trying to install?

---

### Post by teamalpha on 2007-12-25
Update: tried from the cd, but this time morestuff comes up
But still, the installer opens, but crashes when i get to options on easy install


(P.s. this is world in conflict)

---

### Post by TidusBlade on 2007-12-25
If it's on a CD, I would recommend you drag the CD contents into a folder on the HD and install from there, works better than from a CD.

---

### Post by teamalpha on 2007-12-25
Just a question, but why would that be?

---

### Post by TidusBlade on 2007-12-25
Not sure, I am not so good with Hardware, but I can guess that it might be able to read it better from the HD, and the CD might have minor errors, and I have experienced errors with WINE reading from discs, especially when you have to switch discs.

---

### Post by teamalpha on 2007-12-25
But this is a single disk.

By the way, I have found no good installs so far, will no one help?????

---

### Post by frodon on 2010-10-27
closed as per user request.

---

