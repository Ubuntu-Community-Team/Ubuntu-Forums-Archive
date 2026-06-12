---
title: "Disco rígido"
date: 2007-09-24
forum: Argentina Team
---

### Post by faktorqm on 2007-09-24
Hola a todos, me quiero comprar un disco de 320gb sata 2 seagate barracuda, es la decima generacion (7200.10) y la verdad es que me encanta.
paso a explicar un poco, yo ahora tengo 2 de 160gb y 2 de 80gb (tambien seagate barracuda 7200 pero IDE, o mejor dicho PATA) y como antes tenia windows, en uno de los de 160 quedo una particion de 120gb formateada a ntfs con clusters de 4096 (por que total es para mp3 tonces necesito clusters grandes) y otra fat32. en el otro de 160gb tengo 4 particiones en total, 1 ntfs, 2 (o una no recuerdo) fat32, 1 ext3 y otra swap. En el otro de 80 tengo una sola ntfs tambien de 4096 y en el otro de 80 tengo 2, una ext3 de 75 maso y el resto swap.

La pregunta es, si yo me compro el de 320, el plan es hacer muchas particiones, pero... ¿sigo con el problema del limite en el numero de las particiones?
si, si, ya se que para solucionar eso se invento la extendida, pero manteniendo todas las particiones primarias, hasta cuantas le puedo dar?

o sea, sino, no hay problema, gasto un poco mas :( y me compro 2 de 160gb sata2 con toda la bola. si hago esto capaz me mejora mas el rendimiento, o me quede en la prehistoria? ahora traen ncq y PR los discos.... bueno no se, yo lo decia por el tiempo de reaccion. 
NOTA: la mother que tengo en vista tiene soporte para 12 sata 2 asi que si tengo que comprar 10 discos o 2 para mi es lo mismo.

ultima pregunta: en ext3 importa lo que vendria a ser el tamaño del cluster en ntfs? como se setea esto si es que existe? o existe otro tipo de fs que desconozco para almacenar info digamos?

POR FAVOR les ruego que contesten a cada pregunta por separado, por que capaz surgen mas preguntas a partir de sus respuestas, o alguien que no sabe aprende. DESDE YA muchas muchas gracias por todo ^_^

---

### Post by faktorqm on 2007-09-25
hola, aca encontre buena info

[http://www.win.tue.nl/~aeb/partitions/partition_types.html#toc2](http://www.win.tue.nl/~aeb/partitions/partition_types.html#toc2)

esta en ingles, basicamente, el mbr banca hasta 4 entradas, o sea que solo puedo tener 4 primarias, o como maximo 8 en total, PERO con una extendida digamos que a su vez contenga al resto. igual no recomiendo.
la especificacion ATA-6 usa 48bytes para el descriptor, lo cual soporta hasta 160gb. supongo que esto ya es viejo igual. la ata-5 soportaba hasta 127gb no más. (suena lógico, 128 es potencia de 2, no se olviden del 0 ;))

aca esta en la wikipedia en castellano:

[http://es.wikipedia.org/wiki/Master_Boot_Record](http://es.wikipedia.org/wiki/Master_Boot_Record)

aca encontre buena info pero para principiantes digamos, esta en casetllano:

[http://wiki.gleducar.org.ar/wiki/DAEP_Dispositivos,_Sistema_de_archivos_Linux,_Herencia_est%C3%A1ndar](http://wiki.gleducar.org.ar/wiki/DAEP_Dispositivos,_Sistema_de_archivos_Linux,_Herencia_est%C3%A1ndar)

bueno si encuentro la solucion despues edito. salu2!!!!!!!!!

---

