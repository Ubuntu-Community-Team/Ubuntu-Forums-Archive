---
title: "Battery-Status no mostra temps restant"
date: 2011-02-20
forum: Catalan Team
---

### Post by Joan A. on 2011-02-20
Hola a tothom!

Degut al *bug* d'Ubuntu 10.10 amb *gnome-power-manager*, el qual no mostra el temps restant de la bateria del meu portàtil, vaig instal·lar *battery-status* seguint les instruccions d'aquesta pàgina: [http://planetared.com/2010/12/estado-de-tu-bateria-en-ubuntu-10-10/](http://planetared.com/2010/12/estado-de-tu-bateria-en-ubuntu-10-10/)

El problema ara es que segueix sense mostrar-me el temps restant. Algú sap com ho puc solventar?

Moltes gràcies!

---

### Post by kimet on 2011-02-22
No s'acaba d'entendre en el teu post si el battery-status aquest que dius no ha arreglat absolutament res o si ara pots veure el tant per cent de bateria restant...Si es així es possible que sigui tot el que et permet la placa. 
Si no investiga sobre ACPI i APM i els mòduls que corresponguin per al teu ordinador. Al carregar-los hauria d'apareixer informació sobre l'estat de la bateria a /proc/acpi/thermal o alguna cosa semblant.


Salut.

---

