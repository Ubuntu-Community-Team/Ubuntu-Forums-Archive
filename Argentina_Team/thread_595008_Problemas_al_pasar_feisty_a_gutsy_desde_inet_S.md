---
title: "Problemas al pasar feisty a gutsy desde inet :S"
date: 2007-10-28
forum: Argentina Team
---

### Post by sartelinio on 2007-10-28
Bueno lo q hice fue actualizar desde adept mi feisty a gutsy... y el tema es q como  toda actualizacion nunca puede ser limpia.. siempre tiene q tirar algun ******* error :((((((( ... el tema es q al hacer "apt-get install -f" me sale esto..


laptop:/# apt-get install -f
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios
.
libpopt-dev imlib11 pkg-config libglib1.2-dev
linux-headers-2.6.20-16-generic libdv4-dev libraw1394-dev docker sox
linux-headers-2.6.20-16 imlib-base libquicktime0
Utilice «apt-get autoremove» para eliminarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
8 no instalados del todo o eliminados.
Necesito descargar 0B de archivos.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
Configurando linux-image-2.6.22-14-generic (2.6.22-14.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error al procesar linux-image-2.6.22-14-generic (--configure):
el subproceso post-installation script devolvió el código de salida de error 2
dpkg: problemas de dependencias impiden la configuración de linux-ubuntu-modules
-2.6.22-14-generic:
linux-ubuntu-modules-2.6.22-14-generic depende de linux-image-2.6.22-14-generic
; sin embargo:
El paquete `linux-image-2.6.22-14-generic' no está configurado todavía.
dpkg: error al procesar linux-ubuntu-modules-2.6.22-14-generic (--configure):
problemas de dependencias - se deja sin configurar
Configurando memtest86+ (1.70-3ubuntu1) ...
[: 25: ==: unexpected operator
exec: 25: -a: not found
dpkg: error al procesar memtest86+ (--configure):
el subproceso post-installation script devolvió el código de salida de error 2
dpkg: problemas de dependencias impiden la configuración de ubuntu-standard:
ubuntu-standard depende de memtest86+; sin embargo:
El paquete `memtest86+' no está configurado todavía.
dpkg: error al procesar ubuntu-standard (--configure):
problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de linux-image-generic:
linux-image-generic depende de linux-image-2.6.22-14-generic; sin embargo:
El paquete `linux-image-2.6.22-14-generic' no está configurado todavía.
linux-image-generic depende de linux-ubuntu-modules-2.6.22-14-generic; sin emba
rgo:
El paquete `linux-ubuntu-modules-2.6.22-14-generic' no está configurado todavía
.
dpkg: error al procesar linux-image-generic (--configure):
problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de linux-restricted-mod
ules-2.6.22-14-generic:
linux-restricted-modules-2.6.22-14-generic depende de linux-image-2.6.22-14-gen
eric; sin embargo:
El paquete `linux-image-2.6.22-14-generic' no está configurado todavía.
dpkg: error al procesar linux-restricted-modules-2.6.22-14-generic (--configure)
:
problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de linux-restricted-mod
ules-generic:
linux-restricted-modules-generic depende de linux-restricted-modules-2.6.22-14- generic; sin embargo:
El paquete `linux-restricted-modules-2.6.22-14-generic' no está configurado tod avía.
dpkg: error al procesar linux-restricted-modules-generic (--configure):
problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de linux-generic:
linux-generic depende de linux-image-generic; sin embargo:
El paquete `linux-image-generic' no está configurado todavía.
linux-generic depende de linux-restricted-modules-generic; sin embargo:
El paquete `linux-restricted-modules-generic' no está configurado todavía.
dpkg: error al procesar linux-generic (--configure):
problemas de dependencias - se deja sin configurar

Se encontraron errores al procesar:
linux-image-2.6.22-14-generic
linux-ubuntu-modules-2.6.22-14-generic
memtest86+
ubuntu-standard
linux-image-generic
linux-restricted-modules-2.6.22-14-generic
linux-restricted-modules-generic
linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

 
...Leyendo por ahi enkontre algo para solucionar 2 de estos 8 errores ke tira :S... asi ke el memtest86+ y ubuntu-standard ya no es problema... ahora kedan los otros 6 :((((((... asi ke si pueden darme una mano gracias ;)...

Les comento que tengo una Notebook HP pavillion dv2225la...


Rodrigo.

---

### Post by clasificado on 2007-10-29
Te diria que gugles por ahi esta linea
```
User postinst hook script [/sbin/update-grub] exited with value 2
```

que es el resumen de donde todo empieza a salir mal

Clasificado

---

### Post by juanman on 2007-10-30
El problema es q no reconoce un caracter en:
[: 25: ==: unexpected operator
ya q está usando un intérprete q no lo interpreta justamente, q es el dash o el sh. Para q use el bash q si lo conoce, probá con:
```
sudo dpkg-reconfigure dash
```
Y te va a preguntar si lo querés usar a lo q elegís NO

Saludos

---

### Post by angel.ramirez.isea on 2007-12-20
Tuve el mismo problema en una actualización de rutina y automática. Desktop, no laptop.

Se resolvió de la misma manera. Muchas gracias!

---

