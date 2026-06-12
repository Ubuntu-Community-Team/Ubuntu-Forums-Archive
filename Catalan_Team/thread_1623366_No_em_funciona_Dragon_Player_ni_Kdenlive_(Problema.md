---
title: "No em funciona Dragon Player ni Kdenlive (Problema Mplayer/XIne???)"
date: 2010-11-16
forum: Catalan Team
---

### Post by kukat on 2010-11-16
No em funciona Dragon Player de cap manera. He provat moltes coses. 

La sortida per consola és aquesta:

[B][I]jordi@clairvoyant:/usr/lib/gstreamer-0.10$ dragon
dragonplayer(3315)/kdeui (kdelibs): Attempt to use QAction "aspect_ratio_menu" with KXMLGUIFactory! 
dragonplayer(3315)/kdeui (kdelibs): Attempt to use QAction "audio_channels_menu" with KXMLGUIFactory! 
dragonplayer(3315)/kdeui (kdelibs): Attempt to use QAction "subtitle_channels_menu" with KXMLGUIFactory! 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/jordi/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
[/I][/B]

He provat amb tots els Kernels (des del -21 fins al -25) i res de res....
I mira que al principi funcionava!!! :(  no se, jo crec que l'he vist funcionar...

Però el problema no és de Dragon Player, sinó de Mplayer o Xine (no estic segur), ja que amb el KDENLive passa el mateix....I necessite editar un vídeo urgentment, i no hi ha forma!!! 
:( 

Ací hi ha una captura _ > [http://img15.imageshack.us/img15/5224/dragonplayer.png](http://img15.imageshack.us/img15/5224/dragonplayer.png)

També he provat d'esborrar mplyaer i tornar a insta&#320;lar, ídem amb Dragon Player....
:( 

Algú li ha passat el mateix i ho ha pogut solucionar??? 

Gràcies! 
;)

---

### Post by kukat on 2010-11-16
buffff
:confused:

La solució passa per llevar-li el OpenGL al Cairo-Dock.... 
:confused:

Bé, doncs això.
He anat a "Arranjament del Sistema", "Aplicacions d'inici" i al cairo-dock li he afegit cairo-dock -c

que coses.....

bé, ja està arreglat...

---

