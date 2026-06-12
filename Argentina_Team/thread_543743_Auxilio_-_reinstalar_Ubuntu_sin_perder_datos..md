---
title: "Auxilio - reinstalar Ubuntu sin perder datos."
date: 2007-09-05
forum: Argentina Team
---

### Post by djthree on 2007-09-05
Antes que nada,  es posible copiar la carpeta /home a una particion FAT32 para reinstalar ubuntu y luego "levantarla" desde la FAT32?
se puede usar el livecd para esto?
gracias.!

Hola,

En breve resumen, me puse a jugar con los drivers ndvidia para hacer andar la TV conectada a la placa, lo logré, pero despues deje algo mal 
configurado y empece a tener problemas ya que no podia usar una resolucion más alta que 1024x768 yo generalmente uso 1280x1024 con 
monitor lcd 19" --- la cuestion es que empece a toquetear y decidi instalar ENVY.

luego, siguiendo un tutorial de la pagina de ENVY, agregue al source.list los siguientes repositorios:

deb [http://ftp.it.debian.org/debian/](http://ftp.it.debian.org/debian/) etch main
deb-src [http://ftp.it.debian.org/debian/](http://ftp.it.debian.org/debian/) etch main

deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib
deb-src [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib

Despues de esto, me aparecio el icono de "actualizaciones disponibles" y tenia 148 actualizacion para instalar, me pareció raro, pero me mande 
y las actualice todas, algunas me pregunto si queria conservar la version anterior, actualizar o ver los cambios, yo le di a todoas la opcion por 
defecto que era "N" dejar la version por defecto.

Cuando reinicie la PC, despues de dar una plia de mensajes en formato texto de un montonaso de cambios en la configuracion, errores, etc, se 
abre ventana de ingreso y al intentar loguearme, inicia el proceso para abrir el escritorio GNOME y se cuelga.

HAY LAGUNA MANERA DE VOLVER A UNA INSTANCIA ANTERIOR A ESTE DESASTRE QUE ME MANDE????

GRACIAS espero sus novedades!

---

### Post by por100pre1 on 2007-09-05
En la condicion en que esta tu PC... si, puedes usar el live CD para copiar tu carpeta de usuario y reponerla luego. No importa lo que diga en ninguna pagina, los repositorios de Debian y de Ubuntu no se mezclan.

---

### Post by msangil on 2007-09-06
Kcs djthree,

Yo me mandé una parecida hace un par de días. Creo que no podés escribir en la partición FAT32 desde ubuntu. Lo que deberías hacer capaz es copiarte desde el live cd tu carpeta personal a un iPod o lo que tengas a mano para hacer tu backup.

Vas a ver que cuando corrés con el live cd es probable que haya carpetas que no te deje ni leer porque diga que no tenés los permisos adecuados. Hay un comando para cambiar eso...

(no me lo acuerdo - a ver si alguno de los más experimentados tira la línea acá please).

Una vez que tirás el comando ya te deja hacer lo que quieras.

Ya probaste con "sudo dpkg-reconfigure xserver-org" antes de decidir formatear?

EDIT: no, pará... re-leí recién lo de los errores que pusiste. Si, mejor formatear de una. Capaz te queda medio renga si no.

---

### Post by FlyerDie on 2007-09-07
> **msangil said:**
> 
Vas a ver que cuando corrés con el live cd es probable que haya carpetas que no te deje ni leer porque diga que no tenés los permisos adecuados. Hay un comando para cambiar eso...

(no me lo acuerdo - a ver si alguno de los más experimentados tira la línea acá please).

Una vez que tirás el comando ya te deja hacer lo que quieras.


chown ? 
o su - ? 
El "su -" es para ingresar como root.
y el "chown" es para cambiar el dueño usuario:grupo de un directorio o archivo.

---

### Post by djthree on 2007-09-07
Hola, 
Gracias a todos.
les cuento lo que hice:
ingrese con una version LiveCD de SLAX, que entra ultra-rapida, y copie la carpeta .HOME a la particion FAT32 que usaba para intercambiar datos entre ubuntu y win....
hasta ahi todo OK.
Luego intente ingresar con el LIVECD de Ubuntu y me paso lo que pasaba al prinicio NO PUEDO CORRER LA INSTALCION SIN ERRORES: DE LECTURA.. se me cuelga.
A mi me costo mucho  instalar ubuntu y dedpues hacer andar mi modem USB AMIGO....
asi que debido a esto, me calente y con un live cd de gparted voletie la partticion swap y la ext3. y uni todo a la particion de datos...
RESULTADO 1: 2 particion, win NTFS y datos FAT32.
RESULTADO 2: se me **** el GRUB.

Asi que por ahora voy a volver a windows unas semanas, hasta que me agarre ganas de nuevo  y vuelvo a la carga con ubuntu de nuevo.
la verdad es que extraño a AMAROK.

Saludos!

---

### Post by FlyerDie on 2007-09-07
> **djthree said:**
> Hola, 
Gracias a todos.
les cuento lo que hice:
ingrese con una version LiveCD de SLAX, que entra ultra-rapida, y copie la carpeta .HOME a la particion FAT32 que usaba para intercambiar datos entre ubuntu y win....
hasta ahi todo OK.
Luego intente ingresar con el LIVECD de Ubuntu y me paso lo que pasaba al prinicio NO PUEDO CORRER LA INSTALCION SIN ERRORES: DE LECTURA.. se me cuelga.
A mi me costo mucho  instalar ubuntu y dedpues hacer andar mi modem USB AMIGO....
asi que debido a esto, me calente y con un live cd de gparted voletie la partticion swap y la ext3. y uni todo a la particion de datos...
RESULTADO 1: 2 particion, win NTFS y datos FAT32.
RESULTADO 2: se me **** el GRUB.

Asi que por ahora voy a volver a windows unas semanas, hasta que me agarre ganas de nuevo  y vuelvo a la carga con ubuntu de nuevo.
la verdad es que extraño a AMAROK.

Saludos!

Los errores de lectura los tenes sobre el LiveCD? entonces esta mala la imagen que estas utilizando, le corriste MD5 para ver si te da checksum correcto el ISO?
Yo no me tiraria atras por una huevada asi ;)

---

### Post by alfredo_cba on 2007-09-07
> **msangil said:**
>  Creo que no podés escribir en la partición FAT32 desde ubuntu. 
si se puede con **Automatix read/write NTFS and FAT32 mounter**

---

### Post by ivanrengo on 2007-09-12
[SIZE="1"]Quote:
Originally Posted by msangil View Post
Creo que no podés escribir en la partición FAT32 desde ubuntu.
si se puede con Automatix read/write NTFS and FAT32 mounter[/SIZE]

Estan confundiendo algunas cositas...

Las particiones con FAT32 no necesita ningún complemento para poder copiar archivos en ellas. Las particiones con NTFS necesitan del driver 3g para poder escribir en ellas y eso es lo que te instala el Automatix de una manera tan sencilla :)

Con respecto al problema del sistema en general yo en tu lugar reinstalaría todo de nuevo porque quien te puede asegurar que quede todo bien configurado luego del desastre que se produjo??

Saludos

---

### Post by djthree on 2007-09-12
Hola!
Bueno, todavia no volvi a Ubuntu , pero les cuento que pronto lo haré.... la verdad es que la flexibilidad de Ubuntu tanto en GNOME como en KDE y tambien con FLUXBOX es excelente, ahora que estoy usando windows xp me doy cuenta la cantidad de cosas que en ubuntu se pueden "customizar" y ni hablar de AMAROK, excelente aplicación de música!!!
Tambien las aplicaciones para ripear DVD y para ver peliculas, son mucho mejores que el windows media player!!!!
Bueh.. 
Les cuento que baje dos veces las imagenes tanto de Kubuntu y Ubuntu y las chequeee con MD5 y estan ok, sin embargo la unica manera de poder ingresar con el LiveCd para instalar es poniendo un par de parametros que desconectan el ACPI y creo tambien el DMA de mi lectora, ya que si no, da errores. he visto que la instalacion de SuSe viene con una opcion especial para arrancar en ese modo, intuyo que debe ser porque muchos deben tener el miismo  problema.
 
Es verdad lo que dice "ivanrengo" , corriendo el livecd de ubuntu tranquilamente podes escribir en particiones FAT32.

Saludos y hasta pronto!

---

