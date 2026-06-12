---
title: "Com dualitzar una màquina amb Windows 7?"
date: 2010-09-22
forum: Catalan Team
---

### Post by SiscoGarcia on 2010-09-22
Hola,

He vist que alguns/es de vosaltres heu pogut fer dual alguna màquina amb Windows7, però jo he estat incapaç. M'explico:

Una companya de feina s'ha comprat un flamant «[dell inspiron 13z]("http://www.dell.com/us/en/dfo/notebooks/inspiron-13z/pd.aspx?refid=inspiron-13z&s=dfo")» que venia de fàbrica amb Windows 7. El problema és que el fabricant fa una partició primària de recuperació, i el Windows 7 en té 3 més de primàries (una de recuperació, una altra pel sistema i la tercera per les dades), de manera que no podem crear-ne cap més de nova.

La companya no vol perdre la llicència original, de manera que no volem arriscar-nos a eliminar cap partició (hem fet una imatge del disc per si de cas) sense certes garanties. Teniu alguna idea? Els i les que ho heu fet us heu trobat amb algun problema semblant?

---

### Post by wgarcia on 2010-09-22
Has de convertir una d'aquestes particions en una partició "extended" i dins d'aquesta extended definir totes les particions lògiques que necessitis per a Linux.

---

### Post by gunyoles on 2010-09-22
Hola Sisco
Jo tinc dual amb Ubuntu i W7. La instal·lació va ser directa del cd afegint l'Ubuntu al que hi havia, això si donant-li mes espai que al Windows que ara fa poca feina, de fet nomes treballa per el Compe GPS. La partició de recuperació de Windows la vaig anul.lar per que tinc el DVD original, de totes maneres en pots fer una copia de seguretat tu mateix. Tingues present que nomes es podrà tornar a instal.lar al equip de on ha sortit.
Un cop instal·lat el Grub queda així, arrenca automàtic Ubuntu a no ser que seleccionis un altre opció en els 10 segons que et dona.

---

### Post by gunyoles on 2010-09-22
m'he deixat la foto


[ATTACH]170225[/ATTACH]

---

### Post by SiscoGarcia on 2010-09-22
Gràcies als dos per respondre,

> **wgarcia said:**
> Has de convertir una d'aquestes particions en una partició "extended" i dins d'aquesta extended definir totes les particions lògiques que necessitis per a Linux.

