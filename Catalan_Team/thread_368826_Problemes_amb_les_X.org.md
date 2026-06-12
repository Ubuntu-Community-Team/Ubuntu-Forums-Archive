---
title: "Problemes amb les X.org"
date: 2007-02-23
forum: Catalan Team
---

### Post by cortsenc on 2007-02-23
A veure,
porto uns dies que estic de baixa, i estic jugant amb les X.org per veure si puc instal·lar el Beryl i l'acceleració 3D, però tinc el problema de tenir una targeta gràfica ATI. Instal·lant i desinstal·lant drivers me carregat un parell de cops les X i he hagut de reinstal·lar l'Ubuntu.

Ara però, instal·lant la 6.06 no tenia cap problema, però al fer l'actualització a 6.10 m'han petat les x i he hagut de reinstal·lar el paquet xserver-xorg. Ara es carreguen però te una refigeració de pantalla molt lenta (no se si me inventat l'expressió o es diu així) vaja, que quan baixò cap a baix, la pantalla es mou a batzegades i molt lentament. Suposo que això be pels drivers però estic fent servir el mateix driver que abans :confused: 

En fi, les especificacions són les següents:
Targeta gràfica: ATI Technologies RV350 AP [Radeon 9600]
Driver: "Vesa"

Que em recomaneu?

---

### Post by chalimac on 2007-02-23
Et recomano l'script envy que detecta la targeta i es baixa els drivers:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

i després segeix els tutorials per instal·lar beryl del wiki oficial de beryl:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

---

### Post by cortsenc on 2007-02-24
Ei, gràcies chalimac!!
Aquest script m'ha anat de meravella!!

A veure que passa amb el Beryl!!

---

### Post by patrickfromspain on 2007-02-26
Amb aquesta tarjeta pots fer servir el driver radeon. Igual es una mica més lent, pro tindrás l'avantatge de que no t'hauras d'instalar l'XGL, sino que amb les X de serie ja podras fer correr Beryl.

---

