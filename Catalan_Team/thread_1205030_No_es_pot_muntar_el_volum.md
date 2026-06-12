---
title: "No es pot muntar el volum"
date: 2009-07-05
forum: Catalan Team
---

### Post by anikuni_69 on 2009-07-05
Aquest és el problema: tenia ubuntu instal·lat en una partició, hi ha haver un error amb una actualització i ubuntu va deixar de carregar-se. Posteriorment vaig reinstal·lar ubuntu en una altra partició que tenia lliure. Ara quan intento accedir a la partició on es va malmetre ubuntu per tal de recuperar els arxius, surt el següent error:

No es pot muntar el volum.
mount:wrong fs type, bad option, bad superblock on / dev/sda3, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so


potser també us serveix això:


chiara@chiara-laptop:~$ sudo fdisk -l
[sudo] password for chiara:

Disc /dev/sda: 250.0 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae50b7e1

Dispositiu Arrenc. Inici Final Blocs Id Sistema
/dev/sda1 * 1 10697 85922628+ 7 HPFS/NTFS
/dev/sda2 10698 12074 11060752+ 7 HPFS/NTFS
[COLOR=Red]/dev/sda3 12075 25093 104575117+ 83 Linux[/COLOR]
/dev/sda4 25094 30402 42639061 83 Linux
chiara@chiara-laptop:~$


La que està en vermell és la que no puc obrir. Pot ser simplement que la partició estigui malmesa? Aleshores hi hauria alguna manera de recuperar els arxius?

Quan accedeixo a Windows, on tinc instal·lat el Partition Manager, aquest programa reconeix la partició i reconeix quant d'espai se n'està fent servir (uns 10 Gb)

