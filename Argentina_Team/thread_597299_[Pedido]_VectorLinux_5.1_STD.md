---
title: "[Pedido] VectorLinux 5.1 STD"
date: 2007-10-30
forum: Argentina Team
---

### Post by Kasa.Ramone on 2007-10-30
Despues de probar innumerables Distros de linux una de las pocas que me convencio (y pude hacer correr en mi pc vieja) fue VectorLinux 3.2, he visto que hay versiones nuevas, pero algunas necesitan mas que 64mb de ram por lo que no puedo usarlas, pero he visto que la 5.1 Standart usa como recomendacion 64mb de ram y posee Xfce 4.2 (entre otras cosas), por lo tanto quise probarlo ya que si la 3.2 me gusto y andubo bien, la 5.1 de seguro sera mejor.
El tema es que busque por todo internet (inclusive en la pagina de Vectorlinux y su FTP) pero no encontre un Link que no este roto de VectorLinux 5.1 STD, si alguien sabe donde puedo bajarlo les agradeceria.

Saludos.

---

### Post by tzulberti on 2007-10-30
Aca tenes varios links para varias versiones de VectorLinux:
[http://distrowatch.com/table.php?distribution=vector](http://distrowatch.com/table.php?distribution=vector)

Sin embargo, la 5.1 me esta dando un error (no se si es pq tengo la pagina bloqueada o que :) ).

---

### Post by kowal on 2007-10-30
Vector Linux es una distro buena y rápida (basada en Slackware), pero las versiones viejas están un poco desactualizadas y las nuevas tienen mayores requerimientos..

