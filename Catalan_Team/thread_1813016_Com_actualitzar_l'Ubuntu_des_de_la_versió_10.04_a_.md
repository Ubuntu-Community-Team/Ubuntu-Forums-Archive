---
title: "Com actualitzar l'Ubuntu des de la versió 10.04 a 11.04 i no perdre's"
date: 2011-07-27
forum: Catalan Team
---

### Post by Pelacanyes on 2011-07-27
Bon dia a tothom
Després de l'ensurt que vaig tenir, he pensat que poder seria convenient actualitzar la versió que tinc de l'Ubuntu (actualment la 10.04) a la més recent. Però com que sóc un manasses, i no vull perdre l'informació que tinc a la maquina, voldria que em guiesiu en el procés a seguir.
Gracies per endavant pel vostre ajut
 
Salut
 
Pelacanyes

---

### Post by gunyoles on 2011-07-27
obre el terminal i tecleja

update-manager -d

llavors hauria de obrir-se el gestor d'actualitzacions. segueix el que et digui la pantalla

que vagi bé

---

### Post by akyra on 2011-07-28
Pots actualitzar, però jo no he tingut bones experiencies actualitzant, això depen de cada cas.

Jo reconomano fer una instal·lació neta només del sistema operatiu, això no et provocarà que perdis dades si tens el disc ben particionat ("/", "swap", "/home") i en poc més de mitja hora ho tindràs fet.
Després hauràs d'afegir les aplicacions que et faltin i els dispositus externs si no els troba per defecte(impressora, scanner, etc.).

També crec que abans de fer-ho pots provar amb el liveCD ver veure si et reconeix les targes de xarxa, só, video, que són les que et poden donar algun problema.

Espero que vagi bé.

Salutacions.

---

### Post by Pelacanyes on 2011-08-04
Bona tarda a tothom:
Perdoneu que no hagi dit res abans, problemes mèdics m'han tingut uns dies desconectat.
Us poso una mica en antecedents. El disc dur es de 160 Gb aprox. i només te una partició. Donat els problemes que em va ocasionar l'última actualització, penso que la solució plantejada per Akyra serà la més adient.
Ara el meu dubte es com puc fer les particions que dieu i perquè serveixen cadascuna. Suposo que això s'ha de preparar abans de fer l'actualització.
Gracies de nou per la vostre ajut
Salut
 
Pelacanyes

---

### Post by akyra on 2011-08-05
Hola Pelacanyes,

Com tens les particions actualment? Intantariem poder aprofitar-les, si es posible.

Amb el disc que tens tu i si només vols tenir Ubuntu faria el següent repartiment de particions:
  "/" : 15Gbytes (més que suficient), és la partició a on tindrem el sistema operatiu (Ubuntu).
  "swap" : El tamany depen de la meròria RAM que tinguis. En sistemes vells (menys de 2GBytes de RAM) es posava dos vegades la RAM, actualment en que posis el mateix que la RAM ja fariem prou. Això ens serviria en cas de que suspenguesim o hivernesis l'ordinador.
  "/home": La resta del disc. És la partició a on es crearan les carpetes d'usuaris i a on es guardaran les seves dades.

És podem fer moltes més particions, però normalment no cal.

Et recomano abans de res que provis l'Ubuntu 11.04 amb el live CD per veure que tot en funciona amb condicions (tarja de xarxa, wifi, tarja gràfica, so, etc.).

Qualsevol cosa, aquí estem.

Salutacions.

---

### Post by Pelacanyes on 2011-08-05
Hola de nou:
De particions, que jo sapigue, només n'hi ha una i tot està posat dintre (sistema operatiu i arxius propis). De memoria RAM crec que es 1 Gb.
Com se fa per fer les particions?
Gracies pel vostre ajut
Salut.
 
Pelacanyes

---

### Post by akyra on 2011-08-05
Perdona Pelacanyes, no havia vist que tenies només una partició.

Així ho hem de refer del tot.

De la carpeta de cada usuari copiat els arxius que siguin importants en un disc extern, ja que quan formategem es perdran totes les dades.
De fet per intentar no perdre res, copia cada carpeta d'usuari sencera a un disc extern, amb això vull dir també els fitxers i carpetes ocultes. Per veure-les fes CTRL+h.
Amb això haurem guardat arxius i carpetes de configuració de les aplicacions que estiguis utilitzant i les dades de cada usuari.

Per la instal·lació d'Ubuntu pas a pas hi ha bastantes guies, i em sembla recordar que aquí en el forum sempre hi ha una darrera versió.

Bàsicament és seguir els pasos que t'indiquen i quan arribes al formatejat elegeix format manual i així podràs esborrar la partició actual i definir les noves particions.

Les particions "/" i "/home" formateja-les amb format "etx4" i la swap només li has de dir que és una partició d'intercanvi, però no s'ha de formatejar.
L'ordre de les particions per anar bé, ha de ser "/", swap i "/home".

Ja diràs.

Salutacions

---

