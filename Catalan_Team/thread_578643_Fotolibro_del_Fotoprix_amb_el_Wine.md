---
title: "Fotolibro del Fotoprix amb el Wine"
date: 2007-10-17
forum: Catalan Team
---

### Post by jodufi on 2007-10-17
Hola a tothom!

Estic intentant instal·lar-me el Fotolibro de Fotoprix amb l'ajuda del Wine, sense molt èxit.

Quan vaig començar la instal·lació del programa (baixat de la pàgina de Fotoprix), em va sortir un missatge en una finestra emergent (veure adjunt).
Per sort vaig poder continuar i acabar l'instal·lació.

Però ara quan intento executar el programa em surt aquest missatge:

```
~/.wine/drive_c/Program Files/Fotoprix/FotoLibro$ wine FotoLibro.exe 
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:win:EnumDisplayDevicesW ((null),0,0x33f850,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 8203 (SPI_SETFONTSMOOTHINGTYPE)
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b844210 (thread 0009), starting debugger...
First chance exception: 0xc0000025 in 32-bit code (0x7bc312ac).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc312ac ESP:0033f9a4 EBP:0033fa08 EFLAGS:00200282(   - 00      - -IS1)
 EAX:0033f9b0 EBX:7bc7b498 ECX:00110020 EDX:0033fd8c
 ESI:0033fd8c EDI:0033fa14
Stack dump:
0x0033f9a4:  00000000 00000000 0033f9fc c0000025
0x0033f9b4:  00000001 0033fd8c 7bc3a906 00000000
0x0033f9c4:  00000001 7b8b0888 0033fc2c 7b865f0a
0x0033f9d4:  0033fae8 7bc309d0 00000001 7bc7b498
0x0033f9e4:  7b820000 00000002 0033fa88 ff39f9c0
0x0033f9f4:  84c9a906 00000001 00000000 7bc31260
Backtrace:
=>1 0x7bc312ac __regs_RtlRaiseException+0x4c() in ntdll (0x0033fa08)
  2 0x7bc68f73 in ntdll (+0x58f73) (0x0033fd68)
  3 0x7bc30876 RtlRaiseException+0x6() in ntdll (0x0033fde0)
  4 0x00415e29 in fotolibro (+0x15e29) (0x0033fe38)
  5 0x00415db2 in fotolibro (+0x15db2) (0x0033fec0)
  6 0x0040575b in fotolibro (+0x575b) (0x0033fee4)
  7 0x004057c3 in fotolibro (+0x57c3) (0x0033ff08)
  8 0x7b874e7e in kernel32 (+0x54e7e) (0x0033ffe8)
  9 0xb7e51af7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc312ac __regs_RtlRaiseException+0x4c in ntdll: subl $4,%esp
Modules:
Module  Address                 Debug info      Name (105 modules)
PE        400000-  b81000       Export          fotolibro
PE      70d00000-70e91000       Deferred        gdiplus
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc97000       Export          ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ccfc000-7cd11000       Deferred        midimap<elf>
  \-PE  7cd00000-7cd11000       \               midimap
ELF     7cd11000-7cd29000       Deferred        msacm32<elf>
  \-PE  7cd20000-7cd29000       \               msacm32
ELF     7cd29000-7cdee000       Deferred        libasound.so.2
ELF     7cdee000-7ce20000       Deferred        winealsa<elf>
  \-PE  7ce00000-7ce20000       \               winealsa
ELF     7ce20000-7ce71000       Deferred        libgcrypt.so.11
ELF     7ce71000-7ce86000       Deferred        libtasn1.so.3
ELF     7ce86000-7ceb4000       Deferred        libcrypt.so.1
ELF     7cec5000-7cf35000       Deferred        libgnutls.so.13
ELF     7cf35000-7cf66000       Deferred        libcups.so.2
ELF     7d274000-7d278000       Deferred        libgpg-error.so.0
ELF     7d278000-7d2aa000       Deferred        uxtheme<elf>
  \-PE  7d280000-7d2aa000       \               uxtheme
ELF     7d2ac000-7d2b1000       Deferred        libxfixes.so.3
ELF     7d2b1000-7d2ba000       Deferred        libxcursor.so.1
ELF     7d2ba000-7d2c0000       Deferred        libxrandr.so.2
ELF     7d2c0000-7d2c8000       Deferred        libxrender.so.1
ELF     7d7f1000-7d7f3000       Deferred        libnvidia-tls.so.1
ELF     7d7f3000-7e079000       Deferred        libglcore.so.1
ELF     7e079000-7e105000       Deferred        libgl.so.1
ELF     7e105000-7e10a000       Deferred        libxdmcp.so.6
ELF     7e10a000-7e10d000       Deferred        libxau.so.6
ELF     7e10d000-7e1fe000       Deferred        libx11.so.6
ELF     7e1fe000-7e20c000       Deferred        libxext.so.6
ELF     7e20c000-7e211000       Deferred        libxxf86vm.so.1
ELF     7e211000-7e229000       Deferred        libice.so.6
ELF     7e229000-7e232000       Deferred        libsm.so.6
ELF     7e232000-7e2bb000       Deferred        winex11<elf>
  \-PE  7e240000-7e2bb000       \               winex11
ELF     7e34a000-7e36a000       Deferred        libexpat.so.1
ELF     7e36a000-7e395000       Deferred        libfontconfig.so.1
ELF     7e395000-7e3a9000       Deferred        libz.so.1
ELF     7e3a9000-7e414000       Deferred        libfreetype.so.6
ELF     7e414000-7e467000       Deferred        crypt32<elf>
  \-PE  7e420000-7e467000       \               crypt32
ELF     7e467000-7e489000       Deferred        oledlg<elf>
  \-PE  7e470000-7e489000       \               oledlg
ELF     7e489000-7e4b7000       Deferred        liblcms.so.1
ELF     7e4b7000-7e4d3000       Deferred        mscms<elf>
  \-PE  7e4c0000-7e4d3000       \               mscms
ELF     7e4d3000-7e4fa000       Deferred        msvfw32<elf>
  \-PE  7e4e0000-7e4fa000       \               msvfw32
ELF     7e4fa000-7e588000       Deferred        winmm<elf>
  \-PE  7e510000-7e588000       \               winmm
ELF     7e588000-7e5ae000       Deferred        msacm32<elf>
  \-PE  7e590000-7e5ae000       \               msacm32
ELF     7e5ae000-7e5e8000       Deferred        avifil32<elf>
  \-PE  7e5c0000-7e5e8000       \               avifil32
ELF     7e5e8000-7e689000       Deferred        comdlg32<elf>
  \-PE  7e5f0000-7e689000       \               comdlg32
ELF     7e689000-7e6bc000       Deferred        winspool<elf>
  \-PE  7e690000-7e6bc000       \               winspool
ELF     7e6bc000-7e6d9000       Deferred        imm32<elf>
  \-PE  7e6c0000-7e6d9000       \               imm32
ELF     7e6d9000-7e796000       Deferred        comctl32<elf>
  \-PE  7e6e0000-7e796000       \               comctl32
ELF     7e796000-7e7ef000       Deferred        shlwapi<elf>
  \-PE  7e7a0000-7e7ef000       \               shlwapi
ELF     7e7ef000-7e8ed000       Deferred        shell32<elf>
  \-PE  7e800000-7e8ed000       \               shell32
ELF     7e8ed000-7e901000       Deferred        olepro32<elf>
  \-PE  7e8f0000-7e901000       \               olepro32
ELF     7e901000-7e921000       Deferred        mpr<elf>
  \-PE  7e910000-7e921000       \               mpr
ELF     7e921000-7e935000       Deferred        lz32<elf>
  \-PE  7e930000-7e935000       \               lz32
ELF     7e935000-7e94f000       Deferred        version<elf>
  \-PE  7e940000-7e94f000       \               version
ELF     7e94f000-7e963000       Deferred        msimg32<elf>
  \-PE  7e960000-7e963000       \               msimg32
ELF     7e963000-7e976000       Deferred        libresolv.so.2
ELF     7e976000-7e994000       Deferred        iphlpapi<elf>
  \-PE  7e980000-7e994000       \               iphlpapi
ELF     7e994000-7e9ed000       Deferred        rpcrt4<elf>
  \-PE  7e9a0000-7e9ed000       \               rpcrt4
ELF     7e9ed000-7e9f9000       Deferred        libgcc_s.so.1
ELF     7eaf4000-7ebb4000       Deferred        gdi32<elf>
  \-PE  7eb10000-7ebb4000       \               gdi32
ELF     7ebb4000-7ecf1000       Deferred        user32<elf>
  \-PE  7ebd0000-7ecf1000       \               user32
ELF     7ecf1000-7ed39000       Deferred        advapi32<elf>
  \-PE  7ed00000-7ed39000       \               advapi32
ELF     7ed39000-7edd8000       Deferred        ole32<elf>
  \-PE  7ed50000-7edd8000       \               ole32
ELF     7edd8000-7ee75000       Deferred        oleaut32<elf>
  \-PE  7edf0000-7ee75000       \               oleaut32
ELF     7efa6000-7efb1000       Deferred        libnss_files.so.2
ELF     7efb1000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efef000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cd2000-b7cdb000       Deferred        libnss_compat.so.2
ELF     b7cdc000-b7ce0000       Deferred        libdl.so.2
ELF     b7ce0000-b7e21000       Deferred        libc.so.6
ELF     b7e22000-b7e39000       Deferred        libpthread.so.0
ELF     b7e4a000-b7f5e000       Export          libwine.so.1
ELF     b7f60000-b7f7b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Fotoprix\FotoLibro\FotoLibro.exe
        00000009    0 <==
~/.wine/drive_c/Program Files/Fotoprix/FotoLibro$ 

```

