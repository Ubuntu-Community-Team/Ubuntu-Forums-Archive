---
title: "compartir  windows-ubuntu"
date: 2007-04-14
forum: Catalan Team
---

### Post by tfabregat on 2007-04-14
Hola,


Fa uns mesos, engrescat per la filosofia Linux, vaig decidir carregar-me Ubuntu. Ho vaig fer amb prudència, sense prescindir del Windows. No en se gaire i tot em resulta prou feixuc. De totes maneres me'n vaig sortir a base d'unes quantes patacades.

Una se les coses que volia mantenir era la possibilitat d'accedir als meus documents des de Windows i Ubuntu indistintament. Pel que havia llegit això era possible.  Després de diversos assajos vaig optar per fer això:

hda1 ntfs per a Windows
hda2 ubuntu 
hda3 FAT32 documents
hda4 fat32 copia de seguretat

Ara, en canvi em trobo que cada cop entro a Ubuntu he de montar de nou la partició  dels Documents via Terminal si vull accedir-hi.

M'ho vaig  mirar del dret i del revès.Vaig consultar el Wiki d'Ubuntu i no m'ha funcionat.
Què cal fer doncs, per aconseguir accedir als meus documents només entrant a Ubuntu, automàticament. 

A veure si algú em pot donar l'empenta final. Gràcies!

---

### Post by lluisanunez on 2007-04-14
Depenent del que digui el teu /etc/fstab, et caldrà modificar o afegir la línia per la partició FAT. Suposant que la partició és hda3, hauria de dir una cosa com:

```
/dev/hda3    /media/windows vfat  iocharset=utf8,umask=000  0    0

```

/media/windows ha d'estar creat prèviament.

---

### Post by tfabregat on 2007-04-14
Hola,


Aquesta és la informació del fstab. Enlloc d'anomenar-lo windows l'hi dic hda3:


/dev/hda3       /media/hda3     vfat    defaults,nls=utf8,umask=0000,gid=46 0       0
/dev/hda4       /media/hda4     vfat    defaults,nls=utf8,umask=0000,gid=46 0       1


Creus que està malament?

Gràcies.

---

### Post by lluisanunez on 2007-04-14
A mi els valors que poses em semblen correctes.  Potser és qüestió de sintaxi (cometes, =, espais...)?

---

### Post by tfabregat on 2007-04-14
Hola,

Em sembla que ensopego sempre amb la mateixa pedra. No va. Mira què em diu:

mount: wrong fs type, bad option, bad superblock on /dev/hda3,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so




D'aquí no passo. Si vull accedir-hi haig de muntar-lo des de l'editor d'ordres cada cop que obro Ubuntu.

Alguna idea?

Gràcies

---

### Post by lluisanunez on 2007-04-14
I des del terminal no et dóna cap error?
Has mirat si a syslog apareix alguna informació útil?
Si manualment funciona, s'ha de poder establir a fstab... però no tinc més idees :confused:

---

### Post by tfabregat on 2007-04-14
Hola Lluïsa,

Ara sí, ho hem aconseguit. Com? Esborrant de nou tot el que es referia a les particions de Windows (Fstab) i he deixat que es faci automàticament, segons les intruccions del wiki d'Ubuntu. Temps enrere ja les havia utilitzat però no havia fet servir l'opció automàtica sinó la manual i em vaig posar de peus a la galleda.

La informació és a: 
[https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28mount%29%7C%28partitions%29](https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28mount%29%7C%28partitions%29)

Gràcies :D :D

---

### Post by lluisanunez on 2007-04-14
Està molt bé aquest wiki :D 

I què diu ara fstab? per curiositat

---

### Post by tfabregat on 2007-04-14
Hola de nou Lluïsa,

Tal com em demanes, aquí tens el text del fitxer :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
/dev/hda1 /media/hda1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hda3 /media/hda3 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hda4 /media/hda4 vfat rw,user,fmask=0111,dmask=0000 0 0

No se interpretar-ho, però s'assembla moltíssim al que tenia. 
M'he decidit a fer-ho així després d'adonar-me que l'autor de les instruccions del Wiki feia molt d'èmfasi en què era un error molt comú i que per arreglar-ho  calia fer net i deixar que es preparés de forma automàtica.

Gràcies,

A reveure,

---

### Post by lluisanunez on 2007-04-14
Hola,
les diferències (que jo veig) són que especifica rw (lectura / escriptura) en comptes de deixar-ho a defaults, i que els drets els estableix amb comandes diferents (user, dmask, fmask en comptes de umask i gid)
També diu que els ha muntat diskmounter, que és un script que et descarregues del mateix wiki. Moltes gràcies per la info. Em va molt bé perquè he recomanat Ubuntu a molta gent i he de poder ajudar-los amb aquests temes (particions, etc) que fan una mica de por :-/

---

