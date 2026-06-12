---
title: "Problema con Grabadora de DVD"
date: 2007-07-06
forum: Argentina Team
---

### Post by Mauro22 on 2007-07-06
Hace un rato se me ocurrió probar la grabadora de DVD, (no lo habia hecho desde la instalacion de Ubuntu) y usando el K3b, no puedo grabar a mas de 4x.


Cualquier tipo de grabacion sale:

```
Medium or recorder not support xX
```
Donde x es la velocidad elegida.

```
Switching write speed down 4x
```



Será problema de K3b, ya que no probe con otro soft? 


PD: mi lectograbadora es una Pioneer 110D

---

### Post by guillermolisi on 2007-07-06
Mauro

Proba de correrlo como root (se que no es lo mas aconsejable pero para una prueba no creo que pase nada malo).

Para eso edita la opcion de K3b y marca "correr como otro usuario" (por lo menos asi es con KDE). Te pide la pass y quedas como si hubieras realizado un "sudo".

Te hago este comentario porque tuve problemas cuando empece a probar K3b y resulto que por cuestiones de permisos no funcionaba como deberia.

Probe corriendolo como superuser (root) y funciono perfecto.

---

### Post by Apipote on 2007-07-06
Luego de lo que te sugiere Guillermo, yo probaria otro soft y/o chequearia el medio que usas.
Yo tengo unos dvd regrabables que no soportan mas de 4x.

---

