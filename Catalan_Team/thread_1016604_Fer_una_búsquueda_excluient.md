---
title: "Fer una búsquueda excluient"
date: 2008-12-20
forum: Catalan Team
---

### Post by Mutech on 2008-12-20
Hola bones,

M'agradaria poder fer una búsqueda de fitxers però excluïnt tots aquells que siguin .mp3.

Directori mp3
| Grup 1
---- Disc 1
---- Disc 2
---- Disc 3
| Grup 2
---- Disc 1
---- Disc 2
---- Disc 3
| Grup 3
---- Disc 1
---- Disc 2
---- Disc 3

Aquesta és l'estructura dels directoris. Dins hi han fitxers de video, imatges, .txt, etc. He buscat al manuals dels comandos "find" i "ls" però no n'he tret l'aigua clara. També pel google i res que em pugui ajudar.

Salutacions i gràcies ):P

---

### Post by CarlesOriol on 2008-12-20
ls -R | grep -v -i mp3

---

### Post by tanreb20 on 2008-12-22
uhm!

e spot fer que et tregui la busqueda en format maco?

Per exemple HTML?

---

### Post by Mutech on 2008-12-23
Gràcies per la resposta :)

El meu dubte és el següent:

M'agradaria eliminar tots els fitxers diferents a *.mp3. Amb el comando "rm" podria fer el mateix fet amb el "ls"?

Moltes gràcies i salutacions!  ):P

---

### Post by CarlesOriol on 2008-12-23
No
L'exemple anterior primer es fa el ls complet i despres es redirigia la sortida al grep per filtrar-la.

Per fer-ho crec que hauras de jugar amb la comanda find.

Per cert Mutech llegeix [http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965) abans de continuar i passa a presentar-te al fil de benvinguda a : [http://ubuntuforums.org/showthread.php?t=562776](http://ubuntuforums.org/showthread.php?t=562776)

---

