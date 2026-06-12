---
title: "[SOLVED] Amule y la Web no conviven"
date: 2008-02-23
forum: Argentina Team
---

### Post by pol666 on 2008-02-23
Bueno mi problema es que amule me anda perfecto, kadlemia tambien,
me va a 60 kb/s aun compartiendo poco peeeeeeeeeeeero...

Firefox anda lentisimo (navegacion en gral) 
Google tarda unos 4seg, y todo igual de lento...

Fijense si observan algo mal


paso mi captura:


[IMG]http://i27.tinypic.com/2ugywc2.png[/IMG]


Bueno a ver si alguien sabe que puede suceder..

Mi conexion

Speedy adsl 512k
Modem Ethernet

---

### Post by facundocorradini on 2008-02-23
Lógicamente!!!

si estás matando la conexión con el amule... Tenés que bajarle el límite de descarga, como para dejarle un aire a la navegación web.

---

### Post by pol666 on 2008-02-23
pero eso lo copia de mi configuracion en win..
es raro

no se un problema de puertos?


65k esta bien si lo bajo el amule no bajaria absolutamente nada
eso es lo que tiene que ir, mas de 65 no.

---

### Post by facundocorradini on 2008-02-23
bueh, yo no uso p2p salvo por algún que otro torrent. 

Pero me parece absolutamente normal que si estás bajando a 65K y subiendo a 10 no puedas hacer practicamente nada más.

Más aún teniendo speedy.... el ancho de subida es muy limitado

---

### Post by margori on 2008-02-23
Estimado pol666:
Según veo en la captura, estás considerando que la capacidad de tu conexión es de 512 kBps (kilo bytes por segundo) cuando en realidad tenés una conexión de 512 kbps (kilo bits por segundo).

Con esa conexión la máxima velocidad de descarga es de 64kBps. Si quieres que te funcione bien la navegación deberías limitar la descarga de aMule a un valor menor que eso, digamos 57.6 para dejar un 10% de ancho de banda libre.

Por otro lado, las conexiones ADSL normalmente el ancho de subida es un cuarto del ancho de bajada, es decir que una bajada de 64kBps tiene un máximo de subida de 16kBps, como antes tenés que limitarlo a menos, digamos unos 14.4, dejando un 10% libre.

Otro punto es la cantidad de conexiones simultáneas. Mientras más conexiones tenés más larga la cola de espera antes que un petición en el navegador sea enviada al servidor. 400 no está mal, aunque ese número mientras más bajo mejor para las respuestas, pero podés tener menor tasa de descarga.

Resumiendo, tu problema no es más que la asignación de un recurso escazo, la velocidad de subida y bajada.

Buena suerte. Nos vemos.

---

### Post by pol666 on 2008-02-23
margori, gracias por una respuesta tan desarollada y eficaz, te agradesco muchisimo.

si bien sigue andando lento es ya problema de mi isp.
ASi que doy este tema como solved.

Muchas gracias

---

### Post by pante on 2008-02-25
Con ADSL el gran limitante es la subida. Supongo que para tu conexión será 128 kb/s. Esto significa 64 KBytes de bajada y 16 kBytes de subida.

En **Capacidad**, como dice abajo, es sólo para calcular los gráficos. Habría que poner: Descargar=64 y Subida=16.

De los **Límites** el más importante es el de subida, porque tiene que ser lo más alto que se pueda sin saturar tu conexión. Un valor inicial de 10 kBytes/s está bien. Si no se puede navegar, lo vas reduciendo gradualmente hasta encontrar el punto. El límite de descarga pocas veces es necesario reducirlo.

Pero que quede claro que si para poder navegar aceptablemente tenés que poner la subida a menos de 10 kB/s, tu conexión deja mucho que desear, y tu ISP tiene que arreglarlo.

---

