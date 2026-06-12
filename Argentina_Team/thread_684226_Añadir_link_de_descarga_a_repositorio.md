---
title: "Añadir link de descarga a repositorio"
date: 2008-01-31
forum: Argentina Team
---

### Post by h9005 on 2008-01-31
¿Como hago para que en vez de descargar el programa manualmente, agregar el link a un repositorio? Puede hacerse? Así no tener que instalarlo manualmente.

---

### Post by leo_rockway on 2008-01-31
Si el programa tiene un repositorio para ubuntu entonces bastaria agregar la direccion que ellos proveen a tu sources.list (siempre y cuando confies en la fuente del programa).

ej: deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

ese es el repositorio para kde4 para kubuntu.

EDIT: en general tb es necesario agregar una clave.

---

### Post by clasificado on 2008-02-01
Si es de extensión .DEB, esta todo mas que bien

No deberias tener una diferencia considerable contra un repositorio

clasificado

---

### Post by h9005 on 2008-02-03
Donde agrego las direcciones a sources list?

---

### Post by marianom on 2008-02-04
/etc/apt/sources.list (siempre hace un backup antes de empezar a toquetear).

---

### Post by atari130xe on 2008-02-04
OffTopic: Mariano vos no sos el creador el emesene? :)

---

