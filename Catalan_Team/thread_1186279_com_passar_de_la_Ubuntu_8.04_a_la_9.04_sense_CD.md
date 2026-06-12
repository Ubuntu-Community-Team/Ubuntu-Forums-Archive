---
title: "com passar de la Ubuntu 8.04 a la 9.04 sense CD"
date: 2009-06-13
forum: Catalan Team
---

### Post by bikerbaixcamp on 2009-06-13
Bones!

Vaig provar el cd-live de la 9.04 i en el moment de fer la live posa "loading please wait" i es queda penjat.. no continua cap al logo de l'Ubuntu amb la barra a sota de càrrega. 

La cosa és que si vull fer l'actualització des del gestor d'actualitzacions em diu si vull instal·lar la Ubuntu 8.10; i no vull instal·lar la 9.04. 

Com ho puc solucionar, gràcies!

;)

---

### Post by PatrickVogeli on 2009-06-13
si vols fer una actualitzacio has d'anar primer a la 8.10... Si no pots tenir problemes.

Si encara i així ho vols provar, has d'editar l'arxiu /etc/apt/sources.list i canviar Hardy per Jaunty a tot arreu. Despres sudo apt-get update && sudo apt-get dist-upgrade

No t'ho recomano però.

---

### Post by akyra on 2009-06-15
En la versió del 8.10 també vaig tenir problemes amb el live CD, simplement estava el CD mal gravat.

Baix tornar-me a baixar-me una nova imatge de la distribució i vaig tornar-ho a grabar  i va arrancar bé, i el vaig poder instal·lar.

Amb la 9.04 a la primera m'ha anat bé.

L'altra opció seria fer un USB d'arranc.

També si probes a instal·larte la 9.04 podries aprofitar per fer un sistema d'arxius ext4 que funciona més ràpid.

Adeu.

---

### Post by bikerbaixcamp on 2009-06-15
Tindré en compte tot això, gràcies.

No, no passaré directe ja que si dius que pot ser perillós ;)

I bé, pel que fa al cd, ho he provat en un ordinador d'una amiga i si que va el cd live; per tant dubto que sigui del cd, òbviament.

De moment no faré res que no tinc temps, però d'aquí una setmana intentaré passar de la 8.04 a la 8.10 i després a la 9.04 o bé si algú té alguna idea millor; i saber com em pot funcionar el cd de la live 9.04.

Salut!

---

### Post by akyra on 2009-06-16
En el meu cas no era el CD, sino el reproductor.

Sort,

---

### Post by bikerbaixcamp on 2009-06-30
Bones!

Males notícies, estic escrivint des d'un cd live.

Doncs bé, com em vau recomanar (i la lògica diu) doncs avui he actualitzat de la 8.04 a la 8.10 i tot correcte. He entrat a la 8.10 i tot anava aparentment bé. 
Doncs bé, al final de la tarda li he dit que m'instal·les (amb el gestor altre cop) la 9.04; el procés semblava tot correcte, ha arribat al final. Al reiniciar... merda... fa lo mateix que amb el live cd del 9.04 (ho vaig provar a casa d'una amiga i anava bé). Doncs al "loading please wait" es queda penjat i l'ordinar no reacciona ni fa sorolls ni res de res.. Un fet curiós.

Doncs bé, la meva pregunta és com ho puc arreglar. I les possibles solucions a que aspiro es:
- Poder arreglar d'alguna manera aquest problema i que vagi amb 9.04.
- Tornar un pas enrera, avui a la tarda a la 8.10, i quedar-me amb ella sense haver perdut res, que ja m'estaria bé.

Com s'arregla això?

Moltes gràcies! ;)

---

### Post by bikerbaixcamp on 2009-06-30
Noves notícies!!

Estic a la 9.04. A veure...

He provat de posar-me dins el GRUB quan s'inicia l'ordinador. Doncs bé, la kernel que està per defecte és la tal-tal-tal 13, d'acord. Doncs aquesta és la que dic que es queda fixa. He provat amb la 24 i comença a fotre's paranoies amb les X i surt mode gràfics bàsics vaja que malament; i després he provat la kernel 14 que si que va i és aquesta. 

Per tant, m'agradaria saber l'explicació per curiositat. I després com borrar o be fer que la kernel 14 sigui la per defecte. Després també quan actualitzi "normal" i actualitzi la kernel passarà alguna cosa? 

Vaig a dormir que és molt tard, salut!

---

### Post by quitus on 2009-07-01
En altres fils, s'explica com editar el /boot/grub menu.lst per aconseguir això que vols. Però si no tens ganes de editar-lo directament, pots fer servir una aplicació anomenada startup-manager que et permet editar-ho de manera gràfica.

L'explicació de tot plegat la desconec, suposo que no deu haver només una causa per provocar això mateix, com segur més d'una opció per poder sol·lucionar-ho. (que be que m'ha quedat)

Pots provar a tornar a instal·lar els drivers de la tarja gràfica.

salut

---

### Post by bikerbaixcamp on 2009-07-01
Gràcies, ja aniré provant això que dieu.

Si, realment és una mica curiós, i més tenint en compte que l'ordinador és nou, no té masses anys (any).

Salut!

---

