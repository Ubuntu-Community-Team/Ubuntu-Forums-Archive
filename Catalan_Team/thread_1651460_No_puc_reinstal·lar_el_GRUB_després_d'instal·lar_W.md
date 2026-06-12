---
title: "No puc reinstal·lar el GRUB després d'instal·lar Windows 7"
date: 2010-12-23
forum: Catalan Team
---

### Post by mrc2407 on 2010-12-23
Bon dia a tothom!

Fa un any i mig que tinc un portàtil Acer Aspire 5738Z que venia amb Windows Vista instal·lat. Fa un temps hi vaig instal·lar Ubuntu 9.10 i he anat actualitzant versió a versió sense reinstal·lar Ubuntu fins a la 10.10. Ara mateix, si faig "sudo fdisk -l" a la terminal em dóna això:

```
Disc /dev/sda: 500.1 GB, 500107862016 octets
255 heads, 63 sectors/track, 60801 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x588a10cc

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1               1        1275    10240000   27  Desconegut
/dev/sda2   *        1275       46375   362266163+   7  HPFS/NTFS
/dev/sda3           46376       54208    62918572+   7  HPFS/NTFS
/dev/sda4           54209       60801    52958272+   5  Estesa
/dev/sda5           54209       60526    50749303+  83  Linux
/dev/sda6           60527       60801     2208906   82  Intercanvi Linux / Solaris

```

La primera partició ja venia amb l'ordinador i no sé què és, però he preferit no tocar-la fins que s'acabés la garantia de l'ordinador. Us adjunto una captura del gParted de com està tot:

[http://img442.imageshack.us/img442/404/capturabcd.png](http://img442.imageshack.us/img442/404/capturabcd.png)

El cas és que a la partició /dev/sda3 hi havia el Windows Vista. Quan vaig instal·lar Ubuntu, hi va haver un temps que podia carregar els dos sistemes operatius des del GRUB, però un bon dia va deixar de funcionar. No n'hi vaig fer cas, perquè no feia servir el Windows, pràcticament. Ahir, però, vaig instal·lar Windows 7 per fer feina de la universitat i ara no hi ha manera d'instal·lar el GRUB i poder carregar els dos sistemes operatius, ja que directament carrega Windows 7 sense preguntar.

La meva primera idea ha sigut fer servir un LIVE CD d'Ubuntu 10.10 i restaurar el GRUB així:
```
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
grub-install --recheck /dev/sda

(reiniciar i fer:)
sudo update-grub2 o bé sudo apt-get update -grub2 o bé sudo aptitude install grub
```

He trobat les instruccions en un blog que ara mateix no recordo. Ho he intentat, però a la tercera instrucció (sudo mount --bind /dev /mnt/dev) m'ha donat un error, així que he provat una altra cosa:

```
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-intall --root-directory=/mnt/ /dev/sda
```

Això sembla que ha funcionat, he reiniciat i m'ha aparegut el GRUB. He provat de carregar Windws 7, però Windows ha entrat en una espècie de bucle infinit i s'ha reiniciat solet, tornant al GRUB. Llavors he intentat carregar Windows 7 des del CD d'instal·lació, anant a Reparar equipo -> Terminal de operaciones i escrivint "bootrec.exe /fixboot", però no ha fet res. He provat de fer "bootrec.exe /fixmbr", però m'ha eliminat el GRUB i tornava a carregar Windows 7 sol.

He provat de restaurar el GRUB amb el SuperGrubDisk 0.9795, però em diu que no troba l'arxiu "/boot/grub/stage1" o "/boot/stage1", així que no fa res. Ara provaré amb el SuperGrub2Disk, aviam si és això, però començo a perdre l'esperança...

Per cert, amb el SuperGrubDisk puc arrancar Ubuntu, per això he pogut fer captures de pantalla del gParted :)

En fi, alguna idea de com puc solucionar això i fer que el GRUB pugui arrancar els dos sistemes operatius? A les males, es pot fer que el boot de Windows permeti carregar Ubuntu?

Gràcies!

**EDITO (26/12/2010):** Tema solucionat ;)

---

### Post by sordoman on 2010-12-23
hola

Jo diria que et falta actualitzar el grub despres d'instalar-lo

```

sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-intall --root-directory=/mnt/ /dev/sda
sudo update-grub

```

A veure si hi ha sort :)

---

### Post by quitus on 2010-12-24
des de ubuntu executa en el terminal el següent:

sudo upgrade-from-grub-legacy

el sistema et demanarà que seleccionis el dispositiu des de el que vols que arrenqui, assegura't de seleccionar el dispositiu correcte [SIZE="4"]amb la tecla [COLOR="Red"]"espai"[COLOR="Black"][/COLOR][/COLOR] [/SIZE]després només caldra reiniciar i ja està.

extret de la revista linux magazine

salut

---

### Post by mrc2407 on 2010-12-24
quitus, sordoman: gràcies a tots dos! Aviam si ho puc provar avui i us comento què tal ha anat.

De totes maneres, bon Nadal a tothom ;)

---

### Post by mrc2407 on 2010-12-26
Ja està, ja he trobat el problema (i l'he solucionat)! Tot ra culpa de l'arxiu /boot/grub/grub.cfg, que generava malament les entrades i hi posava moltes més línies del que tocava... Ho he configurat a mà i ara va bé :)

Gràcies a tots, tema tancat :)

---

