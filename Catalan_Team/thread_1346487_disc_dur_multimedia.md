---
title: "disc dur multimedia"
date: 2009-12-05
forum: Catalan Team
---

### Post by venusfenix on 2009-12-05
buenas,

tinc un portatil acer AMD 64x2 amb jaunty, i un disc dur multimedia.
el tema es que quan paso información, veig clarament que ubuntu ha copiat els fitxers al disc dur, pero quan reprodueixo, nomes veig les carpetes.
si el conecto a windows vista, confirmo el que veig al TV.
i de moment, estic obligat a pasar per windows per fer les copies al disc dur.
no hi ha manera de fer-ho compatible? em falta algun driver??

moltes merces.

---

### Post by CarlesOriol on 2009-12-06
M'he llegit 10 cops el missatge i confeso que no l'entenc.

Pots intentar explicar que vols dir i quin és el problema?

---

### Post by venusfenix on 2009-12-06
buenas

merci per respondre, i si, acabo de llegir-me el meu missatge i no queda massa clar.

el tema es el següent, si copio fitxers al disc dur desde ubuntu. segons ubuntu, tot es correcte, pero quan conecto el disc dur multimedia al TV i intento reproduïr, (amb el sofware propi del disc dur) nomes veig les carpetes creades (o transferides) i res de fitxers (del tipus que sigui). 
Per l'altre banda, si ho faig desde vista, tot perfecte.

la pregunta del millon es: que tinc que fer perque ubuntu faci la copia correctament?

merci!!

---

### Post by Flocdemer on 2009-12-06
Jo tinc un grabador samsung que selecciona els fitxers que pot reproduir.  Els que no pot reproduir no els mostra.

---

### Post by venusfenix on 2009-12-07
buenas,

no hi han incompatibilitats amb formats, els mateixos fitxers si els grabo amb vista, el disc dur els reconeix i els pot reproduir, pero si el copio amb ubuntu, llavors res de res.

merci,

---

### Post by oriolsbd on 2009-12-07
Quin tipus de format té el disc dur multimèdia? Ntfs o fat32? O algun altre? Apart d'això, suposo que quan desconnectes el disc multimèdia, abans el desmuntes, oi?    (No físicament, clar :-)   )

Salut!

---

### Post by venusfenix on 2009-12-07
buenas,

el disc dur es fat32, si malament no recordo.
i si, sempre faig desmuntar la unitat, "como en los viejos tiempos del DOS".

alguna pista del que pot passar?

merci,

---

### Post by tanreb20 on 2009-12-07
Podries provar de afegir permisos de lectura als arxius per tothom un cop estiguin al disc dur.

es a dir:

sudo chmod +r "fitxers"

o bé

sudo chmod -R +r "carpeta/"

I després proves

---

### Post by CarlesOriol on 2009-12-07
tanreb20: permisos de lectura en un fat32... mmm això existeix?

venusfenix: desmuntar la unitat com als vells temps DOS... mmmm en DOS no es muntava res.

venusfenix: prova de copiar el mateix arxiu en l'ubuntu i amb l'altre.

un cop fet això fes un ls -l a veure si veiem cap llum.

---

### Post by venusfenix on 2009-12-07
CarlesOriol;

suposo que em dius de fer copia i donar el resultat de fer ls-l, primer amb un sistema, i despres amb l'altre. no?

respecte al meu comentari, "desmuntar la unitat com als vells temps DOS", em referia quan es tenir que "aparcar" els disc durs abans d'apagar l'ordinador (ordre PARK). possiblement el mes semblant al concepte de "desmuntar" actual. 

o aixo, o les comparacions son odioses.

enga, fare proves i penjare els resultats aviat.

merci!!!

---

### Post by akyra on 2009-12-09
Jo tinc un multimedia Storex i em funciona bé, i estava pensant amb el que dius, i pot ser que estiguis fent la copia amb usuari root?

Una pregunta més, pots veure des d'Ubuntu el que has copiat en el disc dur multimedia? Si el montes i el desmontes pots veure el que has copiat?

Adeu

---

### Post by venusfenix on 2009-12-23
Buenas,

copiat amb ubuntu i fen un ls -l, el resultat es:

drwxrwxrwx 1 root root 0 2009-11-26 20:34 01._Pato_Quisquilloso
drwxrwxrwx 1 root root 0 2009-11-26 20:33 02._Estornudo
drwxrwxrwx 1 root root 0 2009-11-26 20:33 03._Baila_Pocoy&#00243;
drwxrwxrwx 1 root root 0 2009-11-26 20:33 04._Una_Peque&#00241;a_Nube
drwxrwxrwx 1 root root 0 2009-11-26 20:33 05._La_Llave_Maestra
drwxrwxrwx 1 root root 0 2009-11-26 20:33 06._Querido_Cachorro

segons aixó, hi han fitxers pero no ocupa res d'espai

quina potser l'explicacio??

gracies,

---

### Post by venusfenix on 2009-12-23
Un ls -l un cop copiat amb Ubuntu:

-rwxrwxrwx 1 root root 74520752 2009-11-25 23:45 01. Pato Quisquilloso.avi

Un ls -l un cop copiat amb Vista:
-rwxrwxrwx 1 root root 95390434 2009-11-25 23:56 02. Estornudo.avi


Alguna pista??

merci,

---

### Post by akyra on 2009-12-24
És molt extrany això,

Pel que veig amb la sortida del comando "ls -l", sembla que ho has copiat a diferents carpetes. si és així, és possible que el nom de la carpeta que li has posat en la carpeta d'ubuntu tingui algun caracter especial (',´, etc.) que el reproductor no reconeixi? També és possible que només pugir reproduir fitxers d'una carpeta determinada (video, music, photo, etc..).

Salut

---

### Post by venusfenix on 2009-12-24
buenas,
em sembla que potser el que dius de caracters especials, malgrat tot, encara no ho reconeix, ara mes extrany que mai, ni tan sols copian desde vista.

intentaré cambiar noms de carpeta, pot ser aixo tant sencill??

gracies,

---

### Post by venusfenix on 2010-01-03
ultimes proves i conclusions.

el disc dur era NTFS, per altres motius, he tingut que formatejar-lo a FAT32 i el problema a desaparegut, ara tot funciona be.

algu sap perqué el problema era que el disc estigues formatat a NTFS???

gracies,

---

### Post by CarlesOriol on 2010-01-04
Hi ha una característica del ntfs que penso que no està implementada. Els arxius comprimits (a nivell de sistema d'arxius clar...)

Pot ser que et deixes llegir el disc i tinguessis problemes amb els arxius/carpetes amb aquest flag?

---

### Post by venusfenix on 2010-01-04
buenas,

amb ubuntu, com he comentat anteriorment, podia copiar-lo, etc... i desde l'ordinador podia llegir, executar, etc.... pero el disc dur com a reproductor multimedia, ni tan sols sortia en el directori.

ara, com he dit, amb fat32 cap probleme,

gracies,

---

