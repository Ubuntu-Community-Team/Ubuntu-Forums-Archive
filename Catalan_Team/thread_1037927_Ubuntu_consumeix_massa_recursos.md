---
title: "Ubuntu consumeix massa recursos"
date: 2009-01-12
forum: Catalan Team
---

### Post by vinga on 2009-01-12
ja fa uns dies que noto que l'ubuntu va força lent, i avui fent un top he vist que la memòria usada era gairebé el 100%!!
deixo un top i si si calen més dades només cal que m'ho demaneu.
(hi ha alguna forma de posar el top més clar? )

gràcies!  :-({|=

> top - 15:38:41 up  4:27,  3 users,  load average: 0.34, 0.48, 0.79
Tasks: 135 total,   1 running, 134 sleeping,   0 stopped,   0 zombie
Cpu0  : 13.1%us,  1.3%sy,  0.0%ni, 83.0%id,  0.7%wa,  0.0%hi,  2.0%si,  0.0%st
Cpu1  : 18.2%us,  2.9%sy,  0.0%ni, 78.6%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2072300k total,  2018168k used,    54132k free,   143604k buffers
Swap:  1542200k total,     2984k used,  1539216k free,  1400208k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4611 grr       20   0  543m 158m  39m S   19  7.8   9:58.85 java
 5427 root      20   0  320m  44m  14m S   17  2.2  11:21.68 Xorg
 4519 grr       20   0 92216  37m  18m S    4  1.9  23:16.65 amule
 3887 root      20   0 28756 2900 1108 S    1  0.1   0:54.95 iftop
 6000 grr       20   0 37736  20m  11m S    1  1.0   1:47.54 python
    4 root      15  -5     0    0    0 S    0  0.0   0:01.96 ksoftirqd/0
    7 root      15  -5     0    0    0 S    0  0.0   0:01.05 ksoftirqd/1
 5920 grr       20   0 63012  44m  23m S    0  2.2   0:30.45 compiz.real
 8295 root      20   0  4052 1280  696 S    0  0.1   3:24.25 mount.ntfs-3g
14659 grr       20   0  2416 1164  884 R    0  0.1   0:00.03 top
    1 root      20   0  1740  592  508 S    0  0.0   0:01.42 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.07 migration/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.08 migration/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      15  -5     0    0    0 S    0  0.0   0:00.12 events/0
   10 root      15  -5     0    0    0 S    0  0.0   0:00.14 events/1
   11 root      15  -5     0    0    0 S    0  0.0   0:00.02 khelper
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1


---

### Post by papapep on 2009-01-12
Doncs sí, fent servir l'etiqueta ```
, que al menú de sobre l'edició de posts es representa amb un #.

Exemple:

[CODE]top - 19:10:20 up 14 days,  5:12, 11 users,  load average: 0.11, 0.30, 0.25
Tasks: 188 total,   1 running, 187 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.8%us,  0.9%sy,  0.0%ni, 95.2%id,  0.0%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   3367980k total,  3103912k used,   264068k free,    53984k buffers
Swap:  2867560k total,    40524k used,  2827036k free,   734632k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7211 root      20   0  904m 121m  22m S    8  3.7 142:41.39 Xorg               
29334 jsmesegu  20   0  630m 567m  19m S    2 17.2 255:05.20 VirtualBox         
 8293 jsmesegu  20   0 1145m 1.1g  18m S    1 32.9  16110:08 VirtualBox         
26868 jsmesegu  20   0  242m 112m  22m S    1  3.4   0:41.28 firefox            
 8051 jsmesegu  20   0 22576  13m 8644 S    1  0.4   1:28.61 metacity           
    1 root      20   0  2844 1692  544 S    0  0.1   0:03.36 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   1:08.52 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.20 watchdog/0         
migration/3 
```

Torna-ho a posar amb aquesta etiqueta, a veure si és més llegible. També seria interessant que ho fessis també aturant l'amule, el python, els efectes d'escriptori i la màquina virtual java, per comparar els resultats.

---

