---
title: "problemes de dependències"
date: 2016-06-22
forum: Catalan Team
---

### Post by jinglada on 2016-06-22
Bon dia!

Volia instal·lar el xvidcap per capturar uns flaixos que em surten de tant en tant a l'angle superior esquerre de la pantalla i poder-vos-els mostrar per a veure si podíeu esbrinar què són, i ara el problema el tinc amb les dependències.

Què he de fer? Gràcies a la bestreta!

joan@joan-Aspire-E1-572:~/Baixades$ sudo dpkg -i xvidcap_1.1.5rc2_i386.deb
S'està seleccionant el paquet xvidcap prèviament no seleccionat.
(S'està llegint la base de dades… hi ha 1343499 fitxers i directoris insta&#320;lats actualment.)
S'està preparant per a desempaquetar xvidcap_1.1.5rc2_i386.deb…
S'està desempaquetant xvidcap (1.1.5rc2)…
dpkg: **problemes de dependències impedeixen la configuració de xvidcap**:
 xvidcap depèn de libglade2-0 (>= 1:2.5.1); tot i així:
  El paquet libglade2-0:i386 no està insta&#320;lat.
 xvidcap depèn de liblame0 (>= 3.96.1); tot i així:
 xvidcap depèn de libpango1.0-0 (>= 1.14.5); tot i així:
  El paquet libpango1.0-0 no està insta&#320;lat.
 xvidcap depèn de libxmu6; tot i així:
  El paquet libxmu6:i386 no està insta&#320;lat.
 xvidcap depèn de scrollkeeper; tot i així:

dpkg: s'ha produït un error en processar el paquet xvidcap (--install):
 problemes de dependències - es deixa sense configurar
S'estan processant els activadors per a man-db (2.6.7.1-1ubuntu1)…
S'estan processant els activadors per a mime-support (3.54ubuntu1.1)…
S'estan processant els activadors per a gnome-menus (3.10.1-0ubuntu2)…
S'estan processant els activadors per a desktop-file-utils (0.22-1ubuntu1)…
S'estan processant els activadors per a bamfdaemon (0.5.1+14.04.20140409-0ubuntu1)…
Rebuilding /usr/share/applications/bamf-2.index...
S'estan processant els activadors per a menu (2.1.46ubuntu1)…
S'han trobat errors en processar:
 xvidcap

---

### Post by wgarcia on 2016-06-22
Sembla que la versió que estàs intentant instal·lar depèn d'altres paquets que no tens. Coses que es poden provar:
```
sudo apt-get install -f
```
Aquesta ordre a vegades arregla problemes de paquets mal configurats als quals els falta una dependència.

Ara bé, també pots desinstal·lar el xvidcap i provar el gtk-recordmydesktop, que pots instal·lar directament dels repositoris de l'Ubuntu:
```
sudo apt-get remove xvidcap
```
```
sudo apt-get install gtk-recordmydesktop
```

---

### Post by jinglada on 2016-06-22
Gràcies wgarcia! De fet ja tinc instal·lat el recordmydesktop, però em dona aquest error [IMG]http://ubuntuforums.org/attachment.php?attachmentid=269707&d=1466573736[/IMG]

---

### Post by wgarcia on 2016-06-22
Mira a "Avançat" quina carpeta està establerta per desar els fitxers.

---

### Post by jinglada on 2016-06-22
Gràcies, wgarcia. Semblo un principiant! ;-)

---

### Post by jmaspons on 2016-06-24
Pels problemes de dependències pots provar d'instal·lar el paquet mitjançant el gdebi. A diferència de dpkg, gdebi permet la resolució de dependències de manera automàtica.

> 
apt install gdebi
gdebi xvidcap_1.1.5rc2_i386.deb


---

