---
title: "Es poden assignar més recursos CPU a &quot;ddrescue&quot;?"
date: 2012-02-26
forum: Catalan Team
---

### Post by jinglada on 2012-02-26
Benvolgudes ubunteres,

El *ddrescue* és molt lent, 840 kB/s de mitjana, que per les 250 GB del HD, del que estic creant una imatge, representa unes 83 hores. En canvi el *photorec* va tardar 8126 segons per a 59 GB, o sigui unes 9,6 hores per a les 250 GB.

Hi ha alguna manera de poder dedicar més recursos al *ddrescue* per a fer-lo anar més ràpid?

En el següent àlbum [http://ubuntuforums.org/album.php?albumid=2465](http://ubuntuforums.org/album.php?albumid=2465) hi ha impressions de pantalla referents als recursos i processos quan solament funciona el ddrescue. També n'hi ha una del sistema.

Salutacions cordials.

---

### Post by wgarcia on 2012-02-27
No se m'acut més que intentar que no hi hagi altres processos perquè tots els recursos de la màquina s'hi dediquin. Una altra opció és intentar córrer el ddrescue en alguna altra màquina que tingui processador més ràpid o més memòria RAM.

---

### Post by jinglada on 2012-02-27
> **wgarcia said:**
> No se m'acut més que intentar que no hi hagi altres processos perquè tots els recursos de la màquina s'hi dediquin. Una altra opció és intentar córrer el ddrescue en alguna altra màquina que tingui processador més ràpid o més memòria RAM.

Gràcies wgarcia. Em pensava que potser hi havia algun comanament amb el que es pogués fixar un percentatge determinat de cpu a un determinat procés.

Alguna informació més per si pot ser d'utilitat:

el *free* dóna:

             total       used       free     shared    buffers     cached
Mem:       4060108    4028556      31552          0    1290544    1342452
-/+ buffers/cache:    1395560    2664548
Swap:     12721264       2976   12718288

el *top* dóna:

joan@joan-laptop:~$ top

top - 18:32:34 up  8:27,  3 users,  load average: 1.22, 1.18, 1.10
Tasks: 206 total,   4 running, 201 sleeping,   0 stopped,   1 zombie
Cpu(s): 47.9%us,  1.9%sy,  0.0%ni, 50.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4060108k total,  3903996k used,   156112k free,  1367940k buffers
Swap: 12721264k total,     2976k used, 12718288k free,  1031864k cached
Change delay from 3.0 to: 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 2405 root      20   0 20656 6324  656 R   99  0.2 475:48.77 mount.ntfs                                                                                      
 2207 joan      20   0 1568m 472m  33m R    3 11.9  37:11.80 epiphany-browse                                                                                 
 1991 joan       9 -11  272m 4416 2824 R    1  0.1   4:56.35 pulseaudio                                                                                      
 1333 root      20   0  241m  82m  22m S    1  2.1   7:54.49 Xorg                                                                                            
 2080 joan      20   0 52728 2920 2284 S    0  0.1   0:37.15 gvfsd-trash                                                                                     
 2593 root      20   0 11920  812  592 S    0  0.0   1:36.30 ddrescue                                                                                        
    1 root      20   0 23804 1636 1016 S    0  0.0   0:00.57 init

el *cpuinfo* dóna:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
stepping	: 6
cpu MHz		: 2268.000
cache size	: 3072 KB

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
stepping	: 6
cpu MHz		: 2268.000
cache size	: 3072 KB

---

### Post by wgarcia on 2012-02-28
Una altra possibilitat per alliberar més recursos és córrer la comanda ddrescue sense interfície gràfica. 

Per fer això en reiniciar l'ordinador, a la pantalla de grub per escollir quin sistema començar (si sols tens l'Ubuntu no et surt però es pot fer que mostri aquesta pantalla prement la tecla "majúscula" - shift), prems "e" i et surt una finestra per editar els paràmetres d'arrancada. Has de mirar un lloc on posa "quiet splash" i afegir-li "text" ( o sigui ha de quedar "quiet splash text"). Després prement la tecla F10 farà un inici per un sol cop directament a una línia de comandes, sense iniciar l'entorn gràfic. 

