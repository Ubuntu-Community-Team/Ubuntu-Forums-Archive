---
title: "Toshiba l35  helpp!!"
date: 2008-02-22
forum: Argentina Team
---

### Post by valucha on 2008-02-22
[COLOR="DarkOrchid"]Hola, antes que nada perdonen por el título tan poco descriptivo pero realmente era inresumible (existe esa palabra?! bue, sino la invente:))...

Les cuento que traté de instalar Ubuntu en una Toshiba Satellite L35 y no doy pie con bola.
Con el live cd de Gutsy todo anda de 10, me reconoce la placa wireless, me puedo conectar a internet, y en los drivers restringidos me reconoce la placa de video Ati y algo que se llama "Atheros Hardware Access Layer (HAL)". (la primera no esta habilitada,la segunda si). 
Instala sin problemas pero a la hora de iniciar normalmente se pone toda la pantalla negra (aveces cambia de tonos, como si se prendiera y apagara...) y no responde para nada... Logro ver que aveces carga pero no mucho y en un momento muere... queda prendida y no hace nada más...

La inicio en recovery mode, y al principio me manda un cartel que dice "failed to intialize HAL"... Le doy aceptar y simultaneamente todos los sistray desaparecen... (lease el de actualizaciones y el de controladores restringidos). No tengo internet, y tampoco puedo abrir la configuracion de red porque me dice que no tengo permisos (y tampoco se hacerlo desde la consola :( ) 

Y ahi me quedo, busqué en internet y sobre esta laptop no hay nada más que como solucionar el problema del sonido que ya sé como  hacerlo porque lo hice con la de mi viejo que tiene la misma placa.


Bueno, si necesitan más info porfi diganme... Mil gracias por adelantado :)



Valucha[/COLOR]

---

### Post by valucha on 2008-02-23
[COLOR="black"][COLOR="DarkOrchid"]Bueno, volvi con buenas nuevas :)

Pude hacer andar la notebook perfectamente con Feisty, me reconoce todo y me isntala los drivers restringidos de la placa wifi y la ati. Peeeeeeeeeeeeeeero no puedo hacer andar los efectos de escritorio... ¿Será por eso que no me anda Gutsy? 


[/COLOR][/COLOR]

---

### Post by facundocorradini on 2008-02-23
Sin dudas, es algo que tiene que ver con el xorg.conf y tu placa ATI. 

Pero ya escapa de mi nivel... por ahí alguno de los capos te da una manito...

---

### Post by santiagoward2000 on 2008-02-23
> **valucha said:**
> [COLOR="black"][COLOR="DarkOrchid"]Bueno, volvi con buenas nuevas :)

Pude hacer andar la notebook perfectamente con Feisty, me reconoce todo y me isntala los drivers restringidos de la placa wifi y la ati. Peeeeeeeeeeeeeeero no puedo hacer andar los efectos de escritorio... ¿Será por eso que no me anda Gutsy? 


[/COLOR][/COLOR]

Hola!
La placa ATI podría hacer que no anden los efectos en Feisty. Si instalas los drivers desde los repositorios de Ubuntu, tenés que instalar XGL para poder correr Compiz, ya que no vienen con AIGLX. Si querés probar si andan, el paquete se llama **xserver-xgl**.
Igual, no me imagino que eso tenga algo que ver con los problemas en Gusty. Aunque sea sin ningún efecto, pero Gnome tendría que correr... La verdad que no se me ocurre cuál podría ser el problema.
Espero que le puedas encontrar la vuelta!
Suerte!!

---

### Post by valucha on 2008-02-24
[COLOR="DarkOrchid"]Ya instalé ese XGL, realmente vengo de Nvidia donde no tenes ningun problema, pero bueno, al menos aprendi algo nuevo... Ahora tengo feisty andando con compiz fusion y todo al mango y perfecto... MIlagrosamente con una actualización se arregló lo del sonido, se ve que era un bug y lo arreglaron.

