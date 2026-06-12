---
title: "Problemas Varios"
date: 2008-01-24
forum: Argentina Team
---

### Post by fedescha on 2008-01-24

Tengo algunos problems, probablemente muy tontos y faciles de resolver.
Rhythmbox:
   Cuando quiero escuchar MP3 recibo el siguente mensaje de error:
         [COLOR="Red"]Errores de importacion: no se pudieron enconrar los complementos de GStreamer para decodifcar achivos MP3.[/COLOR]
Segun el Synapsis tengo instalados: GStreamer0.10 -alsa      -esd     
-gnomevfs     -plugins-base     plugins-base-apps     -plugins-good     -tools   y por ultimo      -x      Tambien estan   libgstreamer0.10 -0       -plugins-base0.10     y     -totem-gstreamer

Que puedo hacer.

Cuando quiero usar el Totem para escuchar MP3 me aparece el siguiente mensaje:  Suitable codecs to play media files.  Me pregunta si quiero buscar la solucion y busca GStreamer extra plugins. El problema es que no tengo internet. De donde lo puedo bajar? en pakages.ubuntu.com no lo encuentro. Estoy bajando gstreamer0.10-fluendo-mp3-0.10.5-debian-1_i386, n se si me va a servir.

Otro problema: cuando quiero grabar o borrar algo en el penstck usb me da el siguente mensaje: no se ha podido cambiar los permisos de "disk" porque esta en un disco de solo lectura. En propidades»permisos    dice en:
 Propietario
Acceso a carpeta: Crear y borrar archivos.
Acceso a archivos: ...
 Grupo: Root
Acceso a carpeta: Ninguno.
Acceso a archivos: ...
 Otros
Acceso a carpeta: Ninguno.
Acceso a archivos: ...
 Ejecucion -
 Contexto SELinux: desconocido
Como puedo hacer para grabar y borrar algo en mi penstick?

No se si ya les dije qu no tengo internet.
No se si falta alguna info. Trate de ser lo mas claro y explicito posible.
Gracias a todos, saludos,

---

### Post by sajnox on 2008-01-24
Federico,

Esto ya se trato alguna vez en el foro (arriba a la derecha tenes una casilla de busqueda)

Aca te dejo un link a algo que te puede servir de ayuda

[http://ubuntuforums.org/showthread.php?t=607777&highlight=como+paquetes+sin+internet](http://ubuntuforums.org/showthread.php?t=607777&highlight=como+paquetes+sin+internet)

Saludos

---

### Post by margori on 2008-01-24
> **fedescha said:**
> ...tengo instalados: GStreamer0.10 -alsa      -esd -gnomevfs     -plugins-base     plugins-base-apps     -plugins-good     -tools   y por ultimo -x Tambien estan libgstreamer0.10 -0       -plugins-base0.10     y -totem-gstreamer Que puedo hacer...

Te están faltando los paquetes:
- [gstreamer0.10-ffmpeg]("http://packages.ubuntu.com/gutsy/libs/gstreamer0.10-ffmpeg")
- [gstreamer0.10-plugins-ugly]("http://packages.ubuntu.com/gutsy/libs/gstreamer0.10-plugins-ugly")

---

