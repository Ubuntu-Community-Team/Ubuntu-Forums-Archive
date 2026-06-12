---
title: "Necesito Ayuda Urgente!!"
date: 2007-05-25
forum: Argentina Team
---

### Post by Shot on 2007-05-25
Necesito ayuda estoy usando Fesity y trate de instalar el virtual box y me tiro un error diciendo que no se podia instalar entonces lo cerre y ahora cada vez que quiero abrir el packet manager me dice; The package virtualbox needs to be reinstalled, but I can't find an archive for it.

---

### Post by ferpadro on 2007-05-25
Por que no usas el sitio [http://www.ubuntu-es.org](http://www.ubuntu-es.org) si quieres hacer preguntas en español?

Si quieres posteas aqui en español y esperas que alguien te responda, siento decirlo pero estas perdiendo el tiempo.

Saludos =)

---

### Post by Mafber on 2007-05-26
Hola!! no estoy muy seguro pero proba con desinstalar esos paquetes. Andá al packet manager (Synaptic) y destildá los paquetes que instalaste.

Recuerdo que una vez tuve un problema por haber puesto en el sources.list unas link que no eran para mi versión, pero me funcionaban. Puse para instalar unos archivos y después de instalarlos me tiró un error. Cada vez que abría el gestor de actualización me tiraba un error.

---

### Post by beuno on 2007-05-26
> **ferpadro said:**
> Por que no usas el sitio [http://www.ubuntu-es.org](http://www.ubuntu-es.org) si quieres hacer preguntas en español?

Si quieres posteas aqui en español y esperas que alguien te responda, siento decirlo pero estas perdiendo el tiempo.

Saludos =)

Me parece que estas un poco confundido, este es un subforo en español, para el LoCo argentino.  :D

---

### Post by Shot on 2007-05-26
> **Mafber said:**
> Hola!! no estoy muy seguro pero proba con desinstalar esos paquetes. Andá al packet manager (Synaptic) y destildá los paquetes que instalaste.

Recuerdo que una vez tuve un problema por haber puesto en el sources.list unas link que no eran para mi versión, pero me funcionaban. Puse para instalar unos archivos y después de instalarlos me tiró un error. Cada vez que abría el gestor de actualización me tiraba un error.
Pero es que no puedo abrir el synaptic de ninguna forma siempre me tira ese error.

EDIT: Bueno creo que ya lo solucione...me decia que habia un error en el cache en el archivo /var/lib/dpkg/status asi que lo abri y busque donde estaba la info del paquete del virtualbox que decia half-instaled y lo borre y ahora anda todo bien.

---

### Post by Al_maverick on 2007-05-26
por las dudas, corre los siguientes comandos, para verificar que esta todo ok con el package manager.
```

sudo apt-get udpate

sudo apt-get install -f
```


El primer comando va a actualizar la lista de paquetes, para asegurarse que el cache de sources este ok

El segundo comando es para verificar que no te falte nada de los paquetes y que el package manager esta en un estado consistente.

Por otro lado, habia una thread en este mismo foro sobre la instalacion del virtualbox, parece que es problematica. Que hace el programa que todos quieren instalarlo igual?

Y disculpa si no te pudimos ayudar antes.

---

### Post by Shot on 2007-05-26
Probe esos comandos y todo anda bien gracias.
El virtualbox es un programa para usar virtual pcs como el vmware y otros.

EDIT: A me olvidaba tengo otro problema es que conecte un disco duro en mi pc pero me toma todos los archivos como de solo lectura y no me deja cambiar los permisos...que hago?

---

### Post by spg76 on 2007-05-26
> **Shot said:**
> A me olvidaba tengo otro problema es que conecte un disco duro en mi pc pero me toma todos los archivos como de solo lectura y no me deja cambiar los permisos...que hago?

¿El sistema de archivos del disco es NTFS? Si es así, es probable que está montado como solo lectura y necesitas instalar el driver para leer y escribir en una partición NTFS.

---

### Post by Shot on 2007-05-26
Ok gracias ya los estoy descargando

---

