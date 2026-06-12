---
title: "Idioma Login"
date: 2014-01-20
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2014-01-20
Bones.
Estic provant Edubuntu 14.04 i no veig com canviar l'idioma des de la pantalla de "login".
Els meus dubtes són 2:
-Hi ha manera de canviar l'idioma abans d'entrar (al suport d'idioma hi tinc Anglès i català)?
-Això que no puc fer amb Edubuntu, també passa amb Ubuntu?
Gràcies.

---

### Post by wgarcia on 2014-01-20
Em sembla que també passa amb Ubuntu. És una funcionalitat que hi havia al gestor d'entrada que s'utilitzava abans (GDM) però que encara no s'ha implementat en el que s'utilitza ara (lightdm).

---

### Post by Miquel Ubuntero on 2014-01-25
Gràcies wgarcia.
Saps doncs, si hi ha alguna manera per canviar l'idioma un cop he logat?
Espero no haver d'insta&#320;lar 2 s.o. paralelament per poder treballar en altres idiomes!

---

### Post by CarlesOriol on 2014-01-25
Jo m'hi vaig trobar fa uns dies.

La única solució va ser anar als "Paràmetres de systema" > comptes d'usuari i canviar l'idioma d'aquest (i fer un tornar a la pantalla d'entrada)

Si algú cap solució mes senzilla, un cop de mà serà ben rebut.

---

### Post by wgarcia on 2014-01-26
Hi ha un paràmetre al fitxer de configuració de lightdm ( /etc/lightdm/lightdm-gtk-greeter.conf ) que permet incorporar el canvi de llengua a la pantalla d'entrada (s'ha d'afegir una línia a aquest fitxer que posi: show-language-selector=true .

A Ubuntu però, si es fa servir Unity, no s'utilitza la configuració predeterminada de lightdm (lightdm-greeter) sinó una preparada especialment per Unity (unity-greeter), i per tant ignora aquest paràmetre i no és pot establir en cap dels fitxers de configuració. 

Per tant de moment l'única opció per tenir aquesta configuració a la pantalla d'entrada és instal·lar aquest paquet: lightdm-gtk-greeter.

Per exemple a aquest article expliquen com fer-ho des d'un "ppa":

[http://ubuntuhandbook.org/index.php/2014/01/install-lightdm-gtk-greater-1-7-1-ubuntu/](http://ubuntuhandbook.org/index.php/2014/01/install-lightdm-gtk-greater-1-7-1-ubuntu/)

---

### Post by Miquel Ubuntero on 2014-02-23
Hola de nou. Pot ser una mica tard?
Bé, he provat de fer el que diu Garcia però no me n'he sortit. No puc donar gaires detalls perquè ho vaig provar fa uns dies i no ho recordo bé.
Avui que he tingut la necesitat de logar-me en un altra idioma, he provat l'opció del Carles. Molt senzilla i m'ha funcionat. Així doncs, ja que per a mi m'està bé, ho dono per solucionat.
Gràcies a tots dos.
Salut!

---

