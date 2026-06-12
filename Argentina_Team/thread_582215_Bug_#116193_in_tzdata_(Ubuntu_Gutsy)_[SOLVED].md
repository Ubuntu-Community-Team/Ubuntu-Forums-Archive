---
title: "Bug #116193 in tzdata (Ubuntu Gutsy) [SOLVED]"
date: 2007-10-19
forum: Argentina Team
---

### Post by clasificado on 2007-10-19
¡Buenas a Todos!

Queria comentarles un error que tuve al momento de actualizar de Fiesty a Gutsy.

La cosa es simple: No terminó. No violvió a abrir el Gestor de Actualizaciones, y el synaptic mostraba el paquete tzdata instalado, aunque no podia configurarse, y al no configurarse no instalaba, removia ni actualizaba ningun paquete nuevo.

Trankado.

**El problema:**
```
teclado@negra:~$ sudo dpkg --configure tzdata
Password:
Configurando tzdata (2007f-3ubuntu1) ...
dpkg: error al procesar tzdata (--configure):
 el subproceso post-installation script devolvió el código de salida de error 10
Se encontraron errores al procesar:
 tzdata

```

**La solución:**
Cambiar el contenido del archivo /etc/timezone con 
```
America/Buenos_Aires
```
Y despues, volver a intentar
```
teclado@negra:~$ sudo dpkg --configure tzdata
Configurando tzdata (2007f-3ubuntu1) ...

User defined timezone, leaving /etc/localtime unchanged.
Local time is now:      Fri Oct 19 20:22:57 ART 2007.
Universal Time is now:  Fri Oct 19 23:22:57 UTC 2007.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

```

Desde ahi, todo fue felicidad.

[CENTER]*_POSTLUDIO_*[/CENTER]

Parece que es un problema conocido, y bastante hincha en otras partes del mundo, y que se les escapó la tortuga a la gente de ubuntu, segun:
[https://bugs.launchpad.net/ubuntu/gutsy/+source/tzdata/+bug/116193](https://bugs.launchpad.net/ubuntu/gutsy/+source/tzdata/+bug/116193)

Clasificado.

---

### Post by MeduZa on 2007-10-19
hoy tenia 1 actualizacion en mi 6.04, y era ese mismo packete que decis vos, tambien tengo la distro update esperando a que le haga click!!

---

### Post by undiaperfecto on 2007-10-20
yo tuve el mismo problema, pero me impaciente y hice una instalacion desde cero y la verdad quedo mucho mas lindo.

---

### Post by rojojuan on 2007-10-20
Por ahora sigo usando 7.04.
Recién me apareció una notificación de soft para descarga. Se trata de una versión nueva de TZDATA.
Actualicé sin problemas.
Me parece que esta modificación solucionará para el futuro la actualización a Gusty Gibbon.
Espero sirva esta noticia.

---

### Post by JoACoV on 2007-10-22
yo tengo el mismo problema (instale gutsy de 0)

despues de cambiar el /etc/timezone

probe varias posibilidades:
```

America/Argentina/Cordoba (asi lo tenia por defecto)
America/Argentina/Buenos_Aires
America/Buenos_Aires
America/Cordoba

```y me sigue tirando esto
```

joaco@jubuntu:~$ sudo dpkg --configure tzdata
[sudo] password for joaco:
Configurando tzdata (2007h-0ubuntu0.7.10) ...
dpkg: error al procesar tzdata (--configure):
 el subproceso post-installation script devolvió el código de salida de error 10
Se encontraron errores al procesar:
 tzdata
joaco@jubuntu:~$ 

```les dejo tambien mi locale por las dudas
```

joaco@jubuntu:~$ locale
LANG=es_AR.UTF-8
LC_CTYPE="es_AR.UTF-8"
LC_NUMERIC="es_AR.UTF-8"
LC_TIME="es_AR.UTF-8"
LC_COLLATE="es_AR.UTF-8"
LC_MONETARY="es_AR.UTF-8"
LC_MESSAGES="es_AR.UTF-8"
LC_PAPER="es_AR.UTF-8"
LC_NAME="es_AR.UTF-8"
LC_ADDRESS="es_AR.UTF-8"
LC_TELEPHONE="es_AR.UTF-8"
LC_MEASUREMENT="es_AR.UTF-8"
LC_IDENTIFICATION="es_AR.UTF-8"
LC_ALL=

```

EDIT: en mi busqueda por arreglar el problema crashee el sistema a tal punto que (en mi nivel de usuario) no  huvo mas remedio que hacer una fresh install

---

