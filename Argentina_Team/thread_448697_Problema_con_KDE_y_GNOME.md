---
title: "Problema con KDE y GNOME"
date: 2007-05-19
forum: Argentina Team
---

### Post by seba2611 on 2007-05-19
Bueno el problema que tengo es que quise instalar kubuntu-desktop y al hacerlo mientras se descargaba me pregunto cual era el arranque por defecto q usaba y sin querer marque KDM en vez de GDM , a partir de ahi cada vez que reinicio o apago me sale Kubuntu no Ubuntu como lo hacia , despues quise desinstalarlo y me sigue saliendo igual Kubuntu pero mas alla de eso lo q me molesta es que me han quedado todas las aplicaciones tanto las de internet como las de oficina y quiero sacarlas pero que tengo q hacer?? sacarlas una x una?? crei que desinstalando el escritorio de kubuntu las aplicaciones solas se desinstalaban...

---

### Post by Al_maverick on 2007-05-19
En realidad, por como funciona el sistema de paquetes, al sacar un paquete, instala el resto que necesita por dependencias, pero no al reves. Asi que podes desintalar el kubuntu-desktop, pero no te desinstala las aplicaciones. Esas las vas a tener que desinstalar a mano.

---

### Post by seba2611 on 2007-05-20
Gracias!!! ya me pongo a laburar!!, igualmente me quedo una duda siempre que quiera instalar el escritorio de kubuntu se me van a unir todas las aplicaciones?? lo q quiero es que por un lado dea KDE y por el otro GNOME se puede??.

---

### Post by jpmorelli on 2007-05-20
Soy casi un espcialista en el tema, ya que me paso de un escritorio a otro a cada rato, asi que te voy a poder ayudar.
Para volver a una instalación de gnome limpia tenés esta web, probada por mi y funciona ok:

[http://psychocats.net/ubuntu/puregnome]("http://psychocats.net/ubuntu/puregnome")

En la misma web tenés para dejar kubuntu puro y Xubuntu puro tambien.

Despues, una cosa es el gestor de entrada que puede ser KDM o GDM. Para poder elegirlas usas el siguiente comando:

sudo dpkg-reconfigure gdm
o
sudo dpkg-reconfigure kdm

cuando los dos estan instalados podes correr cualquiera que vas a poder elegir con cual queres entrar a la X.

Con respecto a la barra de progreso de carga, eso es otra cosa. Podés usar un utilitario muy copado que se llama SUM (Startup-Manager) que lo encontré en el foro acá:

[http://web.telia.com/~u88005282/sum/screenshots.html]("http://web.telia.com/~u88005282/sum/screenshots.html")

Te permite no solo cambiar las barras sino poner otras resoluciones, cambiar el tiempo del grub, ponerle colores al grub, etc.
Lo tenía anotado como hacerlo desde linea de comando, eran 3 líneas y no se donde quedó.
Espero te sirva, suerte !

---

### Post by seba2611 on 2007-05-21
Buenisimo toda la info muchas gracias ya estoy laburando con todo, lo primero lo hice y solo quedo alguna aplicacion q la voy a sacar a mano.

Muchas gracias!!

---

### Post by jayflower on 2007-05-21
Buena jmorelli! Yo tenía ganas de probar KDE sin sacar Gnome, porque en su momento en mi primer contacto con Linux KDE se chupaba mi poca memoria, no se como andará ahora en esta PC, pero tenía cosas que me gustaban más. Aunque hoy en día Gnome me parece que tiene una pinta bastante mejor que hace 6 años, muy buenas aplicaciones. A proposito, la preguntonta: cual gusta más en general ? Gnome O KDE?
Saludos

---

