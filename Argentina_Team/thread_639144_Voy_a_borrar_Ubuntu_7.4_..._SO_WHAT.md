---
title: "Voy a borrar Ubuntu 7.4 ... SO WHAT ??"
date: 2007-12-12
forum: Argentina Team
---

### Post by leonardo83 on 2007-12-12
Que tal gente, debido a varios inconvenientes y demas que postee en varias oportunidades, y ademas del post donde dije que le daba unos minutos mas de vida, me decidi a erradicar ubuntu de mi rigido. :mad:
Espero desde win pueda formatear ese rigido como para instalar ubuntu 7.10 de una buena vez, y ver que inconvenientes esto trae.
Muchos archivos no tengo, bah, en realidad no tengo nada importante porque estuve ocupado ene ver como hacer funcionar al muy desgraciado en lugar de crear algo con openoffice o algo similar.
Borro todo y les cuento como me va.
Post al ****? puede ser, pasa que tenia que ponerlo en algun lugar, ja !
Saludos.

PD : para los que les interese, este mes salio el ultimo numero de 
US3RS LINUX .... bajon, con o que me gustaba!! :(
(lo pongo asi porque no se si puede hacer chivos aca).

PD2:despues veo como borrar el grub...

---

### Post by facundocorradini on 2007-12-12
Hola Leo

Podés hacer el formateo desde el mismo instalador del 7.10....

---

### Post by margori on 2007-12-12
Es una lastima que ubuntu no ha funcionado para ti.

Si las dificultades que tuviste son insostenibles, bueno será cuestion de utilizar ese espacio que ocupa linux para algo mas rentable.

Te cuento que lo que te sucedio, a mi ya me paso 4 veces. Entrada a linux, salida con decepcion y silbando bajito. Luego, entrada a linux, salida con decepcion y silbando bajito. Creo que cambio la historia cuando probe ubuntu, pero concidero que tanto a ubuntu como a linux le falta mucho camino por recorrer, y admitamos que esto es debido a que muchas de los avances se hacen de onda, por amor al arte.

Te pido, tomate un tiempo para pasar el mal trago y luego vulves a probar.

Te cuento que estoy en linux por cuestiones mas alla de su performance o diversidad. Windows XP para mi es un excelente sistema operativo, pero esta velado por la filosofia que tiene detraz. Yo estoy en linux por su filosofia y la comunidad que lo sustenta. Con ello me siento comodo, y aportare de mi humilde lugar.

Fue un gusto tenerte entre nosotros, y te esperamos pronto.

----

Se pueden eliminar las particiones ext3 y swap con el administrador de discos de windows 2000 o XP. Si estas con W9x, arranca en modo consola de sistema y usa el comando fdisk para eliminar las particiones foraneas y crea nuevas particiones fat o ntfs.

Para borrar el GRUB usa el comando fdisk /mbr. Con eso lo que haces es restaurar el master boot record para que ejecute el kernel de windows.

---

### Post by pablo0469 on 2007-12-12
Yo tambien innumerables inconvenientes (aclaremos que nos metimos en un sistema completamente diferente al que estabamos acostubrados), pero a pesar de todo, es el dia de hoy que al windows ya no lo puedo ver ni en figuritas.

Y de hecho, ahora voy a postear un nuevo inconveniente :).

Seguramente con Gutsy te va a ir mejor, y con el que se viene en abril del año que viene (el 8.04), ni hablar (hasta lo estan haciendo mas rapido para arrancar).

Saludos y metele para adelante.

---

### Post by facundocorradini on 2007-12-13
Cierto. 

aunque aún falten cuatro meses, soy de los que esperan a Hardy...

si bien hasta donde sé no trae muchas novedades, al ser una versión LTS seguramente tendrá una estabilidad envidiable... 

Mientras sigo con Gutsy, que a mí no me ha dado nunca ni un problema.

---

### Post by User21 on 2007-12-13
Yo también seguiré disfrutando de mi Gutsy, que en un principio me dio dramas con mi Nvidia mx4000, hasta que me dì cuenta que el que la pifiaba era yo!!! :D 

Es el síndrome pos-windowz el que nos hace desistir ? y es el 7.04, cheee! :P

---

### Post by rojojuan on 2007-12-13
> **margori said:**
> Es una lastima que ubuntu no ha funcionado para ti.

Si las dificultades que tuviste son insostenibles, bueno será cuestion de utilizar ese espacio que ocupa linux para algo mas rentable.

