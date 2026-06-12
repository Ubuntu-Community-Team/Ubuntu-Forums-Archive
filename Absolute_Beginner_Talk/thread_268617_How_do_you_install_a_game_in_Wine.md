---
title: "How do you install a game in Wine?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by TailsAndy on 2006-09-30
I've been trying to figure this out.

Can anyone help?

---

### Post by Anonii on 2006-09-30
> **TailsAndy said:**
> I've been trying to figure this out.

Can anyone help?
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by TailsAndy on 2006-09-30
What directory would cdrom0 be?

---

### Post by Anonii on 2006-09-30
> **TailsAndy said:**
> What directory would cdrom0 be?
Check your /etc/fstab file. Dont change it, just check it. You will probably understand the formation and the point of this file.
Your cdrom0, should be on /media/cdrom0 or /mnt/cdrom0. But better check /etc/fstab.

---

### Post by TailsAndy on 2006-09-30
Problem is, it stops at "Configuring Windows Installer" and I followed the HOWTO on Wine.

```
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
wine: Unhandled page fault on write access to 0x00000000 at address 0x339a95 (thread 0026), starting debugger...
WineDbg starting on pid 0x25
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x00339a95).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:00339a95 ESP:00339a4c EBP:0000000f EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:00000000 ECX:00110020 EDX:00171478
 ESI:00339b34 EDI:00339a60
Stack dump:
0x00339a4c:  00000073 00339b34 00339b34 00171550
0x00339a5c:  00000000 00339ac4 65f149e9 80002dc0
0x00339a6c:  00339a90 00000001 00170d08 00339abc
0x00339a7c:  00171550 00339b34 00000000 80002c78
0x00339a8c:  80002db0 0000000f 0000000e 00000002
0x00339a9c:  00040005 00000000 0000000e 0000000f
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x00339a95 (0x00339a95)
  2 0x00000000 (0x00000000)
0x00339a95: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (67 modules)
PE      400000-43d000   Deferred        setup
PE      47d70000-47d82000       Deferred        sdbapi
PE      54100000-54107000       Deferred        sage
PE      65f00000-65fc2000       Deferred        ole32
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d969000-7d9cb000       Deferred        msvcrt<elf>
  \-PE  7d980000-7d9cb000       \               msvcrt
ELF     7db39000-7db6b000       Deferred        uxtheme<elf>
  \-PE  7db40000-7db6b000       \               uxtheme
ELF     7db6b000-7db6f000       Deferred        libxfixes.so.3
ELF     7db6f000-7db78000       Deferred        libxcursor.so.1
ELF     7db78000-7db80000       Deferred        libxrender.so.1
ELF     7db80000-7db9c000       Deferred        imm32<elf>
  \-PE  7db90000-7db9c000       \               imm32
ELF     7e2fd000-7e4e7000       Deferred        r300_dri.so
ELF     7e4e7000-7e4ee000       Deferred        libdrm.so.2
ELF     7e4ee000-7e554000       Deferred        libgl.so.1
ELF     7e554000-7e63a000       Deferred        libx11.so.6
ELF     7e63a000-7e647000       Deferred        libxext.so.6
ELF     7e647000-7e65f000       Deferred        libice.so.6
ELF     7e65f000-7e6e9000       Deferred        winex11<elf>
  \-PE  7e670000-7e6e9000       \               winex11
ELF     7e6e9000-7e708000       Deferred        libexpat.so.1
ELF     7e708000-7e736000       Deferred        libfontconfig.so.1
ELF     7e736000-7e74a000       Deferred        libz.so.1
ELF     7e74a000-7e7b3000       Deferred        libfreetype.so.6
ELF     7e7b3000-7e7c6000       Deferred        libresolv.so.2
ELF     7e7c6000-7e7e5000       Deferred        iphlpapi<elf>
  \-PE  7e7d0000-7e7e5000       \               iphlpapi
ELF     7e7e5000-7e835000       Deferred        rpcrt4<elf>
  \-PE  7e7f0000-7e835000       \               rpcrt4
ELF     7e835000-7e8c8000       Deferred        oleaut32<elf>
  \-PE  7e850000-7e8c8000       \               oleaut32
ELF     7e8c8000-7e98a000       Deferred        comctl32<elf>
  \-PE  7e8d0000-7e98a000       \               comctl32
ELF     7e98a000-7eabc000       Deferred        user32<elf>
  \-PE  7e9a0000-7eabc000       \               user32
ELF     7eabc000-7eb00000       Deferred        advapi32<elf>
  \-PE  7ead0000-7eb00000       \               advapi32
ELF     7eb00000-7eb0a000       Deferred        libgcc_s.so.1
ELF     7ebdf000-7ec91000       Deferred        gdi32<elf>
  \-PE  7ebf0000-7ec91000       \               gdi32
ELF     7ec91000-7ece7000       Deferred        shlwapi<elf>
  \-PE  7eca0000-7ece7000       \               shlwapi
ELF     7ece7000-7edcd000       Deferred        shell32<elf>
  \-PE  7ed00000-7edcd000       \               shell32
ELF     7edcd000-7ede1000       Deferred        lz32<elf>
  \-PE  7edd0000-7ede1000       \               lz32
ELF     7ede1000-7edfa000       Deferred        version<elf>
  \-PE  7edf0000-7edfa000       \               version
ELF     7ee2d000-7ef2f000       Deferred        kernel32<elf>
  \-PE  7ee50000-7ef2f000       \               kernel32
ELF     7ef2f000-7ef39000       Deferred        libnss_files.so.2
ELF     7ef39000-7ef42000       Deferred        libnss_nis.so.2
ELF     7ef42000-7ef57000       Deferred        libnsl.so.1
ELF     7ef57000-7ef60000       Deferred        libnss_compat.so.2
ELF     7ef60000-7ef82000       Deferred        libm.so.6
ELF     7ef82000-7f000000       Deferred        ntdll<elf>
  \-PE  7ef90000-7f000000       \               ntdll
ELF     b7cb4000-b7cb7000       Deferred        libxau.so.6
ELF     b7cb9000-b7cbc000       Deferred        libdl.so.2
ELF     b7cbc000-b7deb000       Deferred        libc.so.6
ELF     b7deb000-b7dfd000       Deferred        libpthread.so.0
ELF     b7dfd000-b7e02000       Deferred        libxxf86vm.so.1
ELF     b7e02000-b7e0a000       Deferred        libsm.so.6
ELF     b7e0a000-b7f1b000       Deferred        libwine.so.1
ELF     b7f1e000-b7f34000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000025 (D) D:\setup.exe
        00000028    0
        00000026    0 <==
0000000e
        00000011    0
        00000010    0
        0000000f    0
0000000a
        0000000b    0

```

