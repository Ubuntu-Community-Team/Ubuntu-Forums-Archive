---
title: "Problema de permisos con disco hda1"
date: 2007-04-14
forum: Argentina Team
---

### Post by seba2611 on 2007-04-14
Tengo Ubuntu Dapper instalado en sda1 y agregue un disco mas IDE esta en HDA1 hasta hace 1 dia estaba todo bien podria escribir en el IDE hacer lo que queria ya q es una particion EXT3 pero de golpe ahora no me deja escribir mas nada me dice que no tengo permisos de escritura no me deja hacer nada solo ver los archivos ,en el FSTAB esta asi:

proc /proc proc defaults 0 0
/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
/dev/sda6 /home ext3 defaults 0 2
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=es_AR.UTF-8 0 1
/dev/hda5 /media/datos ext3 defaults 0 0
/dev/sda5 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0

entrando con nautilus a veces me sale sobre todas las carpetas un simbolito rojo que significa prohibido escribir es un lapiz con el cosito rojo q indica prohibo jeje para ser bien claro, y a veces no sale eso pero si quiero crear una carpeta o borrar algo no me deja, que puede ser?? hace unos dias instale NTFS-3G para poder escribir sobre la particion NTFS que tengo con XP y tb probe de desinstalarlo pero el problema sigue igual en la EXT3, se podra solucionar sin tener q reinstalarl todo de nuevo??

Agrego algo como root tampoco me deja crear una carpeta, desde la consola lo intente y esto es lo que me dice:

root@seba:/media/datos# mkdir prueba
mkdir: no se puede crear el directorio `prueba': Sistema de solo lectura
root@seba:/media/datos#

---

### Post by gepatino on 2007-04-14
El fstab parece estar bien, aunque si queres que se monte automaticamente al inicio, cambia el ultimo 0 por algun numero (es el orden de montaje al inicio, un 2 estaría bien)

En una de esas por algun problema se monto el filesystem como read only. Esto suele pasar si hay algun error que deba ser solucionado. Para comprobar esto, ejecuta el comando mount, sin parametros y fijate si la particion esta montada como rw o como ro (read-write y read-only, respectivamente)

De última desmonta la particion y hace un fsck de la misma para verificar que esté bien el filesystem.

---

### Post by seba2611 on 2007-04-15
Si por lo que veo me la esta montando solo como Read Only pero no se como cambiarlo.

---

### Post by beuno on 2007-04-15
> **seba2611 said:**
> Si por lo que veo me la esta montando solo como Read Only pero no se como cambiarlo.

Repasa bien: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)
Y por otro lado, proba escribir en la particion con sudo.
```
sudo mkdir nuevo_directorio
```

---

