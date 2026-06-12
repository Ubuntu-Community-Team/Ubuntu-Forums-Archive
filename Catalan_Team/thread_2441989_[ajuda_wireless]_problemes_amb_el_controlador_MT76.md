---
title: "[ajuda wireless] problemes amb el controlador MT7630E de Mediatek"
date: 2020-04-28
forum: Catalan Team
---

### Post by estemon on 2020-04-28
Bona tarda, demano ajuda per aquí a veure si tinc sort ja que vaig arrossegant un problema des de fa temps i que no aconsegueixo solucionar.

Tinc un portàtil Asus amb el dispositiu de Wifi de Mediatek MT7630E. Fins ara utilitzava Ubuntu 16.04.5 amb els headers 4.8.0-52-generic per fer anar la Wifi, ja que amb qualsevol capçalera posterior el sistema deixava de reconèixer el dispositiu. Amb tot, he actualitzat a 20.04 i, tal i com em suposava, l'ordinador no reconeix la targeta Wifi. He provat a descarregar-me els drivers a [https://github.com/neurobin/MT7630E.git](https://github.com/neurobin/MT7630E.git) malgrat el propietari del repositori no els manté més. Quan intento compliar, provant amb els comandaments make, install i també amb dkms, retorna tota mena de errors de compilació i "flags" que no sóc capaç d'entendre, ni tampoc sé ben bé com revertir res d'aquests errors de compilació, si és que queden en memòria a alguna banda.

El que obtinc després de fer un lshw és, referent al dispositiu:

 ```
          *-network UNCLAIMED
                description: Network controller
                product: MT7630e 802.11bgn Wireless Network Adapter
                vendor: MEDIATEK Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: memory:a3100000-a31fffff

```

També he provat de reinstal·lar la versió de kernel que sí que reconeixia el controlador, la 4.8.0-52-generic, però ja no el reconeix, a més que també perdo la targeta gràfica i altres funcionalitats. He provat també instal·lant el paquet linux-image-extra corresponent però no millora.

Puc enviar-vos captura del que faci falta, qualsevol idea de resolució que he anat trobant pels diferents fòrums, aquí, a askubuntu, starckoverflow, etc, resulten en errors que no puc solucionar. A veure si aquí algú té idea de què es pot fer, ja que un portàtil que només funciona per Ethernet perd una mica la gràcia.

Potser si aconsegueixo compilar el driver ja es soluciona, però no de moment no me'n surto :|

Molt agraït per la possible ajuda que em pogueu oferir! :o

Addenda: una cosa que he vist, que no tinc ni idea de si afecta o no, és que el sistema és de 64 bits i al retorn de lshw veig que diu "width: 32 bits". Al controlador d'Ethernet (que sí que funciona) diu "width: 64 bits". Pot ser que tingui a veure? Que per algun motiu el driver estigui configurat -ni idea- com a 32 bits però si no coincideix amb el SO a 64 no el "veu"?

---

### Post by estemon on 2020-04-28
Després de fer

```
sudo ./test
```

Retorna tot això:

