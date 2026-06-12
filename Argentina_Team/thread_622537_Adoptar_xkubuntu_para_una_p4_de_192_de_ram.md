---
title: "Adoptar x/k/ubuntu para una p4 de 192 de ram"
date: 2007-11-24
forum: Argentina Team
---

### Post by valucha on 2007-11-24
[COLOR="DarkOrchid"]Hola, estoy tratando de ayudar a un amigo con su compu ya que con XP está por explotar.
Quería saber cçomo hacer para instalarlo y que funcione lo más veloz posible. 
Ahora está usando Xubuntu 7.10 pero la verdad anda re lento. No sé si es porque no se instalaron bien los drivers de su tarjeta de video (tnt2) o porque no tiene el hard suficiente.

¿Alguna forma de adaptar Xubuntu par aque ande más rápido? ¿instalando versiones más viejas tal vez?.

Desde ya muchas gracias.[/COLOR]

---

### Post by santiagoward2000 on 2007-11-24
> **valucha said:**
> [COLOR="DarkOrchid"]Hola, estoy tratando de ayudar a un amigo con su compu ya que con XP está por explotar.
Quería saber cçomo hacer para instalarlo y que funcione lo más veloz posible. 
Ahora está usando Xubuntu 7.10 pero la verdad anda re lento. No sé si es porque no se instalaron bien los drivers de su tarjeta de video (tnt2) o porque no tiene el hard suficiente.

¿Alguna forma de adaptar Xubuntu par aque ande más rápido? ¿instalando versiones más viejas tal vez?.

Desde ya muchas gracias.[/COLOR]

Hola valucha,
Mirá, a mí Xubuntu 7.10 me anda lo más bien con una Celeron con 192mb de RAM. No creo que instalar una versión vieja ayude.
Sobre la placa de video, le instalaron Compiz? Sino no me imagino que pueda ser eso (aunque no estoy completamente seguro).
Sino podrían probar usar Fluxbuntu, que es mucho más rápido.
Saludos!

---

### Post by valucha on 2007-11-25
[COLOR="DarkOrchid"]No, ni intenté ponerle compiz. Pero por ejemplo si tenía el Rithmbox y el gaim abierto de a ratos se tildaba.
A mi me parece que xubuntu es muy  pesado, le anda igual o un poquitín más rápido que Windows XP que tiene como 5 años sin formatiarse :s.[/COLOR]

---

### Post by facundocorradini on 2007-11-25
Valucha:

instalar una versión más vieja no va a ayudar. Los requerimientos de hard siguen siendo los mismos desde el primer Xubuntu. 

Podrías probar desactivar algunos de los servicios que se cargan al principio.


Igualmente, el caso que presentas es bastante raro: Xubuntu corre más que bien en una de mis compus, de 900mhz con 128 MB de RAM...

---

### Post by monofluor on 2007-11-25
El tema de la velocidad tambien va a depender de los programas que instales, por ej. si instalas programas de gnome o kde (Rithmbox, amarok) estas instalando tambien librerias de estos entornos... que se cargan cada ves que levantas esos programas y hacen mas pesado el sistema.
Entonces, ayuda mucho que te fijes cuales son las dependencias de  los programas antes de instalarlos...
Ademas hay programas mas livianos que otros, podes usar en cuenta de:
Rithmbox --> xmms o beep-media-player
totem vlc --> gxine
openoffice ---> abiword y gnumeric

la seleccion de programas que trae xubuntu esta pensada con ese criterio (programas livianos)

Podes buscar tambien en google como optimizar ubuntu.. desctivando servicios.. etc..

Y por ultimo probar zenwalk que es muy parecida pero la note mas liviana que xubuntu.

---

### Post by Hei Ku on 2007-11-25
Podes probar tambien con Fluxbuntu, la distro basada en Ubuntu que usa Fluxbox, que es mas liviano. Tambien tenes Elubuntu, que usa Enlightment.

---

### Post by valucha on 2007-11-25
[COLOR="DarkOrchid"]Los programas con los que probé Xubuntu en esa máquina fueron los que vienen por defecto.

