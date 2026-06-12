---
title: "Cofigurar escaner Samsung SCX-4824-FN"
date: 2011-02-08
forum: Catalan Team
---

### Post by ninfak3 on 2011-02-08
Bon dia,

Sistema operatiu Ubuntu 10.10 64bits

Els voldria demanar ajuda per configurar l'escaner Samung SCX-4824-FN.
He instal·lat els drivers generics de Samsung i la impresora em funciona per el port usb://Samsung SCX-4x24%20Series, com per ethernet per el port ipp://192.168.xxx.xxx, però l'escaner no el detecta.

Llavors he posat a la linia de comandes:
$scanimage -L 
no em detecta cap escaner i em llença aquest error (dos cops):
netdiscovery: relocation error: /lib32/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time references

Els agrairia alguna ajuda, de fet no se si solucionant aquest error de llibreries podem fer que detecti l'escaner.

Salutacions,

Marta

---

### Post by wgarcia on 2011-02-08
Al següent post:

[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

es menciona explícitament el problema que t'estàs trobant i diu que de moment el funcionament d'aquests scanner a sistemes Ubuntu (i Debian) de 64 bits està limitat. També comenta que es pot arreglar però ficant-se amb fitxers de sistema. 

Mirat-el a veure si si et pot ajudar.

---

