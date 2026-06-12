---
title: "l'ubuntu ha petat"
date: 2015-07-25
forum: Catalan Team
---

### Post by josep-maria on 2015-07-25
Quan estava actualitzant l'ubuntu, s'ha aturat tot, la pantalla ha quedat congelada i només he pogut fer que tallar la corrent i tornar a engegar. Llavors la pantalla era negra i sortia un GRUB>. I d'aquí no el treies, fessis com fessis. He intentat tornar a ficar-hi els discos dels ubuntus antics descarregats d'internet, però no feia res. Al final ha acceptat el disc de l'ubuntu 9.04, que em van enviar per correu, sense esborrar cap sistema operatiu dels que tenia. Ara quan engego el pc, pregunta quin sistema operatiu vull:

ubuntu 9.4
3.2.0-88
3.2.0-87
3.2.0-86
3.2.0-85

Suposo que el 3.2.0-88 és l'ubuntu que tenia fins ara, però no sé quin era. Si el trio, no fa res. Sí que funciona el 3.2.0-87, que és l'ubuntu 12.04. I encara gràcies que no s'ha esborrat cap arxiu dels meus. El processador és un intel celeron. Podria ficar-hi l'ubuntu 14.04, esborrant tot allò que hi ha, però no vull perdre l'escriptori gnome. Ja em sembla bé continuar amb l'ubuntu 12.04, però suposo que cal esborrar tots els sistemes operatius que no faig servir. Com ho puc fer?

---

### Post by wgarcia on 2015-07-26
Sempre convé tenir una còpia de seguretat dels fitxers d'usuari, tot i que no tinguem cap problema amb l'Ubuntu o qualsevol altre sistema operatiu que estem utilitzant, pot fallar un disc o la placa mare de l'ordinador i impedir-nos accedir a les nostres dades. 

Dit això, no sé a quina versió et refereixes quan dius "Ubuntu 9.4", pot ser la 9.04? Aquesta és una versió molt antiga ja totalment fora de manteniment. Per eliminar-la, hauries de desinstal·lar el nucli corresponent a aquesta versió. Una manera de fer-lo és instal·lar (si no ho tens) el programa de gestió de paquets "synaptic":
```
sudo apt-get install synaptic
```

Un cop que inicies aquest programa et sortirà una pantalla on et mostra tots els programes, tant els que tens instal·lats com els disponibles per instal·lar. Hi ha un lloc per buscar paquets, i a aquest lloc has d'entrar "linux". Et sortiran molts paquets, però has d'anar recorrent la llista i aquí pots marcar els paquets que vols desinstal·lar. Hauries de buscar els paquets corresponents al nucli que vols desinstal·lar (haurà de ser diferent a aquests que menciones que tenen número
3.2.0-88, 3.2.0-87, 3.2.0-86, 3.2.0-85 i si realment allò que dius de versió 9.4 és la 9.04 serà una versió 2.x.x, es a dir començant per 2). Si identifiques aquest nucli que vols desinstal·lar i cliques amb el botó dret a la línia corresponent, veuràs que tens opcions per "marcar per desinstal·lar completament", has de marcar aquesta opció. Normalment hi ha tres paquets per a cada nucli, de memòria: linux-image, linux-image-extra i linux-headers, has de desinstal·lar els tres.

Un cop que el synaptic acabi de desinstal·lar aquests paquets, un cop reinicies el sistema, al grub t'hauria de sortir únicament els nuclis que estiguin instal·lats, és a dir hauria de desaparèixer aquesta versió 9.4 que dius.

---

### Post by josep-maria on 2015-07-29
He fet això de apt-get synaptic, però no ha fet res. 
He pogut trobar el synaptic a aplicacions>einesdelsistema>administració.
Hi he cercat "linux".
Han sortit un milió de paquets, però he pogut trobar-ne un que diu 3.2.0.88.102.
He fet clic a un quadret que hi ha per marcar-lo. 
He fet clic al botó de la dreta, però al menú que surt no em deixa fer clic on diu "marcar per a eliminar completament".

---

### Post by wgarcia on 2015-07-29
El quadradet que hi ha a la dreta està verd? Si està en blanc és que el paquet en qüestió no està instal·lat, però si et surt al grub hi haurà algun paquet de nucli (que comença amb linux del tipus que et comentava a dalt) que tingui versió 2.x.x, els que venien amb el Linux 9.04 que entenc que vas instal·lar.

---

### Post by josep-maria on 2015-07-29
Ja he trobat el quadret, és a l'esquerra del nom del paquet. N'hi han de blancs i de verds. He cercat tots els que es deien 3.2.0-88 i que tinguessin el quadret verd, els he marcat per a eliminar, i he fet clic a "aplicar". M'ha dit que els ha esborrat, llavots he reengegat el pc. Però a la llista de sistemes operatius torna a sortir el 3.2.0-88, com si no hagués fet res. 