No podrías instalarle FLuxbox o Enlightenment porque es un chico que recién migra de WIndows y que nisiquiera tenía la más pálida idea de como hacer algo en Ws... Le mostré screenshots de enlightenment y de fluxbox y dice que no iba a entender nada. 
Igualmente dijo que se iba a poner a aprender, por eso me parecía que para empezar xubuntu iba a andar bien...

Me desilucionó bastante con la velocidad, pero ahora que recuerdo yo le había pueso xubuntu a una p4 con 128 de ram con placa de video integrada y andaba 10 veces más rápido.
¿Por qué puede ser esa falta de velocidad? [/COLOR]

---

### Post by facundocorradini on 2007-11-26
Por eso, el hardware que tiene debería correr Xubuntu sin problemas. 
De hecho, hasta podría correr decentemente bien Ubuntu.

Segura que no hay problemas de hard? el disco medio roto? el procesador sobrecalentando por un cooler tapado de mugre? ...

Sino fijate si no tiene activado algún servicio que le esté consumiendo mucha memoria/procesador.

Me parece muy raro lo que está pasando...

---

### Post by psiwoods on 2007-12-07
Hola valucha... se que esto es un post en un foro de ubuntu pero podrias probar tal vez otra distro... yo uso ubuntu desde hace un tiempo y sin problemas,,, pero mi pc, Pentuim III 500Hz y 256 de ram andaba re lenta... he probado con puppy linux y los resultados son asombrosos.. sin duda (cronometrado) 3 veces mas rapido...

Puppy es facilisimo de usar y si bien viene en live cd se puede instalar con PUPPY UNIVERSAL INSTALLER que viene en todas las distros por defecto.. ademas una un win manager muy similar al windows... 

busca una llamada Puppylinux NOP

bajala de aca:
[http://www.metamirrors.nl/backend/get.php?lnk=http://download.tuxfamily.org/nop/puppy-301-NOP-rev1.iso](http://www.metamirrors.nl/backend/get.php?lnk=http://download.tuxfamily.org/nop/puppy-301-NOP-rev1.iso)

Esa versio viene con un XFCE hecho simil al XP...

es livianita... tiene sus limitaciones pero yo a esta altura la uso en lugar de ubuntu porque pude ponerle todo lo que me faltaba... eso si... olvidate de apt-get... pero hay muchos paquetes que andan barbaro...

---

### Post by lugonesjoaquin on 2007-12-08
Aver si Windows XP le anda bien, entonces no creo que sea un problema de Hardware. A menos que la parte del disco donde se instalo este dañada... Aunque no creo.

Para mí va por el lado de que Xubuntu ya no es lo que se decía antes. A dejado de ser una distribución para equipos viejos, pero no por la culpa de la misma, sino por XFCE que en las últimas versiones se a vuelto bastante más pesada que las anteriores versiones.

¿Mi recomendación? SImplemente probar otra dstribución, y como vos estas muy acostumbrada a Ubuntu y a su forma de gestionar los paquetes y todo eso entonces te recomiendo que uses Debian o alguna derivada que no sea Ubuntu (Que es bastante pesadita...)

Ahora mismo escribo desde una PIII 500mhz con 128mb de ram, perfectamente mientras escucho música (Eso sí, con audacious, nada pesado) y chateo en el emesene y todo bien. Nada de trabarse. Y eso que uso XFCE... Con este mismo sistema usé Fluxbox que me encantaba y era muy rápido, pero solo por cambiar instalé Gnome y tambien perfecto, obviamente bastante mas lento que Fluxbox, pero el Gnome de Debian no es tan pesado como el de Ubuntu. Y despues le puse Xfce y es con lo que me quedé de momento. =D

Una distro que te puedo recomendar derivada de Debian y que use mucho tiempo en mi otra PC: una P4 con 256MB de ram a 2.8 GHZ es Tuquito, que es Argentina y es basicamente Debian con KDE, con muchos programas que de verdad sirven y bien personalizado para que sea bien lindo.

Creo que irse por Puppy Linux sería algo muy extremo... ;)

