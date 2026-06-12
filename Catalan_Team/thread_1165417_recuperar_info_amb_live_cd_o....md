---
title: "recuperar info amb live cd o...?"
date: 2009-05-20
forum: Catalan Team
---

### Post by loles on 2009-05-20
hola,

he tingut un problema amb l'actualització de la versio de l'ubuntu, ja he ficat un post abans... 

pero ara la meua progunta es un altra.

he reiniciat amb un livecd per recuperar la info amb la sorpresa que en home... ara no apareix res, i en una particio que tinc si que esta la info

que puc fer per recuperar la informacio que hi havia en home???

amb el livecd no es pot tindre acces a aquestes dades?

gracies

---

### Post by papapep on 2009-05-20
Clar que sí :)

Crees un directori (en aquest exemple li direm "backup")

```
mkdir /home/elteuusuari/backup
```

Ara cal muntar la partició del /home a aquest directori:

```
sudo mount /dev/laParticióOnTensElHome  /home/elteuusuari/backup
```

si ara vas al directori "backup", tindràs el contingut del teu antic /home 

```
cd /home/elteuusuari/backup
```

;)

---

### Post by loles on 2009-05-20
bufff aixo ho veig prou complicat, a vore...

el que no he entes es aixo que hem fiques de
sudo mount /dev/laParticióOnTensElHome  

que he de ficar ahi?

jo ho tenia guardat en home/loles... pense que es alguna cosa així, pots aclarirme açò un poc mes?

moltissimes gracies

---

### Post by papapep on 2009-05-20
Això:

```
sudo mount /dev/laParticióOnTensElHome  /home/elteuusuari/backup
```

significa que has de saber quina partició física és on tens el /home antic. Això ho pots saber obrint l'editor de particions (Sistema > Administració > Editor de particions) i mirant per la mida quina partició és. Si només tens un disc, serà /dev/sdaN, essent N un nombre entre 1 i 4 (normalment). 
Quan sàpigues **segur** quina partició és, executes la ordre que t'he comentat (suposem que la partició és /dev/sda2):

```
sudo mount /dev/sda2 /home/loles/backup
```

si ara entres a /home/loles/backup hauries de trobar tot el teu /home antic.

Pensa que el tema de l'estructura de directoris (/home, /etc, /usr, o el que sigui) només és una convenció que posem els humans per fer-nos més fàcil accedir a les dades. Al disc dur, evidentment :),  li és exactament igual que la partició /dev/sda2 sigui /etc o /home, som nosaltres que les etiquetem per tenir referència del contingut. És com les adreces de les cases. Si el nom del carrer i el nombre de casa teva canviés, seguiria sent casa teva, oi? doncs el cas aquest és el mateix. Ara tindràs el contingut del /home antic dins /home/loles/backup ja que tu li has dit a l'ordinador que el volies allà.

Espero haver-me explicat.

---

### Post by loles on 2009-05-21
he provat aixo que m'has dit, al final he trobat quina particio ho tenia i tot, pero....

al ficar l'ordre em diu que /home/loles no existeix!

q puc fer ara?

si faig aço recuperare totes les dades al home?? i dp q faig? instal·le completament desde un cd live?

mil gracies per la teua ajuda

---

### Post by papapep on 2009-05-21
> al ficar l'ordre em diu que /home/loles no existeix!

Bé, és que has d'adaptar l'ordre al camí real al directori que has creat :)

Mira dins el /home del live CD què hi tens, crea el directori allà i torna a executar l'ordre amb els valors correctes. Suposem que tens /home/livecd/:

Crees el directori:

```
mkdir /home/livecd/backup
```

Ho muntes:

```
sudo mount /dev/laParticióOnTensElHome  /home/livecd/backup
```

I ara ja hi pots accedir:

```
cd /home/livecd/backup
```

Que què fas ara?? doncs el que vulguis! desar les teves dades en cd, passar-les a un pendrive, a un disc dur USB, etc...

I amb això no "recuperes" les dades (de fet, no les havies perdut en cap moment), sinó que hi tens accés per fer el que et plagui amb elles :)

---

### Post by loles on 2009-05-21
be, al final he pogut recuperar gran part de la informanció i he instalat una altra vegada el ubuntu 9

pero ara tinc un problema amb les particions...

he deixat una q ja tenia, q he tingut q modificar l'extensio per un altra, i s'ha tingut q formatejar... pero be, aixo es un altre cantar

resulta q veig q te quan examine l'ordinador sols m'apareix: la unitat del cd, sistema d'arxius no l'altra particio q es diu dades. abans m'apareixia ahi!

pero be, no importa (supose) perque la tinc en media

pero quan seleccine les propietats per veure l'extensio em diu que es de 12GB quan deuria de ser de 35GB!!! q passa aci? 

ho he comprovat en el monitor del sistema i m'apareix la particio sda5 amb 35MB 