A la llista de paquets del synaptic ja no hi són els que tenien el quadret verd, però n'hi ha un munt que es diuen 3.2.0-88 i que tenen el quadret blanc.

---

### Post by wgarcia on 2015-07-29
És que aquests no és els que hauries d'eliminar, sinó quelcom que comencí amb un número de versió amb 2, que serà el que correspondrà a la versió 9.04. Els que comencen amb 3 són els que et funcionen, i el que no es va eliminar és segurament el que estàs fent servir. Si elimines el nucli que estàs fent servir no podries tornar a engegar el sistema.

---

### Post by josep-maria on 2015-07-29
La versió que s'ha espatllat és la que surt com a 3.2.0-88, que és la que voldria esborrar (ara ja no puc saber quin ubuntu és perquè no s'engega). 
Per engegar el pc, haig de triar la següent més antiga, que és la 3.2.0-87, que és l'ubuntu 12.04, que sí que funciona. 
L'ubuntu 9.04 també funciona, per tant, pensava esborrar-la després de la que no funciona.

---

### Post by josep-maria on 2015-07-30
Si pogués canviar l'ordre dels sistemes operatius que surten quan engego el pc, ja en tindria prou.
Vull dir, posar el 3.2.0-87 a dalt de tot. Hi han uns quants commands, però no n'he trobat cap que ho faci. Tampoc no he gosat tocar gaire.

---

### Post by wgarcia on 2015-07-30
Això es podria fer ficant-li mà als fitxers de configuració del grub, però jo no ho recomanaria. Perquè no mires a veure si trobes al synaptic els paquets de linux amb versió que com comencen amb 2 i que estan marcats amb verd i els intentes desinstal·lar? Sols els que tenen noms que comencen amb  linux-image, linux-image-extra i linux-headers.

---

### Post by josep-maria on 2015-07-30
He esborrat al synaptic dos paquets que tenien la "versió insta&#320;lada"  = 2...:
linux-image-2.6-38-11-generic
linux-image-2.6.32-25-generic

No n'hi havia cap de linux-header ni de linux-image-extra que tingués la versió insta&#320;lada = 2...
He tornat a engegar el pc i ha tornat a sortir la mateixa pantalla de triar el sistema operatiu, amb el linux 9.04 a dalt i a continuació el 3.2.0-88. 

L'ubuntu 9.04 no importa que hi sigui perquè funciona bé. El que cal esborrar és el 3.2.0-88, que és l'ubuntu que es va desfer quan s'actualitzava. Si no es pot esborrar, no faré res, perquè si hi fiqués l'ubuntu 14.04, perdria l'escriptori gnome, i això no ho vull pas.

---

### Post by josep-maria on 2015-07-30
He esborrat al synaptic dos paquets que tenien la "versió insta&#320;lada"  = 2...:
linux-image-2.6-38-11-generic
linux-image-2.6.32-25-generic

No n'hi havia cap de linux-header ni de linux-image-extra que tingués la versió insta&#320;lada = 2...
He tornat a engegar el pc i ha tornat a sortir la mateixa pantalla de triar el sistema operatiu, amb el linux 9.04 a dalt i a continuació el 3.2.0-88. 

L'ubuntu 9.04 no importa que hi sigui perquè funciona bé. El que cal esborrar és el 3.2.0-88, que és l'ubuntu que es va desfer quan s'actualitzava. Si no es pot esborrar, no faré res, perquè si hi fiqués l'ubuntu 14.04, perdria l'escriptori gnome, i això no ho vull pas.

---

### Post by wgarcia on 2015-07-30
Potser tingui algun altre nucli començant amb 2.x.x.x, per això es veu encara l'Ubuntu 9.04. Quant al 3.x.x.x que vols eliminar, si el trobes i l'elimines al synaptic es deixarà de veure. 

Per tenir l'escriptori Gnome amb l'Ubuntu 14.04, el que pots fer és mirar d'instal·lar una versió que es diu Ubuntu Mate, aquesta versió porta l'escriptori Gnome. El pots baixar de:

[https://ubuntu-mate.org/trusty/](https://ubuntu-mate.org/trusty/)

---

### Post by josep-maria on 2015-07-31
He fet una cerca al synaptic i no hi ha cap paquet que es digui 3.2.0-88 i que tingui cap versió insta&#320;lada. Suposo que és perquè ja els vaig esborrar. Tal com dius, no tocaré el grub, ni tampoc no tocaré res més perquè encara faré una desgràcia. Molt agraït. A reveure.

---

