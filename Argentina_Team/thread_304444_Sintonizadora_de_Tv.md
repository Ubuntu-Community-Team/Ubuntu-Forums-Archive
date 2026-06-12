---
title: "Sintonizadora de Tv"
date: 2006-11-21
forum: Argentina Team
---

### Post by tzulberti on 2006-11-21
Una pregunta basica: me compre una sintonizadora de TV "generica" (las que se consiguen por U$$40 en mercadolibre.com). La cosa es que por el tvtime funciona todo bien... pero al momento de grabar, ahi se escucha un beep y no se escucha nada de las voces...

Queria saber si a alguien mas le pasa esto, o si soy yo... Para grabar probe con el comando streamer, y con el mencoder... La imagen se ve bien, el problema es el sonido...

Saludos,
Tomas

---

### Post by beuno on 2006-11-21
¿Chipset?
¿Modelo?

---

### Post by tzulberti on 2006-11-21
Chipset: saa7134
Modelo: Kozumi KTV-01C

---

### Post by beuno on 2006-11-21
```
/var/log/dmesg
``` no se queja de nada?

---

### Post by beuno on 2006-11-21
Pegale una mirada a: [http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm](http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm)

---

### Post by tzulberti on 2006-11-22
Muchas gracias por los links, pero la configuracion debe estar bien hecha, porque en caso contrario no veria bien en el tvtime...

De todas formas, como no entiendo muy bien lo del desmeg, te pego lo relacionado con la placa:
> 
17179592.212000] saa7130[0]: found at 0000:00:0b.0, rev: 1, irq: 114, latency: 32, mmio: 0xdd000000
[17179592.212000] saa7130[0]: subsystem: 1131:2342, board: ProVideo PV952 [card=51,insmod option]
[17179592.212000] saa7130[0]: board init: gpio is 5d31ff
[17179592.240000] sky2 eth0: enabling interface
[17179592.348000] saa7130[0]: i2c eeprom 00: 31 11 42 23 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17179592.348000] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 37 31 33 30 20
[17179592.348000] saa7130[0]: i2c eeprom 20: 41 42 48 53 ff ff ff ff ff ff ff ff ff ff ff ff
[17179592.348000] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179592.348000] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179592.348000] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179592.348000] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179592.348000] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179592.392000] tuner 1-0060: All bytes are equal. It is not a TEA5767
[17179592.392000] tuner 1-0060: chip found @ 0xc0 (saa7130[0])
[17179592.392000] tuner 1-0060: type set to 37 (LG PAL (newer TAPC series))
[17179592.400000] tuner 1-0061: chip found @ 0xc2 (saa7130[0])
[17179592.416000] saa7130[0]: registered device video0 [v4l2]
[17179592.416000] saa7130[0]: registered device vbi0
[17179592.416000] saa7130[0]: registered device radio0
[17179592.468000] saa7134 ALSA driver for DMA sound loaded
[17179592.468000] saa7130[0]/alsa: saa7130[0] at 0xdd000000 irq 114 registered as card -1


---

### Post by beuno on 2006-11-22
Parece estar bien soportada, no veo ningun problema con la placa.
Debe ser alguna vuelta con el programa.
Nunca lo use, asi que no se por donde buscar.

---

### Post by tzulberti on 2006-11-22
Decime que programa usas, y lo instalo

---

### Post by beuno on 2006-11-22
Ninguno  ;)

---

### Post by ariel on 2006-11-22
capaz que con mythtv tenes mas suerte... el package oficial es bastante nuevo

yo lo use hace mucho con una placa con el mismo chipset y anduvo bien. despues ahorre unos mangos y me compre un televisor y un dvd :)

salu2

---

### Post by tzulberti on 2006-11-23
Lo habia probado de instalar y en su momento no habia podido... Probare durante este finde

---

### Post by felipelerena on 2006-11-30
te recomiendo el TVtime, es muy bueno. Es el que uso yo (cuando lo uso)

---

### Post by tzulberti on 2006-12-01
Si, con TV time no tengo problema alguno. El problema esta al intentar de grabar...

---

### Post by felipelerena on 2006-12-01
ah... eso es otro tema... la ultima vez que lo intente pude grabar sin ningun problema, pero tiene que ver, supongo, con el hecho de que tengo chip brooktree en la capturadotra, que es el mas "estandard" de todos

---

### Post by pump on 2006-12-02
Sorry por el offtopic. Alguien por casualidad tiene una Pinnacle Pctv? Porque hace tiempo que intento pero no quiere andar.

---

### Post by felipelerena on 2006-12-02
(no es offtopic)
yo tengo una avermedia que usa el chip bt8*** que es el mismo que usa la pinnacle (y la gran mayoria) y no tengo ningun problema... por que no te anda? que intentaste hacer?

---

### Post by pump on 2006-12-02
Intente levantar los modulos (saa7***, no me acuerdo bien como se llamaba) siguiendo algunos howto pero nada.
Igual la PCTV no tiene chip BT, es el chip Philips.

---

### Post by felipelerena on 2006-12-02
> **pump said:**
> Intente levantar los modulos (saa7***, no me acuerdo bien como se llamaba) siguiendo algunos howto pero nada.
Igual la PCTV no tiene chip BT, es el chip Philips.

a que no sabes a quien le compra phiips el chip?...

