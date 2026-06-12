---
title: "Papelera en XFCE"
date: 2006-12-24
forum: Argentina Team
---

### Post by lavaramano on 2006-12-24
Bueno, los que habran usado / usan xfce saben que hasta *ahora* no hay papelera en el xfce, lo cual puede llegar a ser un problema porque quizas se borra el archivo erroneo y puede llegar a ser un grave problema.

por lo que lei, en los proximos releases ya va a haber papelera, pero por el momento esto se puede solucionar de esta forma:

```


1) Crear un script que va a ser el que envie archivos a la "papelera" 

sudo mousepad /usr/bin/del

y dentro de ese archivo ponemos esto:

#!/bin/bash
mv -vi "$@" $HOME/.Trash


```

listo. la proxima vez cuando borremos algo en lugar de poner 'rm archivo', ponemos 'del archivo' y listo.

para hacer que esto tambien funcione con el thunar hay que hacer lo siguiente:

```

Ir a **Editar > Configurar Acciones Personalizadas**
Una vez ahi, agregamos una nueva accion. 

En la solapa "Basico", debemos poner los siguientes datos:

Nombre: Mover a la papelera.
Descripcion: Mueve archivos a la papelera.
Orden: del %F 

(nota: el %F es la ruta completa al archivo, por ej: si "archivo" estaba en /home/USUARIO. Entonces, %F = /home/USUARIO/archivo)

Icono: *el que mas te guste*

Ahora en la solapa "Condiciones de Aparicion" hay que poner estos datos:

Patron de archivo: *
Aparece si la seleccion contiene: -tildamos todas las opciones- 


```

y listo. ahi tenemos un simpatico "emulador de papelera" en XFCE. (o xubuntu, en este caso).

y por ultimo, los que se acostumbraron al icono de la papelera en algun panel (como yo :mrgreen:) hacen lo siguiente:

 ```

Click con el boton derecho sobre algun panel y elijen la opcion "Añadir un nuevo elemento al panel"

Ahi, elegimos un "Lanzador".
En nombre ponemos el nombre que mas nos guste como por ejemplo: "Papelera"
En Descripcion: idem.
En Icono: el que mas nos guste.
En Comando: thunar /home/USUARIO/.Trash

``` 

fuentes:
[http://xubuntu.wordpress.com/2006/07/20/howto-terminal-tips-and-tricks/](http://xubuntu.wordpress.com/2006/07/20/howto-terminal-tips-and-tricks/)
[http://xubuntu.wordpress.com/2006/07/28/howto-terminal-tips-and-tricks-part-2/](http://xubuntu.wordpress.com/2006/07/28/howto-terminal-tips-and-tricks-part-2/)

yo solamente lo traduje y agregue lo del link a la papelera :KS 


saludos

---

### Post by beuno on 2006-12-24
Yo hago toda una vuelta para evitar la papelera y ustedes hacen toda una vuelta para tenerla.
Que jodido que es hace un Sistema Operativo...

---

### Post by lavaramano on 2006-12-24
> **beuno said:**
> Yo hago toda una vuelta para evitar la papelera y ustedes hacen toda una vuelta para tenerla.
Que jodido que es hace un Sistema Operativo...

y bueno, es la magia del gnu linux, hay para todos los gustos (?)

---

### Post by BlackHero on 2006-12-25
cuack yo tengo alta papelera y uso xubuntu con xfce4 rc1 :s WTF men look this =) y viene por defecto en la instalacion =)

---

### Post by lavaramano on 2006-12-25
si, lo sabia eso.
pero no es lo mismo que esta en los tutoriales?

---

### Post by BlackHero on 2006-12-25
no no es lo mismo=) por que lo que dicen tus tutoriales es que no existe un lugar llamado trash osea tmp :P la cosa es que no es lo mismo por que lo que esta diciendo el tuto ese es que no existe el trash y ahi lo creas y creo que si haces eso en xfce te va a dar problemas estuve biendo y dije na talves esto no sea para xubuntu talves pueda ser para otra distro pero na zenwalk fedora core etc etc etc todas las que usan xfce lo traen talves ese tuto era para las primeras versiones de xfce pero bue igual hoy en dia es innecesario =) saludos a las primas =)je

---

### Post by lavaramano on 2006-12-26
por ejemplo en gnome, la carpeta trash esta en ~/.Trash y uso la misma carpeta para xfce, asi que al fin y al cabo sigue siendo lo mismo. (en un cierto punto)
aunque en realidad deberia actualizar a la nueva version de xfce  y dejarme de joder :mrgreen:

---