La verdad que me gustaría saber qué hace que en gutsy no me ande la cosa, pero me quedó tan bien feisty que me parece que no voy a probar nada jajaj... de ultima actualizo desde acá la versión y les digo.


gracias por su interes, valucha[/COLOR]

---

### Post by User21 on 2008-02-24
Ademas de lo ya mencionado, en Synaptic hay 3 paquetes relacionados con Toshiba, quizás te pueda ser util instalarlos. Los mismos son:
 
**fnfxd**: ACPI and hotkey daemon for Toshiba laptops
fnfx enables owners of Toshiba laptops to change the LCD brightness,
control, the internal fan and use the special keys on their keyboard
(Fn-x combinations, hot-keys). The internal functions will give the
possibility to map the Fn-Keys to functions like volume up/down, mute,
suspend to disk, suspend to ram and switch LCD/CRT/TV-out. These
functions heavily depend on the system and/or kernel configuration.
You will need at least a kernel (v2.4.x, v2.5.x, v2.6.x) with ACPI and
Toshiba support (CONFIG_ACPI and CONFIG_ACPI_TOSHIBA).

**toshset**: Access much of the Toshiba laptop hardware interface 
Toshset ia a command-line tool to allow access to much of the
Toshiba laptop hardware interface developed by Jonathan Buzzard. It can do
things like set the hard drive spin-down time, turn off the display
and set the fan speed without the help of the kernel.
The difference to toshutils is, that it does not need X or kernel-support.

This package also includes the Toshsat1800-irdasetup by Daniele Peri.  It
can be used to configure IrDA for laptops with ALI1533 bridge (LPC47N227
SuperIO), smc-ircc and not initializing BIOS (tested on Toshiba Satellite
1800-514). Homepage: [http://www.schwieters.org/toshset/](http://www.schwieters.org/toshset/)
Homepage: [http://www.csai.unipa.it/peri/toshsat1800-irdasetup/](http://www.csai.unipa.it/peri/toshsat1800-irdasetup/)

**toshutils**: Toshiba laptop utilities
This is a collection of utilities to control a Toshiba laptop. It includes
programs to turn the fan on and off, to view the power mode, and to set
the supervisor password.

Note that these utilities work with APM features in the Toshiba BIOS.
If your laptop's BIOS only supports ACPI and not APM, then toshutils will
probably not work for you. Toshiba's newer models tend to support ACPI
only, and therefore toshutils will not work with them.

This package has now been compiled against the GTK2 libraries.
For more information: [http://www.buzzard.me.uk/toshiba/](http://www.buzzard.me.uk/toshiba/)

Espero os sirva! Saludos.

---

### Post by santiagoward2000 on 2008-02-24
> **User21 said:**
> Ademas de lo ya mencionado, en Synaptic hay 3 paquetes relacionados con Toshiba, quizás te pueda ser util instalarlos.

Hola User21!
Una pregunta: tenés alguna guía para usarlos? Me interesa el tema de controlar el ventilador. Tengo **toshset** instalado, pero no puedo hacerlo andar.
Gracias!

---

### Post by User21 on 2008-02-24
> **santiagoward2000 said:**
> Tenés alguna guía para usarlos? Me interesa el tema de controlar el ventilador. Tengo **toshset** instalado, pero no puedo hacerlo andar.

Lo ideal seria que te remitas a los sitios que ellos publican en busca de alguna guia..
 [http://www.schwieters.org/toshset/](http://www.schwieters.org/toshset/)
Homepage: [http://www.csai.unipa.it/peri/toshsat1800-irdasetup/](http://www.csai.unipa.it/peri/toshsat1800-irdasetup/)

---

### Post by santiagoward2000 on 2008-02-24
> **User21 said:**
> Lo ideal seria que te remitas a los sitios que ellos publican en busca de alguna guia..
 [http://www.schwieters.org/toshset/](http://www.schwieters.org/toshset/)
Homepage: [http://www.csai.unipa.it/peri/toshsat1800-irdasetup/](http://www.csai.unipa.it/peri/toshsat1800-irdasetup/)

Gracias! Ahora me pongo a verlo!

---

