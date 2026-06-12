---
title: "problemq urgente!!!"
date: 2007-07-28
forum: Argentina Team
---

### Post by marcesneibrun on 2007-07-28
Hola no puedo activar ni el gestor synaptic, ni anadir y quitar aplicaciones, me tira el siguiente error:E: Línea 47 mal formada en lista de fuentes /etc/apt/sources.list (dist absoluta)
E: No se pudo leer la lista de fuentes.
Vaya al diálogo del repositorio para corregir el problema.
E: _cache->open() failed, please report.

alguien me puede ayudar por favor

GRACIAS MARCELO

---

### Post by kowal on 2007-07-28
Hay algo mal en los repositorios. Si podés posteá el contenido del archivo /etc/apt/sources.list

---

### Post by tony_feisty on 2007-07-28
Te fijaste si el archivo sources.list lo podes leer, anda desde la terminal  /etc/apt/sources.list y pegalo en el post, posiblemente haya un error en las lineas del archivo, por eso no te deja actualizar y te tira errores, asi te podemos dar una mejor ayuda.

Saludos.

---

### Post by marcesneibrun on 2007-07-28
HOLA ME TIRA ESTO bash: /etc/apt/sources.list: Permiso denegado
ALGUIEN SABE Q PUEDE PASAR__
MARCELO

---

### Post by marcesneibrun on 2007-07-28
ESTE ES EL ERROR Q TIRA>>

E: Línea 47 mal formada en lista de fuentes /etc/apt/sources.list (dist absoluta)

que hago

marcelo

---

### Post by tony_feisty on 2007-07-28
Desde la terminal en el signo $ escribi lo siguiente:

sudo nano /etc/apt/sources.list

te va a pedir password escribi lo que pusiste.

marca todo lo que te muestra y pegalo en el post.

---

### Post by marcesneibrun on 2007-07-28
te cuento lo q paso
puse despues del signo $ sudo nano..........
me pide el pasword, lo quiero poner y no me lo acepta.
Entonces lo q hice es poner su y enter
me pide el paswoord y ahi lo acepta
paso a ser usuario root , pongo devuelta sudo nano........
y me tira lo siguiente:
sudo: nano/etc/apt/sources.list: command not found
root@cpe-190-55-66-195:/home/marcelosneibrun# 

q hago__

marcelo

---

### Post by lavaramano on 2007-07-28
> **marcesneibrun said:**
> te cuento lo q paso
puse despues del signo $ sudo nano..........
me pide el pasword, lo quiero poner y no me lo acepta.
Entonces lo q hice es poner su y enter
me pide el paswoord y ahi lo acepta
paso a ser usuario root , pongo devuelta sudo nano........
y me tira lo siguiente:
sudo: nano/etc/apt/sources.list: command not found
root@cpe-190-55-66-195:/home/marcelosneibrun# 

q hago__

marcelo

teniendo en cuenta que te aparece esto:
sudo: nano/etc/apt/sources.list: command not found

yo te diria que dejes un espacio entre nano y /etc/apt/sources.list ;P

pd: si sos root no hace falta que uses al sudo.

---

### Post by marcesneibrun on 2007-07-28
hola probe de vuelta y me tiro todo esto:


#
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main $
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty universe
                               [ Leer 47 líneas ]
^G Ver ayuda ^O Guardar   ^R Leer Fich ^Y Pág Ant   ^K Cortar Tex^C Pos actual
^X Salir     ^J Justificar^W Dónde Está^V Pág Sig   ^U PegarTxt  ^T Ortografía

pueden ayudarme ahora

gracias 

marcelo

---

### Post by marcesneibrun on 2007-07-28
hola esto es lo q aparece:

#
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main $
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty universe
                               [ Leer 47 líneas ]
^G Ver ayuda ^O Guardar   ^R Leer Fich ^Y Pág Ant   ^K Cortar Tex^C Pos actual
^X Salir     ^J Justificar^W Dónde Está^V Pág Sig   ^U PegarTxt  ^T Ortografía

me pueden ayudar_

gracias

marcelo

---

### Post by marianom on 2007-07-28
Marcelo, por favor, si todos los posts son del mismo tema intentá mantenerlos dentro del mismo thread.
Gracias.

---

### Post by tony_feisty on 2007-07-28
El error es que hay algo que puede ser que este mal escrito en el sources.list, no pegaste todo archivo completo solo una parte. te adjunto un script del feisty y comparalo. Fiajte si te sirve, sino probamos con otra cosa.


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

---

### Post by Hei Ku on 2007-07-28
podes probar lo siguiente:

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo touch /etc/apt/sources.list
sudo apt-get update

despues de eso:
sudo nano /etc/apt/sources.list.bak

copia todo el contenido del archivo al portapapeles y cerralo

sudo nano /etc/apt/sources.list
pega lo que copiaste del otro archivo

sudo apt-get update

si te sali algun error en el proceso, postea todo el mensaje de error.

---

### Post by kalel on 2007-07-31
hace esto


gedit /etc/apt/sources.list

y borra todo y pega esto


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



luego apt-get update

luego apt-get upgrade

no puse sudo pk supongo que estas con root, sino usa sudo

---

