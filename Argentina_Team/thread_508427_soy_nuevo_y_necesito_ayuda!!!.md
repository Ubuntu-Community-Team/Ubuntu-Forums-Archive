---
title: "soy nuevo y necesito ayuda!!!"
date: 2007-07-24
forum: Argentina Team
---

### Post by marcesneibrun on 2007-07-24
hola  soy nuevo en ubuntu, tengo instalado el ubuntu 7.04, acabo de instalar el programa beryl manager desde añadir y quitar aplicaciones, lo instaló, hicé clic en beryl manager y me apareció un cubo rojo que podía deslizarlo por toda la pantalla, desapareciendo todo lo demás, lugo presione ctrl alt f1, y apareció una pantalla toda negra pidiendome el nombre de usuario y contraseña, lo puse pero no sé como volver a la pantalla de escritorio de Gnome.Disculpen mi ignorancia pero soy muy nuevo; otra cosa no instale ningun driver puede ser por eso tb??
Gracias por la ayuda, por favor si me pueden indicar como volver al escritorio de Gnome se los agradezco.
Marcelo

---

### Post by rojojuan on 2007-07-24
Probá habilitando 4 escritorios.

---

### Post by marcesneibrun on 2007-07-24
podrías guiarme por favor para habilitarlos 
Muchas gracias
Marcelo

---

### Post by faktorqm on 2007-07-24
Hola, no se bien que queres hacer pero espero poderte ayudar.

con CTRL + ALT + F1 vas a un terminal. 

el entorno grafico esta en F7, o sea que para volver tenes ke apretar
CTRL + ALT + F7

Si algo no te funciona y no sabes como cerrarlo, yo uso el metodo mas cavernicola, voy a la lista de procesos y lo cierro.

desde una terminal, escribi:

```
ps ax
```

ahi te tira una lista con todos los procesos que tenes corriendo en la pc con un PID que es el numero de cada proceso. Despues, buscas en la lista el que queres cerrar. (si la lista te queda corta, te podes mover por la consola DE A MEDIA PANTALLA usando SHIFT + RE PAG ó SHIFT + AV PAG, otra opcion es: "ps ax | more" sin comillas).

Cuando tenes el numero que queres, escribis 

```
kill numero_de_proceso
```

y te volves a fijar con ps ax si esta, si no esta, CTRL + ALT + F7 y te fijas, si anda, josha, sino, CTRL + aLT + F1, ps ax, y haces:

```
kill -9 numero_de_proceso
```

OJO! NO uses -9 a menos ke no lo cierre "por las buenas". 

Espero haberte sido de ayuda. cualkier kosa pregunta. salu2!

---

### Post by rojojuan on 2007-07-26
> **marcesneibrun said:**
> podrías guiarme por favor para habilitarlos 
Muchas gracias
Marcelo

Para habilitar escritorios haces click en el panel inferior, al lado de la papelera (es el cuadrado oluminado) con botón derecho y allí indic&#347; cuantos escritos querés. Es muy fácil.

---

