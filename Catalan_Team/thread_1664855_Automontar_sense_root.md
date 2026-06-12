---
title: "Automontar sense root"
date: 2011-01-11
forum: Catalan Team
---

### Post by tanreb20 on 2011-01-11
Bon dia!

Fa un temps vaig conseguir, grácies a un programa, que les particions NTFS i FAT32 que tinc al disc es montessin automaticament al inici, pero aixi pdoer tenir les dade si el Win64 montats i poder accedir al spotify y tot aixo...

Pero m'he trobat que, almenys la de dades (FAT32), es monta com a root.

Aixo em provoca més de una molestia, a vegades puc fer certes coses i a vegades no hi ha manera...

I evidentment no mola tenir els permisos a 777... alguna idea de com cambiar-los?

El fstab el tinc aixi:

```
alorma@Hogwarts:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda7 :
UUID=28c91a62-1219-4b4c-9de6-c53b1e09714c	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=9996ce8a-b65e-4b2e-a46b-1e41e5f93728	/home	ext4	defaults	0	2
#Entry for /dev/sda1 :
UUID=2AFCD8FFFCD8C5EB	/media/Windows	ntfs-3g	defaults,locale=es_ES.utf8	0	0
#Entry for /dev/sda8 :
UUID=d923b146-9d84-4056-a207-d9b098f120ff	/usr	ext4	defaults	0	2
#Entry for /dev/sda6 :
UUID=39c63229-54a7-4b05-bc2b-ee4826f7fa44	none	swap	sw	0	0

/dev/sda9 /media/DADES vfat rw,users,utf8,umask=000 0 0
```

El mtab aixi:

```
alorma@Hogwarts:~$ cat /etc/mtab
/dev/sda7 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
/dev/sda1 /media/Windows fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda9 /media/DADES vfat rw,noexec,nosuid,nodev,utf8,umask=000 0 0
/dev/sda5 /home ext4 rw,commit=0 0 0
/dev/sda8 /usr ext4 rw,commit=0 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
cgroup /dev/cgroup/cpu cgroup rw,cpu 0 0
gvfs-fuse-daemon /home/alorma/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=alorma 0 0

```

---

### Post by kimet on 2011-01-11
Es possible que es munti a un lloc diferent cada vegada.
Prova canviant /dev/sda9 per la seva UUID.
```
sudo blkid
```per saber la uuid.(amb el dispositiu muntat)

Si no funciona, prova a canviar les opcions de muntatge.

---

### Post by tanreb20 on 2011-01-11
Quines opcions canvio?

---

### Post by wgarcia on 2011-01-12
El suggeriment del kimet d'usar el uuid del disk en comptes del /dev/sda9 crec que et pot solucionar problemes.

Per exemple jo tinc per a un disc USB que munto en iniciar l'ordinador:

UUID=a9094f24-41ce-45ee-bb57-875682f263b5 /mnt/Backup    ext4    auto,user,rw,exec 0 0


Per una altra part, quins permisos tens a /media/DADES?, possiblement faci falta que el teu usuari sigui el propietari d'aquesta carpeta.

---

### Post by tanreb20 on 2011-01-12
```
drwxrwxrwx 14 root root 16384 1970-01-01 01:00 DADES
drwxrwxrwx  1 root root 16384 2011-01-05 02:43 Windows

```

Aixo és el que tinc quan faig un ls -l

---

### Post by wgarcia on 2011-01-12
Però suposo que /media/DADES és una carpeta "física", és a dir que no és un enllaç simbòlic sinó que està creada al sistema de fitxers. Per tant potser posant aquesta carpeta sota el teu usuari aconsegueixis que es munti de manera que puguis escriure a ella.

---

### Post by Compact on 2011-01-18
> **tanreb20 said:**
> 
Pero m'he trobat que, almenys la de dades (FAT32), es monta com a root.


El sistema de fitxers FAT32 no fa gestió de permisos, ni amb Windows: no està implementat en el sistema de fitxers, és per això que té permisos 777. Si ho intentes canviar, veuràs que no es canvia.

Una possible solució és muntar-ho dins d'una altra carpeta i que aquesta no tingui permisos d'accés a tothom.

---

