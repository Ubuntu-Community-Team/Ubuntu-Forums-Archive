---
title: "limpieza con Synaptic"
date: 2007-10-24
forum: Argentina Team
---

### Post by jorgito on 2007-10-24
Hola a todos,

En el Synaptic tengo unas cuantas aplicaciones que aparecen como "No Instaladas (configuracion residual)" que quiero saber si se pueden remover...
Es posible que hayan aparecido despues de hacer el upgrade a Gusty, pero la verdad no estoy seguro.
Si alguno tiene idea si rompo algo que por favor avise!

Un cordial saludo!

---

### Post by sajnox on 2007-10-24
```
 $ sudo apt-get autoremove 
```

Va a eliminar los paquetes que no esten en uso

```
 $ sudo apt-get clean
```

Limpia paquetes que esten descargados y no en uso

para mas opciones 

```
 $ apt-get --help
```

---

### Post by tzulberti on 2007-10-24
Tambien te recomiendo que instales un paquete que se llama deborphan que te busca todas las librerias que tenes instaladas y que ningun otro paquete las necesita. Es decir, son librerias que se instalaron porque las necesitaba un programa, pero que no se borran cuando se borra el programa.

---

### Post by Dropknee on 2007-10-24
falto este otro, que es el que por comando, borra los residual config.

```
sudo aptitude purge ~c
```

---

### Post by Mataca on 2007-10-25
> **tzulberti said:**
> Tambien te recomiendo que instales un paquete que se llama deborphan que te busca todas las librerias que tenes instaladas y que ningun otro paquete las necesita. Es decir, son librerias que se instalaron porque las necesitaba un programa, pero que no se borran cuando se borra el programa.


Weniiisima onda ese paquete, sale uno para mi pc =)

---

### Post by por100pre1 on 2007-10-25
Buena idea, solo tengan cuidado de no remover algunos codecs. Algunos paquetes de codecs aparecen como paquetes huérfanos. :)

---

### Post by sharkg on 2007-10-26
Buena la aclaracion!!!! sino nos quedamos sin codecs varios... jeje saludos

---

### Post by jorgito on 2007-10-26
Muchas Gracias!

Esta quedando mucho mas prolijo!

---

