---
title: "automount en xfce xubuntu"
date: 2011-01-07
forum: Catalan Team
---

### Post by pezbaloo on 2011-01-07
Hola: He instalat xubuntu 10.04 i tot bè, però quan endollo un usb no m'el monta. Ho reconeix, perque surt a lsusb, pero no el monta. També he tingut algun problema amb els permisos d'usuari al montar un dvd: el monta amb permisos de root.
He estat revisant la documentació i fòrums de xubuntu. Només trobo ajuda per la configuració a travès de thunar. Això crec que està tot correcte.
Algu sap algo?

---

### Post by wgarcia on 2011-01-07
Mira si tens instal·lada una aplicació que es diu "thunar-volman":

sudo apt-get install thunar-volman

Segons la informació: Extensió de thunar per a muntar volums.

---

### Post by pezbaloo on 2011-01-07
Si, tinc instalat thunar-volman i a traves del menu gui puc configurar com es monten els dispositius. Ho tinc tot seleccionat per l'auto montatge dels usb i altres dispositius (mp4players, etc...) pero continua sense funcionar. El més extrany es que si reinicio el sistema amb l'usb conectat si que el monta i treu una icona a l'escriptori (amb permisos de root) pero, si el conecto un cop accedit al meu usuari, no monta. ???

---

### Post by pezbaloo on 2011-01-08
He trobat la solució aquí.
[http://www.ubuntu-es.org/node/144391](http://www.ubuntu-es.org/node/144391)

Gràcies igualment!

---

