---
title: "Problema, desaparecen los bordes!!!"
date: 2007-11-19
forum: Argentina Team
---

### Post by xpelaox on 2007-11-19
Hola gente, volvi con un nuevo problema... no se bien por que, pero cada tanto de la nada se me desaparecen los bordes de las ventanas(con las cruzecitas y todo), y no logro encontrar un parametro que diga "es por esto" se como volverlos a poner, pero es medio molesto.... alguien sabe como lo puedo solucionar?

Chas gracias!

---

### Post by sajnox on 2007-11-19
Cual es el procedimiento con el que las volves a cargar??

Ese error es comun con compiz, lo estas usando??

Que decorador de ventanas usas, emerald o gtk?

Tiranos un par de datos mas que lo podes solucionar

---

### Post by dj_isaco on 2007-11-19
a mi me pasa algo parecido, se me sale el esmerald y vuelve a metalyc creo q se escriben asi no? bueno y en ese proceso se me queda tildada la maq, pero despues anda normal ¿xq sera?
a tambien esto me acaba de ocurrir se me desaparecio la barrita de awn y avaces no la carga cuando inicio seccion.me habre mando algun moco jeje "******"

---

### Post by arielboss on 2007-11-19
A mi me pasa algo similar, pero el tema que yo tengo dramas solo con el Kde, en Gnome me anda de 10, pero en Kde cuando instale Compiz, se me desconfiguro todo, y no se como volver atras!

---

### Post by xpelaox on 2007-11-19
este es el procedimiento que uso:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
sudo nvidia-xconfig -composite
sudo nvidia-xconfig -allow-glx-with-composite
sudo nvidia-xconfig -render-accel
sudo nvidia-xconfig -add-argb-glx-visuals
Tras esto, reinicia el servidor gráfico con Ctrl+Alt+Borrar. Si el servidor gráfico no arranca y arranca Linux en modo texto, escribe estas órdenes para volver a la situación anterior:
sudo mv /etc/X11/xorg.conf.orig /etc/X11/xorg.conf
startx

Creo que Tengo Compiz-fusion... es el que viene con la 7.10 no?
Tengo emerald instalado, pero la verdad no uso ningun theme... dicen que lo borre?

---

### Post by sajnox on 2007-11-19
Si estas usando compiz te aconsejo que te instales el fusion-icon 

```
 sudo apt-get install fusion-icon
```

Y cuando te pasa eso, podes probar con dos cosas

Desde el icono recargas el compiz (Reload window manager) o ejecutas con alt+f2 compiz --replace

O recargar el decorador de ventanas.

Eso te lo deberia solucionar

Exitos!!

---

### Post by xpelaox on 2007-11-20
> **sajnox said:**
> Si estas usando compiz te aconsejo que te instales el fusion-icon 

```
 sudo apt-get install fusion-icon
```

Y cuando te pasa eso, podes probar con dos cosas

Desde el icono recargas el compiz (Reload window manager) o ejecutas con alt+f2 compiz --replace

O recargar el decorador de ventanas.

Eso te lo deberia solucionar

Exitos!!

no encuentra el paquete:S

---

### Post by santiagoward2000 on 2007-11-20
> **sajnox said:**
> Si estas usando compiz te aconsejo que te instales el fusion-icon 

```
 sudo apt-get install fusion-icon
```

Y cuando te pasa eso, podes probar con dos cosas

Desde el icono recargas el compiz (Reload window manager) o ejecutas con alt+f2 compiz --replace

O recargar el decorador de ventanas.

Eso te lo deberia solucionar

Exitos!!

¿Estás seguro que fusion-icon está en los repositorios? Por lo menos yo no lo encuentro en los míos. Yo lo instalé con un .deb que encontré en otro post y me anda sin problema. Si quieren puedo agregarlo como attatch.

---

### Post by sajnox on 2007-11-20
Que tonto!!! Me devolvio search por que lo tengo instalado, si podes, pone el link para bajarlo

Saludos

---

### Post by santiagoward2000 on 2007-11-20
> **sajnox said:**
> Que tonto!!! Me devolvio search por que lo tengo instalado, si podes, pone el link para bajarlo

Saludos

Bueno, la verdad que ya perdí el link, pero todavía tengo el .deb acá, asique lo pongo como attach.

---

### Post by por100pre1 on 2007-11-20
Presiona ALT+F2 y usa este comando:

```
emerald --replace
```

---

### Post by xpelaox on 2007-11-20
santiagoward2000 mil gracias! ahi lo instalo=D

---

### Post by santiagoward2000 on 2007-11-20
> **xpelaox said:**
> santiagoward2000 mil gracias! ahi lo instalo=D

De nada! Espero que te sirva!

---

