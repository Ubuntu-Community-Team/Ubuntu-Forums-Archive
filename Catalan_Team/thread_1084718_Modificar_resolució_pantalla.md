---
title: "Modificar resolució pantalla"
date: 2009-03-02
forum: Catalan Team
---

### Post by AnFoAr on 2009-03-02
Bona tarda a tothom:

Suposo que és una tonteria, però no sé com es fa i li vaig donant voltes sense èxit. Doncs bé, es tracta de canviar la resolució de la pantalla, estic treballant a 800 x 600 i voldria canviar-ho a 1024 x 768 i tenir més colors. He anat a "configurar ajustes de pantalla" i només tinc la opció de 800 x 600 o 640 x 480. He mirat de tort i de través per tot arreu, i no ho he trobat enlloc. 

He fet un lspci, i entre d'altres coses em posa:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display 

Gràcies

---

### Post by kukat on 2009-03-03
Hola!

Estaria bé saber quin Ubuntu fas servir!

Gràcies!

---

### Post by AnFoAr on 2009-03-03
> **kukat said:**
> Hola!

Estaria bé saber quin Ubuntu fas servir!

Gràcies!


Bona nit,

L'ubuntu que faig servir és la versió 8.1
Vaig baixar-me un.iso i en vaig fer un disc d'arrancada i el vaig instal.lar juntament amb el windows.

---

### Post by torracastanyes on 2009-03-03
No conec aquesta tarja, però darrerament he tingut algun problema gràfic pels canvis que hi ha hagut a l'xorg.conf.

L'ultima vegada em va ajudar el programa "xdebconfigurator". Aquí hi ha una petita explicació :

[http://www.esdebian.org/articulos/24057/configuracion-debian-post-instalacion](http://www.esdebian.org/articulos/24057/configuracion-debian-post-instalacion)

---

### Post by kukat on 2009-03-03
Pot ser que tingues els controladors de maquinari privatius per activar? Ves a "Sistema", "Administració","Controladors de Maquinari" i verifica que no tens la targeta gràfica per a activar.

---

### Post by bratac on 2009-03-23
Bones,

Ens pots dir quina targeta gràfica tens?

gràcies

---

### Post by PatrickVogeli on 2009-03-23
la grafica es una SiS integrada en placa... no sembla que li hagi d'anar massa be, al menys segons diuen aqui:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/332140](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/332140)

salut!

---

