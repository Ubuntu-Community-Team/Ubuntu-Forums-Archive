---
title: "No reconeix CD/DVD"
date: 2016-06-05
forum: Catalan Team
---

### Post by martibitria on 2016-06-05
Hola a tots/es,

Tinc instal·lat per .ISO el Ubuntu 16.04LTS, en un Toshiba Satellite L20 (venia amb XP)

Tinc un problema que no amb reconeix els CD/DVD.

He mirat per Google a varis llocs, i he fet cas a tot el que em deia, però no m'en surto.

A uns llocs deia en el terminal posar sudo lshw, no surt res del CD,cdrom, dvd,......

En deia fdisk -l, em diu:
fdisk: /dev/ram0 no es pot obrir: s'ha denegat el permis
fdisk: /dev/ram1 no es pot obrir: s'ha denegat el permis
fdisk: /dev/ram2 no es pot obrir: s'ha denegat el permis....

igual fins al 15 i l'ultim
fdisk: /dev/sda no es pot obrir: s'ha denegat el permis

Si necessiteu alguna dada més m'ho feu saber.

Gracies

Jeep/Martí

---

### Post by wgarcia on 2016-06-06
Estàs fent servir l'escriptori per defecte (l'Unity) o algun altre escriptori dels disponibles a l'Ubuntu? 

En tot cas mira aquest fil recent, on hi havia el mateix problema:
[http://ubuntuforums.org/showthread.php?t=2312491](http://ubuntuforums.org/showthread.php?t=2312491)

Finalment el que ha semblat funcionar, fins que no s'arregli el muntatge automàtic dels CD que hauria de funcionar sense fer res, és donar les següents ordres des d'una terminal:

```
sudo mkdir /mnt/cdrom
```
```
sudo mount -t iso9660 /dev/cdrom /mnt/cdrom
```

Si tot ha anat bé, s'hauria de poder accedir a aquesta carpeta des del navegador de fitxers. En cas que funcioni i t'animis, també es pot fer perquè es munti aquesta carpeta automàticament quan s'inicia l'ordinador i no s'hagi de donar aquesta ordre cada cop que es vol fer servir el CD.

---

### Post by martibitria on 2016-06-06
Gracies wgarcia!!
Després ho probaré!!!

salutacions

Martí

---

### Post by martibitria on 2016-06-06
Tinc UNITY!!
em surt això:

marti@marti:~$ sudo mkdir /mnt/cdrom
[sudo] contrasenaya per a marti: 
marti@marti:~$ sudo mount -t iso9660 /dev/cdrom /mnt/cdrom
mount: /dev/sr0 is write-protected, mounting read-only
mount: no medium found on /dev/sr0

---

### Post by wgarcia on 2016-06-06
Li havies posat un CD a la unitat? Si no en té cap no podrà muntar res.

---

### Post by martibitria on 2016-06-06
OK.

He posat un CD (en blanc) y ja l'ha reconegut.

S'ha obert la finestra que diu que vull fer, li he dit que preguntar sempre!!!

Ara ja esta tot?

Gracies

Martí

---

### Post by wgarcia on 2016-06-07
No és solució 100% perquè si has d'entrar les instruccions de dalt cada cop que poses un CD no és massa convenient. 

Pot provar que et diu la següent ordre des d'una terminal?
```
gsettings get org.gnome.desktop.media-handling automount
```

Hauria de donar "true".

---

### Post by martibitria on 2016-06-07
Sí, m'ha sortit [B]TRUE

[/B]Una altre pregunta a la terminal amb la ordre** sudo do-release-upgrade -d **he passat a la versió** 16.10, **(això m'ho van ensenyar a fer a SMX)Que et sembla?Gracies de nou
Martí

---

### Post by wgarcia on 2016-06-07
La versió 16.10 encara és de desenvolupament, i en estat molt embrionari. No convé utilitzar-la per ordinadors normals perquè és totalment experimental. Estàs segur que has actualitzat a aquesta versió 16.10? En tot cas aquest és un tema diferent, pel que fa al tema original d'aquest fil, sembla que està definit per automuntar els CD/DVD, per tant cap problema per aquest cantó. 

Per tant si ja et serveix muntar els CD donant l'ordre que et va funcionar a dalt (no s'ha de tornar a donar el "mkdir", la primera ordre, perquè això era per crear el directori i un cop creat ja no fa falta) es pot deixar com està. Suposo que en algun moment s'arreglarà el tema de muntar els discos automàticament un altre cop.

---

### Post by martibitria on 2016-06-07
OK, 
moltes gracies per tot.
un 10

salutacions 

Martí

---