```
make -C /lib/modules/5.4.0-26-generic/build M=/home/estemon/Baixades/MT7630E-release/rt2x00 modulesmake[1]: Entering directory '/usr/src/linux-headers-5.4.0-26-generic'
  CC [M]  /home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00dev.o
In file included from /home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00dev.c:32:
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h: In function &#8216;rt2x00_rf_read&#8217;:
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h:98:19: error: expected &#8216;(&#8217; before &#8216;static&#8217;
   98 | #define __inline  static inline
      |                   ^~~~~~
././include/linux/compiler_types.h:210:24: note: in expansion of macro &#8216;__inline&#8217;
  210 | #define asm_inline asm __inline
      |                        ^~~~~~~~
./arch/x86/include/asm/bug.h:35:2: note: in expansion of macro &#8216;asm_inline&#8217;
   35 |  asm_inline volatile("1:\t" ins "\n"    \
      |  ^~~~~~~~~~
./arch/x86/include/asm/bug.h:73:2: note: in expansion of macro &#8216;_BUG_FLAGS&#8217;
   73 |  _BUG_FLAGS(ASM_UD2, 0);     \
      |  ^~~~~~~~~~
./include/asm-generic/bug.h:62:57: note: in expansion of macro &#8216;BUG&#8217;
   62 | #define BUG_ON(condition) do { if (unlikely(condition)) BUG(); } while (0)
      |                                                         ^~~
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h:2453:2: note: in expansion of macro &#8216;BUG_ON&#8217;
 2453 |  BUG_ON(word < 1 || word > rt2x00dev->ops->rf_size / sizeof(u32));
      |  ^~~~~~
In file included from ./include/linux/bug.h:5,
                 from ./include/linux/thread_info.h:12,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:78,
                 from ./include/linux/spinlock.h:51,
                 from ./include/linux/seqlock.h:36,
                 from ./include/linux/time.h:6,
                 from ./include/linux/stat.h:19,
                 from ./include/linux/module.h:10,
                 from /home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00dev.c:28:
./arch/x86/include/asm/bug.h:35:22: error: expected identifier or &#8216;(&#8217; before string constant
   35 |  asm_inline volatile("1:\t" ins "\n"    \
      |                      ^~~~~~
./arch/x86/include/asm/bug.h:73:2: note: in expansion of macro &#8216;_BUG_FLAGS&#8217;
   73 |  _BUG_FLAGS(ASM_UD2, 0);     \
      |  ^~~~~~~~~~
./include/asm-generic/bug.h:62:57: note: in expansion of macro &#8216;BUG&#8217;
   62 | #define BUG_ON(condition) do { if (unlikely(condition)) BUG(); } while (0)
      |                                                         ^~~
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h:2453:2: note: in expansion of macro &#8216;BUG_ON&#8217;
 2453 |  BUG_ON(word < 1 || word > rt2x00dev->ops->rf_size / sizeof(u32));
      |  ^~~~~~
In file included from /home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00dev.c:32:
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h:98:19: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
   98 | #define __inline  static inline
      |                   ^~~~~~
././include/linux/compiler_types.h:210:24: note: in expansion of macro &#8216;__inline&#8217;
  210 | #define asm_inline asm __inline
      |                        ^~~~~~~~
./arch/x86/include/asm/bug.h:35:2: note: in expansion of macro &#8216;asm_inline&#8217;
   35 |  asm_inline volatile("1:\t" ins "\n"    \
      |  ^~~~~~~~~~
./arch/x86/include/asm/bug.h:73:2: note: in expansion of macro &#8216;_BUG_FLAGS&#8217;
   73 |  _BUG_FLAGS(ASM_UD2, 0);     \
      |  ^~~~~~~~~~
./include/asm-generic/bug.h:62:57: note: in expansion of macro &#8216;BUG&#8217;
   62 | #define BUG_ON(condition) do { if (unlikely(condition)) BUG(); } while (0)
      |                                                         ^~~
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h:2453:2: note: in expansion of macro &#8216;BUG_ON&#8217;
 2453 |  BUG_ON(word < 1 || word > rt2x00dev->ops->rf_size / sizeof(u32));
      |  ^~~~~~
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h: In function &#8216;rt2x00_rf_write&#8217;:
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h:98:19: error: expected &#8216;(&#8217; before &#8216;static&#8217;
   98 | #define __inline  static inline
      |                   ^~~~~~
././include/linux/compiler_types.h:210:24: note: in expansion of macro &#8216;__inline&#8217;
  210 | #define asm_inline asm __inline
      |                        ^~~~~~~~
./arch/x86/include/asm/bug.h:35:2: note: in expansion of macro &#8216;asm_inline&#8217;
   35 |  asm_inline volatile("1:\t" ins "\n"    \
      |  ^~~~~~~~~~
./arch/x86/include/asm/bug.h:73:2: note: in expansion of macro &#8216;_BUG_FLAGS&#8217;
   73 |  _BUG_FLAGS(ASM_UD2, 0);     \
      |  ^~~~~~~~~~
./include/asm-generic/bug.h:62:57: note: in expansion of macro &#8216;BUG&#8217;
   62 | #define BUG_ON(condition) do { if (unlikely(condition)) BUG(); } while (0)
      |                                                         ^~~
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h:2460:2: note: in expansion of macro &#8216;BUG_ON&#8217;
 2460 |  BUG_ON(word < 1 || word > rt2x00dev->ops->rf_size / sizeof(u32));
      |  ^~~~~~
In file included from ./include/linux/bug.h:5,
                 from ./include/linux/thread_info.h:12,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:78,
                 from ./include/linux/spinlock.h:51,
                 from ./include/linux/seqlock.h:36,
                 from ./include/linux/time.h:6,
                 from ./include/linux/stat.h:19,
                 from ./include/linux/module.h:10,
                 from /home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00dev.c:28:
./arch/x86/include/asm/bug.h:35:22: error: expected identifier or &#8216;(&#8217; before string constant
   35 |  asm_inline volatile("1:\t" ins "\n"    \
      |                      ^~~~~~
./arch/x86/include/asm/bug.h:73:2: note: in expansion of macro &#8216;_BUG_FLAGS&#8217;
   73 |  _BUG_FLAGS(ASM_UD2, 0);     \
      |  ^~~~~~~~~~
./include/asm-generic/bug.h:62:57: note: in expansion of macro &#8216;BUG&#8217;
   62 | #define BUG_ON(condition) do { if (unlikely(condition)) BUG(); } while (0)
      |                                                         ^~~
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h:2460:2: note: in expansion of macro &#8216;BUG_ON&#8217;
 2460 |  BUG_ON(word < 1 || word > rt2x00dev->ops->rf_size / sizeof(u32));
      |  ^~~~~~
In file included from /home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00dev.c:32:
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h:98:19: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
   98 | #define __inline  static inline
      |                   ^~~~~~
././include/linux/compiler_types.h:210:24: note: in expansion of macro &#8216;__inline&#8217;
  210 | #define asm_inline asm __inline
      |                        ^~~~~~~~
./arch/x86/include/asm/bug.h:35:2: note: in expansion of macro &#8216;asm_inline&#8217;
   35 |  asm_inline volatile("1:\t" ins "\n"    \
      |  ^~~~~~~~~~
./arch/x86/include/asm/bug.h:73:2: note: in expansion of macro &#8216;_BUG_FLAGS&#8217;
   73 |  _BUG_FLAGS(ASM_UD2, 0);     \
      |  ^~~~~~~~~~
./include/asm-generic/bug.h:62:57: note: in expansion of macro &#8216;BUG&#8217;
   62 | #define BUG_ON(condition) do { if (unlikely(condition)) BUG(); } while (0)
      |                                                         ^~~
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h:2460:2: note: in expansion of macro &#8216;BUG_ON&#8217;
 2460 |  BUG_ON(word < 1 || word > rt2x00dev->ops->rf_size / sizeof(u32));
      |  ^~~~~~
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00dev.c: In function &#8216;rt2x00lib_beaconupdate_iter&#8217;:
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h:98:19: error: expected &#8216;(&#8217; before &#8216;static&#8217;
   98 | #define __inline  static inline
      |                   ^~~~~~
././include/linux/compiler_types.h:210:24: note: in expansion of macro &#8216;__inline&#8217;
  210 | #define asm_inline asm __inline
      |                        ^~~~~~~~
./arch/x86/include/asm/bug.h:35:2: note: in expansion of macro &#8216;asm_inline&#8217;
   35 |  asm_inline volatile("1:\t" ins "\n"    \
      |  ^~~~~~~~~~
./arch/x86/include/asm/bug.h:79:2: note: in expansion of macro &#8216;_BUG_FLAGS&#8217;
   79 |  _BUG_FLAGS(ASM_UD2, BUGFLAG_WARNING|(flags));  \
      |  ^~~~~~~~~~
./include/asm-generic/bug.h:90:19: note: in expansion of macro &#8216;__WARN_FLAGS&#8217;
   90 | #define __WARN()  __WARN_FLAGS(BUGFLAG_TAINT(TAINT_WARN))
      |                   ^~~~~~~~~~~~
./include/asm-generic/bug.h:115:3: note: in expansion of macro &#8216;__WARN&#8217;
  115 |   __WARN();      \
      |   ^~~~~~
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00dev.c:259:2: note: in expansion of macro &#8216;WARN_ON&#8217;
  259 |  WARN_ON(rt2x00_is_usb(rt2x00dev));
      |  ^~~~~~~
In file included from ./include/linux/bug.h:5,
                 from ./include/linux/thread_info.h:12,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:78,
                 from ./include/linux/spinlock.h:51,
                 from ./include/linux/seqlock.h:36,
                 from ./include/linux/time.h:6,
                 from ./include/linux/stat.h:19,
                 from ./include/linux/module.h:10,
                 from /home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00dev.c:28:
./arch/x86/include/asm/bug.h:35:22: error: expected identifier or &#8216;(&#8217; before string constant
   35 |  asm_inline volatile("1:\t" ins "\n"    \
      |                      ^~~~~~
./arch/x86/include/asm/bug.h:79:2: note: in expansion of macro &#8216;_BUG_FLAGS&#8217;
   79 |  _BUG_FLAGS(ASM_UD2, BUGFLAG_WARNING|(flags));  \
      |  ^~~~~~~~~~
./include/asm-generic/bug.h:90:19: note: in expansion of macro &#8216;__WARN_FLAGS&#8217;
   90 | #define __WARN()  __WARN_FLAGS(BUGFLAG_TAINT(TAINT_WARN))
      |                   ^~~~~~~~~~~~
./include/asm-generic/bug.h:115:3: note: in expansion of macro &#8216;__WARN&#8217;
  115 |   __WARN();      \
      |   ^~~~~~
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00dev.c:259:2: note: in expansion of macro &#8216;WARN_ON&#8217;
  259 |  WARN_ON(rt2x00_is_usb(rt2x00dev));
      |  ^~~~~~~
In file included from /home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00dev.c:32:
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00.h:98:19: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
   98 | #define __inline  static inline
      |                   ^~~~~~
././include/linux/compiler_types.h:210:24: note: in expansion of macro &#8216;__inline&#8217;
  210 | #define asm_inline asm __inline
      |                        ^~~~~~~~
./arch/x86/include/asm/bug.h:35:2: note: in expansion of macro &#8216;asm_inline&#8217;
   35 |  asm_inline volatile("1:\t" ins "\n"    \
      |  ^~~~~~~~~~
./arch/x86/include/asm/bug.h:79:2: note: in expansion of macro &#8216;_BUG_FLAGS&#8217;
   79 |  _BUG_FLAGS(ASM_UD2, BUGFLAG_WARNING|(flags));  \
      |  ^~~~~~~~~~
./include/asm-generic/bug.h:90:19: note: in expansion of macro &#8216;__WARN_FLAGS&#8217;
   90 | #define __WARN()  __WARN_FLAGS(BUGFLAG_TAINT(TAINT_WARN))
      |                   ^~~~~~~~~~~~
./include/asm-generic/bug.h:115:3: note: in expansion of macro &#8216;__WARN&#8217;
  115 |   __WARN();      \
      |   ^~~~~~
/home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00dev.c:259:2: note: in expansion of macro &#8216;WARN_ON&#8217;
  259 |  WARN_ON(rt2x00_is_usb(rt2x00dev));
      |  ^~~~~~~
make[2]: *** [scripts/Makefile.build:275: /home/estemon/Baixades/MT7630E-release/rt2x00/rt2x00dev.o] Error 1
make[1]: *** [Makefile:1719: /home/estemon/Baixades/MT7630E-release/rt2x00] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-26-generic'
make: *** [Makefile:9: all] Error 2
'firmware/BT/mt76x0.bin' -> '/lib/firmware/mt76x0.bin'
'firmware/Wi-FI/MT7650E234.bin' -> '/lib/firmware/MT7650E234.bin'
insmod: ERROR: could not load module ./rt2x00/mt7630e.ko: No such file or directory
insmod: ERROR: could not load module ./btloader/mt76xx.ko: No such file or directory

```

I aquí ja em perdo...

---

### Post by wgarcia on 2020-05-05
Has provat iniciar el sistema amb un USB/CD autònom ("life") i mirar si la targeta WIFI respon? No conec massa d'aquest controlador, però he llegit una mica i m'ha semblat entendre que havien millorat el suport al nucli de Linux des de les versions 5.3 o així. 

Per una altra part em sembla que allò de "width: 32 bits" és normal.

Per últim, és convenient que per a sortides llargues de missatges d'ordres o de compilació fer servir [https://paste.ubuntu.com/](https://paste.ubuntu.com/) i aquí sols enganxar l'enllaç.

---

