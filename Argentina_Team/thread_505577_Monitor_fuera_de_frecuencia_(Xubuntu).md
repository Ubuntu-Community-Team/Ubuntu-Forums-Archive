---
title: "Monitor fuera de frecuencia (Xubuntu)"
date: 2007-07-20
forum: Argentina Team
---

### Post by a3reload on 2007-07-20
Gente, que tal??
Anoche instale la ultimar version de Xubuntu y me surgio un problema que al ser un newbie por estas tierras no estoy del todo seguro como solucionarlo.
Cuando booteo e intenta ingresar al entorno grafico del XFCE mi monitor queda con la pantalla negra y con un msg que dice Fuera de Frecuencia (y da valores H y V).
Mi computadora es un PCCHip con placa de video onBoard.
Mi consulta es... por donde arranco para solucionar el problema... por el monitor o la placa de video??
Alguien conoce de este problema??
Saludos y gracias de antemano por el asesoramiento.

---

### Post by scrooge_74 on 2007-07-20
desde una termina (CTRL + ALt + F1)  escribes sudo dpkg-reconfigure xserver-xorg  empieza por allí

hay que ver que tarjeta de video tienes, antes que ver el monitor.

Si no logras que arranque puedes poner mientras que el video driver es VESA. No te va a dar mucha resolución pero te dejaría trabajar mientras encuentras la solución

---

### Post by zspikes on 2007-07-20
intenta cambiar la frecuencia con ctrl alt + (si, la tecla más del teclado numerico)

---

