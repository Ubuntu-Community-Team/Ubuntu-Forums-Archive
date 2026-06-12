---
title: "Kde"
date: 2007-10-25
forum: Catalan Team
---

### Post by Josep Maria on 2007-10-25
Hola : 
Com puc instal.lar l'escriptori KDE sobre un Ubuntu 7.10 amb Gnome?
Provo de instal.lar el paquet Kubuntu amb synaptic, però em demana que insereixi el disc d'instal.lació de Gutsy i jo no el tinc, ja que em vaig actualitzar Feisty.
Ademés em demana que el dis correspongui a una beta d'Ubuntu.

Gràcies.

Josep Maria

---

### Post by jodufi on 2007-10-25
Hola Josep,

No et seria més fàcil instal·lar Kubuntu?

---

### Post by CarlesOriol on 2007-10-25
jodufi: Això no cal posar-ho, els dos sistemes son el mateix amb diferents escriptoris. Si us plau no emboliquis al personal.

Obre amb el synaptic paràmetres > repositoris > Programari de tercers i desmarques el cdrom.

Un cop fet això actualitzes les fonts i insta&#320;les kubuntu-destop i ja està! Pots finalitzar la sessió i iniciar de nou en kde.

---

### Post by Josep Maria on 2007-10-25
Hola amics :
He entrat al synaptic, paràmetres, repositoris, programari de tercers i no veig el CD .
He desactivat dues opcions que no portaven http// davant, i he "refrescat" el synaptic, però en voler instal·lar el Kubuntu Dektop em torna a sortir : Si us plau, inseriu el disc etiquetat:
Ubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.1)
en la unitat /cdrom/
Jo vaig actualitzar des d'Internet, i és clar que no he fet servir aquest disc.
La única cosa que se'm acudeix, es que per actualitzar vaig seguir les instruccions de la pàgina Web de l'ubuntu, i vaig afegir unes fonts a la terminal. Però la pàgina ha canviat, i ara no recordo bé quins eren.

El motiu de voler fer-ho així, és que volia provar l'escriptori KDE sense haver d'instal.lar Kubuntu, ja que amb Gnome em va costar una mica, però ara funciona tot perfectament des de fa mesos.

Gràcies a tots dos.

---

### Post by papapep on 2007-10-25
Edita /etc/apt/sources.list i fica un # davant la línia que posi CDROM.

```
sudo nano /etc/apt/sources.list
```

Amb Ctrl+X deses els canvis.

---

### Post by Josep Maria on 2007-10-25
Hola Papapep :
Al començar, a sources list tinc això : 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.1)]/ gutsy main restricted

és aquí on poso la #?

Josep Maria

---

### Post by Josep Maria on 2007-10-25
Collons! ets un geni Papapep : ho he fet i ja funciona, es veu que al actualitzara la beta s'havia quedat aquesta línia al sources list.
Em pots explicar una mica el que fa el fitxer sources list?

Josep Maria

---

### Post by papapep on 2007-10-25
Mira, aquí:

[https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/PMF_UbuntuCat](https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/PMF_UbuntuCat)

tens una mica d'explicació del tema. Encara està en construcció, però això ja hi és. ;-)

---

### Post by Satboy on 2007-10-25
Hola,
 Magnífica pàgina, **Papapep**. 
 Moltíssimes gràcies!

 Siau! ;-)

---

