---
title: "Actualitzar Ubuntu 8.04.2 a 8.10"
date: 2009-02-24
forum: Catalan Team
---

### Post by SiSTeR on 2009-02-24
Bona tarda,

M'agradaria saber si val la pena actualitzar de la versió 8.04.2 a la 8.10.

He llegit per altres fils que anant a Sistema --> Administració --> Orígens del software i després fer no sé quines passes més s'actualitza.

No sé quines són aquestes següents passes perquè ja m'he quedat aturat aquí ja que aquest "Orígens del software" no hi és. He anat a l'administració del menú principal perquè no fos cas que no tingués l'accés directe marcat i no apareix ni com ha marcat ni com a desmarcat.

És possible que això sigui perquè els tutorials que he vist són per actualitzar des del 8.04.1 al 8.10?

Gràcies per avançat.

---

### Post by socderafel on 2009-02-24
jo no he notat molta diferència, però per allò d'estar a l'ultima versió ho vaig fer.
Per a actualitzar: sistema, aministracio, origes del software, i ves a la pestanya actualitzacions. ahi, baix , en actualització de la distribució, selecciona edidiones normales, i baix de les pestanyes deuria apareixer un missatge dient que hi ha una nova versió i un botò que diu actualitzar o instal.lar o algo aixina. 
apreta este botó i començarà a baixar paquets de la nova distribució. 
Sort!

---

### Post by papapep on 2009-02-24
> M'agradaria saber si val la pena actualitzar de la versió 8.04.2 a la 8.10.


Això és un tema completament subjectiu. Pot haver-hi gent que no li calgui cap més actualització fins el dia del judici final, i hi pot haver gent que li calgui fer-ho immediatament per alguna aplicació/funcionalitat concreta. 

O sigui, això només ho pots dir tu :-)

---

### Post by SiSTeR on 2009-02-24
El que passa és que l'opció aquesta d'Orígens de Software no hi és.

---

### Post by torracastanyes on 2009-02-24
Si téns el sistema en català, es diu "Fonts de Programari"

---

### Post by SiSTeR on 2009-02-24
Gràcies

---

### Post by SiSTeR on 2009-02-24
Ja està.

Gràcies!

Com ho faig per donar per resolt el fil?

---

### Post by tanreb20 on 2009-02-24
No es pot ara per ara....

---

### Post by Curial on 2009-05-21
Primer de tot gràcies perquè aquest fil ha evitat que jo encetés un de calcat: Cal mirar sempre abans.....!!

Referent a aquest tema volia fer un poc més llum dient que si estem en una versió LTS crec que no ens mostra el botó d'actualització a la versió següent dins del gestor d'actualitzacions: Un Botó allargat a la part superior.

Per poder visualitzar aquest botó, si no hi és, cal com bé dèieu, anar a Sistema>Adminstració>Fonts de programari i...,llavors seleccionar la pestanya d'actualitzacions i a la part inferior de la finestra triar la opció "Versions Normals" a Mostrar versions Noves.

Salut.

---

### Post by SiscoGarcia on 2009-05-21
> **Curial said:**
> Referent a aquest tema volia fer un poc més llum dient que si estem en una versió LTS crec que no ens mostra el botó d'actualització a la versió següent dins del gestor d'actualitzacions: Un Botó allargat a la part superior.

Per poder visualitzar aquest botó, si no hi és, cal com bé dèieu, anar a Sistema>Adminstració>Fonts de programari i...,llavors seleccionar la pestanya d'actualitzacions i a la part inferior de la finestra triar la opció "Versions Normals" a Mostrar versions Noves.

Això no ho sabria dir del cert, però el que tinc clar és que sempre pots fer

```
Alt+F2
```

i a la caixa de diàleg escriure-hi:

```
update-manager -d
```

llavors llança el gestor d'actualitzacions que deies i et diu que hi ha una versió nova, hi punxes i a esperar ;)

---

