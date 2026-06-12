---
title: "Problemes amb la resolució."
date: 2007-06-06
forum: Catalan Team
---

### Post by xtort on 2007-06-06
He instal·lat el Ubuntu 7.04 al portàtil i tinc problemes amb la resolució de la pantalla.
M'explico, Al engegar l'ordinador quan el Ubuntu demana el nom d'usuari i la contrasenya abans d'escriure res tinc que fer un ctrl+alt+backspace i llavors arrenca amb la resolució correcte, però si el que faig es introduir el usuari + contrasenya el que fa es engegar a 1024x768, porto molts dies buscant la solució però no me'n surto.
Estic convençut que te que ser una tonteria, però no ho ser trobar.
Salutacions

---

### Post by CarlesOriol on 2007-06-07
Has provat

Sistema > Preferències > Resolució de pantalla

---

### Post by xtort on 2007-06-07
Si que he provat Sistema > Preferències > Resolució de pantalla, si engego sense ctrl+alt+backspace la resolució màxima que em surt es 1024x768.
Estic convençut que és una tonteria, però no soc capaç de trobar la solució.

---

### Post by Frealof on 2007-11-16
Bon dia

He estat buscant a la xarxa i enlloc trobo com solucionar un petit problema amb la resolució de la pantall.


Sóc nou amb això dels posts i com que aquest post tracta d'això, espero que sigui el lloc correcte per demanar ajuda. Però passem al què toca :) 

La qüestió es que quan s'engega el Gnome, ho fa a la resolució de 640X480... després vaig a "Sistema>Administració>Pantalles i gràfics" i no hi ha problema per canviar la resolució a 1280X1024... Em demana per conservar la configuració actual, accepto, però quan torno a obrir el Pc em trobo que torna a estar a 648x480...abans d'instal·lar el Gibbon (amb el Feisty Fawn) això no m'havia passat mai... algú em podria donar un cop de mà?

Gràcies per endavant

---

### Post by papapep on 2007-11-16
Una de les solucions que crec que et podria funcionar és editar el fitxer ***/etc/X11/xorg.conf*** i treu les resolucions que no vulguis de la configuració.

---

### Post by Frealof on 2007-11-16
Gràcies per la informació.

Com a prova he eliminat totes les línies on hi apareixia el 640X480 del  fitxer xorg.conf fent servir gedit. He desat. He reiniciat la màquina però... a la que s'ha engegat l'escriptori del Gnome ho ha fet en 640X480... Alguna altra idea?

Gràcies de nou.

---

### Post by jodufi on 2007-11-16
Jo sempre he tingut problemes amb la resolució en els dos ordinadors on tinc Ubuntu, en un havia de modificar el xorg.conf i en l'altre havia d'instal·lar un paquet extra.

Per sort, amb la versió 7.10 han millora molt aquest tema i ara em funciona bé en els dos ordinadors sense tocar res.

Per tant, et recomana canviar a la versió 7.10

Salut

---

