---
title: "[SOLVED] Dónde encuentro a conky?"
date: 2007-09-06
forum: Argentina Team
---

### Post by Vero1 on 2007-09-06
Hola amigos,

Quisiera saber cómo se hace para hacer funcionar conky.
Lo instalé pero no lo encuentro...

gracias y saludos:)

---

### Post by niko_3100 on 2007-09-06
Muy sencillo en una terminal pone conky asi de una y listo. Igual eso es solo el comienzo lo mejor seria que vayas a la pagina de conky y te fijes todo lo que podes hacer. Yo de paso asi no abro otro tema hago una pregunta, cuando pongo para que me inicie conky cuando arranca el ubuntu como lo inicia primero me queda como si estubiera atras del wallpaper y no lo puedo ver, hay algun comando para que inicie despues de algun tiempo nose... 60 segundos. Ej: conky -t 60   algo asi?? Gracias.

---

### Post by Vero1 on 2007-09-06
Hola niko_3100,

Muchas gracias:)

---

### Post by nest on 2007-09-06
> **niko_3100 said:**
> Muy sencillo en una terminal pone conky asi de una y listo. Igual eso es solo el comienzo lo mejor seria que vayas a la pagina de conky y te fijes todo lo que podes hacer. Yo de paso asi no abro otro tema hago una pregunta, cuando pongo para que me inicie conky cuando arranca el ubuntu como lo inicia primero me queda como si estubiera atras del wallpaper y no lo puedo ver, hay algun comando para que inicie despues de algun tiempo nose... 60 segundos. Ej: conky -t 60   algo asi?? Gracias.

```
sudo gedit/nano ~/.conkyrc
```

donde dice

**own_window_type** ponele normal. quedaría

own_window_type normal

si sigue pasandote eso avisame que te paso por aca el script que tengo yo para que inicie todo como debe ser.

---

### Post by niko_3100 on 2007-09-06
Sip, me lo soluciono pero ahora cuando apreto para ir directo al escritorio me lo mete atras tambine me lo baja como si fuera una ventana mas y me desaparece...... :(

---

### Post by nest on 2007-09-07
> **niko_3100 said:**
> Sip, me lo soluciono pero ahora cuando apreto para ir directo al escritorio me lo mete atras tambine me lo baja como si fuera una ventana mas y me desaparece...... :(

own_window yes
own_window_type normal
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky

ponele eso ;)

---

### Post by niko_3100 on 2007-09-08
no, pero no quiero que sea una ventana mas quiero que este ahi laburando background que tengas que hacer un top para matar el proceso no verlo por ventanas. Debe haber un timer que pone que a tantos segundos levante... me parece.

---

### Post by nest on 2007-09-10
en /home/usuario/ creá un archivo que se llame .conkylaunch y metele lo siguiente:

```
#!/bin/bash
sleep 6 &&
conky &
exit

```

despues anda a **system>preferences>sessions**

y agrega un archivo de inicio que diga:

** /home/axel/.conkylauch**

eso hace lo que queres. un script que tarda 6 segundos (lo que yo necesito, editalo con lo que necesites vos) para levantar el conky.

---

### Post by niko_3100 on 2007-09-10
Unica mente hago eso? porque no me sirvio asi. Hice eso asigne el path /home/nicolas/.conkylaunch pero no me levanto :(   a vos te funciono?

---

### Post by niko_3100 on 2007-09-10
Perdon soy un dolobu me falto poner sh adelante en el comando, ahora si va como piña. Graciaasss!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

