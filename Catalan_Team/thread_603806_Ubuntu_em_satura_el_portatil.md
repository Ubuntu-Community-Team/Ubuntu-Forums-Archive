---
title: "Ubuntu em satura el portatil"
date: 2007-11-05
forum: Catalan Team
---

### Post by kioni on 2007-11-05
Fa cosa de un parell de mesos que tic Ubuntu al portàtil, i de tan en tan em queda el sistema saturat i no puc obrir ni tancar finestres, al cap de uns 10 segons es desbloqueja i funciona normalment, quan es bloqueja em permet moure el punter, escoltar la musica (si la tinc posada).

Seguint el consell de l'Alex he posat un top per veure si hi ha algun programa o activitat del sistema que provoca el problema, però no n'hi ha cap que així ho indiqui.

Tan mateix a la barra superior del sistema tinc posat el monitor de sistema que em permet veure com va els recursos de la RAM, la Xarxa i el processador, és en aquest últim el processador que mostra un augment fins als topes quan hi ha activitat IOWait, en aquest moment és quan tinc el portatil saturat, però un cop veig el let del meu portatil que esta destinat a mostrar quan el processador funciona s'activa fent pampallugues deixa de estar saturat i el IOWait desapareix.

Potser estic equivocat però podria ser que no tingui el sistema o hardware ben configurat ??? Concretament el processador ... 
El meu portàtil és un Acer Aspire 5600, Intel Core TM Duo T2250 (1.73 Ghz 533 Mhz FSB 2 MB L2 Cache)

S'ha de reconfigurar alguna cosa perquè tingui un bon funcionament ?O alguna ideea per solucionar aquest molest problema ?

Gràcies

---

### Post by papapep on 2007-11-05
Enganxa el que et mostri el top.

També digue'ns com tens els disc dur de ple. 
Per això, enganxa'ns el que et mostri la ordre:

```
sudo df -h
```

Per cert, no conec cap portàtil que mostri la activitat del processador. No serà el led d'activitat del disc dur??

---

### Post by guillemsola on 2007-11-05
A mi em passava quelcom amb una simptomatologia molt semblant.

El problema era el lector de DVD model TS-L632D_SC01 que munten a alguns portàtils.

Una solució molt divertida era deixar un disc a dins de la unitat. Així desapareix el problema. L'altre va ser actualitzar el firmware del DVD.

Si li vols donar un cop d'ull

[http://ubuntuforums.org/showthread.php?t=542603](http://ubuntuforums.org/showthread.php?t=542603)

Sort!

---

### Post by kioni on 2007-11-05
Upsss és veritat, no és el let del processador sinó el de funcionament del disc dur :P

T'adjunto les dades del resum de l'estat del disc dur a traves de l'ordre que m'has donat, informació del top i informació sobre la configuració del sistema.

Si fes falta alguna altre dada ja m'ho diries, una salutació.


Kioni

PD

De pas provaré la solució que diu el Angrychai a veure si hi ha sort ...

---

### Post by papapep on 2007-11-05
Buffff.....el problema aquest teu sembla que te MOLTA tela...
Al Launchpad hi ha un fil immens que parla del tema i no en treuen l'entrellat.
Parlen de la versió de kernel, dels discs SATA, del trackerd, del sistema de fitxers Ext3..fins i tot sembla que no és un problema circunscrit a Ubuntu, sinó que en altres distribucions també hi ha gent que s'ho troba, però no acaben trobar-li el punt:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094)

Em sembla que ens haurem d'esperar una miqueta a veure si algun iluminat troba la sol·lució.

---

### Post by kioni on 2007-11-07
Holas de nou, he provat el mètode que va recomenar l'Angrychai (ja que tambe tinc el mateix lector al portatil), he posat un cd dins el lector i des de llavors que no se'm torna a saturar el portàtil :) 
El meu lector és un TS-L632D així suposo que el següent pas serà actualitzar el firmware com vas fer tu, el que passa que no tinc ni idea de com s'ha de fer.
T'estaria molt agraït si m'indiquessis exactament que vas fer per actualitzar-lo ja que he estat buscan informació per Internet i no ho he sabut trobar ... :(
Gràcies a tu ja se d'on ve el problema, ara només falta posar-hi remei.

Kioni

---

### Post by guillemsola on 2007-11-07
Ok, doncs si vols acabar de confirmar l'error jo el vaig detectar perquè si feia un dmeg dona com a sortida:

> ata1: port is slow to respond, please be patient (Status 0xd0)

Mentre el port està "slow" l'ordinador es queda piruli. 

A veure el firmware que jo vaig posar es el TS-L632D_SC03.bin El pots trobar en format zip aquí per exemple (buscat a google)

[http://www.toshibaer.com/firmware/index.php?path=TS-L632D/](http://www.toshibaer.com/firmware/index.php?path=TS-L632D/)

Veig que hi ha una versió TS-L632D_SC04.bin que deu ser mes nova. Jo vaig fer servir la 03.

Per canviar el firmware hi ha moltes opcions que trobaràs al google. Necessites un software per carregar firmware per a un samsung. 

Aquí ho expliquen per exemple.

[http://forum.rpc1.org/viewtopic.php?t=6792](http://forum.rpc1.org/viewtopic.php?t=6792)

bàsicament necessites l'arixu

[http://www.samsungodd.com/KorLib/File/sfdndos.exe](http://www.samsungodd.com/KorLib/File/sfdndos.exe)

Ho poses tot a un disc botable i li endinyes el firmware que t'has baixat i festa.

Sort i que la força t'acompanyi!

---

### Post by kioni on 2007-11-10
Hola, he seguit les teves indicacions i he posat l'executable i el fitxer bin en un cd gravat de manera que sigui bootable.
Al inici del sistema llegeix el cd però al cap de uns 5 segons em queda la instrucció : [DR-DOS] A:\  
No se si haig d'escriure alguna altra cosa perque s'executi .... fent un dir veig que hi ha un arxiu (WWBMU) que es .exe si l'executu em surt una nova pantalla amb 5 pasos a seguir, pero les indicacions son amb Alema, pel poc que puc entendre d'aquest idioma veig que hi ha 5 pasos a seguir, es aixo el que haig de fer perque em quedi el Firmware ben posat ?

Kioni

PD

He mirat a l'altre particio del portatil que hi tinc windows i a traves de l'Everest (programa que et detalla tota l'informacio del sistema) i el Firmware del lector es en versio _00 aixi que dedueixo que o no ho he fet be o be s'ha de posar alguna alte cosa quan pots escriure.

---

