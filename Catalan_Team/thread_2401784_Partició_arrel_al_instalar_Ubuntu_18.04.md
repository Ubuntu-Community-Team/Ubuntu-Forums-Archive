---
title: "Partició arrel al instalar Ubuntu 18.04"
date: 2018-09-22
forum: Catalan Team
---

### Post by negu on 2018-09-22
[COLOR=#666666][FONT=&quot]Hola companys i companyes,[/FONT][/COLOR]
[COLOR=#666666][FONT=&quot]em vull [/FONT][/COLOR][COLOR=#666666][FONT=&quot]instal·lar[/FONT][/COLOR][COLOR=#666666][FONT=&quot] l'[/FONT][/COLOR][COLOR=#666666][FONT=&quot]Ubuntu[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]18.04[/FONT][/COLOR][COLOR=#666666][FONT=&quot] i h faré des d'un USB, ja ho tinc tot preparat i cercant informació sobre com fer-ho i que no m'agafi desprevingut m'han vingut uns dubtes que volia compartir amb vosaltres, ja que he buscat informacions i [/FONT][/COLOR][COLOR=#666666][FONT=&quot]són[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]contradictòries[/FONT][/COLOR][COLOR=#666666][FONT=&quot].[/FONT][/COLOR]
[COLOR=#666666][FONT=&quot]De quina [/FONT][/COLOR][COLOR=#666666][FONT=&quot]mida[/FONT][/COLOR][COLOR=#666666][FONT=&quot] faig les particions?[/FONT][/COLOR]

[COLOR=#666666][FONT=&quot]Les característiques de l'ordinador [/FONT][/COLOR][COLOR=#666666][FONT=&quot]són[/FONT][/COLOR][COLOR=#666666][FONT=&quot]:[/FONT][/COLOR]
[COLOR=#666666][FONT=&quot]Toshiba[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]Satellite[/FONT][/COLOR][COLOR=#666666][FONT=&quot] Pro[/FONT][/COLOR]
[COLOR=#666666][FONT=&quot]Procesador[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]Intel[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]Core[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]i3[/FONT][/COLOR][COLOR=#666666][FONT=&quot]-[/FONT][/COLOR][COLOR=#666666][FONT=&quot]3110M[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]CPU@2,40GHz[/FONT][/COLOR][COLOR=#666666][FONT=&quot] x 4[/FONT][/COLOR]
[COLOR=#666666][FONT=&quot]Disc 488 GB[/FONT][/COLOR]

[COLOR=#666666][FONT=&quot]L'[/FONT][/COLOR][COLOR=#666666][FONT=&quot]altre és que jo fins ara tenia versions de l'[/FONT][/COLOR][COLOR=#666666][FONT=&quot]Ubuntu[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]32bits[/FONT][/COLOR][COLOR=#666666][FONT=&quot], i veig que ara ja no l'han fet.... m'afectaria d'alguna manera?[/FONT][/COLOR]

---

### Post by wgarcia on 2018-09-23
El tipus i mida de les particions depèn del que vulguis fer. És a dir, 1) si l'Ubuntu serà l'únic sistema al disc, o si vols tenir a més algun altre sistema operatiu al costat de l'Ubuntu, 2) quin ús li vols donar a l'Ubuntu, si has de gestionar dades molt voluminoses com vídeos o altre tipus de dades que requereixin molt d'espai de disc. En la meva experiència, per al sistema operatiu va bé reservar uns 30 gigues, però per a les dades d'usuari depèn del volum de dades que vulguis emmagatzemar al disc. Una possibilitat que tens, si no vols pensar-ho massa ara i vols tenir dos sistemes operatius convivint al mateix disc, és deixar-li la meitat del disc a l'Ubuntu.

Una altra cosa que és recomanable és posar els sistema operatiu i les dades d'usuari en una altra particio. Això és fa creant una partició per al punt de muntatge "/" i una altra per al punt de muntatge "/home". L'instal·lador t'ho deixa fer, al moment de fer les particions t'ofereix fer una partició estàndard o "una altra cosa", i has d'escollir aquesta última opció. En tot cas, busca algun tutorial o explicació abans de fer-ho per assegurar-te que tens clar el que s'ha de fer, i en tot cas si tens dades al disc com per exemple un altre sistema operatiu que vols conservar, fes còpies de seguretat d'aquestes dades per si un cas.

Quan a 32 bits o 64 bits, pel tipus d'ordinador que tens no hi ha problema per fer servir la versió de 64 bits. Pràcticament ja no queden ordinadors que sols puguin fer servir la versió de 32 bits, per això ja no distribueixen aquesta versió.

---

### Post by negu on 2018-09-23
Moltes Gràcies wgarcia, 

es veritat que m'he deixat de donar una informació:
1. Jo vull Ubuntu com a únic sistema operatiu
2. La idea es desinstalar tot el que tinc i que s'instali de nou, es a dir que no m'importa perdre la informació ni els programes
3. L'ús que jo en faig de l'ordinador es d'editar textos, emmagatzemar pelis, música.... per tant si que m'interessa tenir espai per les dades.

En quant a les particions el que he llegit és que allò òptim serien 3 (corregiu-me si m'equivoco)

1. la primera, partició arrel (/) per arxius i carpetes del S.O que entenc que aquí és on tu dius de que el tamany sigui de 30GB
2. Partició (/home) per arxius i carpetes dels usuaris que tinguin compte en l'ordinador, en aquest sentit l'ordinador només tindrà un usuari, per tant cal que la faci?
3. Partició d'intercanvi (swap) que equivaldria a la capacitat de la memoria RAM, però com que la del meu oridnador és inferios a 4GB caldria deixar-ne el doble, és a dir 4GB.

Seria correcte fer aquestes 3 particions? el tamany concret de les particions tenint en compte que el disc té una capacitat de 488GB? i no vull tenir cap altre SO a l'ordinador i que només tindré un compte? i també he llegit que l'ordre de les particions es important....quantes coses a tenir en compte.....

En quant als 64 bits, gràcies per l'aclariment!

moltes gràcies al fòrum!!!

---

### Post by jmaspons on 2018-09-24
Hola,

Separar l'arrel de /home té l'avantatge que si vols reinstal·lar el sistema operatiu pots formatejar la partició arrel sense haver de preocupar-te per les dades d'usuari. Per contra, fa que no puguis apurar tant l'espai d'emmagatzematge ja que, per anar bé, sempre tindràs una part d'espai lliure a les dues particions i seria més complicat utilitzar espai de la partició arrel per desar dades d'usuari i viceversa.

Si no tens pensat reinstal·lar el sistema operatiu o no vols encriptar la partició de les dades però no l'arrel, pots utilitzar una sola partició (l'arrel que també inclourà /home).

Si fas 2 particions, 30 Gb per l'arrel serà suficient en la majoria dels casos però depèn dels programes i dades que guardis en aquesta partició

---

### Post by wgarcia on 2018-09-24
Estic d'acord amb jmaspons. Crec que sempre és convenient deixar la partició /home separada. SI has de reinstal·lar algun moment el sistema operatiu, com ell diu tornes a formatejar la partició on tens "/" muntat, muntes "/home" i es conservaran totes les dades que tenies. Això és convenient fins i tot si hi ha un sols usuari al sistema.

Per a les versions recents de l'Ubuntu no cal fer una partició swap. El swap es farà ara amb un altre sistema que fa servir un fitxer, i no una partició. 

Sent l'únic sistema operatiu i tenint 500 gigues d'espai de disc, jo deixaria fins i tot una mica més per al punt de muntatge "/", diguem-ne 50 guiges, així no t'has de preocupar mai instal·lis el que instal·lis, no l'esgotaràs mai aquest espai, i et queden 450 gigues per fitxers que és més que suficient.

---

