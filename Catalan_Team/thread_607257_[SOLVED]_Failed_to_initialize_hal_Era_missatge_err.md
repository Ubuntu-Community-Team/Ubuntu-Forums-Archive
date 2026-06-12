---
title: "[SOLVED] Failed to initialize hal Era: missatge error al iniciar"
date: 2007-11-08
forum: Catalan Team
---

### Post by carlesbm on 2007-11-08
Hola gent

    Us presento un altre problema desde que hem va passar el problema amb  la resolució de l pantalla, m'apareix el missatge que hiha a la imatge que us adjunto.


   Tambe he pogut apreciar que quan vull tancar el sistema, entre que pitjo la icona de surtir i que apareix la pantalla de opcions trancorre molt de temps, durant el qual no hem permet de fer res, es quelcom si estigues mig "penjat".

   També he pogut apreciar qué, un cop arranco e intento de accedir a Internet no hem permet de navegar, llavors reinicio el sistema i aquat segon cop si que ja puc navegar normalment.

   Estic plenament convençut de que mentre intentava adivinar quina icona seleccionava, amb la resolició malament vaig tocar alguna opció que devia, i naturalment ho he desfet tot.


   Teniu alguna idea de que puc fer per solucionar aqeust problemes?


P.D.
      Descartant aquest preoblemes de novell cada cop m'agrada més treballar amb Linux (Ubuntu), al principi hem semblava un cosa molt complicada i dificultosa per un usuari no experimentat, però ara estic ben decidit ha utilitzar-lo amb molta major freqüencia.


        GRACIES HA TOTS

---

### Post by papapep on 2007-11-08
Sembla que hi ha un munt de gent amb aquest problema, i alguns ho han solucionat fent això:

```
sudo mv /etc/rc2.d/S50dbus /etc/rc2.d/S12dbus
```

i tornar a iniciar el sistema, a veure si ja no dóna l'error el Hal.

---

### Post by carlesbm on 2007-11-09
Hola Papapep

    He probat elq ue u m'has dit i m'hapareix aquest misstge

carles@carles-Despatx:~$ sudo mv /etc/rc2.d/S50dbus /etc/rc2.d/S12dbus
mv: ha fallat stat() sobre «/etc/rc2.d/S50dbus»: No such file or directory
carles@carles-Despatx:~$ 


crec que diu que no hi ha el fixer.

Gracies

Alguna altra idea

---

### Post by papapep on 2007-11-09
Fes un:

```
ls -la /etc/rc2.d/
```

i enganxa el resultat.

---

### Post by carlesbm on 2007-11-09
Aquest es el resultat 

carles@carles-Despatx:~$ ls -la /etc/rc2.d/
total 20
drwxr-xr-x   2 root root  4096 2007-11-06 20:59 .
drwxr-xr-x 134 root root 12288 2007-11-09 16:31 ..
-rw-r--r--   1 root root   556 2007-10-04 13:17 README
lrwxrwxrwx   1 root root    17 2007-08-28 23:14 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx   1 root root    15 2007-08-28 23:14 S10acpid -> ../init.d/acpid
lrwxrwxrwx   1 root root    25 2007-08-28 23:14 S10powernowd.early -> ../init.d/powernowd.early
lrwxrwxrwx   1 root root    18 2007-08-28 23:14 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx   1 root root    34 2007-08-28 23:14 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx   1 root root    15 2007-08-28 23:14 S11klogd -> ../init.d/klogd
lrwxrwxrwx   1 root root    13 2007-11-06 07:54 S12hal -> ../init.d/hal
lrwxrwxrwx   1 root root    13 2007-08-28 23:14 S13gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    23 2007-09-01 18:27 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx   1 root root    19 2007-09-01 18:27 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx   1 root root    16 2007-08-28 23:14 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx   1 root root    15 2007-09-01 18:27 S19mysql -> ../init.d/mysql
lrwxrwxrwx   1 root root    24 2007-09-01 17:22 S19postgresql-8.1 -> ../init.d/postgresql-8.1
lrwxrwxrwx   1 root root    24 2007-11-06 07:52 S19postgresql-8.2 -> ../init.d/postgresql-8.2
lrwxrwxrwx   1 root root    14 2007-08-28 23:14 S20apmd -> ../init.d/apmd
lrwxrwxrwx   1 root root    16 2007-08-28 23:14 S20apport -> ../init.d/apport
lrwxrwxrwx   1 root root    22 2007-08-28 23:14 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx   1 root root    17 2007-08-28 23:14 S20makedev -> ../init.d/makedev
lrwxrwxrwx   1 root root    23 2007-08-28 23:14 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx   1 root root    19 2007-08-28 23:14 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx   1 root root    15 2007-08-28 23:14 S20rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root    20 2007-11-06 00:51 S22consolekit -> ../init.d/consolekit
lrwxrwxrwx   1 root root    22 2007-11-06 00:51 S24avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx   1 root root    16 2007-11-06 00:54 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx   1 root root    19 2007-08-28 23:14 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx   1 root root    16 2007-11-06 20:59 S50hdparm -> ../init.d/hdparm
lrwxrwxrwx   1 root root    17 2007-08-28 23:14 S89anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root    13 2007-08-28 23:14 S89atd -> ../init.d/atd
lrwxrwxrwx   1 root root    14 2007-08-28 23:14 S89cron -> ../init.d/cron
lrwxrwxrwx   1 root root    24 2007-08-28 23:14 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx   1 root root    17 2007-08-28 23:14 S98usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root    22 2007-08-28 23:14 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root    21 2007-11-06 00:51 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root    18 2007-08-28 23:14 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx   1 root root    19 2007-08-28 23:14 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx   1 root root    24 2007-08-28 23:14 S99stop-readahead -> ../init.d/stop-readahead
carles@carles-Despatx:~$ 

No hi ha el fixer s50.....

---

### Post by papapep on 2007-11-09
Cap problema. Si no hi és per canviar-lo de nom, el crearem directament:

```
sudo ln -s  /etc/init.d/dbus /etc/rc2.d/S12dbus
```

---

### Post by carlesbm on 2007-11-09
GRACIES

Sembla que ja esta solucionat, sort que he trobat aquest forum sino no ser que hagues fet.

---

### Post by papapep on 2007-11-09
Perfecte!!! Apa, marca el fil com a resolt ;-) 

A "thread tools" clica damunt "Mark this thread as solved".

---

