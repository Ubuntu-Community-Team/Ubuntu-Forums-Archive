---
title: "Gestor grafico"
date: 2007-09-27
forum: Argentina Team
---

### Post by sharkg on 2007-09-27
Hola a todos nuevamente!!
me gustaria saber de algun gestor grafico q no pida mucho para poder instalar en un PII-400Hz y con 256 Mb de ram...
es para un server.
bueno gracias... salu2

---

### Post by leo_rockway on 2007-09-27
se me ocurren fluxbox, blackbox u openbox. aclaro que nunca los probe.

---

### Post by sharkg on 2007-09-27
voy a ver q tal son esos...
xterm es bueno? creo q me dijeron q es muy basico, puede ser?

---

### Post by leo_rockway on 2007-09-27
> **sharkg said:**
> 
xterm es bueno? creo q me dijeron q es muy basico, puede ser?

xterm si no me equivoco es un emulador de terminal, no un entorno de escritorio.

otra cosa, si queres probar fluxbox tenes la opcion de fluxbuntu (es ubuntu con fluxbox y con algunas cosas menos para hacerlo mas liviano)

---

### Post by kowal on 2007-09-27
XFCE, Fluxbox, IceWM..

---

### Post by santiagoward2000 on 2007-09-27
Yo uso XFCE en una celeron 1,4MHz pero con 185MB de RAM (es lo unico que me causo problemas) y anda bastante bien, aunque lo haya sobrecargado con COMPIZ-FUSION, SCREENLETS y KIBA-DOCK. La verdad que no se como vaya a andar en tu PII, pero el ram no va a ser problema.

> **sharkg said:**
> voy a ver q tal son esos...
xterm es bueno? creo q me dijeron q es muy basico, puede ser?

xterm es el emulador de terminal que viene con XFCE. Es como Konsole en KDE, o como gnome-console en Gnome.

---

### Post by nest on 2007-09-27
> **sharkg said:**
> Hola a todos nuevamente!!
me gustaria saber de algun gestor grafico q no pida mucho para poder instalar en un PII-400Hz y con 256 Mb de ram...
es para un server.
bueno gracias... salu2

fluxbox o openbox.

y si querés incursionar un poco más podrías instalar [fluxbuntu]("http://fluxbuntu.org/") que te va a venir perfecto.

aunque ahora la página de fluxbuntu está en desarrollo y van a lanzar el gutsy dentro de unos 20 días. así que mejor instalá fluxbox directamente desde consola (apt-get install fluxbox) y listo.

---

### Post by facundocorradini on 2007-09-27
Para una computadora así, lo más recomendable es uno superligero.

El más pulido y que entre ahí tal vez sea XFCE, pero tal vez no vaya tan fluido como quisieras... 

Yo uso y recomiendo Enlightenment 17, pq a pesar de ser super livianito es espectacular. 

Hay una sub-distro de ubuntu  que viene con la ultima versión de enlightenment y complementos de gnome, llamada GeUbuntu (recien salida del horno).  [http://www.geubuntu.intilinux.com/Home.html](http://www.geubuntu.intilinux.com/Home.html)

También puedes optar por instalar enlightenment 17 en un ubuntu comun, para ello: [http://thefenix.wordpress.com/2007/01/13/instalar-e17-en-ubuntu/](http://thefenix.wordpress.com/2007/01/13/instalar-e17-en-ubuntu/)

También puedes probar con
Fluxbox [http://fluxbox-wiki.org/index.php/Fluxbox-wiki](http://fluxbox-wiki.org/index.php/Fluxbox-wiki)
IceWM  [http://www.icewm.org/](http://www.icewm.org/)   (mas "clasico", tiene algunos skins muy buenos)
WindowMaker [http://www.windowmaker.info/](http://www.windowmaker.info/)
FVWM-Crystal [http://fvwm-crystal.org/](http://fvwm-crystal.org/)   (MUY liviano y bastante lindo)
EDE  [http://equinox-project.org/page/](http://equinox-project.org/page/)

Casi todos están disponibles en synaptic. 

Todos estos van a correr super bien con esa maquina... algunos incluso con mucho menos...

saludos

---

### Post by fajro on 2007-09-27
Ya que mencionan el tema...

Si tienen computadoras muy viejas (64 megas de ram para abajo) y ganas de experimentar prueben Ubuntulite.

Ubuntulite es una distro superliviana que está en desarrollo (hace poco que se "revivió" el proyecto) y necesitan testers.

[URL="http://ubuntulite.tuxfamily.org/"]
http://ubuntulite.tuxfamily.org/[/URL]

:KS

---

### Post by nest on 2007-09-27
> **fajro said:**
> Ya que mencionan el tema...

Si tienen computadoras muy viejas (64 megas de ram para abajo) y ganas de experimentar prueben Ubuntulite.

Ubuntulite es una distro superliviana que está en desarrollo (hace poco que se "revivió" el proyecto) y necesitan testers.

[URL="http://ubuntulite.tuxfamily.org/"]
http://ubuntulite.tuxfamily.org/[/URL]

:KS

me había olvidado.

si tuviera una pc vieja también le daría una oportunidad a ubuntulite.

---

### Post by sharkg on 2007-09-27
bueno gente, les comento que pude instalar todo correctamente, me costo un poco por no tener los paquetes X11 instalados y demas, pero bueno, buscando y con ayuda siempre s puede..
aca les dejo los pasos que hice para q otro q tenga el mismo problema o quiera hacer lo mismo lo haga.

[B]sudo aptitude update
sudo aptitude upgrade[/B]
estas lo hice antes, pero por las dudas si esta recien instalado el soft mejor!

**sudo aptitude install xorg**
para bajar los paquetes graficos de X11 asi andan los gestores graficos

**sudo aptitude install fluxbox fluxconf**
para bajar el  es gestor grafico y su config

esta es la dire del post donde lo saque, esta en ingles, pero se entiende bien..
[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

espero que les sirva y gracias a todos. salu2

---

### Post by nest on 2007-09-27
> **sharkg said:**
> bueno gente, les comento que pude instalar todo correctamente, me costo un poco por no tener los paquetes X11 instalados y demas, pero bueno, buscando y con ayuda siempre s puede..
aca les dejo los pasos que hice para q otro q tenga el mismo problema o quiera hacer lo mismo lo haga.

[B]sudo aptitude update
sudo aptitude upgrade[/B]
estas lo hice antes, pero por las dudas si esta recien instalado el soft mejor!

**sudo aptitude install xorg**
para bajar los paquetes graficos de X11 asi andan los gestores graficos

**sudo aptitude install fluxbox fluxconf**
para bajar el  es gestor grafico y su config

esta es la dire del post donde lo saque, esta en ingles, pero se entiende bien..
[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

espero que les sirva y gracias a todos. salu2

gracias por el aporte.

y bien en haber elegido fluxbox ;)

---

### Post by sharkg on 2007-09-28
en realidad gracias a todos los q ayudaron a que logre instalar el gestor. sin ese aporte de todos yo no hubiera llegado al post anterior... gracias

---

