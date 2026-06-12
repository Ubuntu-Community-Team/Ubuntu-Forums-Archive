---
title: "Quien me da una mano con K3b y Amarok"
date: 2008-05-08
forum: Argentina Team
---

### Post by Mauro22 on 2008-05-08
Buenas!!

He aqui un problema que con google no he podido dar.



Uso Gnome en Hardy pero mis dos aplicaciones favoritas de KDE:

* Amarok
* K3b


El problema es que amarok al iniciar me da un error:

"cannot talk to klauncher"

y k3b solo a veces.

Ahora, ejecutandolos con sudo, no tira ese error.


Alguien ??





Saludos! y mil gracias!


**A los moderadores/admins: DONDE ESTA LA OPCION DE MARK AS SOLVED ????**

---

### Post by lesergi on 2008-05-08
Hola!!

Por lo que parece es problema de configuración, ya que en usuario normal te lo hace y en root no.

Si no tienes problema en perder la configuración KDE, lo que puedes hacer es limpiar la configuración.

Para esto puedes hacer:

```
mv ~/.kde ~/.kde.bak
```

Asegurate de hacer esto mientras tienes las aplicaciones KDE cerradas.

Saludos.

---

### Post by guillermolisi on 2008-05-08
Tambien podria ser una cuestion de archivos con permisos inadecuados, por eso funciona cuando usas root o sus privilegios.

---

### Post by Mauro22 on 2008-05-08
Hice lo de de .kde y no, sigue dando el error.


Segun lei hay un archivo ICEauthoroty o algo asi que hay que darle permisos. Le di todos (a+rwx) y nada. Sigue el cartelito.


Gracias de antemano.

---

### Post by guillermolisi on 2008-05-08
Mauro

Encontre algo, te diria que casi al toque y sin revolver mucho, pero esta en Ingles.

[http://ubuntuforums.org/showthread.php?t=251325](http://ubuntuforums.org/showthread.php?t=251325)

Parece que el problema que tenes tiene que ver con algun ruido que se genera cuando combinas aplicaciones de un entorno grafico en otro distinto.

En el thread del link que te paso justamente hablan de tener problemas con Amarok y K3b.

Si queres mas info, pone "cannot talk to klauncher" en Google y salen mas cosas.

---

### Post by clasificado on 2008-05-08
También pasa mucho con kde4: La mezcla entre kde3 y kde4 causa problemas con klauncher, y tira ese error.

nada grave eh

clasificado

---

### Post by lesergi on 2008-05-09
Para cuándo un estándar freedesktop!!?? :lolflag:

---

### Post by clasificado on 2008-05-09
> Para cuándo un estándar freedesktop!!?? 
Lo van a hacer junto con el ñoco gráfico para conectarse por pppoe :D

---

### Post by lesergi on 2008-05-09
No lo pillo... No está el Kpppoe? :oops:

---

### Post by Mauro22 on 2008-05-09
> **guillermolisi said:**
> Mauro

Encontre algo, te diria que casi al toque y sin revolver mucho, pero esta en Ingles.

[http://ubuntuforums.org/showthread.php?t=251325](http://ubuntuforums.org/showthread.php?t=251325)




Gracias por el link. 


Al parecer me faltaban dos cosas.

Iniciar un demonio llamado **kdeinit**
Instalar desde synaptic [B]kdevelop

[/B]
Hasta ahora 0 problemas![B]

Gracias!!



PD: La opcion 'Mark as Solved' la sacaron o la corrieron de lugar ???
[/B]

---

### Post by guillermolisi on 2008-05-09
El otro dia me recorri todo el site del foro, hasta los lugares que uno mira y dice "nah, aqui seguro que no va a estar, nada que ver con lo que busco" y tal cual, tampoco la encontre.

Habra que editar el subject y ponerle la etiqueta a mano o .... no sera que ahora se maneja con los tags, agregandole un tag de Resolved ?

PS: Me alegro que haya servido lo que te mande, Mauro.

---

