---
title: "Anell de claus en cada inici..."
date: 2009-04-28
forum: Catalan Team
---

### Post by valdric on 2009-04-28
Hola a tothom.

He instalar l'Ubuntu 9.04 i faig servir una targeta de red wifi.
El problema es que a cada inici de sessió, la targeta intenta conectarse a internet i m'apareix el missatge  que l'aplicació necessita la contrasenya de l'anell de claus per autoritzar aquest accés a internet. Soc l'únic usuari de l'ordinador i voldria deixar-ho autoritzat per sempre. Per la red hi han solucions per Ubuntu 8.10 pero que no hem serveixen pel nou.

Algú hem pot donar un cop de mà?:)

---

### Post by oriolsbd on 2009-04-29
Hola.

Et demana la paraula de pas de l'anell de claus perquè la primera vegada et va demanar si volies posar-li una paraula de pas i, pensant-te que et demanava la password del teu usuari, li vas posar. Ho sé perquè fa uns mesos a mi em va passar el mateix... :-)

El que has de fer és esborrar (o, millor encara, renombrar) el fitxer "/home/el_teu_usuari/.gnome2/keyrings/default.keyring". Quan et tornis a connectar a la xarxa, et demanarà la clau WEP, i et tornarà a preguntar quina paraula de pas vols posar a l'anell de claus. En aquest cas, prem "Enter" sense introduir cap paraula de pas a l'anell de claus.

Salut!

---

### Post by RainCT on 2009-04-29
L'anella de claus s'hauria de desbloquejar sola quan inicieu sessió. O és que teniu la sessió configurada per a entrar automàticament sense contrasenya?

---

### Post by PatrickVogeli on 2009-04-29
jo tinc sessio amb entrada automatica i no em demana la contrasenya el network manager.

salut!

---

### Post by valdric on 2009-05-01
He seguit els passos de oriolsbd i quan hem tornava a demanar a contrassenya que volia per l'anell de claus ho he deixat en blanc i ara quan inicio el sistema ja es conecta automàticament a la red.

I sí que tinc inici de sessió sense contrassenya...

---

### Post by Mitsurugi on 2009-09-14
[http://alliberats.cat/evitar-que-lanell-de-claus-ens-demani-la-paraula-de-pas/comment-page-1/#comment-849](http://alliberats.cat/evitar-que-lanell-de-claus-ens-demani-la-paraula-de-pas/comment-page-1/#comment-849)

---

### Post by reginsman on 2013-02-24
Bones,
A mi em passa el mateix, volia modicar el fitxer "/home/el_teu_usuari/.gnome2/keyrings/default.keyring" però no tinc cap directori keyrings dins de .gnome

Faig servir la versió 12.10, entro automàticament i no tinc ni idea de com solucionar tot això :???:
Gràcies per tot!!! ja direu...

---

### Post by wgarcia on 2013-02-25
Hola Reginsman,

El millor és obrir un fil nou i no reaprofitar un d'antic, Ubuntu ha canviat moltíssim des del 2009.

---