Yo te aconsejaría que para la maq. que la querés usar (si es la misma de [este](http://ubuntuforums.org/showthread.php?t=590491) post) instales Debian básico y de ahi vayas armando a gusto los paquetes que quieras instalar (el sistema de instalación de programas es igual al de Ubuntu, o sea a través de apt-get o aptitude). Otra opción sería instalar Slackware, pero si recién entrás en el mundo de Linux no es lo mas recomendable.

---

### Post by Kasa.Ramone on 2007-10-30
> **kowal said:**
> Vector Linux es una distro buena y rápida (basada en Slackware), pero las versiones viejas están un poco desactualizadas y las nuevas tienen mayores requerimientos..

Yo te aconsejaría que para la maq. que la querés usar (si es la misma de [este](http://ubuntuforums.org/showthread.php?t=590491) post) instales Debian básico y de ahi vayas armando a gusto los paquetes que quieras instalar (el sistema de instalación de programas es igual al de Ubuntu, o sea a través de apt-get o aptitude). Otra opción sería instalar Slackware, pero si recién entrás en el mundo de Linux no es lo mas recomendable.
Probe con Slackware 11 y Kwort 2.2(distro rosarina basada en slackware con XFCE 4.4 y pide solo 32mb de ram) pero ninguna de las dos quizo bootear desde mi CD-RW (que lo use ya para bootear en banda de distribuciones..) y con respecto a Debian, esa era una de las ideas de usar Debian 4.0 basico (baje la version XFCE igualmente, pero si andaba muy justo lo cambiaba a fluxbox o Icewm) y con un entorno liviano, pero en el paso "instalacion de sistema base" tira error de que no encuentra los paquetes o estan corruptos (cosa rara porque el Md5 da correcto), lo mismo para fluxbuntu, Xubuntu y Zenwalk.
Slax lo probe pero anda lento, DSL no es muy de mi agrado, FeatherLinux no lo logro bootear. Y con las distros "potentes" como Fedora,Ubuntu,OpenSUSE no me deja pasar al instalador (error de kernel Syncing) por lo que no puedo probar con instalacion base y luego añadir un entorno grafico liviano.
Despues vi otra distribucion KateOS pero esta tampoco bootea (aparece la pantalla de booteo pero no reconoce kernel alguno en el CD)bien.
Una de las unicas distribuciones que no me dio problemas fue Vectorlinux 3.2 (Ok, tube que configurar el monitor y el mouse pero mas alla de eso no pasa..) pero habiendo versiones mas nuevas (hasta la 5.1 sin contar las SOHO) soporta todas se me ocurrio tratar de ponerle algo mejor.

Lo que mas me interesaba era Fluxbuntu, Kwort y Slackware ...
Aunque Debian y Zenwalk eran mis "segundas" opciones, ninguna me funciono, por eso busco esta version de VL.

Saludos,

---

### Post by kowal on 2007-10-30
El problema de instalar/bootear Lives-CDs es que cargan muchas cosas en la memoria RAM dejando poca memoria libre para poder instalar el SO.

Se me ocurre que podrías probar otras alternativas de instalación.. como instalar una versión mínima desde otro dispositivo.. como puede ser un pendrive, floppy, con [debian.exe](http://goodbye-microsoft.com/), vía net-boot PXE, etc, etc. Y luego descargar el resto de los paquetes por internet. Es importante tener una partición swap activada.

Yo tengo una PII 300 64mb RAM, a la cual le pude instalar sin problemas Debian, Ubuntu server y otras. Y en la P 100 32mb RAM tengo Slackware ;)

---

### Post by pablo0469 on 2007-10-30
Ojo con la ultima version de Vector que he leido que no es simple traducirla al español y los paquetes no vienen muy bien organizados que digamos.

---

### Post by Kasa.Ramone on 2007-10-30
> **kowal said:**
> El problema de instalar/bootear Lives-CDs es que cargan muchas cosas en la memoria RAM dejando poca memoria libre para poder instalar el SO.

Se me ocurre que podrías probar otras alternativas de instalación.. como instalar una versión mínima desde otro dispositivo.. como puede ser un pendrive, floppy, con [debian.exe](http://goodbye-microsoft.com/), vía net-boot PXE, etc, etc. Y luego descargar el resto de los paquetes por internet. Es importante tener una partición swap activada.

Yo tengo una PII 300 64mb RAM, a la cual le pude instalar sin problemas Debian, Ubuntu server y otras. Y en la P 100 32mb RAM tengo Slackware ;)
Igualmente todo lo que probe fue en alternate o en "low memory" mode, y Slackware pese a que quiera usarlo no puedo ya que ni siquiera me lo toma como un BootCD (asi como tampoco Kwort) mientras a otros si pero no se instalan en su totalidad (problema ya dicho), con un floppy no tengo idea de como instalarlo (ademas de que no tengo ninguno sano)y mi Bios no tiene la opcion de USB HDD para bootear, la swap esta activada. 
Mediante Network no he probado todavia, mañana me fijare, igualmente si alguien sabe de donde bajar VL 5.1 STD se lo agradesco (por ahi alguno lo tiene guardado por ahi y se le da por subirlo).

Saludos.

---

### Post by faktorqm on 2007-10-31
eeehhhhhhh........................................

[http://public.planetmirror.com/pub/linux/distributions/vectorlinux/veclinux-5.0/iso/?fl=](http://public.planetmirror.com/pub/linux/distributions/vectorlinux/veclinux-5.0/iso/?fl=)

........................................................ ok

---

### Post by lulima on 2007-10-31
A veces los discos duros de las máquinas viejas tienen telarañas de tanto uso, algo que siempre hago en estos casos es limpiar el disco. Insertas una copia de Knoppix (cualquier versión) y en el prompt escribes:

boot: knoppix 2 vga=normal lang=es

esto te da una configuración en formato de texto, con letras grandes y un teclado en español. No hay necesidad de entrar en las Xs.

Termina con un prompt de root:

#

escribes lo siguiente:

# dd if=/dev/zero of=/dev/hda

y lo dejas andando por x cantidad de minutos (de acuerdo al tamaño de tu disco) Ejemplo: un disco de 40 Gb = 15 minutos

Luego que transcurre el tiempo especificado:

Presionas las teclas Control y c

después de unos segundos te da una información, y escribes

# halt

se para y bota el cd, lo sacas y metes el de la instalación del distro que quieras,  reinicias la máquina manualmente (aprietas el botón de reboot), y comienza la instalación, esto siempre me ayuda.

Suerte,

---

### Post by Kasa.Ramone on 2007-10-31
> **faktorqm said:**
> eeehhhhhhh........................................

[http://public.planetmirror.com/pub/linux/distributions/vectorlinux/veclinux-5.0/iso/?fl=](http://public.planetmirror.com/pub/linux/distributions/vectorlinux/veclinux-5.0/iso/?fl=)

........................................................ ok
Agradezco tu ayuda pero no me funciona el Link del 5.1STD no live..
-----------------------------------------------------------
Hoy a la tarde pruebo lo que me dijiste lulima,muchas gracias por responder.

Saludos.

---

### Post by Hernán-Amaya on 2007-10-31
probaste con puppy??

---

### Post by faktorqm on 2007-10-31
....mira, a mi me lo baja..... si no me crees, adjunto screenshot:

[[IMG]http://www.fotazas.com/images/thumbs/uziynyj24zdyktmmtlzr.png[/IMG]](http://www.fotazas.com/photo_uziynyj24zdyktmmtlzr.png.htm)

escuchame una cosa, sino entra aca: [ftp://ftp.planetmirror.com/pub/vectorlinux/veclinux-5.0/iso/](ftp://ftp.planetmirror.com/pub/vectorlinux/veclinux-5.0/iso/)

y sino fijate el ftp usando algun porograma como el gFTP:

[[IMG]http://www.fotazas.com/images/thumbs/ymh0mkzjnwyyzejeiwfj.png[/IMG]](http://www.fotazas.com/photo_ymh0mkzjnwyyzejeiwfj.png.htm)

espero que te haya servido. salu2!

---

### Post by Noich on 2007-10-31
> **pablo0469 said:**
> Ojo con la ultima version de Vector que he leido que no es simple traducirla al español y los paquetes no vienen muy bien organizados que digamos.

Lastima que no lei esto antes :( instale VectorLinux 5.8 Standard Gold tras muchos intentos de instalar disstintas distros (junto con kasa,probamos muchas variantes) y yo feliz y contento q dsp de casi 1 semana d itnentar habia podido con linux no logro ponerlo en español ni configurar la placa de red para usar internet...](*,) :redface:

---

### Post by lulima on 2007-10-31
Acaba de salir Antix (mepis lite 300 mb) se baja de:

[ftp://mirror.cs.vt.edu/pub/MEPIS/antix/antiX-M7.iso](ftp://mirror.cs.vt.edu/pub/MEPIS/antix/antiX-M7.iso)

es bien ligero y configurable, trae aplicaciones ligeras, muy completo, viene con Fluxbox y IceWM.

Screenshot (Fluxbox y Firefox)
[http://farm3.static.flickr.com/2395/1812590056_15b52c7f22_o.jpg](http://farm3.static.flickr.com/2395/1812590056_15b52c7f22_o.jpg)

PD: olvidé mencionar que está basado en Debian stable/testing (etch/lenny)

---

### Post by Kasa.Ramone on 2007-11-02
Probe con el comando de bash que me diste, y aunque me sirvio para limpiar el disco rigido sigo con los mismos problemas de antes.
en cuanto al AntiX mepis lo baje y tampoco me andubo, y los links de VL me siguen sin andar..
Voy a ver instalando mi vieja version VL 3.2 y tratando de actualizar a un XFCE mas nuevo que onda.
La verdad ya no se si es problema del hard o soy yo, no logro hacer andar una distro, todas tienen algun problema que no me deja instalar.

Saludos.

---

### Post by Kasa.Ramone on 2007-11-02
Se que puede ser un pedido de algo medio viejo, pero si alguien tiene un Debian 2.0 o 3.0 (no en adelante) por ahi, le agradeceria si lo pudiera subir.
Desde ya gracias.

Edit: Si conocen de alguna Distro con Enlightment que pueda andar en la pc tambien es aceptado(P3 600mhz, 64mb Ram, HDD 15.3gb,Video Sis620 onboard), o alguna con XFCE(Sin contar las que ya probe: Slack, Kwort, Debian4.0,Sam,VL.) En lo posible que sean de instalacion y no de liveCD..

---

### Post by pablo0469 on 2007-11-03
> **Noich said:**
> Lastima que no lei esto antes :( instale VectorLinux 5.8 Standard Gold tras muchos intentos de instalar disstintas distros (junto con kasa,probamos muchas variantes) y yo feliz y contento q dsp de casi 1 semana d itnentar habia podido con linux no logro ponerlo en español ni configurar la placa de red para usar internet...](*,) :redface:


Ya me parecio que lo que puse paso desapercibido, yo tambien queria probarlo pero cuando comence a buscar informacion, me entere de estos problemas (ademas de la falta de soporte en español, todos opinan que los paquetes vienen organizados en forma confusa, mucho mas para el usuario medio).

No te hagas problema que yo tambien he bajado e instalado distros asi, pero obviamente ahora antes de hacerlo, lo primero que busco es este tipo de informacion.

Saludos.

---

