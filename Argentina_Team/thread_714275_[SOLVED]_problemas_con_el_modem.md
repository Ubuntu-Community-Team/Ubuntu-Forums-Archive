---
title: "[SOLVED] problemas con el modem"
date: 2008-03-03
forum: Argentina Team
---

### Post by andy_91 on 2008-03-03
[[IMG]http://img182.imageshack.us/img182/2793/pantallazokf7.th.png[/IMG]](http://img182.imageshack.us/my.php?image=pantallazokf7.png)

que quiere decir eso de la foto?


es que desde que empeso a salir no me puedo conectar a internet (ahora estoy usando un live)


me dan una mano con eso?

a es ubuntu 7.04

hice unas actualizaciones que salieron en el gestor de actualizaciones

me pidio reiniciar

reinicie y me empeso a salir ese cartel que hago?

desde ya gracias

---

### Post by andy_91 on 2008-03-03
> Muchos me han comentado un problema que hay al configurar internet en ubuntu, despues de ejecutar pppoeconf, todo funciona bien, pero cuando reinician el sistema tienen que volver a lanzar pppoeconf, no se conecta automaticamente, este problema lo resolvemos editando el /etc/network/interfaces :

sudo gedit /etc/network/interfaces
Borramos todo lo que haya en este archivo, y reemplazamos por esto:
auto lo
iface lo inet loopback
mapping hotplug
script grep
map eth0
auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider
auto eth0
iface eth0 inet manual
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

Guardamos y ya deberia funcionar internet automaticamente al prender el computador.


bueno este tutorial es para otra cosa pero resolvio mi problema de red por ahora

---

