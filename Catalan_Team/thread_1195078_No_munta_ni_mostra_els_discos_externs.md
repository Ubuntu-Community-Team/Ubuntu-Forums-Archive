---
title: "No munta ni mostra els discos externs"
date: 2009-06-23
forum: Catalan Team
---

### Post by Quepotser on 2009-06-23
Bona tarda a tothom.

Des de fa un parell de dies quan conecto qualsevol andromina del tipus llapis, disk extern o memòria USB, no ho munta i tampoc m'ho mostra a l'escriptori amb la seva icona corresponent tal com feia fins ara. Sí que els detecta ja que al desplegable "Llocs" sí que hi apareixen; allà els puc muntar clicant a sobre però no tinc manera de desmuntar-los. He estat mirant per tots els recons de Google però no n'he tret l'aigua clara.

Agrairia molt qualsevol orientació sobre què pot haver passat. Gràcies per endavant.

Faig servir el Hardy Heron.

---

### Post by lluisanunez on 2009-06-23
Prova obrint l'editor de configuracions (gconf-editor), Apps > Nautilus > Preferences 
i mira si està marcat "media automount"

---

### Post by Quepotser on 2009-06-23
Gràcies per la resposta.

Ha funcionat tan sols a mitges; munta els dispositius però segueixen sense apareixer les icones a l'escriptori i més important: haig de desconnectar-los sense haver-los pogut desmuntar. I això es una cosa que em preocupa una mica.

De totes maneres alguna cosa hem avançat.

---

### Post by lluisanunez on 2009-06-23
Al mateix gconf, a Apps > Nautilus > Desktop pots activar les icones

---

### Post by Quepotser on 2009-06-23
Oli en un llum. Definitivament era això el que s'havia desterotat. 

Moltes gràcies per les teves indicacions.

---