Appears in the terminal when I start it.

---

### Post by Anonii on 2006-09-30
> **TailsAndy said:**
> Problem is, it stops at "Configuring Windows Installer" and I followed the HOWTO on Wine.

```
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
wine: Unhandled page fault on write access to 0x00000000 at address 0x339a95 (thread 0026), starting debugger...
WineDbg starting on pid 0x25
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x00339a95).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:00339a95 ESP:00339a4c EBP:0000000f EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:00000000 ECX:00110020 EDX:00171478
 ESI:00339b34 EDI:00339a60
Stack dump:
0x00339a4c:  00000073 00339b34 00339b34 00171550
0x00339a5c:  00000000 00339ac4 65f149e9 80002dc0
0x00339a6c:  00339a90 00000001 00170d08 00339abc
0x00339a7c:  00171550 00339b34 00000000 80002c78
0x00339a8c:  80002db0 0000000f 0000000e 00000002
0x00339a9c:  00040005 00000000 0000000e 0000000f
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x00339a95 (0x00339a95)
  2 0x00000000 (0x00000000)
0x00339a95: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (67 modules)
PE      400000-43d000   Deferred        setup
PE      47d70000-47d82000       Deferred        sdbapi
PE      54100000-54107000       Deferred        sage
PE      65f00000-65fc2000       Deferred        ole32
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d969000-7d9cb000       Deferred        msvcrt<elf>
  \-PE  7d980000-7d9cb000       \               msvcrt
ELF     7db39000-7db6b000       Deferred        uxtheme<elf>
  \-PE  7db40000-7db6b000       \               uxtheme
ELF     7db6b000-7db6f000       Deferred        libxfixes.so.3
ELF     7db6f000-7db78000       Deferred        libxcursor.so.1
ELF     7db78000-7db80000       Deferred        libxrender.so.1
ELF     7db80000-7db9c000       Deferred        imm32<elf>
  \-PE  7db90000-7db9c000       \               imm32
ELF     7e2fd000-7e4e7000       Deferred        r300_dri.so
ELF     7e4e7000-7e4ee000       Deferred        libdrm.so.2
ELF     7e4ee000-7e554000       Deferred        libgl.so.1
ELF     7e554000-7e63a000       Deferred        libx11.so.6
ELF     7e63a000-7e647000       Deferred        libxext.so.6
ELF     7e647000-7e65f000       Deferred        libice.so.6
ELF     7e65f000-7e6e9000       Deferred        winex11<elf>
  \-PE  7e670000-7e6e9000       \               winex11
ELF     7e6e9000-7e708000       Deferred        libexpat.so.1
ELF     7e708000-7e736000       Deferred        libfontconfig.so.1
ELF     7e736000-7e74a000       Deferred        libz.so.1
ELF     7e74a000-7e7b3000       Deferred        libfreetype.so.6
ELF     7e7b3000-7e7c6000       Deferred        libresolv.so.2
ELF     7e7c6000-7e7e5000       Deferred        iphlpapi<elf>
  \-PE  7e7d0000-7e7e5000       \               iphlpapi
ELF     7e7e5000-7e835000       Deferred        rpcrt4<elf>
  \-PE  7e7f0000-7e835000       \               rpcrt4
ELF     7e835000-7e8c8000       Deferred        oleaut32<elf>
  \-PE  7e850000-7e8c8000       \               oleaut32
ELF     7e8c8000-7e98a000       Deferred        comctl32<elf>
  \-PE  7e8d0000-7e98a000       \               comctl32
ELF     7e98a000-7eabc000       Deferred        user32<elf>
  \-PE  7e9a0000-7eabc000       \               user32
ELF     7eabc000-7eb00000       Deferred        advapi32<elf>
  \-PE  7ead0000-7eb00000       \               advapi32
ELF     7eb00000-7eb0a000       Deferred        libgcc_s.so.1
ELF     7ebdf000-7ec91000       Deferred        gdi32<elf>
  \-PE  7ebf0000-7ec91000       \               gdi32
ELF     7ec91000-7ece7000       Deferred        shlwapi<elf>
  \-PE  7eca0000-7ece7000       \               shlwapi
ELF     7ece7000-7edcd000       Deferred        shell32<elf>
  \-PE  7ed00000-7edcd000       \               shell32
ELF     7edcd000-7ede1000       Deferred        lz32<elf>
  \-PE  7edd0000-7ede1000       \               lz32
ELF     7ede1000-7edfa000       Deferred        version<elf>
  \-PE  7edf0000-7edfa000       \               version
ELF     7ee2d000-7ef2f000       Deferred        kernel32<elf>
  \-PE  7ee50000-7ef2f000       \               kernel32
ELF     7ef2f000-7ef39000       Deferred        libnss_files.so.2
ELF     7ef39000-7ef42000       Deferred        libnss_nis.so.2
ELF     7ef42000-7ef57000       Deferred        libnsl.so.1
ELF     7ef57000-7ef60000       Deferred        libnss_compat.so.2
ELF     7ef60000-7ef82000       Deferred        libm.so.6
ELF     7ef82000-7f000000       Deferred        ntdll<elf>
  \-PE  7ef90000-7f000000       \               ntdll
ELF     b7cb4000-b7cb7000       Deferred        libxau.so.6
ELF     b7cb9000-b7cbc000       Deferred        libdl.so.2
ELF     b7cbc000-b7deb000       Deferred        libc.so.6
ELF     b7deb000-b7dfd000       Deferred        libpthread.so.0
ELF     b7dfd000-b7e02000       Deferred        libxxf86vm.so.1
ELF     b7e02000-b7e0a000       Deferred        libsm.so.6
ELF     b7e0a000-b7f1b000       Deferred        libwine.so.1
ELF     b7f1e000-b7f34000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000025 (D) D:\setup.exe
        00000028    0
        00000026    0 <==
0000000e
        00000011    0
        00000010    0
        0000000f    0
0000000a
        0000000b    0

```

Appears in the terminal when I start it.
Well, if its not a wine problem and you just cant install the game, try finding the application you want from appdb (search for appdb in google) or in franskcorner.org. Also, it may "just" not be supported <:

---

### Post by TailsAndy on 2006-10-01
Also, I'm having a problem running some programs, when I try to run them it says "A debugger has been detected, unload the debugger and try again"](*,)

---

