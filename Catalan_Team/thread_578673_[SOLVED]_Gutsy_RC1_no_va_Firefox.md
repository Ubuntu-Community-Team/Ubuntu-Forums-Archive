---
title: "[SOLVED] Gutsy RC1 no va Firefox"
date: 2007-10-17
forum: Catalan Team
---

### Post by manelolesa on 2007-10-17
He inst.lat Gutsy RC1 i al fer una actualitzacio amb els repositoris main i universe marcats, el Firefox ha deixat de funcionar.
Clico la icona, surt el rellotge i uns segons després se'n va.
El Firefox deixa logs ?

Salut

---

### Post by albert-I on 2007-10-17
i desde terminal?

---

### Post by manelolesa on 2007-10-17
Ara he vist el que passa.
Si l'executo com usuari no fa res, si ho faig amb sudo si que va.
Alguna cosa ha canviat pemissos.
slt

---

### Post by manelolesa on 2007-10-17
Solucionat.
A la carpeta .Mozilla de la meva home, estava com a propietari el root.
He esborrat la carpeta i al torna executar s'ha creat amb el meu usuari.

Gracies

---

