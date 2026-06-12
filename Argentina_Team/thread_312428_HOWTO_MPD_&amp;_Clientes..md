---
title: "HOWTO: MPD &amp; Clientes."
date: 2006-12-04
forum: Argentina Team
---

### Post by JMO707 on 2006-12-04
Hace tiempo que quiero hacer una guía sobre como tener lo último de este maravilloso daemon, así que hoy va =)

[I]**Music Player [Daemon]("http://en.wikipedia.org/wiki/Daemon_%28computer_software%29") (MPD)** is a music player which allows for remote access from another computer. An example would be a [headless]("http://en.wikipedia.org/wiki/Headless") computer running MPD and using one of the available front ends to control it remotely. It also makes for a good desktop [media player]("http://en.wikipedia.org/wiki/Media_player"), particularly if you either don't use or frequently restart [X]("http://en.wikipedia.org/wiki/X_Window_System").
It utilizes a database (like other music players) to store the basic music file information for each file. Instead of playing files from the filesystem, it plays music from the MPD library. Once the daemon is started, the database is kept entirely in-memory, and there is no disk access necessary to lookup or search for a song. The text file database is only used to maintain the contents of the database when MPD is not running.[/I] [[Wikipedia]("http://en.wikipedia.org/wiki/Music_Player_Daemon")]

Tengan en cuenta, además de esto, que consume escasísimos recursos. En este momento a mi me está llevando 1,9 Mbytes de memoria. Un front-end no añade suficiente para llegar a los 10 Mbytes, y como no lo requiere para reproducir música, se puede programar un playlist y dejarlo corriendo, con lo que podemos mantener esos 1,9 Mbytes.

Creo que el mayor obstáculo que puedo tener para esta guía es la cuestión de las dependencias. Como vamos a instalar 4 programas y varios plug-ins, esto, sumado a que quiero intentar ser neutro con el tema de las distribuciones, puede complicárseme. Pienso extraerlos directamente de las páginas oficiales. Espero sepan disculpar si en dicho aspecto a la guía le falta.

Ahora, lo que vamos a instalar es: MPD, libmpd, ncmpc, gmpc (con: coveramazon, lyrics, wikipedia, last.fm & qosd)

Dejo un screen para que se vea más o menos como es: 

[[IMG]http://img117.imageshack.us/img117/6162/pantallazohd4.th.png[/IMG]]("http://img117.imageshack.us/my.php?image=pantallazohd4.png")

···········

[COLOR=Red]**_MPD (Music Player Daemon)_**[/COLOR]

Vamos a ver primero las dependencias [según el sitio oficial de MPD]("http://www.musicpd.org/install.shtml"):
[I]
** Requirements**
1) [libao]("http://www.xiph.org/ao") libraries and headers are required!
2) [zlib]("http://www.gzip.org/zlib") libraries and headers are required!

Libs included with source (i.e. nothing needed for these): [libid3tag]("http://mad.sf.net/") and [libmad]("http://mad.sf.net/")
Optional
1) for ogg vorbis support: [libogg]("http://www.xiph.org/ogg") and [libvorbis]("http://www.xiph.org/ogg/vorbis")
2) for flac support: [flac]("http://flac.sf.net/") 1.1
3) for wave/aiff/au support: [audiofile]("http://www.68k.org/%7Emichael/audiofile/")
4) for MP4/AAC support: [FAAD2]("http://www.audiocoding.com/")
5) for Mod support: [libmikmod]("http://mikmod.raphnet.net/")[/I]


Probé todos los links, y exceptuando el de *libvorbis* (que se puede encontrar en el link de *libogg*) los demás funcionan bien. Por supuesto que si tienen la posibilidad de utilizar un gestor de paquetes para estas tareas, les va a resultar mucho más sencillo. Eso se da por supuesto de ahora en más.

