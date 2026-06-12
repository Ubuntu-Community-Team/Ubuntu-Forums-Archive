---
title: "Arxius tar.gz (normativa general ¿?)"
date: 2011-03-09
forum: Catalan Team
---

### Post by prostata on 2011-03-09
Tinc un plugin de gimp que es diu wavelet-denoise, amb extensió tar.gz

Segons que diu l'arxiu INSTALL que acompanya el conjunt per fer la instal-lació cal fer:

------------------------
For a system wide installation simply state

	make
	make install

Fins aquí simple i clar, el problema rau en que al fer ja la primera sentencia la terminal em diu:

In file included from plugin.c:16:
plugin.h:21: fatal error: libgimp/gimp.h: No existeix l'arxiu o el directori
compilation terminated.

En altres llocs o vegades prèviament hi ha un ./configure,però seguint les instruccions que diu l'install, en aquest cas sembla que no cal, de fet ho he intentat per si de cas però ...no.

Sempre tinc algun problema amb els empaquetats, ja que de vegades van i de vegades,com és el cas, no...¿què puc fer...??

Salut

Edit; ja em contesto jo solet, el que haig de fer es fixar-me una mica més en les respostes de la terminal,doncs és molt clar, em diu que falta libgimp, i sent així, doncs Synaptic i llestos...Perdoneu les molèsties....i l'atreviment

---

