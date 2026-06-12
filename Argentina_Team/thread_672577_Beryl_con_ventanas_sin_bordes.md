---
title: "Beryl con ventanas sin bordes"
date: 2008-01-19
forum: Argentina Team
---

### Post by aregnando on 2008-01-19
Hola a todos, en principio tengo instalado Kubuntu 7.10, está corriendo correctamente la aceleración de video de mi placa nvidia gforce fx 5200 ya que al instalar Beryl me funciona el cubo y efectos de lluvia por ejemplo, pero tengo el problema de que no aparecen los bordes de las ventanas.
Estuve viendo infinidad de posts en los cuales sugieren editar el xorg.conf, (cosa que no se como hacer) y agregarle a device la linea Option “AddARGBGLXVisuals” “True”, vuelvo a hacer el comentario ya que es algo que desconozco, no se abrir el xorg.conf en la consola, probé varias formas pero ninguna me resultó.
Voy a agradecer cualquier ayuda ya que me encantaría tener funcionando Beryl en mi escritorio.
Gracias.

---

### Post by Darth Trix on 2008-01-19
Proba primero bajandote Emerald que es el manejador de estilos de Beryl, el decorador de ventanas estandar de KDE no funciona con Beryl

---

### Post by aregnando on 2008-01-20
Hola Darth trix, traté de instalar Emerald con adept pero me sale en rojo (ROMPER instalar) y por supuesto no me descarga los paquetes. Como dato te cuento que tengo seteado como fuente de los repositorios el servidor principal y no el de Argentina por lo que supuse que no debía ser ese el problema.

---

### Post by sajnox on 2008-01-21
Para editar el xor desde la consola en Kubuntu tenes que tipear lo siguientes

```
$ sudo kate /etc/X11/xorg.conf
```

Si desaparecen los bordes de las ventanas, proba tipeando en una consola

[HTML]compiz --replace[/HTML]

---

### Post by Darth Trix on 2008-01-22
Si no podes instalar Emerald, proba instalando el paquete compiz-kde, que es un decorador de ventanas para KDE que también funciona con Compiz.
Si o si necesitas otro decorador de ventanas por que el que viene con KDE no anda con Compiz

---

### Post by aregnando on 2008-01-25
Gracias Sajnox por el dato, ya me estaba frustrando de no poder entrar al xorg, aparentemente en este está todo Ok, está funcionando la aceleración de video y figuran los parámetros que había leido en los posts que cité anteriormente.
Igual sigo sin poder hacer funcionar beryl con la complicación de que lo desinstalé y al instalarlo nuevamente ya no me funciona el manejador de ventanas de beryl y salta automáticamente al que usa KDE por defecto.
Traté de instalar Emerald y fué imposible, traté también con Heliodor y lo mismo, Estoy empezando a desistir de la utilización de este manejador de ventanas que tanto me hubiera gustado tener.
Gracias a todos por sus consejos.

---

### Post by guisheca on 2008-01-29
Y porqué queres usar beryl si ubuntu 7.10 ya trae por defecto compiz-fusión? que es mucho mejor y mas estable que beryl.

---

### Post by aregnando on 2008-01-30
Muy buena tu pregunta Guisheca, en el momento en que posteé eso estaba usando Kubuntu 7.10, el cual me gusta mucho pero decidí probar Ubuntu y la verdad es que me resultó más sencillo actualizarlo, cosa que Kubuntu había tenido algunos problemas tal como lo expresé en otro post.

Saludos.

---

