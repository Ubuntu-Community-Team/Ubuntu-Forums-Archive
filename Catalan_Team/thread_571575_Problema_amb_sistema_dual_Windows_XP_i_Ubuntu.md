---
title: "Problema amb sistema dual Windows XP i Ubuntu"
date: 2007-10-09
forum: Catalan Team
---

### Post by Santor on 2007-10-09
Hola!
Primer de tot, hola a tothom, estic molt il·lusionat per entrar a formar part d'aquesta comunitat. Estic estudiant un cicle de grau superior d'informàtica i m'ha interessat el poder tenir un sistema operatiu alternatiu a Windows.
M'he comprat un PC fa 2 setmanes amb 2 disc durs, en el que m'han posat Windows XP en un i Ubuntu a l'altre . Per culpa del Norton Ghost 2003 se m'ha fastidiat el gestor d'arranc del Windows (no el MBR), evidentment puc continuar entrant a Ubuntu. Tenia pensat primer transferir les dades del disc dur de Windows al de Linux per fer còpies de seguretat (ja que no hi puc accedir), però quan provo d'accedir a l'esmentat disc dur des de Ubuntu m'apareix un missatge que em diu que l'accés a aquest disc dur està restringit a l'administrador per qüestions de seguretat. He llegit per vàries pàgines web que l'usuari d'administrador (root) està desactivat per defecte. Un professor d'informàtica m'ha explicat que si vaig a la consola i escric "sudo passwd root" podré escriure una contrassenya per l'administrador i podré accedir al disc dur de Windows. Algú m'ho pot confirmar, siusplau? Moltes gràcies per la vostra col·laboració.
Nota: És curiós però des de Windows no puc veure les particions de l'Ubuntuperò al revés si. No sé si serà rellevant però per si de cas ho comento, gràcies.

---

### Post by Ferri on 2007-10-09
No necessites activar root per fer còpies:```
sudo cp ORIGEN DESTI
```
et permet copiar el que vulguis (si vols copiar subcarpetes has d'afegir -r; posa cp --help per la llista d'opcions).
Efectivament, linux pot llegir particions Windows com FAT16, FAT32 i NTFS, en canvi Windows no pot fer-ho en particions ext3 o Reiserfs, que són les més habituals a linux.
Hi ha programes que permeten que Windows llegeixi particions linux i alguns són lliures. Jo en tinc un instal·lat però em temo que no recordo el nom (això és del sovint que faig servir Windows ;-))

---

### Post by CarlesOriol on 2007-10-09
o 

gksudo nautilus

Si vols recuperar el hasefrog entres amb el disc d'insta&#320;lació, selecciones recuperació per consola i un cop allà fas bootfix.

Així podras anar fent copies de tot tranquilament fins que l'esborris del disc.

---

### Post by Santor on 2007-10-09
Hola de nou!
Perdoneu pel haver tardat tant a respondre. Moltes gràcies pels vostres consells, miraré a veure si ho puc resoldre. Ja us comentaré  si ho aconsegueixo resoldre o no.

---

### Post by Santor on 2007-10-09
Hola!
M'ho he estat mirant i tinc dubtes ja que soc nou en l'ús de Ubuntu, per lo de copiararxius del disc dur de windows al de linux, com ho hauria de fer amb el codi "sudo cp ORIGEN DESTI"?
Haig d'escriure, per exemple: "sudo cp C:\Documents and Settings\Usuari\Mis documentos home\oriol\seguretat windows xp"?
Sinó com ho haig de fer? Perdoneu per les molèsties.

---

### Post by Ferri on 2007-10-10
> **Santor said:**
> "sudo cp C:\Documents and Settings\Usuari\Mis documentos home\oriol\seguretat windows xp"
Et falta una barra abans de "home".
Tot i que les possibilitats de la línia de comandaments cón més grans, potser és millor que comencis per l'opció del CarlesOriol, que et permetrà fer-ho en mode gràfic. Si fas servir KDE en lloc de GNOME, posa "kdesu konqueror" al quadre que s'obre en fer alt+F2.
Nota: després d'escriu l'anterior, he recordat que a la línia de comandaments algun cop he tingut problemes amb les carpetes amb espais. Aquest problema en mode gràfic te l'estalviaràs.

---

### Post by RainCT on 2007-10-10
> **Santor said:**
> Haig d'escriure, per exemple: "sudo cp C:\Documents and Settings\Usuari\Mis documentos home\oriol\seguretat windows xp"?

No, aquí hi ha diversos fallos:

1. Les barres a Linux són sempre cap a l'esquerra "/", al contrari que les del Finestres ("\").

2. Abans del home et falta una barra /, per indicar el directori arrel de l'insta&#320;lació.

3. A Linux no hi ha cap dispositiu que es digui "C:" ni res semblant. Sinó que els dispositius s'anomenen (i tenen un arxiu cadascú amb el mateix nom) "/dev/nom", on nom pot ser hdXN o sdXN (X: lletra minúscula a-z, indica el disc dur; N: número de la partició; sí comença amb hd o sd depèn de quin fabricant sigui el disc), i s'accedeix a les dades que hi ha a través d'un punt de muntatge, que acostuma a ser /media/nom (el nom és el mateix que al /dev. algunes distribucions de Linux fan servir /mnt/ en lloc de media, ho dic només perquè ho sàpigues si et trobessis amb el cas).

4. Si una adreça conté espais, a la terminal sempre convé posar-la entre cometes ("...").

Així doncs podria ser per exemple «sudo cp -r "/media/sda1/Documents and Settings/Usuari/Mis documentos" /home/oriol/seguretat win xp/» (el directori "seguretat win xp" ha d'existir amb anterioritat), en el cas de que el Finestres estigui a la primera partició del primer disc dur.


Però com ja t'han dit per a aquest cas et serà millor simplement:
 - Prémer Alt + F2
 - Escriure-hi: gksudo nautilus /              (si fas servir l'Ubuntu)

Salut

---

### Post by RainCT on 2007-10-10
Se m'oblidava dir que del "root" ja te'n pots oblidar, a l'Ubuntu (i la distribució en la que es basa, Debian) s'utilitza l'ordre "sudo" (o la seva versió gràfica "gksudo") per tal d'aconseguir privilegis administratius.

Aquesta és més segura (per varis motius) i permet que hi pugui haver varis usuaris administradors.

També, si tens interès en aprendre més sobre la terminal, et recomano llegir [aquest document](https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/interpret_comandes).

---

