---
title: "Kde 4"
date: 2007-12-11
forum: Argentina Team
---

### Post by joseluis on 2007-12-11
Hola amigos...tengo entendido que el 12 de diciembre se libera KDE 4.
Ahora bien, yo tengo ubuntu 7.10 y estoy queriendo poner tambien el escritorio de kubuntu, para tener tambien la alternativa KDE.
La pregunta que hago es la siguiente ¿Alguien sabe cuando estaría disponible en los repos de ubuntu el kde 4 para bajar el desktop kubuntu asi me salvo de hacer actualizacion y poner directamente el 4?
Gracias

---

### Post by leo_rockway on 2007-12-11
de hecho kde 4 YA esta disponible, rc1 si no me equivoco.

---

### Post by marianom on 2007-12-11
La manera de seguir al nuevo soft que sale entre release y release de ubuntu es por medio de los [backports]("https://help.ubuntu.com/community/UbuntuBackports").
Estimo que no será necesario que hagas un pedido de backport por algo como KDE porque seguro que alún otro se encargó de eso y también considero que lo más fácil será verlo en funcionamiento en la próxima versión. Pero te sugiero que sigas el link provisto, que leas la info y te suscribas a todos los lugares donde tengas novedades sobre cuando estará disponible.

---

### Post by leo_rockway on 2007-12-11
[http://www.kubuntu.org/announcements/kde4-rc1.php](http://www.kubuntu.org/announcements/kde4-rc1.php)

kde4 ya esta en los backports

---

### Post by kowal on 2007-12-11
KDE 4.0 final se espera para mediados de Enero..

[http://dot.kde.org/1196525703/](http://dot.kde.org/1196525703/)

---

### Post by Hei Ku on 2007-12-11
Y la version 4.0 es una versión de transición. En realidad, no se espera que sea una versión, sino para power users, que puedan colaborar en el pulido de todas las nuevas funcionalidades. KDE 4.0 representa un cambio muy importante en muchas de las estructuras basicas de KDE, muchos sino todos los componentes importantes del sistema se hicieron de cero, desde el menu hasta el Kontact. Por lo tanto, espera que haya un periodo de transicion hasta que el sistema este listo para usuarios comunes, y las distros empiecen a adoptarlo. Eso se espera para la version 4.1, que no tiene fecha todavia.
Yo no lo use todavia, pero por lo que leo regularmente en los blogs de los desarrolladores, el cambio suena muy interesante. Y la comunidad que hay detras de eso es inspiradora.

---

### Post by Darth Trix on 2007-12-11
Ya esta listo, recien salido del horno, el RC 2 de KDE 4.0 y tambien ya hay un liveCD de Kubuntu con KDE 4

---

### Post by josedamico on 2007-12-11
quisiera formular la pregunta de nuevo. A ver...ya he visto que en [http://www.kubuntu.org/](http://www.kubuntu.org/) se dice que viene con KDE 4.0 RC2. Esto esta claro. 
Tengo instalado UBUNTU 7.10, y quisiera poner el entorno KDE No instalar kubuntu, sino mantener ambos entornos.

Mi pregunta sería la siguiente: si hago $:sudo aptitude install kubuntu-desktop me instala el entorno kde (de kubuntu) y pregunto si al instalar esto YA viene con el KDE 4.0.

Espero ser claro..
gracias

---

### Post by pablo0469 on 2007-12-12
No, que yo sepa te va a instalar KDE 3.5.8, la version que viene con Kubuntu 7.10, y que es la que esta en los repositorios.
 
La 4.0 rc2, la tenes que instalar por tu cuenta.
 
Ademas, instala el paquete kde-i18n-es para tenerlo en español.
 
Saludos.

---

### Post by joseluis on 2007-12-12
Entonces quizás convenga a esperar que esté en los repos de kubuntu para cargar todo...
gracias

---

### Post by Hei Ku on 2007-12-12
Por aquí, por favor.

[http://kubuntu.org/announcements/kde4-rc2.php](http://kubuntu.org/announcements/kde4-rc2.php)

RC2 entregada. Mucho gusto. Nos vemos,

:D

---

### Post by josedamico on 2007-12-12
bien!!! muchas gracias!!! bajando...
ahora..repito....¿si pongo instalar kubuntu-destop me pone este??

---

### Post by leo_rockway on 2007-12-12
> **josedamico said:**
> bien!!! muchas gracias!!! bajando...
ahora..repito....¿si pongo instalar kubuntu-destop me pone este??

si pones instalar kubuntu-desktop te instala el 3.5.8 que es el estable.

---

### Post by pablo0469 on 2007-12-12
Instala kubuntu-desktop y kde-i18n-es, y luego actualiza kde a 4.0 desde los links que te pusieron arriba.

Saludos y despues comenta como anda.

---

### Post by Hei Ku on 2007-12-13
Aca estan las instrucciones. Y si esto te parece dificil, por favor no lo instales. KDE4 esta todavia en beta. Si bien se lo llama RC2, la version 4.0 esta pensada para desarrolladores, no para usuarios comunes, asi que tiene problemas mucho mas frecuentes, y mas complicados que lo que uno esta acostumbrado.

Instructions:

    * Remove previous KDE 4 packages, they are not compatible (apt-get remove kdelibs5 kde4base-data kde4libs-data)
    * Add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main to your /etc/apt/sources.list
    * Install the updated kdebase-bin
    * Install kdebase-workspace kdebase-kde4 kdebase-runtime, note that PPAs aren't authenticated so you will likely get a warning when installing
    * KDE 4 apps should appear in your KDE 3 K-menu or you can run a full session by selecting "KDE 4" from your login manager.
    * To avoid having to start a second X server for a full session install xserver-xephyr and run Xephyr :1 & export DISPLAY=:1; xterm and run startkde in the Xerphyr xterm.

Si lo instalan, posteen unos screenshots :D

---

### Post by facundocorradini on 2007-12-13
> Aca estan las instrucciones. Y si esto te parece dificil, por favor no lo instales. KDE4 esta todavia en beta. Si bien se lo llama RC2, la version 4.0 esta pensada para desarrolladores, no para usuarios comunes, asi que tiene problemas mucho mas frecuentes, y mas complicados que lo que uno esta acostumbrado.

no es por iniciar un flame... pero vaya decisión!! ... Llamar RC 2 a un software que apenas alcanza el estado de beta!!!... creí que para eso estaba el soft privativo...

---

### Post by josedamico on 2007-12-13
bien..veo que todavía no está maduro el tema...quizás habría que esperar un poco más y ver qué pasa. Lo que estuve viendo es que kde4 es mas liviano que el anterior. Asi que a esperar que vengan las finales.
gracias a todos

---

### Post by kowal on 2007-12-13
> **facundocorradini said:**
> no es por iniciar un flame... pero vaya decisión!! ... Llamar RC 2 a un software que apenas alcanza el estado de beta!!!... creí que para eso estaba el soft privativo...

Cada vez que una persona dice "no es por iniciar un flame, pero.." automáticamente se convierte en un troll e inicia un flame.

Me parece que indicar un paralelismo o analogía entre el modelo de desarrollo que lleva KDE4 con el software privativo es una critica demasiado aventurada..

---

### Post by Hei Ku on 2007-12-13
> **facundocorradini said:**
> no es por iniciar un flame... pero vaya decisión!! ... Llamar RC 2 a un software que apenas alcanza el estado de beta!!!... creí que para eso estaba el soft privativo...
Y mordi el anzuelo...

Si lees mi mensaje, fui en claro en que es una version para desarrolladores. El objetivo de la version 4.0 es que sea la plataforma para que los desarrolladores puedan empezar a portar el resto de aplicaciones a 4.0. Es mi caso, por ejemplo, que colaboro con una aplicacion kde y estamos esperando el release final para ver como comenzamos el trabajo.

Y la diferencia con un soft privativo es que con este te podes arremangar y ponerte a arreglar bugs para mejorar la calidad. Empeza por aca; [http://bugzilla.kde.org](http://bugzilla.kde.org)

De paso, podes leer aca: [http://planet.kde.org](http://planet.kde.org) las justificaciones de por qué se le llama RC y cuáles son los objetivos de la version 4.0, que en ningun momento se menciona que sea para usuarios finales, sino una plataforma de despegue para la 4.1 que si se espera que sea de una calidad y estabilidad suficiente para usuarios finales.

---

### Post by spg76 on 2007-12-13
Después de probar KDE 4 RC 2 (la versión de Kubuntu y la de OpenSUSE), coincido con lo que dice Hei Ku.
Yo no soy desarrollador y, si bien me gustó bastante, todavía está muy lejos de ser una plataforma estable y hay mucho para pulir.
Yo recuerdo que la serie 3 de KDE tuvo un camino parecido y pasaron varias versiones hasta que se transformará en una plataforma estable y púlida para los usuarios finales.
Les dejó más abajo con un par de capturas (como pidió alguien por ahí) de programas de KDE 4 corriendo en GNOME porque la sesión completa se niega a arrancar como corresponde.
Saludos.

---

### Post by facundocorradini on 2007-12-14
Ok, gracias Hei Ku por la aclaración...

---

### Post by LuisAugusto on 2007-12-15
Todos los problemas graves que pueda tener KDE 4.0 RC 2 (3.97) en Kubuntu, son culpa de Kubuntu.

Yo utilizo KDE 4 como mi escritorio principal desde hace unos 15 días, rara vez algún programa hace "crash" (sorprendentemente mi idioma natal es el español y no se me ocurre un equivalente a esa palabra XD), Plasma es el único que de vez en cuando muere, y se reinicia solito.

KDE 4 RC 2 en su estado actual ya se siente mejor que KDE 3.5.8.

Lo único realmente malo será la falta de kde-pim, kprint y uno que otro detallito (como que plasma no será realmente explotado en KDE 4.0).

¿KDE 4.1 será mejor? Obvio.

---

### Post by valucha on 2007-12-15
[COLOR="DarkOrchid"]Wuaw... acabo de ver las screenshots que postearon de Dolphin y parece muy bueno y completo.
Tal vez me cambie a Kde después de haberle hecho tanto la guerra :$[/COLOR]

---

