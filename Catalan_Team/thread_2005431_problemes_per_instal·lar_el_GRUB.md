---
title: "problemes per instal·lar el GRUB"
date: 2012-06-17
forum: Catalan Team
---

### Post by joaquimrubio on 2012-06-17
Ordinador de taula amb 4 discs durs,en el HD muntat com a master1 hi ha W-7, en el 2on muntat com a master2 hi ha W-XP, en el tercer disc dur, muntat com a slave 1 hi ha Ubuntu 10.04 LTS,  i en el darrer, muntat com a slave2, afegit darrerament i on ara he acabat d'instal·lar Ubuntu 12.04 LTS.

A l'engegar, comença per W-7.

Abans de muntar el 4art HD, on he instal·lat Ubuntu 12.04, el Grub estava en el W-XP i podia triar el S.O. a l'engegar.

He canviat la BIOS per posar a XP com a primer disc dur, i aleshores carrega el GRUb antic, on puc triar entre els 3 HD inicials, però no hi ha el 4art HD.
Dedueixo que cal esborrar el GRUB antic i escriure'n un de nou que detecti els 4 HD. 

Aleshores, les preguntes són: 

[B]Dec haver de suprimir el GRUB antic. Com ho haig de fer?
Dec haver d'esciure un nou GRUB que detecti els 4 HD. Com ho haig de fer? [/B]

Si enlloc del GRUB es més recomanable un altre gestor d'arrencada, cap problema.

Tinc accés al W-7, W-XP i al Ubuntu 10.04 LTS però no he pogut entrar i acabar de configurar a l'Ubuntu 12.04 LTS, si bé s'ha instal·lat correctament a excepció d'aquest problema del GRUB.

Gràcies i perdoneu tantes preguntes. ;) Espero acabar aviat d'actualitzar-me a 12.04 i no haver de demanar suport fins el 2014...

Joaquim

---

### Post by wgarcia on 2012-06-18
Per intal·lar el grub hi ha les comandes "update-grub" que prepara automàticament els fitxers de configuració i "grub-install <disc>" que instal·la el grub als registres d'arrencada del disc escollit. Ara bé, primer s'hauria de veure com es munten els diferents discos, quins dispositius li assigna el sistema. Per això hi ha una petita utilitat que genera tota la informació necessària, el "bootinfoscript". Mira el comentari #2 al següent fil:

[http://ubuntuforums.org/showthread.php?t=1811334&highlight=boot+info](http://ubuntuforums.org/showthread.php?t=1811334&highlight=boot+info)

i intenta generar i adjuntar el fitxer "RESULTS.TXT" que menciona, això permetrà veure quins dispositius (/dev/sd*) assigna el sistema als discos i on està instal·lat ara el grub.

---

### Post by joaquimrubio on 2012-06-18
Gràcies wgarcia.

El programa el baixo correctament suposo (es diu bootinfoscript-061.tar.gz), i es desa a la carpeta "Baixades".
Al escriure les comandes que dius, no em funciona ni l'una ni l'altra Comandes: "sudo bash~/Baixades/boot_info_script*.sh" i " sudo bash boot_info_script*.sh".
El descomprimeixo en el mateix directori de Baixades, per si fos aquest el problema.
Tampoc em responen les comandes.

Aquesta és la còpia de la consola d'ordres:

joaquim@joaquim-laptop:~$ sudo bash~/Baixades/boot_info_script*.sh
sudo: bash~/Baixades/boot_info_script*.sh: command not found
joaquim@joaquim-laptop:~$ sudo bash boot_info_script*.sh
bash: boot_info_script*.sh: El fitxer o directori no existeix

joaquim@joaquim-laptop:~$ sudo bash~/Baixades/bootinfoscript-061*.sh
sudo: bash~/Baixades/bootinfoscript-061*.sh: command not found
joaquim@joaquim-laptop:~$ sudo bash~/Baixades/bootinfoscript-061.tar.gz*.sh
sudo: bash~/Baixades/bootinfoscript-061.tar.gz*.sh: command not found
joaquim@joaquim-laptop:~

Finalment, com a darrer intent, em canvio al directrori de Baixades per intentar executar des d'allí les comandes, tampoc funciona:

Aquesta és la còpia de la consola d'ordres:

joaquim@joaquim-laptop:~$ cd Baixades
joaquim@joaquim-laptop:~/Baixades$ sudo bash boot_info_script*.sh
bash: boot_info_script*.sh: El fitxer o directori no existeix
joaquim@joaquim-laptop:~/Baixades$ sudo bash ~/Baixades/boot_info_script*.sh
bash: /home/joaquim/Baixades/boot_info_script*.sh: El fitxer o directori no existeix
joaquim@joaquim-laptop:~/Baixades$ 

A la "utilitat de discs" (ruta: Sistema - Administració - Utilitat de discs)hi ha informació de com estan organitzats els discs, no sé  si te interés que ho posi aquí.

---

### Post by wgarcia on 2012-06-19
Si des de la línia de comandes vas al directori "Baixades" i dones l'ordre 

```
ls boot*
```

què surt?

---

### Post by joaquimrubio on 2012-06-19
joaquim@joaquim-laptop:~$ cd Baixades
joaquim@joaquim-laptop:~/Baixades$ ls boot*
bootinfoscript  bootinfoscript-061.tar.gz
joaquim@joaquim-laptop:~/Baixades$ 


Això es el que surt.

Gràcies per la paciència...

---

### Post by joaquimrubio on 2012-06-19
joaquim@joaquim-laptop:~/Baixades$ ls boot*
bootinfoscript-061.tar.gz
joaquim@joaquim-laptop:~/Baixades$ 

Això és el que surt després de suprimir el mateix fitxer, que havia descomprimit. Suposo que sortia duplicat per estar en els 2 formats, comprimit i descomprimit.

---

### Post by wgarcia on 2012-06-20
D'acord, fixa't que un cop descomprimit no hi havia cap fitxer "boot_info_script*.sh", sinó que es diu "bootinfoscript" i per tant "sudo bash boot_info_script*.sh" no funcionava. Ho sento, sembla que les instruccions que et vaig comentar a l'enllaç estaven obsoletes. Ara hauries de tornar a descomprimir el fitxer (tar xzvf bootinfoscript-061.tar.gz) i córrer el programeta amb

```
sudo ./bootinfoscript
```

---

### Post by joaquimrubio on 2012-06-20
Ara sí:

         Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD /grldr

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

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

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdd5: __________________________________________________________________________

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


Drive: sdc _____________________________________________________________________

Disc /dev/sdc: 250.1 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   488,375,999   488,375,937   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disc /dev/sdd: 1000.2 GB, 1000204886016 octets
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048 1,951,449,087 1,951,447,040  83 Linux
/dev/sdd2       1,951,451,134 1,953,523,711     2,072,578   5 Extended
/dev/sdd5       1,951,451,136 1,953,523,711     2,072,576  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        307E14D07E1490A8                       ntfs       Reservado para el sistema
/dev/sda2        6C14168214165006                       ntfs       
/dev/sdb1        b603cb8a-4ad9-40c3-b3a9-12bde3a5b299   ext4       
/dev/sdb5        faa8aa53-9ad4-44c5-9e6c-677f6428c63e   swap       
/dev/sdc1        722C84A92C8469C5                       ntfs       
/dev/sdd1        81a13c53-b251-4ca2-a398-46c7a999e023   ext4       
/dev/sdd5        43f0490f-4726-4f64-92d4-499b93928ca3   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,user_xattr)


