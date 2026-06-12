---
title: "[SOLVED] Obrir directament arxius PDF amb firefox"
date: 2008-12-17
forum: Catalan Team
---

### Post by Curial on 2008-12-17
Fa poc he actualitzat a la 8.04.El firefox és doncs 3.0.4.

El problema que tinc és quan navego amb el Firefox i intento abaixar-me un arxiu pdf, trio l'opció d'obrir en comptes de desar l'arxiu i no ho fa com en l'anterior versió de firefox, haig d'anar a les baixades i obrir-lo des d'allà.

Dins de preferències-aplicacions no he vista la possibilitat de canviar-ho.

És normal haver-ho de fer així en aquesta versió del Firefox?

Salut.

---

### Post by lo gambusí on 2008-12-18
Crec que s'obria directament des del navegador gràcies a una extensió... hauries de tornar a intal·lar-la.

---

### Post by oriolsbd on 2008-12-18
Mira com tens la configuració dels fitxers PDF a "Edita>Preferències", i ves a la pestanya "Aplicacions".

---

### Post by PatrickVogeli on 2008-12-18
mira que tinguis instal·lat el mozilla-acroread, es als repositoris de medibuntu

---

### Post by Tomàs M. on 2008-12-18
A mi també em va passar. Ara no recordo exactament com ho vaig solucionar, però va ser amb mozplugger i evince. A edita - preferències - aplicacions hi tinc "utilitza mozplugger" per als documents pdf; amb el mozilla-acroread m'havia deixat de funcionar.

---

### Post by Curial on 2008-12-23
Ja ho he solucionat.

Sí que tenia instal.lat el mozilla-acroread i després també he instal·lat el mozplugger, però no s'obrien els arxius fins que no he tria l'evince.

Per activar l'evince ho he fet des d'Edita-Preferències-Aplicacions i he seleccionat evince tant per a application/pdf com per application/x-download.

L'executable l'he trobat a directori /usr/bin.

Gràcies per l'ajut.

Bon Nadal.

---

