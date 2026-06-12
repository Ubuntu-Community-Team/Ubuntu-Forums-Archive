---
title: "Vuze i 10.04"
date: 2010-05-20
forum: Catalan Team
---

### Post by idrox on 2010-05-20
Hola!

Fa un parell de dies que he fet la actualització al 10.04, i em va tot perfecte, excepte el Vuze (o Azureus, cadascú li diu com vol) que no se m'obre, clico la icona, però no passa res. Miro el monitor del sistema però tampoc es veu que s'executi res.


Cal dir que prèviament (al 9.10) em funcionava de conya. I ara, directament ni se m'obre!

(no he detectat que em passi amb cap altre programa, però no seria estrany, ja que fa poc que he actualitzat...)

Moltes gràcies!

---

### Post by wgarcia on 2010-05-21
És un error conegut ([https://bugs.launchpad.net/ubuntu/+source/swt-gtk/+bug/569461](https://bugs.launchpad.net/ubuntu/+source/swt-gtk/+bug/569461)). Sembla que de moment ho arregla, si des d'una terminal executes les comandes següents:

cd /usr/share/java
sudo ln -s swt-gtk-3.5.1.jar swt.jar

---

### Post by idrox on 2010-05-21
Moltissimes gràcies! Primer no em funcionava el que has dit, però he vist que en comptes de "java" has escrit "jave" xD

Així doncs, la forma correcta és:

cd /usr/share/java
sudo ln -s swt-gtk-3.5.1.jar swt.jar

---

### Post by wgarcia on 2010-05-22
De res, he editat la meva resposta original perquè ho posi bé. Recorda't sisplau de canviar el tema a "Solved" amb "Eines" a dalt de la pàgina.

---

