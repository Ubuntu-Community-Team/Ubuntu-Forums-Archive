---
title: "Problema amb mount i GDM"
date: 2009-09-19
forum: Catalan Team
---

### Post by seimulus on 2009-09-19
Bon dia a tothom. Ja fa temps que intento defendre'm amb Ubuntu i fins ara m'ha anat força be. quan he tingut problemes sempre els he solucionat mirant per forums o per internet, pero amb el problema que tinc ara no trobo solucio. Explico:

He tingut un problema amb les locals i els accents. Definint tot com a ca_ES no tinc accents i, en canvi, com a es_ES si. Despres de molt provar i demes, en un dels meus reboots, no em carrega ubuntu i em dona error de "kinit: no resume image". ho soluciono fent #swapoff /dev/sda3 i #mkswap /dev/sda3 i #update-initramfs -u.

Sembla que ja no dona l'error de kinit, pero no arrenca el sistema grafic GDM. Obre una consola demanant login. Si executo GDM no em troba /home

Si executo #mount, no esta muntada /dev/sda8 que es /home. aixi que perque tot funcioni be, he de fer:
- loguejar com a user
$ sudo mount -a
$ sudo gdm
.. i el sistema arrenca normalment.

On est`a l'errada? com ho soluciono per a que arrenqui automaticament? alguna idea? val la pena o millor reinstalar el sistema?
Gracies

---

### Post by kimet on 2009-09-20
Hauries d'afegir a /etc/fstab la teva partició /home si es que no la hi tens.

Salut.

---

### Post by seimulus on 2009-09-20
Si que hi es...
El que no se es perque no la carrega desde el inici... ni la /home ni la /boot estan disponibles, tot i que la /FAT32 si. Perque carrega algunes particions i no unes altres?

```
camulus@MIKAC:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=1ea50327-fee6-45a4-b950-15a0e4592597 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=709F-A194              /FAT32            vfat    utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=82c4d455-d158-4ebb-a1b7-021d51afa5d1 /boot           ext3    relatime        0       2
# /dev/sda8
UUID=bbd68d58-e7c6-47a3-b24d-e8e2afefd784 /home           xfs     relatime        0      2
# /dev/sda6
UUID=b982cda8-79cb-4573-b7ee-43eded3d73ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
camulus@MIKAC:~$
```

---

### Post by seimulus on 2009-09-21
Cap mes idea? No trobo res de res...

---

### Post by kimet on 2009-09-21
-Pots intentar cambiar del teu fstab la opció: "relatime" (que no se que significa) per "defaults" (que inclou "auto")

-Pots comprovar les UUID que no hagin cambiat, sobretot la de swap.

-Mira si al repositoris hi tens un programa per configurar el fstab en forma grafica.
disk-manager??

- Ve en compte i fes copia del fitxer abans per si de cas.

Salut.

---

### Post by seimulus on 2009-09-21
Hola, gracies per contestar. He canviat l'opció relatime (es veu que es un sistema de registrar els accessos al fitxer, surt per defecte a la darrera versio d'Ubuntu) per default però no ha funcionat.

He revisat les UUID i tenies raó, la de la swap no coincidia. Pero tot i canviant-la, no rutlla. mira:

```
camulus@MIKAC:~$ blkid
/dev/sda1: UUID="742C76F6E49BED2A" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="64E88CFCE88CCE2C" LABEL="ACER" TYPE="ntfs" 
/dev/sda5: UUID="82c4d455-d158-4ebb-a1b7-021d51afa5d1" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda6: TYPE="swap" UUID="356a5056-4ccb-4014-8b8a-8196012644e2" 
/dev/sda7: UUID="1ea50327-fee6-45a4-b950-15a0e4592597" TYPE="ext3" 
/dev/sda8: UUID="bbd68d58-e7c6-47a3-b24d-e8e2afefd784" TYPE="xfs" 
/dev/sda9: UUID="709F-A194" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
camulus@MIKAC:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=1ea50327-fee6-45a4-b950-15a0e4592597 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=709F-A194              /FAT32            vfat    utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=82c4d455-d158-4ebb-a1b7-021d51afa5d1 /boot           ext3    relatime        0       2
# /dev/sda8
UUID=bbd68d58-e7c6-47a3-b24d-e8e2afefd784 /home           xfs     defaults        0      2
# /dev/sda6
#UUID=b982cda8-79cb-4573-b7ee-43eded3d73ef none            swap    sw              0       0
UUID=356a5056-4ccb-4014-8b8a-8196012644e2 none          swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```Sembla que tot és correcte i tot i això no munta cap de les tres darreres particions:

```
camulus@MIKAC:~$ mount
/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda9 on /FAT32 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda5 on /boot type ext3 (rw,relatime)
/dev/sda8 on /home type xfs (rw)
gvfs-fuse-daemon on /home/camulus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=camulus)

