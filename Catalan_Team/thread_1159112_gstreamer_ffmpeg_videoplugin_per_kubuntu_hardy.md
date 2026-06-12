---
title: "gstreamer ffmpeg videoplugin per kubuntu hardy"
date: 2009-05-14
forum: Catalan Team
---

### Post by indiosincracia on 2009-05-14
últimament no puc reproduïr els videos del youtube des de /tmp (nomès passa en videos nous desde Febrer).
Amb el xubuntu jaunty instal·lant gstreamer ffmpeg videoplugin es va resoldre pero no amb kubuntu hardy:
He fet la prova amb la pantera rosa,

[http://www.youtube.com/watch?v=F3gGpf1eCyY](http://www.youtube.com/watch?v=F3gGpf1eCyY)

indiu@hal:/tmp$ kaffeine Flash5GW6Pn
kaffeine: ERROR: KXineWidget: No codecs to handle media
indiu@hal:/tmp$ /usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
  
indiu@hal:/tmp$ vlc Flash5GW6Pn
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[flv @ 0x7f41e6de6160]Unsupported video codec (7)
[00000365] main decoder error: no suitable decoder module for fourcc `undf'.
VLC probably does not support this sound or video format.
[00000405] main decoder error: no suitable decoder module for fourcc `undf'.
VLC probably does not support this sound or video format.

Merci, salut.

---

### Post by CarlesOriol on 2009-05-16
A mi em funciona (aquest mateix video) amb el vlc, totem i xine. I no ho fa el mplayer.

Tens instal.lats els codecs de medibuntu?

---

### Post by indiosincracia on 2009-05-16
doncs tinc aquests:
libdvdcss
libdvdcss2 
libdvdread3
w64codecs
libavcodec-dev
non-free-codecs
kubuntu-restricted-extras
quan l'obro amb kaffeine surt un popup:

---

### Post by CarlesOriol on 2009-05-17
Pot ser per que tens una distribucio de 64 bits... mmmm... (reflexions en tecla alta)

---

### Post by orestesmas on 2009-05-17
Fa temps que ja no tinc la Hardy i no ho puc provar, però amb la kubuntu jaunty de 64 bits no hi ha problemes per reproduir aquest vídeo amb el firefox.

Quin plugin de flash tens instal·lat?

Amb quin navegador fas les proves?

Dius que l'obres amb el Kaffeine, però jo diria que això no pot funcionar. Aniria bé si la URL que li fiques tingués només el vídeo, però una pàgina del youtube és essencialment una pàgina HTML amb un objecte flash incrustat (el reproductor), i dubto molt que el kaffeine sàpiga extreure el vídeo d'aquí (el youtube-dl ho fa, i no és un procés trivial). Jo de tu no provaria d'obrir-lo directament amb el kaffeine sinó amb el firefox.

El que sí que pots provar és a baixar-te el vídeo amb el youtube-dl i aleshores provar de reproduir-lo amb el kaffeine o mplayer. Hauria de funcionar.

---

### Post by indiosincracia on 2009-05-18
Hola orestesmas, he volgut ser breu i no ho he explicat gaire bé.

No és pas amb el firefox amb qui hem barallo, naturalment amb youtube-dl, elltube o alguns "adons" del firefox pots baixar-tels i amb ffmpeg i avidemux passar-los a l'extensió que bulguis (aquest mateix video baixat amb youtube-dl es reprodueix perfectament).

Es tractava de reproduir algunes hores de documentals d'aquesta pàgina [http://www.documentary-log.com/](http://www.documentary-log.com/) com que no tenia temps ni prou ample de banda, el que feia era seleccionar el documental premer al play i treure el so o pause i minimitzar el navegador, (mentres feia punyetes meves), un cop el documental carregat a la carpeta /tmp el copiava a /home /Desktop amb la intenció de reproduir-lo més tard.
És curiós que passa només en alguns vídeos des de'l mes de Febrer i amb la Hardy, amb Jaunty es reprodueixen tots, (el que he fet es passar-los en un segon ordinador amb Jaunty), però ara estic encuriosit, aquí n'hi ha un que li passa el mateix: 
[http://ubuntuforums.org/showthread.php?t=1061606](http://ubuntuforums.org/showthread.php?t=1061606)

La versió del flash 9.0.159
ffmpeg 3.0

---

### Post by PatrickVogeli on 2009-05-18
sembla que es problemes de codecs... aquests videos flash estan fets d'alguna manera que el totem, vlc, etc  del hardy no saben tractar i, en canvi, els de jaunty si.

Tingues en compte que el totem, vlc, etc, no fan servir res del flash player per reproduir els arxius .flv.

salut

---

### Post by CarlesOriol on 2009-05-20
Els que he baixat jo per provar d'on a dit idiosincracia son codificats amb windows media video. El flv és un format de fitxer no de codificacio (em sembla)

---

