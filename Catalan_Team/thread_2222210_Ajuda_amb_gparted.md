---
title: "Ajuda amb gparted"
date: 2014-05-05
forum: Catalan Team
---

### Post by JUSTERINI1 on 2014-05-05
Hola Ubuntuaires,
Necessito més espai a la partició Ubuntú, però al ser una partició extesa no me la deixa ampliar i us agraïria consell, en base al lio de particions que tinc i que us adjunto en la captura de pantalla.
La meva segona opció era copiar la partició sda5 a l'espai no assignat de 92Gb, espai suficient pel que necessito, però em diu que ja he superat el màxim de 4 particions primàries.
Gràcies per la vostra opinió i ajuda.

Salutacions

Justerini

---

### Post by wgarcia on 2014-05-06
Em sembla que sí que podries incrementar la mida de la partició /dev/sda3, perquè tens espai abans d'ella. Serà super lent perquè s'hauran de moure totes les dades cap a l'inici del nou espai, i això pot trigar moltíssim, però jo no veig cap problema perquè el gparted ho faci. 

Suposo que ho estàs fent des d'un USB o CD autònom (un "live" amb el qual inicies l'ordinador), oi? Perquè òbviament no ho pots fer si tens la partició muntada. 

En tot cas és super important que facis còpia de totes les dades perquè no hi ha manera més fàcil de perdre totes les dades que fer manipulacions a les particions. No necessàriament ha de passar, però més val prevenir-se.

---

### Post by JUSTERINI1 on 2014-05-08
Hola Wgarcia, 
No puc augmentar cap a la esquerra de dev/sda3, em diu que no puc sobreposar particions (overlapping)...no sé què fer i estic a punt de llençar la tovallola.
Estic executant el gparted des d'un livecd, sense muntar cap partició.

Gràcies per la teva ajuda, com sempre.

Justerini.

---

### Post by wgarcia on 2014-05-08
Prova de remoure primer la partició swap, intenta fer la manipulació de particions, i després la tornes a crear. Potser el fitxer swap està muntant el seu swap en aquesta partició.

---

