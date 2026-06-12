---
title: "Dual Boot"
date: 2008-04-02
forum: Argentina Team
---

### Post by mcongom on 2008-04-02
Hola, tengo una consulta para hacer.
En mi pc tengo 2 discos, uno con ubuntu y el otro con guindow$. En el disco que tengo el ubuntu bootea con el grub, como puedo hacer para que en el grub aparezca la opcion de bootear guindow$?? alguien sabe???
saludos, y gracias!!!!!

---

### Post by Mauro22 on 2008-04-02
Reinstala el grub

Usa el livecd y en la consola pones:


su
ahora sos root

despues pones 
grub

con eso entras a otra consola, la de grub

y pone:

root (hd0,0) Si ubuntu es el primer disco (primero 0) y esta en la primer particion (segundo 0)

despues pones:

setup (0,0) Los 0,0 igual que arriba, cambialo a como este en tu pc.


Entre root y (hd0,0) y entre setup (0,0) va un espacio!

---

### Post by gmunioz on 2008-04-02
Hola mco...:
Debes averiguar como se identifican tus discos para Ubuntu y para el Grub.
Esto lo haces ejecutando en consola:
sudo fdisk -l
Tendrás una salida parecida a esta:

Disco /dev/hda: 6495 MB, 6495068160 bytes
255 cabezas, 63 sectores/pistas, 789 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0x000437da

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1         749     6016311   83  Linux
/dev/hda2             750         789      321300    5  Extendida
/dev/hda5             750         789      321268+  82  Linux swap / Solaris

Disco /dev/hdb: 8455 MB, 8455200768 bytes
255 cabezas, 63 sectores/pistas, 1027 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0x000168d0

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdb1               1        1027     8249346   83  NTFS
 
Los discos rígidos /dev/hda ó sda para el Grub son hd0
Los discos rígidos /dev/hdb ó sdb para el Grub son hd1

Las particiones /dev/hda1 ó sda1 son hd0,0
Las particiones /dev/hdb1 ó sdb1 son hd1,0

Sabiendo ahora a que nomenclatura del Grub corresponde tu partición de Windows, 
debes editar el archivo /boot/grub/menu.lst mediante el comando:
sudo gedit /boot/grub/menu.lst
Y agregar al final las líneas:

 title		Windows XP
 root		**(hd0,0**)       *-----aquí cambiar por el que corresponde-----*
 makeactive
 chainloader	+1

---

### Post by mcongom on 2008-04-05
> **gmunioz said:**
> Hola mco...:
Debes averiguar como se identifican tus discos para Ubuntu y para el Grub.
Esto lo haces ejecutando en consola:
sudo fdisk -l
Tendrás una salida parecida a esta:

Disco /dev/hda: 6495 MB, 6495068160 bytes
255 cabezas, 63 sectores/pistas, 789 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0x000437da

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1         749     6016311   83  Linux
/dev/hda2             750         789      321300    5  Extendida
/dev/hda5             750         789      321268+  82  Linux swap / Solaris

Disco /dev/hdb: 8455 MB, 8455200768 bytes
255 cabezas, 63 sectores/pistas, 1027 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0x000168d0

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdb1               1        1027     8249346   83  NTFS
 
Los discos rígidos /dev/hda ó sda para el Grub son hd0
Los discos rígidos /dev/hdb ó sdb para el Grub son hd1

Las particiones /dev/hda1 ó sda1 son hd0,0
Las particiones /dev/hdb1 ó sdb1 son hd1,0

Sabiendo ahora a que nomenclatura del Grub corresponde tu partición de Windows, 
debes editar el archivo /boot/grub/menu.lst mediante el comando:
sudo gedit /boot/grub/menu.lst
Y agregar al final las líneas:

 title		Windows XP
 root		**(hd0,0**)       *-----aquí cambiar por el que corresponde-----*
 makeactive
 chainloader	+1

hice eso que dijiste, pero cuando selecciono el xp se reinicia la maquina

---

