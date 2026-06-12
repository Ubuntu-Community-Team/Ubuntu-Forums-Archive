---
title: "Banshee 0.12.0 desde SVN"
date: 2007-03-09
forum: Argentina Team
---

### Post by screening on 2007-03-09
Para instalar [Banshee]("http://banshee-project.org/Main_Page") desde SVN primero debemos activar los repositorios multiverse en Synaptic o en /etc/apt/sources.list y luego hay que controlar que tengamos los siguientes paquetes instalados:

$ sudo apt-get install gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly \
gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly-multiverse \
gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg

Instalamos las dependencias:

$ sudo apt-get build-dep banshee
$ sudo apt-get install libmono-sqlite2.0-cil libmono-cairo2.0-cil libglib2.0-dev \
libtool subversion autoconf automake1.9 gnome-common libavahi1.0-cil

Configuramos automake:

$ sudo update-alternatives --set automake /usr/bin/automake-1.9
$ sudo ldconfig
Obtenemos Banshee desde SVN

$ svn co [http://svn.gnome.org/svn/banshee/trunk/banshee](http://svn.gnome.org/svn/banshee/trunk/banshee)
Y ahora empezamos la construcción del reproductor:

$ cd banshee/
$ ./autogen.sh --prefix=/usr --disable-docs
y terminamos con:

$ make
$ sudo make install


Por último, si no nos gusta o nos parece malo podemos desinstalarlo:

$ cd banshee
$ sudo make uninstall

Para eliminar los archivos de configuración y Base de datos:

$ gconftool-2 --recursive-unset /apps/Banshee
$ gconftool-2 --recursive-unset /apps/banshee
$ rm ~/.gnome2/banshee/banshee.db

Borrar archivos misceláneos:

$ rm -rf ~/.gnome2/banshee/

---