```... que son les que es munten si després de loggejar en consola faig el sudo mount -a. Així que no sé perquè no les munta al principi...¿?

No tinc disk-manager al repositori... saps com aconseguir-lo? De quina third-party?

... i ja tinc una bona copia de seguretat de /home (dev/sda8). Jejeje, gràcies.

Em sambla que acabaré reinstalant i prou...

---

### Post by kimet on 2009-09-21
Disk manager és als repositoris de debian [http://packages.debian.org/lenny/disk-manager]("http://packages.debian.org/lenny/disk-manager") pensaba que podria ser també als d' ubuntu.

Com a última idea, prova de comentar la linia de la partició vfat o posarla al final, no se si l'ordre en que es troben al fstab te cap importancia, pero per si de cas...Pot ser aprendrem alguna cosa nova:)

Salut.

---

### Post by seimulus on 2009-09-21
Doncs el Dsik manager no em troba CAP partició muntable :confused:, tot i que en el mooment que l'he executat estaven totes muntades... no entenc res.
He fet mil i un canvis al fstab i no canvia res de res. Crec que el problema no es el FSTAB sino que el sistema, en l'arrencada no llegeix el fstab i, en consequencia, no munta totes les particions.
No se, no li trobo solució i començo a pensar en una reinstal.lació...

---

### Post by seimulus on 2009-09-22
Ja està arreglat... en certa manera. Passos:

1.- backup de la particio /home a disc extern
2.- formatar la partició /boot, swap i /
3.- instal.lar ubuntu 9.04 en les particions descrites
4.- un cop fet, instalar aquell programari que feia servir abans: kontact, gimp, openoffice, etc etc
5.- un cop tot en marxa, obrir /etc/fstab i afegir /dev/sda8 com a /home

... i llestos! tot funcionant com abans i el sistema més.. depurat, no?+
Gracies per tot

---

### Post by orestesmas on 2009-09-23
> **seimulus said:**
> Bon dia a tothom. Ja fa temps que intento defendre'm amb Ubuntu i fins ara m'ha anat força be. quan he tingut problemes sempre els he solucionat mirant per forums o per internet, pero amb el problema que tinc ara no trobo solucio. Explico:

He tingut un problema amb les locals i els accents. Definint tot com a ca_ES no tinc accents i, en canvi, com a es_ES si. Despres de molt provar i demes, en un dels meus reboots, no em carrega ubuntu i em dona error de "kinit: no resume image". ho soluciono fent #swapoff /dev/sda3 i #mkswap /dev/sda3 i #update-initramfs -u.

Sembla que ja no dona l'error de kinit, pero no arrenca el sistema grafic GDM. Obre una consola demanant login. Si executo GDM no em troba /home

Si executo #mount, no esta muntada /dev/sda8 que es /home. aixi que perque tot funcioni be, he de fer:
- loguejar com a user
$ sudo mount -a
$ sudo gdm
.. i el sistema arrenca normalment.

On est`a l'errada? com ho soluciono per a que arrenqui automaticament? alguna idea? val la pena o millor reinstalar el sistema?
Gracies

No entenc perquè vas refer el disc ram per un simple error de no trobar la imatge de "resume".

Aquest error de "no resume image" indica que en algun moment en lloc de tancar vas hibernar la màquina. Això fa un bolcat de tota la RAM a la partició de swap, per tal de poder arrencar més ràpidament i en l'estat anterior quan tornem a engegar. L'operació té el petit inconvenient de destruir el format original de la partició de swap, però l'inconvenient es soluciona perquè el nucli s'encarrega de restaurar el format abans de reactivar la swap de nou.

Si no et troba la imatge al rearrencar pot ser perquè la mida de la "swap" sigui inferior a la de la RAM i clar, no li cap tota i queda una imatge corrupta. El sistema llavors arrenca normalment.

Això és un problema perquè deixa la swap amb dades que no corresponen al seu format, i falla l'activació de la swap. Cal reformatejar-la, però llavors deu canviar el seu UUID, i has de retocar a mà el /etc/fstab per tal d'arranjar-ho.

Com et deia, no veig perquè cal refer l'initramfs en tot aquest procés (no dic que no hagis fet bé, simplement que jo no ho veig). 

Què tal si proves de refer altra vegada l'initramfs (amb l'opció -c) una vegada tinguis el sistema funcionant normalment, amb totes les particions muntades (a mà)?

Ho dic perquè potser quan vas refer l'initramfs es va copiar allí alguns fitxers desconfigurats.

---

### Post by seimulus on 2009-09-24
```
No entenc perquè vas refer el disc ram per un simple error de no trobar la imatge de "resume".
Aquest error de "no resume image" indica que en algun moment en lloc de tancar vas hibernar la màquina. Això fa un bolcat de tota la RAM a la partició de swap, per tal de poder arrencar més ràpidament i en l'estat anterior quan tornem a engegar. L'operació té el petit inconvenient de destruir el format original de la partició de swap, però l'inconvenient es soluciona perquè el nucli s'encarrega de restaurar el format abans de reactivar la swap de nou.
Si no et troba la imatge al rearrencar pot ser perquè la mida de la "swap" sigui inferior a la de la RAM i clar, no li cap tota i queda una imatge corrupta. El sistema llavors arrenca normalment.
Això és un problema perquè deixa la swap amb dades que no corresponen al seu format, i falla l'activació de la swap. Cal reformatejar-la, però llavors deu canviar el seu UUID, i has de retocar a mà el /etc/fstab per tal d'arranjar-ho.
Com et deia, no veig perquè cal refer l'initramfs en tot aquest procés (no dic que no hagis fet bé, simplement que jo no ho veig). 
Què tal si proves de refer altra vegada l'initramfs (amb l'opció -c) una vegada tinguis el sistema funcionant normalment, amb totes les particions muntades (a mà)?
Ho dic perquè potser quan vas refer l'initramfs es va copiar allí alguns fitxers desconfigurats.     
```Moltíssimes gràcies per l'ajuda, però com pots observar, arriba tard. El perquè vaig fer el que vaig fer és perquè en algún forum ho vaig llegir. es podria dir que no sé ben bé el que feia. Un cop refet el ramdisk no va sortir més l'error però no es muntava cap partició. El millor de tot això és que la teva informació m'ha servit per entendre millor el sistema i saber per on arreglar-ho la propera vegada. 
Gracies.

---

