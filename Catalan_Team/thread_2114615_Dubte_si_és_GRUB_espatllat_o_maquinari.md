---
title: "Dubte si és GRUB espatllat o maquinari"
date: 2013-02-10
forum: Catalan Team
---

### Post by joaquimrubio on 2013-02-10
Torre amb 4 HD muntats: en un disc hi ha el W-7, en un altre W-Xp, en un altre Ubuntu 10.04 LTS i en el darrer Ubuntu 12.04 LTS.

Va cremar-se la font d'alimentació, vaig anar a la botiga, me la van canviar al moment i vaig marxar. A l'arribar a casa, em sembla que no detecta més que 2 HD, el w-7 i l'Ubuntu 10.04.

L'ordre Update grub s'executa però no resol el problema.
El programa Rescatux gravat en un CD s'executa però no resol el problema.

El programeta bootinfoscript (aprés en aquesta consulta: [http://ubuntuforums.org/showthread.php?t=2005431](http://ubuntuforums.org/showthread.php?t=2005431)) em dona aquest results TXT:

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disc /dev/sda: 500.1 GB, 500107862016 octets
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   976,766,975   976,560,128   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disc /dev/sdb: 500.1 GB, 500107862016 octets
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   970,817,535   970,815,488  83 Linux
/dev/sdb2         970,819,582   976,773,119     5,953,538   5 Extended
/dev/sdb5         970,819,584   976,773,119     5,953,536  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        307E14D07E1490A8                       ntfs       Reservado para el sistema
/dev/sda2        6C14168214165006                       ntfs       
/dev/sdb1        b603cb8a-4ad9-40c3-b3a9-12bde3a5b299   ext4       
/dev/sdb5        faa8aa53-9ad4-44c5-9e6c-677f6428c63e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,user_xattr)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
El dubte és: hi ha un error el en GRUB i cal reconfirgurar-lo o simplement, els altres 2 HD es van espatllar quan va fallar la font d'alimentació?

---

### Post by wgarcia on 2013-02-11
Tot apunta a què el sistema sols està reconeixent dos dels discos, identificats amb els dispositiut /dev/sda i /dev/sdb. No crec que sigui un problema del grub.

No necessàriament els discos que no es veuen han d'estar espatllats, també pot estar fallant el controlador dels discos, en el meu parer. 

Una altra possibilitat que se m'acut és que no hagin endollat bé la font d'alimentació als discos que no es veuen.

---

### Post by Miquel Ubuntero on 2013-02-11
> **wgarcia said:**
> Tot apunta a què el sistema sols està reconeixent dos dels discos, identificats amb els dispositiut /dev/sda i /dev/sdb. No crec que sigui un problema del grub.

No necessàriament els discos que no es veuen han d'estar espatllats, també pot estar fallant el controlador dels discos, en el meu parer. 

Una altra possibilitat que se m'acut és que no hagin endollat bé la font d'alimentació als discos que no es veuen.

Estic totalment d'acord amb Garcia, anava a dir quelcom semblant.
Pot ser podríes provar els discs en un altre PC? per verificar-los.
Salutacions,
Miquel.

---

### Post by joaquimrubio on 2013-02-11
Gràcies Miquel i Wgarcia.

Ja buscaré que és el controlador dels discs i ja miraré si obrint la torre sé veure quelcom.

Si tinc dubtes, obriré un altre fil, dono aquest per resolt.

Reitero l'agraiment.

Joaquim

---