me parece muy raro que tengas problemas. yo tenia una pinnacle studio PCTV (que paso a mejor vida) e iba perfecto...

se supone que HAL la deberia "detectar" de una.

ya se que sonara muy de "ama de casa que usa windows"... pero probaste instalar el SO con la placa puesta o la conectaste despues de instalarlo?

---

### Post by Nemesis Teufel on 2006-12-02
offtopic:

> ya se que sonara muy de "ama de casa que usa windows"

jajajaja

---

### Post by pump on 2006-12-02
Jaja, instale con la placa puesta.
El tema mas que nada me parece que viene del sintonizador, o sea lo unico que tengo es interferencia. Ya probe con toda la lista de tuners (usando un script) pero nada, solo interferencia y ejecutando tvtime-scanner no encuentra nada.

---

### Post by felipelerena on 2006-12-02
ok, esta solucion te va a parecer muy pedorra pero a mi me salvo la vida durante dos años...

sintonizá los canales con una video...

conectala por RCA por el puerto de s-video y el sonido metelo por el line-in.


proba....

saludos

---

### Post by felipelerena on 2006-12-02
ah... otra cosa, pone en pal-nc (o pal-n combo) y no en pal-n la norma, por que cuando el script busque puede buscar en otro rango de frecuendias.

---

### Post by beuno on 2006-12-02
> **felipelerena said:**
> ah... otra cosa, pone en pal-nc (o pal-n combo) y no en pal-n la norma, por que cuando el script busque puede buscar en otro rango de frecuendias.

Varias personas lo solucionaron asi.
Probalo y contanos.

---

### Post by tzulberti on 2006-12-02
> **pump said:**
> Intente levantar los modulos (saa7***, no me acuerdo bien como se llamaba) siguiendo algunos howto pero nada.
Igual la PCTV no tiene chip BT, es el chip Philips.

Yo tengo una saa7134...
Mini How-to:
en /etc/modprobe.d/ crear un archivo llamado saa7134 con el siguiente contenido: 
alias char-major-81     videodev
alias char-major-81-0   saa7134
options saa7134 tuner=37 card=51
Paso 2: reiniciar
Paso 3: 
Configurar el tvtime, para que lea cable (dpkg-reconfigure tvtime). Dentro de la configuracion del tvtime, hacer que el mismo use PAL-NC y yo lo tengo que poner en TV (mono only)

Espero que eso te sea de ayuda, ya que a mi me funciona

---

### Post by pump on 2006-12-02
Si, lo de la video lo pense porque creo que la entrada rca esta funcionando y la de super video tambien.
Lo de pal-nc lo lei tambien y las ultimas veces que probe lo hice en ese sistema.

PD: Alguno de ustedes no me podria pasar el channellist.xml asi lo cargo? Asi por lo menos se que esta buscando en las frecuencias correctas y puedo empezar a probar con que tuner agarra, no?

Muchas gracias a todos. :)

---

### Post by tzulberti on 2006-12-03
Te paso mis archivos de configuracion del tvtime. Hay una carpeta oculta (.tvtime) que va en el home de tu user (cambiale el owner)

---

### Post by pump on 2006-12-03
Gracias, pruebo y despues te comento.

EDIT: Al fin despues de tanto tiempo de probar pude hacer andar la capturadora.
Ahora me queda ver si puedo hacer andar el Myth Tv.

Gracias por la ayuda. :D

---

### Post by tzulberti on 2006-12-11
Decime si pudistes hacer andar el MythTv, ya que yo intente pero no pude...

---

### Post by pump on 2006-12-11
No, no pude. Igual no probe mucho, tengo que ver de empezar a instalar y configuralo de 0 otra vez.

---

### Post by faktorqm on 2007-11-18
Hola!!!!!!!!!!!!!!!!!!!!!!!!! como andan? espero ke bien!

toy chocho por que pude hacer andar la capturadora de video. y fue tan facil que no lo podia creer, gracias al mini tuto del maestro tomas (gracias tzulberti!!). Ahora bien, pequeño problema, en realidad es más mio que de otra cosa, yendo al caso digamos. No tengo el cable de super video a RCA, y por razones de la distribución de las paredes de mi casa, es prácticamente imposible llevar un cable coaxil hasta mi pc. por lo tanto, un RCA out desde la video va al RCA de video IN (tengo coaxil, RCA, S-video y audio out en la placa, es una pinnacle re monona, pero no tengo los drivers, ni el remoto, ni el modelo, ni nada JAJAJA, la obtuve por un canje y... bueno ok) y despues puse un RCA a miniplug, el miniplug a la entrada de linea de la placa de sonido, un rca del otro lado al audio out (la video es mono :S). 
paso a contar los resultados: 

en windows: se escucha joya y se ve josha, PERO cuando le pongo que quiero que grabe graba el video no mas y no el sonido. algun programa me recomiendan?
en gnu/linux: se escucha joya y se ve josha, PERO ... no sé como se hace para grabar a un video!!!!
estoy usando el tv timer, y no encontre nada la verdad que me pueda ayudar, si alguien sabe como hcerlo se lo agradeceria. 

gracias de antemano. salu2!!

---

### Post by tzulberti on 2007-11-20
Yo usaba el siguiente script:
 mencoder -tv driver=v4l2:width=640:height=480:norm=pal-nc:input=2:chanlist=us-cable:channel=58
