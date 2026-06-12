---
title: "Ubuntu 16.04 gestor de programari"
date: 2016-03-23
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2016-03-23
Bones.
Estic provant el nou Ubuntu per tal d'anar creant la nova guia ([https://ca.wikibooks.org/wiki/Guia_Ubuntu/%C3%8Dndex_16.04_LTS](https://ca.wikibooks.org/wiki/Guia_Ubuntu/%C3%8Dndex_16.04_LTS)).
Tinc entès que ja no portarà l'habitual gestor de programari i ara vindrà amb el de Gnome.
Bé, doncs jo no trobo ni un ni altre. Suposo que és un "bug" de la versió de prova.
Algú l'ha provat? O Ubuntu 16.04 o el gestor de programari de Gnome?

---

### Post by wgarcia on 2016-03-24
Jo tinc la versió de prova i tinc els dos centres de programari, el d'Ubuntu i el de Gnome. El de gnome es diu directament "Programari" en la versió en català, i suposo que serà l'únic que es veurà si la instal·lació és de zero. En el meu cas com que he actualitzat des de la versió 15.10, encara tinc el centre de programari de l'Ubuntu, que suposo que puc ja desinstal·lar perquè ja no l'actualitzaran més.

---

### Post by Miquel Ubuntero on 2016-04-02
Hola Garcia, gràcies per respondre.
Jo em vaig instal·lar la Daily Build i avui l'he actualitzat.
Tot i actualitzar no tinc o no trobo cap gestor de programari.
Sabries dir-me sisplau com puc des de Terminal:
-Cercar si tinc instal·lat el Gnome gestor?
-Com instal·lar el Gnome gestor programari?

---

### Post by Miquel Ubuntero on 2016-04-02
Hola de nou.
Disculpeu si potser la pregunta era prou bàsica. He cercat al goolge i he trobat la solució:
 sudo add-apt-repository ppa:ubuntu-desktop/gnome-software
sudo apt-get update && sudo apt-get install gnome-software

---

### Post by goofprog on 2016-04-02
I guess.
Hola.
Try sudo apt-get install @gnome-desktop or
sudo apt-get install @gnome
I am not sure which one works.
I guess meho.  I guess.

---

### Post by Miquel Ubuntero on 2016-04-03
Hi googprog
The solution is in my last post
sudo add-apt-repository ppa:ubuntu-desktop/gnome-software
sudo apt-get update && sudo apt-get install gnome-software 

We are grateful for your help, but we should respect the forum catalan rules and we should only write in catalan language.
Best regards,
Miquel Ubuntero.

---

### Post by wgarcia on 2016-04-04
Jo la tinc instal·lada sense cap "ppa". Des del  Tauler s'ha d'entrar "Programari" per accedir-hi. El paquet es diu "gnome-software"

```

$ dpkg -l gnome-software
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  gnome-software 3.20.0-0ubun amd64        Software Center for GNOME

```

---

