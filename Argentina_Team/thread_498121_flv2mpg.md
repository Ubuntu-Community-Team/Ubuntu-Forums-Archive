---
title: "flv2mpg"
date: 2007-07-11
forum: Argentina Team
---

### Post by jajajavi on 2007-07-11
Necesito un script para pasar de flv a mpg, googleando encontré un howto de debian [http://www.cs.unibo.it/~brualdi/guides/shfs.html](http://www.cs.unibo.it/~brualdi/guides/shfs.html) entre otras cosas. ¿Algún maestro armaría un tutorial para hacerlo en Ubuntu? Se agradece!

---

### Post by juanman on 2007-07-11
Bien simple, no es necesario scipts, instala ffmpeg y escribe:
ffmpeg -i tu_archivo.flv tu_nuevo_archivo.mpeg

---

### Post by jajajavi on 2007-07-12
Muchas gracias, funciona, pero sale toda una chorrera de líneas así
```
[flv @ 0x2b54761fa380]Unsupported video codec (4)
[flv @ 0x2b54761fa380]Unsupported video codec (4)
[flv @ 0x2b54761fa380]Unsupported video codec (4)

```

Y al final me dice:
```
Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from 'Unodelosnuestros.flv':
  Duration: 00:02:04.5, bitrate: N/A
  Stream #0.0: Audio: mp3, 44100 Hz, stereo
  Stream #0.1: Video: 0x0004, 29.97 fps(r)
picture size invalid (0x0)
Fallo de segmentación (core dumped)

```

Es grave, doctor?

---

### Post by undiaperfecto on 2007-07-13
queres pasar un video flv al formato mpeg?
si no es muy pesado podes hacerlo via web en [www.zamzar.com](www.zamzar.com)
es facilisimo, espero te sirva.

---

### Post by juanman on 2007-07-13
A mi me funca perfecto... Lo q te dice es como si no reconociera el formato del video. Si el audio (mp3), pero no el video. Y luego se cuelga el programa por un error q deriva del mal reconocimiento del video... Puede ser sea un formato de flash nuevo no soportado. Yo lo probe con videos de youtube y anda bien. Prueba con otros flv para ver si es un problema de ese flv en particular...
Lo instalaste desde los repositorios no? La libreria q deberia haberse instalado q es la q soporta estos formatos es libavformat0d. Yo tengo la libavformat version: 0d.50.5.0. Si no la tienes instalada, hazlo.

Creo q lo mismo e puede hacer con mencoder...

Saludos

---

### Post by se7ensamurai on 2007-07-18
THANK YOU.
MUCHAS GRACIAS!!!!

I've been looking for ffmpeg useage for this purpose for 3 days. I can't believe I found it in spanish. incredible. thank you thank you thank you. the least confusing command line for ffmpeg i have found!

(and i barely speak any spanish too)

---