-ffourcc DIVX -fps 25 -ovc lavc -lavcopts vcodec=mpeg4:vhq -oac
mp3lame -lameopts cbr:br=128 -endpos 60 -o outfile.mpg tv://

donde el input creo que era el canal, y el nro despues del endpos era el tiempo a grabar... 
El problema es que no grababa bien el sonido (grababa un beep terrible)

---

### Post by faktorqm on 2007-11-21
gracias, lo pruebo y te digo. salu2!

---

### Post by vk-cdg on 2008-03-25
> **tzulberti said:**
> Yo tengo una saa7134...
Mini How-to:
en /etc/modprobe.d/ crear un archivo llamado saa7134 con el siguiente contenido: 
alias char-major-81     videodev
alias char-major-81-0   saa7134
options saa7134 tuner=37 card=51
Paso 2: reiniciar
Paso 3: 
Configurar el tvtime, para que lea cable (dpkg-reconfigure tvtime). Dentro de la configuracion del tvtime, hacer que el mismo use PAL-NC y yo lo tengo que poner en TV (mono only)

Espero que eso te sea de ayuda, ya que a mi me funciona

Hace tiempo que vengo luchando con mi TV Card Genius TV a go11. Meses atrás seguí varios tutos y post en cuanto foro encontré que ya ni me acuerdo que hice y que dejé de hacer.
En Semana Santa retomé mis intentos por hacer andar la maldita placa y buscando cuanta cosa haya por internet me topé con este post. Hice los tres pasos que menciona y de una tomó imagen perfecta, con mu buena calidad. El sintonizador anda perfecto, veo todos los canales de mi proveedor, pero tengo un solo problema... no tengo sonido.
Lo primero que hice fue fijarme la entrada de linea como está mencionado en mas de un post pero nada, estaba habilitada. 
Luego de dar vueltas por media internet y de volver loco a uno de los chicos del foro (gracias Mauro) descubrí que no aparece el módulo saa713X en la Sistema/Preferencias/Sonidos, en el menú desplegable de dispositivos.
No tengo acá el screenshot que me mandó Mauro donde me muestra como lo tiene el (estoy en el trabajo) pero en principio el prolbema sería ese.
Busqué por todo google y por (googlubuntu también) y no encontré nada que me solucionara el inconveniente. 

Alguien tiene alguna idea de que puede ser?

---

### Post by faktorqm on 2008-03-26
hola, te fijaste de hacer lspci? a ver que te va a apareciendo? yo en la mia me pasaba lo mismo, pero no me acuerdo si lo habia solucionado o lo habia dejado asi. cosa seria! Salu2!

---

### Post by vk-cdg on 2008-03-26
Bueno, acá posteo las imágenes de la PC de uno de los chicos de acá del foro (la que tiene fondo negro) y la mía (la que tiene fondo naranja).

No logro hacer que aparezca en ese menú desplegable el dispositivo.

El error que me tira por consola cuando corro la instrucción que me pasaron, el error que sale es este.

vikingo@Sion:~$ tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay - 
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
arecord: main:545: error al abrir audio: No existe el dispositivo
Ejecutando tvtime 1.0.2.
Leyendo la configuración de /etc/tvtime/tvtime.xml
Leyendo la configuración de /home/vikingo/.tvtime/tvtime.xml
aplay: playback:2018: error de lectura
Gracias por usar tvtime.
vikingo@Sion:~$

---

### Post by faktorqm on 2008-03-27
posteame el lspci capo! a ver si realmente tenes ese chip u otra cosa.