q ocorre aci? he fet malament alguna cosa?


aço de ser novata... ho duc molt malament

---

### Post by papapep on 2009-05-21
> aço de ser novata... ho duc molt malament 

Això no és cap problema, tots hi hem passat. Mira-t'ho pel cantó bo, no tens vicis adquirits.. ;)

El que sí que et demanaria, és que intentis redactar d'una manera llegible, tan ortogràficament com sintàctica, ja que es fa difícil entendre el que exposes (parlo explícitament de l´ultim apunt) i trobar què demanes en concret.

TAmbé has de tenir present que nosaltres no som davant el teu ordinador, amb el qual és probable que coses que tu dones per clares, nosaltres no en tinguem ni idea.

Un bon principi, seria llegir, o rellegir si és el cas, el [fil específic per als nouvinguts]("http://ubuntuforums.org/showthread.php?t=599965"), on intentem transmetre una mica com intentem funcionar :)

Respecte tot el que expliques, pots fer a un terminal:

```
sudo fdisk -l
```

i et surtiran un munt de coses semblants a això:

```
jsmesegue@SIST001:~$ sudo fdisk -l

Disc /dev/sda: 250.0 GB, 250000000000 octets
255 heads, 63 sectors/track, 30394 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8a74311

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1               1          11       88326    6  FAT16
/dev/sda2           27845       30394    20482875    7  HPFS/NTFS
/dev/sda3   *          12          35      192780   83  Linux
/dev/sda4              36       27844   223375792+   5  Estesa
/dev/sda5           27488       27844     2867571   82  Intercanvi Linux / Solaris
/dev/sda6              36        3658    29101684+  83  Linux
/dev/sda7            3659       27487   191406411   fd  Autodetecció RAID Linux

Les entrades a la taula de particions no estan en l'ordre del disc

Disc /dev/sdb: 250.0 GB, 250000000000 octets
255 heads, 63 sectors/track, 30394 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8a74311

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1               1       23829   191406411   fd  Autodetecció RAID Linux
/dev/sdb2           23830       30394    52733362+  83  Linux

Disc /dev/md0: 196.0 GB, 196000088064 octets
2 heads, 4 sectors/track, 47851584 cylinders
Units = cilindres of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

```

Enganxa el que et surti aquí al fòrum, i comencarem a fer-nos una idea del que tens al disc, i com ho tens organitzat.
;)

---

### Post by loles on 2009-05-21
açò és el que m'apareix:

Disc /dev/sda: 60.0 GB, 60011642880 octets
255 heads, 63 sectors/track, 7296 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56805680

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda2   *           1        7295    58597056    f  W95 Estesa (LBA)
/dev/sda5            2611        7295    37632231   83  Linux
/dev/sda6               1        2488    19984765+  83  Linux
/dev/sda7            2489        2610      979933+  82  Intercanvi Linux / Solaris

Les entrades a la taula de particions no estan en l'ordre del disc
loles@loles-laptop:~$

---

### Post by papapep on 2009-05-21
D'aquestes:

> /dev/sda5 2611 7295 37632231 83 Linux
/dev/sda6 1 2488 19984765+ 83 Linux

Quina és el teu antic /home?

---

### Post by loles on 2009-05-21
el meu antic home era el nº6 i l'altra partició la 5

---

### Post by papapep on 2009-05-21
I la que anomenes "dades", quina és?

---

### Post by loles on 2009-05-21
la que anomene dades, que es l'altra particio es la 5

---

### Post by papapep on 2009-05-21
Fes un:

```
df -h
```

i un:

```
cat /etc/fstab
```

a veure què surt.

---

