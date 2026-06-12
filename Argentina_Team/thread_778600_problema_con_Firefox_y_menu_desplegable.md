---
title: "problema con Firefox y menu desplegable"
date: 2008-05-02
forum: Argentina Team
---

### Post by .NicK_LoVe on 2008-05-02
Hola gente!!! hace ya rato que tengo este problema con firefox, pense primero que era solo de la version 64, asi q aproveche con la salida de hardy para pasarme a 32 y sigue pasando lo mismo.
El tema es que los menues se meten debajo de las fotos y no los puedo ver.
Alguien me puede ayudar???
Saludos

---

### Post by Vermind on 2008-05-02
Hola,
si hablas de los menus Flash, como en nvidia.com, es un bug con Adobe Flash. Hablamos de quels menus?

( Lo siento, mi español no es perfecto...)

---

### Post by .NicK_LoVe on 2008-05-02
Si, a eso me refiero. Como se soluciona? con gnash?

---

### Post by Vermind on 2008-05-02
hola,
no se un solucion por eso.
Pero puedes utilizar le addon que se llama Adblock por Firefox, por bloquer les images que aparecen delante del menu.

---

### Post by .NicK_LoVe on 2008-05-04
Si, pero el tema es que los menus se meten detras de las imagenes de la pagina, prove una distro de fedora y esto no pasa.

---

### Post by clasificado on 2008-05-05
> **.NicK_LoVe said:**
> prove una distro de fedora y esto no pasa.

Entonces hablamos de dos problemas diferentes. veamos esto: 
[http://addsomespark.com/overunder/](http://addsomespark.com/overunder/)

En linux se destruye completamente, porque el plugin de flash para linux no soporta wmode="transparent", utilizado para que el background del flash se fusione con el html.

Este mismo wmode="transparent" se utiliza en los windows para permitir que el código html pueda ser dibujado sobre el flash.

**al no soportar wmode, ninguno de los dos efecto pueden lograrse en el plugin de flash de adobe para linux.**

te invito a probar esa página en tu distribución actual, y despues probarla en la distro de Fedora. 

Si se encuentra** alguna combinación que haga funcionar el wmode** sin la ayuda de adobe (que no parece tener ganas de ayudar) seria un gran avance para la comunidad linux 

[I](en realidad no, ya que todo el esfuerzo sobre el plugin de flash es tirado a la basura al ser pripietario, pero bue, eso es de otro pajonal)
[/I]
clasificado

---

### Post by .NicK_LoVe on 2008-05-06
Ok, entonces vamos a investigar un poco, gracias por la respuesta!!

---

### Post by .NicK_LoVe on 2008-05-06
Lo único que no me cierra de esto es, si soy el único salame con este problema o es que a nadie le importa??
Porque no encontre info por ningun lado.

---

### Post by clasificado on 2008-05-07
> **.NicK_LoVe said:**
> si soy el único salame con este problema o es que a nadie le importa??

Entre los que usan linux hace varios años, es un problma tan viejo que ya es aburrido quejarse.

Por ejemplo, fijate en el [post del lanzamiento formal de flash 9 para linux (del blog de adobe)]("http://blogs.adobe.com/penguin.swf/2007/01/flash_player_9_for_linux_x86.html") que en los millares de mensajes de agradecimiento se pregunta varias veces sobre este bug.

Sin embargo, ahora que lo mencionas, no sé porqué no aparece repetidas veces en los foros de principiantes :-k

Será que los programadores web usan lo suficientemente poco esta combinación de explosivos como para que se note

clasificado

---

