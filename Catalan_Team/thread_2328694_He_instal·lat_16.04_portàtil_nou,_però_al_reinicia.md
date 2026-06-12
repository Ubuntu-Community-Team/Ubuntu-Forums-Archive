---
title: "He instal·lat 16.04 portàtil nou, però al reiniciar no apareix GRUB"
date: 2016-06-23
forum: Catalan Team
---

### Post by pserra on 2016-06-23
Hola,
exposo el meu cas aqui perquè porto estona buscant i no tinc clara la solució.
Tinc un portàtil nou Hp amb el Windows 10, vull instal·lar el 16.04.
Per arrancar desde el Pen ja he entrat modificant de la BIOS la compatibilitat heredada... i polsant F9 he engegat des de el PEN i he fet instal·lació ubuntu.
Ho he instal·lat  escollint opció abaix on crec que posa "altres opcions",  he agafat partició de 50GB i allà he creat una per la home,/,etc...
Ha estat 10 minuts instal·lant... i com sempre demana reiniciar...PERÒ AL REINICIAR NO APAREIX EL GRUB....ho he fet 2 vegades i rés... A la segona ja el sistema em deia que el tenia instal·lat...ho he fet tot de nou (formatejant una altre vegada).... i RÉS...

Alguna pista?

Gràcies per endavant...

---

### Post by wgarcia on 2016-07-11
Quan dius que no apareix el GRUB, vols dir que entra directament al sistema? O no arrenca en absolut? 

En tot cas, una cosa que pots fer és iniciar el sistema des d'un CD o USB autònom, i instal·lar un programa que es diu "Boot-repair". Si ho busques per Internet veuràs que hi ha instruccions per instal·lar-lo. Normalment la reparació recomanada arregla l'inici si hi ha algun problema.

Si el tema és que no es veu el grub en iniciar, però si que arrenca directament l'Ubuntu, pot ser degut a què si l'Ubuntu és l'únic sistema instal·lat, no es mostra el grub. Per veure el menú del grub en aquest cas s'ha de prémer la tecla "Majúscules" tot just arrencar el sistema i es mostrarà el menú del grub.

---

### Post by pserra on 2016-07-13
Merci Wgarcia,
vaig insistir  instal·lant el ubuntu 16.04 fins a 3 vegades... i rés..
L'ERROR EL TINC AMB EL MALEÍT UEFI..que  vaig seguir instruccions extretes de internet per   a la BIOS, però alguna cosa vaig fer malament..
Em vaig adonar que ho tenia instal·lat quan vaig polsar F9 mentre engegava i vaig fer engegar des de el disc dur... JA EM VA APARÈIXER EL GRUB.
MERCI  PER L'AJUT, una vegada més...

---

