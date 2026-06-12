---
title: "Apariencia de la consola terminal"
date: 2008-05-14
forum: Argentina Team
---

### Post by Applelnx on 2008-05-14
Queria saber algo muy simple para explicar (y espero que tambien para hacer).

Alguien sabe comocambiar el color de la letra del nombre del usuario en la consola? Es decir

apple@linux:~$ 

Hay alguna manera de cambiar la letra y el color de esa parte nada mas? como para diferenciarla del otro texto. Saludos

:D

---

### Post by santiagoward2000 on 2008-05-14
> **Applelnx said:**
> Queria saber algo muy simple para explicar (y espero que tambien para hacer).

Alguien sabe comocambiar el color de la letra del nombre del usuario en la consola? Es decir

apple@linux:~$ 

Hay alguna manera de cambiar la letra y el color de esa parte nada mas? como para diferenciarla del otro texto. Saludos

:D

Hola,
No sé si sea igual en todas las teminales (me imagino que no, pero debe ser parecido). En xfce4-terminal, vas a **Preferencias/colores**, y ahí podés elegirlo. Revisá las preferencias, seguro que está por ahí.
Saludos!

---

### Post by euzkoarima on 2008-05-14
Si estas en gnome, menú Editar->Perfil Actual
y ahí solapa colores.

Saludos.

---

### Post by Applelnx on 2008-05-14
Miren, me aparecen estas opciones en Cambiar Perfil Actual

[[IMG]http://img84.imageshack.us/img84/8323/colorestt2.png[/IMG]](http://imageshack.us)

No se bien de donde cambiarlo, no se si son las opciones de la paleta, pero con eso aparentemente no me cambia nada :confused:

---

### Post by euzkoarima on 2008-05-14
Cambia el color donde dice "Color del Texto" y "Color del Fondo".

---

### Post by Applelnx on 2008-05-14
Sisi, eso lo pude cambiar, me gustaria que pudiera quedar algo asi por ejemplo (no se si se puede)

**[COLOR="Lime"]apple@linux:~$[/COLOR]**  sudo apt-get install tvtime

---

### Post by euzkoarima on 2008-05-14
AHHH, está, en ese caso deberías cambiar el prompt del bash, que se guarda en la variable de entorno PS1. El que te viene por defecto está en el archivo ~/.bashrc

Como supongo que hasta es más lo que te estoy confundiendo que ayudando, te recomiendo que en google pongas ".bashrc PS1 prompt color" y vas a encontrar bastante info.
En particular te recomiendo los siguientes links
[Este tutorial]("http://www.euskalnet.net/iosus/linux/Bash-Prompt-HOWTO.html") está bastante bueno, en particular mira el [segundo capítulo]("http://www.euskalnet.net/iosus/linux/Bash-Prompt-HOWTO-2.html")
Y [este otro]("http://www.linuxrc.com.ar/index.php?module=articles&id=22") que esta bueno también.

Saludos.

---

### Post by Applelnx on 2008-05-15
Buenisimo, pude cambiarlo pero solo temporalmente. Sabes bien donde esta el archivo .bashrc, en este tengo que agregarle la linea de PS1=...

Saludos

---

### Post by sergiom99 on 2008-05-15
> **Applelnx said:**
> Buenisimo, pude cambiarlo pero solo temporalmente. Sabes bien donde esta el archivo .bashrc, en este tengo que agregarle la linea de PS1=...

Saludos

esta en el home de tu usuario.
si editas ~/.bashrc con gedit o vi o mcedit o el que tengas, lo podes hacer.

Hablando de .bashrc:
como hago para que el "grep --colour=auto" me resalte lo que busco en verde? por defecto lo hace en rojo, pero como las letras de consola son naranja, mucho no resalta.

---

### Post by Applelnx on 2008-05-15
Gracias a todos, en cuanto a tu inconveniente, fijate el post que publico euzkoarima

[http://www.linuxrc.com.ar/index.php?module=articles&id=22](http://www.linuxrc.com.ar/index.php?module=articles&id=22)

si queres que este resaltado creo que tenes que sumarle 10 al numero, por ejemplo

0;32 es font de color verde
0;42 es resaltado de color verde

Por las dudas lee el post ese, porque no se si es esto lo que preguntas.

Saludos

---

### Post by sergiom99 on 2008-05-15
gracias, pero no era lo que estoy necesitando. esta bueno el howto, pero es solo para el prompt.
yo quiero que cuando hago un grep de algo, me resalte los parametros del grep en un color que yo defina.

---

### Post by euzkoarima on 2008-05-15
Hola sergiom99 mirá [este link]("http://www.debian-administration.org/articles/460") que explica lo de grep (es parecido a como trabaja ls también).
No lo usé nunca, pero supongo que si llenás la variable GREP_COLOR con lo que te guste en el .bashrc debería quedar joya.

Saludos.

---

### Post by sergiom99 on 2008-05-15
gracias!! creo q lo arregle agregando > export GREP_COLOR='1;32'
al .bashrc.
Por ahora lo corri en consola y quedo OK, vamos a ver si lo mantiene al levantar de nuevo el shell.

---

