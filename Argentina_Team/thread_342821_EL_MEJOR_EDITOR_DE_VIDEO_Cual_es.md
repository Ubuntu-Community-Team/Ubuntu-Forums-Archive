---
title: "EL MEJOR EDITOR DE VIDEO Cual es?"
date: 2007-01-20
forum: Argentina Team
---

### Post by jpoeta on 2007-01-20
Amigo del LOCO TEAM quiera que me recomienden un buen editor de video.
Que soporte Formatos como AVI, MPEG, yq ue me de una gran variedad de efectos.
Cual es el mejor apelo a s u sabiduria y experiencia
Quiero hacer Un VCD de OASIS:guitar: :guitar:

---

### Post by Mike_Longbow on 2007-01-20
Avidemux es bueno, puedes hacer muchas cosas con él...
[http://avidemux.sourceforge.net/]("http://avidemux.sourceforge.net/")
Si quieres instalarlo sólo haz:
```
sudo apt-get install avidemux
```

---

### Post by Piti on 2007-01-20
Ese avidemux parece interesante, pero creo que necesitarias algo mas al estilo Adobe Premiere / Sony Vegas, no? Digo, para tener transiciones y todo eso.

En linux nunca edité video, pero algunos programas que por ahi te sirvan son [Cinelerra]("http://heroinewarrior.com/cinelerra.php3"), [Jahshaka]("http://www.jahshaka.org/"), [kdenlive]("http://kdenlive.sourceforge.net/index.php"), [Kino]("http://kinodv.org/") y [LiVES]("http://lives.sourceforge.net/index.php?do=home").

No los use nunca como para saber cual es bueno o no, por ahi si alguien los uso puede comentar algo.

---

### Post by jpoeta on 2007-01-20
como instalo? Jahshaka? 
como instalo? cinelerra?

por favor no soy tan bueno en las instalaciones ayudenme !!!

Gracias por las respuestas.

Quiero hacer un super video necesito los mejores pregramas gracias!!!!:rolleyes:

---

### Post by felipelerena on 2007-01-21
avidemux es fantastico, se zarpa

---

### Post by jpoeta on 2007-01-21
AYUDENME CON JAHSHAKAAAAAAAAAAAA:lolflag:

---

### Post by Mike_Longbow on 2007-01-22
Ok, si tanto quieres usar Jashaka, te explicaré como instalarlo... Aunque el instalador que viene el página de Jashaka esta diseñado para Dapper... no te aseguro que funcione en Edgy
Bien, para empezar descarga el instalador de [aquí]("http://sourceforge.net/project/downloading.php?groupname=jahshaka&filename=jahshaka-dapper-x86.sh&use_mirror=superb-west").
Guárdalo en tu carpeta personal (/home/<nombre-del-usuario>)
Ahora abre una terminal y teclea:
```
sh ~/jashaka-dapper-x86.sh
```
Se abrirá una ventana de bienvenida, selecciona "yes" y escribe tu password.
Al final el instalador te preguntara si quieres instalar iconos en el escritorio, selecciona una opción ylisto.

---

### Post by jpoeta on 2007-01-22
gracias amigo mike pero no funciono:frown:

---

### Post by beuno on 2007-01-22
> **jpoeta said:**
> gracias amigo mike pero no funciono:frown:

Generalmente ayuda si das más información.

¿Qué pasó?
¿Qué error está tirando?

---

### Post by jpoeta on 2007-01-22
jpoeta@jpoeta-desktop:~$ sh ~/jashaka-dapper-x86.sh
sh: Can't open /home/jpoeta/jashaka-dapper-x86.sh
jpoeta@jpoeta-desktop:~$ sh ~/jahshaka-dapper-x86.sh
/home/jpoeta/jahshaka-dapper-x86.sh: 3: Syntax error: "(" unexpected
jpoeta@jpoeta-desktop:~$ sudo sh ~/jahshaka-dapper-x86.sh
Password:
/home/jpoeta/jahshaka-dapper-x86.sh: 3: Syntax error: "(" unexpected

---

### Post by beuno on 2007-01-22
> **jpoeta said:**
> jpoeta@jpoeta-desktop:~$ sh ~/jashaka-dapper-x86.sh
sh: Can't open /home/jpoeta/jashaka-dapper-x86.sh
jpoeta@jpoeta-desktop:~$ sh ~/jahshaka-dapper-x86.sh
/home/jpoeta/jahshaka-dapper-x86.sh: 3: Syntax error: "(" unexpected
jpoeta@jpoeta-desktop:~$ sudo sh ~/jahshaka-dapper-x86.sh
Password:
/home/jpoeta/jahshaka-dapper-x86.sh: 3: Syntax error: "(" unexpected

Parece que tenes un error en el archivo.

¿Lo bajaste bien?

Subilo aca si podes.

---

### Post by jpoeta on 2007-01-22
Lo volvi a bajar y lo volvi a intentar dio el mismo error de aqui lo baje

[http://sourceforge.net/project/downloading.php?groupname=jahshaka&filename=jahshaka-dapper-x86.sh&use_mirror=superb-west](http://sourceforge.net/project/downloading.php?groupname=jahshaka&filename=jahshaka-dapper-x86.sh&use_mirror=superb-west)

GRACIAS POR LA AYUDA

---

### Post by beuno on 2007-01-22
> **jpoeta said:**
> Lo volvi a bajar y lo volvi a intentar dio el mismo error de aqui lo baje

[http://sourceforge.net/project/downloading.php?groupname=jahshaka&filename=jahshaka-dapper-x86.sh&use_mirror=superb-west](http://sourceforge.net/project/downloading.php?groupname=jahshaka&filename=jahshaka-dapper-x86.sh&use_mirror=superb-west)

GRACIAS POR LA AYUDA

El archivo esta mal.
No se en que lenguaje se supone que esta hecho, pero bash no es seguro...

---

### Post by jpoeta on 2007-01-22
alguien podria ayudarme a instalarlo=? darme otro enlace¿? o un paquete deb??

POR FAVOR No quiero volver a WINDOWS:roll:

---

### Post by Piti on 2007-01-22
Aca [http://www.getdeb.net/category.php?id=27&release=Edgy]("http://www.getdeb.net/category.php?id=27&release=Edgy") tenes un .deb para LiVES, por ahi podes probar ese a ver si te sirve.

---

### Post by gdgardnerw on 2007-03-24
He intentado instalar jahshaka y también he experimentado algo de problemas, aunque de naturaleza diferente. A continuación aparece lo que me pasa y no lo entiendo porque no hablo Linux:

gdgardnerw@dad:~$ sh -/jahshaka-dapper-x86.sh
sh: -/: invalid option
Usage:  sh [GNU long option] [option] ...
        sh [GNU long option] [option] script-file ...
GNU long options:
        --debug
        --debugger
        --dump-po-strings
        --dump-strings
        --help
        --init-file
        --login
        --noediting
        --noprofile
        --norc
        --posix
        --protected
        --rcfile
        --restricted
        --verbose
        --version
        --wordexp
Shell options:
        -irsD or -c command or -O shopt_option          (invocation only)
        -abefhkmnptuvxBCHP or -o option

¿Hay alguien que me puede ayudar con eso?

---

### Post by jpmorelli on 2007-03-27
No será que no le diste permisos suficientes al archivo para correrlo ?
Tal vez se instale con el comando poniendo el sudo adelante o tal vez tengas que darle permisos de ejecución al que bajaste ( chmod 755 )

---

### Post by felipelerena on 2007-03-27
por que no probas con avidemux?

---

### Post by kowal on 2007-03-28
Avidemux es bastante útil

---

### Post by valucha on 2007-03-28
[COLOR="DarkOrchid"]Pero jahshaka es más gráfico :) [/COLOR]

---

### Post by LuisAugusto on 2007-08-02
Me pregunto yo porque nadie le dice como instalar cinelerra...

si tienes: i586

```
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/ ./
```

si tienes Pentium 4:

```
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/ ./
```

Agrégalos con synaptic.

---

### Post by juanman on 2007-08-02
Alguien sabe como instalar cinelerra en kubuntu 7.04 64b. Instale todas las dependencias y compile pero me falla el make. 
Me tira este error:
#luego de varias cosas antes
/usr/bin/ld: ffmpeg/libavcodec/.libs/libavcodec.a(cputest.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
ffmpeg/libavcodec/.libs/libavcodec.a(cputest.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libquicktimehv.la] Error 1
make[3]: Leaving directory `/media/datos/cinelerra/cinelerra-2.1/hvirtual/quicktime'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/media/datos/cinelerra/cinelerra-2.1/hvirtual/quicktime'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/datos/cinelerra/cinelerra-2.1/hvirtual'
make: *** [all] Error 2

Me dice q recompile con -fPIC pero Q? y como lo hago? edito el makefile?

No hay algun .deb? Probe los de i386 con dpkg -i --force-architecture pero no funca... Aparte este es un programa en el q se aprovechan los 64 bits...

---

### Post by marianom on 2007-08-02
La última vez que me tuve que meter con el -fPIC, abrí el archivo Makefile del programa que intentaba compilar y busqué 
```
EXTRACFLAGS=
```
Ahí el agregué el -fPIC, grabé y reintente con rotundo éxito.

---

### Post by Ark_74 on 2007-10-16
Pero chicos, con respecto al Jahshaka, por que tanto problema, simplemente agregen el repositorio que contiene el documento .sh, a los repositorios de Ubuntu y listo.

```
deb http://repo.jahshaka.org/ubuntu/dapper/ binary-i386/

```

Usan synaptic, linea de comandos o lo que gusten para  instalarlos.

Saludos a todos.

---

### Post by LuisAugusto on 2007-10-16
Jahshaka es una aplicación bastante de calidad media tirando a baja, lo que tienen es un website bonito y una GUI atractiva, pero hazte a la idea han decido re-escribir el programa por su ridícula estabilidad.

Cinelerra para 64 bits (AMD):

```
deb http://giss.tv/~vale/debian64 ./
deb http://giss.tv/~vale/ubuntu64 ./
```

---

### Post by el_itur on 2007-10-17
> **jpoeta said:**
> jpoeta@jpoeta-desktop:~$ sh ~/jashaka-dapper-x86.sh
sh: Can't open /home/jpoeta/jashaka-dapper-x86.sh
jpoeta@jpoeta-desktop:~$ sh ~/jahshaka-dapper-x86.sh
/home/jpoeta/jahshaka-dapper-x86.sh: 3: Syntax error: "(" unexpected
jpoeta@jpoeta-desktop:~$ sudo sh ~/jahshaka-dapper-x86.sh
Password:
/home/jpoeta/jahshaka-dapper-x86.sh: 3: Syntax error: "(" unexpected
Vi luz y entré, parece que paso bastante agua por el puente. Ese error tiene toda la pinta de que esté relacionado al interprete de bash de ubuntu. Ubuntu usa dash por defecto en vez de bash.
$ sudo dpkg-reconfigure bash
y seleccionar bash tiene que corregirlo.
Una vez instalado podes setear dash nuevamente
si no funciona probá sacando el sh ~/ y corriendo directamente ./jashaka-dapper-x86.sh

BTW. Jashaka es una ve***. no hay editores copados en linux, slavo los de pago. Main Actor, Combustion Fire y Combustion Smoke.

Si querés hacer cosas simples tipo vlog o esas historias te recomiendo mucho pitivi o avidemux como ya han hecho otros.

---

### Post by juanman on 2007-10-17
Q bueno q halla paquetes para 64bits!
Al final instale el cinelerra en un chroot de 32bits...
Un editor de video simple q promete es el [OpenMovieEditor]("http://openmovieeditor.sourceforge.net/HomePage")

---

### Post by h9005 on 2008-01-23
En open movie editor no puedo editar el video con audio, se importa solo el video. tampoco se como hacer para agregar transiciones.

---

### Post by anubis4d on 2008-04-21
las transiciones en Open Movie Editor se logran superponiendo clips, entonces el área de superposición se vuelve un fundido entre ambas.
si usás un PNG totalmente transparente y lo superponés a la salida del vídeo lográs un buen fade-to-transparente, aunque por algun bug, no funciona como fade in.
estoy en un proyecto para generar efectos, plantillas de texto SVG, y distorsiones UV para OME en mi blog:
[http://gvfx.blogspot.com/](http://gvfx.blogspot.com/)

en los foros de OME me la paso pidiendo features, visítenlos y vean los avances de ome.
[IMG]http://i242.photobucket.com/albums/ff260/mdpsistemas/gvfx/fade.jpg[/IMG]

Como siempre le digo a richard, el mejor soft no es el del codigo mñas fuerte sino el que deja que los usuarios lo modifiquen y expandan.como prueba, te cuento que OMe no tiene Chromakey, pero yo se lo FABRIQUE con nodos:
[IMG]http://i242.photobucket.com/albums/ff260/mdpsistemas/gvfx/chromakey-greenscreen.jpg[/IMG]

un saludo amigo

Marquitux de Argentina. 
PD: también podés visitar si querés ver algunas experiencias que he realizado con nodos:
[http://www.niel3d.com/niel2/modules/newbb/viewtopic.php?topic_id=2579&post_id=24381#forumpost24381](http://www.niel3d.com/niel2/modules/newbb/viewtopic.php?topic_id=2579&post_id=24381#forumpost24381)
[http://www.openmovieeditor.org/board/viewtopic.php?id=832](http://www.openmovieeditor.org/board/viewtopic.php?id=832)
[http://www.openmovieeditor.org/board/viewtopic.php?id=803](http://www.openmovieeditor.org/board/viewtopic.php?id=803)

---

### Post by anubis4d on 2008-04-22
Sable laser hecho en Open Movie Editor
[IMG]http://i242.photobucket.com/albums/ff260/mdpsistemas/gvfx/LIGHTSABER.jpg[/IMG]

vean e video
[http://www.youtube.com/watch?v=ocXm3kc1oRw](http://www.youtube.com/watch?v=ocXm3kc1oRw)

Marquitux

---