**Addendum:** Había olvidado que puede ser no todos tengan *svn* instalado. Dejo entonces acá él link a la página oficial: [http://subversion.tigris.org/](http://subversion.tigris.org/)

Una vez que instalamos las dependencias, vamos a descargar MPD del subversion repository:

*svn co [https://svn.musicpd.org/mpd/trunk](https://svn.musicpd.org/mpd/trunk) mpd*

Esto desde una terminal, claro está. A continuación entramos a la carpeta *mpd* recién descargada, y ejecutamos en la terminal:

[I],/autogen.sh
make
sudo make install[/I]

Tres cosas... 
Primero, a la salida de *,/autogen.sh* puede verse con que librerías fue configurado MPD, y por lo tanto para que cosas tiene soporte. Es buena idea fijarse que todo esté en orden antes de continuar.
Segundo, que si puede evitarse hacer *sudo make install* así, system wide, mejor. Si pueden construir un paquete con alguna herramienta, se los recomiendo, y si no siempre pueden usar un prefijo, digamos *sudo make install **&#8211;prefix=/usr/local/*** por ejemplo. Eso les va a permitir ordenar la manera en que se instala. Esto vale para todos los programas que vayamos instalando de ahora en más.
Tercero, por comodidad voy a utilizar mis paths para el resto del tutorial. Cámbienlos según donde lo hayan instalado.

Listo. Ahora tenemos MPD. Pero no termina acá.
Lo que sigue es configurarlo. Empezamos editando con permisos de root el archivo *mpd.conf* que se encuentra en */etc*. Ejemplo: sudo nano /etc/mpd.conf
Van a encontrar cantidad de opciones, pero lo que a nosotros nos interesa es modificar las siguientes:


*pid_file    "/var/run/mpd/pid" *

Comentamos esta linea, poniéndole un # por delante. Esto es porque el archivo pid no es creado con la instalación y si dejamos la linea no vamos a poder iniciar MPD luego. 


[I]#mixer_type    "alsa"
#mixer_device    "default"
#mixer_control    "PCM"  [/I]

Si usan ALSA, recomiendo descomentar estas lineas y cambiar *PCM* por *Master*. Esto va a evitar que cuando subamos demasiado el volumen los parlantes se saturen.


*#filesystem_charset "ISO-8859-1"*

Desconmentamos esta linea y cambiamos *ISO-8859-1* por *UTF-8*, para que al generar la base de datos acepte caracteres especiales.


Eso es lo más esencial creo yo. Espero no estarme olvidando de nada. En cualquier caso, son libres de navegar y probar el archivo después =]

Guardamos los cambios en *mpd.conf*. Luego:

*cd /var/lib/mpd/music/*
*sudo ln -s &#8220;ruta hacia el directorio con nuestra música&#8221;*

Repítanlo con todos los lugares donde tengan su música. Esto crea unos enlaces blandos que permite a MPD tomar los archivos desde varios directorios con música, a diferencia de si lo hubiesemos puesto directamente en el archivo de configuración.
Vale. Todo está listo. Lo último es crear la base de datos, y para eso hacemos:

*sudo mpd &#8211;create-db*

Luego, cuando queramos iniciar MPD solo basta hacer:

*sudo mpd*

Y repetir el comando de creación de la base de datos cada vez que deseemos actualizarla.

···········

[COLOR=DarkOrange]**_libmpd (Librería de MPD)_**[/COLOR]


[Sitio de Qball]("http://sarine.nl/gmpc-compile-svn"):
[I]
**Requirements**
- C99 Compatible C compiler (for example: gcc >= 3.0)
- autotools (automake, autoconf)
- make
- libtool
- Subversion (to fetch a copy) [/I]


Luego descargamos con:

*svn co [https://svn.musicpd.org/libmpd/trunk](https://svn.musicpd.org/libmpd/trunk) libmpd*

Nos dirigimos a la carpeta descargada, y dentro hacemos:
[I]
,/autogen.sh
make
sudo make install[/I]

···········

[COLOR=DarkOrchid]_**NCMPC (Ncurses Music Player Client)**_[/COLOR]


Este es mi cliente favorito =)

[Sitio oficial de MPD]("http://www.musicpd.org/install.shtml"):

[I]**Requirements**
 - [ncurses]("http://www.gnu.org/software/ncurses/")
 - [glib-2]("http://www.gtk.org/")[/I]


Lo descargamos con:

*svn co [https://svn.musicpd.org/ncmpc/branches/tradiaz](https://svn.musicpd.org/ncmpc/branches/tradiaz)*

Esta es una rama de ncmpc diferente de la indicada en el sitio de MPD. Esto se debe a que el desarrollador original aparentemente abandonó el proyecto, y ahora lo continúa otra persona.
Continuamos dentro del directorio recién descargado:

[I],/autogen.sh &#8211;enable-lyrics-screen --enable-clock-screen
make
sudo make install[/I]

Luego pueden acceder desde cualquier terminal tipeando *ncmpc*.
Como tip, pueden añadir a su bashrc (*~/.bashrc*) un alias tipo *alias ncpmc=&#8221;ncmpc &#8211;colors&#8221;*, lo cual va a permitirle usar colores cada vez que lo inicien. Aca dejo un screen.

[[IMG]http://img138.imageshack.us/img138/9206/pantallazo2al9.th.png[/IMG]]("http://img138.imageshack.us/my.php?image=pantallazo2al9.png")

···········

[COLOR=DarkGreen][COLOR=SeaGreen]**_GMPC (Gnome Music Player Client)_**[/COLOR]
[/COLOR]

Este es el front-end para X que vamos a utilizar. Hacia el final de la guía voy a hablar de otra opción, pero opino que este es el más completo que hay.
[URL="http://sarine.nl/gmpc-compile-svn"]
Sitio de Qball[/URL]:

[I]**Requirements**
- C99 Compatible C compiler (for example: gcc >= 3.0) 
- autotools (automake, autoconf) 
- Gtk+-2.8 (and dependencies) 
- libmpd from svn (see above) 
- Gob2 
- libsm 
- libglade 
- Libcurl (version 3)
- intltool 
- make 
- Subversion (te fetch a copy) [/I]

En la terminal:

*svn co [https://svn.musicpd.org/gmpc/trunk/](https://svn.musicpd.org/gmpc/trunk/) gmpc/*

Dentro de la carpeta:

[I],/autogen.sh
make
sudo make install[/I]

---

### Post by JMO707 on 2006-12-04
[COLOR=DeepSkyBlue]_**Plugins de GMPC**_[/COLOR]

Pueden ver todos los plugins disponibles en [https://svn.musicpd.org/gmpc/plugins/](https://svn.musicpd.org/gmpc/plugins/)

Se pueden descargar de la siguiente manera:

* svn co [https://svn.musicpd.org/gmpc/plugins/"nombre"/trunk]("https://svn.musicpd.org/gmpc/plugins/%22nombre%22/trunk")*

Para instalarlos se me complicó un poco, porque empaquetándolos no lo lograba. Así que esto es lo que hice:
[I]
,/autogen.sh
make
sudo make install[/I]

Luego, me dirigía a */usr/local/share/gmpc/share/gmpc/plugins/* y movía el archivo **.so* que se encontraba allí a */usr/local/share/gmpc/plugins*. En cualquier caso esto es para una instalación global del plugin. Para instalarlo localmente se debería mover a *~/.gmpc/plugins/*

Por lo demás, yo tengo instalado: 

** coveramazon **---> toma las tapa de los álbumes de Amazon para mostrarlas.

** last.fm** ---> lo mismo pero con fotos de los músicos, y me parece que también funciona enviando información a last.fm sobre los hábitos de escucha.

** lyrics** ---> para poder descargar las letras de LeosLyrics y LyricsTracker.

** wikipedia** ---> habilita una pestaña que busca información del músico o agrupación en Wikipedia (en inglés)

** qosd **---> permite advertir sobre el tema que se está reproduciendo en un display con transparencias.

···········

Finalmente les comento que existe una alternativa a GMPC muy grata. Es Sonata, un cliente muy bien trabajado y con la particularidad de no utilizar ningún menú o barra de herramientas.
 La página oficial es [http://sonata.berlios.de/](http://sonata.berlios.de/) y la forma de descargarse la última versión e instalarla es:


  *svn co [http://svn.berlios.de/svnroot/repos/sonata/trunk](http://svn.berlios.de/svnroot/repos/sonata/trunk) sonata*


 Entramos a la carpeta y entonces:


 *sudo python setup.py install*
 

Desinstalarlo no es tarea sencilla porque Sonata utiliza distutils de Python para ser instalado, y aparentemente (e increiblemente) distutils no provee mecanismos para desinstalar. La localización de los archivos de la instalación, para removerlos manualmente, es:


[I]/usr/bin/sonata
/usr/lib/python2.4/site-packages/mmkeys.so
/usr/lib/python2.4/site-packages/mpdclient3.py
/usr/lib/python2.4/site-packages/mpdclient3.pyc
/usr/lib/python2.4/site-packages/sonata.py
/usr/lib/python2.4/site-packages/sonata.pyc
/usr/share/applications/sonata.desktop
/usr/share/locale/de/LC_MESSAGES/sonata.mo
/usr/share/locale/fr/LC_MESSAGES/sonata.mo
/usr/share/locale/pl/LC_MESSAGES/sonata.mo
/usr/share/locale/ru/LC_MESSAGES/sonata.mo
/usr/share/pixmaps/sonata.png
/usr/share/pixmaps/sonatacd.png
/usr/share/pixmaps/sonatacd_large.png
/usr/share/sonata/CHANGELOG
/usr/share/sonata/README
/usr/share/sonata/TODO
/usr/share/sonata/TRANSLATORS[/I]
 

···········

Bueno, espero que a alguien le resulte útil esto. Si lo hice es porque sinceramente considero que MPD es una forma excelente de reproducir música, y espero lograr que al menos alguien más lo conozca u aprecie un poco como yo =)
 

Saludos.
 

P.D: Estoy abierto a críticas y correciones. Más de una vez abré metido la pata =p

---

### Post by beuno on 2006-12-04
Buenisimo el aporte.
Estamos armando la pagina web para poder contener todos estos howto's un poco mas ordenados.
Gracias.

---

### Post by Nemesis Teufel on 2006-12-04
Es para edgy o dapper? o se puede en ambos?

---

### Post by beuno on 2006-12-04
> **Nemesis Teufel said:**
> Es para edgy o dapper? o se puede en ambos?

Considerando que es todo por subversion, deberia ser ambos.

---

### Post by jpmorelli on 2006-12-04
Gracias por el aporte y toda la explicación 10 puntos, eso sí , decime de donde sacas esos íconos que están buenísimos !!!

---

### Post by JMO707 on 2006-12-04
[Buuf icon theme]("http://www.gnome-look.org/content/show.php?content=44539") ;) 

Me alegra que les haya gustado ^^

---

### Post by QUASAR_FREAK on 2006-12-04
y para el ke es vagoneta aka les dejo un repo de donde bajarse todo menos el sonata ya compilado para edgy =)
```

deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-proposed main restricted universe multiverse

```

---

### Post by jpmorelli on 2006-12-04
> **JMO707 said:**
> [Buuf icon theme]("http://www.gnome-look.org/content/show.php?content=44539") ;) 

Me alegra que les haya gustado ^^

Gracias por el dato, ya estoy usando buff, muuuy bueno !

---

### Post by Nemesis Teufel on 2006-12-04
Muy bien redactado aunque prefiero la forma vaga.

offtopic: RAMMS+EIN [IMG]http://i117.photobucket.com/albums/o77/nemesisteufel/rock.gif[/IMG]

---

### Post by elektronaut on 2006-12-13
This seems to be the only relevant thread on this subject. Any possibility to get an english translation of this guide? Spanish is the fourth language I know, and my knowledge is quite limited.

A little remark: The song from Rammstein in the ncpmc window is called "Bück Dich". Which leads to my question concerning unicode support. At the moment, gmpc only shows me '#' instead of special characters. What is causing this error? mpd, gmpc, ...?

---

### Post by DuckMan on 2006-12-13
RAMMSTEIN! RAMMSTEIN! RAMMSTEIN! (L) buena nemesissss

a ver a ver, no entendi mucho el tema de este programa, te permite manejar la musica remotamente?

---

### Post by beuno on 2006-12-13
> **elektronaut said:**
> This seems to be the only relevant thread on this subject. Any possibility to get an english translation of this guide? Spanish is the fourth language I know, and my knowledge is quite limited.

A little remark: The song from Rammstein in the ncpmc window is called "Bück Dich". Which leads to my question concerning unicode support. At the moment, gmpc only shows me '#' instead of special characters. What is causing this error? mpd, gmpc, ...?

¿Quien puede traducirle esto al amable señor? (y muchos otros amables señores que seguro lo van a apreciar)

---

### Post by QUASAR_FREAK on 2006-12-13
si nadie lo hace antes, este finde se lo traduzko.

---

### Post by JMO707 on 2006-12-14
> **elektronaut said:**
> This seems to be the only relevant thread on this subject. Any possibility to get an english translation of this guide? Spanish is the fourth language I know, and my knowledge is quite limited.

A little remark: The song from Rammstein in the ncpmc window is called "Bück Dich". Which leads to my question concerning unicode support. At the moment, gmpc only shows me '#' instead of special characters. What is causing this error? mpd, gmpc, ...?

Haha, that is because I had those songs terribly tagged :p (now I finished my renaming/tagging campaing a week ago or so ^^)

To have "special" characters you have to edit a part of */etc/mpd.conf* and change the *ISO-8859-1* codification by *UTF-8*. Like this:

################# FILESYSTEM SETTINGS ####################
#
# If the names of files or directories are
# not correctly displayed then set the
# following to the filesystem coding.
#
#	Usually this is either:
#	ISO-8859-1 or UTF-8
#
# After changing the filesystem_charset
# you will need to recreate the db:
#	mpd --create-db
#
filesystem_charset "UTF-8"
#
##########################################################

[[IMG]http://img340.imageshack.us/img340/3465/pantallazobs7.th.png[/IMG]](http://img340.imageshack.us/my.php?image=pantallazobs7.png)

Por cierto: déjenme traducirlo. No me sentiría bien si otro lo hiciese por mi :-k

---

### Post by beuno on 2006-12-14
> **JMO707 said:**
> 
Por cierto: déjenme traducirlo. No me sentiría bien si otro lo hiciese por mi :-k

Me parece lo ideal.

---

### Post by JMO707 on 2006-12-17
Well, here it is =p

[Tutorial translation]("http://www.ubuntuforums.org/showthread.php?t=320469")

---

### Post by QUASAR_FREAK on 2006-12-17
excelente, menos mal que alguien lo tradujo porque este finde no estuve cerca de la compu.

Seria bueno también que agregues los repos con los binarios.

---

### Post by JMO707 on 2006-12-18
Me gustaría intentarlo. ¿Sabés como se hace?

---

