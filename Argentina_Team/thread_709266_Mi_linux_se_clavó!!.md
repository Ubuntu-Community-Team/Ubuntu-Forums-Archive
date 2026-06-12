---
title: "Mi linux se clavó!!"
date: 2008-02-27
forum: Argentina Team
---

### Post by wanchan on 2008-02-27
Hola, que tal.
Me pasó esto: estaba queriendo ver un video en youtube, mi conexión se volvió muy lenta, hasta que llegó a que mi sistema no respondiera en nada, pero el raton si me respondía.
Esperé un tiempo para ver si se solucionaba, pero nada, mientras se estaba cargando el video, que de echo se cargaba ,muy lento.
No se que pudo haber pasado, alguien sabe que pudo haber ocurrido?.
No tuve mas remedio que reiniciar el equipo, y con un poco de miedo porque segun leí, sí reinicias linux sin haber guardados tus trabajos u otros archivos, puede afectar algunos archivos que maneja linux para su ejecución eficiente, y éstos se pueden dañar.

Espero alguna sugerencia, y cómo tengo que proceder si me vuelve a suceder.
Gracias.:)

---

### Post by Mauro22 on 2008-02-27
Usando firefox experimente lentitudes en paginas web, hasta que la ventana se pone gris.

Lo mejor es cerrarla y listo.


Seguro es algo de flash o java que esta hinchando.

---

### Post by leo_rockway on 2008-02-27
Si te vuelve a pasar y te sigue funcionando el mouse y el sistema todavia responde un poco, usa un teclado virtual y fijate en top / htop que es lo que te esta consumiendo todos los recursos.

Tambien fijate si dmesg tira algo de informacion.

---

### Post by Hei Ku on 2008-02-27
Youtube? 
Apuesto 1 pinta a pagar en la fiesta de release de Hardy que es un problema con firefox y el plugin de flash :lolflag:

---

### Post by faktorqm on 2008-02-27
Hei ku una vez mas tenes razon, a mi ultimamente en algunos sitios, como Daily Motion por ejemplo, directamente me salta un cartel y me dice "adobe flash player 9: la pagina que usted esta visitando puede esta provocando que el reproductor flash se alentice y es probable que vuelva inestable su sistema, desea interrumpir la ejecucion?" SI/NO. (el msj es aprox jijijij)
La verdad la verdad la verdad, me tiene un pokiiiiiiiiiiiito las bo****s lle****s todo este temita con el flash, es mas, ojala nos pusieramos todos de acuerdo como con el tomate y no visitemos mas paginas con flash asi lo DESINSTALO, que en realidad es todo lo que deseo. Salu2!

---

### Post by godzeus on 2008-02-28
> **Hei Ku said:**
> Youtube? 
Apuesto 1 pinta a pagar en la fiesta de release de Hardy que es un problema con firefox y el plugin de flash :lolflag:

Va a haber una fiesta del release de Hardy, yo me anoto.
Unas cervecitas no me vendrian nada mal, para desenchufarme del laburo.

Saludos

---

### Post by juanman on 2008-02-29
> **faktorqm said:**
> Hei ku una vez mas tenes razon, a mi ultimamente en algunos sitios, como Daily Motion por ejemplo, directamente me salta un cartel y me dice "adobe flash player 9: la pagina que usted esta visitando puede esta provocando que el reproductor flash se alentice y es probable que vuelva inestable su sistema, desea interrumpir la ejecucion?" SI/NO. (el msj es aprox jijijij)
La verdad la verdad la verdad, me tiene un pokiiiiiiiiiiiito las bo****s lle****s todo este temita con el flash, es mas, ojala nos pusieramos todos de acuerdo como con el tomate y no visitemos mas paginas con flash asi lo DESINSTALO, que en realidad es todo lo que deseo. Salu2!

Una pseudo solucion es usar la extension flash block en firefox, q bloquea por defecto todo lo q tenga flash pero te pone un icono de play en cada animacion, video, lo q sea, para reproducir la q quieras.
Se puede colgar alguna vez, pero hay muchisimas menos probabilidades...

Otra cosa... no se podria hacer alguna extension (o tal vez ya exista) q por ej, para los videos de youtube, en ver de abrirte el flash, te lo abra con el plugin del reproductor de video y se vea por streaming el flv? Si no existe, estaria bueno desarrollarlo... aparte se podrian ver videos de youtube (todos los flash en gral) con soft libre...

---

### Post by faktorqm on 2008-02-29
bu... no uso firefox :( existira algo parecido para opera?
Yo lo votaria es por desarrollar un nuevo estandard para animaciones webs, basicamente lo que se me ocurrio es fusionar 3 modelos: el primero, que los fotogramas se guarden en formato SVG como si fueran las estructuras del 3d max, segundo, que se guarden comprimidos en algun formato que no sea tan pesado de descomprimir a tiempo real, y tercero, algun tipo de renderizado tambien a tiempo real partiendo desde las estructuras en SVG. Un proyecto muy ambiocioso sin duda pero que pienso podria desbancar la supremacia flash. Que les parece? una locura? muy dificil? facil? Salu2!!

---

### Post by leo_rockway on 2008-02-29
> **faktorqm said:**
> bu... no uso firefox :( existira algo parecido para opera?


Este UserJS [0] no es exactamente lo mismo, pero es bastante similar a la extension de FF. Te desactiva todo el flash de las paginas y solamente se activa al hacer doble click sobre la pagina (la diferencia con la extension de FF es que se activa todo el Flash y en la extension de FF se puede elegir que activar y que no).
BTW, userjs.org tiene cosas MUY interesantes para usuarios de Opera.

En Konqueror yo usaba la opcion "Cargar filtros solo cuando se necesiten", pero desde que actualice a KDE 3.5.9 (que no es recomendada por kubuntu [1]) esta opcion no funciona y flash me carga directamente.

[0] [http://userjs.org/scripts/general/enhancements/hide-objects](http://userjs.org/scripts/general/enhancements/hide-objects)
[1] [http://www.kubuntu.org/announcements/kde-359.php](http://www.kubuntu.org/announcements/kde-359.php)

---

