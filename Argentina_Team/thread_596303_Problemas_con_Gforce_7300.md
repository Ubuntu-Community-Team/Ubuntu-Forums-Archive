---
title: "Problemas con Gforce 7300"
date: 2007-10-29
forum: Argentina Team
---

### Post by mauro7g on 2007-10-29
Hola a todos....tengo un pequeño problema con Ubuntu 7,10. Se cuelga la pc de manera tal que no tengo sonido, el video se traba todo no anda ni el puntero del mouse, no puedo reiniciar el modo gráfico, tampoco puedo iniciar una terminal....nada de nada tengo que resetear la pc directamente.. Creo yo que debe ser problema de video, porque cuando comienza a funcionar el protector de pantallas despues de un tiempo se traba todo mal. Tengo instalados los drivers de Nvidia que trae ubuntu.....bueno, la verdad es que no sé por donde empezar...por eso traigo mi inquietud...desde ya les agradezco a todos. :lolflag:

---

### Post by Hernán-Amaya on 2007-10-29
proba reconfigurando el xorg.conf con el siguiente comando
```

sudo dpkg-reconfigure xserver-xorg

```

elegí el driver de nvidia y proba, sino te anda proba con el driver de vesa

y si no ten anda cosa mandanos tu /etc/X11/xorg.conf 

suerte!

---

### Post by rojojuan on 2007-10-29
Con esa placa tuve también algunos problemas.
Hasta el declado funcionaba mal.
Los arreglé así:
Instalé Envy
Lo corrí y desinstalé todo nvidia.
Abrí Envy nuevamente e Instalé nvidia. Envy baja los últimos driver de nvidia.
Reinicié y todo perfecto.

---

### Post by mauro7g on 2007-10-29
Ok Hernan! Voy a porbar con eso en un rato te aviso a ver como me fué! muchas gracias.

---

### Post by mauro7g on 2007-10-29
> **rojojuan said:**
> Con esa placa tuve también algunos problemas.
Hasta el declado funcionaba mal.
Los arreglé así:
Instalé Envy
Lo corrí y desinstalé todo nvidia.
Abrí Envy nuevamente e Instalé nvidia. Envy baja los últimos driver de nvidia.
Reinicié y todo perfecto.

Y como haces si queres volver a los Drivers anteriores??? Yo instalé Envy cuando tenia Ubuntu 7.04. Desinstale Envy y me quedé sin video.

---

### Post by rojojuan on 2007-10-30
> **mauro7g said:**
> Y como haces si queres volver a los Drivers anteriores??? Yo instalé Envy cuando tenia Ubuntu 7.04. Desinstale Envy y me quedé sin video.

Buena pregunta. No tengo necesidad por ahoa de desintalar Envy, pero me parece -es solo una suposición porque no la probé- que correría Envy y desinstalaría todos los drivers de nvidia, (trae esa opción) rearrancaría con el xorg.conf genérico  y desde Sistema agregaría los drivers de Nvidia.
Te parece que puede ser?

---

### Post by mauro7g on 2007-10-30
Gracias a todos...y queria decirles que pude solucionar el problema instalando Envy...me anda todo de 10!!! Muchas gracias por la ayuda que me brindaron...nos estamos viendo!!!

---

### Post by faktorqm on 2007-10-31
despues dicen que el mejor driver es ese....y no el de nvida.... (el envy instala el de nvidia)

---

