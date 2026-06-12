---
title: "convmv k3b i lletres de Windows"
date: 2007-04-28
forum: Catalan Team
---

### Post by bikerbaixcamp on 2007-04-28
Bones,

doncs al començar a gravar un dvd al K3b m'ha sorgit aquest inconvenient, i m'ha dit que ho rectifiques amb "convmv". Pel que he entès resulta que els caràcters estranys no els reconeix i per tant no me'ls inclou per gravar-los.

És a dir, com molts arxius els vaig fer quan estava amb Windows i alguns portaven "ç" i accents doncs a les carpetes em surten amb uns interrogants i caràcters estranys.

M'agradaria solucionar aquest últim problema, i el primer també.

Gràcies!

---

### Post by patrickfromspain on 2007-04-28
jo el que faria es renombrar-ho.. es la solucion que faig servir jo XD

---

### Post by bikerbaixcamp on 2007-04-28
> **patrickfromspain said:**
> jo el que faria es renombrar-ho.. es la solucion que faig servir jo XD

També, també, jejeje

---

### Post by patrickfromspain on 2007-04-28
bueno va, he mirat una mica de que va el convmv.

[http://www.gpltarragona.org/archives/419](http://www.gpltarragona.org/archives/419)

salut!

---

### Post by CarlesOriol on 2007-04-29
Temporalment pots canviar la linia del fstab per alguna cosa similar a : 

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,iocharset=utf8 0 0

(iso8859 <-> utf8 )

o més facilment desmuntar el cd tornar-lo a muntar amb el mount equivalent amb el iocharset.

---

