---
title: "Escriure en NTFS"
date: 2007-06-04
forum: Catalan Team
---

### Post by rajoar on 2007-06-04
A veure, segons Softcatalà es pot fer així:

Ja podem escriure sobre NTFS
Enviat per Jordi, 18:19:56 19/07/06

Ja podem llegir i escriure sense problemes sobre particions ntfs

NTFS-3G és un driver que utilitza FUSE(Filesystem in USErspace), fa que no formi part del kernel y no sigui necessari re compilar-lo per fer servir aquest driver, Per poder muntar particions ntfs(Windows XP) en linux de 32 bits i així escriure i llegir sense perill.

Com jo ho he fet en la CATix

Imprescindible: Tenir els arxius de capçalera (linux-headers) del kernel que fas servir a /usr/src i gcc, normalment ja hi són a totes les distribucions.


1.- Instal.lar FUSE 2.5 ([http://mesh.dl.sourceforge.net/sourceforge/fuse/fuse-2.5.3.tar.gz](http://mesh.dl.sourceforge.net/sourceforge/fuse/fuse-2.5.3.tar.gz)).

M'ha funcionat descomprimint-lo dins de /usr/src

Des de consola i tot com a root:
./configure
make
make install
modprobe fuse

2.- Instalem el driver ntfs-3g
ens el descarreguem d'aqui ([http://mlf.linux.rulez.org/mlf/ezaz/ntfs-3g-20070714-BETA.tgz](http://mlf.linux.rulez.org/mlf/ezaz/ntfs-3g-20070714-BETA.tgz))

Des de consola i tot com a root:
./configure
make
make install

3.- muntem la partició:
#mount -t ntfs-3g /dev/hdaX /mnt/hdaX
on hdaX es el dispositiu que representa la partició windows, igualment a /mnt.

Tot això com a root, així per escriure a la partició sols ho podrà fer root
si es vol editar fstab per a que es munti cada cop que arranquem la màquina,

si no, fem des de consola:
modprobe fuse
#mount -t ntfs-3g /dev/hdaX /mnt/hdaX
i tindrem accés de nou a la partició.

Sort

Ho he provat però quan estic al punt 3 (muntar la partició), hi poso:
# mount -t ntfs-3g /dev/hda1 /mnt/hda1
i em dóna el missatge d'error:
usermount: failed to access mountpoint /mnt/hda1: No such file or directory
FUSE mount point creation failed
Unmounting /dev/hda1 ()

Segons el Konqueror tinc el Windows a /media/sda1
Què és el que faig malament?...

Disculpeu però sóc una xic novell...

---

### Post by papapep on 2007-06-04
> Segons el Konqueror tinc el Windows a /media/sda1
Què és el que faig malament?...

T'ho està dient aquí:

> usermount: failed to access mountpoint /mnt/hda1: No such file or directory

Ja que tu intentes muntar el /media/sda1 dient-li que el tens a /mnt/hda1

> # mount -t ntfs-3g /dev/hda1 /mnt/hda1

O sigui, per si no m'he explicat, que la ordre correcta segons les teves dades, haurà de ser:

```
# mount -t ntfs-3g /dev/hda1 /media/sda1
```

---

### Post by jmaspons on 2007-06-04
Pel què sembla intentes muntar la partició en un directori que no existeix. Prova de muntar-ho a /media/hda1 en comptes de /mnt/hda1 o crea el directori /mnt/hda1 (sudo mkdir /mnt/hda1)
Prova amb:
```
sudo mount -t ntfs-3g /dev/hda1 /media/hda1
```

Pel què fa a l'intal·lació del driver jo et recomanaria que l'instal·lessis dels repositoris d'ubuntu (amb el synaptic per gnome o adept si utilitzes kde).

Sort!

---

### Post by rajoar on 2007-06-04
Bé, després de rectificar el directori em dóna l'error:
usermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/hda1 ()

Tampoc entenc que vol dir...

Ah! d'antuvi, moltes gràcies a tots...

---

### Post by patrickfromspain on 2007-06-04
sudo apt-get install ntfs-3g ntfs-config

facil no? ;)

---

### Post by rajoar on 2007-06-04
Sí, realment és fàcil fer-ho... Això m'ha instal·lat el menú NTFS Configuration Tool al submenú Sistema (sense icona), però quan el premo no fa absolutament res, com si no hi l'hagués pitxat...
Una mica extrany, no?...

---

### Post by patrickfromspain on 2007-06-04
podries probar a obrir-ho per consola:

gksudo ntfs-config

i a vere que et diu

---

