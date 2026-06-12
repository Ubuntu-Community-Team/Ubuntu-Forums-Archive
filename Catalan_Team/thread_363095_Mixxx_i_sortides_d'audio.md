---
title: "Mixxx i sortides d'audio"
date: 2007-02-16
forum: Catalan Team
---

### Post by cortsenc on 2007-02-16
Hola!

El primer post en aquest fòrum va de música.
La història és que fa temps que busco un programa per a "punxar discos". O sigui, per posar cançons (en dos canals en temps real) per anar-les convinant. Vaig trobar el Mixxx i he de reconeixer que va força be   >>[http://mixxx.sourceforge.net/](http://mixxx.sourceforge.net/)   però tinc un problema. No se com configurar dues sortides d'àudio. M'explico.

Per poder lligar les cançons, és indispensable que m'entre esta sonant una peça, puguis escoltar l'altre per un altre canal (uns auriculars), cosa que el programa suporta. Potser fent la sortida princial al Jack i els auriculars per USB, no ho se. La qüestió és que el propi programa limita les sortides a **/dev/dsp** que no tinc ni idea de que és. He intentat obrir el arxiu i esta en blanc :confused: 
Be, si algú em pot explicar quin és aquest arxiu /dev/dsp i perquè esta en blanc?

:guitar:

---

### Post by Ivà on 2007-02-16
A veure, sense ser-ne un expert ni molt menys, però crec que el primer que necessites és una tarja de sò que tingui dos canals d'audio de sortida i que a més estigui suportada sota linux.

Si la que tens ja ho té i està correctament reconeguda pel kernel i configurada, tindries tants /dev/dsp1 ... /dev/dspn com canals de sortida. I aleshores redirigeixes el sò cap on vulguis.

---

### Post by orestesmas on 2007-02-16
Buff... si que apretes per ser el primer!

Anem a pams: en primer lloc /dev/dsp no és un fitxer real, sinó que és un pseudofitxer que crea el kernel (concretament el driver de la teva tarja de so) per tal de poder-hi accedir. En unix la gran majoria de dispositius de maquinari es veuen com a fitxers, excepte alguns com ara les interfícies de xarxa que van diferent.

Com diu Ivà, per escoltar dues coses diferents alhora hauràs d'enrutar-ne una cap a un dispositiu i l'altre cap a l'altre. T'hauràs de mirar com ho fa això cada aplicació (a vegades és un paràmetre de la línia d'ordres), però si uses una aplicació compatible amb JACK potser la cosa és més planera. Tanmateix, estic mirant la web del mixxx aquest i a la doc. en PDF diu:

"The binary version is not compiled with support for Jack. If you want to use Jack Sound
Server you have to install Mixxx from source."

O sia que si vols JACK l'has de compilar. Altrament no sé quin sistema de so suporta, perquè és multiplataforma. Segurament en GNU/Linux deu suportar OSS o ALSA.

Mira, ja ho he trobat: a la Doc (més avall) posa que això es configura a Options -> Preferences:

Configure soundcard and latency
When Mixxx is launched first time it detects your installed
sound cards, and tries to select a reasonable device for sound
output. You can check the settings, by selecting Preferences
from the Options menu.
In Mixxx you can use one sound card for output at a time. In general you will need a card
with two stereo channels for live performance, one for Master output, and one for
headphone output (cueing). If you practice you can work with one stereo card, mapping
master output to the left channel of your card, and headphone output to the right channel.
In this way you can work with both master and
headphone output using a normal stereo sound card,
although the output will be in mono.
Currently Mixxx does not support multiple sound
cards open at the same time. The reason for this is
mainly that it will increase the overall latency of the
system to use several sound cards at the same time.
Thus we recommend to use one multichannel card
instead.

Vaja, que millor una tarja de 2 canals, o si només en tens una amb un canal (estéreo) hauràs d'emetre la música en mono.

Bé, mira-t'ho i ja diràs.

---

### Post by cortsenc on 2007-02-17
Val,
Tinc accés a un portàtil amb una sola sortida, i la meva torre que te dues sortides d'audio. Per tant, de moment, ho provarem amb la torre.

Estic compilant el programa, i m'encallo en el primer punt:
> cortsenc@amd64:~/Desktop/mixxx-1.4.2/src$ ./configure --enable-Jack
-----------------------------------------------------------
Project file is:       mixxx.pro           enable
Checking whether QTDIR is set ........ no ,

__ QTDIR must be properly set.
__ Please see at [http://www.trolltech.com](http://www.trolltech.com), section developers
__ and find the installation instructions.

He googlejat i en algun lloc he llegit que és un directori. Llavors he intentar crear el directori directament dins /usr/lib/qt3/ però no ha funcionat. M'he mirat la pàgina que em diu però el meu nivell d'anglès no m'ho ha deixat trobar.
Seguiré buscant...


**Edito: **Sembla ser que és un directori antic. He aquesta ordre i s'ha arreglat.
> export QTDIR=/usr/share/qt3

Segueixo compilant...

**Ara m'he enquellat aqui;**
> In file included from dlgpreferences.cpp:23:
mixxx.h:22:18: error: qapp.h: No such file or directory
mixxx.h:32:21: error: qmsgbox.h: No such file or directory
make: *** [.obj/dlgpreferences.o] Error 1


Però pel missatge que surt, no és problema del meu ordinador, no?

---

### Post by orestesmas on 2007-02-17
A veure un moment... se suposa que has instal·lat prèviament els paquets de desenvolupament necessaris, no? Em sembla que són

libqt3-mt-dev
qt3-apps-dev
qt3-dev-tools

Confirma'm aquest punt abans de seguir.

---

### Post by cortsenc on 2007-02-17
Si, abans d'aquest anava donant diferents errors del tipus "no es pot, perquè falta aquesta llibreria -dev" i els he anat instal·lant.

Però aquest últim error no se que fer.

---

