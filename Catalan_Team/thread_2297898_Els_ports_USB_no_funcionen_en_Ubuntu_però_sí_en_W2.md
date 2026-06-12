---
title: "Els ports USB no funcionen en Ubuntu però sí en W2"
date: 2015-10-07
forum: Catalan Team
---

### Post by jinglada on 2015-10-07
Bona tarda, ubuntaires: Els ports USB no funcionen en Ubuntu, en canvi en W2, funcionen normalment. A la barra esquerra del "Navegador de fitxers" (Nautilus) no hi surten aquests dispositius externs. 

Ubuntu 14.04.3 LTS
x86_64
3.13.0-65-generic #106-Ubuntu SMP Fri Oct 2 22:08:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Comes pot solucionar?
Gràcies a la bestreta.

---

### Post by wgarcia on 2015-10-08
Vols dir que no es munta cap dispositiu que endolles a l'USB o que no veus els volums muntats al Nautilus, però sí que es munten?

---

### Post by jinglada on 2015-10-08
> **wgarcia said:**
> Vols dir que no es munta cap dispositiu que endolles a l'USB o que no veus els volums muntats al Nautilus, però sí que es munten?

Gràcies wgarcia:

Quan engego surten missatges que desapareixen ràpidament, com ara:

usb 2-5: device not accepting address 10, error -71 (més o menys)

------------------------------------------------------

Vaig fer "sudo dmesg -c" i després "dmesg" i no em va mostrar res.

------------------------------------------------------

És aleatori. De vegades els USB funcionen i d'altres, 9 de cada 10 engegades, no. En W2 funcionen sempre que hi entro, només per verificar els ports USB. Avui funcionen bé en Ubuntu.

-------------------------------------------------------

A veure si "fdisk -l" indica alguna cosa significativa:

joan@joan-Aspire-E1-572:~$ sudo su
[sudo] password for joan: 
root@joan-Aspire-E1-572:/home/joan# fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xdc4d3b68

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00002504

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 62.9 GB, 62932647936 bytes
61 heads, 61 sectors/track, 33032 cylinders, total 122915328 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcff28405

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdc1   *        8064   122915327    61453632    c  W95 FAT32 (LBA)

----------------------------------------------------------------------------------------------

---

### Post by jinglada on 2015-10-08
Per anar a dinar he aturat "temporalment" i al re-arrencar m'ha arrencat com si hagués aturat del tot i no funcionen els port USB.

He fet "sudo dmesg -c" i després "dmesg" i no em mostra res.

He fet "fdisk -l" i tampoc en dona res!

---

### Post by wgarcia on 2015-10-08
Sembla que tens 3 discos, que es munten a /dev/sda, /dev/sdb, i /dev/sdc. El tercer sembla és un disc formatejat amb FAT32, està endolat a USB?

El missatge que dones a dalt l'he vist quan hi ha problemes amb els cables USB, són molt sensibles i de seguida produeixen fallades. Però si a Windows no t'estan donant errors doncs no sembla aquest el tema.

Una cosa que pots provar és entrar amb l'usuari "Visitant", o crear-te un altre usuari, i mirar si aquest problema també hi és a un altre usuari. Si no hi fos podria estar indicant que hi ha algun problema amb el teu perfil d'usuari.

---

### Post by jinglada on 2015-10-08
Gràcies!

> **wgarcia said:**
> Sembla que tens 3 discos, que es munten a /dev/sda, /dev/sdb, i /dev/sdc. El tercer sembla és un disc formatejat amb FAT32, està endolat a USB?

Tinc el disc dur de 750 GB, un disc extern de 500 GB i un pendrive de 64 GB.

> **wgarcia said:**
> Una cosa que pots provar és entrar amb l'usuari "Visitant", o crear-te un altre usuari, i mirar si aquest problema també hi és a un altre usuari. Si no hi fos podria estar indicant que hi ha algun problema amb el teu perfil d'usuari.

Passa el mateix tant si entro amb el meu usuari com si entro com a convidat.

El que he observat és que abans de decidir amb quin usuari entro, si el llum vermell de sota el ratolí està encès, reconeix els ports USB i si està apagat no els reconeix.

---

