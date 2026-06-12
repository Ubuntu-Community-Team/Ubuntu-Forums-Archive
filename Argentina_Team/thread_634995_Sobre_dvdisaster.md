---
title: "Sobre dvdisaster"
date: 2007-12-08
forum: Argentina Team
---

### Post by UBUjuan on 2007-12-08
Tengo un par de dvd's que no me funcionan, cuando utilizo dvdisaster y hago un 'scan' me informa que todos los sectores se peeden leer, sin embargo no logro recuperarlos ¿es que hay que tener el archivo de correccion de errores .ecc obligatoriamente?, porque no no lo hice.

Aclaro que no lo puedo montar, en el syslog me aparece:
attempt to access beyond end of device
hdd: rw=0, want=68, limit=4
attempt to access beyond end of device
hdd: rw=0, want=1252, limit=4
attempt to access beyond end of device
hdd: rw=0, want=1028, limit=4
UDF-fs: No partition found (1)
attempt to access beyond end of device
hdd: rw=0, want=68, limit=4
isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16

---

### Post by juanman on 2007-12-08
Si todos los sectores se pueden leer, con la opcion read te graba una imagen iso en el lugar especificado en current image file (caja de texto q está arriba al medio). Después esa imagen la podés grabar en otro cd o montarla...
La opción scan solo te informa de los errores. Para la opción Fix (q arregla errores irrecuperables) es necesario el .ecc, pero no sería tu caso...

---

