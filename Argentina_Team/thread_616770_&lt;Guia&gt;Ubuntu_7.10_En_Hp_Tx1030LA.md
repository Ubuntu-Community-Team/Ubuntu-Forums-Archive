---
title: "&lt;Guia&gt;Ubuntu 7.10 En Hp Tx1030LA"
date: 2007-11-18
forum: Argentina Team
---

### Post by xpelaox on 2007-11-18
Mi primer aporte!

[COLOR="Red"]_Instalar Ubuntu En Hp Pavilion Tx1030LA_[/COLOR]

Bueno, me decidí a armar esta guía, a pesar de ser principiante en Linux, por que encontré varias guías y ninguna es totalmente concluyente, por eso voy atratar de ir haciendo el rejunte de todo lo que hice yo para que funcione el asunto.

Cabe aclarar que en muchas guías llaman a esta espectacular notebook &#8220;Linux Unfriendly&#8221; eso era cierto, pero con nueva versión 7.10, la cosa es MUCHISIMO mas simple.

Pero bueno, empecemos:

Voy a empezar enumerando lo que no pude hacer funcionar (se aceptan cualquier tipo de ayuda)

-_Lector de Huellas_
-_Pantalla tácti_l (varias personas dicen que la lograron instalar, yo no pude, pero tampoco le dedique demasiado tiempo)
-_Módem_(no se no lo probé y la verdad no me importa:P)
-_Cámara_ (yo no me puse a instalarla, pero se puede, voy a adjuntar una guía de una fuente externa)

Creo que eso es todo, así que empecemos:

El primer problema que se presenta es cuando queremos bootear el Live cd, si lo abrimos de una llega un momento que la pantalla se  pone toda negra y se empieza a transformar en blanca con un degrade muy bizarro, la primera vez me asuste, es agrarismo, si no tenes nada que hacer miralo que esta bueno:P pero bueno, la solución es esta:
	Ponemos El CD, y prendemos la compu(doy por entendido que el bios esta configurado para bootear del cd) nos aparece la pantalla de ubuntu para correr el Live CD, ahí, arriba de la opción de iniciar el live cd o instalar, *apretamos &#8220;F6&#8221;* va a parecer escrito una linea de comandos raros, no les demos bola, ahí escribimos los siguiente* &#8220;noapic nolapic&#8221;* (así con un espacio en el medio y sin comillas, obviamente xD y le damos enter.
Ahí si se va a cargar bien ubuntu desde el live cd, si queremos podemos jugar e investigar un poco, eso es a gusto, Pasemos a instalarlo, Tenemos un iconito para instalar en el escritorio, doble clic y lo instalamos, no tendría que presentar problemas, a lo sumo puede resultar un poco raro el tema de las particiones para alguien que no conoce mucho, pero hay miles de threads que hablan de eso, sino cualquier cosa me pueden preguntar y vemos que podemos hacer, (vuelvo a repetir, uso ubuntu hace poco mas de 2 meses :P no soy un Linux-geek ni nada parecido xD).

Buenisimoooo Tenemos instalado ubuntu, espectacular!

Lo primero que hice yo* Instalar las Actualizaciones*, esto conectado a internet por lan (cable) por que de entrada no te reconoce tan rápido la placa de red Wifi, pero ojo que es facilisimo!

Entonces, retomando, Ya instalamos ubuntu y lo conectamos a internet por LAN nos va a decir que hay actualizaciones nuevas, las bajamos, instalamos y reiniciamos.
Luego, cuando volvemos a prender la compu, nos va a decir que se pueden instalar *&#8220;controladores restringidos&#8221; le damos doble clic* y nos aparecen dos drivers los de la placa de vídeo Nvidia y los de la placa broadcom wifi,* los instalamos los dos*, para esto es necesario estar conectado a internet, es posible que despues de instalar un driver nos pide reiniciar, lo hacemos y después instalamos el otro... total no tenemos apuro, no?
	
	Bueno, vamos bastante bien, ya tenemos Wifi y los últimos drivers instalados, la única cosa realmente importante que nos falta es el sonido, es raro el asunto, por que la placa la reconoce pero al reproducir no sale sonido xD.
