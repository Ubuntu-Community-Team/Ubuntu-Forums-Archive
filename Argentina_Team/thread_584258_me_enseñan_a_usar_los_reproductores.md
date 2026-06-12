---
title: "me enseñan a usar los reproductores"
date: 2007-10-20
forum: Argentina Team
---

### Post by dj_isaco on 2007-10-20
hola a todos aca de vuelta tengo varios problemas con varios reproductores ej: tolem,exaile y el mplayer les paso a comentar
**con el tolem cuando cargo unos dvd ripeados (hogareños) con el DVD Decrypter no me aparecen los subtitulos y no pude encontrar como verlos.
**con el exaile no puedo generar un playlist por categoria; elegi este porq el trae ubuntu el Rhythmbox me las agregaba al final de la que recien habia creado y se me mezclaba todo,despues probe Amarok pero una no le entendia ni "J" y la otra cuando ponia a buscar los archivo multimedis tardaba uzzz... eso q tengo 2 gb de musica nada mas, y bueno lo descarte.
**con el mplayer cuando selecciono el vob o el ifo del dvd me tira este error
Error opening/initializing the selected video_out (-vo) device.
y no  me abre el video si alguien sabe como solucionarlos desde ya gracias y a seguir aprendiendo.

pd: otro problema con exaile es cuando habro las herramientas y seleciono ecualizador me dice:
 "GStreamer equalizer is not available.  It can be found in gstreamer-plugins-bad 0.10.5."
pero ya revise en synaptic y no lo encuentro con esa descripcion ni nombre

---

### Post by freed0m on 2007-10-20
Probá de instalar el VLC. Es un muy buen player, lo mejor es que ya viene por default con muchisimos codecs incluyendo reproduce DVDs.

Saludos.

---

### Post by dj_isaco on 2007-10-21
gracias ya lo estere probando, pero una duda como fui user de win lo q aprendi fue a no instalar y desinstalar muchos soft no se si en linux es lo mismo, lo q si nunca pude encontrar el reg. aqui existe o no?

---

### Post by WanderingKnight on 2007-10-21
> 
**con el mplayer cuando selecciono el vob o el ifo del dvd me tira este error
Error opening/initializing the selected video_out (-vo) device.
y no me abre el video si alguien sabe como solucionarlos desde ya gracias y a seguir aprendiendo.

Primero y principal, tenes los codecs de la pagina de mplayer? Acordate de bajarlos e instalarlos de acuerdo a las instrucciones (vienen dentro del paquete).

Segundo, para resolver el problema de mplayer, abrilo, hace clic derecho, anda a Preferences--->Video, y donde dice "available drivers" selecciona xv. Cerralo y volve a arrancarlo, y fijate si ahi anda.

El VLC, en mi opinion, es una tremenda ********* para mostrar softsubs. He tenido muy malas experiencias con el... mplayer con los codecs binarios anda perfecto para cualquier archivo.

> lo q si nunca pude encontrar el reg. aqui existe o no?

No, no existe. El registro es un concepto completamente retardado e ilogico, algo que nunca deberia haber existido en primer lugar. Se trata de algo tan contraproductivo y estupido que me llama la atencion que la gente lo haya soportado durante tanto tiempo. El concepto principal en un sistema basado en Unix es "TODO es un archivo", por lo tanto, no existe tal cosa como el registro, que ni siquiera aparece como un archivo en Windows.

---

### Post by leo_rockway on 2007-10-21
> **WanderingKnight said:**
> 
El VLC, en mi opinion, es una tremenda ******** para mostrar softsubs. He tenido muy malas experiencias con el... mplayer con los codecs binarios anda perfecto para cualquier archivo.

+1 vlc es muy bueno, pero a la hora de reproducir subs va para atras. mplayer es muchisimo mejor que vlc en ese sentido y ademas es muy buen programa.

> **WanderingKnight said:**
> No, no existe. El registro es un concepto completamente retardado e ilogico, algo que nunca deberia haber existido en primer lugar. Se trata de algo tan contraproductivo y estupido que me llama la atencion que la gente lo haya soportado durante tanto tiempo. El concepto principal en un sistema basado en Unix es "TODO es un archivo", por lo tanto, no existe tal cosa como el registro, que ni siquiera aparece como un archivo en Windows.

primero que nada... la palabra es contraproducente :lolflag: que clase de traductor!? jaja :guitar:

anyway... el registro es parte de la politica de "esta oculto y fuera del alcance del usuario/admin (que en windoze en general es lo mismo... y es un grave error) asi que si algo se rompe es culpa de ellos y no nuestra"

el registro no esta documentado, asi que para hacer algo hay que ir a ciegas tanteando que hace cada cosa. un reverenda porqueria. en los sistemas *nix, como bien dijo mi querido amigo WanderingKnight, todas las cosas son archivos (documentados); por ej: la configuracion de un programa esta en un archivo, los dispositivos son archivos, etc. 

