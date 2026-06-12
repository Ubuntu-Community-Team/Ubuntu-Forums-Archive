---
title: "[SOLVED] Recien quise ir a imprimir y NO TENGO IMPRESORA? o.O"
date: 2007-11-19
forum: Argentina Team
---

### Post by MeduZa on 2007-11-19
Es simple, instale la impresora despues de instalar el gutsy, imprime la pagina de prueva 100 puntos, estuve usando la impresora por red desde otro puesto, hoy, quiero imprimir en esta pc y NO LA TENGO EN LA LISTA DE IMPRESORAS o.O, me voy a la otra pc y ANDA de 10 o.O
¿porque no veo las impresoras locales desde ningun programa y desde la red andan de 10?

raro :confused:

---

### Post by xpelaox on 2007-11-19
hmmm probaste reiniciando? 
sino en sistema---->Administracion--->Impresoras  ????

.... la impresora esta conectada directo a la compu con ubuntu, no?

---

### Post by MeduZa on 2007-11-20
> **xpelaox said:**
> hmmm probaste reiniciando? 
sino en sistema---->Administracion--->Impresoras  ????

.... la impresora esta conectada directo a la compu con ubuntu, no?

no tiene nada que ver reiniciar o no, es algo que cambiaron, agregaron algo que proteje pero no entiendo que.

La impresora andaba perfecta en 6.04 --> 6.10 --> 7.04, pero en 7.10 anda perfecta desde otro lado que no sea localhost (desde otras pc puedo imprimir a esta pc que es server de cups), estoy leyendo y parece ser problema de permisos a cups para 172.0.0.1, pero no se como repararlo, alguno q sepa? :confused:

por ahora me arreglo mandandole emails a mi esposa y gritandole IMPRIMI ESO pero me gustaria poder imprimir en mi pc :(

gracias gente

---

### Post by MeduZa on 2007-12-13
alguno sabe como le cambio los permisos a cups?

---

### Post by pante on 2007-12-13
> **MeduZa said:**
> alguno sabe como le cambio los permisos a cups?
No sé si te entendí bien, pero en Xubuntu 6.06 tuve un problema parecido y resolví el problema según lo que dicen aquí: [http://ubuntuforums.org/showthread.php?t=304320](http://ubuntuforums.org/showthread.php?t=304320) 

Con  Xubuntu 7.04 el problema no se me presentó así que no sabría decirte. :(

Buena suerte

---

### Post by margori on 2007-12-13
Yo tuve problemas con mi impresora al actualizar a Gutsy. Lo solucione usando esta linea:

sudo aa-complain cupsd

La informacion la obtuve de [http://www.ubuntu-es.org/index.php?q=node/66537]("http://www.ubuntu-es.org/index.php?q=node/66537")

Fijate si te sirve.

---

### Post by MeduZa on 2008-01-09
Bueno, con este mensaje posteo la solucion que al parecer era una ***** y que recien hoy me puse a encontrarla, ya que me parecia raro que solo mi esposa pudiera imprimir desde la red y ni yo ni el root pudieran hacerlo en local!

el problema era en set alowed users en las settings de la impresora solo esta puesto el user de mi esposa y ninguno mas, agregue los 2 que faltaban (yo y el root) mando a imprimir una imagen de prueba y ya anda :(

tremenda pabada era, lo raro es que nadie se haya abivado de decirme!

---

### Post by margori on 2008-01-10
Serena morena, que acá nos tratamos bien.

Si la solución era una pavada, como es que no fuiste tan vivo de darle los permisos a los usuarios antes de hacer un post por tu falta de viveza?

Esta es una comunidad que hace las cosas de onda, no son todos expertos ni tienen todas las respuestas, y mucho menos la obligación de brindarlas.

---

### Post by MeduZa on 2008-04-13
> **margori said:**
> Serena morena, que acá nos tratamos bien.

nadie trato mal a nadie, baja un cambio.
> **margori said:**
> 
Si la solución era una pavada, como es que no fuiste tan vivo de darle los permisos a los usuarios antes de hacer un post por tu falta de viveza?

¿y que hice? empece a buscar la solucion y la encontre, como te dije antes andaba, y dejo de andar en el cambio, no me imagine hasta despues de probar varias cosas, que se habia borrado o cambiado el modo de dar permisos. Ademas agarre para el lado de los tomates, por el lado de appguard o como sea.

> **margori said:**
> 
Esta es una comunidad que hace las cosas de onda, no son todos expertos ni tienen todas las respuestas, y mucho menos la obligación de brindarlas.
Este post lo hice solo con dos intenciones, 1 resolver mi problema, 2 ayudar a los que puedan tener el mismo problema como todos mis post, incluiso respondo MPs muy seguido.

No obligue a nadie, pero es que todos parecen mas  capacitados que yo en linux, yo soy relativamente un noob en esto y solo por eso lo decia.

Saludos y solo queria dejar este thread a modo de ayuda para los demas.

---

