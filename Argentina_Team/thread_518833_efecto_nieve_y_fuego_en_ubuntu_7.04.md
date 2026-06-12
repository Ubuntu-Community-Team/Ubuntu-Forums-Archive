---
title: "efecto nieve y fuego en ubuntu 7.04"
date: 2007-08-06
forum: Argentina Team
---

### Post by aceki on 2007-08-06
Gente como hago para activar esos efectos, yo tengo el ubuntu 7.04 base, con el cubo y con los efectos de ventas.

---

### Post by zspikes on 2007-08-06
q cubo? compiz y beryl?
Cual efecto de fuego? el de quemar ventanas? o el de escritura con fuego?

Es todo cuestion de tocar la configuracion del cubo, dependiendo de que cubo tengas, es donde tenes q tocar.

---

### Post by aceki on 2007-08-06
Mira el cubo es el que viene con la instalacion basica de ubuntu 7.04

---

### Post by sdm_cacto on 2007-08-06
No podes con lo q viene instalado, tenes q instalar los plugins de compiz, o instalar beryl, o instalar compiz-fusion (con sus respectivos plugins).

si queres saber como googlea, hay bocha de guias.

y la proxima pone mas info igual... o pone Hola por favor, o gracias, o saludos, etc..., t conteste porq hoy estoy reeee buena onda

---

### Post by aceki on 2007-08-06
sdm_cacto, gracias por la info.

---

### Post by zspikes on 2007-08-06
> **sdm_cacto said:**
> No podes con lo q viene instalado, tenes q instalar los plugins de compiz, o instalar beryl, o instalar compiz-fusion (con sus respectivos plugins).

si queres saber como googlea, hay bocha de guias.

y la proxima pone mas info igual... o pone Hola por favor, o gracias, o saludos, etc..., t conteste porq hoy estoy reeee buena onda

jaja, tranquilo compadre por favor!!! :P

me parece q tenemos q poner un bot en el foro, q cuando lea "principiante con problemas" o ese tipo de titulos responda automaticamente "googlea" XD jaja

---

### Post by marianom on 2007-08-06
> **zspikes said:**
> me parece q tenemos q poner un bot en el foro, q cuando lea "principiante con problemas" o ese tipo de titulos responda automaticamente "googlea" XD jaja


Sección II de las reglas del foro, por favor relean todos si son tan amables.

Como resumen:
1- En este foro están permitidas todas las preguntas (incluso las más simples), aquellos que consideren que la pregunta no debe ser ni siquiera hecha, tienen la opción de ignorarla.
2- No está permitido que como única respuesta se envíe al usuario al buscador. Los posts que así lo hagan serán editados.

Con respecto a los dichos de smd_cacto no creo que rompan las reglas ya que le sugiere la solución y solo le indica que con google encontrará las guías necesarias para lograrlo (hay formas más felices de hacerlo pero bueno, es lunes y en MDQ debe hacer frío).

---

### Post by sdm_cacto on 2007-08-06
> **marianom said:**
> Sección II de las reglas del foro, por favor relean todos si son tan amables.

Como resumen:
1- En este foro están permitidas todas las preguntas (incluso las más simples), aquellos que consideren que la pregunta no debe ser ni siquiera hecha, tienen la opción de ignorarla.
2- No está permitido que como única respuesta se envíe al usuario al buscador. Los posts que así lo hagan serán editados.

Con respecto a los dichos de smd_cacto no creo que rompan las reglas ya que le sugiere la solución y solo le indica que con google encontrará las guías necesarias para lograrlo (hay formas más felices de hacerlo pero bueno, es lunes y en MDQ debe hacer frío).

jjaja sorry, ese soy yo cuando paso mucho tiempo sin dormir, igual no fui taaan rudo.

---

### Post by aceki on 2007-08-07
sdm_cacto yo te iva a mandar al demonio, pero dije "por ahi durmio mal" me imagine bien!!! te cuento, hise andar los efectos de agua con ubuntu 7.04 sin instalar nda. Ahora falta los de fuego. :lolflag:

---

### Post by undiaperfecto on 2007-08-09
yo nunca pude activar el efecto de nieve en beryl, no se si hay que instalar algun plugin o sera que no encuentro la opcion correcta

---

### Post by jpmorelli on 2007-08-11
Para el efecto de nieve hacé lo siguiente:
El beryl que tenés que tener cargado es uno más adelantado ( creo que está en éste repositorio )

[http://ubuntu.beryl-project.org/]("http://ubuntu.beryl-project.org/")

En esa dirección están los repositorios para agregar al sources.list y la llave para bajar e instalar.

Ok, a partir de ahí los paquetes esenciales para la nieve serían:

beryl  (obvio)
beryl-manager ( a veces el beryl no carga este otro )
emerald-themes (gestor de temas de las ventanas y bordes, etc)
beryl-plugins-unsupported ( en éste es donde está el efecto de la nieve por ej.)

Entrás a la administración de beryl desde el diamantito rojo:
1) Gestor de ajustes Beryl
2) Extras
3) Acá está el efecto llamado SNOW

Activalo con algun atajo de teclado y reiniciá beryl porque sino no te toma el cambio y el efecto no arranca ( yo me pasé dos días activandolo y dándole a la tecla para que el efecto empieze hasta que probé esta opción JUAAA )
El efecto es excelente y no solo es de nieve, podés poner tu propio gráfico y decirle desde que posición arranca y en cual termina o sea que se puede armar también lluvia, hojas que vuelan desde un costado, etc.:popcorn:

---

### Post by undiaperfecto on 2007-08-12
Buenisimo, funciona de maravillas

---

### Post by fernando_bonnin on 2007-08-14
Una pregunta, uds tenian instalado los efectos de escritorio que vienen con el feisty, o le habían instalado el beryl? La pregunta es porque yo pude hacer funcionar el cubo con la instalacion original, aunque no llegué a usar muchas funciones, y cuando quise instalar el compiz-fusion siguiendo un tutorial se me descaje... y no pude volver a tener entorno gráfico.

---

### Post by aceki on 2007-08-14
Fer los efectos de feisty son el cubo basico y  los de ventanas de ondas, si queres instalar el beryl hace esto:

[http://ubuntu-beryl.com.ar/2007/04/instalar-beryl-en-ubuntu-feisty-fawn_26.html](http://ubuntu-beryl.com.ar/2007/04/instalar-beryl-en-ubuntu-feisty-fawn_26.html)

Ahi te dice como instalar todo los efectos de beryl y sus correspondientes paquetes, anda en todos lados (lo probe en varias maquinas con distintas distro y configuraciones)

Fijate de saltate la parte de configuracion de la placa ATI, no se cual tenes vos, pero ya tenes lo drivers instalados.

Yo uso estos, tambien estan los de compiz-fushion pero no los instale todabia (igual para lo que uso yo la pc no me llama mucho los efectos)

---

### Post by sajnox on 2007-08-15
Beryl - Compiz con placas ATI es igual a parir trillizos sin anestesia. Yo me volvi loco siguiendo tutoriales y copiando del Live cd el xorg.conf,y al final me funciono si instalaba desde cero y NUNCA instalaba ningun driver de la placa y me quedaba con lo que venia en la instalacion.

Respecto a instalar Compiz Fusion tienen los repositorios de Treviño que andan bien, aunque ahora que lo pienso algo debe faltar por que hay efectos que nuevos que no los tengo, en casa lo reviso

Saludos,

---