### Post by s4ntis0 on 2008-03-10
Hola gente que tal, les cuento que instale ubuntustudio7.10 tras una batalla de semanas, asi que imaginen lo qeu me esta costando todo  Instale compiz-fusion y emerald y por fin logre hacer funcionar los efectos.pero no me acuerdo que mas  toque en Compiz Manager (Advanced Desktop Effects Settings)  y  ahora no tengo los iconos de las ventanas para Maximizar, Mininimizar, y Cerrar. Solamente cuando desactivo los efectos en Apariencia vuelven estos . Otro dato es que cuando abro el Emerald Theme Manager no entra completamente en la pantalla ni tampoco puedo arrastarlo o moverlo. Ya probe instalando fusion-icon, Tambien reinstale metacity pero tampoco funciona. :confused:  Ya me recorri varios threads y otros foros pero no encuentro nada para que esto funcione otra vez-, ya llevo varias horas con esto  :(

---

### Post by sajnox on 2008-03-10
Es comun el error que te tira, fijate que decorador de ventanas te funciona con compiz, en mi experiencia funciona mejor emerald pero no necesariamente es asi.

Desde el fusion-Icon entras a los settings de compiz y en decoracion de ventanas escribis en el comando emerald --replace

Tambien te sugiero que en crash handler uses la linea compiz --replace para que te lo recargue cuando se cuelga

Cualquier duda contanos

---

### Post by s4ntis0 on 2008-03-10
No entiendo bien como ir a los settings de compiz y ...

quote: Tambien te sugiero que en crash handler uses la linea compiz --replace para que te lo recargue cuando se cuelga -- / quote

es coreano esto para mi en su estado mas puro.

---

### Post by s4ntis0 on 2008-03-10
Ahh algo entendi...pero igual fijate que no se si es aca que tengo que tipear ese comando?

configcompiz manager:

[[img]http://www.upload-images.net/imagen/c1b26b3613.jpg[/img]](http://www.upload-images.net)


y aca supuestamente ejecuto el comando compiz --replace asi a secas?

[[img]http://www.upload-images.net/imagen/38c7bd490c.jpg[/img]](http://www.upload-images.net)

perdon por la insistencia pero la verdad tras que me costo muchisimo instalar todo y hacer funcionar los efectos me da bronca que no pueda hacer esta tarea sencilla  , gracias de antemano.

---

### Post by s4ntis0 on 2008-03-10
Aca les dejo de paso el "manager" del emerald 

[[img]http://www.upload-images.net/imagen/f3a4e1397c.png[/img]](http://www.upload-images.net)

gracias de nuevo y espero puedan ayudarme

---

### Post by santiagoward2000 on 2008-03-11
> **s4ntis0 said:**
> y aca supuestamente ejecuto el comando compiz --replace asi a secas?

perdon por la insistencia pero la verdad tras que me costo muchisimo instalar todo y hacer funcionar los efectos me da bronca que no pueda hacer esta tarea sencilla  , gracias de antemano.

Hola!
Si, ahí, donde dice **comando** tenés que poner **emerald --replace**. Después, tocá Alt+F2 y escribí
```
emerald --replace
``` para reiniciarlo.
Con eso tendría que andar. Cualquier cosa avisá.
Suerte!

---

### Post by s4ntis0 on 2008-03-11
sigue sin funcionar...hay alguna manera para desinstalar todo lo que es compiz y emerald y volver a instalar?

---

### Post by s4ntis0 on 2008-03-11
acabo de desinstalar con synaptic todo lo referido a emerald y compiz...y sigo sin botones en los cuadro de ventana . con lo unico que vuelven es cuando en Apariencia elijo sin efectos visuales.

[[img]http://www.upload-images.net/imagen/accd7a6142.png[/img]](http://www.upload-images.net)

---

### Post by guisheca on 2008-03-11
Copio y pego del foro de ubuntu en españa:
> 
Solución 1 (automática y sencilla)

La descubrí de casualidad trasteando la tarjeta gráfica. Al menos a mí (y a casi todo el mundo, según los comentarios) esta solución me ha funcionado perfectamente, y es el método más sencillo para configurar el xorg.conf. Hay que escribir estas órdenes en la consola (puedes copiar y pegar):

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig 

sudo nvidia-xconfig -composite 

sudo nvidia-xconfig -allow-glx-with-composite 

sudo nvidia-xconfig -render-accel 

sudo nvidia-xconfig -add-argb-glx-visuals

Tras esto, reinicia el servidor gráfico con Ctrl+Alt+Borrar. Si el servidor gráfico no arranca y arranca Linux en modo texto, escribe estas órdenes para volver a la situación anterior:

sudo mv /etc/X11/xorg.conf.orig /etc/X11/xorg.conf

startx

Estas órdenes sirven para restaurar la copia de seguridad y volver a arrancar el servidor X.

Solución 2 (si no funciona la primera)

Hay que editar el archivo “xorg.conf”:
Pulsar Alt+F2, y en la caja que aparece, escribir:

gksudo gedit /etc/X11/xorg.conf

Una vez abierto el editor, hay que hacer varias cosas:

2.1.1. Buscar donde pone ‘DefaultDepth’, en ‘ Section “Screen” ‘, y si el valor que aparece a la derecha no es 24, pon 24.

2.1.2. Borrar, si existen, estas entradas en ‘ Section “Modules” ‘ :

Load “dri”

Load “GLCore

2.1.3. Añadir esta entrada en ‘ Section “Modules” ‘ :

Load “glx”

2.1.4. Añadir esta entrada en ‘ Section “Screen” ‘ :

Option “AddARGBGLXVisuals” “True”

Nota: en el comentario 6 del post de instalación de Beryl, Raúl dice que a él le funciona poniendo esto en otra parte del fichero. Podrías probar una opción, y si sigue sin funcionar, la otra.
2.1.5. Añadir esta sección al final del archivo (pegar tal cual):

Section “Extensions”
Option “Composite” “Enable”
EndSection

Tras editar xorg.conf, puedes pulsar Ctrl+Alt+Backspace para reiniciar las X y probar la nueva configuración. En teoría, este problema se soluciona haciendo esto, si tienes cualquier duda o sugerencia puedes dejarla en un comentario.

Con alguno de esos se arregla seguro

---

### Post by s4ntis0 on 2008-03-12
Perdon por la demora pero me quedé sin maquina ahora les cuento porqué. La solución 1 es para placas nvidia imagino y la mia es una ATI x1800. Los drivers funcionan bien. Usé la opcion 2 de editar el xorg.conf y me quedé sin maquina, como no corria y me quedaba en modo texto intenté volver con **sudo mv /etc/X11/xorg.conf.orig /etc/X11/xorg.conf** pero no funciono. TAmbien lei por otro foro que habia que hacer un back up del xorg.conf que yo no tenia , asi no importa lo que hiciera siempre terminaba en modo texto. 
Asi qeu bueno, formatee todo y reinstale ubuntustudio 7.10 nuevamente. Isntale el Xserver, y el compiz, todo a traves de synaptic para no hacer quilombo. Tambien el compiz manager. Ahora tengo obviamente los bordes de las ventanas, pero quiero configurar el cubo 3d y no puedo. Si puedo configurar los efectos. Cuando reinicio para activar todo me sale este mensaje

[B]Ocurrió un un error al iniciar el Administrador de Preferencias de Gnome.

Es posible que las configuraciones de temas, sonidos, fondos de pantalla y otros elementos experimenten problemas en su funcionamiento.

El último mensaje de error fue:

Failed to connect to socket /tmp/dbus-sBrsx60MHi: Connection refused

Gnome seguirá intentando reiniciar el Administrador de Preferencias la próxima vez que inicie una sesión.[/B]

Reinicio y aveces no aparece el mensaje y a veces si y no reconoce ningun tema de escritorio. La cuestion es que no se si por esto no puedo activar tampoco el cubo. Hago click en Cubo 3D, Click en Rotacion Cubo, y luego en General configuro  DEsktop Size : 4 pero no rota ni a palos.

---

### Post by s4ntis0 on 2008-03-13
Ya esta solucionado. Aparentemente el cartelito ese no salio mas, y creo que refiere a alguna opcion  del compiz. Con respecto a los botones como reisntale todo no tuve mas problemas pero igualmente dejo lo que para mi es una solucion. Aparentemente en el compiz manager, en la parte Effects , Decoracion de ventanas, dentro hay unas opciones de sombra. Quiza haya sido eso que volvian a los bordes negros y no se veian los botones de Cerrar /Minimizar/Maximizar. Etc. En fin, Gracias a todos igual.

---

### Post by Cristian CP on 2008-05-06
Hola gente, queria agregar mi experiencia con el tema de los bordes que desaparecen. Tengo una tarjeta nvidia geforce 6200 y la tuve andando perfectamente pr unos dias, hasta que se me ocurrio seguir algunos pasos para mejorar el rendimiento del sistema (esta en la guia y tambien en los foros creo). La cuestion es que cambie la profundidad del color de 24 a 16 bits en la xorg y a partir de ahi, con compiz activado empeze a tener los problemas aqui descriptos por uds. No aplique las soluciones descritas sino que opte por volver a 24 bits y solucionado. 

Conclusion no se si sera la causa raiz del problema en todos pero... Volver a 24 no me ha desmejorado mucho el rendimiento asi que creo q se puede mantener la configuracion de esa forma para evitar problemas con compiz.

Saludos :)

---

