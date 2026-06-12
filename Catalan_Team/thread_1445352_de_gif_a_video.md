---
title: "de gif a video"
date: 2010-04-02
forum: Catalan Team
---

### Post by sianeu on 2010-04-02
He creat un gif animat amb el gimp. Ara voldria afegir-lo a un muntatge amb el kdenlive, que no l'accepta com animaciò (mostra nomès la primera foto). He provat de convertir-lo a avi amb el ffmpeg, però no em surt:

> sianeu@sianeu-desktop:~/Escriptori$ ffmpeg gif -i prova2.gif prova.avi
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
Unable to find a suitable output format for 'gif'
sianeu@sianeu-desktop:~/Escriptori$ 


Què podria fer?

Salut

---

### Post by papapep on 2010-04-02
Prova el que diuen [aquí]("http://www.kdenlive.org/forum/animated-gif-import").

---

### Post by sianeu on 2010-04-03
Molt agraït per la pista. M'ha fucionat de primera.

Pels qui volen saber més:
Amb el sinaptic he instalat un plugin del gimp que es diu gimp-gap. Aquest afegeix un nou menù a la barra d'eines que es diu "video", on cal buscar l'eina "Master videoencoder", i, desprès de complimentar les dades (pal, nº de fotogrames...) s'aplica i ja està el avi fet i a punt pel kdenlive.

nota: A calgut fer-ho des d'el gif animat, dons si ho feia desde la foto amb les diverses capes, la capa de fons (que s'ha de veure a tots els fotogrames) no sortia (es veia nomès al primer fotograma). Falta d'habilitat, està clar, però no tinc gaire experiencia.

Salut

---

