---
title: "Problema con aplicaciones de KDE en Ubuntu 7.10"
date: 2007-10-20
forum: Argentina Team
---

### Post by lordpuppet on 2007-10-20
Buenas, tengo mi nuevisimo ubuntu 7.10 recien instalado. Instalé el amarok y el ktorrent (aplicaciones de KDE) pero ninguna funciona, amarok me da muchos errores y ktorrent ni siquiera abre. Uno de los errores que me da amarok cuando lo quiero iniciar es este:

[[IMG]http://img206.imageshack.us/img206/5301/lalano8.png[/img]](http://imageshack.us)

El error que tira el ktorrent cuando lo ejecuto de la consola es el siguiente:

```
esteban@esteban-desktop:~$ ktorrent
trying to create local folder /home/esteban/.kde/share: Permission denied
trying to create local folder /home/esteban/.kde/share: Permission denied
trying to create local folder /home/esteban/.kde/share: Permission denied
trying to create local folder /home/esteban/.kde/socket-esteban-desktop: Permission denied
trying to create local folder /home/esteban/.kde/socket-esteban-desktop: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/esteban/.kde/socket-esteban-desktop/kdeinit__0'
ERROR: KUniqueApplication: Can't setup DCOP communication.

```

Que es el DCOP? y por que no funciona?

---

### Post by tzulberti on 2007-10-20
Desde una consola escribi: "ls -l .kde"
Fijate que la file de share sea algo del estilo: 

drwx------ 8 tzulberti tzulberti 4096 2007-10-13 00:58 share

Sino es asi, hace lo siguiente:
chmod 700 .kde/share

---

### Post by lordpuppet on 2007-10-20
Parece que esta todo en orden:

```
esteban@esteban-desktop:~$ sudo ls -l .kde
[sudo] password for esteban:
total 4
drwx------ 3 root root 4096 2007-10-19 17:21 share
esteban@esteban-desktop:~$ 

```

hice el chmod de todos modos pero el problema persiste.

---

### Post by mo_x on 2007-10-20
```
sudo chown -R esteban .kde
```

---

### Post by lordpuppet on 2007-10-20
Ahi funciono. Gracias, salieron unos errores que no entiedo que quieren decir, pero la aplicacion funciona:

```
esteban@esteban-desktop:~$ ktorrent
kbuildsycoca running...
kbuildsycoca: WARNING: Parse error in /home/esteban/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/esteban/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
DCOP Cleaning up dead connections.
esteban@esteban-desktop:~$ kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Could not write data
kio (KLauncher): ERROR: SlavePool: No communication with slave.

```

---

