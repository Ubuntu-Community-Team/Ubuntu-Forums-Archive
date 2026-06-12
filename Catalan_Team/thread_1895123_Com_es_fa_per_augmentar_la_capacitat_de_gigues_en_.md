---
title: "Com es fa per augmentar la capacitat de gigues en el disc dur dedicats a Linux?"
date: 2011-12-14
forum: Catalan Team
---

### Post by Jayhawker on 2011-12-14
Hola.

Com es fa per augmentar la capacitat de gigues en el disc dur dedicats a Linux amb la modalitat instal·lada per funcionar amb WIndows? Parlo de la darrera versió, la 11/10. Vaig començar amb 12 G, els que vaig indicar en el moment de la instal·lació, des de Windows, però ara voldria augmentar a més gigues per poder fer més coses. 

Mercès.

---

### Post by wgarcia on 2011-12-14
Ho pots fer amb el programa "gparted", però primer convindria que defragmentares un parell de cops les teves particions de Windows (des de Windows) i que fessis còpia de seguretat de tot, perquè canviar el tamany de les particions a vegades fa perdre dades, no ha de passar però millor tomar precaucions. 

Amb el programa gparted primer hauries de reduir la partició que té Windows, i després incrementar la partició que té Linux. Això sols s'ha de fer entre particions contigües. 

En aquesta pàgina tens una descripció en anglès sobre com fer-ho:

[https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

---

