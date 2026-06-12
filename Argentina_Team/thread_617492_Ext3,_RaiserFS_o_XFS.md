---
title: "Ext3, RaiserFS o XFS???"
date: 2007-11-19
forum: Argentina Team
---

### Post by Thalskarth on 2007-11-19
Hola, buenas... estube viendo un rato en la internet y me enteré de la existencia de estos sistemas de archivos... y ahí me entró la duda--- cual es más conveniente usar? o cual usan y porque?

O sea, buscando encontre que decian que ext3, es el "peorcito" pero el más estable y con mejor soporte... otros decian que RaiserFS era el mejor, más rápido y orientado a archivos pequeños, otros que XFS era mejor para grandes. O que era mejor para todo... y cosas asi...

Lo malo, es que vindo en la red, casi todo lo que decian estaba fechado desde el 2005 para atras... y no encontra nada "actualizado"...

entonces ahi, mi duda...cual conviene para una pc de escritorio?

PD: basando entre todo lo viejo, la mejor opcion parecia ser / en XFS y /home en ext3.   y en otro lado, el raiserfs para / , Ustedes que dicen, ya que saben más que yo

---

### Post by marianom on 2007-11-19
A esta altura, ext3 es un standard seguro (y no abro juicio de valor sobre los otros porque no los he puesto a prueba lo suficiente). Yo -posiblemente por cobardía y porque para experimentos ya tengo otras cosas- estoy en ese y me voy a quedar una buena temporada.

---

### Post by por100pre1 on 2007-11-19
ReiserFS es más rápido que ext3, pero esa rapidez trae consigo un mayor consumo de cpu; eso puede ser una desventaja en sistemas viejos o laptops. ReiserFS es también más vulnerable a corrupción de archivos que ext3. No sé sobre XFS.

---

### Post by MeduZa on 2007-11-19
fijate que raiser tanto como ext3 sacaron vercion nueva, ext4 y no me acuerdo el otro XD
cuando compile el otro dia el kernel encontre que podia agregar ext4 (experimental)

---

### Post by clasificado on 2007-11-19
[Off Topic]
¿Asi que queres complicarte la vida?

Mira este listado que es muy divertido

[http://fuse.sourceforge.net/wiki/index.php/FileSystems](http://fuse.sourceforge.net/wiki/index.php/FileSystems)

[Off Topic]

Clasificado

---

### Post by Thalskarth on 2007-11-19
> **MeduZa said:**
> fijate que raiser tanto como ext3 sacaron vercion nueva, ext4 y no me acuerdo el otro XD
cuando compile el otro dia el kernel encontre que podia agregar ext4 (experimental)

Si, no los nombre ni nada, porque por lo que se, el Ext4 todavia esta como "developtment" y el Reiser4 no esta incluido en el kernel todavia... o al menos eso entendí...

---

### Post by MeduZa on 2007-11-20
> **Thalskarth said:**
> Si, no los nombre ni nada, porque por lo que se, el Ext4 todavia esta como "developtment" y el Reiser4 no esta incluido en el kernel todavia... o al menos eso entendí...

reiser4 era xD gracias ;)

si los 2 ya estan creo para ser usados siempre qeu sea para debelopment, aunque yo creo que deben andar bien :)

---

### Post by faktorqm on 2007-11-20
para mi el mejor que vi hasta ahora es ZFS. el sistema de archivos de sun (solaris) salu2!

---

### Post by Thalskarth on 2007-11-20
> **faktorqm said:**
> para mi el mejor que vi hasta ahora es ZFS. el sistema de archivos de sun (solaris) salu2!
Talvez sea tonta mi pregunta, pero el ZFS se puede usar con Linux??? o es solo para OpenSolaris???





Entonces, para una PC normal de escritorio... conviene usar solo ext3???

---

### Post by clasificado on 2007-11-20
> Entonces, para una PC normal de escritorio... conviene usar solo ext3???

Ajá. Todo aquel que quiera usan la PC y no quiera complicarse la vida ext3 es lo bastante rapido, lo bastante confiable y lo bastante potente como para que no vayas a necesitar nada mas.

Ahora, si estas en desacuerdo en ese ultimo parrafo, es que estas dispuesto a buscar algo mas, y si es por ajuste fino y rendimiento, depende del propósito de cada carpeta, el sistema de archivos que quieras usar. ReiserFS maneja mejor cuando abundan archivos pequeños, y en caso de documentos importantes, mejor usar algo como CryptoFS, que encripta al vuelo.

Al final, a prueba y error, cada uno va encontrando la mejor estructura para sus necesidades, que puede ser ext3, ext2, reiserfs o xfs, o una combinacion de todas las anteriores

