---
title: "Problema importante en un fichero montado en un XFS"
date: 2008-02-19
forum: Argentina Team
---

### Post by jclevien on 2008-02-19
Hola que tal,

Les molesto para comentarles un error severo que tengo con una máquina virtual.

Resulta que la máquina virtual tenía un programa servidor, lo dejé prendido durante la noche para brindar un servicio. OK.

Al levantarme, veo que en la máquina virtual, la pantalla se puso negra, no funcionaba el ratón ni el teclado. OK.

Bien, luego decidí apagarla y prenderla nuevamente a la máquina virtual. Apareció un hermoso cartel azul de la muerte de XP diciendo que no se podía montar el volúmen. OK.

Luego, dije: "Entonces reinstalo el VirtualBox, para ver si AL MENOS puedo arrancar mi máquina y sacar mis proyectos inmediatamente.". Fue lo que hice, y apareció un error de un objeto COM VirtualBox. OK.

La frutilla del postre fue cuando quise reiniciar mi computadora, tiene 2 discos SATA de 80 GB c/u. Uno tiene un filesystem reiserfs y el otro un xfs. El problema está en el xfs, porque al arrancar directamente no me quiso ni montar el xfs (que justamente es donde está la máquina virtual). Que MAL.

Con lo que ahora estoy un poco en llamas, bajando el paquete xfsprogs, pero ni siquiera me deja chequear el disco, porque me dice "Error de superbloque", ni me lo levanta aún desmontado.

Y ahora, ¿quien podrá ayudarme?

Necesito URGENTE sacar esa máquina virtual de ese filesystem y recuperar esos archivos.

Muchas gracias por su aporte.

Saludos.


Juan

---

### Post by faktorqm on 2008-02-19
Bueno, hay que ser muy puntiagudo y preciso a la hora de operar. Yo esperaria varias opiniones aparte de la mia, estudiaria todas las soluciones y luego ejecutaria una accion.
para empezar a diagnosticar el problema, la opcion -v en el mount es de verbose, asi que podrias ver con eso que onda. posteate el fstab y el mtab asi vemos donde esta y esas cosas. T recuerdo que el mount SIEMPRE lee primero el fstab para montar, ignorando las opciones que vos le pones si existe entrada en el fstab. asi que a veces hay que hacer un trabajo de toqueteria para que funcione.
El error de superbloque me paso una sola vez y no me acuerdo por que habia sido, pero no me habia sido muy agradable.

Cuando haces "man mount" en una parte te aparecen las opciones de montaje para xfs. hay una opcion que es --force en el mount, pero creo que era para que te lo monte cuando no fue limpiamente desmontado. y en xfs_progs no hay ninguna especie de scandisk (vos me entendes...) para xfs?

Para mas info; si tenes el qparted instalado abrilo y fijate si aunke sea te tira bien los datos de la particion xfs, si no es asi, esta la informacion pero la tabla de particiones esta defectuosa, o capaz te tira todo bien y es otro el error. 

Salu2!!

---

### Post by jclevien on 2008-02-19
Hola faktorqm,

Gracias por contestar.
Con respecto a lo del "scandisk"... sería "fsck" :D

Te cuento:

1. Ya pude montar la partición XFS. No me preguntes como, al rebootear la máquina varias veces la montó. Saqué rápido el VDI pero me enteré que está corrupto, ya que el XP me tira el error de la muerte que no puede montar el volumen NTFS.
2. ¿No habrá algún "repair" de archivos VDI? ¿Se habrá jodido el filesystem virtual o tendrá un error el archivo VDI "real" luego de este problema?


Veremos que pasa. Sigo posteando novedades. Gracias nuevamente.


Juan

---

### Post by faktorqm on 2008-02-19
si si t dije lo del scandisk por que como nombraste el xfs-progs capaz pense que fsck sirve solo para ext2 y ext3. buenisimo que salvaste eso, el tema con el vdi seria lo siguiente, si lo podes copiar, o mover, seria reinstalar el windows. si no podes copiarlo o moverlo, la idea seria buscar un visor de archivos .vdi, cosa que te permita abrirlo, explorar la estructura de directorios, copiar lo que te hace falta, e instalar todo de cero otra vez. salu2!

---

### Post by jclevien on 2008-02-19
Hola faktorqm,

Listo, ya solucioné todo.
El problema es que se había dañado el XFS, a gatas pude copiar el VDI.
Usé el RIP (Recovery Is Possible) LiveCD, que de paso te digo que me SALVO la vida, el problema era que el NTFS de la máquina virtual tenía corrupto el journal. Corrí el ntfsfix y asunto arreglado.

Mil gracias por tus recomendaciones. Saludos.


Juan

---

