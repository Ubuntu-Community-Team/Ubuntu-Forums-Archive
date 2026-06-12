---
title: "Cliente para entorno remoto"
date: 2007-07-04
forum: Argentina Team
---

### Post by aceki on 2007-07-04
Gente, buenas noches, los molesto para consultarles, si alguien conoce algun clientes como el que trae windows XP o Vista, para escritorio remoto, no quiero algo que haga VNC, sino que me arranque otra secion en la pc o servidor, lo nesecito ya que administro mi servidor de esa forma, gracias a todos.

pd: Tengo ubuntu 7.04

---

### Post by Al_maverick on 2007-07-04
El VNC te arranca otra sesión en el servidor. El x11vnc es el que te permite tomar control de una sesión existente.
Tenes tambien el freenx, y kde viene con el krfb, pero ese es de escritorio compartido.

Yo uso el x11vnc, pero por los comentarios que vi, el freenx es el mejorcito.

---

### Post by kowal on 2007-07-05
El mejor que probé es el protocolo NX.. o sino ssh desde consola a secas :P

NX server -> Es el programejo oficial de NX. El server es gratuito, pero con limitaciones (no te deja usar más de dos sesiones). Tiene un excelente rendimiento, aunque es soft propietario. [http://www.nomachine.com](http://www.nomachine.com)

FreeNX -> La implementación libre de NX. A veces parece que está un poco abandonado el proyecto y no funciona tan bien como NX server. No tiene limitaciones de usuarios. [http://freenx.berlios.de/](http://freenx.berlios.de/)

Saludos

---

### Post by aceki on 2007-07-05
Al final encontre lo que buscaba, se llama Rdesktop, es identico a Escritorio remoto de Micro****, asi que lo recomiendo plenamente!!!!!

Tambien probe los que me pasaron, pero me gusto mas este por su simplizidad. Gracias a todos !!!

---

### Post by kowal on 2007-07-05
Rdesktop es parecido al Escritorio Remoto de Micro***** porque justamente usa el mismo protocolo (RDP) :P

Saludos.

---

### Post by aceki on 2007-07-05
Eso es lo que buscaba  que use RDP

---

### Post by Kittukahier on 2007-09-27
cuando se instala el x11vnc hay que desinstalar "vino"?

---

### Post by Hei Ku on 2007-09-28
no deberias tener problemas que ambos estén instalados,  aunque no te conviene que esten los dos corriendo al mismo tiempo.

---

### Post by sharkg on 2007-09-28
hola, una pregunta sobre Rdesktop.
este escritorio remoto funciona como el de Win, pero tmb con linux y ademas me permitiria poder entrar desde una maquina con win a la maquina con linux y alrevez tmb??

---

### Post by Kittukahier on 2007-09-28
Gracias por responderme, me funcionó el x11vnc en una sóla dirección y tuve que parar el "vino" para que fuera posible, hice los mismo pasos en cada máquina pero sólo funciona en una dirección!!

---

