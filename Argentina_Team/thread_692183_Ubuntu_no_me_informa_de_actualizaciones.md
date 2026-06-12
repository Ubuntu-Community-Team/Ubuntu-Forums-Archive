---
title: "Ubuntu no me informa de actualizaciones"
date: 2008-02-09
forum: Argentina Team
---

### Post by Mauro22 on 2008-02-09
Asi es, de un dia para el otro (hace rato me pasa esto), ubuntu no me informa que tengo actualizaciones.

El otro dia al leer aca que el emesene se habia actualizado, fui a sistema -> administracion -> gestor de actualizaciones y tenia como 150mb para bajar.



Que puedo hacer??

Saludos!

---

### Post by rojojuan on 2008-02-09
Podés activar las actualizaciones automáticas en Sistema - Administración  -Orígenes del Software- Actualización

---

### Post by facundocorradini on 2008-02-09
Supongo que debés haber desactivado el servicio "Update Notifier"

Andá a sistema -->preferencias -->Sesiones, y fijate que la casilla de Update notifier tiene que quedar tildada.

---

### Post by Mauro22 on 2008-02-09
Todo lo que dicen esta activado.

El perfil esta configurado para que chequee a diario las actualizaciones y tiene activada la opcion de "Notificar las actualizaciones"


:confused:
Gracias!

---

### Post by niko_3100 on 2008-02-09
fijate en /etc/init.d si tenes algo como update-notifier o algo asi, no me acuerdo bien ahora. Estoy en xp proque estoy a punto de jugar al sonic adventure jejeje!! mañana me fijo bien y te digo como se llama bien el nombre del update, igualmente si tenes todo eso tildado fijate si en el monitor del sistema te lo marca como que sta levantado.

---

### Post by Mauro22 on 2008-02-10
Me fije y si lo quiero abrir me da esto:

** (update-notifier:6018): WARNING **: already running?

:confused:


Gracias!

---

### Post by facundocorradini on 2008-02-10
weird. Lo único que se me ocurre entonces es que no tengas puesto  un applet de "área de notificación".....

---

### Post by Mauro22 on 2008-02-10
El area de notificacion esta...


Rarisimo. A nadie mas le pasa:confused:



Grax por la respuestas!

---

### Post by faktorqm on 2008-02-11
tira este comando para saber si esta corriendo:

```
ps ax | grep update
```

mi salida es esta:

```

faktorqm@ttheedge:~$ ps ax | grep update
 5410 ?        S      0:00 update-notifier
 7010 pts/0    R+     0:00 grep update
faktorqm@ttheedge:~$

```

asi que yo lo tengo corriendo. si lo tenes y sigue sin pasar nada, tira este comando:

```
sudo apt-get update -qq
```

salu2!

---

