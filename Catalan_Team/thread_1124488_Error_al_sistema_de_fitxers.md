---
title: "Error al sistema de fitxers"
date: 2009-04-13
forum: Catalan Team
---

### Post by sianeu on 2009-04-13
Al arrancar l'ordinador em dona un error al sistema de fitxers i em demana que l'arregli manualment. Al log corresponent diu:

[HTML]Log of fsck -C3 -R -A -a 
Sun Apr 12 20:24:58 2009

fsck 1.41.3 (12-Oct-2008)
/dev/sda4 contains a file system with errors, check forced.
Error reading block 5429192 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 1058279.  

/dev/sda4: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Sun Apr 12 20:28:14 2009
----------------[/HTML]

Si faig control+D carrega el sistema correctament i el puc fer servir com si res.

Que hauria de fer?

Salut

---

### Post by sianeu on 2009-04-15
Problema solucionat.

Des d'un liveCD (en el meu cas per que sda4 es /home, en altres casos potser no cal) fem > sudo fsck /dev/sda4 y contestem "y"(si) a cada pregunta.

Ara el sistema arranca correctament y no he notat cap error en els fitxers multimedia que tenia guardats en /home (sda4).

Salut

---

