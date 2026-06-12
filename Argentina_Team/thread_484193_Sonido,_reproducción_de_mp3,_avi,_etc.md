---
title: "Sonido, reproducción de mp3, avi, etc"
date: 2007-06-25
forum: Argentina Team
---

### Post by elviolator2004 on 2007-06-25
Buenas tardes a la comunidad de Ubuntu. Soy un usuario nuevo en Linux y por recomendaciones instalé el live cd de Ubuntu, para empezar. La instalación todo bien, el sistema ya esta funcionando, pero no puedo reproducir los archivos ej: mp3, avi, etc, porque segun me lo marca el mismo sistema me faltan instalar los paquetes correspondientes. Mi problema es el siguiente, la pc donde lo instalé no tiene conexión a internet. y no creo que por el momento la pueda tener, entonces, como puedo hacer para solucionarlo?. Estuve pensando en bajar los paquetes desde otro lado y luego ejecutarlos en la otra, pero la pregunta es si se puede?, como? y por ultimo cuales serían los paquetes que tendría que bajar y de donde?. Desde ya gracias por la ayuda que puedan brindar, 

Elvio
Córdoba, Argentina

---

### Post by guillermolisi on 2007-06-25
Elvio

Seguramente tenes varias alternativas pero creo que para todas vas a necesitar un enlace a Internet, aunque sea en otra maquina, y que tambien tenga Ubuntu ya que estas herramientas trabajan con los repositorios.

Te paso una que tenia vista para uso propio:

** CD-based repository creator** for packages downloaded via APT
Tool for the creation of a CD-based repository containing all packages
downloaded via apt-get. Helpful for a post-installation on several
machines or a simple backup method to re-install the system.
After you've created the CD, you will be able to add it as a repository,
as if it were an Ubuntu 'CD 2'. To run it, type "aptoncd" in a terminal.
Or alternatively, via System -> Administration -> APTonCD menu entry.

For more information, visit [http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)

Espero te sea de utilidad.

---

