---
title: "Servidor"
date: 2007-09-26
forum: Argentina Team
---

### Post by sharkg on 2007-09-26
Hola a todos... hace rato q leo el foro, pero no posteo nada... hasta hoy.
les comento mi priblema:
arme una maquina, entre varias y lo mejor q me quedo es una PII-400 con 256 pc 133, pero creo q la placa solo tira pc-100 y un disco de 8Gb.
bueno, le instale ubuntu server 7.4, al momento de poner la ip, lo deje para despues porq tengo ips dinamicas en un server para ello entre otras cosas y necesitaba el num MAC para poder subirla a la red y asignarle un ip, todo eso esta de el server de dhcp, pero en el de linux, terminada la instalacion no se q mas hacer, no se como configurar para q entre a la red y demas... si alquine me puede dar una mano o algun link para un manual.. algo.. desde ya muchas gracias. saludos
eZe

---

### Post by faktorqm on 2007-09-26
Hola, willkommen al foro.
Anda a aplicaciones -> Accesorios -> terminal y escribi:

```
ifconfig
```

para ver la configuracion actual de tu placa. (si tenes dhcp y la placa todo ok deberia mostrarte una direccion autoasignada)

si queres setear una ip fija, haces:

ejemplo: ```
ifconfig eth0 192.168.10.12 netmask 255.255.255.0 
```

forma general: ```
ifconfig <nombre> <direccion IP> netmask <mascara> 
```

si te llega a decir que no tenes permisos, usa la palabra "sudo" (sin comillas) adelante de cada comando.

En Sistema -> Administracion -> Red tenes para configurarlo gráficamente.

En la barra, cerca del icono del tacho de basura, tenes un icono como con 2 monitores parecido a uno que ya debes conocer, solo que no es verde, ni azul titilando ;) ahi tambien tenes para configurar.

para mas informacion, escribi "man ifconfig" o para info rapida "ifconfig --help".

Si necesitas compartir archivos, loguear users en dominio y demas menesteres, no dudes en consultar. Wenas noches. salu2!!

---

### Post by sharkg on 2007-09-27
uhhh muchas gracias, voy a ver q sale.
te comento q solo tengo terminal, no instale gestor grafico todavia....
otra.. como tengo servidor dhcp, seguramente pongo eth0 auto..
voy a ver q pasa. muchas gracias y te aviso q paso!!

---

### Post by sharkg on 2007-09-27
jeje... bueno meti mano por todos lados y logre hacer andar la maquina en red.... ponia ipcofig antes.... por eso no me andaba nada.... muchas gracias. salu2

---

### Post by FlyerDie on 2007-09-27
> **sharkg said:**
> jeje... bueno meti mano por todos lados y logre hacer andar la maquina en red.... ponia ipcofig antes.... por eso no me andaba nada.... muchas gracias. salu2

ifconfig :lolflag:

---

### Post by sharkg on 2007-09-27
jejeje...si es verdad q $%&*!, pero bueno, de los errores se aprende!!! ](*,)

---

### Post by faktorqm on 2007-09-28
me alegro de que te haya servido. salu2!

---

### Post by Teno on 2007-10-01
No dudes del producto porque la verdad para un newbie como yo funciona fantastico. Ya pude montar un Samba para red local y un FTP para acceso remoto a los archivos.
Y por las dudas, un backup diario a un disco USB del recurso de samba...
ahora voy por mas!!!

Hay miles de miles de COMOs y guias varias para hacer todo lo necesario en linux, por ahora todo josha!

Te recomiendo la documentacion de "server" en la pagina de Ubuntu, que como guia de inicio para servicios es fantastica.:popcorn:

---

### Post by sharkg on 2007-10-01
bueno gracias por la info.. voy a ver q puedo encontrar... y q puedo hacer, el drama es q como hay mucha info, no toda es buena..
despues pongo los resultados, salu2 y gracias

---

