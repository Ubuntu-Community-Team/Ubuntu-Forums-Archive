---
title: "Carpeta d'inici a l'escriptori"
date: 2007-10-26
forum: Catalan Team
---

### Post by jodufi on 2007-10-26
Doncs això,
Algú em podria dir com posar la carpeta d'inici a l'escriptori amb el Gusty?
Al actualitzar la vaig perdre (vaig fer instal·lació des de zero), i ara no recordo com es posava.

Gràcies

---

### Post by papapep on 2007-10-26
En un terminal:

```

ln -s /home/el_teu_usuari/ /home/el_teu_usuari/Desktop/Inici
```

---

### Post by CarlesOriol on 2007-10-26
Papapep: Marrano!

gconf-editor > nautilus > desktop > home_icon_visible

Per cert per crear l'enllaç com diu en papapep podeu arrossegar directament el menu a l'escriptori. I així us estalvieu l'artrosi als ossos de les mans produïda per tant de picar tecles.

---

### Post by papapep on 2007-10-26
Carles: Innovador, hippie, yuppie, happie....:-D

Sóc de la vella escola, què vols...

---

### Post by jodufi on 2007-10-26
Gràcies,

Em sonava que hi havia una opció sense utilitzar el gconf.

I una altra, sabeu com s'activa la vista d'arbre? No ho trobo ni amb el gconf!

---

### Post by papapep on 2007-10-26
Hem de fer una miqueta els deures abans de preguntar, eh!! Que això és ben fàcil :-)

Dins el Nautilus: Visualitza > Subfinestra lateral. (també es pot fer prement F9).

(Apart, tal i com diu el Carles, som democràtics: un tema,  un fil. El proper cop, si us plau, obre un altre fil)

---

### Post by jodufi on 2007-10-26
Tens tota la raó amb el fil.

La barra lateral la tenia oberta, el que no recordava era que havies de canviar "Llocs" per "Arbre".

Salut

---

