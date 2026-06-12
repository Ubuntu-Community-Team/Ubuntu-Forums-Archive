---
title: "Pinnacle PCTV Stereo (SAAxxx)"
date: 2007-11-07
forum: Argentina Team
---

### Post by Lauchazo on 2007-11-07
Hola gente, les comento que soy un total principiante con linux, y estoy sorpendido por la nueva ubuntu 7.10, realmente buenisimo.
Mi problema es que no he podido ver tele con mi Pinnacle PCTV stereo SAxxx (no brooktree).
Estuve leyendo otros posts sobre este mismo tema y no sirvieron, no se si por falta de manejo de linux o que.
Lo que les puedo comentar es que instale el Xawtv y lo unico que pasa cuando lo inicio, es que toda mi pantalla se pone negra, y se queda asi indefinidamente.
Tambien probe MythTv, pero por alguna razon no pude hacerlo andar.
Tambien intente con VLC player, pero no hace nada, no muestra imagen ni tira sonido.

Alguno me podra orientar un poco?

Mil gracias!

---

### Post by tzulberti on 2007-11-08
Mira... Si es una saa7134 aca tenes un mini-howto de como configurarla...
[http://ubuntuforums.org/showthread.php?t=304444](http://ubuntuforums.org/showthread.php?t=304444)

Respuestas #24 y #26. En el xawtv no lo puede configurar, pero no tuve problemas en el tvtime.

---

### Post by Lauchazo on 2007-11-08
Muchas gracias tzulberti!, esta noche lo pruebo y te comento como va.

---

### Post by Lauchazo on 2007-11-08
tzulberti, desde ya te agradezco por tu respuesta, pero te comento que segui tu how-to y aun asi sigo sin poder hacerlo funcionar. El tvtime simplemente muestra pantalla negra y nada de sonido.
Use tus archivos de configuracion y nada. Tambien intente que autoconfigurara los canales, pero sin suerte..
tenes alguna otra idea, o tendre q seguir viendo tele desde Win?
Muchas gracias...

---

### Post by tzulberti on 2007-11-09
> **Lauchazo said:**
> tzulberti, desde ya te agradezco por tu respuesta, pero te comento que segui tu how-to y aun asi sigo sin poder hacerlo funcionar. El tvtime simplemente muestra pantalla negra y nada de sonido.
Use tus archivos de configuracion y nada. Tambien intente que autoconfigurara los canales, pero sin suerte..

Dos cosas:
1) Corre el tvtime desde consola (escribiendo tvtime), y fijate que mensajes te aparecen
2) Una vez dentro del tvtime, recuerdo que tenia que seleccionar el cable, la señal (ya no tengo la placa sinotinizadora por lo que no puedo probar). Cambiastes alguno de los valores de ahi?

> **Lauchazo said:**
> 
tenes alguna otra idea, o tendre q seguir viendo tele desde Win?
Muchas gracias...

Que perdida de espacio en el rigido tener un windows :)

---

### Post by Lauchazo on 2007-11-09
[QUOTE=
Que perdida de espacio en el rigido tener un windows :)[/QUOTE]

jejejeje sisi... de a poco me estoy convirtiendo en un creyente....
Mirá, te paso el resultado de tvtime -v:

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/lauchazo/.tvtime/tvtime.xml
cpuinfo: CPU AMD Athlon(tm) XP 2600+, family 6, model 10, stepping 0.
cpuinfo: CPU measured at 1913.232MHz.
xcommon: Display :1.0, vendor The X.Org Foundation, vendor release 70000000
xfullscreen: No support for the vidmode extension, assuming square pixels.
xfullscreen: Pixels are square.
xfullscreen: Number of displays is 1.
xfullscreen: Head 0 at 0,0 with size 1152x864.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is compiz and is EWMH compliant.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 48: Xgl Generic Texture Video.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /home/lauchazo/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'saa7134', card 'ProVideo PV952' (bus PCI:0000:01:08.0).
videoinput: Version is 526, capabilities 5010015.
videoinput: Maximum input width: 720 pixels.
tvtime: Sampling input at 720 pixels per scanline.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (70).
station: Reading stationlist from /home/lauchazo/.tvtime/stationlist.xml
station: Reading stationlist from /home/lauchazo/.tvtime/stationlist.xml
/home/lauchazo/.tvtime/stationlist.xml: No existing PAL-NC station list "us-cable100".
station: Adding frequency table us-cable100, all channels active
station: Reading stationlist from /home/lauchazo/.tvtime/stationlist.xml


Te dice algo nuevo??
Gracias!

---

### Post by tzulberti on 2007-11-09
Vamos con todos los detalles:
1) Para poder usar la placa sintonizadora vas a necesitar tener configurado la placa de video con aceleracion OpenGL. Esto se hace instalando los drivers privativos (por lo menos en los casos de nvidia, no se con ati).
2) En etc/modprobe.d/ crear un archivo llamado saa7134 (en verdad tiene que ser saaXXXX) como root (sudo gedit /etc/... ) con el siguiente contenido:
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 tuner=37 card=51

3) Reiniciar la PC
4) Instalar tvtime (sudo apt-get install tvtime), y configurarlo para que use el protocolo Pal-Nc y Cable. Si ya lo tenes instalado, podes cambiar las configuraciones haciendo "sudo dpkg-reconfigure tvtime".

5) Abrir el tvtime. Si ya tenias el archivo de configuracion borralo antes de abrirlo. En el menu que aparece (sino te aparece presiona TAB)  ir a Input Configuration, Television Standard. Asegurarse que figure Pal-NC. En ese mismo menu, ir a Change Video Source. Creo que ahy te figuraban tres opciones (no puedo entrar porque no tengo una placa sintonizadora instalada asique hasta ahi llego).

---

### Post by Illuminator on 2007-11-11
Proba arrancar el TVTime desde la consola:

```
gksudo tvtime
```

---

