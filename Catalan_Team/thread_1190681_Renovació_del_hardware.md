---
title: "Renovació del hardware"
date: 2009-06-18
forum: Catalan Team
---

### Post by pixatintes on 2009-06-18
Bon dia,

Tinc un dubte, a veure si algú de vosaltres s'hi ha trobat o en sap quelcom.

M'han demanat d'actualitzar el Hardaware d'un ordenador que serveix de servidor en una petita xarxa d'ordinadors (7 o 8 ).
Aquest actualment és servidor d'arxius (amb 4 HD) i impressió (SAMBA,CUPS), i disposa de 2 o 3 serveis d'accés web.
El servidor funciona amb un Ubuntu Hardy (8.04) sense entorn gràfic.

La configuració de tot el sistema tal com està, des de cero és una feinada de collons.

La meva pregunta és: Si canvio placa i micro, el sistema ho detectarà? em donarà un KERNEL PANIC? hi ha alguna forma de que funcioni?

El hardware actual és un P4 a 2.8Ghz (s. 478) i podria posar-hi algun un C2D (s. 775).

Amb entorns windows, el canvi de hardware no solia funcionar.. però amb sistemes linux no ho he probat mai.

Gracies per endavant,
pixatintes

---

### Post by papapep on 2009-06-18
> Si canvio placa i micro, el sistema ho detectarà? em donarà un KERNEL PANIC? hi ha alguna forma de que funcioni?

Això és impossible de contestar amb certesa completa. Si el maquinari no és extremadament modern o estrany, t'hauria de funcionar, jo ho he fet molts cops. Tot i això seguretat completa no es té mai o sigui que, considerant que estàs parlant d'un servidor productiu, és clar que hauries d'efectuar totes les proves possibles abans d'efectuar el canvi real.
A banda d'això, no sé del pressupost que disposes, al preu que van actualment les màquines crec que seria bastant més recomanable comprar un servidor sencer nou, no només la placa. I això, a més, et permetria més marge en la migració. Jo ho orientaria així.

---

### Post by indiosincracia on 2009-06-18
A mi també hem va funcionar però no és cap garantia, si parlem de la mateixa arquitectura, el cpu i tarja de vídeo no afecta a l'engegada si el kernel detecta el hardware, es pot obtenir un kernel pànic si les particions han canviat d'ordre, la bios i els discs durs han d'estar en la mateixa situació que estaven abans.

El haselfrog queda descartat, la pantalla blava la tens assegurada.

---

### Post by ilku on 2009-06-19
Tal com diu en Papapep, en principi no hi ha d'haver cap problema. Jo ho he fet diverses vegades i no he tingut mai cap problema. Ara bé, seguretat davant de tot, i mes si és productiu (copia de seguretat de tot, d'entrada).

Et recomano al igual que en Papa :) un de nou, si per alguna raó no pots convèncer al comptable, llavors pots utilitzar un pc vell per utilitzar-lo  com a servidor mentre fas el canvi, copiant tota la info i les configuracions, així pots treballar tranquil·lament. Una altre opció és treballar el cap de setmana :lolflag:.

---

### Post by pixatintes on 2009-06-19
Primer de tot, gracies a tots per les respostes.
La veritat és que només de saber que pot funcionar, ja val la pena probar-ho. 
El tema de canvi de placa o nou servidor tampoc m'importa massa, si no em detecta bé el hardware i haig de començar de 0, la feina grossa la tindré configurant-lo. Encara que sempre és millor muntar-ne un, amb la tranquilitat que l'altre no l'has de tocar i segueix funcionant.

Pel que tinc entès, i corregiu-me si m'equivoco, des de fa un temps el kernel d'ubuntu és generic pel que encara que la placa tingués un chipset diferent o una arquitectura diferent de CPU (p.e.: p4 -> AMD2) no tindria pq donar un kernel panic, oi? Només en el cas com indica el papapep que el hardware fos molt nou o estrany i no estès suportat pel kernel.

I una última qüestió, sobre discs durs i particions. 
Abans quan fstab funcionava en relació a les direccions (hdX,X), el muntatge de discos podia varia en funció de la connexió física d'aquests.
Ara que el muntatge dels discos va en relació al 'uuid', aquest no varia en funció de la connexió? Encara que sigui Sata, Ata, placa o controladora.
O sigui que, si el munto els discos en un nou servidor mentre li doni el Boot al disc correcte, la resta s'haurien de muntar correctament.

Gracies per endavant,
pixatintes

---

### Post by papapep on 2009-06-19
> El tema de canvi de placa o nou servidor tampoc m'importa massa, si no em detecta bé el hardware i haig de començar de 0, la feina grossa la tindré configurant-lo

Si t'informes bé abans de la compra de les experiències d'altres amb el maquinari que vols comprar, t'estalviaràs molts de mals de cap.
I que no et detecti directament el maquinari (depèn de quin, clar) no implica que ho hagis de configurar tot de cero. Pot voler dir que et portarà feina configurar el maquinari o, en casos extrems, que no et funcioni mai, però el programari és més que possible (per no dir probable), si fas el que cal, que no hagis de repetir la configuració. També depèn de en quina versió el tinguis, quina vulguis fer servir ara, etc., punts que no has comentat.

> Abans quan fstab funcionava en relació a les direccions (hdX,X), el muntatge de discos podia varia en funció de la connexió física d'aquests.
Ara que el muntatge dels discos va en relació al 'uuid', aquest no varia en funció de la connexió? Encara que sigui Sata, Ata, placa o controladora.

L'únic que hauràs de fer és averiguar l'uuid dels discs i adaptar l'fstab, res més.

Però, insisteixo, si t'ho pots permetre, munta un servidor nou sencer, t'ho auto-agrairàs durant molt temps :)

---

### Post by pixatintes on 2009-06-20
Gracies papapep per la resposta.

El tema de la compatibilitat ja ho tinc clar que hi haig d'estar el cas. Ja m'ha pasat més d'una vegada, muntar quelcom i trobarme sense drivers.. :D

Sobre la versió, > **pixatintes said:**
> 
El servidor funciona amb un Ubuntu Hardy (8.04) sense entorn gràfic.

Sempre hi deixo la versió LTS en aquests equips.

El que volia dir amb la feinada, és que s'ha de deixar exactament com igual com està pq tot segueixi funcionant sense problemes.
Per tant que m'estalviaria una feinada de por si pogués muntar els discos actuals al nou servidor o canviar placa i micro i no petes tot amb un KERNEL PANIC. D'aquí la qüestió inicial i la del fstab.

Crec que agafaré un cap de setmana i probaré de fer el canvi a veure que. 
De totes formes segons les vostres respostes tinc forces números pq funcioni xDD a veure si tinc sort.

Fins ara,

---

