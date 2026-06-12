---
title: "Problemas con cerrar ventanas"
date: 2007-08-24
forum: Argentina Team
---

### Post by jorgito on 2007-08-24
Hola a todos!

El otro dia quise probar los efectos de escritorio en feisty. Como era de esperarse no funcionaron, pero no me preocupe demasiado. Sin embargo, despues de  deshabilitarlos las ventanas siguen abriendo y cerrando como si se fueran desplegando o replegando progresivamente y con un poquito de transparencia. Lo mas molesto es que cada vez que abro algo nuevo, no lo puedo cerrar desde la X de la ventana, ya que al pulsarla pierde el foco y no responde. Tengo que ir a cerrarla desde el menu de la aplicacion (por ej: FIle --> Quit). 
Hay forma de eliminar completamente los efectos?

Desde  ya muchas gracias!

---

### Post by por100pre1 on 2007-08-24
Probaste usar Beryl Manager? Tal vez con el puedas usar el manejador de ventanas que te sea mas util.

```
sudo apt-get install beryl-manager emerald-themes emerald
```

---

### Post by Mafber on 2007-08-24
Hola jorgito!!!
Podes mandarle este comando... probablemente haya alguna forma de solucionar tu problema sin este nivel de agresión (eliminar compiz) :)

sudo aptitude remove compiz-core desktop-effects

Suerte

---

### Post by por100pre1 on 2007-08-24
REMOVIDO: post repetido...

---

### Post by jorgito on 2007-08-24
Gracias Mafber, 

Pero entre las cosas que va a sacar esta tambien el escritorio de ubuntu... Es seguro sacarlo?

Saludos y gracias de nuevo!

---

### Post by por100pre1 on 2007-08-24
No es dañino removerlo, es solo el listado de la instalación basica...

---

### Post by jorgito on 2007-08-24
Gracias a vos tambien por100pre1!

Efectivamente se fueron los efectos.
Ahora.. digo yo... donde aprende uno a usar todos los comandos que se pueden usar en la terminal?
Y como se hace para diagnosticar un problema si no estuvieran todos ustedes ayudando a novatos como yo? O como hago para saber que paquete es el  que tiene el problema o hay que reconfigurar....
Esta bien que preguntando se aprende, pero me parece que le tengo que poner un poco de onda para no preguntar lo absolutamente basico.

Saludos y gracias de nuevo!

---

### Post by sajnox on 2007-08-24
Donde aprender??

[http://www.codigolibre.org/modules.php?name=Downloads&d_op=viewdownload&cid=1](http://www.codigolibre.org/modules.php?name=Downloads&d_op=viewdownload&cid=1)

Ahi tenes un par de libros muy buenos para descargar, te recomiendo la guia de ejercicios basicos.

Otra forma de aprender es usar el comando man, por ejemplo 

man cp

y te da un monton de informacion, estos tipos que nos asombran con sus trespuestas tienen las pestañas quemadas de horas con la PC, no hay mucho misterio mas.....

Saludos,

---

### Post by por100pre1 on 2007-08-25
En mi firma hay varios recursos posteados por los colegas ubunteros. Te recomiendo imprimas la Guía de Comandos.
Espero que te aproveche. :)

---

