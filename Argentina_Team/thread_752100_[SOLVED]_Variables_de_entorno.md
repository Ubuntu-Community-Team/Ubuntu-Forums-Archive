---
title: "[SOLVED] Variables de entorno?"
date: 2008-04-11
forum: Argentina Team
---

### Post by Teno on 2008-04-11
Hola,

Estuve haciendo unas pruebas con un programita llamado "biflter" para ver si podia -sin exito- para tratar de saltear el proxy transparente de Fibertel.

Pero al sacarlo, me quedaron dos variables, que la hacer "export" salen al final, y aparentemente esto me esta molestando con el apt-get

Cuando hago export, sale:

declare -x XAUTHORITY="/home/marcelo/.Xauthority"
declare -x http_proxy="http://127.0.0.1:8000/"
declare -x no_proxy="localhost,127.0.0.0/8,*.local"

Donde estan esas entradas? Las quiero sacar y no puedo. Mire por todos los perfiles y nada, estaran el el gnome???

Muchas gracias!!!

---

### Post by Teno on 2008-04-11
Cristo...

Ya lo encontre...

Systema > Preferencias > Proxy de la red....:popcorn:

---

### Post by sajnox on 2008-04-11
> **Teno said:**
> Cristo...

Ya lo encontre...

Systema > Preferencias > Proxy de la red....:popcorn:

Podriamos decir que el thread esta [SOLVED]??

---

### Post by Teno on 2008-04-11
Si, perdon, como lo pongo en solved? Le cambio el titulo ???

---

### Post by Skavenger on 2008-04-13
> **Teno said:**
> Si, perdon, como lo pongo en solved? Le cambio el titulo ???
arriba en "Thread Tools" lo marcas como solved

---

