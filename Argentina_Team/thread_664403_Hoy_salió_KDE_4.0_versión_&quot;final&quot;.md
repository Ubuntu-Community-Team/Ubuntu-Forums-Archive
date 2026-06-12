---
title: "Hoy salió KDE 4.0 versión &quot;final&quot;"
date: 2008-01-11
forum: Argentina Team
---

### Post by facundocorradini on 2008-01-11
Bueno gentes...

Seguramente habrán visto en más de un post que KDE no es mi escritorio favorito... De hecho, me las he arreglado para no usar ningún programa que use KDE o librerías QT, a un punto de casi anti-fanatismo...

Pero bueno, hoy se liberó la versión 4.0 de KDE, y me ha ganado la tentación. Ya la estoy bajando, es bien pesadita así que tengo para un rato...


Solo quiero recordarles que KDE 4.0 "no es KDE 4", ya que es una versión un poco incompleta. 
Teóricamente, KDE4 vá a estar listo para el público masivo recién con la versión 4.1, la cual se espera para fin de este año....


En fin, cuando lo pruebe les posteo mi opinión. ;)

EDIT: q bobo!, por no fijarme bien termine con kde 3... jeje.. ahora bajo el correcto...

---

### Post by spg76 on 2008-01-11
Yo actualicé a la versión final ayer. Lo venía actualizando desde RC1 y la verdad que fue mejorando en cada versión. Creo que todavía le falta un poco (como dijo Facundo "todavía no está listo para el público masivo"). Cuando se termine de desarollar Plasma, la versión de kdepim sea estable, salgan Amarok 2 y Koffice 2, y haya muchos programas portados se podrá decir que está preparado para el usuario "común". Para esto faltan varios (¿muchos?) meses.
Para los que quieren instalar o probar Kubuntu con KDE 4.0.0 pueden seguir las instruccions o bajar el LiveCD de [http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)

---

### Post by brunovecchi on 2008-01-11
> Seguramente habrán visto en más de un post que KDE no es mi escritorio favorito...

Justamente ayer lo instalé para probarlo... tardé veinte minutos en marearme, descomponerme y desinstalarlo. Debo estar malcriado por la simpleza de Gnome. ¡Tantas aplicaciones, y todas comienzan con K! No es para mi.

Por favor no me insulten los fanas de KDE, quizás estaba yo en un mal día. :confused:

---

### Post by qntal on 2008-01-11
ayer instalé la RC2 desde los repo y a los 5 minutos me marcó la actualización a 4.0 :P

estuve boludeando un rato y... esta lindo, pero volví a gnome. a medida que lo siga probando / tweakeando comentaré.

---

### Post by facundocorradini on 2008-01-11
Pues ahora sí, lo acabo de probar...

Lo bueno:

Lo primero que se nota es una estética muy pulida y agradable. Muy buen trabajo de la gente de Oxygen.

Lo malo:

El nuevo menú K es una burla a la usabilidad .( <-- punto)

Por lo demás,no se ven grandes cambios,al menos no superficialmente...  ya lo voy a exprimir un poquito más para ver que tal se porta...


(obvio, a mí nadie me saca de mi querido E17...jeje)

---

### Post by spg76 on 2008-01-11
> **facundocorradini said:**
> 
Lo malo:

El nuevo menú K es una burla a la usabilidad .( <-- punto)


Sin duda uno de los puntos más criticados. Tal es así que en las últimas versiones agregaron la versión "clásica" del menú K a los widgets como alternativa.
Con respecto a esto, hay un proyecto muy interesante que se llama Raptor que plantea una alternativa más original y en teoría con más usabilidad. Pueden ver info y capturas en [http://pinheiro-kde.blogspot.com/2007/10/raptor-join-fun.html](http://pinheiro-kde.blogspot.com/2007/10/raptor-join-fun.html) y en [http://commit-digest.org/issues/2007-11-04/](http://commit-digest.org/issues/2007-11-04/)

---

### Post by pablo0469 on 2008-01-12
Quisiera ver que tal va el KDE4, pero que paquetes instalo desde synaptic? El chorizo de alternativas es interminable....

Gracias y Saludos.

---

### Post by v1ncent on 2008-01-12
> **pablo0469 said:**
> Quisiera ver que tal va el KDE4, pero que paquetes instalo desde synaptic? El chorizo de alternativas es interminable....


Desde la consola, si tenemos GNOME:
Primero: si ya habíamos instalado KDE4, ahora tenemos que desinstalarlo con el siguiente comando:
$ sudo aptitude remove kdelibs5 kde4base-data kde4libs-data

Y luego instalamos nuevamente:
$ sudo gedit /etc/apt/sources.list
Agregamos esta linea:
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main
$ sudo aptitude update
$ sudo aptitude install kde4-core

A pesar de que el repositorio especifica que es para Kubuntu, también funciona con Ubuntu.

---

### Post by v1ncent on 2008-01-12
Tengo la esperanza de que a lo largo del desarrollo de la versión 4, KDE se muestre todo su potencial, las nuevas tecnologías (como plasma) son muy prometedoras, espero que le saquen provecho.

---

### Post by leo_rockway on 2008-01-12
como quizas sepan yo soy un kde fanboy y hace un ratito instale kde 4 y la verdad que pinta que a futuro va a estar bueno, pero de momento le falta y mucho.

como comente recien en #ubuntu-ar-cafe ... yo le dejo una ficha a kde 4, pero por ahora para el dia a dia me quedo con kde 3.5.8

---

### Post by pablo0469 on 2008-01-13
> **v1ncent said:**
> Desde la consola, si tenemos GNOME:
Primero: si ya habíamos instalado KDE4, ahora tenemos que desinstalarlo con el siguiente comando:
$ sudo aptitude remove kdelibs5 kde4base-data kde4libs-data

Y luego instalamos nuevamente:
$ sudo gedit /etc/apt/sources.list
Agregamos esta linea:
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main
$ sudo aptitude update
$ sudo aptitude install kde4-core

A pesar de que el repositorio especifica que es para Kubuntu, también funciona con Ubuntu.

Gracias Vincent, ya que la noche recien comienza, lo estoy bajando :)

---

