---
title: "scanner no funciona"
date: 2010-01-22
forum: Catalan Team
---

### Post by josep-maria on 2010-01-22
He ficat l'ubuntu 9.10. El scanner-impressora és HP deskjet F2280, i ara ja no funciona.
Quan engego el xsane, surt una finestra i abaix, on diu la mida de l'arxiu, diu:
0*1020*8 (0.0B), 0,00 mm x 129 mm. És a dir, zero bytes. He mirat a tots els menús i no he trobat la
solució.

---

### Post by lpargemi on 2010-01-29
Però et reconeix l'escaner? Suposo que si arriba fins aquí serà que si que el reconeix.

Has provat d'activar la vista de previsualització? Si pots demana de fer una previsaulització i a veure si la fa.

Potser tens algún paràmetre fora de mare en les opcions de la lectura...

Lluís

---

### Post by kukat on 2010-01-30
Pots provar a executar-lo com a root??

**sudo xsane** 
Al terminal....
tot i que llança un missatge un tant ombrívol...
Algú pot confirmar que no passa res per executar com a root??? Jo ho he fet ara, però no se per que llança eixe missatge:confused:


[LIST=1]
[*]Pots intentar també executar-lo des del terminal, sense root, per veure si llança algun missatge.
[*]Reinstal.lar el programa al Synaptic, fent lo de "eliminar completament"
[*]Provar de instal.lar alguna alternativa a Xsane, per a descartar que sigui el programa: [http://www.somgnu.cat/2009/12/01/gnome-scan-i-enviem-xsane-a-la-seua-epoca/](http://www.somgnu.cat/2009/12/01/gnome-scan-i-enviem-xsane-a-la-seua-epoca/). Gnome-scan pinta molt bé!
[/LIST]

Salutacions! ;)

---

### Post by josep-maria on 2010-01-30
He fet la previsualització i ha funcionat bé. Gràcies.

---

