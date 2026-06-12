---
title: "Upgrade a Kubuntu 9.04 es penja: què faig?"
date: 2009-05-06
forum: Catalan Team
---

### Post by vallibona on 2009-05-06
Hola a tots
Ahir el meu portàtil (Toshiba A400, gràfica Intel 4500 [http://es.computers.toshiba-europe.com/innovation/series/Serie-Satellite-U400/149966/](http://es.computers.toshiba-europe.com/innovation/series/Serie-Satellite-U400/149966/)) va suggerir-me un upgrade des de Kubuntu 8.10 a Kubuntu 9.04.

Vaig acceptar el suggeriment, i tot anava bé fins que, al cap d'una estona, la descàrrega d'arxius es va congelar al 99% (baixant l'últim dels 992 arxius a actualitzar).

El PC funciona correctament, continua havent connexió a Internet, però l'actualització, 24h ores després, s'ha quedat paralitzada.
El botó "Més detalls" no està actiu, i si tanco l'actualització m'adverteix que el sistema pot quedar inservible.....
Alguna idea abans de reiniciar i resar per que no passe res?

Moltes gràcies per endavant per la vostra ajuda, espero que arribe a hora, encara que siga a l'ultim minut com el Barça esta nit.... ;-)

Salutacions,

Fidel

---

### Post by papapep on 2009-05-06
Si s'ha quedat "penjat" mentre descarregava els paquets **i encara no els havia començat a instal·lar**, només et cal tornar a començar el procés. No t'hauria de passar res i hauria d'acabar bé tot plegat.

---

### Post by vallibona on 2009-05-06
Gràcies Papapep.... vaig a cancel·lar i reiniciar actualització, a vore què passa....

---

### Post by vallibona on 2009-05-11
Hola a tots
Una vegada cancel·lat, la instal·lació s'ha realitzat sense problemes.
La única cosa que em passa és que la barra d'eines apareix amb els contorns borrosos, i no puc veure el que toco, ho he de fer de memòria, i és proooou molest.
Alguna idea?
Gràcies!

---

### Post by orestesmas on 2009-05-12
Què entens tu per la "barra d'eines"? Vols dir el panell, on hi ha el menú principal, barra de tasques, rellotge, etc?

Si és així prova de:

1) Desactivar la composició (Menú: Arranjament del sistema -> Escriptori -> (des)Habilita els efectes d'escriptori) a veure si millora alguna cosa

2) Provar a veure si t'ha quedat algun paquet a mig configurar. Obre un terminal i posa-hi:
```

sudo apt-get -f install
sudo dpkg --configure --pending

```

---

### Post by vallibona on 2009-05-19
Solucionat, moltes gràcies!
Pareix que fent el que comentaves el sistema s'ha recuperat.

---

### Post by marteljorge on 2009-05-20
Per si cal:
sudo dpkg --configure -a

---

