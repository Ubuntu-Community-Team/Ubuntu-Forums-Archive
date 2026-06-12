---
title: "Feisty i la encriptació WEP"
date: 2007-06-15
forum: Catalan Team
---

### Post by pixatintes on 2007-06-15
Tinc muntat un PC a la sala d'estar amb Feisty Fawn i Freevo com a media center. Comparteixo les pelicules i la música des de l'ordenador del despatxet (amb feisty també per samba).

El fet és que funcionava com una seda fins a alguna actualització de Feisty. A partir de llavors la xarxa anava tant lenta que les pelicules no es podien veure i en prou feines escoltar música.
Després de molt remenar he trobat que el problema ve de l'encriptació WEP, si la desactivo del router, la xarxa  funciona bé, si la activo torna a anar lenta.

La veritat és que no se com arreglar-ho, si és un bug de feisty o tinc alguna cosa mal configurada.

Algú si ha trobat o sap de que va?

Gràcies per endavant,
jordi

---

### Post by AlexMuntada on 2007-06-16
No en conec els motius però sembla que les wifi a Feisty funcionen un pèl pitjor que amb l'Edgy.

Pot ser es deu al fet de què cada cop hi ha més wifis per tot arreu i els canals estan saturats de tràfic.  Aleshores, si a més a més uses WEP, l'ample de banda efectiu és més petit.  Pots mirar de comprovar si tens gaires veïns amb wifi per descartar això?

---

### Post by pixatintes on 2007-06-16
Gràcies Alex, però em sembla que no déu se pas això (tan sols agafo 4 xarxes des de casa..)

He estat buscant i crec el problema ve del paquet 'avahi'. Durant el boot tinc un error de de 'Avahi mDNS/DNS-SD Daemon: avahi-daemon [fail].' Haure de estudiar-ho millor.

Amb lo bé que m'anava l'Edgy, que hi farem.

---

### Post by AlexMuntada on 2007-06-17
Heu provat a aturar l'avahi? ```
sudo /etc/init.d/avahi-daemon stop
```

Potser aleshores haureu de configurar a mà la wifi al /etc/network/interfaces, però de fet això ja us està bé perquè no es tracta d'un equip portàtil, és a dir, que sempre s'hauria de connectar a la mateixa wifi.

D'altra banda, penseu que 4 wifis són força wifis, sobretot si estan en els mateixos canals (dels 13 canals disponibles a la freqüència de 2.4GHz, només n'hi ha 3 que no se solapen).

---

### Post by Ferri on 2007-06-18
Jo fent servir WPA no tinc problemes (un cop configurada) i és més segura. Fas servir WEP per algun motiu?

---

### Post by pixatintes on 2007-06-18
Primer de tot gràcies a tots, la veritat és que he parat boig, no sabia exactament d'on venia el problema.

L'equip sempre havia funcionat bé i de cop i volta no funciona.

Utilitzo WEP pq és molt fàcil i no tinc por que algu em robi xarxa amb l'aircrack o algo semblant, estic en edifici ple d'avis, i on visc no és BCN que està ple d'antenes dirigides ;).
Però al final el problema no venia d'aquí. El que passa és que al desconnectar l'encriptació WEP vaig guanyar  una mica de velocitat i creia que d'aquí és on venia el problema.

Sobre el Wifi i els canals la veritat és que em perdo una mica, creia que de 13 canals, cada xarxa només n'utilitzava 1. De totes formes són xarxes d'oficines que de nit no crec q funcionin massa. L'equip està configurat tal com dius Alex que només d'arrancar es connecta a la xarxa (sempre la mateixa) i monta per cifs (fins ahir amb smbfs, diuen que va un pèl millor la cifs) les carpetes de xarxa.

Després vaig pensar que no fos el driver de la targeta, però vaig connectar a un equip a la mateixa distància amb carpetes compartides per Win XP i funcionava.
El curiós és que llegint des de l'equip amb win al mateix servidor smb ubuntu funcionava.

O sigui, el servidor Samba funcionava bé amb equips Win i no funcionava bé amb equips Linux.

Després de molt remenar, he trobat una solució que funciona, no ho acabo d'entendre però funciona. He connectat el Firestarter i he obert els ports de samba (137-139 i 445) al servidor. Ara sembla que funciona, la veritat no les tinc pas totes, però la xarxa funciona altre cop a més de 1 MB/s (suficient pel que la utilitzo).

Hi ha coses que no entenc, els port no són els mateixos tant per els equips windows q per els equips linux? pq per uns funciona i els altres no? Per defecte no venen tots els ports obert a ubuntu?

---

### Post by CarlesOriol on 2007-06-18
Es possible que el xip de la targeta de xarxa sigui una broadcom? ( modul bcm44xx ) ??

---

### Post by pixatintes on 2007-06-18
La targeta wifi és una conceptronic C54ri amb xip  Ralink rt2500. La de xarxa del servidor va integrada ala placa crec és  Realtek RTL8111B.

---

### Post by patrickfromspain on 2007-06-19
desinsta&#320;la el network manager:

sudo apt-get remove network-manager network-manager-gnome. Reinicia y fes servir l'eina de gnome per configurar-la. A mi en funciona, i tambe tinc una ralink de conecptronic.

Si no va, enganxan's el que et sur si poses lsmod en un terminal.

Salut!

---

### Post by pixatintes on 2007-06-20
Per ara sembla que va, crec q abans anava més bé.. però funciona.

Gràcies

---

