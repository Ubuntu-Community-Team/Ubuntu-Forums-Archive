---
title: "Problemes al instal·lar l'Ubuntu 7.10"
date: 2007-10-19
forum: Catalan Team
---

### Post by Aljullu on 2007-10-19
Hola, normalment no em passo per aquest fòrum, però com que estic veient que sou la millor manera (com a mínim la més ràpida i fiable segur) d'obtenir ajuda amb l'Ubuntu vinc per aquí.

He intentat instal·lar l'Ubuntu 7.10 sense èxit. Us explico:

Me'l vaig baixar i el vaig gravar en un CD. Avui m'havia disposat a instal·lar-lo. He post el CD, he anat al Live, i he apretat Install (com vaig fer amb el 7.04). Tot molt bé, el tema de particions m'he liat molt, havia guardat un espai lliure al disc per fer-hi la instal·lació, però no sé com es feia per dir-li «Crea una partició a l'espai lliure!» i después d'uns quants intents he agafat la primera opció, que em deia de redimensionar no sé quina partició i instal·lar-me l'Ubuntu amb 20 GB de memòria (el meu PC en té 160, i de lliure (sense cap partició en ells) en deu tenir poc més de 100). He seguit, i he arribat al punt d'instal·lació, allà s'ha anat omplint la barra fins que ha desaparegut sense avís.

He pensat que ja s'hauria instal·lat, he reiniciat (treient el CD) però segueixo tenint l'Ubuntu 7.04. No sé com fer-ho per instal·lar-lo. A un lloc diuen que el millor és fer primer les particions, en d'altres recomanen que t'ho faci dierectament el CD.

Us ensenyo ara com tinc les particions al meu PC:
[IMG]http://godlike.cl/up/im/8/001oefv.png[/IMG]
A la primera i tinc el Windows XP sense res (és a dir, només ocupa la mida de la seva instal·lació). A la /dev/sda2 tinc l'Ubuntu 7.04 i la /dev/sda5 és aquella que s'ha de tenir obligatòriment no?

Per tant: al instal·lar el 7.10 puc aprofitar el mateix "linux-swap" o n'he de fer un altre? Creo primer alguna partició ext3? O vaig directament amb el CD i ell sol en principi ja ho farà tot?

Moltes gràcies, a veure si em podeu ajudar, és que estic molt peix en això...

Si us falta alguna informació només digueu-m'ho que us la donaré.

També tinc un problema: no em reconeix Internet, em va passar el mateix amb el 7.04, però l'usuari "angelacebes" del Racó Català em va donar uns números (IP, DNS, màscara de subxxarxa, adreça de la passarel·la, etc.) per posar i tot em va funcionar, però ara els poso i no em surt. Tinc un router de Telefónica amb fil. Al "Paràmetres de xarxa" em diu que es diu: "Connexió per xarxa amb fil".

Moltes gràcies de bestreta.

---

### Post by jodufi on 2007-10-19
Hola Aljullu,

Veig que tens un embolic amb les particions. T'aconsello redistribuir-les d'aquesta manera utilitzant el gparted (que veig que coneixes) en mode Live (utilitzant el CD de l'Ubuntu 7.10):

· Elimina totes les particions que tens ara. Vale, si vols deixa sda1 amb el windows, però jo ja el tinc eliminat ;)

· Crea un "extended" amb tot l'espai lliure (unes 134 GB), a dins hi afegiràs les tres següents particions:

· Afegeix la partició que serà "/", aquesta tindrà 8 GB (més que suficient). El format de la partició serà "ext3"

· Afegeix una altra partició que serà la "swap" amb 1 GB. El format de la partició serà "linux-swap"

· I amb l'espai restat, creat una altra partició, que serà el teu "/home"

Aquesta és la distribució bàsica que s'acostuma a utilitzar en Linux. Així tindràs una partició pel programari (la "/"), una altra per la memòria (la "swap") i la de dades i configuracions d'usuari (la "/home").
D'aquesta manera podràs fer instal·lacions noves esborrant només el "/" i sense perdre les dades del "/home".

Un cop fetes les particions (sobretot, perdràs TOTES LES DADES, així que fes copies de seguretat) comença a instal·lar l'Ubuntu 7.10, però aquest cop li indicaràs tu quina serà la partició "/" i la "/home" de forma manual.

També pot deixar que t'ho faci manualment, però a mi no m'agrada ja que et posa el "/" i el "/home" en la mateixa partició (igual que el windows) però perds totes les avantatges de tenir separades les dades del sistema de les del usuari (que són més de les que t'he dit).

Pel tema de connexió a Internet, ho sento però no et puc ajudar.

Ja ens explicaràs com t'ha anat o si tens algun dubte.

---

### Post by Aljullu on 2007-10-20
Aquest vespre o tornaré a intentar, tot i això no em fa gaire gràcia esborrar la partició de l'Ubuntu 7.04, perquè si amb el 7.10 no tinc Internet...

Gràcies, de totes maneres ho intentaré ;-)

---

### Post by Aljullu on 2007-10-20
> **jodufi said:**
> Hola Aljullu,

Veig que tens un embolic amb les particions. T'aconsello redistribuir-les d'aquesta manera utilitzant el gparted (que veig que coneixes) en mode Live (utilitzant el CD de l'Ubuntu 7.10):

· Elimina totes les particions que tens ara. Vale, si vols deixa sda1 amb el windows, però jo ja el tinc eliminat ;)

