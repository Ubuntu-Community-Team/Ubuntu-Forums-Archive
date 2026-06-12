---
title: "Optima Configuracion de Sonid: Brilla Por su auscencia"
date: 2008-02-16
forum: Argentina Team
---

### Post by pol666 on 2008-02-16
Bueno, el problema es lo siguiente....

Instale los driver de sonido de vuelta por que se escuchaba pesimo, ahora mejoro, lo noto mas claro aun asi escucho muy saturado...

La placa es una Sound Blaster Audigy, tengo sonido 5.1 y con los driver de win se escuchaba muy lindo, en fin aca no lo logro darle ese toque de calidez al sonido

Este es el **.asounrc**

> #########################################################
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
        type plug
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
}
########################################################
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
    type plug
    slave.pcm "hw:0,1"
}

#######################################################
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want. 


pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}

[B]
el asound.conf NO TIENE NADA 
el esd.conf NO TIENE NADA 
[/B]

Soluciones que mejoraron un poco:
[LIST]
[*]Instalar Alsamixer para Gnome y regular el volumen de los altavoces.

[*]Normalizar los mp3 con mp3gain
y hacer:
 $ find . -type f -iname '*.mp3' -print0 | xargs -0 mp3gain -r -k
[/LIST]

PD: Otra cosa es el que el mix de sonido se va default cuando reinicio es un bajon que pase eso y tener que activar todos los canales otra vez, ese es otro tema y si alguien sabe, agradesco su ayuda

---

### Post by faktorqm on 2008-02-18
Bueno, raro problema el tuyo, vamos a ver que se puede hacer.

Primero, tenes una placa integrada en la mother? por que de ser asi la tenes que desactivar del BIOS para que el linux no se """confunda""" ni generar conflictos de irq.
(aunque no deberia no siempre es asi) y listo.

Segundo, si estas seguro de que la desactivaste, te copypasteo algo del foro de ubuntu-es:

"Acabo de abrir el control de volumen. En la pestaña de conmutadores he desmarcado la opción "Audigy Analog/Digital Output Jack" y... yaaa ta'; se hizo el sonido."

Tercero, me lo saltee por que decis que escuchas sonido, mal pero escuchas. El tema del alsamixer, que onda con eso? tenes los volumenes bien activados y esas cosas? si t pasa que queres cambiar el volumen y no podes le tenes que poner que te controle el front.

Cuarto, tu chip es el ca0106? por que la mayoria de los post que veo son para ese integrado, o sea, hay varios modelos. Mira este post en este blog que al menos tiene info sobre los archivos que vos tenes vacios. (pregunta: tenes instalado el alsa mixer?!?)

[http://dudas.wordpress.com/2007/03/24/ubuntu-facil-sonido-51-en-ubuntu/](http://dudas.wordpress.com/2007/03/24/ubuntu-facil-sonido-51-en-ubuntu/)

Bueno, segui buscando y esclareciendo un poco la situacion, me di cuenta de que hay un driver distinto para cada placa..... la lista esta aca:

[http://alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

Ahora bien, a partir de aca tenes que saber que chip tenes con dmesg en la consola o desde el gnome-device-manager desde el entorno grafico. 

Si el chip que tenes vos no esta listado en alsa, capaz podemos llegar a usar uno "parecido". Si sigue sin andar, deberiamos probar OSS como servidor de sonido. 

El alsaconf que te dice? lo tenes?  bueno basta de preguntas. fijate punto por punto todo lo que te dije aca, lo mas importante es averiguar que chip tenes. Salu2!!

---

### Post by pol666 on 2008-02-19
Bueno ayer justamente solucione 2 de los problemas:

El de flash reinstalando firefox desde synaptic nada raro.

y un poco el sonido mejoro al modificar los dos archivos con una configuracion

Igual no consigo mi antiguo y calido sonido surround solo sonido 3d clasico 

y ni hablar de poner musica fuerte.. imposible se satura todo

Me dijeron que baje el foobar para ubuntu, no se ni lo que es :roll: pero bue veremos.

Otra cosa, no hay un Equalizador que me permita regular los bajos, agudos ?
ammm

---

