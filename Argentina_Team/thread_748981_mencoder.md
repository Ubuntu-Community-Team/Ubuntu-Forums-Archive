---
title: "mencoder"
date: 2008-04-08
forum: Argentina Team
---

### Post by lega on 2008-04-08
Buenas, a ver si alguien puede darme una mano con esto, me bajé una pelicula y resulta que el audio esta fuera de sincro con el video, para win el mismo grupo que codifico la peli sacó .bat que arregla la desincronización, pero no para lin, pues bien averiguando me dijeron que podía arreglarlo con mencoder
> Si tenes el mplayer (y mencoder) usa esto para arreglarlo:

mencoder -oac copy -ovc copy -delay -0.314 He.Was.A.Quiet.Man.2007.DVDRip.XviD-VoMiT.avi -o He.Was.A.Quiet.Man.2007.DVDRip.XviD-VoMiT-fixed.avi

contentisimo de dispuse a hacer el arreglo y me pasa esto > ~/Videos/He Was a Quiet Man$ mencoder -oac copy -ovc copy -delay -0.314 He.Was.A.Quiet.Man.2007.DVDRip.XviD-VoMiT.avi -o He.Was.A.Quiet.Man.2007.DVDRip.XviD-VoMiT-fixed.avi
MEncoder 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) Processor (Family: 6, Model: 4, Stepping: 2)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x2bdf7000
AVI file format detected.
VIDEO:  [XVID]  640x352  12bpp  23.976 fps  858.2 kbps (104.8 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:640x352  fps:23.98  ftime:=0.0417
videocodec: framecopy (640x352 12bpp fourcc=44495658 )
audiocodec: framecopy (format=55 chans=2 rate=48000 bits=0 B/s=19855 sample- 0 )

ahí se queda...puedo dejarlo horas (de hecho me fui a trabajar y volvi a las 10 horas y estaba igual) que será lo que esta pasando?

Alguien sabe si con el avidemux puedo hacer esto? es decir correr el audio de un video 314milisegundos para atras? lo estuve mirando pero ni idea como se hara.
Gracias

---

### Post by sdennie on 2008-04-09
avidemux debe funcionar pero, tambien podes usar '-' y '+' en mplayer para sincronizar el audio sin modificar el .avi.

---

### Post by lega on 2008-04-09
Gracias no la sabía esa, pero yo quería arreglar el video porque las peliculas las veo en el reproductor de dvd de mesa.

De todos modos ya lo arreglé con Mencoder, se me ocurrió habilitar los repositorios backports y lo actualizé y ahí funcionó :)

Igualmente si alguien sabe como se haría esto con Avidemux se agradecería el dato
Saludos

---

### Post by pante on 2008-04-10
En Avidemux en la parte Sonido podés elegir el CóDec en un menú, hay un botón Configurar y un botón Filtros y una opción Desfase. Creo que podrías usar esa opción Desfase y probar algunos valores, o dándole al botón Filtros configurarlo donde dice "Time Shift (ms)".

Para no esperar que codifique la película completa, seleccioná un fragmento de película y codificalo; si el resultado es satisfactorio, dale con todo.

Saludos :)

---