buscando como solucionar esto encontré un montón de guías raras, supuestamente lo complicado es instalar los puertos delanteros (los de auriculares y eso) yo lo solucione fácil instalando los últimos drivers de ALSA, y se hace asip:

[COLOR="Red"]//--Edit 6/12/07--// [/COLOR]: Si recien instalan ubuntu, les va a tirar un error en uno de los pasos por que faltan unos paquetes, asi que en la consola ponemos esto para instalarlos: 

 sudo apt-get install build-essential


abrimos la consola y ponemos estos comandos:

sudo wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2)

sudo tar xvfj alsa-driver-1.0.15rc3.tar.bz2

cd alsa-driver-1.0.15rc3

sudo ./configure

sudo make -j 3       (esto puede tardar bastante)
sudo make install
Reiniciamos y listo, ahhh si, tenemos que ir al panel de sonido y subir el volumen, por que de fabrica viene todo muteado.(nótese que los tres botones de subir, bajar y mutear volumen funcionan!!!)

[SIZE="5"][COLOR="Red"]Edit 25/03/08 [/COLOR][/SIZE]

[U][I][COLOR="Red"]
Pantalla Tactil
[/COLOR][/I][/U]

Bueno bueno, Despues de mucho trabajo Probar, romper reinstalar y demases, encontre la manera de hacer funcionar la pantalla tactil y es la siguiente(mi agradecimiento a la gente de [http://darkgiank.freeforums.org/](http://darkgiank.freeforums.org/) que practicamente me base totalmente en su guia para mandriva, solo hize dos retoquesillos):

Primero Bajamos esto 

[http://www.zshare.net/download/5421622ff8c658/]("http://www.zshare.net/download/5421622ff8c658/")

Lo descomprimimos en algun lugar, ahi adentro tenemos dos archivos uno egalax_drv.so y otro Touchkit. Bueno, lo que hacemos es lo siguiente: copiamos el archivo egalax_drv.so a  "/usr/lib/xorg/modules/input"
(esto lo podemos hacer desde la consola haciendo
 sudo Nautilius
 , esto nos abre una ventana para trabajar con privilegios de Root)

Despues otra vez en la conosola ponemos

sudo gedit  /etc/X11/xorg.conf

y ahi hacemos esto:

en el parrafo "Serverlayout" justo antes del end section, ponemos esto:

InputDevice "EETI" "SendCoreEvents"

y despues abajo de todo copiamos esto

Section "InputDevice"
    Identifier "EETI"
    Driver "egalax"
    Option "Device" "usbauto"
    Option "Parameters" "/etc/egalax.cal"
    Option "ScreenNo" "0"
EndSection

guardamos.

Reciniciamos.

desde la consola abrimos el TouchKit para poder calibrar algo asi:

sudo ./TouchKit

calibramos y todo tendria que andar. :)

aaaa otra cosa es necesario que ubuntu este booteando con noacpi, sino la touchscreen va a funcionar con un delay feo.

Bueno, ahora solo nos falta la rotacion de la pantalla, vere que se puede hacer, por ahora algo es algo xD
-------------------------------------------------------------------------------
Bien, acá en general ya tenemos lo mas importante instalado.
van a notar un problemita, si quieren por ejemplo reproducir un Mp3 o algo así van a notar que no pueden por que no tienen los codecs, así que vamos a bajarlo, la solucionan mas fácil que encontré fue mediante &#8220;automatix&#8221; que es un programa que nos instala programas solo como el Synaptic, solo que los programas que te deja instalar no son &#8220;open source&#8221;  y van en contra de la filosofía ubuntu.

lo bajan de acá, y lo abren, así de una, es fácil es un archivo .deb, se les va a abrir una ventana y hacen un clic en el botón de instalar, y sale como piña.

acá están las links: 
		Para Ubuntu 7.10 32 bits: [http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/automatix2_2.0.5-7.10gutsy_i386.deb](http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/automatix2_2.0.5-7.10gutsy_i386.deb)
		Para ubuntu 7.10 64 bits: [http://www.getautomatix.com/apt/dists/gutsy/main/binary-amd64/automatix2_2.0.1-7.10gutsy_amd64.deb](http://www.getautomatix.com/apt/dists/gutsy/main/binary-amd64/automatix2_2.0.1-7.10gutsy_amd64.deb) 

nota: yo isntale la versión 32, por eso toda esta guía esta basada en 32 bits, si instalaste ubuntu de 64bits puede que algunas cosas no funcionen.

una vez instalado van a Aplicaciones --->herramientas de sistemas---> automatix, y de ahí siguen las instrucciones e instalan todo lo que quieran, es muy fácil:) nuevamente, cualquier problema no duden en preguntar!
Cualquier cosa acá les dejo la link de la pag de automatix, esta todo muy bien explicadito:)          	

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

ahora, sobre la cam, les dejo la link de la guía en la que me base, ahí esta explicado el asunto de la cam, y como instalar algunos de los botones de la pantalla, también hay una alternativa para instalar la pantalla táctil, a mi no me sirvió. Es importante destacar que el autor se bazo en Fedora 7, creo, así que algunas cosas pueden variar, ante la duda, pongan &#8220;sudo&#8221; xD

[http://www.kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z](http://www.kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z)

Efectos 3d y demases:
	Bueno como saben ubuntu 7.10 viene con compiz pre-instalado, pero no viene con el las opciones modificables, así que hacemos así:
	vamos a el instalador synaptic y buscamos &#8220;compizconfig-settings-manager&#8221; y lo instalamos con todas sus dependencias, también pueden buscar e instalar &#8220;emerald&#8221; para instalar themes y demás.
una vez hecho esto, vamos a sistema---->preferecias--->apariencias y ahí vamos a la lengüeta &#8220;efectos visuales&#8221; , tildamos &#8220;personalizado&#8221; y entramos a &#8220;preferencias gtk&#8221; ahí podemos elegir y modificar de todo, a gusto.

un problema que me paso MUCHAS veces, es que desaparezcan los bordes de las ventanas, lo cual resulta muy molesto, pero tranquilos, se soluciona muy fácil: vamos a la consola y ponemos los sig. comandos:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig 
sudo nvidia-xconfig -composite 
sudo nvidia-xconfig -allow-glx-with-composite 
sudo nvidia-xconfig -render-accel 
sudo nvidia-xconfig -add-argb-glx-visuals
Tras esto, reinicia el servidor gráfico con Ctrl+Alt+Borrar. Si el servidor gráfico no arranca y arranca Linux en modo texto, escribe estas órdenes para volver a la situación anterior:
sudo mv /etc/X11/xorg.conf.orig /etc/X11/xorg.conf
startx

[COLOR="Red"]
AGREGADO 19/11/07:[/COLOR]
Hay un bug que hace que ubuntu se congele unos segunds, bastante repetitivo y molesto, al menos a mi me paso, y era extraño ya que una de las cosas que mas se rescata de usar linux es su Estabilidad, encontre el culpable: este bug: <https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643/comments/9>. 
Parece que el problema lo genera una Funcion del Micro AMD 64 que se llama "Cool n quiet" algo asi, no se bien como sera el asunto, pero si se como remediar el problema, y es asi =D:
En la Terminal ponemos esto:
1.
sudo su
cp /etc/init.d/powernowd /etc/init.d/powernowd.bak
gedit /etc/init.d/powernowd

2. abajo de esta linea
#! /bin/sh
ponemos esto:
exit 0

guardamos, cerramos y listo :)

Y bien, por ahora creo que es todo, Con el tiempo voy a ir modificando esta guía en base a los problemas que surgan o cosas que faltan, por favor, pido a los que saben mas que si puse alguna ganzada o ven algo que debería ser modificado me lo digan así podemos hacer que esto pueda ser lo  mas útil posible.
Quizás parezca que esta guía esta escrita muy &#8220;a lo bruto&#8221; pero lo que busque es que la persona que jamas uso linux e incluso las personas que no están muy interiorizados con la computación en general puedan entenderlo.

Asia que bueno, sin mas los dejo en este nuevo mundo, Libre de virus, libre de pantallas azules, libre de cuelgues extraños, libre de consumición irracional de recursos, y por sobre todas las cosas, libre y gratuito para todos.

Vaz a pagar por un sistema operativo teniendo una opción gratis y superior?

=D

Saludos

p.d: les dejo mi mail por cualquier cosa no duden en agregarme a MSN o escribirme.

---

### Post by niko_3100 on 2007-11-18
Flor de ntoebook te compraste chabon yo tengo una compaq v3415 con ubuntu feisty.

---

### Post by leonardo83 on 2007-11-18
[IMG][CENTER][http://www.dialogica.com.ar/rosarioalternativo/aplausos.gif](http://www.dialogica.com.ar/rosarioalternativo/aplausos.gif)[/CENTER][/IMG]

Te zarpaste man !!! Muy buen aporte, apesar de que hace poco tengo ubuntu me parecio muy interesante tu ayuda.
como te envidio con tu laptop!! y yo con mi pentium 3 hace 7 añitos :(

Saludos!!

---

### Post by xpelaox on 2007-11-19
JAjajajaaj Gracias muchachos!! 
leonardo83 quedaste tranquilo que esta notebook va a tirar por 7 años o mas xD


saludos

---

### Post by niko_3100 on 2007-11-19
y que te parece chabon con tremenda notebook, no se para lo que la usas pero yo que la uso para programar necesito mas que nada mucha memoria ram ahora tengo 1,5 gb y pronto le pondre 2 gb. Obviamente que me va a durar hasta que vea que con 2 gb me estoy quedando corto, calculo que va a ser unos 4 o 5 años y despues me comprare otra notebook.

---

### Post by xpelaox on 2007-11-19
[COLOR="Red"][SIZE="5"]UPDATE 19/11/07[/SIZE][/COLOR]

Agregue datos sobre como solucionar un bug que hace que el S.O Se Congele cada tanto. 

Saludos

---

### Post by xpelaox on 2007-12-06
**[COLOR="Red"][SIZE="7"]UPDATE 6/12/07[/SIZE][/COLOR]**


El otro dia meti la pata y me vi obligado a reinstalar ubuntu xD, cosas de la vida, y me di cuenta que faltaban algunas cositas en la guia, asi que agregue xD

Saludosss

---

### Post by xpelaox on 2008-03-25
[COLOR="Red"][SIZE="7"]UPDATE 25/3/08[/SIZE][/COLOR]

Agregue como instalar la pantalla tactil: MUEEEHEHEHEHEHHHE:guitar:

---

### Post by .NicK_LoVe on 2008-04-06
Que bueno!!!! ya tengo de donde adoptar información para instalar ubuntu en mi nueva hp 6768se!!!!!!!!!!!

---

### Post by xpelaox on 2008-04-07
Genial! Cualquier duda no dudes en preguntar! =D

---

### Post by Martinsito on 2008-04-29
> **xpelaox said:**
> Genial! Cualquier duda no dudes en preguntar! =D

Hola!, tengo una duda bastante grande, hice los pasos que decis en la parte de instalacion del sonido y no solo que no lo instalo sino que ademas "borro" los dispositivos que al menos antes podia verlos en la parte de pruebas de sonido... es raro, cuando lo instale reconocia los dispositivos pero el boton de "mute" siempre estaba en rojo, si sabes por que seria de gran ayuda!
Estaba pensando en actualizar a la version 8.04 pero no creo q solucione el problema..
Espero tu comentario ya que vos lograste hacerlo andar, lo demas funciona todo menos el detector de huellas, pero ese es tema aparte...
Gracias!

---

### Post by xpelaox on 2008-05-11
Uhh lamento no poderte ayudar, Recien ayer me llego la notebook del servicio tecnico de HP y todabia no instale UBUNTU, lo voy a hacer cuando me llegue el cd de 8.04. Ahi me voy a fijar si puedo ver que tu problema, si queres agregame a msn : [email]xpelaox@gmail.com[/email]


Saludos!

---

