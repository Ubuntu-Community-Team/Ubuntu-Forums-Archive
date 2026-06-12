---
title: "error al actualizarme"
date: 2007-10-21
forum: Argentina Team
---

### Post by dj_isaco on 2007-10-21
hola a todos si ya se muchas preguntas :confused:pero asi se aprende no, bueno hoy quise actualiza mi distro; jajaja ya estoy aprendiendo a utilizar el dialecto; volvamos como les decia cuando quise actulizarme me dio este error y no se porq pudo haber sido:

[http://ar.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:](http://ar.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:) El subproceso gzip devolvió un código de error (1)

despues aparecio esto

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 3E231AC7F4ECF181

y no me deja actualizar nada, que pudo haber pasado, pero me imagino, si alguien me puede ayudar se lo agradecere gracias y hasta la proxima.

Lo q me imagine no era, luego de editar el sources.list colocando un "#" antes de la dire tuxfamily, como me soluciono antes otros problemas; pero en esta ocacion no sugio efectos y me dio estos errores:

[http://ar.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:](http://ar.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:) No pude resolver 'ar.archive.ubuntu.com'
[http://ar.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-es.bz2:](http://ar.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-es.bz2:) No pude resolver 'ar.archive.ubuntu.com'
[http://ar.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-es.bz2:](http://ar.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-es.bz2:) No pude resolver 'ar.archive.ubuntu.com'
[http://ar.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-es.bz2:](http://ar.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-es.bz2:) No pude resolver 'ar.archive.ubuntu.com'
[http://ar.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-es.bz2:](http://ar.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-es.bz2:) No pude resolver 'ar.archive.ubuntu.com'
[http://ar.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-es.bz2:](http://ar.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-es.bz2:) No pude resolver 'ar.archive.ubuntu.com'
[http://ar.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-es.bz2:](http://ar.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-es.bz2:) No pude resolver 'ar.archive.ubuntu.com'
[http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:) No pude resolver 'security.ubuntu.com'
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-es.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-es.bz2:) No pude resolver 'security.ubuntu.com'
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-es.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-es.bz2:) No pude resolver 'security.ubuntu.com'
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-es.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-es.bz2:) No pude resolver 'security.ubuntu.com'
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-es.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-es.bz2:) No pude resolver 'security.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:) No pude resolver 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-es.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-es.bz2:) No pude resolver 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-es.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-es.bz2:) No pude resolver 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-es.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-es.bz2:) No pude resolver 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-es.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-es.bz2:) No pude resolver 'archive.ubuntu.com'
[http://ar.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:](http://ar.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:) El subproceso gzip devolvió un código de error (1)

aca les dejo el sources ya editado

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
##andabien
## Avant Window Navigator
##deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
##deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

seguimos intentando....

---

### Post by Hei Ku on 2007-10-21
un mantenedor cambió su clave. Pone esto en una consola:

wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update

---

### Post by samanosuke1983 on 2007-10-23
excelente. gracias...

:):)

---

### Post by dj_isaco on 2007-10-23
gracias Hei Ku pero como se cuando un mantenedor cambia su clave?

---

### Post by facundocorradini on 2007-10-23
pues cuando te aparezcan de nuevo esos errores :p :p :p

Esas cosas no pasarían si no usaras repositorios externos. Que paquetes necesitabas de esos repos? seguro seguro que no estaban en los de ubuntu?

---

### Post by Hei Ku on 2007-10-24
El problema es que fueron los mantenedores de Ubuntu los que cambiaron su clave. :D

---