Clasificado

---

### Post by faktorqm on 2007-11-21
> **Thalskarth said:**
> Talvez sea tonta mi pregunta, pero el ZFS se puede usar con Linux??? o es solo para OpenSolaris???

Entonces, para una PC normal de escritorio... conviene usar solo ext3???

en una pc normal de escritorio conviene usar ext3 si no te quita el sueño este tema. por ejemplo yo tengo todo en ext3, pero soy un lokillo de la informatica y me gusta tener el sistema al limite siempre, entonces tengo el SO mas rapido, mas eyecandy y mas operable posible. es decir, si por poner iconitos de colores veo que el rendimiento baja, los saco. el inicio tarda mucho? saco todo. no puedo instalar la impresora? entonces no sirve.

Vos podes usar el sistema de archivos que mas te guste, siempre y cuando este soportado por el kernel. Ejemplo, vos no podes usar ntfs para poner tu gnu/linux por que no esta soportado nativamente. ni siquiera poniendole el ntfs-3g. En cambio, ext2 y ext3 si esta soportado. creo que vfat tambien. existen varios sistemas de archivos, y siguen evolucionando, muy muy de a poco, pero siguen. yo quiero que salga ext4 y supere todo, :P :P

mas info: [http://es.wikipedia.org/wiki/Anexo:Sistemas_de_archivos_de_disco](http://es.wikipedia.org/wiki/Anexo:Sistemas_de_archivos_de_disco)

salu2!

---

### Post by clasificado on 2007-11-21
> Talvez sea tonta mi pregunta, pero el ZFS se puede usar con Linux??? o es solo para OpenSolaris???
Se puede por FUSE

clasificado

---

### Post by faktorqm on 2007-11-22
como / se puede usar? o solo para montar en alguna carpeta tipo /media/algo? salu2!

---

### Post by Thalskarth on 2007-11-29
> **clasificado said:**
> Se puede por FUSE

clasificado

Ahi ya superé mis pequeños conocimientos... ya que más alla que de leerlo alguna vez, no se que es el FUSE. Asi que mejor ahi no me meto :)



Lei lo del Ext4, pinta interesante... esperemoslo :D

---

### Post by Hei Ku on 2007-11-29
FUSE te permite montar el file system en userspace, o sea en el espacio de uso del usuario, no del kernel. O sea que podes montarlo para archivos, pero no podrias correr un kernel desde ahi.

---

### Post by juanman on 2007-11-30
Personalmente uso reiserfs y ntfs, q desde hace un año estoy tratando de migrar a xfs (ya no uso win, pero no puedo hacer espacio :p). En mi caso no usaría ext3 xq solo aprovecha el 92% del espacio total del disco, mientras q los demás aprovechan mas del 99,8%
Segun he leido estas son las recomendaciones:
ext3: mas compatible (hay drivers para windows) y estable, lento pero consume poca cpu
reiserfs: rapido e ideal con archivos chicos pero consume mucha cpu. Hay varias distros q lo usan por defecto como Suse. Actualmente, su creador Hans Reiser está preso (parece q no se llevaba bien con su esposa) y Reiser4 quedó medio parado... La pagina oficial de reiser hoy ni siquiera está online...
xfs: ideal con archivos grandes. En [varios lugares]("http://elblogdeover.wordpress.com/2007/04/14/comparacion-de-sistemas-de-archivos-ext3-reiser-xfs-jfs/") lo dan como el filesystem mas recomendable, salvo para la particion de boot
jfs: el mas seguro y con mas bajo consumo de cpu

El zfs tambien recibió criticas, uno de ellos era Linus, q decia q en Linux ya existe el resier q hace lo mismo y q no se porque se habla tanto de éste...

---

### Post by Daishiman on 2007-11-30
Hmm, Hans está preso por ser acusado de ASESINATO :-O .
Igualmente cambia poco las cosas. Lo que sí hay que tomar en cuenta es que Reiser es propenso a corrupción de datos si cortás energía de golpe (o sea, tené una UPS a mano o usalo en una notebook), y no tiene un maintainer actualmente. O sea, no hay nadie agregando cosas al driver de Linux para el filesystem.

Creo que la cuestión de uso de CPU es algo que se puede ignorar tranquilamente. En una máquina moderna eso es, como mucho, un 1% más de uso de CPU, pero cuando tomás en cuanta que muchos archivos se abren dos veces más rápido en Reiser of XFS, es una mejora neta infernal, porque el acceso a disco es mucho más lento. Tu PC se pasa más tiempo esperando a que se abran archivos a que completen operaciones de CPU o memoria.

---

