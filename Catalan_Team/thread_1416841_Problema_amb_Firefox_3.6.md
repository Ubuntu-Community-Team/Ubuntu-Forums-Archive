---
title: "Problema amb Firefox 3.6"
date: 2010-02-26
forum: Catalan Team
---

### Post by Joan A. on 2010-02-26
Hola a tothom!

Tinc un petit problema amb el nou **Firefox 3.6**. Vaig actualitzar ahir a la versió final i no em deixa desinstal·lar el pack del llenguatge espanyol de la versió **3.5.7**. A complements/idiomes no puc fer click al botó desinstal·lar. Algú sap com puc fer-ho? Ja sé que no és un problema greu, però em duu de cap. Per cert, la meva distribució és *Ubuntu 9.10 (32 bit)*.

Gràcies i salutacions des de Mallorca! ;)

---

### Post by SiscoGarcia on 2010-02-26
Joan A. no sé si acabo d'entendre't. El Firefox 3.6 el tens en català? Són els paquets de castellà del 3.5.7 els que no et deixen tenir-lo en català? No has desinstal·lat la versió anterior?

Has mirat de baixar-te i instal·lar-te el [paquet d'idioma de softcatalà]("http://www.softcatala.org/wiki/Rebost:Paquet_català_per_al_Firefox"), o del [lloc web de firefox]("http://www.mozilla-europe.org/ca/firefox/"), per exemple.

---

### Post by Joan A. on 2010-02-26
Encara no l'he posat en català. El que passa és que a idiomes m'apareixen dos paquets de castellà, el de **Firefox 3.6 **i el de **Firefox 3.5.7**. Aquest darrer el vull eliminar i no puc. Com he explicat abans, el botó *Desinstal·lar* no funciona. Hi ha qualque manera d'eliminar aquest paquet que no sigui a través del navegador?

Gràcies!

---

### Post by SiscoGarcia on 2010-02-27
No acabo d'entendre quin és el paquet que no pots eliminar. Pots adjuntar-nos el resultat d'executar al terminal l'ordre següent?

```
sudo dpkg --get-selections > paquets_instalats.txt
```

El resultat (paquets_instalats.txt) el tindràs a la carpeta principal del teu usuari.

---

### Post by Joan A. on 2010-02-28
Jo només vull eliminar el paquet d'idioma de la versió de Firefox 3.5.7. No et puc adjuntar el que m'has demanat perquè supera el límit permès pel fòrum.

---

### Post by lpargemi on 2010-02-28
> **Joan A. said:**
> Encara no l'he posat en català. El que passa és que a idiomes m'apareixen dos paquets de castellà, el de **Firefox 3.6 **i el de **Firefox 3.5.7**. Aquest darrer el vull eliminar i no puc. Com he explicat abans, el botó *Desinstal·lar* no funciona. Hi ha qualque manera d'eliminar aquest paquet que no sigui a través del navegador?

Gràcies!

Jo aquests darrers dies també he estat potinejant amb les versions del firefox, i també he vist això que tu comentes: des de la pestanya d'extensions no es pot desintal·lar -però si deshabilitar- ni el paquet d'idiomes ni d'altres extensions.

No tinc ni idea del motiu, però simplement ho he ignorat. Podria ser que els paquets d'extensions es facin servir al 3.6 i que per això no els deixi treure. 

Salut

Lluís

---

### Post by Joan A. on 2010-02-28
No és una cosa important i que limiti el rendiment del meu ordinador, però ho tenc entre cella i cella i he estat incapaç d'eliminar el paquet d'idioma. A veure si qualqú ens pot donar una solució.

---

### Post by SiscoGarcia on 2010-03-01
> **Joan A. said:**
> No et puc adjuntar el que m'has demanat perquè supera el límit permès pel fòrum.

Mira d'enganxar-nos només la part que fa referència al firefox, no sé si tens entrades diferents que facin referència a paquets diferents (de la versió 3.5.7 i de la 3.6).

---

### Post by Joan A. on 2010-03-01
Aquí tens els paquets:

[B]firefox                                    install
firefox-3.5                              install
firefox-3.5-branding               install
firefox-3.5-gnome-support     install
firefox-branding                      install
firefox-gnome-support            install[/B]

He pegat una ullada a aquests paquets a **Synaptic**, però a la columna versió instal·lada d'aquests m'apareix el següent:* 3.6 + nobionly -0ubuntu4-mfs-karmic1*.

---

### Post by SiscoGarcia on 2010-03-01
Bé, a la màquina des d'on t'escric ho tenia igual i el que he fet és eliminar els paquets que fan referència al firefox 3.5 (amb això elimines el que fa referència a la versió anterior... i suposo que també eliminaràs el paquet d'idioma), ho deses i després fas el següent:

```
sudo dpkg --set-selections < paquets_instalats.txt
```

Amb la qual cosa recuperes la llista de paquets que tens instal·lats però sense el firefox 3.5, que més o menys és el que volies. Després fas:

```
sudo apt-get -u dselect-upgrade
```

Amb la qual cosa actualitzes la llista de paquets, i ja posats fas:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

de manera que els tindràs tots a l'última versió; evidentment, aquest pas és innecessari pel que tu vols.

Totes aquestes instruccions les he après del mestre (aka papapep) ;)

---

### Post by Joan A. on 2010-03-01
Disculpa, no he entès el primer pas. He d'eliminar els paquets referents a **Firefox 3.5** des de **Synaptic**? Si és així, no esborraré el navegador? Pensa que les versions dels paquets que t'he adjuntat a l'anterior resposta pertanyen a la versió **Firefox 3.6.**

Gràcies!

---

### Post by SiscoGarcia on 2010-03-01
Perdona, no me he explicat clarament. Edites el fitxer paquets_instalats.txt i allà esborres les tres línies que fan referència al firefox 3.5 (les tres del mig que ens has copiat abans). Deses el fitxer i fas el que t'he apuntat abans.

---

### Post by Joan A. on 2010-03-01
No em va bé. Esborr les línies que tú m'has dit i guard els canvis, però quan torn a consultar el document me segueixen apareguent els paquets de **Firefox 3.5**.

---

### Post by SiscoGarcia on 2010-03-01
Al Firefox, si vas a Ajuda>Quant al Mozilla Firefox, també et surt la versió 3.5?

---

### Post by Joan A. on 2010-03-01
Em surt que tenc la versió **Firefox 3.6**.

---

### Post by SiscoGarcia on 2010-03-01
Prova d'instal·lar el paquet de català com expliquen en aquest [altre fil]("http://ubuntuforums.org/showthread.php?t=1418149").

---

### Post by Joan A. on 2010-03-01
M'ha anat bé. Però jo ja tenia el **paquet en castellà del 3.6**. Només vull fer desaparèixer el paquet de la **versió 3.5.7**.

---

### Post by Joan A. on 2010-03-01
Vos adjunt una imatge per a que veieu què és exactament el que me passa.

---

### Post by SiscoGarcia on 2010-03-01
Hola Joan A.

Ja veig quin és el teu problema. Gràficament no hi pots fer res perquè ja no tens el firefox 3.5.7 i per tant no et deixa desinstal·lar-lo des de la finestra de gestió de complements. Caldria saber quin és el nom del paquet exactament i obrint un terminal fer:

```
sudo apt-get remove nom_exacte_del_paquet
```

De tota manera si ja tens instal·lat el paquet d'idioma en català, et deixa seleccionar-lo? Prova de fer-ho per tenir el firefox en català... i ja sé que només vols eliminar aquest paquet ;)

---

### Post by Joan A. on 2010-03-01
Gràcies! Ja he instal·lat el paquet de català. Pero tenc una darrera pregunta. Com puc saber quin és el nom exacte del paquet? :p

Ja veig la llum al final del túnel... Jeje.

---

### Post by SiscoGarcia on 2010-03-03
> **Joan A. said:**
> Com puc saber quin és el nom exacte del paquet?

Això ho desconec. De tota manera, estic observant que entre els complements tens una categoria d'idiomes que jo no tinc, potser perquè només hi tinc el català. Realment vols tenir-ho en dos idiomes?

---

### Post by Joan A. on 2010-03-04
En relació als idiomes, me'n vaig donar compte ahir que altres Firefox no tenen la categoria d'idioma. La veritat no tenc ni idea. Quant el que m'has dit dels dos idiomes, encara que posi Firefox en català i desinstal·li el castellà, el paquet de la versió 3.5.7 segueix.

---

### Post by SiscoGarcia on 2010-03-04
Doncs sento no poder ajudar-te més. Personalment, jo ho deixaria còrrer, però evidentment no ho hem solucionat :(

---

### Post by Joan A. on 2010-03-04
No passa res. Almenys s'ha intentat solventar l'error. Jo he estat cercant el paquet però res de res i ja m'havia fet la idea de deixar-ho córrer. De totes formes, gràcies. :)

---