este metodo resulta mucho mas practico, aunque a algunos despues de tantos anios de estar esclavizados por el sistema de registro les cueste adaptarse.

---

### Post by dj_isaco on 2007-10-21
bien hay logre ver los videos en mplayer pero cuando llego la hora del sub no los tomaba les paso a explicar la situacion
primero tengo tengo dos discos en uno tengo win y en el otro ubuntu, pero de la casualidad q en el de win tengo las pelis ripeadas, cuando abro el mplayer no puedo llegar hasta ella xq no me aperece tengo q ir manual" y seleccionar el vob y decirle q lo abra con mplyer,ya q al ifo no lesta asociado a nadie y para el colmo no se donde esta para seleccionarlo, abro el vob y se reproduce pero no me aparecen los idiomas ni los sub.
Con respecto al cometario de WanderingKnight fui hasta la pagina y no supe cuales eran los codec q sebia bajar ya q son muchos y encima hay varios en rpm, q tengo entendido q hay q pasarlo a deb para q los pueda hacer andar con un doble clik, [**aca**]("http://www1.mplayerhq.hu/MPlayer/releases/codecs/") les dejo la un enlace asi me ayundan gracias

---

### Post by WanderingKnight on 2007-10-21
> primero que nada... la palabra es contraproducente que clase de traductor!? jaja

Bueno, que queres, eran las 5 de la matina, no me pidas mucha gramatica a esas horas :p

> 
Con respecto al cometario de WanderingKnight fui hasta la pagina y no supe cuales eran los codec q sebia bajar ya q son muchos y encima hay varios en rpm, q tengo entendido q hay q pasarlo a deb para q los pueda hacer andar con un doble clik, aca les dejo la un enlace asi me ayundan gracias

Los codecs no vienen ni en deb ni en rpm, los tenes que copiar a mano directamente. Los bajas de donde dice "Binary Codec Download", pero como soy bueno, te lo linkeo directamente [aca](http://www3.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2).

Despues lo que haces es lo siguiente: Extraes el archivo (es un .tar, equivalente a un zip o un rar en Windows), vas a una consola y haces:

```
sudo nautilus
```

De ahi, navega hasta /usr/lib/codecs/, y copia todos los codecs que estaban en el archivo que bajaste a esa carpeta. Ahi el mplayer deberia tomarte absolutamente todo.

Ah, y si queres que mplayer muestre subtitulos con formatos especiales, tenes que hacer lo siguiente: vas a la consola y tipeas:

```
gedit ~/.mplayer
```
...si tenes GNOME, (Ubuntu) o

```
kate ~/.mplayer
```
...si tenes KDE (Kubuntu).

Se te va a abrir un editor de texto con una linea, y le agregas las siguientes lineas:

```
sid=0
ass=1
embeddedfonts=1
correct-pts=1
```

Salvas el archivo y listo, mplayer ya tiene soporte para tipografias customizadas.

---

### Post by ariel on 2007-10-21
Si usas gutsy lo que te puedo recomendar es dejar todo por default, y en System > Add/remove..., busca "Ubuntu Restricted"  (si no te sale nada, asegurate que este en Show = All available apps). Eso te instala todos los codecs includa la app que hace falta para ver dvds. 

Antes de gutsy, yo usaba vlc porque totem no andaba ni para atras. VLC no es cool pero le tiras cualquier cosa y no tiene problemas. Con gutsy, vlc lo tengo de backup nomas.

salu2



> **dj_isaco said:**
> hola a todos aca de vuelta tengo varios problemas con varios reproductores ej: tolem,exaile y el mplayer les paso a comentar
**con el tolem cuando cargo unos dvd ripeados (hogareños) con el DVD Decrypter no me aparecen los subtitulos y no pude encontrar como verlos.
**con el exaile no puedo generar un playlist por categoria; elegi este porq el trae ubuntu el Rhythmbox me las agregaba al final de la que recien habia creado y se me mezclaba todo,despues probe Amarok pero una no le entendia ni "J" y la otra cuando ponia a buscar los archivo multimedis tardaba uzzz... eso q tengo 2 gb de musica nada mas, y bueno lo descarte.
**con el mplayer cuando selecciono el vob o el ifo del dvd me tira este error
Error opening/initializing the selected video_out (-vo) device.
y no  me abre el video si alguien sabe como solucionarlos desde ya gracias y a seguir aprendiendo.

pd: otro problema con exaile es cuando habro las herramientas y seleciono ecualizador me dice:
 "GStreamer equalizer is not available.  It can be found in gstreamer-plugins-bad 0.10.5."
pero ya revise en synaptic y no lo encuentro con esa descripcion ni nombre

---

