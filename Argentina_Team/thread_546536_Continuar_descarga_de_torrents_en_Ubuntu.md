---
title: "Continuar descarga de torrents en Ubuntu"
date: 2007-09-09
forum: Argentina Team
---

### Post by ideafix on 2007-09-09
ola gente. Lo que qiero hacer es que cuando entre a Xubuntu (7.04) poder seguir descargando lo que tengo en el uTorrent. La misma pregunta y la respuesta la encontre aca:
[http://ubuntuforums.org/showthread.php?t=266204](http://ubuntuforums.org/showthread.php?t=266204)
y siguiendola pude hacer andar de diez el uTorrent con wine. Pero lo q no consigo es que me cargue lo que ya estoy bajando, o sea, lo que carga si entro a windows, no se si se entiende. Por ahi lei en la guia que no se soporta escritura en NTFS, ahi tambien me pierdo con lo que debo hacer. Supuestamente el flaco lo hizo andar, pero no da muchas precisiones. 
Le dejo un par de datos:
la carpeta donde esta lo que se va descargando es (en windows)
c:\documents and settings\administrador\mis documentos\downloads

y donde estan los archivos torrents es en
c:\documents and settings\administrador\datos de programa\utorrent

Se agradece la ayuda!!!

---

### Post by FlyerDie on 2007-09-09
a mi entender es medio cabeza eso de usar el utorrent tanto en linux como en windows,ya que podrias usar clientes de linux sin drama pero cada uno tirne sus gustos gustos..

En el caso del link que posteas estan hablando de FAT32, y no de NTFS..

Lo que te recomiendo que hagas es que escribas sobre la particion ext3 tanto en windows como en linux, y NO que utilices la particion NTFS en windows y linux para escribir los torrents.

Como accedes a la particion ext3 tanto para escritura-lectura en windows? facil, con el IFS Drives que lo podes bajar de [http://www.fs-driver.org/](http://www.fs-driver.org/) 
Con este soft monta la particion ext2 o ext3 como una unidad de windows (F: G: o lo que sea) y utilizala como la repositoria de los torrents que bajes, se entiende?

Saludos:guitar:

---

### Post by faktorqm on 2007-09-11
hola, trata en lo posible de no usar wine, y windows tampoco.... :lolflag:

para escribir en ntfs lo que tenes que instalar es un paquete que se llama ntfs-3g. lo instalas con sudo apt-get y despues lo usas como el mismisimo mount.
por ejemplo: 
```
sudo ntfs-3g /dev/hdc1 /media/jojo
```
espero ke te sirva. salu2!!

---

### Post by FlyerDie on 2007-09-11
> **faktorqm said:**
> hola, trata en lo posible de no usar wine, y windows tampoco.... :lolflag:

para escribir en ntfs lo que tenes que instalar es un paquete que se llama ntfs-3g. lo instalas con sudo apt-get y despues lo usas como el mismisimo mount.
por ejemplo: 
```
sudo ntfs-3g /dev/hdc1 /media/jojo
```
espero ke te sirva. salu2!!

:-$ le estoy diciendo que use solo ext3 para que termine de irse del lado oscuro :lolflag:

Yo lamentablemente (por ahora), no me voy de windows solo por el hecho de que no me funcan los auriculares sin mutear los parlantes en la notebook, sino ya estaria 100% pasado a ubuntu (ya probe todo lo que postearon :( )

---

### Post by faktorqm on 2007-09-12
ahh si yo respondi por ahi algo de eso, eras vos?

le digo lo de ntfs por que me parecio ke no tiene muchas intenciones de borrar güindous, y necesitaba una solucion. yo respondi lo que pregunto, o sea, ya sabemos cual es "EL CAMINO", pero si quiere usar güindous.................... alla el!!
:lolflag: cada uno con su pc hace lo que quiere! salu2!!

---

### Post by ideafix on 2007-09-12
ja, me encanto, mis post reunen a la gente... me siento el del programa ese de gente q busca gente (karinaaaa... jajaja). Por razones varias no migro totalmente, pero eso no viene al caso. Graacias por las respuestas, utorrent con wine me funciona a la perfeccion con el IFS. se continua la descarga. Con los programas de torrrent de ubuntu probe y nunca se conectan, sera cuestion de seguir probando.... El otro driver para escribir en NTFS lo conocia pero todavia no lo probe en xubuntu (en ubuntu 6.06 si lo probe pero no lo pude hacer andar, por temas de los repositorios creo, ya me olvide). De nuevo gracias che. Alla yo

---

### Post by FlyerDie on 2007-09-12
> **faktorqm said:**
> ahh si yo respondi por ahi algo de eso, eras vos?

le digo lo de ntfs por que me parecio ke no tiene muchas intenciones de borrar güindous, y necesitaba una solucion. yo respondi lo que pregunto, o sea, ya sabemos cual es "EL CAMINO", pero si quiere usar güindous.................... alla el!!
:lolflag: cada uno con su pc hace lo que quiere! salu2!!


jejej si...soy yo!:lolflag:
Pero sigo con el mismo quilombo...le tendre que tener fe al 7.10?:confused:

---

### Post by AnRa on 2007-09-12
Podés usar un cliente diferente en cada SO,  lo que tenés que tener en cuenta es la forma en la que almacenan las descargas. ;)

---

### Post by faktorqm on 2007-09-13
flyer: yo no kiero ponerme la gorra, pero el problema es que no liberan las instrucciones en assembler, por lo tanto yo creo que lo que hicieron hasta ahora es una proeza si ya suena. el tema del jack sensing esta volviendo loco a mas de uno, creeme. pasa muy principalmente con alc883 y alc888.
Ojala se solucione el tema en la nueva. 
yo ahora toy mirando de comprarme un quad fx (es una manera de decir) y si no existe una mother con chipset nvidia, no la compro. chipset via, NUNCA MAS. tengo en el laburo y el video es imposible, y trae otros problemas tambien. chipsets intel, nvidia, hasta ahora no reportaron problemas. y yo quiero usar GNU/Linux, no quiero quemarme la VISTA. ajjajajaja salu2!!

---