### Post by loles on 2009-05-22
en la primera  ordre que m'has ficat em posa:
loles@loles-laptop:~$ df -h
^[[6~S. fitxers            Mida En ús Lliure %Ús Muntat a
/dev/sda6              19G  6,6G   12G  37% /
tmpfs                 498M     0  498M   0% /lib/init/rw
varrun                498M  104K  498M   1% /var/run
varlock               498M     0  498M   0% /var/lock
udev                  498M  152K  498M   1% /dev
tmpfs                 498M   76K  498M   1% /dev/shm
lrm                   498M  2,4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda5              36G  874M   33G   3% /home

i en la segona ordre em diu command not found

---

### Post by papapep on 2009-05-22
Fixa't que aquí surt correctament el teu /home, amb una mida de 36GB, dels quals tens ocupats 874 MB:

```
fitxers Mida En ús Lliure %Ús Muntat a
/dev/sda6 19G 6,6G 12G 37% /
tmpfs 498M 0 498M 0% /lib/init/rw
varrun 498M 104K 498M 1% /var/run
varlock 498M 0 498M 0% /var/lock
udev 498M 152K 498M 1% /dev
tmpfs 498M 76K 498M 1% /dev/shm
lrm 498M 2,4M 495M 1% /lib/modules/2.6.28-11-generic/volatile
**/dev/sda5 [COLOR="Red"]36G[/COLOR] 874M 33G 3% /home**
```

> i en la segona ordre em diu command not found 

Copia i enganxa la ordre directament del fòrum, que és impossible que no trobi la ordre "cat". Ha de ser un error al picar-la.

---

### Post by loles on 2009-05-22
val, ara si, no se que ficava!!

loles@loles-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=c3972aa7-feb0-4f36-9fb2-a8f4bc814e26 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=418bf0c5-654c-481e-b8fc-d6825348af52 /home           ext3    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=02eeb089-d697-404c-8a39-5357538efe51 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
loles@loles-laptop:~$

---

### Post by papapep on 2009-05-22
Bé, companya, doncs fins on jo veig tot és bastant normal...no veig res fora de lloc. :)

Ja diràs si alguna cosa no et quadra, però tot és prou coherent.

---

### Post by loles on 2009-05-22
a vore, vaig a explicar-me una altra vegada...

resulta, que la partició aquesta, DADES, jo ara la tinc al meu ordinador en /media i quan fique a les propietats d'aquesta carpeta m'apareix que hi ha un espai lliure de 11,3GB quan hauria de ser de 35!!

Aleshores, ahi és la meua qüestió preocupació

---

### Post by papapep on 2009-05-22
No tens cap partició /media/DADES muntada, com pots verificar al /etc/fstab.. 

El que dius del /media/DADES ho veus executant l'Ubuntu del disc dur, o des d'un live-cd???

---

### Post by loles on 2009-05-22
ho veig des del disc dur, es que pense que igual no vaig fer be la partició! o no se que és el que ha pogut passar!!!

---

### Post by PatrickVogeli on 2009-05-23
el que et pasa es que deus haver creat la particio /media/dades pero no esta muntada ni res... llavors quan pitjes propietats, veus l'espai lliure de l'arrel /.

Pot ser aixo?

---

### Post by loles on 2009-05-25
mmm...

Doncs no ho sé. Però podria ser-ho. Com puc fer per a muntar-la?

---

### Post by papapep on 2009-05-25
Segons les teves pròpies dades:

> 
loles@loles-laptop:~$sudo fdisk -l
Disc /dev/sda: 60.0 GB, 60011642880 octets
255 heads, 63 sectors/track, 7296 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56805680

Dispositiu Arrenc. Inici Final Blocs Id Sistema
/dev/sda2 * 1 7295 58597056 f W95 Estesa (LBA)
[COLOR="SeaGreen"]/dev/sda5 2611 7295 37632231 83 Linux[/COLOR]
[COLOR="Blue"]/dev/sda6 1 2488 19984765+ 83 Linux[/COLOR]
/dev/sda7 2489 2610 979933+ 82 Intercanvi Linux / Solaris

Les entrades a la taula de particions no estan en l'ordre del disc


Amb el qual, en aquest disc només tens quatre particions. Una que deu tenir un antic windows, les dues de Linux i la d'intercanvi, de les que:

> loles@loles-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
[COLOR="Blue"]# / was on /dev/sda6 during installation
UUID=c3972aa7-feb0-4f36-9fb2-a8f4bc814e26 / ext3 relatime,errors=remount-ro 0 1[/COLOR]
[COLOR="SeaGreen"]# /home was on /dev/sda5 during installation
UUID=418bf0c5-654c-481e-b8fc-d6825348af52 /home ext3 relatime 0 2[/COLOR]
# swap was on /dev/sda7 during installation
UUID=02eeb089-d697-404c-8a39-5357538efe51 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

/dev/sda5 és el teu home actual, i /dev/sda6 és la partició arrel (root). 

Aquestes particions, estan de la següent manera:

> loles@loles-laptop:~$ df -h
^[[6~S. fitxers Mida En ús Lliure %Ús Muntat a
[COLOR="Blue"]/dev/sda6 19G 6,6G 12G 37% /[/COLOR]
tmpfs 498M 0 498M 0% /lib/init/rw
varrun 498M 104K 498M 1% /var/run
varlock 498M 0 498M 0% /var/lock
udev 498M 152K 498M 1% /dev
tmpfs 498M 76K 498M 1% /dev/shm
lrm 498M 2,4M 495M 1% /lib/modules/2.6.28-11-generic/volatile
[COLOR="SeaGreen"]/dev/sda5 36G 874M 33G 3% /home[/COLOR]


Amb el qual, o tens algun disc dur extern que és on veus el teu /media/DADES, o has fet algun batibull al moment de particionar i reinstal·lar que no podem veure, però seria molt estrany no veure-ho en tot això que ja has arribat a posar...

Tens algun disc dur més, a banda de l'intern de l'ordinador??

---

### Post by loles on 2009-05-25
BUFFF...

pense que ho deixaré com està i prou! o més endavant... tornaré a instal·lar-ho!

moltes gràcies xic!

---