No hay mucha info, parece que es medio jodido hacerla andar, PERO mira lo que encontre aca: [http://www.yoreparo.com/foros/software/137426.html](http://www.yoreparo.com/foros/software/137426.html)

tu placa se corresponde con eso? aca en este blog (particularmente amo ese blog) dice algo tambien para ver ke ahcer:

[http://www.yoreparo.com/nav/?url=http://tuxpepino.wordpress.com/2007/06/07/television-en-ubuntu-linux/](http://www.yoreparo.com/nav/?url=http://tuxpepino.wordpress.com/2007/06/07/television-en-ubuntu-linux/)

me parece que no es con la saa7134 pero bueno, por lo menos hay que arrimar el bochin y no bajar los brazos.

Bueno por ahora eso, despues sigo buscando. Sau2!

---

### Post by vk-cdg on 2008-03-27
Esta noche llego a casa y posteo el resultado del lspci. 

Una cosa no me queda del todo clara hasta este momento y es la siguiente. 
Yo de entrada, le mandé los valores de card y tunner que posteó tzulberti en su mini how to. Luego tiré el reconfigure del tvtime para que apunte a /dev/video1 (en video0 tengo la webcam) y salió sintonizando lo mas bien. Veo los canales perfecto.

Puede ser que el hecho de elegir X sintonizador haga que se vean los canales pero no el sonido? Yo no probé con todos los números de sintonizador, en ningún momento corrí el script ese que anda dando vueltas para encontrar el N° de sinto. Tendrá que ver eso?

Si es así, primero corro eso.

---

### Post by tzulberti on 2008-03-27
Sino me equivoco tambien habia que configurar algo del sonido en tvtime... Fijate que tambien tiene una opcion para eso. Ademas, en las opciones de sonido tenes que deshabilitar el linein (cuando haces doble clic en la opcion de subir/bajar volumen).

No te puedo ayudar mucho mas porque hace tiempo que no tengo la placa sintonizadora.

---

### Post by vk-cdg on 2008-03-28
El lspci me tira esto

```
vikingo@Sion:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
07:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
vikingo@Sion:~$ 
```

El dmesg | grep saa me tira esto

```
vikingo@Sion:~$ dmesg | grep saa
[   29.797130] saa7130/34: v4l2 driver version 0.2.14 loaded
[   29.797540] saa7130[0]: found at 0000:01:08.0, rev: 1, irq: 20, latency: 32, mmio: 0xfdeff000
[   29.797545] saa7130[0]: subsystem: 1131:2341, board: ProVideo PV952 [card=51,insmod option]
[   29.797552] saa7130[0]: board init: gpio is 5d31ff
[   29.931004] saa7130[0]: i2c eeprom 00: 31 11 41 23 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   29.931011] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 37 31 33 30 20
[   29.931016] saa7130[0]: i2c eeprom 20: 41 41 48 53 ff ff ff ff ff ff ff ff ff ff ff ff
[   29.931022] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.931027] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.931032] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.931037] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.931042] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.074750] tuner 2-0060: chip found @ 0xc0 (saa7130[0])
[   30.082730] tuner 2-0061: chip found @ 0xc2 (saa7130[0])
[   30.093407] saa7130[0]: registered device video1 [v4l2]
[   30.093431] saa7130[0]: registered device vbi0
[   30.093450] saa7130[0]: registered device radio0
vikingo@Sion:~$ 
```

---

### Post by xpelaox on 2008-03-30
hola muchachos, hace unos meses me compre una encore TV tuner pro enl tv-fm alguien tiene idea si se puede hacer andar?:S Saludos

---

### Post by Mauro22 on 2008-03-30
> **xpelaox said:**
> hola muchachos, hace unos meses me compre una encore TV tuner pro enl tv-fm alguien tiene idea si se puede hacer andar?:S Saludos

Dicen que con los kernels mas actuales ya esta el soporte para la saa713x.

Entonces, con probar no cuesta nada.

En consola hace:

sudo rmmod saa7134_alsa saa7134_dvb saa7134
sudo modprobe saa7134 card=3 tuner=69

y abri el tvtime o gnomeradio y fijate si anda.

:lolflag:

---

### Post by xpelaox on 2008-03-30
cuando puse el primer comando me decia que no existia  saa7134_dvb

no me importo, segui.

ahora el tvtime me dice: Frames too short from saa7134
No puedo abrir dispositivo de captura /dev/video0/


:S:S:S:S:S:S:S:confused:

---

### Post by faktorqm on 2008-03-31
Ahora que sabemos que es la 7130 la cosa va mejorando. Fijate que los dispositivos los tenes, el tema es que funcionen bien.

este tiene tooooooooooooda la pinta de funcionar, fijate que el lspci que tiene el chabon es IDENTICO al tuyo;
[http://www.larepaweb.com.ar/index.php?id=post&n=243](http://www.larepaweb.com.ar/index.php?id=post&n=243)

y aca hay un bug en launchpad, no se que onda:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209247)

y sino: 
[http://www.ubuntu-es.org/index.php?q=node/57707](http://www.ubuntu-es.org/index.php?q=node/57707)
[http://ubuntuforums.org/showthread.php?t=437325](http://ubuntuforums.org/showthread.php?t=437325)

Lo seguimos viendo salu2!!

---

### Post by vk-cdg on 2008-03-31
> **faktorqm said:**
> Ahora que sabemos que es la 7130 la cosa va mejorando. Fijate que los dispositivos los tenes, el tema es que funcionen bien.

este tiene tooooooooooooda la pinta de funcionar, fijate que el lspci que tiene el chabon es IDENTICO al tuyo;
[http://www.larepaweb.com.ar/index.php?id=post&n=243](http://www.larepaweb.com.ar/index.php?id=post&n=243)

y aca hay un bug en launchpad, no se que onda:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209247)

y sino: 
[http://www.ubuntu-es.org/index.php?q=node/57707](http://www.ubuntu-es.org/index.php?q=node/57707)
[http://ubuntuforums.org/showthread.php?t=437325](http://ubuntuforums.org/showthread.php?t=437325)

Lo seguimos viendo salu2!!

Mil gracias por la data, la verdad es que no se me ocurrió buscar en google con el resultado de dmesg | grep saa tal cual como aparece.
Ayer, entre todos los valores que probe, con card=2 el sonido andaba pero muy muy bajito, apenas se escuchaba por lo auriculares que conecté directo a la salida de la sintonizadora. Eran como las 2AM y no había ni un ruidito en casa, de casualidad lo escuché. 
El problema es que todos los volumenes estaban al mango y el otro problema (y principal) es que luego de cerrar el TVtime sigue sonando.
De mas está decir que descarté ese n° de card.

Hoy probaré con estos valores que aparecen en los links que me paseste. 
Mil gracias!

---

### Post by vk-cdg on 2008-04-04
Bueno, ahora si que la c*gué del todo!

Me prestaron una placa sintonizadora ENCORE ENLTV+FM. La instalé en la PC y me dispuse a seguir un tutorial que encontré en internet haciendo los siguientes pasos:

*1) Instalar mercurial:*

```
sudo apt-get install mercurial
```

*2) Descargar el fuente del driver:*

```
hg clone http://linuxtv.org/hg/v4l-dvb
```

*3) Instalar el driver:*

```
cd v4l-dvb
sudo make
sudo make install
```
[I]
4) Liberar los modulos que Feisty instala por defecto y cargar los nuevos (se puede hacer un script para esto)[/I]

```
sudo rmmod saa7134_alsa
sudo rmmod saa7134_dvb
sudo rmmod saa7134
sudo modprobe saa7134 card=107
sudo modprobe saa7134_alsa
sudo modprobe saa7134_dvb
```

*Ahora cuando hago un dmesg | grep saa me tira esto:*

```
vikingo@Sion:~$ dmesg | grep saa
[   31.917455] saa7134: Unknown symbol videobuf_streamoff
[   31.917501] saa7134: Unknown symbol videobuf_poll_stream
[   31.917544] saa7134: Unknown symbol videobuf_read_stop
[   31.917628] saa7134: Unknown symbol videobuf_dma_free
[   31.917672] saa7134: Unknown symbol videobuf_reqbufs
[   31.917762] saa7134: Unknown symbol videobuf_waiton
[   31.917841] saa7134: Unknown symbol videobuf_dqbuf
[   31.917948] saa7134: Unknown symbol videobuf_queue_init
[   31.918150] saa7134: Unknown symbol videobuf_dma_unmap
[   31.918172] saa7134: Unknown symbol videobuf_read_stream
[   31.918202] saa7134: Unknown symbol videobuf_querybuf
[   31.918268] saa7134: Unknown symbol videobuf_qbuf
[   31.918321] saa7134: Unknown symbol videobuf_read_one
[   31.918471] saa7134: Unknown symbol videobuf_iolock
[   31.918512] saa7134: Unknown symbol videobuf_streamon
[   31.918630] saa7134: Unknown symbol videobuf_mmap_mapper
[   31.918727] saa7134: Unknown symbol videobuf_mmap_free
[   31.926558] saa7134: Unknown symbol videobuf_streamoff
[   31.926603] saa7134: Unknown symbol videobuf_poll_stream
[   31.926645] saa7134: Unknown symbol videobuf_read_stop
[   31.926728] saa7134: Unknown symbol videobuf_dma_free
[   31.926771] saa7134: Unknown symbol videobuf_reqbufs
[   31.926860] saa7134: Unknown symbol videobuf_waiton
[   31.926937] saa7134: Unknown symbol videobuf_dqbuf
[   31.927044] saa7134: Unknown symbol videobuf_queue_init
[   31.927232] saa7134: Unknown symbol videobuf_dma_unmap
[   31.927253] saa7134: Unknown symbol videobuf_read_stream
[   31.927283] saa7134: Unknown symbol videobuf_querybuf
[   31.927348] saa7134: Unknown symbol videobuf_qbuf
[   31.927399] saa7134: Unknown symbol videobuf_read_one
[   31.927548] saa7134: Unknown symbol videobuf_iolock
[   31.927588] saa7134: Unknown symbol videobuf_streamon
[   31.927705] saa7134: Unknown symbol videobuf_mmap_mapper
[   31.927801] saa7134: Unknown symbol videobuf_mmap_free
```

Hago un lspci para ver si la placa es detectada y si, aparece:

```
01:07.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
```

La placa es fisicamente [esta]("http://www.topcomputer.com.ar/imgMercadoFotos/l_sintonizadora-FM-GRANDE.4.gif"). 
Por un momento pensé que podía estar muerta por lo que inicié en windola y levantó de una. 
Algo me pareció de lo mas extraño, mi placa, es una Genius TVgo a11. Al arrancar con la encore instalada, no la detectó, no pidió ningun driver, cuando abro el soft para ver TV (desde windola) salió andando lo mas bien. Apagué todo y saqué la placa y la comparé con la mía. Resulta que son IDENTICAS!

Me pregunto por que no puedo hacer anadar ninguna en mi ubuntu cuando de la ENCORE hay miles de tutos con los números de card y tuner.

La pregunta, o mas bien, pedido desesperado es como hago ahora para cargar los módulos de la saa713x porque ahora el dmesg no la reconoce.


Los tutos que seguí son estos:
[http://www.ubuntu-es.org/index.php?q=node/45630](http://www.ubuntu-es.org/index.php?q=node/45630)
[http://www.ubuntu-es.org/index.php?q=node/78523](http://www.ubuntu-es.org/index.php?q=node/78523)
[http://ubuntuforums.org/showthread.php?t=304444](http://ubuntuforums.org/showthread.php?t=304444)

Entre otros tantos.

---

### Post by vk-cdg on 2008-04-04
Otra de las cosas que hice fue esto

1) Ver si está cargado:

```
#dmesg | grep saa
```

Debería aparecer el detalle de la tarjeta sintonizadora. Si no aparece nada, entonces hay que cargar el módulo del kernel. Si aparece alguna como Phillips, o similar, entonces está cargado pero posiblimente no correctamente. 

2)  Descargar los módulos del kernel:

```
#sudo rmmod -f saa7134_alsa
#sudo rmmod -f saa7134-dvb
#sudo rmmod -f saa7134
```

[COLOR="DimGray"]Al querer hacer este paso me da el siguiente error:
```
vikingo@Sion:~$ sudo rmmod -f saa7134_alsa
[sudo] password for vikingo:
ERROR: Removing 'saa7134_alsa': No such file or directory
vikingo@Sion:~$ sudo rmmod -f saa7134-dvb
ERROR: Removing 'saa7134_dvb': No such file or directory
vikingo@Sion:~$ sudo rmmod -f saa7134
ERROR: Removing 'saa7134': No such file or directory
vikingo@Sion:~$ 

```[/COLOR]

Si te da error al descargar, lo ideal es pasar a una consola (Control + ALT + F1) matar las X (sudo killall gdm) y ejecutar los comandos anteriores desde ahí.

3) Instalar modconf:

```
#sudo apt-get install modconf
```

4) ejecutar modconf

```
#sudo modconf 
```

5) modconf permite buscar módulos posibles para cargar en el kernel y configurarlos. Busca en la lista uno por uno (de paso te familiarizas con el sistema algooooo ) hasta encontrar el saa7134. Una vez encontrado, apretar ENTER.

