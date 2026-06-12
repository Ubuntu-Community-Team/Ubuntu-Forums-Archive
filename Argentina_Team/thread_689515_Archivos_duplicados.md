---
title: "Archivos duplicados"
date: 2008-02-06
forum: Argentina Team
---

### Post by h9005 on 2008-02-06
¿Como hago para eliminar archivos duplicados de instaladores o paquetes? ¿Como se si tengo archivos duplicados? Como hago para desinstalar programas sin borrar los instaladores desde añadir quitar, así no hay que descargar de vuelta de internet?

---

### Post by nemodot on 2008-02-06
Cuando instalas un programa desde el synaptic, el "setup" se baja y queda en el sistema, si lo reinstalas, lo hace desde el paquete que previamente bajó.

Si quieres eliminar todos estos paquetes que ya instalaste puedes hacer

```
sudo apt-get autoclean
``` Esto borra los instaladores de los programas que ya se desinstalaron, para ser mas agresivo y borrar todos los instaladores puede hacer:

```
sudo apt-get clean
```

---

### Post by h9005 on 2008-02-06
Y como hago para obtener un listado de cuales son y poder elegir cuales borar y cuales no? Porque al borrar los instaladores tengo que bajarlos de vuelta de internet en caso de que me arrepienta.

---

### Post by marianom on 2008-02-06
Podes ir a /var/cache/apt/archives y hacerlo a mano. Ojo de no borrar uno que te parece instrascendente y después resultó ser una dependencia.
En esta era de soporte digital cada vez más barato (hasta que llegue el canon :)), lo mejor es copiar los paquetes a CD y listo, ahí están.

---

### Post by h9005 on 2008-02-06
Ok gracias y como hago para saber si es una dependencia o no?

---

### Post by faktorqm on 2008-02-07
Anda a sistema -> administracion -> gestor de paquetes synaptic.
Ahi busca el nombre del paquete que queres, y cuando lo encontras, haces click derecho -> propiedades, vas a la ficha dependencias y ahi te dice de que depende y los paquetes sugeridos. La verdad no conozco (en realidad no investigue) como hacerlo por consola, pero calculo que debe ser alguna opcion del apt-get o del aptitude. Salu2!

---

### Post by margori on 2008-02-08
Yo normalmente utilizo la linea:

sudo apt-get autoremove

con eso logro borrar todos los paquetes que realmente no estoy usando. Normalmente son librerías, que al no tener paquetes que dependan de ellas se pueden borrar con toda tranquilidad.

Muchas veces lo he hecho y no he tenido problema.

Aunque veo que no estamos yendo al punto del hilo de conversación "archivo duplicados".

Yo más que nada estoy interesado en una herramienta de limpieza de disco o de liberación. (Disculpen se estoy cayendo en un Off Topic)

---

### Post by anka on 2008-02-08
Un programita que acabo de descubrir gracias a este post (trato de tener el mayor control sobre los archivos, asi que es muy dificil que tenga algo duplicado) es el FSlint, esta en los repos.

Esta bien que no sea EL apocalipsis de los archivos duplicados, pero me gusto que tenga varias opciones. [Aca]("http://www.pixelbeat.org/fslint/") hay un poquito mas de info.

Suerte!

---

### Post by h9005 on 2008-02-08
No estamos tan offtopic. Gracias por el flsynt, lo voy a probar.

---

### Post by h9005 on 2008-02-08
Fslint no pude hacer que ande desde el lin que me mandaste. No me reconoce la direccion del repositorio.

---

### Post by rojojuan on 2008-02-08
Está en los repositorios de Ubuntu -Synaptic.

---

### Post by leo_rockway on 2008-02-08
kleansweep es la respuesta.

---

