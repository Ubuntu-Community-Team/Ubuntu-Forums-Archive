---
title: "Problema Con Wine y Juegos"
date: 2008-03-17
forum: Argentina Team
---

### Post by gabyrsh on 2008-03-17
Hola muchachos, hace unos meses entre en el mundo de linux a traves de Ubuntu. Y la verdad que estoy muy contento porque estoy aprendiendo cada dia mas sobre el tema. Ahora bien, hay algo que me tiene sin dormir y no lo puedo resolver. Estoy usando la version Gutsy 7.10. Instalé Wine. Quiero jugar al Age of Empires II. El Wine lo instala exitosamente, pero cuando quiero ejecutar el juego me aparece el siguiente error:

```

fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 16/03/2008, dlt (d/m/y): 5/10/2008
wine: Unhandled page fault on write access to 0x3d796daa at address 0x40d772 (thread 000e), starting debugger...
Unhandled exception: page fault on write access to 0x3d796daa in 32-bit code (0x0040d772).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0040d772 ESP:0034fd90 EBP:0034fe7c EFLAGS:00010212(   - 00      - RIA1)
 EAX:00400000 EBX:7b8b0888 ECX:0034fd94 EDX:00000067
 ESI:00110ad3 EDI:7ffdf000
Stack dump:
0x0034fd90:  00410db5 00000000 00400000 00000067
0x0034fda0:  7ffdf000 00110ad3 7b8b0888 00570d90
0x0034fdb0:  00570e10 00000000 7bc8443c 00570000
0x0034fdc0:  00570578 0034fde4 00000018 00000065
0x0034fdd0:  00000000 00400000 00000067 00570578
0x0034fde0:  7b860001 00000094 00000005 00000001
Backtrace:
=>1 0x0040d772 in age2_x1 (+0xd772) (0x0034fe7c)
  2 0x0041a132 in age2_x1 (+0x1a132) (0x0034ff08)
  3 0x7b874c7e start_process+0xee(arg=0x0) [/build/buildd/wine-0.9.46/dlls/kernel32/process.c:839] in kernel32 (0x0034ffe8)
  4 0xb7ebc9d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0040d772: rcrl        $1,0x3d6862d7(%esi)
Modules:
Module  Address                 Debug info      Name (49 modules)
PE        400000-  459000       Export          age2_x1
PE      10000000-1000c000       Deferred        drvmgt
ELF     7b800000-7b929000       Dwarf           kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d973000-7d97c000       Deferred        libxcursor.so.1
ELF     7d97c000-7d999000       Deferred        imm32<elf>
  \-PE  7d980000-7d999000       \               imm32
ELF     7d999000-7d9a1000       Deferred        libxrender.so.1
ELF     7dd5c000-7dd5e000       Deferred        libnvidia-tls.so.1
ELF     7dd5e000-7e873000       Deferred        libglcore.so.1
ELF     7e873000-7e917000       Deferred        libgl.so.1
ELF     7e917000-7e91c000       Deferred        libxdmcp.so.6
ELF     7e91c000-7e91f000       Deferred        libxau.so.6
ELF     7e91f000-7ea10000       Deferred        libx11.so.6
ELF     7ea10000-7ea1e000       Deferred        libxext.so.6
ELF     7ea1e000-7ea23000       Deferred        libxxf86vm.so.1
ELF     7ea23000-7ea3b000       Deferred        libice.so.6
ELF     7ea3b000-7ea43000       Deferred        libsm.so.6
ELF     7ea43000-7ea48000       Deferred        libxfixes.so.3
ELF     7ea48000-7ea4e000       Deferred        libxrandr.so.2
ELF     7ea55000-7eae0000       Deferred        winex11<elf>
  \-PE  7ea60000-7eae0000       \               winex11
ELF     7eb35000-7eb55000       Deferred        libexpat.so.1
ELF     7eb55000-7eb80000       Deferred        libfontconfig.so.1
ELF     7eb80000-7eb95000       Deferred        libz.so.1
ELF     7eb95000-7ec05000       Deferred        libfreetype.so.6
ELF     7ec17000-7ec2b000       Deferred        lz32<elf>
  \-PE  7ec20000-7ec2b000       \               lz32
ELF     7ec2b000-7ec45000       Deferred        version<elf>
  \-PE  7ec30000-7ec45000       \               version
ELF     7ec45000-7ec8e000       Deferred        advapi32<elf>
  \-PE  7ec50000-7ec8e000       \               advapi32
ELF     7ec8e000-7ed29000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed29000       \               gdi32
ELF     7ed29000-7ee67000       Deferred        user32<elf>
  \-PE  7ed50000-7ee67000       \               user32
ELF     7efa6000-7efb1000       Deferred        libnss_files.so.2
ELF     7efb1000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7efee000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d32000-b7d3b000       Deferred        libnss_compat.so.2
ELF     b7d3c000-b7d40000       Deferred        libdl.so.2
ELF     b7d40000-b7e8a000       Deferred        libc.so.6
ELF     b7e8b000-b7ea3000       Deferred        libpthread.so.0
ELF     b7eb5000-b7fc9000       Dwarf           libwine.so.1
ELF     b7fcb000-b7fe7000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f 
        00000012    0
        00000011    0
        00000010    0
0000000d (D) C:\Archivos de programa\Microsoft Games\Age of Empires II\age2_x1\age2_x1.exe
        0000000e    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000009    0

```

Me pasa tambien con la expansion del Age. Recuerdo que con la version anterior de ubuntu la 6 y algo (no recuerdo bien) me funcionaba de 10.
Busco por todos lados y no puedo encontrarle la vuelta. Alguna Ayuda????

Probando con Cedega el Age me funciona bien, Creo que seria algo de Wine y mi Ubuntu,

Muchas Gracias.:popcorn:

---

### Post by malbecar on 2008-03-17
Buenas, se que instalaste wine, pero probaste con hacerlo desde playonlinux? Tiene algunos scripts, entre ellos el de age of empiere, que facilita un poco las cosas.

---

### Post by pante on 2008-03-17
En la página de Wine lo catalogan entre Platinum y Gold, o sea que funciona casi perfectamente, pero con un parche. Más información: ** [http://appdb.winehq.org/objectManager.php?sClass=application&iId=99](http://appdb.winehq.org/objectManager.php?sClass=application&iId=99) **.

Saludos :)

---

### Post by Radiobuzz on 2008-03-17
Se debe seguramente a que funciona la protección anticopias, con Wine es usual que tengas que meter un parche no-cd. Además recordá emular un escritorio virtual.

---