Walter, convertint una d'aquestes particions en «extended» el Windows la podria llegir bé? Ho dic perquè aquest és el problema que se'm planteja :(

D'altra banda, Gunyoles, al teu grub la situació és diferent de la que jo plantejo, ja que no hi ha cap partició del fabricant; però gràcies de tota manera ;)

---

### Post by wgarcia on 2010-09-22
No, Windows ha d'estar en una partició primària. Em referia a eliminar alguna d'aquestes primàries, comprimir una mica les particions on és Windows i deixar espai per a una extended amb les particions lògiques necessàries per posar Linux. Realment necessita les 3 particions el Windows?

---

### Post by wgarcia on 2010-09-22
Se m'acut que la manera seria que la partició de dades de Windows tenir-la com partició lògica dins la "extended". Formatejant aquesta partició com ntfs windows ja la veuria. El que no pot windows és estar instal·lat en una partició lògica, vol la seva pròpia partició primària.

---

### Post by akyra on 2010-09-23
Hola Sisco, amb un portatil nou amb Vista, tenia les mateixes particions que tu tens amb W7.
Jo el que vaig fer va ser fer molt petita la particio a on està instalat el Windows i també la de dades ja que no la utilitzava. Això ho vaig fer des del gestor de particions del propi windows i fent un desfragmentar abans.

Després vaig reduir molt la ultima partició de windows i vaig crear la partició "extended" com indica en Walter, i en aquesta "extended" vaig fer totes les que necessitava per Ubuntu.
Amb el grub vaig poder redimensionar totes les particions de Windows, ja que no em deixaba baixar de 100GB per la partició de windows.

Si vols et puc pasar una imatge de la meva partició actual amb grub.

No vaig tenir problemes, però s'ha de fer amb ordre.

Salutacions

---

### Post by wgarcia on 2010-09-23
Una última opció per a l'amiga del Sisco, és simplement instal·lar l'ubuntu a dins del windows amb el virtualbox. Des de l'ubuntu pot compartir fitxers amb el windows, i pot anar provant l'ubuntu sense riscos. Si li agrada més endavant la pots ajudar a instal·lar definitivament l'ubuntu amb doble arrencada. 

Em sembla que el "wubi" també permet instal·lar ubuntu sense fer particions, però això no estic segur perquè mai no l'he fet servir.

Em sembla que l'opció que suggereix l'Akira no és factible en la configuració del PC de l'amiga del Sisco perquè té a més de les tres particions primàries del Windows una altra amb les utilitats de Dell i no vol carregar-se cap. Tot i que redueixis l'espai de les particions, no et deixarà crear una cinquena partició, sols es poden crear 4 primàries per disc.

---

### Post by akyra on 2010-09-23
Hola
Jo proposo a la ultima partició que hi ha creada per Windows, reduirla, i a l'espai que queda fer-la "extended", encara que hagis d'anar movent les paticions, gparted ho permet fer.
Hi ha una cosa que no entenc:
> Una companya de feina s'ha comprat un flamant «dell inspiron 13z» que venia de fàbrica amb Windows 7. El problema és que el fabricant fa una partició primària de recuperació, i el Windows 7 en té 3 més de primàries (una de recuperació, una altra pel sistema i la tercera per les dades), de manera que no podem crear-ne cap més de nova.
Això voldria dir 4 primaries, i això no pot ser. Hauria de ser 3 primaries i una lògica. Aquest última la podriem reduir, crear-ne una de nova a la dreta "extended" moure les dades cap a aquesta nova, unir l'extended amb la que té a la dreta que hem mogut i que per tant queda espai lliure, i finalment colocar les dades al principi de la partició extended.
Després amb l'espai que hi ha a continuació posar l'ubuntu, swap, home.

Us paso una mostra de com ho tinc fet, crec que és molt semblant al que te l'amiga d'en Sisco, i és com normalment et venen els ordinadors ara.

Si he dit alguna bestiesa, que tot pot ser, digueu-m'ho.

De totes maneres crec que és indispensable fer una copia de seguretat de les paticions que hagi de tocar.

Salutacions


Perdoneu, com es pugen imatges?

---

### Post by gunyoles on 2010-09-23
Jo proposo una possibilitat una mica en línia al que deia el Walter, per provar l'Ubuntu de moment. El wubi permet treballar des de el cd o instal·lar el sistema sense tocar particions. Si mes endavant l'amiga del Sisco l'hi agrada l'Ubuntu (segur que si) i s'anima, llavors pot estudiar millor la possibilitat de restringir el windows o fins i tot eliminar-lo, encara que perdi la llicencia. Si d'aquí un temps no el necessita que tiri nomes d'Ubuntu.
Possibilitats ja ho veus, n'hi ha moltes, el difícil es escollir, sobretot si has de aconsellar a un altre persona.

---

### Post by SiscoGarcia on 2010-09-23
> **wgarcia said:**
> Em sembla que l'opció que suggereix l'Akira no és factible en la configuració del PC de l'amiga del Sisco perquè té a més de les tres particions primàries del Windows una altra amb les utilitats de Dell i no vol carregar-se cap. Tot i que redueixis l'espai de les particions, no et deixarà crear una cinquena partició, sols es poden crear 4 primàries per disc.

Exactament aquest era el problema.

Perdoneu que no hagi respost abans, però he estat embolicat fent altres coses i no he comunicat que el problema estava resolt. Abans de res he de dir que no ens plantejàvem la instal·lació del wubi perquè no acaba d'allibarar-te del Windows, i ella ja és usuària d'ubuntu al [centre]("http://ponent.caliu.cat/2010/07/30/tot-linsti-amb-ubuntu/")... a part que personalment em sembla que aquesta opció és subordinar l'ubuntu al windows i no deixar que s'expressi en tota la seua plenitud ;)

Ho hem resolt fent creant una imatge del disc, per si de cas, i després carregant-nos una de les particions (la de dades). A partir d'aquí hem redimensionat la del sistema perquè hi pogués desar dades i hem instal·lat l'ubuntu a l'espai lliure continu més gran; el que ja no hem fet és una instal·lació avançada separant l'arrel (/) de la home (/home), per exemple, però la companya ha marxat ben contenta amb el dos sistemes operatius... operatius i funcionant :D

Gràcies a tots pel cop de mà!

---

