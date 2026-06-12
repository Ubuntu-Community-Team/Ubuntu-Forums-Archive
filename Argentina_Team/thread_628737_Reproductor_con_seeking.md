---
title: "Reproductor con seeking"
date: 2007-12-01
forum: Argentina Team
---

### Post by Fikcio on 2007-12-01
Mi laburo consiste en hacer transcripciones de audios, así que necesito un reproductor con una buena función de seeking. O sea, tengo que pausar, reproducir y retroceder/adelantar unos segundos (si puedo configurar cuántos, mejor) -- todo sin sacar las manos del teclado. Si aguanta múltiples listas de reproducción en tabs, muchísimo mejor. Algo onda Foobar2000.

¿Alguien sabe?

---

### Post by User21 on 2007-12-03
SI no hay caso, y no consigues una alternativa, aun puedes emular Foobar2000 con wine. Solo es cuestión de probar: sino te convence su desempeño, pues sigue en la busqueda. Yo seguiré investigando!..

Si no instalaste wine, puedes hacerlo mediante 
sudo apt-get install wine (requiere conexion a internet)

y luego, instalalo desde el mismo instalador de win, en la consola:
wine /ruta/programa de instalacion.exe  

Si ya sabias hacer todo esto, jaja, pues perdon! 

No se si te sirven Amarok o Exaile en Ubuntu. La verdad no se como te desempeñas. Son lo mejorcito en players, sobre el pinwino.


Suerte!

---

### Post by Fikcio on 2007-12-03
Gracias, User21.

> No se si te sirven Amarok o Exaile en Ubuntu. La verdad no se como te desempeñas. Son lo mejorcito en players, sobre el pinwino.

Puede ser, pero yo no solo quiero escuchar música. Ninguno de los dos tiene *ambas* funcionalidades, ¿no? El Rhythmbox tiene un seeking con keyboard shortcuts, pero es de diez segundos e inmodificable (AFAIK).

Y sí: si no queda otra voy a tener que probar el Wine.

---

### Post by User21 on 2007-12-03
Chequea los mensajes privados que te envié, por unas cuestiones OFF TOPIC! 
Saludos!

---

### Post by User21 on 2007-12-03
Es muy loco, pero en Synaptic encontre esto:
**TRANSCRIBER**
Transcribe speech data using an integrated editor
Transcriber enables easy transcription of recorded speech.
It is indispensable for every task that involves examination and
transcription of audio files, like transcription of recorded interviews, song
lyrics, radio shows and so on.  It is also useful if you are active
in the field of speech research.

The snack library (included in contrib in transcriber-1.2) is now a
separate package, libsnack2.  This package still includes html_library-0.3.

Lo he probado y al parecer Ubuntu lo tiene todo!!! xD 
Espero te sea util.

```
sudo apt-get install transcriber
```COMO USARLO: desde una consola, simplemente escribe:
```
transcriber </ruta/del/archivo.mp3;wav;ogg>
```Chequea todas las opciones, y puedes abrir cuantos transcriber necesites, desde distintas solapas de la consola... A mi vision general, y no conociendo el tema, parece de todas formas muy completo: seteas intervalos de busquedas, seteas comandos de teclado, vas tipeando mientras ves la barra de reproduccion y los picos de la grafica de onda... 

PRUEBALO!

---

### Post by Alejandro Vidal on 2007-12-03
Nunca usé el Foobar pero entré en la página y me da la sensación de que podrías probar el Audacity. Es realmente muy bueno. Yo lo utilicé para hacer grabaciones para implementar un pbx Asterisk y realmente quedé impresionado. Es un programa de primera.
Saludos.

---

### Post by Fikcio on 2007-12-04
Muchas gracias, User21, pero el Transcriber no es lo que necesito. Tampoco el Audacity, Alejandro. No se hagan drama; ya veré qué hago. Muchísimas gracias.

---

