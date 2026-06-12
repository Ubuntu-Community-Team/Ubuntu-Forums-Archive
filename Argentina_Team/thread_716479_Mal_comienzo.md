---
title: "Mal comienzo"
date: 2008-03-05
forum: Argentina Team
---

### Post by gualter666 on 2008-03-05
Buenas a todos, y desde ya gracias por tomarse la molestia de leer!. Recien me inicio en esto de linux/ubuntu, y no logro que funcione.
Me descargue la version 7.10 de Ubuntu,grabe la imagen en un CD, pero al iniciar no aparecio la pantalla que vi por ahi en algunas guias, sino algo mas basico (estilo MS-DOS) que al final dejaba como unica opcion "boot:". En fin, leyendo un poco, puse "live" y arranco, aparecio la pantalla de ubuntu, parecio comenzar a correr el SO, pero despues se quedo en un pantalla con una especie de "dibujo" muy raro, del cual no salio hasta que no reinicie.
Pensando que quiza pudo haber algun error en la descarga o en la grabacion de la imagen, en el trabajo lo volvi a descargar (sin que nadie se entere de que no estaba trabajando, jejeje), grabe la imagen en el cd, lo inicie, ahi si me aparecio el menu que habia visto en la guia de instalacion, comenzo a correr el cd, hasta que en un momento la pantalla se puso negra, y todas las lucecitas de los ajustes del monitor parpadeaban. La pc del trabajo es un amd 64 x2 4800+, con una mother nvidia k9n6sgm-v.
en fin, al volver a casa, probe con el cd que hice en el trabajo, nuevamente la interfaz era tipo MS-DOS, aunque ahora la instalacion arranco sin dibujos raros ni nada, hasta que llego a una pantalla donde aparecio el siguiente menasje:
"*Starting deferred execution scheduler atd        [OK]"
y de ahi no sigue mas.
Aca les dejo los datos de mi sistema, espero puedan darme una mano, porque de verdad me gustaria pasarme a Ubuntu

--------[ Overclock ]---------------------------------------------------------------------------------------------------

    Propiedades de la CPU:
      Tipo de procesador                                VIA C3
      Alias de la CPU                                   WinChip 5B, Samuel 2, Cyrix IIIA
      (CPUID) Nombre de la CPU                          VIA Samuel 2
      (CPUID) Revisión                                  00000673h

    Velocidad del CPU:
      Velocidad de reloj del procesador                 798.9 MHz
      Multiplicador de la CPU                           6.0x
      FSB de la CPU                                     133.2 MHz  (original: 133 MHz)
      Bus de la memoria                                 133.2 MHz
      DRAM:FSB Ratio                                    1:1

    Caché del CPU:
      Código de caché L1                                64 KB
      Datos de caché L1                                 64 KB
      Caché L2                                          64 KB  (On-Die, Full-Speed)

    Propiedades de la Placa Base:
      Identificación de la Placa Base                   08/03/2004-CLE266-8235-6A6LUJ1CC-00
      Nombre de la Placa Base                           Jetway V623DM/V623DMP/V623DMW/V623F/V623FP/V623FT/V623FW/V625EM/V625EMP

    Propiedades del chipset:
      Chipset de la Placa Base                          VIA VT8622/3 Apollo CLE266
      Tiempos de Memoria                                2.5-3-3-6  (CL-RCD-RP-RAS)
      Command Rate (CR)                                 2T

    Módulos de memoria del SPD:
      DIMM2                                             512 MB PC3200 DDR SDRAM  (3.0-3-3-8 @ 200 MHz)  (2.5-3-3-7 @ 166 MHz)  (2.0-2-2-6 @ 133 MHz)

    Propiedades de la BIOS:
      Fecha de la BIOS del sistema                      08/03/04
      Fecha de la BIOS de video                         04/01/04
      Tipo de BIOS Award                                Phoenix - AwardBIOS v6.00PG
      Mensaje de BIOS Award                             V.625EMP C04 08-03-2004

    Propiedades del procesador gráfico:
      Tarjeta gráfica                                   VIA VT8622/3 CLE266 Chipset - Graphics Controller
      Número de código                                  CastleRock  (Integrated 1106 / 3122, Rev 03)
      Velocidad de reloj                                133 MHz
      Reloj de la memoria                               133 MHz

Gracias de nuevo!!

---

### Post by gualter666 on 2008-03-06
Estoy ahora descargendo el alternate install cd....
despues comento como fue

---

### Post by Hei Ku on 2008-03-06
al poner el cd te aparece el menu de booteo?
La pantalla donde te dice si queres iniciar ubuntu, comprobar la memoria, el cd, correr desde el disco rigido, etc.

Y probaste de correr el booteo con la opcion noacpi?

---

