---
title: "Problema con mi Pc"
date: 2008-04-18
forum: Argentina Team
---

### Post by katon on 2008-04-18
hola tengo un problema mi Ubuntu se pone muy pesado todo el tiempo, 
ya sea cuando abro el FIrefox con 1 o 2 ventanas o cualquier otro programa y se cuelgan las ventanas osea que hay que cerrarlos a la fuerza. como si fuera windows. Y se traban todas las ventanas , muchas veces pasa tambien cuando navego en internet paginas que tienen muchas fotos, o flash se pone muy pesado y aveces nose puede hacer nada mas que esperar y/o hacer KILL desde el process manager.

cuando miro en Process manager muchas veces veo que el procesador se pone al maximo y nose porque. 
Mi maquina es Pentium 4 1.6 ghz  , 630 mb ram placa de video Ati rage mobility 64mb . 
No estoy usando el manejador de ventanas compiz ni nada , porque pense que era por eso, pero ahora el ubuntu gnome como viene tambien me hace eso...ya nose que puede ser....estoy pensando algo de Hardware..... ni idea que . Hize una prueba a las memorias desde el bios , estan bien, 

les agradeceria su ayuda,

---

### Post by erginemr on 2008-04-18
1. No estoy seguro, pero puede ser un problema acerca del tamaño de "swap".
Cuales son los resultados de estos commandos en el terminal:
```
sudo fdisk -l
```
```
cat /etc/fstab
```

2. De lo contrario, puede ser un programa con un uso excesivo de CPU:
Puede usted tomar una captura de pantalla de este commando:
```
top
```
parecida a la imagen adjunta?

---

### Post by katon on 2008-04-18
[I][SIZE="3"]mati@mati-desktop:~$ cat /etc/fstab[/SIZE]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a77080c5-fb01-4361-afef-738c860ef540 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=43ecace9-5961-4dff-b675-54f8d1637848 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0[/I]

[COLOR="DarkOrange"]mati@mati-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb573b573

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4877e03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 998 MB, 998768640 bytes
254 heads, 60 sectors/track, 32 cylinders
Units = cylinders of 15240 * 2048 = 31211520 bytes
Disk identifier: 0xdbc937d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          32      975240    6  FAT16
[/COLOR]

y el otro comando aca esta la foto

---

### Post by erginemr on 2008-04-18
Lo siento **katon** pero el problema es ni uno, ni otro: Su partición "swap" es activa, y los usos de CPU por los programas estan normales. No tengo ningun idea...

---

### Post by erginemr on 2008-04-18
Creo que usted debe esperar hasta que su ordenador se pone lenta de nuevo, y probar "top" o el "Process Manager" para descubrir el programa / la actividad quien es responsable de esta lentitud.

Por otra parte, puede probar a desactivar "trackerd", uno daemon para buscar los archivos. ¿Hay alguna diferencia? (Véase la imagen adjunta)

---

### Post by Alejandro Vidal on 2008-04-18
Buenas.
Se que ésta no es la respuesta ideal, pero quería compartir mi experiencia.
Me pasaba algo similar en una notebook vieja con características similares a las que vos mencionas.
Hace un par de semanas instalé xubuntu de cero.
Los resultados son increíbles. La máquina funciona mejor de lo que funcionaba el día que la compré hace aproximadamente seis años.

Espero que puedas resolverlo.
Suerte.

---

### Post by katon on 2008-04-18
gracias a todos., 
si lo que pasa Alejandro es que antes usaba ubuntu talvez la version anterior, y con los efectos y todo y me andaba bien.....
puede ser que instale xubuntu...aunque pentium 4 es tan vieja??

---

### Post by Alejandro Vidal on 2008-04-18
> **katon said:**
> gracias a todos., 
si lo que pasa Alejandro es que antes usaba ubuntu talvez la version anterior, y con los efectos y todo y me andaba bien.....
puede ser que instale xubuntu...aunque pentium 4 es tan vieja??

Si antes funcionaba bien es seguramente otro el tema. Me gustaría poder ayudarte pero mis conocimientos técnicos en la materia son bastante limitados.
En lo que respecta a si pentium 4 es vieja opino que no.
Sin embargo los SO y las aplicaciones son cada vez más demandantes.
No se exactamente cuáles son los requerimientos del vista pero dudo que funcione con fluidez.
Mi sensación con xubuntu fue sencillamente que absolutamente todo funciona con un fluidez asombrosa cuándo con ubuntu tenía tiempos de espera mayores aunque funcionaba correctamente.

Saludos.

---

