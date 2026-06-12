---
title: "clonatge entre disc IDE a SATA no s'inicia X."
date: 2010-01-25
forum: Catalan Team
---

### Post by indiosincracia on 2010-01-25
Hola,
vaig fer un clon d'un disk IDE a un disc dur SATA nou (vull dir que no està fotut)
sudo dd if=/dev/sda of=/dev/sdb bs=1M

al comprovar si s'havia copiat i iniciava bé deixant el disc SATA sol i reiniciant l'ordinador no s'engegen les X. 

Grup 2.6.31-17-generic

es para a:
root@ordinador:~#  * Starting init crypto disks...
control+c

root@ordinador:~#startx
mktemp: failed to create file via template '/tmp/serverauth.XXXXXXXXXX': Read-only file system
/usr/bin/startx: line 157: cannot create temp file for here-document: Read-only file system
xauth: error in locking authority file /root/.Xauthority
mktemp: failed to create file via template '/tmp/serverauth.XXXXXXXXXX': Read-only file system
/usr/bin/startx: line 173: cannot create temp file for here-document: Read-only file system
xauth: error in locking authority file /root/.Xauthority
/usr/bin/startx: line 173: cannot create temp file for here-document: Read-only file system

Fatal server error:
Could not create lock file in /tmp/.tX0-lock

Please consult the The X.Org Foundation support
at [http://wiki.x.org](http://wiki.x.org) for help

ddxSigGiveUp: Closing log
giving up.
xinit: Connection refused (errno 111): unable to connect to x server
xinit: No such process (errno 3): Server error.
xauth: error in locking authority file /root/.Xauthority
root@ordinador:~#

que puc fer per que el SATA s'engegui igual que l'altre:confused:, merci

---

### Post by papapep on 2010-01-25
Et diu a diversos llocs que /tmp i /root no tenen permisos per escriure-hi.
Revisa els permisos del sistema de fitxers.

Estàs intentant arrencar el sistema gràfic com a root? ho has provat com a usuari normal?

---

### Post by PatrickVogeli on 2010-01-25
el sistema de fitxers s'ha montat com a només de lectura... prova a pasar-hi un fsck, a veure si això ho soluciona.

salut

---

### Post by indiosincracia on 2010-01-25
> Estàs intentant arrencar el sistema gràfic com a root? ho has provat com a usuari normal?

ep! aquesta és la clau, merci.
root@ordinador:~# exit
"parrafada sobre inconsistència", he passat el GParted Live CD i tema resolt:D

m'agradaria saber però, si es possible que aquest error el doni el fet que mentre es fa la copia s'activi l'"screensaver" o el "powermanager", és possible això?, merci un cop més.

---

### Post by papapep on 2010-01-25
Uhm...has fet còpia amb 'dd' d'un sistema de fitxers muntat i en funcionament?

Això s'ha de fer sempre, per exemple, des d'un cd en viu, amb els sistemes de fitxers orígen i destí desmuntats :)

---

### Post by indiosincracia on 2010-01-25
sipp,:D entesos, com diu la dita popular: Mai t'agitaràs sense mirar el teu ordinador desde la punta del nas.

---