ZenWalk como ya te dijeron antes es otra muy buena opción ;)

Aunque es raro que en ese equipo ande lento che... Practicamente ningun Linux debería andarte lento.. Revisa bien aver si no hay algo que esta sobrecalentando..;)

---

### Post by valucha on 2007-12-08
[COLOR="DarkOrchid"]Y la verdad que la compu es re vieja y encima cuando fui a la casa y vi estaba metida en una especie de "cajon" osea un lugar que tenia el escritorio en el que entraba apretada y para el colmo con miles de papeles encima tapando la única salida de aire que tenia, osea, 0 ventilación. Le hice sacar los papeles y corrimos la compu para  adelante para que tenga ventilación.

Voy a vr que fue lo que hizo que andar tan lento... Le bajé programas más livianos para que escuche música, chatee, navegue. Tipo Opera,emesene y abiword y todo eso. Pero no habia caso, juro que poniamos una canción mientras navegabamos y chateabamos y se aparaba la cancion por unos segundos :S.

Nunca se llgó a tildar, el sistema corría, pero andaba igual o un toquesiiiiin más rápido que Windows.

Voy a reinstalar sino pruebo con Zenwalk que lo probe en mi compu y me encanto

Mil gracias por su opinion :)[/COLOR]

---

### Post by pante on 2007-12-08
Hola

Algo más sencillo de hacer es en ese mismo Xubuntu instalar Fluxbox (con Synaptic o Apt-get), y al iniciar sesión seleccionarlo para probar que tal corre. Tengo Xubuntu y le agregué Fluxbox instalando (con Synaptic) **fluxbox**, **fluxconf** y **gsetroot** y me funciona perfecto.

Saludos

---

### Post by Hei Ku on 2007-12-08
> **pante said:**
> Hola

Algo más sencillo de hacer es en ese mismo Xubuntu instalar Fluxbox (con Synaptic o Apt-get), y al iniciar sesión seleccionarlo para probar que tal corre. Tengo Xubuntu y le agregué Fluxbox instalando (con Synaptic) **fluxbox**, **fluxconf** y **gsetroot** y me funciona perfecto.

Saludos

Como arrancas el entorno de fluxbox una vez que lo instalaste en el xubuntu?

---

### Post by pante on 2007-12-08
> **Hei Ku said:**
> Como arrancas el entorno de fluxbox una vez que lo instalaste en el xubuntu?

Conozco una forma de entrar al entornode Fluxbox, a la que llego por una de tres vías. Paso a detallar.

* Estando dentro de Xubuntu con Xfce ir a "Salir" (como si lo fuera a apagar) y selecciono la opción "Log out". Con eso cierra Xfce y vuelve a la ventana de Log In;

* La opción drastica. Estando dentro de Xubuntu con Xfce apretar las teclas Ctrl+Alt+Back space (retroceso); con esto terminan (casi) todos los programas que estén corriendo y vuelve a la ventana de Log in;

* Y la opción conocida por todos. Cuando uno prende o ha reiniciado la PC, se inicia Ubuntu y llega a la ventana de Log in.

Cuando ya esté en la ventana de Log in, antes de poner usuario y contraseña, hago clic en Session y aparece un menú. De ese menú selecciono fluxbox y lo aplico haciendo clic en Change session. Después de entrar usuario y contraseña, Ubuntu pedirá confirmar si cambio de entorno definitivamente, o sólo por esta sesión, o si cancelo. Elijo solo por esta sesión para que en el próximo log in entre directamente a Xfce.

**Resumen:**

1) Salir de Xfce con Log out, Ctrl+Alt+Retroceso o reiniciando,

2) Cambiar de tipo de sesión por fluxbox,

3) Ingresar nombre de usuario y contraseña, 

4) Confirmar si el cambio es sólo por esta sesión o definitivo.

Saludos

PS: soy nuevo en esto y tengo mucho que aprender, así que si la erré corríjanme sin asco.

---

