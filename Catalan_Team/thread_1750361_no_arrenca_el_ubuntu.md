---
title: "no arrenca el ubuntu"
date: 2011-05-05
forum: Catalan Team
---

### Post by mggg on 2011-05-05
no arrenca el pc en linux, m'apareixen, entre altres aquests missatges:


mounting /sys on /root/sys failed: no such file or directory
no init found. Try passing init=bootarg.

enter 'help' for a list of built-in commands

hi ha alguna forma de reparar el sistema?

gràcies

---

### Post by snoopo71 on 2011-05-05
Nones mggg, sembla que tens problemes amb el Grub... . 
Prova de passar per [aqui]("http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB#Usando_Super_Grub_Disk") i fer el que hi ha al primer punt. Sort.

---

### Post by wgarcia on 2011-05-05
Seria útil saber quan apareixen aquests missatges. Arribes al menú del grub?

---

### Post by mggg on 2011-05-06
si, però després al intentar entrar amb el sistema operatiu linux em surt el missatge d'error. Si arrenco en windows no tinc cap problema.

---

### Post by wgarcia on 2011-05-06
És possible que hagis de córrer un "fsck" al disc d'arrencada, no et surt cap missatge suggerint-hi fer-ho? Pots arrencar en mode "recovery"?

---

### Post by mggg on 2011-05-06
amb mode recovery també em dona el mateix error

el fsck em diu que not found

entre les diferents opcions al posar help, no apareix la fsck

---

### Post by wgarcia on 2011-05-06
El que pot funcionar és el següent:

1. Inicia des d'un CD o USB Ubuntu autònom (Live)

2. Aplicacions -> Terminal

3. Entra: sudo fdisk -l    
(per saber el nom del dispositiu)

Per exemple pot sortir:
 
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: **********

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30238 242886703+ 83 Linux
/dev/sda2 30239 30401 1309297+ 5 Extended
/dev/sda5 30239 30401 1309266 82 Linux swap / Solaris

El nom del dispositiu seria /dev/sda1 en aquest cas


4. Entra: sudo fsck /dev/sda1            
5.  Reinicia l'ordinador a veure si ara arrenca

---

