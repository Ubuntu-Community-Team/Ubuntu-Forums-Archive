---
title: "Desde que puse Conky escritorio se comporta raro!"
date: 2008-05-13
forum: Argentina Team
---

### Post by smrdelj on 2008-05-13
Hola q tal. Tengo un problemita: desde que uso conky que todo icono que tengo sobre el escritorio no se ve. O sea, desaparece, y la unica forma de verlo es pasarle por arriba con el puntero...Y no solo sucede con los iconos, sino q tamb me desaparece el "cuadrado naranja" de seleccion que se forma al mantener apretado el click izq y arrastrar. Digamos que, todo en mi escritorio, tiene cierto efecto "intermitente"

Alguien sabe qué onda?

Muchas gracias, saludos.

---

### Post by _kAz_ on 2008-05-14
A mi me paso hoy luego de la ultima actualizacion de AWN (bzr). Los iconos se cambiaban, se daban vuelta, y cuando queria hacer el efecto de rotación (al pasar sobre el icono) parecía cuando la tele no sintoniza que hace un monton de rayas.

---

### Post by smrdelj on 2008-05-14
A mi lo unico raro q me pasa con la AWN es que cuando inicio el sistema, los iconos me aparecen sobre el margen izq superior, y luego aparecen en el marco iza inferior y empiezan a acomodarse lentamente hasta posicionarse en la barra (q siempre está donde tiene q estar). O sea, los iconos defilan lentamente en linea por el margen inferior de la pantalla hasta acomodarse. No aparece todo de una.

Vos decis q esto q me pasa debe ser error de AWN y no de conky? La verdad me suena raro, porq justamente comencé a percibirlo a partir de q instalé conky, no la barra. Quiza, a lo sumo, sea una "incompatibilidad" entre ambos; pero me suena q no es solo culpa de la awn. Conky tiene seguro algo q ver

---

### Post by Thalskarth on 2008-05-14
> **smrdelj said:**
> Hola q tal. Tengo un problemita: desde que uso conky que todo icono que tengo sobre el escritorio no se ve. O sea, desaparece, y la unica forma de verlo es pasarle por arriba con el puntero...Y no solo sucede con los iconos, sino q tamb me desaparece el "cuadrado naranja" de seleccion que se forma al mantener apretado el click izq y arrastrar. Digamos que, todo en mi escritorio, tiene cierto efecto "intermitente"

Alguien sabe qué onda?

Muchas gracias, saludos.

A mi me pasaba lo mismo, nunca supe el poque ocurre.

Pero se soluciona, llendo al archivo de configuración de Conky (.conkyrc)

Y le seteas que use su propia ventana (por defecto no la usa), al estilo le pones overdrive (asi no tiene bordes ni nada) y el fondo transparente asi se ve lo que halla detras (wallpaper).

El codigo seria:
```
own_window yes
own_window_type override
own_window_transparent yes
```

Fijate tu conkyrc, si tiene esas opciones, cambialas por lo que dice aqui, si no las tiene... agregalas.

Con eso, ami me anda perfecto.

De paso, como dije no se poque ocurre... solo se que asi pude solucionarlo (y me costo :P)... si alguno sabe algo mas o el porque de esto, estaré encantado con una explicacion :)

---

### Post by Aspergillus on 2008-05-14
segun tengo entendido sucede por que conky y nautilus no se llevan bien...o sea no son compatibles

---

### Post by Air23 on 2008-05-14
> **_kAz_ said:**
> A mi me paso hoy luego de la ultima actualizacion de AWN (bzr). Los iconos se cambiaban, se daban vuelta, y cuando queria hacer el efecto de rotación (al pasar sobre el icono) parecía cuando la tele no sintoniza que hace un monton de rayas.

> **smrdelj said:**
> A mi lo unico raro q me pasa con la AWN es que cuando inicio el sistema, los iconos me aparecen sobre el margen izq superior, y luego aparecen en el marco iza inferior y empiezan a acomodarse lentamente hasta posicionarse en la barra (q siempre está donde tiene q estar). O sea, los iconos defilan lentamente en linea por el margen inferior de la pantalla hasta acomodarse. No aparece todo de una.

Vos decis q esto q me pasa debe ser error de AWN y no de conky? La verdad me suena raro, porq justamente comencé a percibirlo a partir de q instalé conky, no la barra. Quiza, a lo sumo, sea una "incompatibilidad" entre ambos; pero me suena q no es solo culpa de la awn. Conky tiene seguro algo q ver

A mi me pasan las dos cosas
Al ir a la configuracion de AVN y hacer que giren los iconos o cambiar el valor de icons offset en apariencia de la barra, se ve como una tv no sintonizada, desaparecen iconos o cambian por otros.
Tambien me pasa que aparece por la izquierda y se mueve lentamente hacia el centro

