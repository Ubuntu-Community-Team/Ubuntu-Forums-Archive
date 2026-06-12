---
title: "Instal.lació: particionar manualment: no s'ha definit el sistema de fitxers arrel"
date: 2009-12-06
forum: Catalan Team
---

### Post by Flocdemer on 2009-12-06
Hola ubuntaires,

quan estic instal.lant l'ubuntu 9.10 durant el particionat manual em diu que no puc continuar perquè [COLOR=DimGray]*no s'ha definit el sistema de fitxers arrel*[/COLOR] o semblant. Tinc un disc sata2 de 500GB amb una partició de 150GB windows i a continuació hi vull afegir un ubuntu de 150GB i una partició d'intercanvi de 4GB.

Gràcies per avançat.

---

### Post by quixote on 2009-12-07
I don't speak Catalan, so I'm pretty much guessing.  (If it serves no other purpose, at least this'll kick your question back to active status :D.)  

It sounds to me like it may be telling you that you haven't specified a mount point.  During manual partitioning, a window comes up where you set the size of the partition.  I believe it's on that same little window, you'll see a line saying "Mount point" with a blank square next to it.  It's not very obvious, but if you click on that, a list drops down.  One of the choices is "/" i.e. "root."  At least one partition must be root, because that's where the system files are installed.  

It's also a good idea to have a separate /home partition.  If you make a second partition for ubuntu, then for "Mount point" choose "/home".

---

### Post by quitus on 2009-12-08
Doncs això, en el particionat manual has de identificar les particions. La partició on vols instal·lar l'ubuntu s'identifica com a / que vol dir l'arrel del sistema, i si vols posar la carpeta home (on es guarden totes les configuracions del teu usuari i tots els arxius) en una partició diferent la identifiques com a /home.

salut

---

