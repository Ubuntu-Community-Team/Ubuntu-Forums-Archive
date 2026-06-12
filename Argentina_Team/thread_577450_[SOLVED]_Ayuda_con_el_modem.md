---
title: "[SOLVED] Ayuda con el modem"
date: 2007-10-16
forum: Argentina Team
---

### Post by lopulus on 2007-10-16
Hola amigos de la comunidad: Les escribo para comentarles que me he instalado Ubuntu 7.04 luego de renegar un poco ya que soy absolutamente nuevo y todo lo que se refiere a terminologia es tambien nuevo para mi, asi que desde ya les pido paciencia.
Paso a detallar con el problema que me he encontrado. 
Buscando tutoriales en internet logre instalar el  modem, configurar la coneccion, pero no logre poder conectarme. Entonces intente reinstalar todo nuevamente (si es que se puede) y a la hora de ejecutar el comando ./go me sale un error que a continuacion detallo

mkdir -p /usr/sbin
/usr/sbin/install/ -c -m 755pppoe /usr/sbin
/usr/sbin/install/ no se puede borrar: permiso denegado
make *** [install] error
Oops! it looks like make install failed

eso me aparece luego de que el sistente hace varias operaciones. 
El tutorial que utilice es el siguiente

[http://www.guia-ubuntu.org/index.php?title=Configuraci%C3%B3n_del_modem_Huawei_SmartAX_MT_810](http://www.guia-ubuntu.org/index.php?title=Configuraci%C3%B3n_del_modem_Huawei_SmartAX_MT_810)

y tambien este:

[http://www.taringa.net/posts/info/910779/Configurar-módem-Huawei-en-Ubuntu-7_04.html](http://www.taringa.net/posts/info/910779/Configurar-módem-Huawei-en-Ubuntu-7_04.html)

Lo que no se es que es el nas0 ya que cuando coloque el siguiente comando, la segunda vez que lo "instale"(?)
sudo br2684ctl -c 0 -b -a 0.33  (Tengo arnet)
no me salio lo que me tenia que salir y me salio esto

bridge: Interface "nas0" could not be created: Files exists (o algo similar)
bridge: Communicating over ATM 0.0.33, encapsulation: LLC 
bridge: fatal: failed to conect to socket

No se si esto sera de ayuda pero es lo que tengo. Desde ya agradezco mucho


Lopulus

---

### Post by JoACoV on 2007-10-16
no entiendo mucho de esto, pero yo instale el mismo modem sin problemas..

instalaste todas las dependencias y el build-essential?

fijate si te salteaste un paso o algo

---

### Post by Hei Ku on 2007-10-16
te dio un error de permisos, porque el make install solo puede hacerlo como superusuario.

proba ponerle sudo adelante para correrlo.

Deberia ser: sudo ./go

---

### Post by lopulus on 2007-10-16
Hola amigos! quiero decirles que ya estoy navegando desde ubuntu con mozilla firefox
gracias todo anduvo a la perfeccion

---

