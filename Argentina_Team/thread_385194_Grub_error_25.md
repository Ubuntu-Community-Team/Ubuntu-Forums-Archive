---
title: "Grub error 25"
date: 2007-03-15
forum: Argentina Team
---

### Post by undiaperfecto on 2007-03-15
Bueno, despues de buscar por todos lados y no encontrar una solucion, me decidi a recurrir a este foro. Onda, me quise hacer el canchero que yo podia, pero no pude nada :( 

Antes que nada lo mio es asi, tengo un disco primary master de 80gb con una instalacion de winxp, y un primary slave de 20gb con ubuntu dapper.

durante mucho tiempo mi grub funciono de maravillas, cada vez que reiniciaba podia acceder a xp y a ubuntu de manera correcta, hasta que un dia se quedo en 
**GRUB Loading Stage1.5.**
**GRUB Loading, Please Wait...** 

durante un par de minutos y finalmente me tiro el mensaje 
**Error 25**

Busque en foros y lo unico que logre fue reinstalar el grub, pero volvio a lo mismo.
Tambien probe con el supergrubdisk, pero nada, no funciono.

Yo creo que el problema es que el MBR no esta en el disco primary master, pero puedo estar equivocado, de ser asi tendria que reinstalar ubuntu en el mismo disco que xp (distinta particion) para solucionar el problema, pero necesito poder entrar a windowsxp o a ubuntu para poder hacer backups de algunas cosas (no se si eso se puede hacer desde el livecd) o directamente solucionar este error 25 que seria lo ideal.

Desde ya, mil gracias.

---

### Post by Mafber on 2007-03-15
Hola!! Como andas
En cuanto al backup una forma fácil es ir a Windows e instalarte un programa para que te reconozca las unidades de Linux. El programa es el "IFS Drivers". Una vez instalado ves las unidades como particiones (ej: D, E, etc)
Suerte con lo del Grub :)

---

