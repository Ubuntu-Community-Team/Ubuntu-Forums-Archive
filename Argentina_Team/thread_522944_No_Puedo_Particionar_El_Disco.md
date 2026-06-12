---
title: "No Puedo Particionar El Disco"
date: 2007-08-11
forum: Argentina Team
---

### Post by marcesneibrun on 2007-08-11
HOLA A TODOS ME BAJE EL LIVE CD DESDE INTERNET, LO PROBE EN MI OLIVETTI 710-430 VSE, ME GUSTO ENTONCES ESTABA DECIDIDO A INSTALARLO. TENGO EL WINDOWS VISTA STARTERQ VINO POR DEFECTO, TRATE PRIMERO DE HACER LA PARTICION CON EL G-PARTED,ME DECIA Q EN MI DISCO ESTABA USADO 18 GB QUEDANDO LIBRE 62 GB.PUSE REDIMENSIONAR DANDOLE 10GB A UBUNTU Y ME TIRA ERROR NO ME PERMITE HACERLO .
AHORA EN LA VENTANA ME APARECE /DEV/SD1 o SDA NO ME APARECE HD1 SERA ESTE ES EL PROBLEMA?
PERDONEN MI IGNORANCIA Y AGRADEZCO AYUDA
GRACIAS
MARCELO

---

### Post by facundocorradini on 2007-08-11
> AHORA EN LA VENTANA ME APARECE /DEV/SD1 o SDA NO ME APARECE HD1 SERA ESTE ES EL PROBLEMA?

No, ese no es el problema.. de hecho a mi me ocurrió lo mismo,. Pero eso no causa ningún problema. Es solo un cambio en la denominación en los nuevos kernels, que marcan como SDx los discos SATA y algunos IDE(no estoy bien seguro del criterio que utiliza)

En cuanto al problema para particionar, muy probablemente se deba a una protección propia de windows vista; sé que mi hermano tuvo el mismo inconveniente cuando borró el vista de su máquina para poner solo ubuntu... Le voy a preguntar a ver si me guía un poco en el tema...

(por cierto, te da error de que "no puede redimensionar" o algún otro error?)

---

### Post by marcesneibrun on 2007-08-11
hola ante todo gracias por tu respuesta, me dá error cunado quiero redimensionar, me dice q va a comenzar con las aplicaciones y me tira error como q no puedo redimensionarlo al disco.
gracias 
marcelo

---

### Post by lmaruiz on 2007-08-12
Hace poco cambie de PC y no tuve ningun problema con GParted, todo lo contrario, me parece una herramienta excelente.
Probaste desframengtar el disco desde vista antes de reparticionar?
A mi me aparecen un par de particiones muy chicas al principio y al final del disco, que no toque, por que no se si tiene algun significado para vista (y no molestan por su tamaño).
Yo compre en Garbarino (por una cuestion de conveniencia de precios; siempre recomiendo casas dedicadas solo a computacion), y estaba tentado con las notebooks de Olivetti.
Si compraste ahi es casi seguro que el esquema de particionado del disco sea similar. Si te interesa conservar vista, asegurate de no tocar la particion desde donde podes reinstalarlo (se llama "recupero" en mi pc).
En mi caso deje dos particiones para windows, la final de recuperacio/instalacion, y para Ubuntu una logica que contiene dos mas: raiz y swap.
Si continuas con problemas trata de detallar mas cada paso y los mensajes de error que ves.

---

### Post by faktorqm on 2007-08-13
Hola, Windows Vista no debería interferir en ningún aspecto con el particionado del disco rígido. Si tenés problemas con el Gparted, bajate el Norton Partition Magic 10 que trae soporte para Vista y desde ahí lo hacés a mano y desde windows. Sino sabés como se hace posteá. Salu2!!!

Off topic: ¿Vista starter edition? por favor muchachos! un poco de amor propio... instalen la profesional, enterprise o como se llame!!!!! esa version es una ******.

---

### Post by marcesneibrun on 2007-08-13
Graciasssssssssssssssssssss
Pude Particionar Con El Gparted, Cuando Me Conecte A Internet, No Se Si Tendra Q Ver O No Pero Pude Hacerlo
Estoy Muy Contento, Les Agradezco A Todos.
Lo Q No Puedo Es Ver Peliculas Dvd Con El Totem, Dice Q Me Faltan Controladores , Y Ya Instale Desde El Synaptic Gstreamer 0.8, Cual Es El Mejor Reproductor Para Dvd Para Ver Todas Las Pelis?? O Que Me Falta Instalar??
Gracias 
Marcelo

---

### Post by faktorqm on 2007-08-13
Te aconsejo que instales automatix2 para todo lo que es codecs y algunos programas mas. Te evita miles de dolores de cabeza y en el tema codec exclusivamente es lo mejor que existe. 

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Ojala te sirva. ahh y no tiene nada que ver, pero absolutamente nada que ver que te hayas conectado a internet con el tema de las particiones. Que haya funcionado en paralelo a eso es una mera casualidad. Salu2!!

---

### Post by Hei Ku on 2007-08-13
Lo que te falta son los codecs para ver DVDs, y probablemente los de mp3, etc. que no vienen instalados por defecto. Busca en wiki.ubuntu.com por restricted drivers

Yo te recomendaria que no uses el automatix. El modo en que actualiza los paquetes no es algo recomendable, sobre todo para algo tan simple como los codecs de dvd.

---

### Post by facundocorradini on 2007-08-13
vamos gente... no hagan complicadas las cosas que no lo son....

para leer un mp3, basta con tratar de abrirlo, y ubuntu se encarga solo de preguntarte si querés instalar los codecs...

---

### Post by faktorqm on 2007-08-14
no se, a mi no me pregunto nada, al menos con el xmms. como no lo podia reproducir, baje los codecs desde el automatix, que me parecio lo mas comodo, lo menos complicado, lo mas rapido y lo mas principiante supported posible. No solo eso, me reproduce cualquier tipo de video, sonido o contenedor multimedia que tenga, hasta ahora no me dio ningun problema. Salu2!

---

