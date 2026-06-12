---
title: "PC es tanca de cop"
date: 2010-02-13
forum: Catalan Team
---

### Post by nickpage on 2010-02-13
Hola companys,

de fa unes setmanes tinc un problema amb el meu ordinador.
Tinc instal·lat la versió 9.10 de l'ubuntu i resulta que quan estic treballant l'ordinador es tanca de cop, sense que pugui esbrinar que el fa tancar, és una apaga tal com si de repent no tingués electricitat.

Em prodieu donar alguna pista de com esbrinar que passa?

Gràcies.

---

### Post by jdk9 on 2010-02-14
Que és, un sobretaula o un portàtil?

Prova d'actualitzar la bios, a mi em passava en el netbook i crec que era per excés de temperatura de l'ordinador. Vaig actualizar la bios i cap problema.

---

### Post by nickpage on 2010-02-14
És un sobretaula,
la temperatura la tinc monitoritzada i de fet sempre estava a menys de 20 graus.

Provaré d'actualitzar la BIOS però sembla que el problema no va per aquí.

Gràcies

---

### Post by jdk9 on 2010-02-14
Si no és pel tema de la temperatura, no cal que actualitzis, millor inclús si no ho fas.

---

### Post by nickpage on 2010-02-14
Be, aniré provant, ara he deshabilitat el compiz, a veure si te alguna cosa a veure....

---

### Post by nickpage on 2010-02-18
Actualitzo,

em passa el mateix sense compiz.
He descartat qualsevol aplicació, a no ser que sigui per algun tema del firefox, perque només navegant ja em peta.

Alguna cosa a mirar abans de reinstalar?

---

### Post by bonsaiw on 2010-02-18
Si tens la sensació que pot ser pel firefox... intenta navegar amb un altre navegador abans de formatejar a vere si s'apaga també.
.
 .
  .
   Podria ser causa de la electricitat estàtica? o pols?

---

### Post by wgarcia on 2010-02-19
És possible que es tracti d'un conflicte d'algun element amb l' ACPI (els mòduls de control d'energia). Sembla que per a la versió 2.6.33, la que va amb la Lucid Lynx, s'introdueixen moltes millores de la gestió d'energia. Un dels conflictes coneguts és amb els teclats i els "touchpad". Prova de fer des d'una terminal:

$ dmesg | grep -i i8042 

a veure què surt...

---