· Crea un "extended" amb tot l'espai lliure (unes 134 GB), a dins hi afegiràs les tres següents particions:

· Afegeix la partició que serà "/", aquesta tindrà 8 GB (més que suficient). El format de la partició serà "ext3"

· Afegeix una altra partició que serà la "swap" amb 1 GB. El format de la partició serà "linux-swap"

· I amb l'espai restat, creat una altra partició, que serà el teu "/home"

Aquesta és la distribució bàsica que s'acostuma a utilitzar en Linux. Així tindràs una partició pel programari (la "/"), una altra per la memòria (la "swap") i la de dades i configuracions d'usuari (la "/home").
D'aquesta manera podràs fer instal·lacions noves esborrant només el "/" i sense perdre les dades del "/home".

Un cop fetes les particions (sobretot, perdràs TOTES LES DADES, així que fes copies de seguretat) comença a instal·lar l'Ubuntu 7.10, però aquest cop li indicaràs tu quina serà la partició "/" i la "/home" de forma manual.

També pot deixar que t'ho faci manualment, però a mi no m'agrada ja que et posa el "/" i el "/home" en la mateixa partició (igual que el windows) però perds totes les avantatges de tenir separades les dades del sistema de les del usuari (que són més de les que t'he dit).

Pel tema de connexió a Internet, ho sento però no et puc ajudar.

Ja ens explicaràs com t'ha anat o si tens algun dubte.
Hola, ara ho anava a fer, però he vist que hi ha una cosa que no sé fer.

Has dit que he de fer un extended i després, a dins, posar-hi particions. Com es fa això? S'ha de cerar una partició ext3? O és una altra cosa?

Molts gràcies.

---

### Post by papapep on 2007-10-20
El que no acabo d'entendre Aljullu, és si vols reparticionar el disc perquè realment vols, o ho fas per que et penses que per actualitzar cal refer les particions. Ja que com que dius que ja tens la Feisty instal·lada, ja tens les particions i els sistemes de fitxers fets...

---

### Post by Aljullu on 2007-10-21
> **papapep said:**
> El que no acabo d'entendre Aljullu, és si vols reparticionar el disc perquè realment vols, o ho fas per que et penses que per actualitzar cal refer les particions. Ja que com que dius que ja tens la Feisty instal·lada, ja tens les particions i els sistemes de fitxers fets...
Realment vull fer una instal·lació neta: l'actual Ubuntu 7.04 el tinc ja molt ple de "merda" (perdó per l'expressió) i m'agradaria fer una instal·lació nova. A part d'això he llegit que és millor fer una instal·lació neta que no actualitzar.

Tot i això ahir vaig provar d'actualitzar i igualment em va donar un missatge d'error, o sigui que també tindria problemes:confused:.

També m'interessaria reparticionar per poder fer això d'aïllar el /home.

Moltes gràcies.

---

### Post by papapep on 2007-10-21
Si, la swap és obligatòria, sinó quan tinguis tota la RAM ocupada se't bloquejarà el sistema. 
Al particionador es veu que tens un espai de 109 Gb sense fer servir. Pots crear una nova partició amb aquest espai i fer-la servir pel /home. No et caldria fer més.

---

### Post by jodufi on 2007-10-21
Hola Aljullu,

En la imatge que has enviat, si t'hi fixes apareix una partició extended i a dins hi tens el sda5.

L'extended serveix per posar-hi particions a dins, pq em sembla que si no estaries limitat a 3 o 4 (no ho recordo).

 Per fer-ho primer has d'esborrar les particions existents, crear l'extended i finalment a dins crear-hi les particions ext3 i companyia.

El papapep té raó, podries utilitzr la part amb 110GB com a /home i el sda2 con a /.
Jo el que et vaig recomenar era per poder aprofitar les 4 GB que tens penjades entre el sda2 i el sda5.

Salut

---

### Post by Aljullu on 2007-10-26
Aquest cap de setmana ho tornaré a intentar, fa&#341;e això d'aïllar el /home i posar-lo a tot l'espai lliure que tinc.

Llavors amb el CD de l'Ubuntu 7.10 esborrarré les particions del Ubuntu 7.04 i les extended i després amb l'instal·lador ja em farà les aprticions que calgui, no?

Hi ha alguna altra cosa que hagi de tenir en compte?

Respecte el tema d'Internet què me'n dieu?

Moltes gràcies, de veritat.

---

### Post by jodufi on 2007-10-26
És bona idea, pots esborrar totes les particions menys la de windows, i després dir-li a l'instal·lador que utilitzi l'espai lliure.

Pel tema internet, em sembla que serà una altra batalla :(

---

### Post by papapep on 2007-10-26
> Llavors amb el CD de l'Ubuntu 7.10 esborrarré les particions del Ubuntu 7.04 i les extended i després amb l'instal·lador ja em farà les aprticions que calgui, no?


Bé, el particionador que tens al instal·lar farà les particions que tu li diguis que faci. No ho farà pas sol. I més si pretens separar el /home de la resta...

Pel tema d'internet obre un altre fil específic, si us plau.

---

### Post by Aljullu on 2007-10-27
D'acord, quan el tingui instal·lat ja faré un tema per això d'Internet.

Respecte les particions, quina opció del menú hauré de triar? Quan instal·les l'Ubuntu t'ofereix que faci ell les particions o fer-les manualment.

Les faig manualment? Quines hauré de fer?

Moltes gràcies.

---