Tengo la ultima AVN (la de los repos de launchpad) y conky (pero matando AVN y conky y luego ejecutando AVN de nuevo se comporta igual)

---

### Post by _kAz_ on 2008-05-14
> **Air23 said:**
> A mi me pasan las dos cosas
Al ir a la configuracion de AVN y hacer que giren los iconos o cambiar el valor de icons offset en apariencia de la barra, se ve como una tv no sintonizada, desaparecen iconos o cambian por otros.
Tambien me pasa que aparece por la izquierda y se mueve lentamente hacia el centro

Tengo la ultima AVN (la de los repos de launchpad) y conky (pero matando AVN y conky y luego ejecutando AVN de nuevo se comporta igual)

El asunto es que no tengo Conky (quiero tener pero no se bien como instalarlo, poner el theme que concuerda con mi desk -Brit-, y que me muestre algunos datos que no salen como default -clima y otras yerbas-; tengo que ponerme todavía).

El inconveniente que tenía con AWN ayer (que se cambiaban los iconos o se veían como distorsión cuando giraban) no sucede hoy. Pienso que posiblemente la causa sea que tenía muchas ventanas abiertas en ese momento, por lo tanto varios iconos se achicaban automáticamente y quizás ahí se armaba bolonqui.

---

### Post by smrdelj on 2008-05-14
> **Thalskarth said:**
> A mi me pasaba lo mismo, nunca supe el poque ocurre.

Pero se soluciona, llendo al archivo de configuración de Conky (.conkyrc)

Y le seteas que use su propia ventana (por defecto no la usa), al estilo le pones overdrive (asi no tiene bordes ni nada) y el fondo transparente asi se ve lo que halla detras (wallpaper).

El codigo seria:
```
own_window yes
own_window_type override
own_window_transparent yes
```

Fijate tu conkyrc, si tiene esas opciones, cambialas por lo que dice aqui, si no las tiene... agregalas.

Con eso, ami me anda perfecto.

De paso, como dije no se poque ocurre... solo se que asi pude solucionarlo (y me costo :P)... si alguno sabe algo mas o el porque de esto, estaré encantado con una explicacion :)

Hola que tal! Mirá, tenes razón, poniendo esos comandos se soluciona el asunto; pero aparece otro problema: conky queda siempre en primer plano. O sea que, si tengo algo maximizado (por ejemplo el firefox), conky se superpone y me **** el angulo superior izq del navegador (donde tengo conky colocado). Cómo soluciono esto? O sea, seria asignarle al conky q esté siempre below o en segundo plano.

Muchas gracias! Saludos

---

### Post by vk-cdg on 2008-05-14
A mi me pasa lo mismo con la AWN y no tengo Conky. Por lo que estuve leyendo, eso ocurre cuando carga la AWN y compiz al mismo tiempo. Yo lo que hice fue crear un script que lanza a la AWN luego de un delay X, pero se ve que lo setié en un valor bajo porque me sigue pasando lo mismo.

---

### Post by Air23 on 2008-05-14
> **_kAz_ said:**
> El asunto es que no tengo Conky (quiero tener pero no se bien como instalarlo, poner el theme que concuerda con mi desk -Brit-, y que me muestre algunos datos que no salen como default -clima y otras yerbas-; tengo que ponerme todavía)

La instalacion de conky es tan sencilla como escribir esto en una terminal:
```
sudo apt-get install conky
```
Aca tenes un conky de Elegant Brit: [http://gnome-look.org/content/show.php/Elegant+Brit+Conky?content=76383](http://gnome-look.org/content/show.php/Elegant+Brit+Conky?content=76383) 
Si no es exactamente lo que buscas, en [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865) tenes muchisimos conkys que te pueden servir 
Luego desde la terminal:
```
sudo gedit ~/.conkyrc
```
Se debe abrir un documento en el cual debes pegar el conkyrc que te gusta, guardas y cerras.
Finalmente desde una terminal ejecutas: conky y listo
Si queres que conky se inicie con tu ubuntu, anda a sistema>preferencias>sesiones y añadi Conky (vas a añadir y en la ventana que se abre pone como orden: conky)

---

### Post by smrdelj on 2008-05-15
Ya solucioné el problema que mencionaba en mi ultimo post. Al final, el archivo tiene que contener esto:
```

own_window yes
own_window_type normal
own_window_transparent yes
```

Saludos, muchas gracias

---

### Post by Thalskarth on 2008-05-15
> **smrdelj said:**
> Ya solucioné el problema que mencionaba en mi ultimo post. Al final, el archivo tiene que contener esto:
```

own_window yes
own_window_type normal
own_window_transparent yes
```

Saludos, muchas gracias

Que raro... yo lo tengo tal como te habia dicho... y no me pasa nunca eso de que el conky quede siempre encima de todo...

Será que alguna otra opcion, hiso que nos afecte distinto?

---

