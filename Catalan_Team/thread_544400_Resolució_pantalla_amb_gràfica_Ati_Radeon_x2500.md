---
title: "Resolució pantalla amb gràfica Ati Radeon x2500"
date: 2007-09-06
forum: Catalan Team
---

### Post by acrocephalus on 2007-09-06
Hola,
Tinc un problema similar. Tinc un portàtil nou de trinca, Acer Travelmate 5720, amb la tarja gràfica Ati Radeon x2500. Tot i que sé que puc tenir una resolució de 1280x800, l màxima que em dóna és 1024x768. He provat vàries coses:
- buscar el driver, no l'he trobat ni a la web d'Ati
- a través de Envy, i no em detecta la tarja
- modificar xorg.conf afegint la resolució desitjada i reiniciar les X, però res
Algú té una idea?
Moltes gràcies,

Dani

---

### Post by papapep on 2007-09-06
Dani: t'he mogut el post de fil i n'he creat un de nou per no barrejar temes, encara que tinguin certes connexions.

---

### Post by papapep on 2007-09-06
Aquest sembla que hagi de ser el controlador d'ATI, no?:
[http://www.nvidia.es/object/linux_display_ia32_100.14.11_es.html](http://www.nvidia.es/object/linux_display_ia32_100.14.11_es.html)

---

### Post by patrickfromspain on 2007-09-06
papapep... ejem... estas enllaçant a la web d'nvidia ;)

jo juraria que ati encara no ha tret un driver per linux compatible amb aquesta grafica.. aixi que estas fent servir el driver "vesa", que te una resolucio maxima de 1024x768,

salut!

---

### Post by papapep on 2007-09-06
Si noi, últimament les presses em porten fregit.

Aquí:[http://www.notebookcheck.net/ATI-Mobility-Radeon-X2500.3774.0.html](http://www.notebookcheck.net/ATI-Mobility-Radeon-X2500.3774.0.html)

diuen que la Mobility Radeon x2500 són unes x1600 - x1700 canviades de nom.

Podries provar com et va amb el controlador de la x1600 que trobaràs aquí:[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by xoldy on 2008-02-15
Suposo que la solució que doneu a aquest post, serveix per la x2600. Efectivament m'utilitza el controlador vesa amb resolució màxima 1024x768. Es veu molt bé però sap greu tenir les vores en negre...
Si estic d'humor provaré amb els controlador de l'Ati x1600.

---

### Post by CarlesOriol on 2008-02-15
Si el controlador de l'envy no et va t'hi pots posar fulles.

---

