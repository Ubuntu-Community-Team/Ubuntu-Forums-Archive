---
title: "[SOLVED] Instal·lar adobe reader"
date: 2007-06-08
forum: Catalan Team
---

### Post by Curial on 2007-06-08
A Maria,

Abans de tot, perdoneu què estigui tant verd.

Estic intentant instal·lar l'Adobe reader i m'he trobat amb uns quants dubtes.
1)  He triat la opció d'OS linux, tenia dues opcions de baixar l'arxiu d'instal·lació:
com a ".rpm" ó "tar.gz", me les he baixat totes dues.
2) La .rpm no em deixa executar-la : diu que l'arxiu no està implementat.
La tar.gz la he descomprimit i he intentat executat l'arxiu de text executable des del terminal.
He cregut que s'havia d'instal·lar  a /usr/local/adobe/adobe... , però resulta que tampoc puc crear
els directoris adobe amb mkdir perquè no tinc permisos. He provat amb sudo regid però es veu que no son per directoris.

Existeix algun llistat de comandes?
O de conceptes com per exemple muntar una unitat? (porto un cacau mental impressionant)

Com se solen instal·lar els programes, cal passar pel terminal?

Gràcies per endavant.

---

### Post by kukat on 2007-06-08
Jo també estic molt verd, però si vols provar açó, igual funciona :D

sudo apt-get install [programa a instalar]

Crec que és una cosa així. Per a instalar determinades coses així funciona. Amb el amarok ho instale així:
sudo apt-get install amarok


Bé, si funciona serà la meva primera aportació al món lliure. :)

---

### Post by Ferri on 2007-06-08
El millor és instal·lar-lo fent servir els repositoris de Medibuntu. Si no els tens activats, fes això, des de la línia de comandaments:
```
sudo su -c 'echo deb http://packages.medibuntu.org/ feisty free non-free >> /etc/apt/sources.list'
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
I després:
```
sudo aptitude install acroread
```

---

### Post by RainCT on 2007-06-08
[En resposta a kukat]

Cert, la millor manera d'insta&#320;lar programes a l'Ubuntu és amb `sudo apt-get install <nom del programa>` o bé des de l'interfície gràfica, a `Sistema -> Administració -> Gestor de Paquets Synaptic` (o d'altres variants de l'apt, com l'aptitude).

---

### Post by Curial on 2007-06-08
El problema que estic tenint és que no se amb quin nom haig de fer la insatl·lació, en aquest cas és l'Adobe Reader, he posat però totes les combinacions (adobe,adobereader,acroread,etc,etc) i em diu que:No s'ha pogut trobar cap paquet amb un nom o descripció que coincideixi amb......

Què faig malament?

---

### Post by orestesmas on 2007-06-08
Això et passa perquè l'Acrobat Reader NO és lliure i per tant no està als repositoris "normals" d'ubuntu.

Fes el que t'ha dit Ferri: es tracta d'activar els repositoris de "Medibuntu" que contenen tots els programes "problemàtics" pel que fa a les llicències.

---

### Post by Curial on 2007-06-09
Efectivament, he fet el que ha dit en Ferri pero ho  dec haver fet malament el primer cop.
Ja el tinc instal·lat i funcionant.

Gràcies a tots.

---

