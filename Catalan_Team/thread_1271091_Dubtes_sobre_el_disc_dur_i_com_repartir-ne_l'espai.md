---
title: "Dubtes sobre el disc dur i com repartir-ne l'espai"
date: 2009-09-20
forum: Catalan Team
---

### Post by xavix2005 on 2009-09-20
Gràcies pels suggeriments, he arregalt algunes configuracions de xarxa i ara ja puc rebre les actualitzacions! Ara tins però un altre problema, de manca d'espai: un cop rebudes les actualitzacions, no les puc instal.lar perquè em surt el missatge:

No disposeu de suficient espai al disc

L'actualització requereix 416M d'espai lliure al disc «/». Hauríeu d'alliberar almenys 416M d'espai de disc a «/». Buideu la vostra paperera i esborreu els paquets temporals utilitzant «sudo apt-get clean».

El dubte és com localitzar aquest disc / i ampliar-lo, de moment no me'n surto...

---

### Post by SiscoGarcia on 2009-09-20
> **xavix2005 said:**
> El dubte és com localitzar aquest disc / i ampliar-lo, de moment no me'n surto...

Em sembla que hauries de fer una petita revisió del sistema de fitxers a GMU/Linux; resulta que la barra inclinada (/) indica l'arrel del sistema de fitxers, per tant és on hi diu ordinador>sistema de fitxers. El que vol dir és que no hi ha prou espai al disc (si més no a la partició arrel) per instal·lar-hi les actualitzacions. El que has de fer és alliberar espai al disc dur.

Per tal d'ajudar-te millor ens hauries d'explicar com tens el teu disc dur. Quines particions tens? Com les tens dimensionades?... etc.

---

### Post by xavix2005 on 2009-09-20
Bona nit i gràcies per avançat, cal dir que sóc totalment neòfit en Ubuntu i Linux. Pel que he pogut veure, tinc:

- sistema de fitxers de 2,3 GB al directori /
- un disc anomenat Suport 3 GB, amb 2,8 GB reals i ext3 i ext4
- Un disc anomenat Suport 33,8 GB amb 31 GB reals ext 3 i ext 4

El problema deu venir pel sistema de fitxers, que està gairebé ple (77 MB lliures), però no ser com cambiar les dimensions del sistema per adequar-lo. El KDE que he pogut activar em diu que no tinc permisos i no sembla detectar cap partició.

---

### Post by papapep on 2009-09-20
Cap problema. Mira, per tenir prou informació, fes a un terminal:

```
sudo fdisk -l
```
veurem quines particions tens definides i quants discs durs físics

i

```
df -h
```
veurem els punts de muntatge i la seva ocupació

i 

```
cat /etc/fstab
```

Copia el resultat de tot plegat, i enganxa-ho aquí, si us plau.

---

### Post by xavix2005 on 2009-09-21
Bé, aquestes són les respostes obtingudes, per a mi gairebé inintel.ligibles. Us agraeixo molt la col.laboració, suposo que poc a poc se'n va aprenent!



Disc /dev/sda: 40.0 GB, 40020664320 octets 
 255 heads, 63 sectors/track, 4865 cylinders 
 Units = cilindres of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0x0d030d02 
  
 Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema 
 /dev/sda1   *           1         365     2931831   83  Linux 
 /dev/sda2             366        4865    36146250    5  Estesa 
 /dev/sda5             366         426      489951   82  Intercanvi Linux / Solaris 
 /dev/sda6             427        4539    33037641   83  Linux 
 /dev/sda7            4540        4843     2441848+  83  Linux 
 /dev/sda8            4844        4865      176683+  82  Intercanvi Linux / Solaris 
 

 

 S. fitxers            Mida En ús Lliure %Ús Muntat a 
 /dev/sda7             2,3G  2,2G   34M  99% / 
 tmpfs                 123M     0  123M   0% /lib/init/rw 
 varrun                123M  104K  123M   1% /var/run 
 varlock               123M     0  123M   0% /var/lock 
 udev                  123M  156K  123M   1% /dev 
 tmpfs                 123M   76K  123M   1% /dev/shm 
 lrm                   123M  2,4M  121M   2% /lib/modules/2.6.28-11-generic/volatile
 

 

 # /etc/fstab: static file system information. 
 # 
 # Use 'vol_id --uuid' to print the universally unique identifier for a 
 # device; this may be used with UUID= as a more robust way to name devices 
 # that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    defaults        0       0 
 # / was on /dev/sda7 during installation 
 UUID=c2a14e72-36d8-45c3-9b3a-6b2413a87e63 /               ext3    relatime,errors=remount-ro 0       1 
 # swap was on /dev/sda8 during installation 
 UUID=94c99488-571f-48ea-9ed1-0b84fbc6a844 none            swap    sw              0       0 
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Diegstroyer on 2009-09-21
Utilitza un LiveCD, no pots redimensionar les particions muntades.

