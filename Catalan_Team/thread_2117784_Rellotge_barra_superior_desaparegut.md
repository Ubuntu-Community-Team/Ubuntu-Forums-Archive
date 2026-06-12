---
title: "Rellotge barra superior desaparegut"
date: 2013-02-19
forum: Catalan Team
---

### Post by trinkus on 2013-02-19
Hola amics,

He actualitzat a 12.04 i ara resulta que ha desaparegut el rellotge de la barra superior. No trobo la manera de restablir-lo.
Sospito que ja venia "fotut" de l'anterior versió perquè em trobava que no canviava l'hora (semblava que mantenia la de quan havies obert la sessió, però no hi vaig parar atenció).
Ara sense ell té nassos com el trobes a faltar!
Algú sap com restablir-lo?

Merci!

---

### Post by jesús sol on 2013-02-19
salut trinkus!
crec que la manera de restablir-lo, és obrir "Paràmetres del sistema" i al capdavall hi ha una icona d'un rellotge que diu "Data i hora". Entrant aquí, hi ha una pestanya que diu "rellotge". Cal triar i marcar el que vulguis.

---

### Post by trinkus on 2013-02-20
Justament no m'apareix aqeusta icona... pot ser que hi hagi algun paquet no instal·lat, esborrat o malmès? Però no sé pas quin paquet és...

---

### Post by wgarcia on 2013-02-20
Prova des d'una terminal:

```
sudo apt-get install --reinstall indicator-datetime
```

a veure si t'ho arregla.

---

### Post by trinkus on 2013-02-25
Ostres Gràcies!

Exactament el que biscava i necessitava! Merci!
No sé com es posa SOLVED però vaja... que SOLVED està!

---

### Post by wgarcia on 2013-02-26
Per posar "Solved" cliques sobre "Thread tools" a dalt i esculls "Solved".

---

