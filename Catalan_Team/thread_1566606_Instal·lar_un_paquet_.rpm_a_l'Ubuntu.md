---
title: "Instal·lar un paquet .rpm a l'Ubuntu"
date: 2010-09-02
forum: Catalan Team
---

### Post by Black_02 on 2010-09-02
Hola a tothom,

Tinc un problema amb un paquet .rpm. He buscat informació sobre com instal·lar-lo, però no me'n surto. He instal·lat el programa "alien" per convertir paquets rpm a deb però no hem dona resultat:

[IMG]http://s2.subirimagenes.com/imagen/5103068rpm.png[/IMG]

Segons el que posa aquí al terminal sembla que s'hagi creat, però no és així.

El programa en concret és [[COLOR="Red"]el corrector.[/COLOR]]("http://www.elcorrector.cat/linux.html")

Gràcies.

---

### Post by kimet on 2010-09-02
I que passa quant intentes instal.lar el .deb?

---

### Post by Black_02 on 2010-09-02
> **kimet said:**
> I que passa quant intentes instal.lar el .deb?

El problema que tinc és que no puc transformar el .rpm en un .deb, encara que al terminal posi: ***elcorrector_1.0.0-2_i386.deb generated*** no el genera, o no sé on el guarda.

---

### Post by kimet on 2010-09-02
Fes el que et diu, usa la extensió --scripts
 ```
alien --scripts ElCorrectorLinux.rpm
``` i si no, revisa que tinguis els paquets necesaris dpkg, dpkg-dev etc. (que em penso que els has de tenir). 
L'archiu amb extensió .deb ha d'apareixer en el mateix directori hon estas.

Salut

---

### Post by tanreb20 on 2010-09-02
diria que has de psoar el -i

alien -i *.rpm [*.deb]

---

### Post by Black_02 on 2010-09-04
No em funciona de cap de les maneres :???:, crec que serà perquè és un programa per a 32 bits i jo tinc l'Ubuntu de 64 bits.

En fi, que hi farem...

---

### Post by tanreb20 on 2010-09-04
Home.. es pot forçar la instalació eh!

dpkg --force-architecture paquet

---