Un cop en el LiveCD, ves a Sistema-->Administració-->Gestor de particions.

Des d'allà podràs redimensionar o fer el que vulguis amb les particions del sistema.

Salutacions.

---

### Post by oriolsbd on 2009-09-22
Xavi, has fet més d'una instal·lació d'Ubuntu? O d'alguna altra distribució de GNU/Linux?

Segons el resultat del "df -h", tens muntat al directori "/" la partició "/dev/sda7", que només té 2,3Gb. I res més. En canvi, en l'arbre de particions mostrat pel "fdisk -l" hi ha moltes altres particions de Linux (que realment no estàs utilitzant). Fins i tot hi ha dues particions de Swap. Realment, 2,3Gb és molt poc, i és normal que se't queixi.

És possible que instal·lessis Ubuntu un cop i, per algun motiu (algun error, per exemple), tornessis a instal·lar-lo. En aquesta segona instal·lació, a l'hora d'indicar-li on instal·lar Ubuntu, en comptes de dir-li que t'utilitzés tot el disc, li devies dir que t'agafés un espai al final, i realment és insuficient.

_Si és aquest el cas_, jo et recomanaria que tornis a instal·lar Ubuntu i, quan demana quina part del disc utilitzar, que l'agafi tot (o fer un particionament manual personalitzat). Sobretot, abans de fer-ho, has de guardar-te còpia de tots els fitxers importants.

Salut!

---

### Post by orestesmas on 2009-09-23
> **Diegstroyer said:**
> 
Un cop en el LiveCD, ves a Sistema-->Administració-->Gestor de particions.
Des d'allà podràs redimensionar o fer el que vulguis amb les particions del sistema.
Salutacions.

Permeteu-me un incís: Tècnicament és possible redimensionar una partició, però en cap cas es pot fer alegrement, si no vols arriscar-te a perdre dades. Desconec si el gestor de particions del LiveCD (que deu ser el GParted) és prou intel·ligent com per redimensionar particions ext3 (o ext4) sense perdre dades, perquè per "allargar" una partició primer cal reduir-ne una altra de veïna per fer-li espai. Si la partició que cal reduir és buida i s'ubica **després**, es pot esborrar i ja està, però sovint et trobes que no és buida i cal reduir-la desplaçant l'inici (que és on hi ha dades) i no el final (que acostuma a estar buit), i això implica que cal primer desplaçar les dades, etc. Un maldecap.

Tot això només es pot fer de forma natural si els discs estan configurats amb LVM. Qualsevol altra cosa o no funciona o són invents estranys que més val oblidar. És preferible reinstal·lar de nou formatejant i reparticionant millor.

En fi, no sé si m'he explicat: O en saps una mica, o no remenis les particions. És preferible reinstal·lar perquè, total, segurament hauràs d'acabar-ho fent igualment després d'haver deixat el sistema inusable.

Jo provaria primer coses molt més simples per fer una mica d'espai. Segurament deus tenir el directori /var/cache/apt/archives ple dels paquets que t'has anat baixant abans d'instal·lar-los. Pots purgar el contingut d'aquest directori amb:
```

sudo apt-get clean

```

Això et pot alliberar un espai notable (ho pots saber fent "df -h" abans i després de l'ordre aquesta). Després d'haver-ho fet, prova d'actualitzar a veure si funciona.

---

