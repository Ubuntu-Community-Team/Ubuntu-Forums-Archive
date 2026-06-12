---
title: "Quick Question about Wine"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by cattleeyes on 2007-10-15
I'm sure this question has a simple solution, but today is my first day using Wine and I'm running into a problem.
I'm trying to setup a Linksys router and need to run the CD, etc.
Anyway, running Wine from the terminal seems to work and run stably until I start clicking the "next" buttons for installation.  After several seconds, the entire setup closes and nothing I can think to do will make it more stable (though again, this is my first Wine attempt).

**When attempting to install, the installer loads seemingly stable, but then, after clicking "Next," the following code occurs while the screen loads and the installer crashes:**

fixme:ole:OleLoadPictureEx (0x7eca12dc,2929,1,{00020400-0000-0000-c000-000000000046},x=0,y=0,f=0,0x7fb9f8a0), partially implemented.
fixme:ole:OleLoadPictureEx (0x7eca12dc,2944,1,{00020400-0000-0000-c000-000000000046},x=0,y=0,f=0,0x7fb9f848), partially implemented.
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4590f811-1d3a-11d0-891f-00aa004b2e24}, hres is 0x80040154
wine: Unhandled page fault on read access to 0x00000004 at address 0x449bba (thread 000c), starting debugger...
fixme:ole:OleLoadPictureEx (0x7eca12dc,2672,1,{00020400-0000-0000-c000-000000000046},x=0,y=0,f=0,0x7fb9f8a4), partially implemented.
WineDbg starting on pid 0xa
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x00449bba).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1137 GS:0033
 EIP:00449bba ESP:7eaf3a8c EBP:7eaf3bf8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000004 EBX:00000000 ECX:7eaf3ae4 EDX:004ffd6c
 ESI:7eaf3ae4 EDI:7ec856e8
Stack dump:
0x7eaf3a8c:  00000000 7eaf3a98 7eaf3ae4 00000000
0x7eaf3a9c:  00449c34 004ffd6c 7ec856e8 7ec856e0
0x7eaf3aac:  7eaf3bf8 7ec856e0 00506f6c 00000000
0x7eaf3abc:  7eaf3ae4 80040154 7ec856e8 7eaf3bf8
0x7eaf3acc:  00449ada 7eaf3af4 004c1710 00000000
0x7eaf3adc:  0040b692 00000003 004c9ab4 7ec856e8
0226: sel=1137 base=7eef4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x00449bba in setupwizard (+0x49bba) (0x00449bba)
  2 0x7ffbc543 in ntdll (+0x3c543) (0x7ffbc543)
  3 0xb7f79341 start_thread+0x81 in libpthread.so.0 (0xb7f79341)
  4 0xb7f0e4ee __clone+0x5e in libc.so.6 (0xb7f0e4ee)
0x00449bba: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (83 modules)
PE      0x00400000-00698000     Export          setupwizard
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7ed82000-7edce000     Deferred        libgcrypt.so.11
ELF     0x7edce000-7edde000     Deferred        libtasn1.so.2
ELF     0x7edde000-7ee0b000     Deferred        libcrypt.so.1
ELF     0x7ee19000-7ee82000     Deferred        libgnutls.so.12
ELF     0x7ee82000-7eeb0000     Deferred        libcups.so.2
ELF     0x7ef08000-7ef0c000     Deferred        libgpg-error.so.0
ELF     0x7ef48000-7ef79000     Deferred        uxtheme<elf>
  \-PE  0x7ef50000-7ef79000     \               uxtheme
ELF     0x7ef97000-7efa0000     Deferred        libxcursor.so.1
ELF     0x7efa0000-7efbc000     Deferred        imm32<elf>
  \-PE  0x7efb0000-7efbc000     \               imm32
ELF     0x7efbc000-7efc4000     Deferred        libxrender.so.1
ELF     0x7efc4000-7f02a000     Deferred        libgl.so.1
ELF     0x7f02a000-7f110000     Deferred        libx11.so.6
ELF     0x7f110000-7f128000     Deferred        libice.so.6
ELF     0x7f128000-7f1ab000     Deferred        winex11<elf>
  \-PE  0x7f140000-7f1ab000     \               winex11
ELF     0x7f1ab000-7f1ca000     Deferred        libexpat.so.1
ELF     0x7f1ca000-7f1f8000     Deferred        libfontconfig.so.1
ELF     0x7f1f8000-7f20c000     Deferred        libz.so.1
ELF     0x7f20c000-7f276000     Deferred        libfreetype.so.6
ELF     0x7f276000-7f295000     Deferred        mpr<elf>
  \-PE  0x7f280000-7f295000     \               mpr
ELF     0x7f295000-7f2dc000     Deferred        wininet<elf>
  \-PE  0x7f2a0000-7f2dc000     \               wininet
ELF     0x7f2dc000-7f307000     Deferred        ws2_32<elf>
  \-PE  0x7f2e0000-7f307000     \               ws2_32