6) Aparecerán todos los módulos relacionados. Si alguno está cargado aparecerá con un + y si no con un - (lo más probable es que aparezcan todos con un - dado que los descargamos previamente.

7) Posicionarse sobre saa7134 y apretar enter. Preguntará si queremos instalarlo y decimos "si".

algooooo Luego aparecerá la posibilidad de insertar opciones. Este paso es importante. Acá debemos elegir correctamente la placa y el sintonizador. Si tu placa es la ENLTV o ENLTV-FM, modificar la linea por defecto (o escribirla) para que diga:

```
card=3 tuner=38
```

Luego aceptar...

[COLOR="DimGray"]Al hacer estos últimos pasos y seleccionar el modulo saa713X me sale el sigueinte error:
```
FATAL: Error inserting saa7134 (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Falló la instalación.

```[/COLOR]


Y listo... con TVTIME se puede configurar luego la norma (En mi caso, Argentina: PAL Nc) y el tipo de entrada (Television) así como la sintonía fina... todo debería funcionar.

---

### Post by vk-cdg on 2008-04-10
A la pelota, apenas unos días y ya estoy en la página 3. Snif snif.

Decidido a hacer andar esta alpargata, consulté al oráculo (San Google) y me topé con este post del foro de ubuntu-es:

[http://www.ubuntu-es.org/index.php?q=node/76478](http://www.ubuntu-es.org/index.php?q=node/76478)

Uno de los post decía esto:

[I][COLOR="DimGray"]Tengo una tarjeta ENLTV-FM de Encore con el chip SAA7130 que hasta donde yo he podido investigar esta soportada por el mismo driver que para el chip SAA7134, acabo de instalar Gutsy, hice lo que hacia siempre para instalarla en ubuntu 6.06 y 7.04 y esta vez no me funcionó, investigando encontre varios tuturiales y ninguno me sirvio, hasta que encontre que gutsy lo soporta en forma nativa, aunque yo no pude revertir lo que había hecho y tuve que reinstalarlo, una vez instalado nada más instalé el tvtime y gnome radio, el gnomeradio me decia que no sa podía abrir el dispositivo dev/radio y nada más le agrege dev/radio0 y ya con esto me funciono tanto la tv como el radio.

Espero te sirva.

Saludos desde Celaya, Gto. México[/COLOR][/I]

Muy prrobablemente sea por eso que cuando hago un dmesg | grep saa me sale esto

```
[   31.917455] saa7134: Unknown symbol videobuf_streamoff
[   31.917501] saa7134: Unknown symbol videobuf_poll_stream
[   31.917544] saa7134: Unknown symbol videobuf_read_stop
[   31.917628] saa7134: Unknown symbol videobuf_dma_free
[   31.917672] saa7134: Unknown symbol videobuf_reqbufs
[   31.917762] saa7134: Unknown symbol videobuf_waiton
[   31.917841] saa7134: Unknown symbol videobuf_dqbuf
[   31.917948] saa7134: Unknown symbol videobuf_queue_init
[   31.918150] saa7134: Unknown symbol videobuf_dma_unmap
[   31.918172] saa7134: Unknown symbol videobuf_read_stream
[   31.918202] saa7134: Unknown symbol videobuf_querybuf
[   31.918268] saa7134: Unknown symbol videobuf_qbuf
[   31.918321] saa7134: Unknown symbol videobuf_read_one
[   31.918471] saa7134: Unknown symbol videobuf_iolock
[   31.918512] saa7134: Unknown symbol videobuf_streamon
[   31.918630] saa7134: Unknown symbol videobuf_mmap_mapper
[   31.918727] saa7134: Unknown symbol videobuf_mmap_free
[   31.926558] saa7134: Unknown symbol videobuf_streamoff
[   31.926603] saa7134: Unknown symbol videobuf_poll_stream
[   31.926645] saa7134: Unknown symbol videobuf_read_stop
[   31.926728] saa7134: Unknown symbol videobuf_dma_free
[   31.926771] saa7134: Unknown symbol videobuf_reqbufs
[   31.926860] saa7134: Unknown symbol videobuf_waiton
[   31.926937] saa7134: Unknown symbol videobuf_dqbuf
[   31.927044] saa7134: Unknown symbol videobuf_queue_init
[   31.927232] saa7134: Unknown symbol videobuf_dma_unmap
[   31.927253] saa7134: Unknown symbol videobuf_read_stream
[   31.927283] saa7134: Unknown symbol videobuf_querybuf
[   31.927348] saa7134: Unknown symbol videobuf_qbuf
[   31.927399] saa7134: Unknown symbol videobuf_read_one
[   31.927548] saa7134: Unknown symbol videobuf_iolock
[   31.927588] saa7134: Unknown symbol videobuf_streamon
[   31.927705] saa7134: Unknown symbol videobuf_mmap_mapper
[   31.927801] saa7134: Unknown symbol videobuf_mmap_free

```

Alguien tiene idea de si esto se puede revertir y como?
No voy a reinstalar como lo hizo el amigo Mexicano, en todo caso esperaré a la salida de Hardy que tengo pensado hacer una instalacion limpia. De todas formas me gustaría solucionarlo en Gutsy.

Por otro lado, estuve probando el LiveCD de mandriva, que la trae soportada nativamente, con solo especificarle el numero de card y tuner sale andando (estando en LiveCD).
Lo investigué un poco, pero me gusta mas mi Ubuntu, a Mandriva lo veo como medio secote, quizás le falte personalización, pero bue, me dio la sensación de estar comiendo un sanguche de pan solamente.


**Para no hacer un doble post.... EDITO**

La cag*da que me mandé fue justamente por seguir tutos sin saber que hace cada instrucción... en fin.
Buscando en google me topé varias veces con esto, pero no entiendo bien por que es que lo hacen y que es lo que hace. Se que algo del sonido tiene que ver (no hay que ser un genio para saberlo) pero bue, si alguien me puede encender una lámpara (hechar luz) con esto se agradece.

Lo que hacen es esto:

*en el archivo /etc/modprobe.d/alsa-base*

```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

```

---

### Post by ariel on 2008-04-10
Ojo, las placas con saa7134 como la tuya se piantan mal con hardy (8.04). Antes de hacer tu upgrade en un par de semanas, consulta aca:

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212271](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212271)

