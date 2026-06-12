---
title: "Arrancar varias sesiones X"
date: 2008-03-15
forum: Argentina Team
---

### Post by jclevien on 2008-03-15
Hola que tal,

Estoy necesitando correr varias sesiones X. Una sesión, es la que se ve en pantalla :0.0, las restantes quisiera que se arrancaran en background.

¿Cómo lo puedo hacer? ¿Donde consigo documentación para hacerlo?

Gracias.


Juan

---

### Post by Hei Ku on 2008-03-16
No te sirve arrancarlas con Ctrl+Alt+F8, F9 ,etc?

---

### Post by ariel on 2008-03-17
> **jclevien said:**
> Hola que tal,

Estoy necesitando correr varias sesiones X. Una sesión, es la que se ve en pantalla :0.0, las restantes quisiera que se arrancaran en background.

¿Cómo lo puedo hacer? ¿Donde consigo documentación para hacerlo?

Gracias.


Juan

se puede hacer pero no es trivial.

Aca: [https://help.ubuntu.com/community/VNC#head-a2254fc1fe04cd6bacc05b7277c2b76a65ccb36c](https://help.ubuntu.com/community/VNC#head-a2254fc1fe04cd6bacc05b7277c2b76a65ccb36c)

tenes un ejemplo de como logearte remotamente usando via VNC, accediando via gdm (user login / chooser). Si te fijas, vas a ver que usan una sesion X independiente, en la pantalla virtual 1 (ej: 192.168.1.25:1)

el howto tiene tiene bastantes vueltas; si encontras uno mejorplease postea el link ;)

---

### Post by jclevien on 2008-03-17
Hei Ku,

No, tiene que ser en forma automática, mediante un programa.

ariel,

El problema con tu propuesta es que usa el Xvnc.
Paso a explicar: necesito correr el X puro para asociarle un x11vnc a cada sesión X. Esto es necesario porque cada conexión necesito que se realice mediante SSL. El x11vnc soporta SSL directamente, con lo que queda solucionado el problema, el tema es que no se como arrancar X puro, ya intenté asociar el x11vnc con una sesión Xvnc, pero no hubo caso.

Gracias a ambos, si encuentro algo que sirva lo publico.
Saludos.


Juan

---

### Post by Hei Ku on 2008-03-17
No me acuerdo donde es, pero  hay un archivo que te dice cuantas sesiones de cada tipo arranca automaticamente. El que dice que arranque 6 tty (F1 a F6) y 1 de X (F7). Seguramente podes modificarlo para que arranque varios X

---

### Post by jclevien on 2008-03-17
Hei Ku,

Gracias por tu recomendación.
Lamentablemente, la creación de sesiones X tiene que ser en forma dinámica, es decir, yo desarrollé un servicio que a medida que llegan peticiones, se lanzan las sesiones X y se asignan dinámicamente.

Estoy pensando en incorporar SSL a mi desarrollo y evitar este problema.

Muchas gracias.


Juan

---