Si veus que queda parat sense mostrar-te el símbol de línia de comandes pots anar a la consola amb la combinació de tecles "Control-ALT-F1", et demanarà usuari i clau i et donarà una terminal perquè puguis executar la teva comanda.

---

### Post by jinglada on 2012-02-28
> **wgarcia said:**
> Una altra possibilitat per alliberar més recursos és córrer la comanda ddrescue sense interfície gràfica. 

Per fer això en reiniciar l'ordinador, a la pantalla de grub per escollir quin sistema començar (si sols tens l'Ubuntu no et surt però es pot fer que mostri aquesta pantalla prement la tecla "majúscula" - shift), prems "e" i et surt una finestra per editar els paràmetres d'arrancada. Has de mirar un lloc on posa "quiet splash" i afegir-li "text" ( o sigui ha de quedar "quiet splash text"). Després prement la tecla F10 farà un inici per un sol cop directament a una línia de comandes, sense iniciar l'entorn gràfic. 

Si veus que queda parat sense mostrar-te el símbol de línia de comandes pots anar a la consola amb la combinació de tecles "Control-ALT-F1", et demanarà usuari i clau i et donarà una terminal perquè puguis executar la teva comanda.

Gràcies, altra vegada, wgarcia. Ho he volgut fer i al prèmer "e" m'he trobat amb una línia que deia "quiet". Hi he afegit "splash text", he premut F10 i no ha respost. He premut ESC i he tornat al mode gràfic. M'he rellegit el teu missatge i ho he tornat a intentar. Llavors la línia "quiet splash text" havia desaparegut. L'he afegida i F10 tampoc ha produït cap moviment.

---

### Post by jinglada on 2012-02-28
He escrit a l'autor de *ddrescue* Antonio Diaz Diaz i m'ha respost això:
No me das muchos detalles, pero hasta ahora la causa más común de una disminución de velocidad como la que describes ha sido el uso de un sistema de ficheros NTFS en el dispositivo de destino. Creo que el primero en notificar este problema fué Gene Vayngrib en este mensaje[1].
[1]http://lists.gnu.org/archive/html/bug-ddrescue/2009-06/msg00004.html

En Gene Vayngrib diu:
...
Then I noticed that ntfs-3g was eating 100% cpu. So, I created an ext3
partition on the same USB drive, copied my image file and log there and
restarted ddrescue.
Boy! it finished in a couple of hours!
...
En el HD exterior de 1TB hi tinc 264 GB lliures. El HD del DVD és de 250 GB per tant ho puc intentar. 

El sudo fdisk -l dóna:
Disk /dev/sdb: 1000 GB, 1000202273280 bytes 
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System 
/dev/sdb1 1 121602 976768033 7 HPFS/NTFS
Warning: Partition 1 does not end on cylinder boundary

Com es fa per crear una partició amb els 264 GB lliures?

---

### Post by wgarcia on 2012-02-28
Per acabar amb el tema d'iniciar directament a la línia de comandes sense interfície gràfica, si posava sols "quiet" el millor és posar ara "quiet text", o sigui afegir "text" (sense les cometes) a "quiet". 

Però bé, segons el que t'explica el desenvolupador del programa sembla més un mal funcionament que una manca de recursos per córrer el programa.

---

### Post by jinglada on 2012-03-04
Només dir que de les 90 hores que vaig trigar a fer la imatge del HD del DVD de 250 GB sobre un HD NTFS amb el ddrescue, s'ha reduït a una mica més de 5 hores en fer de nou la imatge sobre un HD ext3.
Gràcies per la vostra ajuda.

---