---

### Post by vk-cdg on 2008-04-10
Vaya que agradable noticia! :(

Alguien tiene algún cable para tirarme sobre como deshacer la macana que me mandé sin tener que reinstalar?

---

### Post by vlitzer on 2008-04-24
> **tzulberti said:**
> Yo tengo una saa7134...
Mini How-to:
en /etc/modprobe.d/ crear un archivo llamado saa7134 con el siguiente contenido: 
alias char-major-81     videodev
alias char-major-81-0   saa7134
options saa7134 tuner=37 card=51
Paso 2: reiniciar
Paso 3: 
Configurar el tvtime, para que lea cable (dpkg-reconfigure tvtime). Dentro de la configuracion del tvtime, hacer que el mismo use PAL-NC y yo lo tengo que poner en TV (mono only)

Espero que eso te sea de ayuda, ya que a mi me funciona

Altisimo genio es ud..

Tengo una Encore ENLTV-FM, como siempre en windows anda joya, en linux segui muchos tutos, ninguno me andubo. Hice lo q esta ahi, y arranque el tvtime, y andubo perfecto. Ahora el unico problema que tengo es que no logro hacer andar el sonido. Tengo una mother intel GIZ946, con el audio onboard Sigmatel. Ya probe todas las combinaciones posibles de activar swiches y volumenes, no hay forma. Tengo hardy recien instalado y limpito. Alguien tiene idea de como puedo hacer andar el audio en el tvtime? tambien me interesaria poder usar la radio.

Gracias por adelantado.

---

### Post by tzulberti on 2008-04-24
> **vlitzer said:**
> Altisimo genio es ud..

Tengo una Encore ENLTV-FM, como siempre en windows anda joya, en linux segui muchos tutos, ninguno me andubo. Hice lo q esta ahi, y arranque el tvtime, y andubo perfecto. Ahora el unico problema que tengo es que no logro hacer andar el sonido. Tengo una mother intel GIZ946, con el audio onboard Sigmatel. Ya probe todas las combinaciones posibles de activar swiches y volumenes, no hay forma. Tengo hardy recien instalado y limpito. Alguien tiene idea de como puedo hacer andar el audio en el tvtime? tambien me interesaria poder usar la radio.

Gracias por adelantado.

Para hacer andar el sonido sino mal recuerdo en TvTime tenia que seleccionar una opcion (no recuerdo muy bien cual porque hace tiempo que no tengo mas esa sintonizadora), y destildar el mute del Mic-in (o de algo similar asi que aparecia en la opcion de sonido).

Saludos,
TZ

---

### Post by vlitzer on 2008-04-24
Si tambien probe todas las variantes del volumen dentro del tvtime pero no funciona igual :(

Y con el tema de la placa de sonido, el problema es q no se que cosa corresponde que opcion :(

Ahi esta un screen de lo q me aparece en el panel de volumen.

---

### Post by fmsismo on 2008-04-25
Probaste con el cable loop del sonido (que sale de la placa capturadora y lo deberías conectar al line in o mic (este último si no tenes la primera opción))?

Si hiciste eso, asegurate de habilitar y subir el volumen de las entradas de sonido.

Yo probe una flyview 2000 con gusty y no tuve problemas.  Si el canal lo tenes sintonizado y la norma es correcta (pal-nc) por la salida de audio de la placa tenes que tener sonido (es por hard que por ahí tiene que salir).  Para aislar problemas, pone unos auriculares o parlantes.

Estas seguro que la sintonizadora que configuraste es la que corresponde no (en el módulo especificas cual es la placa y la sintonizadora que usa)?

Yo lo que hice para descubrir cual es la mía fue usar un script que estaba dando vueltas por ahí (lo adjunte) y recorrí todas las variantes (cambiaba el archivo de frecuencias sintonizadas).  Busque las 4 o 5 que más habían detectado y probe con esas (preparate café y tenes que estar dispuesto a poner tu paciencia a prueba).


Alguien pudo hacer andar la fm?  Vengo con varias frustraciones con este tema. :-S

---

### Post by vk-cdg on 2008-04-26
> **ariel said:**
> Ojo, las placas con saa7134 como la tuya se piantan mal con hardy (8.04). Antes de hacer tu upgrade en un par de semanas, consulta aca:

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212271](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212271)

Mas allá de que seguro voy a actualizar a Hardy, quise probar como se comportaba con la sintonizadora de TV y si el bug este había sido solucionado. 
Arranqué la PC con el liveCD de Hardy y luego de descargar los módulos genéricos de la placa (una ENLTV-FM) y cargrlos con los parámetros de mi placa descubro que el problema es el mismo que antes. Sintoniza a la perfección, pero no se escucha nada.
Luego de probar varias cosas, enchofé unos auriculares directamente sobre la salida de audio de la placa y descibro que se escucha pero muy bajito, casi imperceptible (esto en 8.04) cosa que también me pasaba con 7.10.

Alguien tiene idea de que puede ser? Los niveles de volumen están todos al mango y todos habilitados.

Seguramente es una combinación entre el hardware y Ubuntu ya que levantando un LiveCD de Mandriva y haciendo el mismo procedimiento el nivel de audio es OPTIMO, se escucha de primera.

Mi mother es una ASUS M2N-E y la sintonizadora una ENCORE ENLTV-FM.

Alguna idea?

---

### Post by vlitzer on 2008-04-29
bueno, hice como me dijeron arriba y corregi los parametros.. listo funciona el audio saliendo de la placa de tv. lo que sigue sin andar, es el line in de mi placa de sonido :( no hay manera. Creo q voy a tener q comprarme alguna mas decente para que funcione. Para el que busque los parametros de la encore ENLTV son 

tuner=3 card=51

al menos a mi me funcionaron.

---

### Post by vk-cdg on 2008-04-29
Yo tengo el mismo problema que vos, si conecto los parlantes directamente a la salida de la placa, anda de maravillas, pero si tengo conectado el puente no se escucha nada. 

Ahora, en esto algo tiene que ver ubuntu, ya que con el LiveCD de mandriva, el sonido sale a un volumen óptimo, con la conexión indicada (es decir, usando el puente).

---

### Post by Applelnx on 2008-05-07
Hola, queria revivir este thread por un problema que tengo con mi placa de tv.

Chipset: btv878
Modelo: Kozumi KTV-01C

Instale v4l para hacerla funcionar segun este tutorial:
[http://mfireweb.wordpress.com/2007/02/12/tutorial-para-placa-tv-encore-tv-fm-enltv-fm/](http://mfireweb.wordpress.com/2007/02/12/tutorial-para-placa-tv-encore-tv-fm-enltv-fm/)

Despues vi que tambien lo habian puesto aca. El tema es el siguiente:

- no puedo cambiar de canal
- no se escucha nada :(

Les pego lo que me tira el dmesg (vi que muchas veces lo necesitaban para entender el problema)

```
[   27.741819] Linux video capture interface: v2.00
[   27.826689] bttv: driver version 0.9.17 loaded
[   27.826696] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   27.826803] bttv: Bt8xx card found (0).
[   27.826852] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[   27.826874] bttv0: Bt878 (rev 17) at 0000:02:01.0, irq: 21, latency: 64, mmio: 0xfdfff000
[   27.826901] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   27.826952] bttv0: gpio: en=00000000, out=00000000 in=007fc0ff [init]
[   27.827910] tveeprom 1-0050: Huh, no eeprom present (err=-121)?
[   27.827917] bttv0: tuner type unset
[   27.827921] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   27.828742] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   27.829588] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   27.830452] bttv0: registered device video0
[   27.830487] bttv0: registered device vbi0
[   28.210695] input: PC Speaker as /devices/platform/pcspkr/input/input4

```

el lspci me tira:

```
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:02.0 Communication controller: Conexant HSF 56k Data/Fax Modem
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

```

Se ve imagen, pero solo de 1 canal :'(

Alguien me podria ayudar?

pd: perdon por la longitud del post

---

### Post by Applelnx on 2008-05-09
Problema solucionado: encontre la lista de tarjetas, me fije cual era la correcta (card=151) y se soluciono todo :D

Saludos

---

### Post by hernyman on 2008-05-10
Si tienen una KWorld Analog PCI Lite las opciones que tienen que poner en el /etc/modprobe.d/saa7134 son:

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 tuner=69 card=63
```

y funciona JOYA :KS

---

### Post by Applelnx on 2008-05-10
A mi me ayudo leer el README de video4linux (nunca lo habia encontrado :mad:)

---

