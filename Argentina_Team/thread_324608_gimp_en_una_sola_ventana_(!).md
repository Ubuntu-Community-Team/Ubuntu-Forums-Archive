---
title: "gimp en una sola ventana (!)"
date: 2006-12-24
forum: Argentina Team
---

### Post by lavaramano on 2006-12-24
estaba leyendo xubuntu.wordpress.com y lei algo *mas* que interesante:

[como hacer para correr al gimp en una sola ventana ]("http://xubuntu.wordpress.com/2006/09/05/howto-run-gimp-in-one-window/") :mrgreen: 

aca lo hacen funcionar en xfce, lo acabo de probar y va como piña.

cito (y traduzco):
```

1) ir a la terminal (xfce menu > sistema > terminal) e instalar los siguientes programas:
sudo apt-get install xnest xfwm4 gimp

2) escribir lo siguiente en la terminal:
Xnest :1 -ac -name GIMP -geometry 1024x690 & xfwm4 --display :1 & gimp --display :1

Buenisimo, no? Asi es como se hace *shortcut*

1) crear un archivo que se llame /usr/bin/gimp1window

sudo touch /usr/bin/gimp1window
sudo mousepad /usr/bin/gimp1window

2) Pegar lo siguiente dentro del archivo:

#!/bin/sh
Xnest :1 -ac -name GIMP -geometry 1024×690 & xfwm4 –display :1 & gimp –display :1

3) escribir 'sudo chmod +x /usr/bin/gimp1window' y cambiar los *shortcuts* del gimp a gimp1window

Diviertanse!

```

saludous

---

### Post by Nemesis Teufel on 2006-12-24
wow, quiero eso para ubuntu.

Se podra utilizar el mismo how to o na' q ver?

---

### Post by pump on 2006-12-24
Si, yo tambien. Todavia no me acostumbro a tener todo separado en ventanas..

Ahi probe, funciona en gnome. :) 
Solo tenes que instalar el xnest. Lo que si ahora tengo que ver si puedo arreglar porque no me deja mover las ventanas del gimp.

Editazo 2: Para que funcione en gnome hay que ejecutar el xnest asi:
```
Xnest :1 -ac -name GIMP -geometry 1024x690 & metacity --display :1 & gimp --display :1
```

Muchisimas gracias por el tuto.

---

### Post by lavaramano on 2006-12-24
buenisimo.
iba a ver que onda con el gnome, pero eran las  5.30 am y no me daba mas la cabeza :mrgreen:

---

### Post by BlackHero on 2006-12-25
safa pero crei que te integraba todo a una misma ventana por que es lo mismo nada mas con una  ventana grande de pared pero igual ta lendo =)

---

### Post by lavaramano on 2006-12-26
y si, es medio cabesa :KS
pero bueno, es mucho mas comodo que tener todas las ventanitas de gimp desparramadas por ahi.

---

### Post by el_itur on 2006-12-27
mmm, esto es medio choto, en realidad lo que estás haciendo es crear otra instancia de X dentro de la que está corriendo (nested), y alli llama a metacity para gestionar las ventanas y al gimp. Es jodido porque estás consumiendo los recursos de dos servidores X.

No recomendable, no ganás nada salvo espacio en la barra de tareas

---

### Post by lavaramano on 2006-12-27
pf.
a esto le decis consumir recursos?
y al *magico beryl* que todos aclaman?

saludos.

---

### Post by Ptero-4 on 2006-12-27
Por ahí hay un programa llamado gimpshop que es el gimp modificado para tener todo en una sola ventana (o algo así), quizas sea mejor usar eso en vez de tener un X anidado por ahí tragando recursos.

---

### Post by beuno on 2006-12-27
> **Ptero-4 said:**
> Por ahí hay un programa llamado gimpshop que es el gimp modificado para tener todo en una sola ventana (o algo así), quizas sea mejor usar eso en vez de tener un X anidado por ahí tragando recursos.

Yo estoy con el gimpshop, pero no te acomoda todo en una ventana, sencillamente te distribuye los elementos mas parecidos a photoshop.
Ayuda, pero igual es molesto...

---

### Post by QUASAR_FREAK on 2006-12-28
para el ke kiera usarlo, aka les dejo komo hacer para ke embeba sus configuraciones (komo ikonos y temas) de gnome y ke use un fondo negro en lugar de ese kema vista =)

Xnest :1 -ac -name GIMP -geometry 1024x690 -br & metacity --display :1 & gimp --display :1 & gnome-settings-daemon --display :1

---

### Post by lavaramano on 2006-12-28
ah, mira.
queda mas lindo asi.

yo creo que habria que hacer un sticky con esto, hay mucha gente que se queja de que el gimp tiene ventanas separadas..

a pesar de que sea un coma-recursos ;P

---

### Post by beuno on 2006-12-28
> **lavaramano said:**
> ah, mira.
queda mas lindo asi.

yo creo que habria que hacer un sticky con esto, hay mucha gente que se queja de que el gimp tiene ventanas separadas..

a pesar de que sea un coma-recursos ;P

Lo stickeo un rato (semanas?), pero no mucho porque sino es un enchastre.

---

### Post by lavaramano on 2006-12-29
se.
de ultima sino se puede hacer un sticky con varios posts interesantes en lugar de poner sticky a todo el thread..
que se yo

---

### Post by beuno on 2006-12-29
> **lavaramano said:**
> se.
de ultima sino se puede hacer un sticky con varios posts interesantes en lugar de poner sticky a todo el thread..
que se yo

Eso me gusto mas.

Junten 4 o 5 y lo armamos.

---

