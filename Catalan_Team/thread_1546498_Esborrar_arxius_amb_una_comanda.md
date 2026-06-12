---
title: "Esborrar arxius amb una comanda"
date: 2010-08-05
forum: Catalan Team
---

### Post by Daerun on 2010-08-05
Fa un temps, no sé si va ser aqui o a la llista de correu, vaig llegir un mètode per esborrar del disc tots els arxius ocults de còpia de seguretat o de còpia temporal, o com es diguin: aquells que quan mostres els arxius ocults apareixen amb el mateix nom que els documents de text -per exemple- però amb un símbol "~" darrere de l'extensió de tipus d'arxiu.
Algú sap de què parlo? :P

---

### Post by tanreb20 on 2010-08-05
```
rm *~
```

?

---

### Post by epileg on 2010-08-06
Jo ho faria així:
> $ find -iname "*~" 2> /dev/null -print0 | xargs -0 rm

---

### Post by Daerun on 2010-08-07
> **epileg said:**
> Jo ho faria així:

I per esborrar el contingut només d'una carpeta determinada (ho dic per si de cas, per no cagar-la :P).

---

### Post by wgarcia on 2010-08-08
Totes aquestes comandes són perilloses, assegura't de tenir còpies de seguretat perquè més d'un ha tingut malsons amb comandes d'esborrament massiu, sobretot quan les executes amb privilegis d'administrador. Es mencionen també moltes d'aquestes comandes en les comandes "malicioses" a la primera entrada d'aquest fòrum ([http://ubuntuforums.org/announcement.php?f=206](http://ubuntuforums.org/announcement.php?f=206))

Per esborrar un directori, tot i que tingui dades (fitxers i altres subdirectoris), ho pots fer amb "rm -fr <nom del directori>".

---

### Post by epileg on 2010-08-09
Per a determinar el nivell de sots-directoris a explorar pel «find» ho post fer amb l'opció «-maxdeph». Amb un 1 només examina el directori actual, amb 2 l'actuals i els sots-directoris directes, amb 3, com el 2 + un nivell més de sots-directoris, etc. 

Aquesta ordre només eliminaria tots els fitxers/carpetes que acabessin amb «~» del directori actual.

$ find -maxdepth 1 -iname "*~" 2> /dev/null -print0 | xargs -0 rm

Quan a la seguretat de les ordres, és un bon costum fer alguna prova abans de llençar-se a fer coses que no tenen remei, com ara els esborrats massius.

En aquest cas, jo primer executaria la mateixa ordre però sense l'«rm» final, per a veure per pantalla que és el que m'està llistant l'ordre «find», i per tant, que és el que esborraré.

En aquest cas l'ordre seria així:

$ find -maxdepth 1 -iname "*~" 2> /dev/null -print0 | xargs -0

Com podràs comprovar, l'ordre et mostra els resultats sense retorns de línia, això és correcte i necessari si vols que els fitxers/carpetes amb espais als seus noms es processin correctament.

Si el que vols és un llistat ortodox, fes servir aquesta ordre:

$ find -maxdepth 1 -iname "*~" 2> /dev/null

Ja per últim, he anu&#320;lat la sortida «stderr» per si hi ha algun error de denegació d'accés/lectura a algun directori/carpeta. Com a exemple, això et passaria si fessis una cerca amb «find» des del directori arrel i sense l'opció «-maxdepth».

Si no vols tenir anu&#320;lat l'«stderr» és tant simple com fer això:

$ find -maxdepth 1 -iname "*~" -print0 | xargs -0

Salut,

---

