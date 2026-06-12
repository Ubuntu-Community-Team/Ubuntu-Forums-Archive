---
title: "No apareix la opció per instal·lar l'Ubuntu mantenint els altres sistemes operatius"
date: 2011-01-09
forum: Catalan Team
---

### Post by Aljullu on 2011-01-09
Hola, m'he baixat l'Ubuntu 10.10 Live USB i volia instal·lar-lo, el problema és que en fer la instal·lació, al pas que toca fer les particions, no m'apareix l'opció que m'hauria de permetre fer més petita la partició de Windows i instal·lar l'Ubuntu a l'espai lliure.

És a dir, només m'apareixen l'opció d'esborrar tot el que hi ha ara al disc i la de manipular les particions manualment (cosa que no sé com es fa).

Us adjunto una captura de pantalla com a prova:
[[img]http://www.freeimagehosting.net/uploads/c4481f3091.png[/img]](http://www.freeimagehosting.net/)

Quan, si tot anés bé, m'hauria d'apareixer això: [http://www.ubuntu.com/sites/default/files/active/maverick/install_03_medium.jpg](http://www.ubuntu.com/sites/default/files/active/maverick/install_03_medium.jpg)

Actualment a l'ordinador hi tinc instal·lat el Windows 7. Si selecciono l'opció de manipular manualment les particions, m'apareix el següent mapa:
[[img]http://www.freeimagehosting.net/uploads/a72723401c.png[/img]](http://www.freeimagehosting.net/)

De l'anterior imatge no entenc res.

Sabeu perquè passa això? Pot ser que tingui a veure amb el fet que és un Live USB i no un Live CD? O potser és per com em van vendre l'ordinador? (el noi de la botiga em va dir que el Windows 7 estava instal·lat en una mena de partició)

Moltes gràcies!

---

### Post by oriolsbd on 2011-01-09
Jo crec que el problema és que en el disc ja tens quatre particions primàries, i aquest és el màxim a què es pot arribar. Tampoc no pots crear particions lògiques, perquè necessitaries crear una partició extesa on incloure una o més particions lògiques, però no es pot pel mateix motiu. Per això la instal·lació no et dóna l'opció de mantenir el que ja tens.

És molt estrany perquè tens una partició primària creada de 104MB (la sda1) que no sé quina utilitat deu tenir. També tens la sda4 de 1GB. Jo suposo que la partició de recuperació que t'han comentat deu ser la sda3.

Salut!

Oriol.

---

### Post by wgarcia on 2011-01-10
Estic d'acord, algunes instal·lacions de Windows 7 venen ara amb particions separades per al sistema i per a les dades, i si a més el disc compta amb una partició d'utilitats instal·lades per l'empresa productora de l'ordinador, i una altra de recuperació de Windows, això fan 4 particions. 

Si vols conservar el Windows la clau estriba en unificar les particions de sistema i de dades de Windows, cosa que suposo que es pot fer des d'aquest sistema operatiu, i després eliminar la partició on tenies la part de dades de Windows per alliberar una partició i aquí crear una partició lògica que et permetrà crear totes les particions que vulguis de linux.

---

### Post by falsospam on 2011-01-13
A mi hem va passar quelcom i el problema es del Windows que no el tens desfragmentat per tant encara que tinguis espai buit el tens dintre de les dades i Ubuntu no pot alliberar-ho   :) espero que estiguis en el mateix cas ja ens ho comentaras.

---

### Post by akyra on 2011-01-14
Bé,jo amb Windows Vista em pasava una cosa semblant, tenia 4 particions, has de carregar-te la "sda4" com ja ha dit wgarcia guardant les dades abans. El que vaig fer i va anar bé és:

1.- Guardar dades que singuin importants en un altre disc (per si acàs).
1.- Desfragmentar el disc de windows.
2.- Reduir la partició de windows (sda2) al tamany que necessitis, depenent de si vols seguir utilitzant windows i instal·lant programes.
3.- Moure la partició "sda3" a continuació de la sda2.
4.- Convertir la "sda4" en partició extesa (es perderan les dades).
5.- Crear les 3 particions per Ubuntu.

Crec que es important mirar si valen per alguna cosa les dades del "sd4", suposo que és per recuperar el sistema.

També podries esborrar la "sd3" i moure la "sd4" i fer el mateix.

Ja diràs.

Adeu

---

### Post by Aljullu on 2011-01-17
Moltes gràcies a tots per les respostes.

Com dieu, la partició sda3 serveix de recuperació del Windows (a la finestra Ordinador del Windows 7 m'apareix com a Recover (D: )). El que segueixo sense entrendre és què són la sda1 i la sda4 i què passarà si les esborro.

A la finestra d'Ordinador també m'apareixen dues coses que potser hi estan relacionades perquè no entenc que són:
[[img]http://www.freeimagehosting.net/uploads/36f4f0d0c2.png[/img]](http://www.freeimagehosting.net/)
1. **Microsoft Office 2010 (Protected) (Q: )**: quan hi intento entrar em diu:
"La ubicació no està disponible

Q:\ no està accessible.

Acceso denegado."

Podria ser que fos una de les particions? A les propietats em diu que ocupa 0 bytes.

2. **BullGuard Online Drive**: no entenc què hi pinta això aquí (el BullGuard és un antivirus), però què vol dir que estigui com a "Un altre" i no a "Unitats de disc dur" o "Dispositius amb emmagatzematge extraïble"? Quan hi intento entrar em diu que m'he de registrar primer.

Moltes gràcies a tots per l'ajuda. Ara m'estic instal·lant l'Ubuntu a través del Wubi, però m'agradaria fer-ho en una partició perquè el rendiment és millor.

---

### Post by wgarcia on 2011-01-17
A la /dev/sda1 poden haver-hi algunes utilitats posades pel fabricant de l'ordinador que els serveixen de diagnosi si es presenta algun problema de maquinari. Almenys els Dell fan això.

---

### Post by Aljullu on 2011-07-23
Ep, sento haver tardat tant en respondre. Vaig estar un temps utilitzant l'Ubuntu a través del Wubi i fa poc, al final, el vaig instal·lar esborrant la partició sda4 amb el Gparted i després fent la instal·lació normal.

De moment tot funciona perfectament.

Gràcies a tots per les respostes!

---

