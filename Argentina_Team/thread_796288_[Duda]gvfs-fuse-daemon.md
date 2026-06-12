---
title: "[Duda]gvfs-fuse-daemon"
date: 2008-05-16
forum: Argentina Team
---

### Post by lega on 2008-05-16
Ayer chusmeando el monitor de sistema vi que me sale una partición o no se muy bien que es con el nombre del título de este thread, tiene el mismo tamaño y el mismo espacio libre que la particion raiz y está montada en el /home/miusuario/.gvfs fui a ver esa carpeta y no hay nada.

Alguien más le pasa esto? para que sirve? es una especie de copia de resguardo o algo así? Tengo Ubuntu 8.04, adjunto captura

Gracias por la ayuda

Saludos.

---

### Post by faktorqm on 2008-05-18
GVFS viene de Gnome Virtual File Systen, y eso esta ahi para la integracion a FUSE (File system in userspace). O sea para que por ejemplo puedas montar una direccion de una red, o sea, puedas montar una carpeta compartida a traves de la red como si fuera una particion (o sistema de archivos como mas te guste), para que la use mplayer por ejemplo y puedas ver un video. Tiene muchas utilidades, FUSE por ejemplo tambien se usa en programas como el acetoneiso para tener montados imagenes iso de dvd's, o de cd's, etcetc. Cabe destacar que esto es todo virtual, en tu disco no existe nada de esto fisicamente.

Mas info:

[http://en.wikipedia.org/wiki/GVFS](http://en.wikipedia.org/wiki/GVFS)
[http://en.wikipedia.org/wiki/Filesystem_in_Userspace](http://en.wikipedia.org/wiki/Filesystem_in_Userspace)
[http://fuse.sourceforge.net/](http://fuse.sourceforge.net/)
[http://library.gnome.org/devel/gnome-vfs-2.0/unstable/](http://library.gnome.org/devel/gnome-vfs-2.0/unstable/)

Salu2!

---

### Post by sanflores on 2008-05-18
Che, y se puede borrar? o almenos hacerlo "desaparecer"???

Me molesta TERRIBLEMENTE que cuando hago un sudo find me aparezca permiso denegado... al menos me quiero automentir ocultandolo a full, va no se si es posible... se puede?

---

### Post by faktorqm on 2008-05-18
Mira yo no intentaria sacarlo por que esta integrado al nautilus y al gnome, pero creo que lo ideal seria que puedas excluirlo de las rutas de busqueda del find. No se como se hace eso pero aca tenes una buena guia de como usar el comando find 
[http://linux.about.com/od/commands/l/blcmdl1_find.htm](http://linux.about.com/od/commands/l/blcmdl1_find.htm)
Espero que te haya servido, salu2!!!

---

### Post by lega on 2008-05-19
Gracias por la respuesta ya existia esto en Gutsy? no recuerdo haberlo visto, aunque tampoco recuerdo haber husmeado en el monitor de sistema:)
Saludos

---

