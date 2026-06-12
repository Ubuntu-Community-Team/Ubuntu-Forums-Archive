---
title: "Modificar  nom ditribució"
date: 2010-01-18
forum: Catalan Team
---

### Post by tanreb20 on 2010-01-18
Hola amics!

Fa uns dies vaig afegir els repositoris del linux mint al meu ubuntu, pero tal e tenir certs programes, per ara el vui esborrar, ja que no el faig servir la vritat.

Apart de esborrar el repo, hi ha un detall.

Quan el vaig instalar em va modificar el nom de la distribució de tal manera que ara es pensa que e sun "Linux Mint 8", tant en el grub, com en tot... i no em mola jeje.

Apart m'ha canviat la pagina de inici, el gdm vaja, i no se ocm es canvia, algu em pot dir com canviar el nom i el "tema" del gdm?

(ubuntu 9.10)

---

### Post by kukat on 2010-01-20
Per canviar el GDM:

Sistema --> Administració --> Pantalla d'Entrada, i canvies el tema per un que no siga del Linxu Mint 8 (pots trobar-ne un fum al web Gnome Look)

I respecte al grub, crec qeu tens que modificar algun paràmetre al fitxer "grub.cfg" [http://grub.enbug.org/grub.cfg(anglès](http://grub.enbug.org/grub.cfg(anglès))

per editar el fitxer --> sudo gedit /boot/grub/grub.cfg


També pots ficar-li imatges de fons al Grub 2 i coses per l'estil: 

[http://www.dacostabalboa.com/es/personalizar-grub-2-de-ubuntu-9-10/5300](http://www.dacostabalboa.com/es/personalizar-grub-2-de-ubuntu-9-10/5300) (castellà)

---

### Post by tanreb20 on 2010-01-20
Pero ara tinc un problema.

Al intentar afegir una repository em salta que no coincideix el nom de la distribucio, evidentment intenta trobar "ubuntu" i troba "linux mint", com puc canviar aixo?

Actualment el nom de la distribucio(segons el ubuntu tweak) es linux mint, aixo es pot canviar a má?

---

### Post by kukat on 2010-01-21
Quin missatge et surt ??? 

Crec que el que hauries de fer es editar el fitxer "sources.list"

sudo gedit /etc/apt/sources.list

i afegir els repositoris del Ubuntu 9.10 Karmic Koala...

Et passe els que tinc jo també al Karmic Koala, en el fitxer adjunt (el passe comprimit, sinó no em deixa pujar-lo) ;)



PD: Algú em pot confirmar si "repositoris" està ben dit en català? :D

---

