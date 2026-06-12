---
title: "Compartir carpetes virtualbox"
date: 2009-05-01
forum: Catalan Team
---

### Post by lFossil on 2009-05-01
Hola companys, estic intentant compartir dades al virtualbox (ubuntu> WXP) i he estat buscant en alguns llocs però veig diferents maneres de fer-ho i m'estic fotent panera! N'he provat un però no m'he aclarit.
Algú en sap com puc fer-ho?
Gràcies

---

### Post by oriolsbd on 2009-05-02
Hola.

Fa unes setmanes vaig escriure una sèrie de 5 anotacions sobre el Virtualbox que potser t'ajuden. L'anotació en concret on escrivia com compartir fitxers amb màquines virtuals (tant Windows com GNU/Linux) és [aquesta]("http://alliberats.org/maquines-virtuals-4-guest-additions/").

Salut!

---

### Post by kukat on 2009-05-02
Quin Virtualbox utilitzes??? El lliure que ve als repositoris, o el que pots descarregar de la seua web? (no lliure) [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Si es el "no-lliure", es tan senzill com anar als Paràmetres de la màquina virtual, i a "carpetes compartides" i afegir alguna carpeta.

edito: Si no estic equivocat, el que ha dit oriolsbd, es la forma de fer-ho en la versió lliure! :) 

Salut!

---

### Post by oriolsbd on 2009-05-03
Hola, Kukat. La manera que jo indico funciona a la versió "no-lliure".  :-)

Es pot fer de les dues maneres. Amb la que jo indico, té dues avantatges: Pots compartir una carpeta en una màquina virtual engegada, i pots fer una compartició "temporal" (apart de la compartició permanent que també es pot fer com tu indiques).

L'avantatge que jo li trobo a la compartició "temporal" és que, quan reinicies la màquina, la carpeta ja no està compartida. Pot semblar un desavantatge, però com que a les màquines virtuals li poso els mínims sistemes de seguretat, així no comprometo tant les meves dades.

Per cert, si es fa com tu comentes (que és més fàcil de trobar) després igualment cal fer el "net use x: \\vboxsvr\nom_recurs_compartit" des de la màquina virtual.

---

### Post by kukat on 2009-05-04
ah! excuse-moi! jejejeje
es que se que quan tenia la versió lliure, hi havia algunes restriccions amb els USB i coses així, i pensava que era això!
Salut!

---

### Post by lFossil on 2009-05-04
Tinc el virtualbox OSE però no sé si és la versió lliure o no.

---

### Post by RainCT on 2009-05-04
Sí (OSE = Open Source Edition).

---

### Post by lFossil on 2009-05-07
Però llavors, si estracta de la versió lliure com ho faig?
Serveix el mateix mètode? Suposo que no

---

### Post by oriolsbd on 2009-05-07
Sí que és el mateix. Les diferències entre la versió lliure i no-lliure són poques. La més important, que amb la lliure (OSE) no pots utilitzar dispositius USB, el servidor RDP i Serial ATA. Pots veure les diferències entre les dues versions [aquí]("http://www.virtualbox.org/wiki/Editions"). Per la resta, les dues versions són exactament iguals.

---

