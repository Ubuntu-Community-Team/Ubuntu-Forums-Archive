---
title: "desbloquear equipo con mouse"
date: 2021-08-25
forum: Catalan Team
---

### Post by dashky2 on 2021-08-25
hola me gustaria saber si hay alguna opcion para desbloquear el equipo con el mouse que no sea introduciendo la contraseña
por ejemplo con alguna imagen o algo a modo de bloqueador de imagen como en el movil etc

---

### Post by wgarcia on 2021-08-26
Això depèn del que hi hagi disponible al teu sistema. Per exemple per empremta digital:

[https://help.ubuntu.com/stable/ubuntu-help/session-fingerprint.html.en](https://help.ubuntu.com/stable/ubuntu-help/session-fingerprint.html.en)

---

### Post by dashky2 on 2021-08-26
para eso necesito un lector de huellas dactilares no?
yo me refería a una contraseña de imagen por ejemplo
pero gracias por la informacion

---

### Post by wgarcia on 2021-08-27
Ubuntu fa servir [PAM]("http://en.wikipedia.org/wiki/Pluggable_authentication_module") per fer l'autenticació. Hi ha maneres d'usar mecanismes alternatius a la contrasenya per l'autenticació, depenent del context on es troba l'usuari. Per exemple, hi ha maneres d'autenticar-se amb la imatge de la cara (el projecte es pot trobar [aquí]("http://code.google.com/p/pam-face-authentication/")). 

Compte perquè és molt fàcil autobloquejar-se i no poder accedir al sistema quan es proven aquestes coses.

---

