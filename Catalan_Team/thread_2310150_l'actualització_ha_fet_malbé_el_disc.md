---
title: "l'actualització ha fet malbé el disc"
date: 2016-01-16
forum: Catalan Team
---

### Post by josep-maria on 2016-01-16
A un pc hi tenia l'ubuntu 14.04, però no n'estic segur. Fa tres o quatre setmanes vaig fer una actualització. Quan era a mig descarregar, es va quedar tot mort. La pantalla deia  "grub rescue" i d'aquí no sortia. He fet reparar el pc, li han canviat el disc dur perquè s'havia fet malbé. No han pogut ficar-hi l'ubuntu si abans no hi ha cap windows. Hi han ficat el windows 7. No han pogut ficar-hi l'ubuntu. Sembla que el windows 7 no permet fer-ho. Ara provaran amb un windows més antic.

Què cal fer per insta&#322;lar l'ubuntu sense cap sistema operatiu funcionant-hi?
Com puc ficar-hi l'ubuntu 14.04 però amb l'escriptori gnome?

---

### Post by wgarcia on 2016-01-17
Potser millor si tractem cada tema per separat. Sí que es pot instal·lar l'Ubuntu al costat del Windows 7. La clau és saber com té l'ordinador configurat l'arrencada. Abans els ordinadors feien servir un petit programa abans de l'arrencada del sistema operatiu que es deia BIOS. Des de fa uns anys els ordinadors s'envien amb un nou sistema que es deiu UEFI, i que permet coses com el "Secure Boot" (arrencada segura), que exigeix que el sistema operatiu que s'arrenca estigui signat per una autoritat reconeguda. Això ho va fer servir Microsoft per posar una mica més difícil la instal·lació de sistemes alternatius al Windows. Però des de fa unes quantes versions l'Ubuntu, i la resta de distribucions Linux, compten amb versions signades que es poden instal·lar sota "Secure boot". Per tant hi ha unes quantes coses que no entenc en el que expliques:

1) En la meva opinió no hi ha cap problema d'instal·lar l'Ubuntu, o qualsevol altre sistema Linux, si no n'hi ha Windows al disc. El més fàcil és configurar el sistema com a "Legacy", o si es vol instal·lar l'arrencada a la partició "Uefi", l'instal·lador d'Ubuntu  ja et dóna aquesta opció.

2) Si es vol instal·lar el Windows al costat de l'Ubuntu, tampoc no hi ha cap problema. Convé primer instal·lar el Windows, i un cop instal·lat, fer la instal·lació de l'Ubuntu. 

Quant a tenir Gnome, no sé si et refereixes a la versió d'escriptori clàssic del Gnome, o la més moderna. Si vols la versió clàssica del Gnome ara hi ha una versió d'Ubuntu que es diu Ubuntu Mate, que porta aquest escriptori. Si vols la versió moderna també hi ha un sabor d'Ubuntu amb l'escriptori modern de Gnome, i es diu tal qual, Ubuntu Gnome.

---

### Post by josep-maria on 2016-01-18
Com es fa per configurar el sistema com a Legacy? Perquè el PC no té cap sistema operatiu.

Jo només he vist un gnome, deu de ser la versió antiga de sempre. Quan descarregues d'nternet el disc de l'ubuntu, no et pregunta pas quin escriptori vols. Quan l'insta&#320;les, es pot triar l'ubuntu mate?

---

### Post by wgarcia on 2016-01-18
Per configurar l'arrencada com a "Legacy" has d'accedir al menú inicial de configuració, abans que arrenqui cap sistema operatiu. Això depèn de cada ordinador, però sol accedir-se amb F2 o a vegades F4 si recordo bé. És l'antic menú de Bios. 

La versió que descarregues d'Ubuntu des de la pàgina d'Ubuntu és la que porta l'escriptori Unity. Per instal·lar els sabors (Kubuntu, Lubuntu, Xubuntu, Ubuntu Mate o Ubuntu Gnome), cadascuna de les quals porta un escriptori diferent, has d'anar a la pàgina de descàrregues d'aquestes versions. També es pot instal·lar l'escriptori que vulguis un cop instal·lat qualsevol d'aquestes versions, però és més fàcil si ja descarregues el sabor corresponent. 

Per descarregar l'Ubuntu Mate, que porta l'escriptori Gnome clàssic, o millor dit una versió que ha continuat aquest paradigma d'escriptori, pots anar a:
[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

---

### Post by josep-maria on 2016-01-20
Ja he anat a [https://ubuntu-mate.org](https://ubuntu-mate.org), i he descarregat un arxiu que es diu: ubuntu-mate-15.10-desktop-i386.iso.torrent.
Però aquest arxiu només té 45 kB. És normal això? Si l'arxiu està bé, què cal fer? Vull dir, el gravo a un CD?
I podré insta&#322;lar l'ubuntu al meu PC ficant-hi el disc i reengegant, com sempre?

---

### Post by wgarcia on 2016-01-20
Aquest fitxer és un enllaç "Torrent", si fas doble clic sobre ell se t'hauria d'obrir l'aplicació "Transmission" i baixar-te la imatge "iso" normal. Al final hauràs de gravar aquest iso normal per fer la instal·lació.

El sistema Torrent és un sistema que permet baixar-se els fitxers més ràpid, perquè fa servir un sistema de "parells", és a dir si hi ha altres usuaris que tinguin el mateix fitxer i el transmission obert, l'aprofita per baixar el fitxer de forma cooperativa.

---

### Post by josep-maria on 2016-01-21
He pogut descarregar l'ubuntu-mate i instalar-lo al pc. Té l'escriptori bo, tal com jo volia. I moltes més millores.

A&#320;leluia! Queden un parell de preguntes per fer, però a un altre fil.

Moltes gràcies.

---

