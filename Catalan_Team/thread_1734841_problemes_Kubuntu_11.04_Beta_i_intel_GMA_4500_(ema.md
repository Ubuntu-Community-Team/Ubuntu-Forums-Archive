---
title: "problemes Kubuntu 11.04 Beta i intel GMA 4500 (emachines e725)"
date: 2011-04-20
forum: Catalan Team
---

### Post by franz666es on 2011-04-20
Hola, tinc un portàtil eMachines E725 amb targeta gràfica integrada intel GMA 4500. Quan faig servir Kubuntu beta amb el kernel 2.6.35 funciona perfectament i fins i tot tinc acceleració de gràfics. Quan instal·lo el kernel 2.6.38 el sistema arrenca normal, però la pantalla s'enfosqueix totalment (com si s'apaguès la retroil·luminació) fent que sigui pràcticament imposible veure-hi res tant en el mode gràfic com en el mode de recuperació. El driver és el correcte (el controlador d'intel deel xorg-Xserver) i ja he probat a generar un fitxer xorg.conf per mirar de sol·lucionar-ho.

Alguna idea?


Gràcies per endavant i si necessiteu que publiqui el contingut d'algun fitxer de configuració, dieu-m'ho, si-vos-plau

---

### Post by iSoc on 2011-04-21
> **franz666es said:**
> Hola, tinc un portàtil eMachines E725 amb targeta gràfica integrada intel GMA 4500. Quan faig servir Kubuntu beta amb el kernel 2.6.35 funciona perfectament i fins i tot tinc acceleració de gràfics. Quan instal·lo el kernel 2.6.38 el sistema arrenca normal, però la pantalla s'enfosqueix totalment (com si s'apaguès la retroil·luminació) fent que sigui pràcticament imposible veure-hi res tant en el mode gràfic com en el mode de recuperació. El driver és el correcte (el controlador d'intel deel xorg-Xserver) i ja he probat a generar un fitxer xorg.conf per mirar de sol·lucionar-ho.

Alguna idea?


Gràcies per endavant i si necessiteu que publiqui el contingut d'algun fitxer de configuració, dieu-m'ho, si-vos-plau


Hola company em passa exactament el mateix que a tu, poso el Kubuntu amb una maquina virtual i em va perfecte en cambi, si poso el Natty alpha, o Natty Beta 2 no funciona Unity nomes em funciona el unity 2d. Tinc un toshiba satelite pro U-400 amb la mateixa targeta **GMA 4500** . No se quin driver tinc posat per que no hi entenc gaire, pero si o soluciones m´aniria be també saber com ho has fet per poder arreglar, si es que es pot un salut company.

---

### Post by wgarcia on 2011-04-21
iSoc: el teu problema sembla diferent que el de franz666es, ell està fent servir KDE i tu Gnome. 

Pel problema de franz666es a veure si alguns del kubuntaires que volten per aquí poden donar una mà, sembla un problema d'habilitació de la llum de fons de la pantalla. 

Per iSoc, millor obre un altre fil específic per al teu problema.

---

### Post by franz666es on 2011-04-22
Hola Wgarcia:

Gràcies per la resposta- De fet en el Kubuntu també tinc instal·lats els escriptoris de gnome (de vegades en faig servir un o l'altre, que hi farem!) i tant amb el gnome classic com amb el gnome amb unity la retroill·luminació queda com desconnectada en quant faig servir el kernel de natty, però no amb el propi de maverick. He probat a reinstal·lar el kernel, els headers de linux, el xorg, el driver d'intel... i res. 

Quant a l'equip, per a més dades, porta un iPentium T4500 a 64 bits, 2 Gb de memòria i el xip gràphic és de la sèrie GMA 45. Quan comprobo la configuració de pantalla i l'openGL em diu que, efectivament, fa servir els drivers d'Intel :( Vaig totalment despistat

---

### Post by franz666es on 2011-04-29
Bé, he descarregat les versions per amd64 i i386 d'UBUNTU natty i el problema continua sent el mateix que amb la beta de KUBUNTU. La retroalimentació de la pantalla roman desactivada tot i que el sistema funciona correctament. Potser un problema del kernel amb el T4500 i la GMA45? Alguna idea?

---

### Post by wgarcia on 2011-04-29
Hi ha molts informes d'aquest problema, i sembla estar relacionat amb el nucli que fa servir la nova versió (el 2.6.38 ). 

He vist que se suggereixen dues solucions:

1) iniciar amb un nucli més antic, si hi ha algun al grub. Per veure el grub si no et surten en començar, tot al principi quan el sistema ha passat les comprovacions inicials i comença a carregar el grub s'ha de prémer la tecla "majúscula" (SHIFT). 

2) entrar, i des d'una terminal donar la comanda:

sudo setpci -s 00:02.0 F4.B-0

clar que si no veus res serà difícil entrar-la.

---

### Post by franz666es on 2011-05-04
Gràcies Wgarcia. 

El problema és que així havia de introduir l'ordre en cada reinici. Al final he optat pel següent:

En iniciar he editat /etc/rc.local i he afegit com a penúltima línia 
setpci -s 00:02.0 F4.B=00
Llavors he editat el GRUB_CMDLINE_LINUX_DEFAULT= indicant com a opcio "quiet splash acpi_osi=Linux"
i llavors he actualitzat el grub2 

No és la solució òptima, però funciona, gràcies un altre cop

---