Te cuento que lo que te sucedio, a mi ya me paso 4 veces. Entrada a linux, salida con decepcion y silbando bajito. Luego, entrada a linux, salida con decepcion y silbando bajito. Creo que cambio la historia cuando probe ubuntu, pero concidero que tanto a ubuntu como a linux le falta mucho camino por recorrer, y admitamos que esto es debido a que muchas de los avances se hacen de onda, por amor al arte.

Te pido, tomate un tiempo para pasar el mal trago y luego vulves a probar.

Te cuento que estoy en linux por cuestiones mas alla de su performance o diversidad. Windows XP para mi es un excelente sistema operativo, pero esta velado por la filosofia que tiene detraz. Yo estoy en linux por su filosofia y la comunidad que lo sustenta. Con ello me siento comodo, y aportare de mi humilde lugar.

Fue un gusto tenerte entre nosotros, y te esperamos pronto.

.

Concuerdo totalmente!!!! Muy claro lo tuyo.

---

### Post by leonardo83 on 2007-12-14
Todo bien manes, pero NO dije que me deshacia del linux para siempre, solo que lo borraba del todo para instalarlo de nuevo!!
Es decir que borro todo de ese rigido e instalo ubuntu 7.10 de cero a ver que pasa.


No se si ...... en fin ... saludos. :lolflag:

---

### Post by margori on 2007-12-14
Ja! Eso me pasa por leer lo que tenia ganas de leer. Como el titulo decia "borro ubuntu... y que?" pense que dejabas linux. Ja.

Pido disculpas. Es que como venia vicioado por otro hilo en el que una persona se retiraba pense que esto era una historia parecida.

Ahora bien, por que una instalacion fresca y no una actualizacion?

---

### Post by leonardo83 on 2007-12-15
en fin....... fear,emptyness, despair !!!!!!
ayuda!! 
saben como puedo borrar al linux de mi segundo rigido??
no se puede usar format, que hago?? :confused:
esta en otro rigido solo para linux, lo del grub ya se que como se hace, pero como lo borro a este linux ??
Se puede desde la terminal o algo?? :confused:
En resumen, quiero que el rigido donde SOLO esta linux quede vacio, como si fuera uevo, no se como borrar ese linux, si desde terminal se puede, o como hago?
con win aparece el rigido de linux pero no me deja formatearlo, no lo reconoce y da error.
 A-Y-U-D-A !!! :( :(

Saludos!

---

### Post by pante on 2007-12-16
> **leonardo83 said:**
> 
En resumen, quiero que el rigido donde SOLO esta linux quede vacio, como si fuera nuevo, 


Con cualquier programa para particionar. Por ejemplo el viejo FDISK de WinDOS.

Saludos

---

### Post by leonardo83 on 2007-12-16
gracias pante, pero fijate que dije que fdisk ni format me funcionan con ese rigido. :mad:
Si elijo aplicarlo en el rigido de win si, pero en el de linux me tira error de comando, o de volumen, etc.

AYUDAAAAA!!! :(

Saludos.

---

### Post by Kasa.Ramone on 2007-12-16
Mira, tratando de instalar diferentes distros de linux en mi pc vieja (ya desisti, ahora voy a intentar con la pc nueva) continuamente particionaba y habia veces que se "*****" el rigido y no podia usar el fdisk para formatear porque me tiraba error en el disco.
Para eso usaba un Zero Fill que borra toda la data de ese disco (lo llena de 0) que seria algo como esto:

sudo dd if=\dev\zero of=\dev\UNIDAD
(si es root el user sacale el sudo)

Donde unidad vendria a ser el disco que queres que se borre todo su contenido (puede ser sda, hda,hdb, fijate que en ubuntu te tiene que decir que disco es.), cuidado de no pifiarle de disco que borra toda la info.
Si vos te fijas esta en la lista de codigos "maliciosos" o algo por el estilo(para prevenir que usuarios nuevos mediante una duda les digan esto y se les borre la info), sin embargo si lo que queres hacer es borrar entonces no hay ningun problema.

Saludos.

---

### Post by pante on 2007-12-16
Yo entiendo que estás tratando de eliminar desde WinDOS.

Desde WinDOS podés usar el Partition Magic. Es lo que conozco porque yo lo usé para crear las particiones que uso con Xubuntu.

Si no, desde un live CD (puede ser el de Ubuntu) particionás con la herramienta para particiones que traen muchos LiveCDs.

Saludos

---

### Post by kowal on 2007-12-16
Para crear/borrar particiones funcionan a la perfección Gparted (gráfico) o cfdisk (desde consola).

Saludos

---