### Post by fetova on 2007-06-26
Pues puedes checar en [http://packages.ubuntu.com/](http://packages.ubuntu.com/) estos paquetes:

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg

Bajatelos con sus dependencias y en tu maquina los metes a /var/cache/apt/archives/

Despues das en una terminal:

```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg --no-download  -ignore-missing
```

Saludos

---

### Post by faktorqm on 2007-06-27
Hola, primero que nada trata de ponerte internet. Segundo te paso aca una solucion "robada".

Como sos nuevo te cuento, existe un programa, que es un instalador automatico de cosas, muy bueno por cierto y te ahorra mucho trabajo, se llama automatix. es un programa que vos le decis que instale, por ejemplo, el amule (cliente ed2k y kad para linux) y te corre un script en una terminal, lo baja, lo instala y ya. Tambien permite desinstalar. Para tu caso, no te sirve, asi que fui hasta el archivo que usa este programa, que es el ubicado en "/usr/etc/automatix2/ax_data/feisty.autoscript" y te copie las partes que necesitas para tener lo multimedia en OK. Aclaro, hay algunas cosas que no se cual es la diferencia, pero que te instalan todo todo para que veas cualquier cosa, capaz si necesitas algun formato "raro" ya lo tenes instalado.

Siguiendo el metodo propuesto antes, vas a [http://packages.ubuntu.com](http://packages.ubuntu.com) y los elegis uno por uno a mano, pero es un bodrio. si lo haces asi, te los bajas a todos, los mandas en un cd,  y despues tenes que copiar cada .deb en "/var/cache/apt/archives" y luego correr los comandos que te paso mas abajo con las opciones. (OJO! le agregue "--no-download" al final de cada una, en el original no esta asi, y no tengo tiempo de probarlo, si no te anda, saca esa opcion, si no te anda, posteá ;) )

```
sudo apt-get --assume-yes install libdvdnav4 libdvdplay0 libdvdread3 totem-xine libxvidcore4 lame sox ffmpeg mjpegtools vorbis-tools mpg321 libxine1 libxine1-plugins gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-farsight gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux gstreamer0.10-gnonlin gstreamer0.10-sdl faac faad alsa-oss oss-compat libk3b2-mp3 gstreamer-tools --no-download
```

Este "paquete" se llama multimedia, **LOS NOMBRES DE LOS PAQUETES QUE TENES QUE BUSCAR EN LA WEB SON IGUALES QUE LOS QUE APARECEN AHI, EJ.: LIBDVDNAV4, FAAC**

estos vendrian a ser los codecs digamos y un reproductor, el totem para dvd's y demas, te agrego mas cosas, reproductores, fuentes extras, etc.

Fuentes extra:

```
sudo apt-get --assume-yes install msttcorefonts gsfonts-other t1-xfree86-nonfree ttf-dustin ttf-f500 ttf-isabella ttf-larabie-deco ttf-larabie-straight ttf-larabie-uncommon ttf-staypuft ttf-summersby ttf-ubuntu-title ttf-xfree86-nonfree xfonts-artwiz xfonts-intl-european gsfonts-x11 gsfonts ttf-liberation ttf-georgewilliams ttf-sjfonts --no-download
```

Compresores/descompresores:

```
sudo apt-get --assume-yes install rar unace unrar p7zip p7zip-full arj unzoo lha libarchive1 libarchive-tar-perl libarchive-zip-perl dpkg-dev alien cabextract --no-download
```

Reproductor al mejor estilo WinAMP (yo lo uso, a mi me encanta):

```
sudo apt-get --assume-yes install vorbis-tools sox mjpegtools ffmpeg lame imagemagick toolame mpeg2dec gstreamer0.8-mpeg2dec gstreamer0.8-a52dec audacity --no-download
```

Reproductor de "todo" por si el totem no te gusta. VLC se llama:

```
sudo apt-get --assume-yes install vlc vlc-plugin-arts wxvlc vlc-plugin-esd vlc-plugin-arts vlc-plugin-ggi vlc-plugin-sdl --no-download
```


PARA TODO (paquetes para instalar paquetes ;) ):

```
sudo apt-get install gnutls-bin build-essential --no-download
```

Bueno, fijate que onda. Estos paquetes que te puse aca son del automatix2 para ubuntu feisty 7.04 AMD64. Estoy en el laburo y tengo 64bits, en mi casa tengo 32bits, aunque no creo que haya diferencia por que no dependen de la arquitectura (ESTOS, hay otros que si, y mucho). Salu2!

---

### Post by elviolator2004 on 2007-06-27
Gracias por las respuestas. Ya pude solucionar el tema de la instalacion de los paquetes y además configurar la salida del sonido. Ahora me funciona todo 10 puntos. Solo me queda bajar el paquete completo para poder visualizar los videos en formato mpg y mpeg.
Con respecto al so puedo decir que me gustó mucho, veo que pueden hacer muchas cosas (muchas mas que en Windows) y por lo tanto me encuentro entusiasmado aprendiendolo a usar.
La unica critica que podría llegar a hacerle es lo lento o lo largo del ingreso al sistema.
Lo demás 10 puntos.:p
Saludos y gracias nuevamente

---

### Post by Al_maverick on 2007-06-29
> **elviolator2004 said:**
> Gracias por las respuestas. Ya pude solucionar el tema de la instalacion de los paquetes y además configurar la salida del sonido. Ahora me funciona todo 10 puntos. Solo me queda bajar el paquete completo para poder visualizar los videos en formato mpg y mpeg.
Con respecto al so puedo decir que me gustó mucho, veo que pueden hacer muchas cosas (muchas mas que en Windows) y por lo tanto me encuentro entusiasmado aprendiendolo a usar.
La unica critica que podría llegar a hacerle es lo lento o lo largo del ingreso al sistema.
Lo demás 10 puntos.:p
Saludos y gracias nuevamente

Para hacerla completa :D

Si buscas en los foros por "readahead" vas a encontrar tips para acelerar el inicio. 

Igual, mi experiencia es que es engañoso el arranque rapido de windows. Basicamente, la pantalla de login te la muestra rapido, pero el sistema no es "usable" hasta que realmente termina de cargar todo. En mi caso, son un par de minutos. En linux, con este tip, en 1 minuto estoy adentro y con todas las aplicaciones abiertas.

---

### Post by elviolator2004 on 2007-07-05
> **Al_maverick said:**
> Para hacerla completa :D

Si buscas en los foros por "readahead" vas a encontrar tips para acelerar el inicio. 

Igual, mi experiencia es que es engañoso el arranque rapido de windows. Basicamente, la pantalla de login te la muestra rapido, pero el sistema no es "usable" hasta que realmente termina de cargar todo. En mi caso, son un par de minutos. En linux, con este tip, en 1 minuto estoy adentro y con todas las aplicaciones abiertas.

Ok gracias!! tendré en cuenta tu comentario y le echaré una leída a los tip para ver que puedo ir descubriendo. Muchas gracias. Les comento que ya solicité el servicio de internet, seguramente en el transcurso de la semana que viene estaré conectado desde casa. Ahora estoy buscando en el foro algún tema en que se haya tratado la configuración del acceso a internet. Si no encuentro o no entiendo voy a estar preguntando. Muchas gracias
Saludos!!:p

Elvio

---

