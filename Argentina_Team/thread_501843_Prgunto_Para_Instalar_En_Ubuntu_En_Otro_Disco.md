---
title: "Prgunto Para Instalar En Ubuntu En Otro Disco"
date: 2007-07-15
forum: Argentina Team
---

### Post by josedamico on 2007-07-15
Amigos, soy nuevo en esto. Estoy por instalar ubuntu. Les cuento la situación , para que me ayuden.
Tengo dos discos:
1 . SATA, de 160 gigas con winXp en NTFS
2 (esclavo) IDE, de 80 gigas

En el esclavo tengo instalado knoppix en una partición reiserf (algo asi n?) de 8 gigas, el resto es una particion FAT 32.

Quisiera instalar ubuntu en la particion en la que está knoppix y hacer volar a knoppix.

Preguntas:
en las opciones de instalacion ubuntu me tira varias opciones (instalar en todo el disco, instalar en el espacio libre, y por ultimo formatear).

Mi intención no es, creo , ninguna de las tres, ya que la primera me haría volar XP del disco C. Y lo mismo la segunda, me haria meterlo en el C y no es mi intención.

Repito, mi intención es que "pise" a knoppix en esa particiòn.

¿como lo hago? ¿que opcion elijo?
ademas
es suficiente esos 8 gigas? No tengo demasiada idea de darle un nuevo formato a swap etc...
Por favor, lo mas detallado posible lo voy a agradecer.

Gracias
José Luis

---

### Post by scrooge_74 on 2007-07-16
cuando tengas el Live CD corriendo y le digas que instale, primero reparticionas manualmente tus discos.  No tocas el que tiene XP, pero el otro lo puedes re-hacer al gusto (de preferencia haces que tu swap  y tu /home estén en particiones separadas del resto del sistema aunque todo esté en el mismo disco)

Por lo menos tienes que darle 10 GB mínimo al sistema de Ubuntu + tu particion separada para /home y para tu swap le das el doble (mínimo) del RAM que tengas.

Cuando termines de particionar y llegue el momento de instalar, le dices al sistema que instale en ese disco y no toque el que tiene XP (cuando mucho que te cree enlaces y puedas leer el disco desde Ubuntu)

Luego te va a decir que va a instalar GRUB en el primer disco (eso está bien), lo necesitas para que tengas la opción de usar XP o Ubuntu.

Y eso es todo, cualquier pregunta tira de vuelta y alguien responderá

---

### Post by josedamico on 2007-07-16
Con respecto al Grub ¿es posible no instalarlo en el MBR? Esto es  porque he visto que en algunas instalaciones (lo lei en algunos foros) el Grub no siempre da bien en la tecla para que se botee los dos sistemas.
Yo tengo instalado el knoppix y en la instalación me pregunto dónde instalar el grub , si en el bot maestro en el disco raiz. Cuando le dije en el disco raíz, me creó un disco de inicio que metia el grub en un disquete. Asi las cosas boteo desde el disquete y desde alli puedo elegir con qué sistema operativo trabajar sin ningun problema. ¿Que opinan de esto?¿se puede en Ubuntu? Repito. he visto en varios foros que mucha gente tuvo lios con grub.
Gracias

---

### Post by scrooge_74 on 2007-07-16
Puedes instalar el grub en un floppy y arrancar desde allí, yo la verdad tengo dos laptops con dual boot y grub está en el mbr y no he tenido mayor problema bastante gente usa esta configuración sin mayor problema.

En caso tal que sufrieras un daño con el mbr, con tu cd de XP usas la herramienta de reparación y el XP arranca otra vez y luego con un Live CD arreglas grub y continuas sin mayor problema.

---

### Post by josedamico on 2007-07-16
bien!!! esa es la opción que quisiera utilizar ¿ubuntu da esa opción en la instalción de cargar el grub en un floppy? Knoppix si la da, por eso pregunto..GRACIAS

---

