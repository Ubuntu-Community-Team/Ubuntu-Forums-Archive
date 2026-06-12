---
title: "Error al muntar les particions"
date: 2012-11-17
forum: Catalan Team
---

### Post by pserra on 2012-11-17
Hola,
fa uns dies que he hagut de canviar el Disc dur i he instalat el windows i el ubuntu  12.10 juntament amb altres (moltes) particions.El cas es que a /media se'm va instalar només els directoris dels usuaris.
Jo a través de la barra lateral puc accedir a totes les particions, però els altres usuaris els hi demana la contrasenya.
he volgut editar el fitxer fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=46f9b310-c6f1-4005-8093-6291018d124f /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=c9bd1c53-de2d-4433-9f7b-d545f7adf57d /boot           ext2    defaults        0       2
# /home was on /dev/sda11 during installation
UUID=28a607b9-6223-4488-8b57-6b541d9f5fa6 /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=6d050430-3367-4c60-8d9f-5dd01c37d38d none            swap    sw              0       0
[COLOR="DarkRed"]#a partir d'aqui ho he afegit jo....[/COLOR]
UUID=0C182D8E4435290E    media/windows   ntfs-3g auto,rw,users,umask=000 0 0
UUID=4A426FE71B46020F    media/SMALL     ntfs-3g auto,rw,users,umask=000 0 0 
UUID=63CCDED76940C2B5    media/COMPARTIT ntfs-3g auto,rw,users,umask=000 0 0 
UUID=2D955EC90300F4D8    media/DADES     ntfs-3g auto,rw,users,umask=000 0 0
UUID=620C34B2190EF8DC    media/ATOM      ntfs-3g auto,rw,users,umask=000 0 0
UUID=53832F3F1B764DA1    media/PATUFET   ntfs-3g auto,rw,users,umask=000 0 0


primer he posat les adreces /dev/sdax..... i també em donava error.
per donar més informació:
pere@pere-PC:~$ sudo fdisk -l
[sudo] password for pere: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d94b9

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *        2048   163839999    81918976    7  HPFS/NTFS/exFAT
/dev/sda2       184322046   307199999    61438977    5  Estesa
Partition 2 does not start on physical sector boundary.
/dev/sda3       163840000   184319999    10240000    7  HPFS/NTFS/exFAT
/dev/sda4       307200000   625141759   158970880    7  HPFS/NTFS/exFAT
/dev/sda5       184322048   185548610      613281+  83  Linux
/dev/sda6       249708544   307199999    28745728    7  HPFS/NTFS/exFAT
/dev/sda7       206030848   245207039    19588096   83  Linux
/dev/sda8       206001558   206004223        1333    7  HPFS/NTFS/exFAT
Partition 8 does not start on physical sector boundary.
/dev/sda9       245209088   249706495     2248704   82  Intercanvi Linux / Solaris
/dev/sda10      206006272   206028799       11264    7  HPFS/NTFS/exFAT
/dev/sda11      185548800   206001556    10226378+  83  Linux

Les entrades a la taula de particions no estan en l'ordre del disc

i també sudo blkid

pere@pere-PC:~$ sudo blkid
[sudo] password for pere: 
/dev/sda1: LABEL="windows" UUID="0C182D8E4435290E" TYPE="ntfs" 
/dev/sda3: LABEL="SMALL" UUID="4A426FE71B46020F" TYPE="ntfs" 
/dev/sda4: LABEL="COMPARTIT" UUID="63CCDED76940C2B5" TYPE="ntfs" 
/dev/sda5: UUID="c9bd1c53-de2d-4433-9f7b-d545f7adf57d" TYPE="ext2" 
/dev/sda6: LABEL="DADES" UUID="2D955EC90300F4D8" TYPE="ntfs" 
/dev/sda7: UUID="46f9b310-c6f1-4005-8093-6291018d124f" TYPE="ext4" 
/dev/sda8: LABEL="ATOM" UUID="620C34B2190EF8DC" TYPE="ntfs" 
/dev/sda9: UUID="6d050430-3367-4c60-8d9f-5dd01c37d38d" TYPE="swap" 
/dev/sda10: LABEL="PATUFET" UUID="53832F3F1B764DA1" TYPE="ntfs" 
/dev/sda11: UUID="28a607b9-6223-4488-8b57-6b541d9f5fa6" TYPE="ext4" 


L'ERROR EM SURT QUAN CARREGA, PERÒ SI ESCOLLEIXO L'OPCIÓ DE NO ARREGLAR EL PROBLEMA QUAN ENTRO COM ALTRES USUARIS NO TINC CAP PROBLEMA PER ACCEDIR ALS DISCS, UNICAMENT VULL EVITAR CADA VEGADA L'ERROR: NO S'HA POGUT VARREGAR.......

---

### Post by wgarcia on 2012-11-20
M'estranya que tinguis "media/..." al fstab i no "/media/...", però bé, si et funciona...

Crec que demana la contrasenya perquè els usuaris no tenen els mateixos privilegis que tu. els volums estan muntats pel teu usuari que estarà al grup de sudoers i ells nos. Perquè no demani la clau una cosa que pots provar és crear un grup on estiguin tots els teus usuaris, i especificar el número del grup a la línia del fstab amb "gid=<número del grup>".

Compte amb el fstab que és la manera més típica de perdre l'accés al sistema (va ser recordo el meu primer ensurt amb Linux ja fa molts anys, vaig canviar alguna cosa al fstab i després no podia accedir al sistema, encara recordo el meu estómac). Suposo que saps com arreglar-ho si passa amb un CD o USB autònom.

---

### Post by pserra on 2012-11-20
merci wgarcia una altre vegada....
JA ESTA ARREGLAT!! quina coll****a!!... mira que ho vaig estar mirant estona i em semblava que ho tenia bé.........quina badada meva....
respecte a editar malament fstab  també en tinc males experiències.... crec recordar que amb el LiveCd  ho vaig poder arreglar... per sort veig que ara si no carrega la partició t'avisa, però pots engegar igualment....

També he trobat un programet  que he instal·lat ara que es força 'didactic'. Es diu MountManager.... no el coneixia...

---

