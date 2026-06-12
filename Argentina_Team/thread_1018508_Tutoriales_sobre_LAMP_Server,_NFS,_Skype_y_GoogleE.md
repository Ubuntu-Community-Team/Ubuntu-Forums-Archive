---
title: "Tutoriales sobre LAMP Server, NFS, Skype y GoogleEarth en ubuntu-ar.org"
date: 2008-12-22
forum: Argentina Team
---

### Post by guillermolisi on 2008-12-22
Se han publicado los tutoriales del asunto en nuestro site gracias a la colaboracion de Fernando Sismonda y Alvaro Soliverez, en esta oportunidad.

Para leerlos, apuntar el navegador a [http://ubuntu-ar.org](http://ubuntu-ar.org) - Soporte - Tutoriales

---

### Post by Hei Ku on 2008-12-22
Dudas, correcciones o preguntas sobre los tutoriales, ponganlas en este thread. Gracias!

---

### Post by c4d0rn4 on 2008-12-22
no sería bueno, ya que están, poner un link directo a las guías? 

[http://ubuntu-ar.org/soporte/comos](http://ubuntu-ar.org/soporte/comos)

no se, pero me pareció medio rebuscado encontrarlas; faltaría un link en la parte de Accesos rápidos.

---

### Post by guillermolisi on 2008-12-22
> **c4d0rn4 said:**
> no sería bueno, ya que están, poner un link directo a las guías? 

[http://ubuntu-ar.org/soporte/comos](http://ubuntu-ar.org/soporte/comos)

no se, pero me pareció medio rebuscado encontrarlas; faltaría un link en la parte de Accesos rápidos.

No cuesta nada, es cierto, pero hay por lo menos dos ideas detras de esa omision.

La primera es que ingresen al site, lo naveguen, conozcan (hay gente nueva todo el tiempo), vean algunos pequeños cambios que se estan realizando, etc., etc. Es decir, que lo usen y tengan conocimiento de su contenido, posibilidades, etc. (no solo de un tutorial de interes especifico).

La segunda es la que acabas de hacer con tu comentario de que te parecio rebuscado. Feedbacks como ese nos sirven muchisimo para dejar lo que resulte de utilidad, quitar lo que no agregue valor a quienes lo visitan (para eso debe cumplirse lo que puse en el punto anterior) y adecuar lo que no sea funcional, con la idea de tender a que cada visitante logre una buena experiencia con cada visita al site.

Gracias por tus comentarios.

---

### Post by papachan on 2009-01-05
me gustó mucho el primer tutorial sobre Jdownloader, no tenia ni idea de este programa, quisiera mas tutoriales sobre herramientas que nos puedan servir a diario !

muchas gracias a todos !

---

### Post by sartrejp on 2009-01-29
La sección de los tutoriales está bárbara, pero creo que cabría una observación (desde mi humilde punto de vista).
Me resultaron muy interesantes los tutoriales, pero ya llevo un par de años con ubuntu, y me parece que tendría que haber más material orientado a quienes recién llegan (tablas de equivalencias, problemas comunes con la placa de videos, audio en dos programas a la vez, etc.) esas cuestiones sencillas pero que lo hacen a uno tambalear cuando empieza.

---

### Post by Hei Ku on 2009-01-29
Cualquiera de estas cosas sobre las que quieran mandar su aporte, solo tienen que mandarla y la agregamos a la FAQ u otra seccion correspondiente. ;)

---

### Post by guillermolisi on 2009-01-29
> **sartrejp said:**
> La sección de los tutoriales está bárbara, pero creo que cabría una observación (desde mi humilde punto de vista).
Me resultaron muy interesantes los tutoriales, pero ya llevo un par de años con ubuntu, y me parece que tendría que haber más material orientado a quienes recién llegan (tablas de equivalencias, problemas comunes con la placa de videos, audio en dos programas a la vez, etc.) esas cuestiones sencillas pero que lo hacen a uno tambalear cuando empieza.
Algo de eso hay en el website, algo parecido al sticky con los enlaces recomendados que HeiKu puso hace unos meses atras en este foro.

Igual, nada cuesta revisar y adecuar para lograr una mejora en el apoyo a los que se inician o refrescar la memoria de los "veteranos" con referencias como las que mencionas, en el website.

Gracias por la critica/sugerencia/opinion.

---

### Post by NickCis on 2009-02-05
Encontre un par de errores en esta guia (fueron problemas que tuve en mi pc, con ubuntu 8.04, no se si sera lo mismo para los demas, perdonenme si no es asi).
Guia de Servidor NFS: [http://ubuntu-ar.org/node/208](http://ubuntu-ar.org/node/208)

En donde dice
```
El archivo donde se definen los directorios a compartir es "/etc/exportfs".  Para editarlo se debe ejecutar el siguiente comando:

< sudo vi /etc/exportfs

```
El archivo no tendria que ser "/etc/exports" ? en vez de /etc/exportfs

Y antes de la verificacion tenes que hacer un "sudo /etc/init.d/nfs-kernel-server restart" para que te tome los cambios.

Dsp la verificacion, el comando que se debe ejecutar es "sudo exportfs" no "sudo export[COLOR="Red"]s[/COLOR]fs" (hay una S de mas entre la t y la f)

Ahh,, ademas tendrian que agregar algo que diga que los discos montados por fuse (o los de NTFS) no se pueden compartir por un bug del ubuntu...

Saludos. :P

---

### Post by Hei Ku on 2009-02-05
> **NickCis said:**
> Encontre un par de errores en esta guia (fueron problemas que tuve en mi pc, con ubuntu 8.04, no se si sera lo mismo para los demas, perdonenme si no es asi).
Guia de Servidor NFS: [http://ubuntu-ar.org/node/208](http://ubuntu-ar.org/node/208)

En donde dice
```
El archivo donde se definen los directorios a compartir es "/etc/exportfs".  Para editarlo se debe ejecutar el siguiente comando:

< sudo vi /etc/exportfs

```
El archivo no tendria que ser "/etc/exports" ? en vez de /etc/exportfs

Y antes de la verificacion tenes que hacer un "sudo /etc/init.d/nfs-kernel-server restart" para que te tome los cambios.

Dsp la verificacion, el comando que se debe ejecutar es "sudo exportfs" no "sudo export[COLOR="Red"]s[/COLOR]fs" (hay una S de mas entre la t y la f)

Ahh,, ademas tendrian que agregar algo que diga que los discos montados por fuse (o los de NTFS) no se pueden compartir por un bug del ubuntu...

Saludos. :P

Tenés razón en las correcciones. Respecto a los discos montados por fuse, el problema es solo con los NTFS.

Guille, podés hacer los cambios?

---

### Post by guillermolisi on 2009-02-16
> **Hei Ku said:**
> Tenés razón en las correcciones. Respecto a los discos montados por fuse, el problema es solo con los NTFS.

Guille, podés hacer los cambios?

Si, ya me estoy poniendo al dia luego de pasar unos dias de vacaciones en modo "detox" :D

Gracias por los comentarios y observaciones.

---

### Post by guillermolisi on 2009-02-16
Bueno, ya estan realizadas las adecuaciones junto con una mencion a la colaboracion brindada por NickCis.

Cualquier otra cosa que vean, ya saben que hacer para corregirla/mejorarla.

---

