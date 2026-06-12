---
title: "Ayuda. No Puedo Entrar Al Entorno Gráfico."
date: 2007-10-26
forum: Argentina Team
---

### Post by gustmarti on 2007-10-26
Hola Gente. Les pido ayuda con un problema que capaz es simple pero no lo pude solucionar. La cuestión es que al instalar la versión 7.10 en notbook e intentar adjuntar la resolución 1280x800 en el menu de opciones y aplicarla se me puso la pantalla negra y a partir de ahí nunca mas pude entrar al entorno gráfico, cuando inicio la maquina 
va directamente al modo consola y por más que haga crtl-alt-f7 no puedo pasar al modo gráfico.
Buscando en los post encontre al alguien que le habia pasado algo similar usando el berryl y se le recomendó que haga ps ax luego encontrar el proceso y hacerle kill. Pero no se cual es el proceso para correguir la resolución. La placa de video es una MOBILE INTEL (R) 945 GM EXPRESS CHIPSET FAMILY.
espero me puedan ayudar

---

### Post by gustmarti on 2007-10-26
Alguie que me ayude, please

---

### Post by margori on 2007-10-26
Creo que somos muchos los que te podemos ayudar, pero necesitamos que nos cuentes cual es tu problema.

Si es que no has podido resolver el problema de un thread (hilo o discusion) ya hecho, sigue insistiendo por ese thread, porque una vez que pones un nuevo post queda primero en la lista nuevamente.

Si es por otro problema, pone el nombre o descripcion del problema en el titulo y conta que es lo que te pasa.

---

### Post by jorgito on 2007-10-26
Hola gustmarti, 

Yo mucho de esto no entiendo, pero estoy practicamente convencido de que si no explicas que clase de ayuda necesitas, va a ser complicado darte una mano.

Creo que tendrias que explicar un poco que te esta pasando, (con Ubuntu se entiende).

Suerte

---

### Post by gustmarti on 2007-10-26
Gracias, no se porque no se ve el post que mande antes yo lo veo en la lista, acá lo repito

Hola Gente. Les pido ayuda con un problema que capaz es simple pero no lo pude solucionar.
La cuestión es que al instalar la versión 7.10 en notbook e intentar adjuntar la 
resolución 1280x800 en el menu de opciones y aplicarla se me puso la pantalla negra 
y a partir de ahí nunca mas pude entrar al entorno gráfico, cuando inicio la maquina 
va directamente al modo consola y por más que haga crtl-alt-f7 no puedo pasar al modo gráfico.
Buscando en los post encontre al alguien que le habia pasado algo similar usando el berryl y se le 
recomendó que haga ps ax luego encontrar el proceso y hacerle kill. Pero no se cual es el proceso para 
correguir la resolución. La placa de video es una MOBILE INTEL (R) 945 GM EXPRESS CHIPSET FAMILY.
espero me puedan ayudar

---

### Post by Hei Ku on 2007-10-26
la respuesta rapida es que desde la consola hagas:

sudo pico /etc/X11/xorg.conf

y desde ahi edites el archivo y borres el modo 1280x800

La otra es que desde consola hagas:

sudo dpkg-reconfigure xserver-xorg

eso te va a ayudar a reconfigurar la placa. Elegis la opciones por default y con eso deberias poder volver a ingresar al modo grafico. Despues de eso, podemos seguir con tu problema.

---

### Post by gustmarti on 2007-10-26
Gracias lo intento y me conecto devuelta.

---

### Post by Mafber on 2007-10-26
Hola, no estoy muy seguro si te va servir esto... pero por las dudas proba. 
sudo dpkg-reconfigure xserver-xorg
con esto tendrías que poder reconfigurar "xorg.conf" Si mal lo recuerdo debería reconfigurarse solo cuando detecta que hay un error
Suerte!!!

---

### Post by gustmarti on 2007-10-26
Mil gracias, lo intento y te digo

---

### Post by gustmarti on 2007-10-26
MIL GRACIAS. PUDE RECONFIGURAR EL XSERVER y volvi a ver iconos y el cursor. como los extrañe. Hasta me funciona la placa wifi que con la distro anterior nunca pude hacer que funcione. MIL GRACIAS GENTE

---

### Post by niko_3100 on 2007-10-26
hay un paquete llamado 915resolution apenas abris el synaptics te paso la descripcion para que veas me parece que te va a venir al pelo. Ubuntu se instala mucho mejor en noteboks que en pc de escritorio armadas, obviamente por el hardware debe ser mas comun de fabricantes.

resolution modification tool for Intel graphic chipset
915resolution is a tool to modify the video BIOS of the 800
and 900 series Intel graphics chipsets. This includes the 845G,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
This modification is necessary to allow the display of certain
graphics resolutions for an Xorg or XFree86 graphics server.

915resolution's modifications of the BIOS are transient.
There is no risk of permanent modification of the BIOS.
This also means that 915resolution must be run every time the
computer boots in order for its changes to take effect.
If you want to automatically set the resolution on each boot
and before X is launched, see /usr/share/doc/915resolution/README.Debian
for information about configuring the provided initscript.

 Homepage: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

---

