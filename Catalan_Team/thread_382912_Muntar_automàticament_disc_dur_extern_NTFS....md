---
title: "Muntar automàticament disc dur extern NTFS..."
date: 2007-03-12
forum: Catalan Team
---

### Post by peremayol on 2007-03-12
Hola,

Tinc un disc dur extern de 250G que vaig formatar en NTFS. Ara, en connectar-ho a l'USB del meu portàtil amb Ubuntu, me'l munta com a Només lectura.
Voldria que se'm muntés automàticament com a RW.
Ja he baixat els drivers ntfs3g, però no sé com configurar l'ubuntu per que el carregui en RW en connectar el disc dur extern.

Alguna idea?
Moltes gràcies
Pere

---

### Post by DerHesse on 2007-03-12
Que tal tu fstab? 
```
$ cat /etc/fstab
```
Que idioma hablas, catalan?

---

### Post by peremayol on 2007-03-12
Sí, parlo català: Ubuntu LoCo Teams  > Catalan Team

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=4c063fc7-1aa0-4f29-a3be-35186334ad69 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=8a5f9fec-0a85-444b-8fc5-e34d571173f7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by marcoil on 2007-03-12
La propera versió d'Ubuntu inclourà l'[_ntfs-config_]("http://flomertens.free.fr/ntfs-config/"), una eina que s'encarrega de configurar això que demanes.

Pots trobar un paquet instal·lable per a la versió actual i més informació aquí mateix als fòrums:
[http://www.ubuntuforums.org/showthread.php?t=337970&highlight=ntfs-config](http://www.ubuntuforums.org/showthread.php?t=337970&highlight=ntfs-config)

Si t'ho vols instal·lar tu mateix, te recoman que vaig a la [_pàgina de l'ntfs-config_]("http://flomertens.free.fr/ntfs-config/") i també t'instal·lis el pmount que hi trobaràs.

---

### Post by peremayol on 2007-03-13
Ho he instal.lat, però quan he connectat el disc dur extern. M'apareix un error en muntar-se

$logfile indicates unclean shutdown (0, 0)

failed to mount '/dev/sda1': operation not supported

mount is denied because ntfs logfile is unclean. choose one action:

   boot windows and shutdown it cleanly, or if you have a removable

   device then click the 'safely remove hardware' icon in the windows

   taskbar notification area before disconnecting it.

or

   run 'ntfsfix' on linux unless you have vista, then mount ntfs with

   the 'force' option read-write, or with the 'ro' option read-only.

or

   mount the ntfs volume with the 'ro' option in read-only mode.

error: no s'ha pogut executar pmount



Alguna idea de què fer?
Moltes gràcies per endavant
Pere

---

### Post by RainCT on 2007-03-13
Prova a seguir les instruccions que hi ha a [http://www.ubuntu-es.org/node/21061](http://www.ubuntu-es.org/node/21061), a mi em va funcionar.

---

### Post by RainCT on 2007-03-13
(Post duplicat)

---

### Post by CarlesOriol on 2007-03-13
Sols et diu que tens errors al disc i que si el vols muntar o:

A- Engegues el uiondous i comproves el disc

o

B- Uses una eina en linux per testejar-lo.

Jo et recomano que ja que tens els disc en uindous ho facis amb aquest.

Després tornes a iniciar l'ubuntu i ... ja està. 

Per cert et calen 3 reinicis

       1- Engegues el uindous i dius que et comprovi el disc ... ho farà quan reiniciis
       2- Tornes a iniciar-lo i t'arregla els errors del disc. (el disc està marcat encara per reparar)
       3- Tornes a reiniciar ... i et treu les marques de comprovació del disc.

...i ja està....

---

### Post by peremayol on 2007-03-13
No m'aclareixo amb el post que m'heu enviat. No és gaire "for human beings"...
Alguna idea concreta de com arreglar l'error?
Gràcies
Pere

---

### Post by CarlesOriol on 2007-03-14
No... tens raó... l'error que et produeix el unindous no és gaire "for human beings".

Arregla el disc des de uindous

---

