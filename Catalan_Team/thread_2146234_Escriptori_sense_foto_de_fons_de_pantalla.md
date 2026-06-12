---
title: "Escriptori sense foto de fons de pantalla"
date: 2013-05-17
forum: Catalan Team
---

### Post by MiquelAS on 2013-05-17
Fa unes dues setmanes que tinc el 13.04 instal·lat al meu ordinador i fins ara havia anat perfecte. Ara m'ha sorgit un "problema" amb l'escriptori que m'apareix gris i sense la foto de fons de pantalla.

Qualcú te idea del que passa?

Salutacions

MiquelAs

---

### Post by wgarcia on 2013-05-18
Per poder saber què passa es necessitaria una mica més d'informació. Per exemple: tota la resta funciona? Et falta alguna altra funcoinalitat o simplement el que passa és que no hi ha imatge de fons a l'escriptori?

---

### Post by tsanchez on 2013-05-21
Bon dia, 

El que també pot fer es mirar quina imatge te configurada com a fons de pantalla. fent en una shell:

gsettings get org.gnome.desktop.background picture-uri

T'ha de retornar el path i el nom de la imatge configurada. 

Si el que vols es establir una canvi la clau get, per set i la URI del fitxer, per exemple:

**gsettings set org.gnome.desktop.background picture-uri 'file:///usr/share/backgrounds/IMATGE.png'**

Slts.

tsanchez

---

### Post by MiquelAS on 2013-05-21
Hola!
 El que em fa l'escriptori era que només no apareix la foto que tenc triada de fons de la pantalla, però la resta del sistema va
 bé!

---

### Post by wgarcia on 2013-05-22
Fas servir l'escriptori d'Ubuntu per defecte o has instal·lat algun altre escriptori addicional?

---

### Post by MiquelAS on 2013-05-22
Hola!

Tenc instal·lades les opcions d'escriptori gnome i cianmon


Salutacions

---

### Post by wgarcia on 2013-05-22
Però fas servir algun d'aquests dos escriptoris o el d'Ubuntu per defecte (Unity)? 

He vist informes de què l'escriptori Gnome ha canviat el lloc on es desen les imatges de fons de pantalla i per això entra en conflicte amb Unity, així com també d'altres que diu que algunes versions no estàndard de Gnome (PPA) generen aquest problema.

---

### Post by MiquelAS on 2013-05-23
Normalment faig feina a dins Unity sense usar els gnome a no ser a vegades

---

### Post by wgarcia on 2013-05-24
Una solució que donen passa per installar "gnome-tweak-tool", per exemple des d'una terminal:

```
sudo apt-get install gnome-tweak-tool
```

Un cop instal·lat obres aquest programa (per exemple ALT-F2 i entres "gnome-tweak-tool") i a la finestra es desmarca la primera opció (en anglès "Have file manager handle the desktop")

No em queda clar si això estableix el fons de pantalla però trenca que es vegin les icones i carpetes a l'escriptori. Altres opcions són desinstal·lar el gnome ni el fas servir massa, o esperar que s'arregli aquest problema amb alguna actualització d'unity o de gnome.

---

### Post by MiquelAS on 2013-05-24
Gràcies miraré de desinstal·lar gnome i ja us dic

---

### Post by MiquelAS on 2013-05-25
He desinstal·lat gnome i problema arreglat!

Gràcies pel vostre ajut!

---

### Post by wgarcia on 2013-05-27
Si no et sap greu,  marca sisplau el fil com a "Solved", ja que això serveix per a futures consultes. Per veure com es fa mira aquest missatge: 

[http://ubuntuforums.org/showthread.php?t=2137063&p=12613376#post12613376](http://ubuntuforums.org/showthread.php?t=2137063&p=12613376#post12613376)

---

