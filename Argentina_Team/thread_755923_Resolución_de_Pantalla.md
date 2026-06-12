---
title: "Resolución de Pantalla"
date: 2008-04-15
forum: Argentina Team
---

### Post by mrchelo2002 on 2008-04-15
Hola, Estoy intentando instalar ubuntu 7.10 en mi maquina. Es un micro athlon de 1.2Ghz, tengo una placa de video vodoo3 de 8mb.
Mi problema es que la resolución máxima que me permite el sistema es de  800x600. Al intentar instalarlo no veo los botones de aceptar, cancelar, etc
¿Es una limitación de mi placa de video? O como se puede solucionar? En windows uso sin problemas 1024 x 768.
Desde ya muchas gracias.

---

### Post by sajnox on 2008-04-15
Hola

Proba con lo siguiente:

Abris una terminal y escribis:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.back
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reinicias las graficas con ctrl + alt +backspace y fijate si te reconoce mayor resolucion, si se traba y la grafica no anda apretas ctrl + alt  + f1 te logueas con tus datos y escribis

```
sudo mv /etc/X11/xorg.back /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

---

### Post by mrchelo2002 on 2008-04-16
Gracias, ahora estoy en el trabajo pero a la tarde pruebo y te cuento. Muchisimas gracias. Saludos.

Chelo.

---

