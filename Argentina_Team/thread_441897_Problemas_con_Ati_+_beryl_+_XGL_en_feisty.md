---
title: "Problemas con Ati + beryl + XGL en feisty"
date: 2007-05-13
forum: Argentina Team
---

### Post by seba2611 on 2007-05-13
Bueno no queria postear esto pero no se que mas hacer me gano!!! tengo el feisty y quise instalar beryl y lo hice mas de una vez pero no hay caso seguis estos dos tutoriales:

[http://damr.net/blog/2007/05/07/howt.../#comment-5884](http://damr.net/blog/2007/05/07/howt.../#comment-5884)

[http://elnorber.wordpress.com/2007/04/26/instalar-beryl-02-en-ubuntu-feisty-con-tarjeta-grafica-ati/#comment-1452](http://elnorber.wordpress.com/2007/04/26/instalar-beryl-02-en-ubuntu-feisty-con-tarjeta-grafica-ati/#comment-1452)

Tambien instale los drivers de mi ATI X550 desde : Sistema - administracion - gestor de controladores y me baja el driver 8.34.8 la cosa es que luego de seguir el tutorial y con el driver instalado tengo la aceleracion 3d y una vez q reinicio ejecuto el beryl desde herramientas del sistema y la primera vez me andubo barbaro pero despues q reinicio de nuevo no me anda mas, me carga el diamante pero solo tengo 2 escritorios los cuales cambio como si el diamante noe estuviera ahi , entonces pruebo el comando "glxinfo | grep direct" y tengo este resultadodentro de la sesion XGL)

seba@seba:~$ glxinfo | grep direct
Xlib: extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

ahora este mismo comando lo ejecuto en la sesion sin XGL y el direct rendering me sale : YES.
Aparentemente se desactiva la aceleracion 3d en esa sesion y es por eso que beryl no anda, alguno tuvo el mismo problema , se puede solucionar esto de alguna manera???.

Muchas gracias!!!.

---

### Post by jbro on 2007-05-13
Buenas,

Tengo un ATI X300 pero he tenido unas experiencias muy parecidas a las que describe. En mi primer intento de instalar Beryl, lo logré hacer pero sin utilizar el driver propietario de ATI y andaba bien un par de días, pero repentinamente dejó de funcionar y no sé por qué ya que no hice ningún cambio a la configuración de Beryl, pero descubrí que si corría "beryl" desde un terminal o Alt+F2, entonces funionaría y así agregué ese programa a mi sesión de GNOME. Después de hacer esto, todo funcionaba bien.

Un tiempo después (es decir, hace dos o tres días) decidí intentar utilizar el driver de ATI ya que el rendering con el driver radeon era un poco lento. Instalé el driver de ATI igual como hizo Ud. y todo marchaba bien - estaba activado el "direct rendering" y vi una mejora tremenda en la velocidad del rendering. Entonces instalé Beryl y todo parece bien, sin embargo, cuando intenté ```
fgl_glxgears
``` para probar el nuevo entorno vi el mensaje que vio Ud. - eso de Xfree-DRI no está instalado. Sin embargo, me parece que el rendering es mucho mejor y las animaciones se ven bien. Investigué y encontré muchas personas que tenían el mismo problema y al parecer hay algún tipo de conflicto entre XGL y DRI y hasta el momento no he encontrado una solución, pero dado que me parece que el rendimiento es mejor, me quedo con el driver propietario y Beryl XGL. Si encuentro una solución al problema actualizaré este hilo con ella.

Saludos y suerte,
jbro

---

### Post by seba2611 on 2007-05-13
Muchas gracias si encontras algo por favor ponele yo sigo buscando mientras tanto.

---

### Post by lavaramano on 2007-05-13
yo tengo ati y miles de problemas para configurarla decentemente y que todo sea feliz en gnu/linux con ati.
y siempre tenia un problema para <editado por beuno> complicarme </editado por beuno> la vida.

[http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=26907](http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=26907)

en fin.

---

### Post by seba2611 on 2007-05-13
Esta bien entonces no deberia poder usarse pero por que hay tutoriales en donde a todos les funciona , tiene q haber una manera.

---

### Post by lavaramano on 2007-05-13
> **seba2611 said:**
> Esta bien entonces no deberia poder usarse pero por que hay tutoriales en donde a todos les funciona , tiene q haber una manera.

si, supongo que se deberia poder.
de hecho vi videos de flacos con ati que lo hacian funcionar y eso.
creo que beuno tb tiene ati y el tenia beryl (o alguno de esos) 

pero bueno, yo te hablo por experiencia personal. tengo ati radeon mobile xpress 200m y no va ni para el costado ....

---

### Post by nachotronics on 2007-05-14
Yo tengo XGL-Beryl en con una ATI X1400, andando de 10. Fijate que versión del paquete beryl-core estás usando. A mí la última no me funciona, la penúltima si, es la 0.2.0~0beryl1. Podes instalarla con synaptic, buscala, seleccionala y hace click en paquete -> forzar versión, ahi elegis la 0.2.0~.

Este howto es de los más completos: **_[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)_**

Cuando estás en una sesión XGL, el comando "glxinfo | grep direct" siempre dice que no tenés direct rendering, eso lo tenés que chequear en tu sesión por defecto de gnome, no te preocupes si en la otra no aparece, igual funciona. Muchas funciones del driver de ATI no andan bajo XGL, por ejemplo fgl_glxgear, o el modo de bajo consumo(casi 40 minutos menos de autonomia que en la sesión común).

Espero que ésto ayude :wink:

---

### Post by seba2611 on 2007-05-14
Es tal cual me decis, en la sesion XGL cuando pongo el comando : "glxinfo | grep direct"  me da rendering :NO y en la sesion gnome normal me da que si, los drivers lo instale desde el ubuntu, los controladores restringidos , lo mas raro es que una vez q lo termino de instalar el beryl funciona, despues reinicio una vez y chau no anda mas, se carga al inicio pero no anda y solo me salen 2 escritorios disponibles, me dijeron en un blog que pruebe con los drivers "radeon" a ver q pasa.

---

### Post by jbro on 2007-05-14
Y en esa segunda vez que corres Beryl y solamente sale con dos escritorios, ¿aparece algún error en /var/log/Xorg.0.log? Otra pregunta es ¿cómo arrancas Beryl cuando inicias una sesión? He visto dos maneras - una manera es que creas un script que corre primero beryl-manager y después gnome-session y la segunda es que corres beryl-manager como parte de tu sesión GNOME (ve System->Preferences->Session). Para mi, las dos me han funcionado, pero claro que todo puede depender de tu configuración.

Respecto a intentar Beryl con el driver radeon, así lo hice en mi primer intento y funcionaba pero no hubo efectos 3D y tambien el rendering de algunos efectos eran un poco lento y "entrecortado". De repente funciona mejor para ti. Usé  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29") para instalar Beryl de esta manera. De repente funcione mejor con tu ordenador.

Si puedes revisar Xorg.0.log y posteas las advertencias y errores que encuentras allí podemos ver cuál es el problema.

Suerte y saludos,
jbro

P.D. Para Beryl con XGL yo tenía que pegar la versión de Beryl como menciona nachotronic (0.2.0~beryl) ya que la versión que se instala por defecto (0.2.1...) no marchaba bien.

---

### Post by seba2611 on 2007-05-16
Bueno paso a comentar que pude hacerlo andar con el driver libre osea el " RADEON" segui los pasos en esta guia :

[http://www.ubuntu-es.org/index.php?q=node/46437]("http://www.ubuntu-es.org/index.php?q=node/46437")

Me andubo perfecto , creo que igual que cuando me andubo una vez con el XGL y el driver propietario de ATI y me lo carga al inicio con los 4 escritorios, ahora voy a tener q crear una sesion en la que se cargue sin el beryl, tengo q ver como hacerlo.

Gracias por la ayuda!!

---

### Post by JAntonioS on 2007-05-23
Hola, veo que los tutoriales que ya pusieron son parecidos a este; pero como sea lo pongo. Igual y le entiendes más a este.

[http://www.andreimosso.com/?p=42](http://www.andreimosso.com/?p=42)

Suerte.

---

### Post by trasto on 2007-05-29
Hola que tal:

Tengo un portatil acer 1652wlmi con una grafica ati x300 es un centrino M740 con 1 gb de ram

instalé ubuntu feisty, actualizaciones y beryl con aixgl siguiendo este tutorial:

[http://http://ubuntu-beryl.com.ar/2007/04/instalar-beryl-en-ubuntu-feisty-fawn_26.html]("http://http://ubuntu-beryl.com.ar/2007/04/instalar-beryl-en-ubuntu-feisty-fawn_26.html")

donde explica como instalarlo:
   
   deshabilitando el driver nativo fglrx
 
   y modificando algunas cosas del xorg.conf como ahi indica

   luego se cambian las sources y se instala sin mas problemas

lo que me ocurre es que despues de estar usando 5 10 o 15 min beryl, flipando con sus movidas se me cuelga la pantalla, y digo pantalla por que el raton funciona, no puedo hacer click sobre nada pero se mueve, accedo por ssh, y el sistema esta UP, pero no puedo matar el gdm ni conseguir hacer nada mas, el /var/log/messages no arroja nada y el /var/log/Xorg.0.log no se que tiene q decir, si es fallo de ahi o de donde.

Teneis noticia de esta inestabilidad.
Para rematar si cambio a compiz no se ven los bordes de las ventanas, un desastre. A ver si alguien me puede tirar una cable, plis.

---

### Post by jpmorelli on 2007-05-29
Por el tema de los bordes yo tuve en Edgy el mismo problema y lo solucioné con esto:

append the following to your /etc/X11/xorg.conf in the “Device” section:

      Option         "AddARGBGLXVisuals" "True"
      Option         "RenderAccel" "True"
      Option         "AllowGLXWithComposite" "True"
      Option         "backingstore" "True"
      Option         "TripleBuffer" "True"

Fuente: [http://nlindblad.org/author/admin/](http://nlindblad.org/author/admin/)

Creo que con la primera linea ya es suficiente pero bueno... de más está decir que hay que reiniciar para que los cambios en xorg sean tomados.
Suerte !

---

