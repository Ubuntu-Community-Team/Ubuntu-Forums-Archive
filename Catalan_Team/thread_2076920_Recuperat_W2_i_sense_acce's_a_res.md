---
title: "Recuperat W2 i sense acce's a res"
date: 2012-10-27
forum: Catalan Team
---

### Post by jinglada on 2012-10-27
Benvolgut/d@s ajudant@s:

Al meu Packard Bell Easynote MT85-M-005SP, Intel Core 2 Duo P8400 2.26 GHz, Ram 4 Gb DDR2, ATI HD3650 512 MB, Hard Drive 320 GB, amb el 12.04 Precise Pangolin, vaig intentar entrar al Windows Vista perque' necessitava quelcom de W. que ara no recordo. Era la primera vegada que hi entrava despr'es de l'actualitzaci'o al 12.04. I no hi vaig poder entrar i em va suggerir el recovery. Al final va acabar reinstal.lant el W2 i quan va reiniciar ja no va entrar res ni el W2, ni el grub. 

"Sortosament" des de la pantalla d'inici, que va repetint sense parar, he pogut accedir al menu' de boot per indicar-li que arranque's des de CD i amb el disc d'Ubuntu he arribat fins aqu'i. 

Veig la partici'o del W2, la d'ubuntu de 40 GB i el home de 218 GB amb 3,2 lliures.

He anat a Aplicacions per obrir el Terminal per'o no hi 'es. 

Com puc reinstal.lar el grub? 

En /boot/grub/ el ***grub.cfg*** no hi 'es. Solament hi ha 2 fitxers, grubenv i gfxblacklist.txt

---

### Post by jinglada on 2012-10-27
Fent Ctrl+Alt+T s-ha obert el terminal :)

----------------------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf571c4dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    25173854    12586896   27  Hidden NTFS WinRE
/dev/sda2   *    25173855    99490544    37158345    7  HPFS/NTFS/exFAT
/dev/sda3        99490545   625137344   262823400    5  Extended
/dev/sda5       603754893   625137344    10691226   82  Linux swap / Solaris
/dev/sda6        99490671   177614639    39061984+  83  Linux
/dev/sda7       177614703   603754829   213070063+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 16.0 GB, 15971909632 bytes
100 heads, 36 sectors/track, 8665 cylinders, total 31195136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2416    31195135    15596360    c  W95 FAT32 (LBA)
-------------------------------------------------
He llegit a internet que ara hauria de fer:

*sudo mount /dev/sda1 /mnt* si el GRUB fos a /dev/sda1 (**com se sap la particio'?**)
i *sudo mount --bind /dev /mnt/dev* per a muntar la resta de dispositius.

Accedir al sistema de fitxers de la partició amb *sudo chroot /mnt* &#8220;

i per últim, reinstal.lar GRUB: *grub-install --recheck /dev/sda*
-------------------------------------------------
En un altre lloc he llegit que e's a la partici'o del Linux o sigui que hauria de ser: *sudo mount /dev/sda6 /mnt*

E's correcte?

---

### Post by jinglada on 2012-10-27
He fet el seguent:

----------------------------------------------
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
root@ubuntu:/# 
----------------------------------------------------
Em podeu dir si el contingut del /boot/grub/device.map es correcte?

---

### Post by jinglada on 2012-10-27
Ja m'ha arrancat bé l'Ubuntu!
Ara miraré el Windows.

---

### Post by jinglada on 2012-10-28
Windows es va iniciar però abans de mostrar l'escriptori es va parar l'ordinador.  Al reiniciar ja surt el típic missatge:
 --------------------------------------------------------
Windows no puede iniciar. Esto se puede deber a un cambio reciente de hardware o software. 

-Iniciar reparacion de inicio (recomendado) 
-Iniciar windows normalmente 
-----------------------------------------------------------

No penso fer la reparació. El que m'agradaria fer és eliminar Windows i aprofitar l'espai de disc.  Com es pot fer?

---

### Post by wgarcia on 2012-10-28
Mira't aquesta pàgina, si tens problemes amb l'anglès comenta-ho, però no és un procés massa complicat (tot i que com sempre si tens dades importants als discos millor primer fer còpies de seguretat per si alguna cosa va malament):

[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)

---

### Post by jinglada on 2012-10-28
> **wgarcia said:**
> Mira't aquesta pàgina, si tens problemes amb l'anglès comenta-ho, però no és un procés massa complicat (tot i que com sempre si tens dades importants als discos millor primer fer còpies de seguretat per si alguna cosa va malament):

[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)

Gràcies!

---

