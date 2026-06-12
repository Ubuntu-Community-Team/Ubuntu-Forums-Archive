---
title: "Texto desalineado en panel laterial de nautilus"
date: 2008-05-09
forum: Argentina Team
---

### Post by valucha on 2008-05-09
[COLOR="DarkOrchid"]Hola, ahora volví con un problema que es más un "me quiero matar para que anduve tocando"... aunque después diga "bueh tan mal no me fue, ahora sé qué es esto"...

En fin, mañana rindo un parcial de álgebra, por el cual estoy remil nerviosa (y que tiene que ver?), y para desconcentrarme me puse a personalizar ubuntu (ahhh...)

La cuestión es que tratando de mejorar el sidebar panel cuando se elije la opción "información" se me ocurrió tocar el gconf-editor...

Hice lo siguiente:
EN nautilus -> preferences cambié:

sidebar_width a 0 

Obviamentecuando abrí el nautilus la barrita estaba completamente cerrada a la izquierda... la estiré y la abri y ahi noté que después de esto el texto quedó desalineado...

empecé a ver que mas podría haber tocado en el gconf-editor, y nada funcionaba...

Busquéen internet, y no hay nada, nisiquiera el reporte de un bug :( nada...

Queria saber si me pueden ayudar de alguna forma, cómo tengo que proceder o si me pueden pasar ua copia de su gconf-editor en esa parte...

MIl gracias :) 

dejo screenshot para que vean de que hablo

saludos
[/COLOR]

---

### Post by Mauro22 on 2008-05-09
Yo en sidebar_width tengo 193.

Lo que no aclaraste es si volviste a poner lo que tenias antes de cambiarlo a 0.



PD: Como se llama el theme?

---

### Post by valucha on 2008-05-10
[COLOR="DarkOrchid"]Cuando resizie la barra para poder verla y luego volví al gedit, vi que el valor había vuelto a la normalidad.[/COLOR]

---

### Post by Mauro22 on 2008-05-10
Entonces ya lo arrglaste?

---

### Post by valucha on 2008-05-10
[COLOR="DarkOrchid"]Nop, lo que volvió a la normalidad es el valor y la barrita, osea por más que mueva la barrita que me deja elegir el tamaño de ese panel, el texto está desalineado :(
[/COLOR]

---

### Post by Mauro22 on 2008-05-10
Al parecer es un bug ya reportado:

> 
When using nautilus in browser mode with the "Information" sidebar open, the current folder's icon displays in the middle, with information about it centered underneath in the default configuration. When a background image or color is added, the text underneath the icon shifts to the right, with the folder title a bit to the left of the details underneath, none of it centered together. If the text doesn't shift immediately after it's applied, restarting Nautilus will show the problem.


 To correct, right-click on the panel and click "Use default background", and restart nautilus.  The text centers once again.

Te lo traduzco por si no cazaste ni una:


> 
Cuando se usa nautilus con la barra de costado en "Informacion", el icono de la carpeta esta en el medio con la informacion centrada debajo. Cuando una imagen de fondo o color es agregado, el texto debajo del icono se corre a la derecha [...]

 

Para corregirlo:
Clic derecho en el panel del costado y elegir "Usar fondo por defecto", reiniciar nautilus.

  Eso centrará el texto otra vez.

 


:guitar:

---

### Post by valucha on 2008-05-10
[COLOR="DarkOrchid"]Ufa... me gustaba como me había quedado...

:(

No encontré ese bug, y eso que busqué


Muchisisisismas gracias, y SOLVED[/COLOR]

---

