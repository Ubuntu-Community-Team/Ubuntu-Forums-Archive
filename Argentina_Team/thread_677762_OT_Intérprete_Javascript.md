---
title: "OT: Intérprete Javascript"
date: 2008-01-25
forum: Argentina Team
---

### Post by jclevien on 2008-01-25
Hola,

Necesitaría obtener un intérprete Javascript en línea de comandos. Idealmente, tendría que funcionar así: escribo "jsinterp codigo.js" y me devuelve en un archivo el output que genera el código Javascript.

Esto lo estoy necesitando en Windows y Linux.

¿Vds. conocen algún intérprete de este estilo, que corra standalone (sin necesidad de tener un navegador instalado)?

Gracias.



Juan

---

### Post by mexpolk on 2008-01-25
SpiderMonkey...

the code-name for the Mozilla's C implementation of JavaScript.

[http://www.mozilla.org/js/spidermonkey/](http://www.mozilla.org/js/spidermonkey/)

---

### Post by jclevien on 2008-01-25
Hola mexpolk,

Gracias por el link. De hecho, ya compilé con éxito el jsshell, y funciona pero "parcialmente". Es decir, el problema es así:

Tengo un script hecho en Javascript. El mismo está embebido en una página web. La página se descarga de un servidor y viene ya con todas las funciones, lo único que hay que hacer es abrirla con un navegador y listo.

El problema es que el jsshell, si bien funciona, no lee correctamente ciertos objetos que son propios de la página HTML, es decir, interpreta solo código puro JS.

La idea es integrar esas funciones en un programa, ya sea automatizando un Firefox, o creando un objeto "CORBA" de Firefox (no se si se puede, no conozco CORBA), o como se pueda... la idea que tengo es correr un Firefox en un Ubuntu y crear un servidor que de respuesta a peticiones mediante TCP.

El esquema sería mas o menos así:

Cliente -----> Servicio en Ubuntu -> Ejecuta Firefox con funciones
Cliente <----- Servicio en Ubuntu <- Resultado

Cualquier sugerencia es más que bienvenida.

Muchas gracias.



Juan

---

### Post by jclevien on 2008-01-28
Listo, ya lo solucioné.
Una mezcla de PHP, REALbasic, Xubuntu, Firefox y otras yerbas...

Gracias.


Juan

---

