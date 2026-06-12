---
title: "[SOLVED] problema con virtualbox"
date: 2007-10-09
forum: Argentina Team
---

### Post by JoACoV on 2007-10-09
bien la cuestión es así:

instale virtualvox desde un paquete deb porque no lo encontre en los repositorios, hasta ahi todo bien.

la cosa es que entro al programa, creo una maquina virtual, le pongo lo parametros casi por defecto y cuando la voy a correr....

```


**No se puede iniciar la maquina virtual (nombre de la maquina)**

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


```

el paquete en cuestion es este:
virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb
creo que lo baje de getdeb

Muchas gracias de antemano por la ayuda

---

### Post by juanman on 2007-10-09
Tenes q agregar tu usuario al grupo vboxusers. No tengo a mano gnome, pero debe ser desde administracion-> Usuarios (o algo asi)

---

### Post by jpmorelli on 2007-10-09
Exactamente lo que dice juanman, fijate que hay un lugar donde dice administrar grupos, entr´a al que dice Vboxusers y tilda tu usario. Para que funcione ten´es que salir y volver a entrar de tu sesi´on. Despues de eso ya queda listo. Suerte !

---

### Post by sajnox on 2007-10-09
Link para agregar VBox a los repositorios:

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by JoACoV on 2007-10-09
Son unos capos, sabia que no podia ser el paquete, la parte de "current user" era sospechosa, pasa que todavia no me familiarizo bien con el sistema operativo...

Pero ya esta funca de 10

Solved

---

