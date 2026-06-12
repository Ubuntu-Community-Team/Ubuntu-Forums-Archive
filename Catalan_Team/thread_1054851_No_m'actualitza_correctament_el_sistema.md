---
title: "No m'actualitza correctament el sistema"
date: 2009-01-30
forum: Catalan Team
---

### Post by kukat on 2009-01-30
Salutacions!

Des de fa un parell de mesos que el meu gestor d'actualitzacions em treu un missatge de "No s'han pogut insta&#320;lar totes les actualitzacions".

Al principi creia que era per l'OpenOffice, ja que totes les actualitzacions eren de l'OpenOffice (al insta&#320;lar la nova versió 3, pensava que tendria alguna cosa a veure...)

però avui ja tinc actualitzacions de seguretat importants que no s'ista&#320;len ([http://img140.imageshack.us/img140/3651/94023236if3.png](http://img140.imageshack.us/img140/3651/94023236if3.png)) , i ja em preocupa un poc!!

Adjunte el meu "sources.list" per si te alguna cosa a veure


Gràcies

---

### Post by open-pitu on 2009-01-30
Prova d'actualitzar des del terminal, i enganxa l'error que et dongui:

```
$ sudo aptitude update
```

Així podrem fer-hi alguna coseta més.

---

### Post by oriolsbd on 2009-01-30
Hola, ahir vaig veure en un post d'Ubuntips que, des de fa uns dies, hi ha un problema amb les claus de Launchpad. En el mateix post indiquen com arreglar-ho. Jo no ho he provat encara, però l'article és [aquest]("http://www.ubuntips.com.ar/2009/01/29/como-solucionar-el-error-gpg-en-las-llaves-publicas-de-launchpad/").

Si el proves, ja diràs si va bé.

Salut!

---

### Post by kukat on 2009-01-31
Al fer un aptitude update (o un apt-get update) em surt açò:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: Les següents signatures no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 60D11217247D1CFF
W: Potser voldreu executar apt-get update per a corregir aquests problemes


Vaig va veure el post que m'heu passat a veure...:) thanks!

---

### Post by kukat on 2009-01-31
Molt estrany.....

[he fet el que diu, executant l'script i ja no em tira l'error de la clau pública]("http://b2dbuntu.wordpress.com/2009/01/29/solucion-actualizar-las-llaves-publicas-gpg-de-launchpad-en-ubuntu/"), però he actualitzat, he fet "sudo aptitude update" i he apretat a "Comprova" en el gestor d'actualitzacions però em surt el mateix missatge de "no s'han pogut insta&#320;lar totes les actualitzacions...." 

No se de que es pot tractar.....

---

### Post by Diegstroyer on 2009-02-01
Ves a Synaptic, a la part de paquets trencats i clica sobre un d'ells (dels que et dona problemes), et demanarà per marcar els paquets en conflicte per desinstal·lar-los, fes-ho amb tots els que tinguis problemes.

Salitacions.

---

### Post by kukat on 2009-02-03
Gràcies!! era exactament això!
Anar al synaptic i actualitzar els paquets (que en el meu cas s'han esborrat alguns i altres s'han actualtizat)
Salutacions!
;)

---

### Post by SiscoGarcia on 2009-02-03
kukat, marca el fil com a resolt, que tu ja t'ho saps ;)

Fins aviat.

---

