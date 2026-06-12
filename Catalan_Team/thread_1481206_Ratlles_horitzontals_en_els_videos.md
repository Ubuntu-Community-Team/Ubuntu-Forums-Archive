---
title: "Ratlles horitzontals en els videos"
date: 2010-05-12
forum: Catalan Team
---

### Post by albertdelleida on 2010-05-12
Hola a tots i totes,

sóc un usuari d'Ubuntu novell (des de fa un mes) i aquest és el primer problema que no he pogut solucionar:

Quan reprodueixo arxius .avi, en les escenes ràpides o d'acció, quan la càmera es mou molt, quan hi ha canvis de plans molt ràpids o en escenes que apareixen molts elements,  m'apareixen unes ratlles horitzontals a la pantalla. Tan se val si reprodueixo l'arxiu en pantalla completa o en una finestra, sempre passa igual.

He provat de tot i no me'n surto. He provat amb diferents reproductors (Totem, Totem-xine, VLC...) i aplicant les opcions d'entrellaçar. He provat canviant la configuració del Compiz "General/Display Settings/sincronitza amb l'enfosquiment vertical". Ho he provat desactivant tots els efectes visuals.

També m'he baixat tots els paquets de còdecs disponibles (tant els lliures com els no lliures).

També he provat d'actualitzar els drivers de la meua targeta gràfica (tinc una ATI Mobility Radeon HD 3400). També he provat amb els drivers d'ATI lliures i tampoc res. Quan comprovo l'acceleració gràfica de la targeta tot em surt correcte:

[I]"albert@albert-laptop:~$ glxinfo | grep direct
direct rendering: Yes
albert@albert-laptop:~$ glxgears
18965 frames in 5.0 seconds
17798 frames in 5.0 seconds
19685 frames in 5.0 seconds
28590 frames in 5.0 seconds"[/I]

I res... no hi ha manera. Per descomptat he comprovat que els arxius .avi no estiguessin danyats i a l'obrir-los en "Windows" no hi ha cap mena de problema.

He buscat per fòrums, pàgines web, guies... i res de res... Siusplau, us agraïra molt que m'ajudéssiu amb aquest petit problema perquè estic molt content d'haver fet el pas a l'Ubuntu i no m'agrada gens haver d'usar el Windows per a poder visualitzar bé els arxius .avi

La meua versió d'Ubuntu és la 9.10

Gràcies per avançat!

---

### Post by Black_02 on 2010-05-12
Hola Albert,

Això a mi també em passava fins que vaig instal·lar la versió 10.04, hauries de fer una instal·lació neta, és a dir des de 0 i una vegada instal.lat, **no** instal·les cap driver ATI, ja que el sistema ja porta els drivers oberts integrats, al principi el sistema et dirà que hi han drivers restrictius disponibles, però no els has d'instal·lar, ja que si ho fessis tornaries a veure les ratlles horitzontals.

La veritat és que la versió 10.04 és molt millor que la 9.10, jo de tu l'actualitzaria, val la pena, això sí, fent una instal·lació neta. T'asseguro que el problema et desapareixerà.

---

### Post by albertdelleida on 2010-05-12
Moltes gràcies per contestar-me tan ràpid Black_02!

De fet he estat pensant en instal·lar-me la versió 10.04 però com que justament ha sortit quan acabava de configurar tot el SO pensava en instal·lar-me-la dintre d'unes setmanes. Ara ja veig que realment val la pena fer-ho. 

Sobre el tema de fer una instal·lació neta, la veritat és que tinc uns dubtes. Com ja he comentat sóc molt nou en aquest món i quan vaig instal·lar l'ubuntu 9.10 vaig fer l'instal·lació automàtica (no em veia capaç de fer una instal·lació manual la primera vegada) i clar... ara no sé com esborrar l'ubuntu 9.10 i instal·lar el 10.04. Buscaré una mica, a veure si tinc sort!

Merci per tot! :)

---

### Post by SiscoGarcia on 2010-05-12
El tema de les instal·lacions netes o de les actualitzacions és una discussió eterna amb defensors i detractors d'ambdues opcions. A mi l'actualització m'ha funcionat sempre bé, i per tant te la recomano; si més no, sempre pots fer una instal·lació neta després ;)

Per fer-la només cal que tinguis actualitzat el sistema, i si el gestor d'actualitzacions no t'ofereix la possibilitat d'actualitzar-te a la 10.04, només has de prémer les tecles Alt + F2 simultàniament i a la caixa de diàleg que s'obre escriure-hi «update-manager -d», llavors t'ho proposarà.

Prova-ho així i si no n'estàs content en parlem més endavant.

---

### Post by albertdelleida on 2010-05-13
Hola SiscoGarcia!

Pel que he anat llegint aquest sembla un tema (instal·lacions netes/actualitzacions) de debat força interessant. 

He estat indagant una mica més per la xarxa i crec que m'arriscaré a fer una instal·lació neta amb el mode avançat. Ho dic, més que res, perquè al ser la primera vegada que he usat l'Ubuntu he anat provant cosetes (moltes d'elles via la "Terminal") i és més que probable que hagi tocat coses que no hauria d'haver tocat. Ara, com que ja n'he aprés una miqueta més, intentaré no fer tantes provatures i així tenir l'Ubuntu més "net". 

Ja tinc el CD d'instal·lació de l'Ubuntu 10.04 i em disposo a fer l'instal·lació, a veure com me'n surto. Ja us ho comentaré :P

Moltes gràcies per tots els consells que m'esteu donant, s'agraeix molt!

---

### Post by albertdelleida on 2010-05-13
[LEFT]Ja està! Ja ho he aconseguit! Tinc l'Ubuntu 10.04 instal·lat i el problema amb la reproducció dels arxius .avi s'ha sol·lucionat. Ara toca personalitzar una mica l'entorn i a continuar gaudint de l'Ubuntu! :)
[/LEFT]

---

