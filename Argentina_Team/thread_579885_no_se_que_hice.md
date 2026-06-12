---
title: "no se que hice"
date: 2007-10-18
forum: Argentina Team
---

### Post by dj_isaco on 2007-10-18
hola a todos estuve queriendo instalar AWM y no q hice en la lista de repositorio, y bueno despues de luchar un poco y me di por vencido cuando volvi a prender la maq me aparecio un cartel diciendome que habia ocurrido un error y q ejecute el gestor de paq y el msj era 
E, linea 44 mal formada en lista de fuentes /etc/apt/sources.list (dist absoluta)
E: No se pudo leer la lista de fuentes.
Vaya al diálogo del repositorio para corregir el problema.
E: _cache->open() failed, please report.
bueno no q hacer si alguien tiene una respuesta se los agradecere:)

---

### Post by sajnox on 2007-10-18
Pareceria que para agregar el AWN agregaste alguna linea al sources.list (es el listado de repositorios del sistema)

Lo primero que podes hacer para evitar el problema es lo siguiente:

```
$ sudo gedit /etc/X11/apt/sources.list
```

Busca la linea 44 y ponele un # adelante para que la omita, guardalo y sali, y desde una consola proba lo siguiente

```
$ sudo apt-get update
```

Esto deberia dejar de tirar errores

tambien te diria que nos copies el contenido de tu sources.list aca para que lo podamos ver.

Saludos

---

### Post by dj_isaco on 2007-10-18
gracias por responder mira borre todo y me quedo esto 

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
ahora nose si me falta algo 
por lo menos anda q es algo :):)

---

### Post by Mauro22 on 2007-10-18
te falta el de AWN, aunque este es para Gusty Gibbon

```
deb http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
```

Salu2

---