### Post by beuno on 2007-03-15
Mientras encontramos una solucion para tu problema, para acceder a los archivos de Ubuntu desde windows: [http://www.kbglob.com/gnulinux/driver-de-ext2ext3-xfs-y-reiserfs-para-windows/](http://www.kbglob.com/gnulinux/driver-de-ext2ext3-xfs-y-reiserfs-para-windows/)

---

### Post by undiaperfecto on 2007-03-17
Sin dudas mi compu me odia.
Reinstale ubuntu, pero esta vez en el disco primary master, el problema era que solo tenia 4 o 5gb libres, pero bueno, lo instale igual y pensaba ir a windows para hacer backups y con el partition magic darle un poco de justicia al asunto, o sea 15gb para win y 65gb para ubuntu. 
Pero el hijo de bill se me rompio, una pavada, ya encontre la solucion pero solo me falta el disco de winxp booteable asi que todavia no lo hice por eso.
El tema es que use el ubuntu asi como viene nomas lo actualice y le instale dos pavadas, y asi anduve 2 dias perfectamente... peeeero al reiniciar recien, mister ubuntu simplemente no me deja entrar, le pongo mi user y pass, amaga a entrar y cuando carga la siguiente pantalla pooom, vuelve a la parte de login.
Me estoy quemando la cabeza, me odio, y odio a mi compu, pero como me costo mucho comprarla no la voy a incendiar por ahora, creo que estoy destinado a usar el livecd de por vida :(

Gracias por el driver para windows, me va a servir mucho para los backups. ;(

---

### Post by strugart on 2007-03-17
Una pregunta...borraste o por lo menos quitaste del sistema (osea le desenchufaste el clave ide) al disco de 20? Empezemos con esto. 
Aparte, si ya sacaste el disco de 20 y winxp se te jodio y aparte el ubuntu no te corre (me decis que te logea y no funka) yo haria lo siguiente:
Desconecto el disco de 80, osea le saco el cable IDE, dsp de eso conecto el de 20 reviso todo en el bios (que me lo renoce y botea bien...) dsp le pongo el live cd y si tengo una segunda grabadora de cds grabo un backup, sino pruebo con un pendrive o un diskette (no te digo zip porque es probable que no lo tengas). Despues de esto instalo ubuntu. Dsp que todo botea bien y anda de 10, conecto el disco de 80 y instalalo el win xp (si necesitas leer unidades NTFS desde linux, anda aca: [http://www.cesarius.net/ntfs-3g-escribiendo-en-particiones-ntfs/)](http://www.cesarius.net/ntfs-3g-escribiendo-en-particiones-ntfs/)). Espero haber ayudado un poco, cualquier cosa avisa que te seguimos ayudando.

---

### Post by undiaperfecto on 2007-03-17
Lo desenchufe al de 20, total despues hago los backups con tiempo.
Ya habia probado bootear con el disco de 80 solo y con el disco de 20 solo y no funciono, por eso decidi a instalar todo en un mismo disco, pero no sabia que si en la particion ubuntu me quedaba sin espacio, no iba a poder entrar. Eso lo acabo de leer buscando en google, que le paso a mas de uno, se quedaron sin espacio y no los dejaba entrar, onda no pasaban la pantalla de login.
Asi que mi mision ahora es entrar a windows, ya tengo el cd booteable para corregir lo que anda mal, y con el partition magic darle mas lugar a ubuntu, y si eso no funciona borro esas particiones y lo instalo de nuevo con mas espacio disponible. Mañana posteo los resultados. Mil gracias por tu tiempo y ayuda.

pd: tengo zip, el mejor invento jajajaja. mucho mas practico que un diskete y con buena capacidad, lastima que ahora con 100mb no hacemos nada. igual tambien tengo una memory stick de 4gb para salvar las papas.

---

### Post by undiaperfecto on 2007-03-20
Bueno finalmente cuento los resultados finales.
Perdi 0-1 con el "grub error 25"
Asi que finalmente decidi reinstalar todo, incluso winxp porque estaba mal instalado. Y tambien me pase a ubuntu edgy eft para estar un poco mas al dia.
Instale en un disco de 250gb, 1 particion con winxp de 30gb, 1 particion de 30gb para ubuntu, 270 y pico para archivos, y 1gb para el swap, todo manualmente, y por ahora funciona de maravillas. Lo unico que deberia despues arreglar unas cosas del grub que ya se como se hacen porque me tomo mi viejo win y mi viejo ubuntu ya que estaban los discos conectados para hacer los backups.
Asi que todo marcha de maravillas, estoy actualizando el sistema, pero acabo de descubrir una cosa, edgy solo tiene dos escritorios, me parece raro, ya me habia acostumbrado a los 4 de dapper, o sera que esos 4 aparecen cuando instale beryl? Bueno si alguno sabe, se agradece respuesta.
Gracias nuevamente por la buena onda de siempre.

---

### Post by lavaramano on 2007-03-20
para agregar escritorios virtuales dale click derecho sobre los escritorios y despues en **preferencias ** vas a tener una opcion que dice algo de **areas de trabajo**
y abajo un input(?) que dice **nro de areas de trabajo**, bueno. ahi agregas / sacas todos los escritorios que quieras.

---

### Post by undiaperfecto on 2007-03-20
Buen dato, gracias!!!!

---

### Post by undiaperfecto on 2007-03-21
Perdonen que joda con mis preguntas, pero como hago para poder habilitar la escritura en otra particion ext3 que nos ea donde esta instalado ubuntu?
Crei que iba a poder hacerlo por defecto, pero lo tengo habilitado solo para lectura y no encontre como habilitarlo desde el terminal :(

---

### Post by strugart on 2007-03-21
Dos cosas: Uno nunca joden las preguntas mas si a alguien le jodiera esto no habria llegado hasta donde llego...
Otra cosa fijate en permisos, osea click derecho, propiedades y dsp anda a la pestana de permisos. Ahi fijate si esta la solucion.

---

### Post by undiaperfecto on 2007-03-21
Claro, pero como no soy root no me deja, y no se como entrar root en modo grafico o como darle el permiso, supongo que debe haber un comando para hacerlo, al menos eso busque y no encontre nada, o tal vez modificando el /etc/fstab que ahi meti un poco de mano, pero no pude hacer nada asi que volvi a dejarlo como al principio. 
Debe ser una re boludez, reiniciar como root, pero no tengo idea de como se hace :(

---

### Post by strugart on 2007-03-21
Bueno yo tengo un script que abre natilius como root en modo grafico =). Ya te lo subi a rapidsahre
bajalo de aca:
[http://rapidshare.com/files/22157414/root-nautilus-here.html](http://rapidshare.com/files/22157414/root-nautilus-here.html)
Para instalar:
Anda a Lugares Carpeta personal, presiona ctr y dsp h y te van a aparecer los archivos ocultos. Busca uno que dice .gnome2 dentro de alli hay una carpeta que se llama nautilius scripts. Pegalo aca.
Despues en equipo click derecho scripts, root natilius here, te pregunta el pass y dsp te abre otra ventana pero con permisos de root.

Espero que te sirva.Strugart

---

### Post by lavaramano on 2007-03-23
mas facil todavia.
agrega un boton al panel y donde diga comando pone 'gksu nautilus'
charan.
tenes nautilus con root en un paso.

---

### Post by undiaperfecto on 2007-03-23
perfecto, ahi lo logre.
por error puse sudo nautilus 
pero funciono de todos modos, reinicie y ya estaba barbarisimo.
muchas gracias :)

---