(perdona papapep per no haver tancat abans l'altre fil..)

---

### Post by papapep on 2009-07-05
Ensenya'ns què tens dins el fitxer /etc/fstab:

```
less /etc/fstab
```

---

### Post by anikuni_69 on 2009-07-05
Això és el que hi ha:



# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=5fad0aee-c058-4f7c-a376-92cc378a9b4c /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by papapep on 2009-07-05
El que jo faria és el següent:

1.- Fer una còpia de seguretat de l'fstab:

```
sudo cp /etc/fstab /etc/fstab.backup
```

Fet això, editar-lo.

```
sudo nano /etc/fstab
```

I provaria a deixar-lo així (que només quedi el text que et poso):

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda4 during installation
/dev/sda3 / ext3 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0 
```

Tant si arrenca correctament, com si no, hauràs de fer algunes proves més, però a veure si adelantem alguna cosa amb això.

---

### Post by anikuni_69 on 2009-07-05
Doncs no sé si haurem avançat... he fet el que m'has dit i la partició ha desaparegut de la llista de llocs. Però has dit que hauria de fer més proves, ara què?

---

### Post by papapep on 2009-07-05
Què vols dir amb "la llista de llocs"??
Ha arrencat correctament l'ordinador, o no? no entenc el que ha passat... recorda que nosaltres no som davant el teu ordinador.

Per cert, com estàs accedint a aquestes particions, i a modificar els fitxers???

---

### Post by anikuni_69 on 2009-07-05
L'ordinador ha arrancat correctament.
Amb la llista de llocs em refereixo al menú inicial (Aplicacions, Llocs, Sistema)
Dins de la pestanya Llocs, abans entre altres coses (és a dir Carpeta inici, Escriptori, Documents, etc..) hi havia Ordinador, Suport 88 Gb (Windows), Suport 107 Gb (el que no funciona)

Ara, despres d'haver fet això, no hi ha la partició de 107 Gb, l'ubuntu ja no la reconeix. (suposo)

Pel que fa a com modifico els fitxers entro a la terminal i poso els codis que m'has escrit.

---

### Post by oriolsbd on 2009-07-05
Amb les línies que t'ha indicat el Papapep, en principi ja tens muntada a "/" la partició que tu volies (la /dev/sda3). És a dir, si busques per l'arbre de directoris, hauries de trobar tots els fitxers que havies perdut en els mateixos directoris on eren abans.

Salut!

---

### Post by anikuni_69 on 2009-07-06
Ho he buscat i no hi és. Dintre la carpeta /dev no hi ha /sda3.
Quina informació us puc donar per ajudar a ajudar-me?
El que he fet aquesta vegada és entrar a la carpeta Ordinador, comprovar que la partició no apareix en aquesta carpeta, després entrar a Sistema de Fitxers/dev i allà buscar la carpeta sda3, que no hi és.

---

### Post by papapep on 2009-07-06
A veure, anikuni. Tal i com t'ha comentat l'oriolsbd, si el que tu ens indicaves abans era correcte, la partició /dev/sda3 és la que estàs fent servir en arrencar l'ubuntu. 

Si fas un:

```
ls -la /dev |grep sd[a-z][0-9]
```

no et surt sda3?

Fent:

```
less /etc/mtab
```

veuràs quines particions tens muntades i podrem intentar entendre alguna cosa.

---

### Post by anikuni_69 on 2009-07-06
Demano molt perdó i comprensió si m'explico fatal... de moment no en sé més...


Aquí es veuen les particions que tinc:


Disc /dev/sda: 250.0 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae50b7e1

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       10697    85922628+   7  HPFS/NTFS
/dev/sda2           10698       12074    11060752+   7  HPFS/NTFS
/dev/sda3           12075       25093   104575117+  83  Linux
/dev/sda4           25094       30402    42639061   83  Linux
chiara@chiara-laptop:~$ 


Jo a l'inici vaig instal·lar ubuntu a la partició sda3, però aquesta és la que va petar, i posteriorment vaig instal·lar ubuntu a la partició sda4, que és la que estic fent servir ara. El meu problema és accedir a sda3 per a recuperar els arxius. Al principi d'aquest fil, jo accedia al menú principal d'ubuntu: Llocs/ i podia visualitzar:

Ordinador (sda4 que estic utilitzant)
Suport 88Gb (NTFS Windows)
Suport 107Gb (sda3 ubuntu petat, que a l'intentar muntar el volum em donava l'esrror *mount:wrong fs type, bad option, bad superblock on / dev/sda3, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so*)

Després de seguir les instruccions el Suport 107Gb va desarèixer.

Aquesta és la informació que em demanes: less /etc/mtab

/dev/sda3 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-13-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/chiara/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=chiara 0 0


Us estic dient alguna cosa que no sigui possible? He de recuperar el fitxer fstab.backup i deixar fstab tal com estava?

---

### Post by papapep on 2009-07-06
Bé. Segons el que acabes d'enganxar:

En aquests moments no estàs treballant amb l'ubuntu que dius que has instal·lat a /dev/sda4, sinó al que tenies originàriament a /dev/sda3:

> Aquesta és la informació que em demanes: less /etc/mtab

**[COLOR="Red"]/dev/sda3 /[/COLOR]** ext3 rw,relatime,errors=remount-ro 0 0

I, evidentment, no et surt /dev/sda3 a *Llocs*, per que és el teu sistema de fitxers principal (el que estàs fent servir en aquests moments per a fer anar l'ordinador).
Així doncs, com ja t'havia comentat abans l'oriol, a no ser que vulguis seguir treballant amb l'instal·lació que has fet a /dev/sda4, ja tens els fitxers recuperats! mira als directoris on tenies l'informació abans de que et petés, hauria de ser allà...i si no és així, no entenc res :)

---

### Post by anikuni_69 on 2009-07-06
Ostres doncs ara sí que no entenc res jo tampoc!!! ....... començo a desesperar-me.
Entenc el que em dius, té tota la lògica del món, però els fitxers no hi són! A més a més, la capacitat del sistema de fitxers amb el qual estic treballant és de 40Gb (sda4 oi??) perquè sda3 té 107Gb!!! que és la que va desaparèixer després de canviar fstab.

i si provo de tornar fstab com estava? perquè ara aquells 107 Gb de disc dur és com si no hi fossin...

alguna idea?...

---

### Post by papapep on 2009-07-06
> A més a més, la capacitat del sistema de fitxers amb el qual estic treballant és de 40Gb

D'on ho treus això? ensenyan's-ho.

Més fàcil, fes:

```
df -h
```

---

### Post by anikuni_69 on 2009-07-06
He obert l'analitzador de l'ús dels discs, he escanejat el Sistema de Fitxers, i aquest és el resultat de l'encapçalament.

*Capacitat total del Sistema de fitxers: 40,0Gb (utilitzat 3,0Gb  disponible 37,0Gb)*

Hi ha alguna manera de mirar aquesta informació a la terminal per a poder-t'ho posar exacte?

---

### Post by anikuni_69 on 2009-07-06
perdó

S. fitxers            Mida En ús Lliure %Ús Muntat a
/dev/sda3              41G  3,1G   35G   8% /
tmpfs                 1,5G     0  1,5G   0% /lib/init/rw
varrun                1,5G  108K  1,5G   1% /var/run
varlock               1,5G     0  1,5G   0% /var/lock
udev                  1,5G  184K  1,5G   1% /dev
tmpfs                 1,5G   76K  1,5G   1% /dev/shm
lrm                   1,5G  2,2M  1,5G   1% /lib/modules/2.6.28-13-generic/volatile

---

### Post by papapep on 2009-07-06
Torna a fer un:

```
sudo fdisk -l
```

un:

```
less /etc/fstab
```

un:

```
ls -la /dev/disk/by-uuid/
```

i un:

```
ls -la /dev |grep sd[a-z][0-9]
```

---

### Post by anikuni_69 on 2009-07-06
**sudo fdisk -l**

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       10697    85922628+   7  HPFS/NTFS
/dev/sda2           10698       12074    11060752+   7  HPFS/NTFS
/dev/sda3           12075       25093   104575117+  83  Linux
/dev/sda4           25094       30402    42639061   83  Linux


**less /etc/fstab**


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda4 during installation
/dev/sda3 / ext3 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/etc/fstab (END) 



**ls -la /dev/disk/by-uuid**


total 0
drwxr-xr-x 2 root root 120 2009-07-06 18:42 .
drwxr-xr-x 6 root root 120 2009-07-06 18:42 ..
lrwxrwxrwx 1 root root  10 2009-07-06 18:42 3fb5167e-238f-4fd4-a2a5-d25f2dba66c7 -> ../../sda3
lrwxrwxrwx 1 root root  10 2009-07-06 18:42 4647951E62A3F86D -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-07-06 18:42 5fad0aee-c058-4f7c-a376-92cc378a9b4c -> ../../sda4
lrwxrwxrwx 1 root root  10 2009-07-06 18:42 CA3C557B3C55640B -> ../../sda2

[B]
ls -la /dev |grep sd[a-z] [0-9][/B]


brw-rw----   1 root   disk      8,   1 2009-07-06 18:42 sda1
brw-rw----   1 root   disk      8,   2 2009-07-06 18:42 sda2
brw-rw----   1 root   disk      8,   3 2009-07-06 18:42 sda3
brw-rw----   1 root   disk      8,   4 2009-07-06 18:42 sda4

---

### Post by papapep on 2009-07-06
No ho entenc....

La partició /dev/sda3, l'fdisk diu que té 100 i escaig gigues:

/dev/sda3 12075 25093 104575117+ 83 Linux

Però, en canvi, un df- h, diu que només en té 40 i escaig:

/dev/sda3 41G 3,1G 35G 8% /

Fem una cosa, canvi l'fstab per l'UUID de /dev/sda3. Deixa'l així:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=3fb5167e-238f-4fd4-a2a5-d25f2dba66c7 / ext3 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

A veure si així munta correctament la partició de 100 gigues. Tot i això, on haurien de ser (a quin directori) els fitxers que dius que no apareixen??

---

### Post by sianeu on 2009-07-07
A la resolució del problema no se pas ajudar. Peró, per recuperar els fitxers, has provat des del cd-rom d'ubuntu (provar sense instal·lar) a navegar fins on els tenies?

Salut

---

### Post by anikuni_69 on 2009-07-07
A veure, primer he provat el cosell d'arrancar des del cd d'instal·lació d'ubuntu i entrar amb l'opció "prova ubuntu sense instal·lar", i la cosa estava igual que al principi, el mateix error:

[quote=anikuni_69

Al principi d'aquest fil, jo accedia al menú principal d'ubuntu: Llocs/ i podia visualitzar:

Ordinador (sda4 que estic utilitzant)
Suport 88Gb (NTFS Windows)
Suport 107Gb (sda3 ubuntu petat, que a l'intentar muntar el volum em donava l'esrror *mount:wrong fs type, bad option, bad superblock on / dev/sda3, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so*)

Després de seguir les instruccions el Suport 107Gb va desarèixer.

[/quote]


Al veure que d'aquesta manera tampoc no podia accedir al volum 107Gb, he seguit les instruccions de papapep. L'ordinador ha arrancat correctament, però no hi ha cap canvi visible.

Deixo aquí informació actual, que no sé si serveix...

**sudo fdisk -l**

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       10697    85922628+   7  HPFS/NTFS
/dev/sda2           10698       12074    11060752+   7  HPFS/NTFS
/dev/sda3           12075       25093   104575117+  83  Linux
/dev/sda4           25094       30402    42639061   83  Linux


**less etc/fstab**

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=3fb5167e-238f-4fd4-a2a5-d25f2dba66c7 / ext3 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0


[B]ls -la /dev/disk/by-uuid

[/B]total 0
drwxr-xr-x 2 root root 120 2009-07-07 19:28 .
drwxr-xr-x 6 root root 120 2009-07-07 19:28 ..
lrwxrwxrwx 1 root root  10 2009-07-07 19:28 3fb5167e-238f-4fd4-a2a5-d25f2dba66c7 -> ../../sda3
lrwxrwxrwx 1 root root  10 2009-07-07 19:28 4647951E62A3F86D -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-07-07 19:28 5fad0aee-c058-4f7c-a376-92cc378a9b4c -> ../../sda4
lrwxrwxrwx 1 root root  10 2009-07-07 19:28 CA3C557B3C55640B -> ../../sda2


[B]ls -la /dev |grep sd[a-z][0-9]


[/B]brw-rw----   1 root   disk      8,   1 2009-07-07 19:28 sda1
brw-rw----   1 root   disk      8,   2 2009-07-07 19:28 sda2
brw-rw----   1 root   disk      8,   3 2009-07-07 19:28 sda3
brw-rw----   1 root   disk      8,   4 2009-07-07 19:28 sda4

---

### Post by papapep on 2009-07-08
Sembla que en algun moment que has modificat particions (crear, eliminar o redimensionar) alguna cosa no ha quedat fina del tot. Et deu fer falta redimensionar el sistema de fitxers. El que no tinc clar és què passa amb els fitxers que dius que vols recuperar. No tinc clar, bàsicament per què no sé què has fet abans de començar aquest fil, com recuperar-los, si ni amb un CD viu hi pots accedir...

Si són fitxers vitals per a tu, en aquests moments no sé com fer-ho per que el que provaria no sé si provocarà que no els puguis recuperar definitivament. Si no són tan importants, podem intentar redimensionar el sistema de fitxers, per que s'assabenti d'un cop que la mida de la partició no és la que ell es pensa, que sembla que sigui el problema.

---

### Post by anikuni_69 on 2009-07-08
Els fitxers que realment són molt molt importants, els tinc gravats en un cd. Els que volia recuperar són uns que em sabria molt greu perdre, però ja me'n vaig fent a la idea.

Redimensionant el sistema de fitxers és gairebé segur que s'esborraran oi? O hi ha alguna possibilitat que no passi? Si hi ha aquesta possibilitat, provem-ho.

En cas que perdre els documents sigui inevitable, ja posats m'agradaria que ubuntu quedés instal·lat a sda4 per així poder utilitzar sda3 per a guardar-hi els documents (després de formatejar-la i deixar-la nova) És possible? O és una tonteria?

---