Algú sap què puc fer perquè funcioni?
Fins ara l'he utilitzat amb el VirtualBox, però va bastant lent i ja n'estic fart.

Salut,
Joan

---

### Post by ilku on 2007-10-18
Hola company:
No et puc resoldre el teu dubte, però per fer un llibre de fotos, et recomano el HOFMANN és molt millor que el fotolibro.

Jo de tu intentaria instal-lar aquest haver-ha si tens més sort.

---

### Post by jodufi on 2007-10-18
Hola iku,

Havia sentit a parlar del HOFMANN, i també vaig intentar instal·lar-lo.

Però la cosa es va acabar molt més ràpid al no poder-se ni instal·lar el Framework .NET

Tot i això, de moment estic content amb els resultats del fotolibro, és ràpid, econòmic, eficaç (almenys de moment) i fàcil de recollir (tinc una tenda prop de casa).

Abans havia provat amb pixmania, amb resultats horrorosos.

Salut

---

### Post by Ferri on 2007-10-18
Jo tampoc puc resoldre el problema. Només volia preguntar si ningú coneix algun programa comparable per a Linux i així ho tindries arreglat.

---

### Post by JoJoC on 2007-10-18
A veure si hi hagues una alternativa gpl...

---

### Post by xoldy on 2007-10-18
Jo he provat amb el programa de l'fnac, però només en windows. Si tinc temps provaré a veure que tal... Ja us diré.
El resultat és comparable al Hoffmann, però trobo que tots fem millor color de cara.
Provaré a instal·lar amb el wine amb la beta que tinc instal·lada i com tenia la intenció de començar amb la Gutsy de zero doncs me la jugo i jugo...
Ja us comentare que tal.

---

### Post by jodufi on 2007-10-18
A veure si aconseguim un programa per a fer llibres sense instal·lar el windows, encara que sigui virtualment.

---

### Post by Aljullu on 2007-10-19
Jo no us puc ajudar, però us animo a que ho intenteu seria molt útil per a tots.

Si voleu podem iniciar una campanya d'enviar correus electrònics a FotoPrix.:lolflag:

---

### Post by jodufi on 2007-10-19
Jo ja els hi vaig enviar un correu fa temps ara no recordo què em van respondre (se em van respondre), però una campanya potser tindria una mica més d'èxit :)

---

