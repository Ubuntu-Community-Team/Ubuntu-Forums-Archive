---
title: "Falla actualización libsmbclient"
date: 2007-11-16
forum: Argentina Team
---

### Post by majatu on 2007-11-16
Gente a alguno le esta haciendo este error cuando les instala las ultimas actualizaciones? a mi me bajó todas menos la de libsmbclient. como puedo descargarlo manual de ultima?

me dice:

W: Falló al obtener [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden



Saludos!

---

### Post by por100pre1 on 2007-11-16
No estás a solas:

[http://ubuntuforums.org/showthread.php?t=614969](http://ubuntuforums.org/showthread.php?t=614969)

espera a que la situacion sea corregida. :)

EDIT: Prueba bajarlo de [aquí]("http://packages.ubuntu.com/gutsy/libs/libsmbclient").

---

### Post by Hernán-Amaya on 2007-11-16
somos varios entonces, como decia un viejo personaje de chachacha seremos******* pero somos una bocha!

---

### Post by Keith_Beef on 2007-11-16
Yo, también, veo el mismo mensaje.

K.

---

### Post by rojojuan on 2007-11-17
Recién instalé las actualizaciones y veo que se instaló libsmbclient. Ahora bien, no se si se instaló antes o con la actualización de hoy.

---

### Post by facundocorradini on 2007-11-17
A mi me paso lo mismo hace unas horas, pero al reintentar recien andubo.

Puede haber sido alguna cuestion del server..

---

### Post by por100pre1 on 2007-11-17
Yo acabo de recibir la actualización, no tuve problemas. Siempre existe la opción de seleccionar otro servidor:

```
gksu software-properties-gtk
```

---

### Post by Hernán-Amaya on 2007-11-17
se soluciona eligiendo otro servidor yo tuve el mismo problema, y pido disculpas se me escapo el Bo**** a veces soy medio mal hablado.

suerte!

---

### Post by clasificado on 2007-11-17
[segun este bug]("https://bugs.launchpad.net/ubuntu/+bug/163116") encontraron regresiones en las versiones nuevas de esos paquetes

pero en lugar retirar las actualizaciones, les cambiaron los permisos, y eso hace que falle. Cuestionable desde mi punto de vista, pero que se yo!

De ser asi, creo que lo mejor seria aguantarselo un cacho, o clavar la version desde synaptic. Encontrar ese paquete y bajárselo por no-synaptic significaria exponerse a la regresión de la cual ellos estan tratando de protegernos

clasificado

---