### Post by wgarcia on 2015-10-09
Pots entrar una terminal, entrar l'ordre:
```
mount
```
i enganxar el que posa?

---

### Post by jinglada on 2015-10-09
> **wgarcia said:**
> Pots entrar una terminal, entrar l'ordre:
```
mount
```
i enganxar el que posa?

Ara els ports USB funcionen. 

joan@joan-Aspire-E1-572:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda7 on /home type ext4 (rw)
/dev/sda2 on /boot/efi type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=joan)
/dev/sdc1 on /media/joan/572d462a-94a7-41b4-924d-80b6183dbf8e type ext3 (rw,nosuid,nodev,uhelper=udisks2)

Ara pararé i quan torni al vespre ho tornaré a provar i si no funcionen, tornaré a fer "mount"

Gràcies!

---

### Post by jinglada on 2015-10-10
Avui no funcionen. Vet ací el "mount":

joan@joan-Aspire-E1-572:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda7 on /home type ext4 (rw)
/dev/sda2 on /boot/efi type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=joan)

---

### Post by wgarcia on 2015-10-10
Prova donar des d'una terminal la següent ordre:
```
sudo dpkg-reconfigure xserver-xorg
```
reiniciar i veure si funcionen els ports USB.
(Font: [http://askubuntu.com/questions/526082/2-usb-ports-stopped-working](http://askubuntu.com/questions/526082/2-usb-ports-stopped-working))

---

### Post by jinglada on 2015-10-10
> **wgarcia said:**
> Prova donar des d'una terminal la següent ordre:
```
sudo dpkg-reconfigure xserver-xorg
```
reiniciar i veure si funcionen els ports USB.
(Font: [http://askubuntu.com/questions/526082/2-usb-ports-stopped-working](http://askubuntu.com/questions/526082/2-usb-ports-stopped-working))

Gràcies, wgarcia. Ha funcionat. Esperaré un parell de dies a posar SOLVED.

---

### Post by wgarcia on 2015-10-10
Què bé, a veure si aguanta. Ara, no entenc com una cosa relacionada amb la gràfica pot arreglar el tema dels USB, misteris de la informàtica...

---

### Post by jinglada on 2015-10-10
Han tornat a fallar. He reiniciat entrant a W2 i després a Ubuntu i ara funcionen.

---

### Post by wgarcia on 2015-10-14
Llástima. Al fil que t'he passat:

[http://askubuntu.com/questions/52608...topped-working](http://askubuntu.com/questions/52608...topped-working)

diu que és un problema d'energia als ports USB, que el nucli de Linux (no sé si els més recents ho arreglen) per alguns dispositius no habiliten l'energia. També proposen una altra solució a part de la senzilla que vas provar a dalt. Mira si pots provar alguna d'aquestes altres solucions, sota la teva responsabilitat perquè impliquen remenar l'arrencada i això sempre et pot deixar sense arrencada. Si et passés es pot arreglar amb un CD o USB d'instal·lació iniciant una sessió autònoma (millor tenir-lo preparat). Si no entens el que s'ha de fer comenta-ho. 

Això que proposa per provar a l'arrencada també es pot provar en una arrencada abans de fer-lo permanent (al fil expliquen com fer-lo permanent), editant la línia d'arrencada a l'inici des del menú del Grub. Si vols provar això primer, es pot fer. Si no saps com editar la línia d'arrencada per una arrencada sola comenta-ho i ho repassem.

---

### Post by jinglada on 2015-10-14
Gràcies wgarcia!
He provat les dues solucions que donen i tot segueix igual, falla aleatòriament, al 50% d'arrencades, més o menys.

---

### Post by jinglada on 2015-10-15
Una altra verificació: Quan s'inicia l'ubuntu el llum del ratolí està encès i s'apaga quan surt el missatge "usb 2-5: device not accepting address 7, error -71", missatge que desapareix instantàniament però que l'he trobat fent "dmesg" al terminal.

---

### Post by jinglada on 2015-10-15
Ara he aconseguit que funcionin executant sudo dpkg-reconfigure xserver-xorg i reiniciant.

Pregunta: Es podria incloure aquesta comanda en algun lloc de l'arrancada?

---

### Post by wgarcia on 2015-10-16
Es podria incloure el "reconfigure" com a comanda a executar, però jo crec que no té massa sentit reconfigurar la gràfica a cada arrencada. 

Quant al missatge 
```
usb 2-5: device not accepting address 7, error -71
```
jo l'he vist quan hi ha problemes amb el cable o el connector d'algun port USB. Els dispositius USB són molt sensibles a la qualitat dels cables i els connectors. No estaria malament que els revisessis i poguessis provar amb cables alternatius, que no fos que hi hagués algun problema per aquest cantó.

---

### Post by jinglada on 2015-10-16
> **wgarcia said:**
> Quant al missatge 
```
usb 2-5: device not accepting address 7, error -71
```
jo l'he vist quan hi ha problemes amb el cable o el connector d'algun port USB. Els dispositius USB són molt sensibles a la qualitat dels cables i els connectors. No estaria malament que els revisessis i poguessis provar amb cables alternatius, que no fos que hi hagués algun problema per aquest cantó.

He arrancat i ha anat malament. He desconnectat el HD extern, he reiniciat i ha funcionat. Ho provaré així alguns cops més i ja informaré.

Gràcies, un cop més, wgarcia.

---

### Post by jinglada on 2015-10-20
> **jinglada said:**
> He arrancat i ha anat malament. He desconnectat el HD extern, he reiniciat i ha funcionat. Ho provaré així alguns cops més i ja informaré.

Gràcies, un cop més, wgarcia.

Tot segueix igual fins i tot desconnectant el ratolí; o sigui sense res connectat als ports USB. Si pot ser d'utilitat, podria copiar aquí els trossos del dmesg on esmenta "usb"per si dona alguna pista.

En W2, no fallen mai.

---

### Post by jinglada on 2015-10-25
Avui s'ha apagat el llum del ratolí quan ha sortit l'última de les següents línies:

[   21.092119] xhci_hcd 0000:00:14.0: xHCI host not responding to stop endpoint command.
[   21.092121] xhci_hcd 0000:00:14.0: Assuming host is dying, halting host.
[   21.092134] xhci_hcd 0000:00:14.0: HC died; cleaning up

---

### Post by wgarcia on 2015-10-26
No sé, no queda gaire més per provar que no sigui provar amb algun nucli més nou a veure si no és alguna cosa que s'ha arreglat amb controladors més nous al nucli

---

### Post by jinglada on 2015-10-26
Gràcies, wgarcia! 
Tinc Ubuntu 14.04.3 LTS. Quin nucli em recomanes?

---

### Post by wgarcia on 2015-10-28
Penso que el més recent és el millor que es pot provar, a veure si segueix reproduint aquest problema. Primer s'hauria de veure exactament quin nucli tens, amb l'ordre:

```
uname -a
```

Mentrestant per tenir una idea de què es tracta es pot llegir:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

A l'hora de provar un nucli potser el millor a provar seria:
v3.14-rc8-trusty/

Però si vols repassem com fer-ho ( i com desinstal·lar-lo si dóna problemes).

---

### Post by jinglada on 2015-10-28
Tinc això:

joan@joan-Aspire-E1-572:~$ uname -a
Linux joan-Aspire-E1-572 3.13.0-66-generic #108-Ubuntu SMP Wed Oct 7 15:20:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Veient la pàgina que em senyales m'adono que em ve una mica gran ;-) T'agrairia em donessis indicacions de com fer-ho.

---

### Post by wgarcia on 2015-10-28
D'acord. Bàsicament el que faràs serà instal·lar un nucli més nou, et crearà una entrada nova en el grub que serà la primera que es veurà per reiniciar l'ordinador en aquest nucli. Si el vols desinstal·lar hauràs d'iniciar l'ordinador, buscar en el grub l'entrada anterior a aquest nucli més nou (la que posa 3.13.0 que és la que tens ara), i desinstal·lar aquest nucli que vas provar. Un cop fet això al grub ja no es veurà més i es tornarà a veure com es veu ara. Aquesta solució més que res et mostrarà si els nuclis més nous han solucionat aquest problema que veus amb els USB, perquè no és una solució de llarg termini (el nucli més nou pot generar altres problemes, i no es podrà actualitzar). Però almenys sabràs que quan actualitzis tot el sistema a una nova versió de l'Ubuntu, el problema que tens segurament desapareixerà.

Per instal·lar el nucli que et suggeria has d'anar a aquest lloc:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc2-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc2-trusty/)

De la llista de fitxers que es veuen t'has de baixar els que estan marcats amb "X":
 
[X]	linux-headers-3.15.0-031500rc2-generic_3.15.0-031500rc2.201404201435_amd64.deb	20-Apr-2014 18:53 	1.1M	 
[ ]	linux-headers-3.15.0-031500rc2-generic_3.15.0-031500rc2.201404201435_i386.deb	20-Apr-2014 19:13 	1.0M	 
[ ]	linux-headers-3.15.0-031500rc2-lowlatency_3.15.0-031500rc2.201404201435_amd64.deb	20-Apr-2014 18:55 	1.1M	 
[ ]	linux-headers-3.15.0-031500rc2-lowlatency_3.15.0-031500rc2.201404201435_i386.deb	20-Apr-2014 19:14 	1.0M	 
[X]	linux-headers-3.15.0-031500rc2_3.15.0-031500rc2.201404201435_all.deb	20-Apr-2014 18:36 	12M	 
[X]	linux-image-3.15.0-031500rc2-generic_3.15.0-031500rc2.201404201435_amd64.deb	20-Apr-2014 18:53 	51M	 
[ ]	linux-image-3.15.0-031500rc2-generic_3.15.0-031500rc2.201404201435_i386.deb	20-Apr-2014 19:13 	51M	 
[ ]	linux-image-3.15.0-031500rc2-lowlatency_3.15.0-031500rc2.201404201435_amd64.deb	20-Apr-2014 18:55 	51M	 
[ ]	linux-image-3.15.0-031500rc2-lowlatency_3.15.0-031500rc2.201404201435_i386.deb	20-Apr-2014 19:14 	51M	 

Els has de baixar tots a la mateixa carpeta, obrir una terminal i anar a aquesta carpeta. Un cop fet això la següent instrucció els instal·larà:

```
sudo dpkg -i *.deb
```

Ara pots reiniciar l'ordinador i hauries de veure una primera entrada al grub que mostra 

```
Ubuntu Trusty, kernel 3.15.4-031500rc2-generic
```

Un cop provat el nucli, si el vols desinstal·lar entra al grub, escull el nucli anterior, 3.13.0-66-generic,  i des d'una terminal:

```
dpkg -l | grep "linux\-[a-z]*\-" | grep 3.15.0
```

Això et mostrarà els paquets que has instal·lat d'aquest nucli (seran 3 o quatre línies i és el que posa després de "ii"). Per desinstal·lar ara fas:

```
 sudo apt-get remove <PAQUETS QUE HAS IDENTIFICAT EN EL PAS ANTERIOR> 
```

Ja s'haurien d'haver desinstal·lat, però perquè no et tornin a aparèixer a l'ordre "dpkg" ara pots fer:

```
sudo dpkg --purge ENTRY
```

---

### Post by jinglada on 2015-10-28
Gràcies, wgarcia! Demà ho provaré i ja et diré com ha anat.

---

### Post by wgarcia on 2015-10-29
Tingues com sempre una bona còpia de seguretat i un disc o USB d'arrencada que sàpigues que funciona. No ha de passar res, aquest procediment l'he fet molts cops, però sempre s'ha d'anar amb cura quan remenem aquestes coses.

---

### Post by jinglada on 2015-11-02
Sembla que el problema s'ha solucionat amb la teva última proposta d'instal·lar un nucli nou.

joan@joan-Aspire-E1-572:~$ uname -a
Linux joan-Aspire-E1-572 3.15.0-031500rc2-generic #201404201435 SMP Sun Apr 20 18:36:18 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Des que vaig fer la instal·lació he engegat 3 vegades i no n'ha fallat cap.

Gràcies, wgarcia.

---

### Post by wgarcia on 2015-11-03
A veure si hi ha sort.

En tot cas és una solució provisional perquè no sé si s'anirà actualitzant aquest nucli. El que sí mostra és que quan surti la nova versió de llarg termini, la 16.04 a l'abril de l'any que ve, el més probable és que aquest problema dels USB se't solucioni.

---