=========================== sdb1/boot/grub/grub.cfg: ===========================

---

### Post by wgarcia on 2012-06-20
D'acord, doncs el grub està al MBR (master boot record, registre mestre d'arrencada) del dispositiu /dev/sdc. Per tant es tracta d'actualitzar-lo simplement els fitxers de configuració del grub perquè vegin la nova instal·lació d'Ubuntu 12.04 que has fet, això es fa automàticament amb:

```
sudo update-grub
```

el sistema hauria de trobar i incorporar el nou sistema operatiu al menú d'opcions d'arrencada inicial.

Penso que amb això hi haurà suficient, no fa falta reinstal·lar el grub mateix enlloc sinó simplement actualitzar els fitxers de configuració amb la comanda anterior.

---

### Post by YannBuntu on 2012-06-20
això també pot ajudar:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by joaquimrubio on 2012-06-21
Funciona, he teclejat l'ordre màgica i ja tinc el GRUB arreglat.

Gràcies wgarcia i YannBuntu.

Del tema de l'arrencada em queda un altre problema per resoldre, aquest  equip es va configurar inicialment per a 2 discs durs, en un hi havia  W-XP i en l'altre, Ubuntu, en aquell moment crec que era Hardy Heron.  Per tant, el MBR es va ubicar en el disc on hi havia el W-xp. Després, a  la botiga em van posar un altre disc dur, on hi va anar el W-7 i ara un  altre on hi va el U-12.04. 

Des de que hi ha el w-7, a l'engegar vaig directe a W-7, per evitar-ho haig de prémer F12,  entrar a la BIOS i escollir que comenci pel disc de W-xp, aleshores ja  detecta el grub i a continuació puc escollir quin disc dur vull muntar. Però aquesta  programació no hem queda gravada i a la próxima engegada estic igual. He  buscar quelcom similar a "save & exit" quan sóc a la BIOS per desar els canvis però no  ho trobo. Hi ha alguna manera d'arreglar-ho?

(He dubtat si posar o no aquesta dificultat aquí, si els entesos creieu que és millor començar un altre tema, posaré l'etiqueta de "Solved" en aquest i així ho faré).

---

### Post by wgarcia on 2012-06-22
El tema està ben ubicat, penso, segueixen sent problemes d'instal·lació del grub. 

Per arreglar això últim que dius simplement has de fer:

```
sudo grub-install /dev/sda
```

perquè d'acord amb els resultats del "bootinfoscript" que vas penjar aquest és el disc que dius que comença primer en el teu sistema, a no ser que canviïs l'ordre al BIOS del sistema. 

Això hauria d'instal·lar el grub al registre d'arrencada (MBR) del disc que tens primer al sistema.

---

### Post by joaquimrubio on 2012-06-22
Funciona, s'ha arreglat, em meravella la potència, les possibilitats que ofereix la consola!!!

Moltes gràcies a tots els que m'heu ajudat i en especial a  wgarcia.

Joaquim

---

