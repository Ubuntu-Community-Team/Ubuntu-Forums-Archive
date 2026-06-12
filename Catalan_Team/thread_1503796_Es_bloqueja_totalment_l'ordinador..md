---
title: "Es bloqueja totalment l'ordinador."
date: 2010-06-07
forum: Catalan Team
---

### Post by enricXIII on 2010-06-07
Molt bones tinguem!
A veure...després de buscar per sant google fins a l'esgotament, sou la meva última esperança!
Tinc Lucid instal.lat al sobretaula meu i al de la meva parella.
Son 2 màquines completament diferents, però amb un error idèntic a primera vista que hem fa la vida impossible.
Engego l'ordinador, entro al meu usuari, i de cop i volta sense cap motiu aparent es bloqueja tot. Deixa de respondre el teclat i tampoc va el ratoli. 
Apareix l'imatge amb el logo d'Ubuntu i hem parpellegen els leds del teclat (el de majuscules i el de bloc numèric ) no puc fer absolutament res més que apagar l'ordinador apretant una estona el boto. O sigui, per la força bruta!
Això passa aleatòriament, tant m'ho pot fer al cap de 30 segons d'iniciar la màquina, com en qualsevol moment inesperat al cap d'una hora o dues...
He provat de deixar que vagi fent, per veure si al cap d'una estona es reinicia sol...però que va! He d'apagar per la força.
No he trobat cap cas com aquest per la xarxa, no puc treballar en aquestes condicions, ja que estic estudiant per internet i és un greu problema quant de cop ho perds tot i has de tornar a començar...amb la por al cos de que ho tornis a perdre!

Siusplau, algú té idea de que pot estar passant?

Gràcies.

---

### Post by papapep on 2010-06-07
Idea, gens ni mica, però consells per intentar aïllar el problema, algun:

1. Suposo que ja ho heu fet, però fer còpia de tot el que us importi.

2. Que passi a les dues màquines, i sent diferents, fa un tuf immens.

3. Teniu talls (els microtalls solen ser imperceptibles per a nosaltres) de corrent a casa vostra? Teniu algun lladre/SAI entre la corrent i els ordinadors? de ser positiva la resposta, treieu-lo. De ser negativa, proveu a posar-hi un SAI que us filtri les pujades i baixades de tensió (són baratets).

4. Proveu a arrencar l'ordinador i treballar amb una versió Live en un pendrive o CD, a veure si us passa el mateix.

5. Us passa amb tots els usuaris?

I per ara i tant, fins aquí les idees. En funció del que trobeu i proveu, podrem pensar més coses.

---

### Post by enricXIII on 2010-06-07
Ostres Papapep! Ets un crak! 
Ni se m'havia ocorregut pensar en aquesta possibilitat, però és possible, i tant! i ho indica el fet de que ens passa als 2 sobretaules....i per més inri al miniportàtil no hi tinc cap problema.
No tinc cap SAI d'aquests posat, però ara mateix surto a comprar i en portaré un, no farà cap mal...i és possible que solucioni el problema (tant de bó!).
Moltes gràcies per l'interés i l'ajut, de seguida que vegi si va bé o no, ho faré saber. (Si va bé m'esperaré un parell de dies a dir rès per assegurar el tema).
Merci company!

---

### Post by RicardKp on 2010-06-07
Doncs jo m'acabo de comprar un Dell Inspiron 1750 de 17,3 polzades intel dual core i 4 gb de ram. Quan arriba a casa corro a esborra-li el windows 7 i a instal·lar el Lucyd... doncs no hi ha manera, el gome se'm penja cada dos per tres; de vegades, quan tinc dos usuaris oberts, se'm tanca el gnome. Els programes se'm tanquen sols, i els plugins del flash em peten cada dos per tres. He reinstal·lat els plugins, el flash, els restricted-extras i no sé quantes coses més no sé quantes vegades, al final he decidit reformatejar-lo i fer una instal·lació neta, a partir del Cd que m'havien enviat els de Canonical(l'anterior instal·lació l'havia fet aprofitant la configuració del meu Ubuntu 9.10 de l'ordinador de sobretaula i traspassant-la al nou 10.04). Doncs amb la instal·lació neta passa exactament el mateix, No sé si aquest portàtil no suporta correctament l'Ubuntu... no ho entenc, els controladors privatius sembla que funcionen correctament, no entenc, res... algú li ha passat el mateix amb un Dell?
Després de 4 anys de LInux sense massa problemes, ara no em crec que hagi de tornar a windows, és que no m'ho puc creure!

---

### Post by papapep on 2010-06-07
Ricard,

Per poder-te ajudar ens calen dades objectives.
Obre un altre fil, i enganxa amb un adjunt el que et surti de fer un:

```
lspci -vv
```

un:

```
lsusb -v
```

i un:

```
uname -a
```

aquest últim no serà massa llarg, o sigui que pots posar-ho al cos del missatge, si vols.
Qualsevol altra dada sobre la versió de l'Ubuntu, programes que tinguis en marxa quan peta, si tens activats o no els efectes d'escriptori, etc, pot ser d'ajut per tenir alguna pista.

---

