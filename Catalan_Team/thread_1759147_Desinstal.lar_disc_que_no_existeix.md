---
title: "Desinstal.lar disc que no existeix"
date: 2011-05-15
forum: Catalan Team
---

### Post by JUSTERINI1 on 2011-05-15
Hola,
Vaig  formatejar un disc portàtil USB des de la configuració NTFS i ja no l'he connectat més al pc, però ara cada vegada que inicio sessió, el sistema intenta muntar la unitat automàticament, i m'informa que no es pot muntar aquest disc, i que ho faci manualment o que ho cancel.li. Veig que aquesta unitat de disc té una icona a la carpeta media. Com ho puc fer per anular-la i que ja mai més em demani de muntar-la?

Gràcies per endavant.

Justerini

---

### Post by wgarcia on 2011-05-15
Potser estigui definit el punt de muntatge al fitxer /etc/fstab i per aixó cada cop que comença el sistema t'ho intenta muntar. 

Per veure que hi ha a aquest arxiu simplement obre una terminal i entra 

cat /etc/fstab

a veure què surt.

---

### Post by JUSTERINI1 on 2011-05-17
Hola Wgarcia, això és el que em surt:
El volum que no haurien d'existir a la carpeta media es diuen: Nuevo Volumen i Sdb5
Com ho haig de treure aquest punt de muntatge?
gràcies per endavant.

jordi@BIG-PORTATIL:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda5 :
UUID=ea51f8dd-39b7-464c-9d70-5898327adfdd    /    ext3    relatime,errors=remount-ro,user_xattr    0    1
#Entry for /dev/sda1 :
UUID=1468505A68503D24    /media/XP    ntfs    defaults,nls=utf8,umask=0222    00
[B]UUID=D014F45F14F449CC    /media/Nuevo\040vol    ntfs-3g    defaults,nosuid,nodev,locale=ca_AD.utf8    0    0
UUID=7AA82C43A82BFBEF    /media/sdb5    ntfs-3g    defaults,locale=ca_AD.utf8    00[/B]
#Entry for /dev/sda6 :
UUID=59fb2c50-61bd-4ec0-8208-449904161c70    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8    0    0

---

### Post by wgarcia on 2011-05-17
Pots fer des d'una terminal

sudo gedit /etc/fstab

i o bé posar-li el caràcter # davant de les dues línies que mencionen els punts de muntatge que no vols per convertir-les en comentaris (en cas que vulguis conservar aquestes línies per si, en algun altre moment vols muntar automàticament aquests discos un altre cop en arrencar l'ordinador), o bé esborrar-les directament si no t'interessen. 

Compte de no tocar res més d'aquest fitxer, un fstab incorrecte és una de les maneres més clàssiques de deixar el sistema inarrencanble, tot i que es pot arreglar fàcilment des d'un CD o USB autònom.

---

### Post by JUSTERINI1 on 2011-05-18
Perfecte, ara funciona correctament, ja no em demana muntar les unitats.
Moltes gràcies Wgarcia, en aquest fòrum sempre hi trobo el que necessito.


Justerini

---

