---
title: "No puedo reproducir avi ni stream.. codecs?"
date: 2007-11-17
forum: Argentina Team
---

### Post by Mataca on 2007-11-17
Hola gente? como andan tanto tiempo?

weno les cuento mi problema, instale mediante fresh install Gusty. Todo fue de maravillas, la verdad es una maza esta nueva version!!

Bueno como paquete nro 1 instale "ubuntu restricted extras" que tengo entendido instala codecs, mp3 etc etc... Luego instale mplayer sin ningun tipo de error.

Pero no puedo reproducir videos ni divx, avi. la pantalla se ve rosa pero se escucha el sonido. Lo cual me hace pensar que es un tema de codecs.  me pasa con todos los reporductores, y no me tira el clasico "falta tal codec, quiere descargarlo... Alguna idea???

Por otro lado, mi viejo no puede ver las carreras online de turf. Que las transmiten en vivo mediante windows media player 10. Alguna sugerencia como puedo hacer para ver este tipo de stremeeng? o como se escriba :)

Espero solucionar estos problemillas. Abrazos

---

### Post by Hernán-Amaya on 2007-11-17
fijate si tenés instalado libavcodec1d

por lo que dice el synaptic te puede servir

This is the codec library from the ffmpeg project. It supports most existing
encoding formats (MPEG, DivX, MPEG4, AC3, DV...).

---

### Post by clasificado on 2007-11-17
> **Mataca said:**
> 
Por otro lado, mi viejo no puede ver las carreras online de turf. Que las transmiten en vivo mediante windows media player 10. Alguna sugerencia como puedo hacer para ver este tipo de stremeeng? o como se escriba :)

Probá con el reproductor embebido que tiene mplayer.

Sino será wine nomás

Clasificado

---

### Post by guillermolisi on 2007-11-17
Mataca

Que placa de video tenes, con cuanta RAM ?

Te pregunto porque tengo el mismo problema con una Compaq DeskPro (si, me encantan las antiguedades) con una placa PCI Matrox Millennium G200 que (creo) es de 8 Mb. 

En otras Deskpro pero con TNT2 Riva con 32 Mb funciona todo perfecto.
Tengo los codecs, la libreria libavcodec1d, etc. pero solo hay audio, de video nada, solo el fondo del VLC, Kaffeine, del Xine o cualqueir repro que use para ver videos (probe con AVIs) en un solo color solido.

Para mi que el problema pasa por la RAM de la placa de video por lo que sucede con las otras dos Deskpro con placas con mas memoria que la del caso.

---

### Post by Mataca on 2007-11-18
Chicos, tengo una gforce 7900 gt 256 mb, no creo q sea la placa ya que con feisty andaba todo de maravilla. Esto me sucedio ahora con Gusty
Los codecs andan de 10 !! ya lo solucione solo. Simplemente reinstale el paquete "Ubuntu restricted extra" reinicie y listo

---

### Post by faktorqm on 2007-11-19
matacaaaaaaaaaaaaaa!!!!!!!!!!!!

proba esto a ver que onda: 

```
sudo aptitude install ffmpeg
```

no me acuerdo de memoria el paquete, y aca en el laburo se me kemo el disco con linux, asi que todo mal, de ultima hace aptitude search ffmpeg.
sino en casa te busco bien algo. salu2!

---

