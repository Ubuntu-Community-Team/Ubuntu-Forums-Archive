---
title: "Permis per veure el Sisteme de fitxers"
date: 2009-10-14
forum: Catalan Team
---

### Post by pserra on 2009-10-14
Hola,
no se que em passa però no puc accedir al meu sistema de fitxers... se'm denega el permís...
per fer una carpeta (  ho faig de memòria)  no és chmod +r 777 (fitxer o carpeta)?
però en el cas de tot el sistema de fitxers on tinc el ubuntu com ho faig?
quina comanda he de fer servir?
Merci.

---

### Post by epages on 2009-10-16
Pots posar captura de missatge que et dona i mirar d'explicar-te una miqueta millor per tal de poder ajudar-te? :confused:

---

### Post by papapep on 2009-10-16
Pserra: si fas una llegida al que hi ha a aquest enllaç, probablement t'ajudi a aclarir alguns conceptes: [https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#Permisos](https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#Permisos)

I la ordre que poses, no és correcta del tot. Si poses :

```
sudo chmod 777 nomdelfitxer (o directori)
```

ja no et cal posar el -r, ja li dones permisos totals, compte que en MOLTS cops és desaconsellable, el 777, i el +r, en aquesta ordre i cas en concret, probablement faci que la ordre no executi cap modificació.

---

### Post by pserra on 2009-10-16
Merci per l'enllaç, molt util.....
el meu problema es que ara no puc accedir al director de sistemes de fitxers
si faig llocs->ordinador-<sistema de fitxers-> em diu que no es pot mostrar el contingut  de la carpeta... i em diu que no tinc el permís necessari per veure el contingut de  '/'.
el sistema de fitxers es sda7
el fstab em surt:


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=aa94329c-8110-44f0-8d5d-57611cb1e7a8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1134e58d-8967-4184-9fed-ed96cea20a7e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0```

```

---

### Post by pserra on 2009-10-16
ara estava rellegint el missatge del papapep:

               sudo chmod 777 nomdelfitxer (o directori)

puc fer:   sudo chmod 777 /sda7  ??

Merci

---

### Post by papapep on 2009-10-16
> ara estava rellegint el missatge del papapep:

sudo chmod 777 nomdelfitxer (o directori)

puc fer: sudo chmod 777 /sda7 ??

No, per vàries raons:

 a) /sda7 és una partició del disc dur, no un directori (a no ser que n'hagis creat un amb aquest nom, fet que no crec).

 b) fer això "a sac" són de les coses que trenquen un sistema de fitxers, com ara sembla que tens tu el teu :)

Has provat a crear un usuari nou i intentar entrar amb ell? és per veure si el problema està circumscrit al teu usuari o si tot el sistema de permisos està fet una coca.

---

### Post by pserra on 2009-10-18
Hola Papapep,
he creat un nou usuari i li he donat tots el privilegis d'usuari, però  des de ell tampoc  no tinc accés al sistema de fitxers, em surt el amteix missatge (adjunt).
Que més puc provar?
Merci

---

### Post by papapep on 2009-10-18
Doncs pinta malament. Enganxa el resultat de fer un:

```
sudo ls -la /
```

---

### Post by pserra on 2009-10-18
**aqui esta el resultat de la comanda:**
pere@pere-portatil:~$ sudo ls -la /
[sudo] password for pere: 
total 108
d-wx--x--x  23 root root  4096 2009-10-15 02:04 .
d-wx--x--x  23 root root  4096 2009-10-15 02:04 ..
drwxr-xr-x   2 root root  4096 2009-07-17 00:48 bin
drwxr-xr-x   3 root root  4096 2009-10-01 01:20 boot
lrwxrwxrwx   1 root root    11 2009-06-26 17:35 cdrom -> media/cdrom
drwxr-xr-x  18 root root  4660 2009-10-18 19:07 dev
drwxr-xr-x 153 root root 12288 2009-10-18 19:07 etc
drwxrwxrwx   4 root root  4096 2009-10-18 02:02 home
lrwxrwxrwx   1 root root    33 2009-08-22 11:21 initrd.img -> boot/initrd.img-2.6.28-15-generic
lrwxrwxrwx   1 root root    33 2009-07-30 09:46 initrd.img.old -> boot/initrd.img-2.6.28-14-generic
drwxr-xr-x  19 root root 12288 2009-10-15 23:55 lib
drwxr-xr-x   2 root root  4096 2009-09-21 10:21 lib64
drwx------   2 root root 16384 2009-06-26 17:34 lost+found
drwxr-xr-x   7 root root  4096 2009-10-18 19:07 media
drwxr-xr-x   2 root root  4096 2009-04-13 11:33 mnt
drwxrwxrwx   3 root root  4096 2009-10-12 02:49 mount-point
drwxr-xr-x   3 root root  4096 2009-10-15 02:04 opt
dr-xr-xr-x 152 root root     0 2009-10-18 21:06 proc
drwx------  14 root root  4096 2009-10-16 16:26 root
drwxr-xr-x   2 root root  4096 2009-09-21 10:21 sbin
drwxr-xr-x   2 root root  4096 2009-03-06 17:21 selinux
drwxr-xr-x   2 root root  4096 2009-04-20 15:59 srv
drwxr-xr-x  12 root root     0 2009-10-18 21:06 sys
drwxrwxrwx  12 root root  4096 2009-10-18 19:07 tmp
drwxr-xr-x  13 root root  4096 2009-07-09 11:19 usr
drwxr-xr-x  15 root root  4096 2009-04-20 16:07 var
lrwxrwxrwx   1 root root    30 2009-08-22 11:21 vmlinuz -> boot/vmlinuz-2.6.28-15-generic
lrwxrwxrwx   1 root root    30 2009-07-30 09:46 vmlinuz.old -> boot/vmlinuz-2.6.28-14-generic
pere@pere-portatil:~$

---

### Post by oriolsbd on 2009-10-18
En el llistat que passes, es veu que només tens falta d'accés al directori "/" en sí, i no al que hi penja. Això es pot veure perquè només el "." (i el "..") no té els permisos "r". Per arreglar-ho, executa la comanda següent:
```
sudo chmod +r /
```
Salut!

---

### Post by pserra on 2009-10-18
Merci Oriolsbd,
problema solventat.....
Ja hi tinc accés.
A reveure.

---