ELF     0x7f307000-7f321000     Deferred        wsock32<elf>
  \-PE  0x7f310000-7f321000     \               wsock32
ELF     0x7f321000-7f3b7000     Deferred        oleaut32<elf>
  \-PE  0x7f340000-7f3b7000     \               oleaut32
ELF     0x7f3b7000-7f3cb000     Deferred        olepro32<elf>
  \-PE  0x7f3c0000-7f3cb000     \               olepro32
ELF     0x7f3cb000-7f3e5000     Deferred        oledlg<elf>
  \-PE  0x7f3d0000-7f3e5000     \               oledlg
ELF     0x7f3e5000-7f411000     Deferred        winspool<elf>
  \-PE  0x7f3f0000-7f411000     \               winspool
ELF     0x7f411000-7f4d1000     Deferred        comctl32<elf>
  \-PE  0x7f420000-7f4d1000     \               comctl32
ELF     0x7f4d1000-7f4f0000     Deferred        iphlpapi<elf>
  \-PE  0x7f4e0000-7f4f0000     \               iphlpapi
ELF     0x7f4f0000-7f539000     Deferred        rpcrt4<elf>
  \-PE  0x7f500000-7f539000     \               rpcrt4
ELF     0x7f539000-7f5ca000     Deferred        ole32<elf>
  \-PE  0x7f550000-7f5ca000     \               ole32
ELF     0x7f5ca000-7f625000     Deferred        shlwapi<elf>
  \-PE  0x7f5e0000-7f625000     \               shlwapi
ELF     0x7f625000-7f6f1000     Deferred        shell32<elf>
  \-PE  0x7f640000-7f6f1000     \               shell32
ELF     0x7f6f1000-7f78e000     Deferred        comdlg32<elf>
  \-PE  0x7f700000-7f78e000     \               comdlg32
ELF     0x7f78e000-7f7ce000     Deferred        advapi32<elf>
  \-PE  0x7f7a0000-7f7ce000     \               advapi32
ELF     0x7f8a3000-7f954000     Deferred        gdi32<elf>
  \-PE  0x7f8c0000-7f954000     \               gdi32
ELF     0x7f954000-7fa80000     Deferred        user32<elf>
  \-PE  0x7f970000-7fa80000     \               user32
ELF     0x7fb90000-7fb94000     Deferred        libxfixes.so.3
ELF     0x7fb94000-7fb9b000     Deferred        libdrm.so.2
ELF     0x7fbce000-7fcd0000     Deferred        kernel32<elf>
  \-PE  0x7fbf0000-7fcd0000     \               kernel32
ELF     0x7fcd3000-7fce0000     Deferred        libxext.so.6
ELF     0x7fce5000-7fce8000     Deferred        libxrandr.so.2
ELF     0x7fce8000-7fceb000     Deferred        libxau.so.6
ELF     0x7fceb000-7fcf0000     Deferred        libxxf86vm.so.1
ELF     0x7fe01000-7fe0b000     Deferred        libgcc_s.so.1
ELF     0x7fe0b000-7fe15000     Deferred        libnss_files.so.2
ELF     0x7fe15000-7fe1e000     Deferred        libnss_nis.so.2
ELF     0x7fe1e000-7fe33000     Deferred        libnsl.so.1
ELF     0x7fe33000-7fe3c000     Deferred        libnss_compat.so.2
ELF     0x7fe3d000-7fe42000     Deferred        libxxf86dga.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Export          ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e42000-b7e45000     Deferred        libdl.so.2
ELF     0xb7e45000-b7f74000     Export          libc.so.6
ELF     0xb7f74000-b7f86000     Export          libpthread.so.0
ELF     0xb7f95000-b7faf000     Deferred        libwine.so.1
ELF     0xb7fb2000-b7fc8000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) Z:\home\bryan\Desktop\Bin\NonXP\SetupWizard.exe
        0000000c    0 <==
        0000000b    0
00000008
        00000009    0


**Any tips?  Thanks so much!  (*Edit*  I'm also still on Dapper Drake for some reason.  Think that matters?)**

---

### Post by oodledoodle on 2007-10-15
i would be very suprised if your router software worked in wine, is there not a windows machine handy to use? 

or can you not type the ip address of your router into a web browser while cabled in, and setup the router from there?

---

### Post by Hospadar on 2007-10-15
you probably don't even need the software
routers don't require any software on the client machines.

If you look in the manual, there is usually an IP address to go to when plugged into the router that will take you to the router's config page.

it's probably something like 192.168.0.0 or 192.168.0.1, so in a web browser do something like [http://192.168.0.0/](http://192.168.0.0/)

usually those cd's just have a little wizard to guide you through the setup, but all of those setup options will be available through the router's config page

---

### Post by oodledoodle on 2007-10-15
you forgot to mention that the cds also install yahoo toolbar for you. im pretty sure routers dont work without it... 

;)

---

### Post by cattleeyes on 2007-10-16
Durr.  Thank you so much for saving me hours of doing stupid things.

---