### Post by gualter666 on 2008-03-06
Hola Hei Ku, gracias por responder.
En cuanto a tu consulta, al poner el cd no aparece el menu de booteo.
Probe correrlo en no acpi, hace exactamente lo mismo.

---

### Post by xboo2 on 2008-03-06
Hola gualter666, te aseguraste de que la descarga fué correcta, chequeando el MD5sum. Si no lo hiciste, buscá primero los números de md5sum para la versión que bajaste, luego si estás usando windows buscá en Google el winmd5sum instalalo. Y cotejá que el número que te genere la imagen del cd bajado coincida con el número que te da la gente de ubuntu. 
Si esto te coincide, fijate de cuando quemás tu cd, verificá los datos grabados, si usas Nero es fácil. Sino podés bajarte algunos softwares para incluso comparar la copia que ya quemaste con la imagen en el rígido. Cualquier cosa preguntá que me fijo cómo se llama el programa. Suerte.:)

---

### Post by gualter666 on 2008-03-06
Hola xboo2, hice la comprobacion al montar la imagen, ademas, despues hice el chequeo de disco en el menu de instalacion de ubuntu , y no me dio ningun error.
Por otro lado, probe instalar el alternate install cd, corrio bien, completo la instalacion, pero ahora no arranca ni el ubuntu ni el xp.

---

### Post by Hei Ku on 2008-03-06
Como que no arranca? Aparece algun mensaje?

---

### Post by tony_feisty on 2008-03-06
Llegas al menu del grub, o directamente se te queda tildado antes?.... podes ser mas especifico en la falla. Saludos

---

### Post by gualter666 on 2008-03-07
Hice la instalacion del alternate install cd, se completo, aparentemente bien, pero al momento de reiniciar, me aparece el menu de inicio, con la opcion de ubuntu, ubuntu en safe mode, el test de memoria (dio bien), y el xp.
Al intentar arrancar el ubuntu, llega hasta que me aparece el siguiente mensaje:
"starting anac(h)ronic cron anacron ................[OK]"
y ahi queda.
Si elijo iniciar en xp, se queda en Starting up........
Yo ya saque toda la informacion importante del disco, por lo que no seria tan grave formatear e instalar desde cero, pero me gustaria saber si hay alguna forma de no tener que instalar todo lo de xp nuevamente, hasta que definitivamente use solo el ubuntu.

---

### Post by wanchan on 2008-03-07
Tenés las particiones de tu disco bien?.
Una para windows, otra para ubuntu y otra para el swap (tiene que ir si o si). 
Si vas a instalar todo, primero instalate el windows y luego ubuntu, xq me parece que si lo haces a al revés te borra el GRUB de arranque.

---

### Post by gualter666 on 2008-03-07
Las particiones estan bien, quisiera saber si hay alguna solucion antes de formatear y reinstalar, porque tengo unos cuantos programas en windows y no quiero tener que instalar todo de nuevo.
Ademas me gustaria saber si una vez que formatee no voy a seguir teniendo este problema con ubuntu, creo que mi maquina lo deberia correr sin problemas, pero por ahora no lo hace

---

### Post by Radiobuzz on 2008-03-07
Mis conocimientos sobre GNU/Linux son totalmente básicos ya que hace poco más de un mes que uso Ubuntu, pero igual me prendo :P. ¿Podés ir a la terminal cuando se cuelga el inicio de booteo? Esto lo hacés presionando CTRL+ALT+F1. Luego de loguearte usá el comando "sudo startx" para ver qué pasa, aunque tengo el presentimiento que el problema está en la configuración de video.

Cuando estés en la consola escribí "sudo dpkg-reconfigure -phigh xserver-xorg", y luego intentá de nuevo con "sudo startx". Por cierto, ¿podés bootear en modo de recuperación?

---

### Post by gualter666 on 2008-03-07
Hola radiobuzz, gracias por responder, hoy cuando llegue pruebo lo que me dijiste y te comento como va. 
En modo recuperacion inicia, pero no se que hacer despues...

---

### Post by tony_feisty on 2008-03-08
Consulta, no intentaste probar con otras distros, ej. Kubuntu, Xubuntu para ver si levanta bien en forma normal.... en el caso que no ingresa en XP es por problemas con el grub.... tendrias que intentar recuperarlo.... 

----------------------------------------------------------------------------------------------------------------------
Pasos a seguir para recuperarlo.....

Levantar con un LiveCD (en mi caso Kubuntu)
Abrir la consola y escribir

$ sudo grub

despues

$ find /boot/grub/stage1

te muestra la configuraciòn de las unidades, en mi caso aparecio (hd0,1) o algo asi... despues tipeamos el comando root con ese dato tal cual. 

$ root (hd0,1)

despues (disco origen)

$ setup (hd0)

Salimos
$quit
----------------------------------------------------------------------------------------------------------------------------

Fijate si esto te sirve para ingregar en Windows...

---

