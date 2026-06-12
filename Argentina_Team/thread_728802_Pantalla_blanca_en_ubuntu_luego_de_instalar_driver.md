---
title: "Pantalla blanca en ubuntu luego de instalar driver nvidia"
date: 2008-03-19
forum: Argentina Team
---

### Post by Apokalyptica79 on 2008-03-19
Hola, mi problema es el siguiente:
Quise instalar el driver de mi placa de video una Nvidia GForce 6200 de 256 agp y me baje el driver le di permisos de ejecucion y luego hice /etc/init.d/gdm stop y procedi a ejecutar el .bin una vez terminado hice /etc/init.d/gdm start y carga todo bien, el tema es que aparece una pantalla blanca y no logro ver el escritorio, pero si me paso a las consolas, con eso no hay problemas, probe tratar de solucionarlo con dpkg-reconfigure xserver-xorg, con dpgk-reconfigue -phigh xserver-xorg y editando el /etc/X11/xorg.conf y nada, no tengo suerte.
Pero por lo visto el driver se cargo bien porque me aparece el logo de nvidia.
Perdon por las molestias.
Muchas gracias.

---

### Post by faktorqm on 2008-03-19
hace una cosa, para que te arranque de vuelta, sacale el driver de nvidia en la seccion driver del xorg.conf, y ponele vesa. cuando tengas el escritorio andando, bajate el "envy". Salu2!

---

### Post by Apokalyptica79 on 2008-03-19
Hola muchas gracias lo pruebo y te comento.

---

### Post by Apokalyptica79 on 2008-03-19
Hola, hice lo que me dijiste lo cambie a vesa y anduvo.
Luego baje envy y me dio unos problemas, creo que cumpli con sus dependencias e instalé lo que me pedía pero a la hora de querer instalar el driver nvidia me tira lo siguiente.
Creo que adjunté la imagen en caso de haberlo hecho bien.
Desde ya muchas gracias.

---

### Post by niko_3100 on 2008-03-19
No probate los drivers restringidos que te baja automaticamente ubuntu?

---

### Post by Apokalyptica79 on 2008-03-19
Hola, si traté de instalarlo de esa manera pero no hace caso la aplicación no se abre ni nada.

---

### Post by faktorqm on 2008-03-20
lo del envy me parece raro... basicamente ahi lo que dice es que no encontro el instalador en /usr/share/envy/kernel/blabla. no tendras la version d 64bits no?

---

### Post by Apokalyptica79 on 2008-03-20
Hola, gracias por preguntar eso, me olvide de decir algo muy importante. Tengo arquitectura de 64 bits pero es ubuntu gutsy de 32, entonces me bajé **NVIDIA-Linux-x86-96.43.05-pkg1.run** y el envy que me bajé es **envy_0.9.10-0ubuntu7_all.deb** y si mal no recuerdo también es para 32 bits.
Espero esto sea útil.
Gracias a todos.

---

