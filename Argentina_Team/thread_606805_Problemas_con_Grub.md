---
title: "Problemas con Grub"
date: 2007-11-08
forum: Argentina Team
---

### Post by UBUjuan on 2007-11-08
Ayer me llegaron los cd de ubuntu 7.10 y empece a instalarlo desde cero (ya tenia la 7.04 en una particion y xubuntu en otra).
Todo bien durante la instalacion, pero al reiniciar el equipo el grub me tiro "error 15". Inicie con el live y monte la particion en donde lo instale y me di cuenta que en /boot no habia el directorio "grub". Como no pude solucionarlo, me decidi a instalarlo de nuevo, y en el reinicio si lo cargo, pero en la lista de sistemas operativos me tira error en todos:
si eligo "ubuntu 7.10" me tira error 17
si eligo  "xubuntu" error 15
si elijo "windows" me tira : "a kernel file is missing from the disk. Insert a system diskette and restart the system."

Cabe aclarar que con el live puedo montar y leer claramente todos los datos de todas las particiones. Ademas, como mencione ya teneia instalado el xubuntu en otro disco (y el grub lo instale en el mbr de ese disco, un IDE) y cuando elijo "bootear" desde ahi todo carga normalmente, el problemas es con el "nuevo grub" que esta instalado en el disco rigido SATA.

Los discos son hdc 80GB IDE y otro SATA 320GB sda,este ultimo es el que tengo configurado para "bootear" primero y el que me trae problemas.

---

