---
title: "información sobre sources list"
date: 2007-07-31
forum: Argentina Team
---

### Post by marcesneibrun on 2007-07-31
Hola quería saber todo acerca de source list, como opera, para que sirve, y como se implementa en una terminal?
Es obligatorio usarlo?
Muchas Gracias
Marcelo

---

### Post by aceki on 2007-07-31
En lo unico que te puedo ayuda es como podes editarlo:

sudo nano /etc/apt/sources.list

Ahi vas a ver en donde dice deb blablablabla esa es la lista del repositorio, podes agregar las que vos quieras.

---

### Post by kowal on 2007-07-31
Básicamente, */etc/apt/sources.list* es el archivo donde figuran los repositorios (que a su vez, contienen los paquetes a descargar/instalar)..

+Info:
[http://es.wikipedia.org/wiki/Sources.list](http://es.wikipedia.org/wiki/Sources.list)

---

### Post by marcesneibrun on 2007-07-31
SI UTILIZO EL SYNAPTIC, O AÑADIR Y QUITAR APLICACIONES, Y A SU VEZ DESCARGO LAS ACTUALIZACIONES QUE ME INFORMA UBUNTU Q HAY A TRAVES DEL SYNAPTIC, ES NECESARIO HACER sudo apt-get update y sudo apt-get upgrade?
Gracias por las respuestas
Marcelo

---

### Post by spg76 on 2007-07-31
> **marcesneibrun said:**
> SI UTILIZO EL SYNAPTIC, O AÑADIR Y QUITAR APLICACIONES, Y A SU VEZ DESCARGO LAS ACTUALIZACIONES QUE ME INFORMA UBUNTU Q HAY A TRAVES DEL SYNAPTIC, ES NECESARIO HACER sudo apt-get update y sudo apt-get upgrade?
Gracias por las respuestas
Marcelo

Cuando estás en Synaptic, presiona el botón "Recargar" y te actualizas la lista de paquete, tal cual como lo harías en una terminal. Esto no siempre es necesario ya que el notificador de actualizaciones chequea sin que uno tenga que hacerlo.
Si agregas un repositorio, tenes que presionar recargar en Synaptic (o hacer sudo apt-get update y sudo apt-get upgrade en una terminal) porque sino no te va a aparecer la lista actualizada hasta que el corra el notificador de actualizaciones.
Saludos.

---

### Post by marcesneibrun on 2007-07-31
Primeramente quiero agradecer por toda la ayuda en el foro, mi pregunta es la siguiente como hago para agregar repositorios a traves de la terminal y de donde los obtengo?
gracias 
marcelo

---

### Post by kowal on 2007-08-01
Por lo general con los repositorios oficiales de Ubuntu alcanza (rara vez se recurre a un repositorio externo). Lo que si es recomendable es que actives los repositorios Universe y Multiverse.

Saludos

[http://www.guia-ubuntu.org/index.php?title=Activar_universe_y_multiverse](http://www.guia-ubuntu.org/index.php?title=Activar_universe_y_multiverse)

---

### Post by facundocorradini on 2007-08-01
El sources.list es la lista de repositorios ("lugares") desde donde vas a descargar el software mediante el sistema apt. Synaptic es una interfaz gráfica para este sistema.

Las principal ventaja de esta forma de instalar software es que todo lo que descargas viene de una fuente confiable, por lo que sabés que está libre de cualquier tipo de amenaza, que funciona y que estás bajando la ultima versión estable.
 Además el sistema se encarga automáticamente de descargar todas las dependencias (otro software que el que estás bajando necesita para funcionar bien).


[B]Normalmente alcanza con los repositorios oficiales de ubuntu (lo que vienen activados default).
[/B]
Desde synaptic podés modificar el sources.list, actualizar la base de datos y todo eso sin necesidad de entrar en la consola (a la que la mayoría de los usuarios novatos temen como si se tratara del mismísimo cuco)

Te paso unas "equivalencias"

sudo apt-get install nombredelpaquete:    buscas en synaptic el nombre del paquete y le das doble click, luego el boton instalar...
sudo apt-get update:     boton recargar del sinaptic
editar sources.list:          configuracion ---> repositorios. Creo que el cuadro de dialogo es suficientemente explicativo.

Saludos y espero haber sido de ayuda!
Facundo

---

