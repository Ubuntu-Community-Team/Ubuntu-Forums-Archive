---
title: "rm -recursive"
date: 2007-05-18
forum: Catalan Team
---

### Post by ernestux on 2007-05-18
Hola,

He fet la bestiesa d'executar desde la consola:  ~$ sudo rm --recursive /home/merlot/.doc
per esborrar aquest directori ocult  que tenia a la home.

Ara intento obrir  la  Carpeta d'inici i  "s'està iniciant" però res. No puc veure cap directori de la home , ni ocult, ni visibles.
No els he esborrat perquè els veig des del F-spot, amaroK.... i del monitor del sistema ,però no sé com solucionar-ho.

Una pista: A través del vlc puc veure:  /home/merlot/Desktop/nautilus-home.desktop  

Tinc  gnome

AUXIL·LI !!

Ernest

---

### Post by hardyn on 2007-05-18
sudo rm /home/merlot/*.doc

or sudo rm -R /home/merlot/*.doc

---

### Post by CarlesOriol on 2007-05-18
Per què has fet sudo?

---

