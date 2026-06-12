---
title: "connexio internet 'petada'"
date: 2010-05-19
forum: Catalan Team
---

### Post by pserra on 2010-05-19
Hola,
vaig instal·lar un navegador que em va força bé que es diu ephiphany.. avui se'm ha penjat i el sistema no em reaccionavam el punter del ratolí se'm ha tornat com una mà.... he inmtentat amb la icona de finalitzar feina... i tampoc reaccionava, el cas es que he polsat el boto 'apagar del portàtil' ja que el del menú no feia rés.
El cas es que al engegar he perdut la connexió, la icona de les connecions m'ha marxat i si vaig a preferencies->connexions em surt la connexió antiga però no connecta... hi ha alguna manera de restaurar-lo? des de el live cd si que funciona!!
He provat el firefox, el chrome i rés...
com ho puc fer?
Merci.

---

### Post by RicardKp on 2010-05-19
Hola, pserra,

Instal·lat el wicd, des de sinaptic mateix, és un gestor de xarxes que funciona molt millor que el predeterminat de l'Ubuntu i és molt fàcil d'usar.

Despres executa per terminal:

sudo dhclient3 eth1

Obre el wicd, Aplicacions>Internet>Wicd, i ja t'han de sortir tortes les xarxes que enganxi la teva targeta wifi. Connecta't a la teva i tot hauria de funcionar correctament.

Vagi bé!

Ricard

---

### Post by pserra on 2010-05-19
> **RicardKp said:**
> Hola, pserra,

Instal·lat el wicd, des de sinaptic mateix, és un gestor de xarxes que funciona molt millor que el predeterminat de l'Ubuntu i és molt fàcil d'usar.

Despres executa per terminal:

sudo dhclient3 eth1

Obre el wicd, Aplicacions>Internet>Wicd, i ja t'han de sortir tortes les xarxes que enganxi la teva targeta wifi. Connecta't a la teva i tot hauria de funcionar correctament.

Vagi bé!

Ricard

Merci Ricard,
el problema es que sense connexió el synaptic esta KO..
alguna altre suggerència??
Merci

---

### Post by RicardKp on 2010-05-19
Hola, de nou,

Provar de fer:

sudo dhclient3 eth1

al terminal, i reinicia l'ordinador a veure si el gestor de xarxes connecta amb la xarxa antiga que dius que encara tens configurada.

Si no funciona prova de baixar-te el paquet del wicd des del live cd guardant-lo al disc dur o en un llapis de memòria. Per després instal·lar-lo i tornar a provar de fer sudo dhclient3 eth1 i la resta del procés que ja t'he explicat.

Apa siau,

Ricard

---

### Post by pserra on 2010-05-20
> **RicardKp said:**
> Hola, de nou,

Provar de fer:

sudo dhclient3 eth1

al terminal, i reinicia l'ordinador a veure si el gestor de xarxes connecta amb la xarxa antiga que dius que encara tens configurada.

Si no funciona prova de baixar-te el paquet del wicd des del live cd guardant-lo al disc dur o en un llapis de memòria. Per després instal·lar-lo i tornar a provar de fer sudo dhclient3 eth1 i la resta del procés que ja t'he explicat.

Apa siau,

Ricard
merci Ricard per consell,
com que tenia diversos errors,
després de perdre moltes estones, al final he formatejat les particions de ubuntu i windos, De dividid la partició de ubuntu per/ i la /home i l'he intalat i tot perfecte, em reconeix els 2 sistemes, m'engega més ràpit. TOT OK.
em sembla que hi tenia masses pedaços...

---

