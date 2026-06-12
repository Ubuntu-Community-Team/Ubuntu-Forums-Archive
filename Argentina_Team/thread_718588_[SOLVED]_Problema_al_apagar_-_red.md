---
title: "[SOLVED] Problema al apagar - red"
date: 2008-03-08
forum: Argentina Team
---

### Post by Tosh78 on 2008-03-08
Hola! Espero que puedan ayudarme con este problemita que tengo.
Estoy usando Ubuntu 7.10 con un dual con wingarch XP. Ayer instale el ntfs-config, y funciono todo perfecto, pero cuando decido apagar, me surge un problema. Le doy al boton de apagar, aparece la ventana con la linea naranja de Ubuntu que se va descargando y poniendo negra, pero despues de eso, aparecen los siguientes carteles y la maquina queda tildada. Es decir, no se apaga. Alguien tiene alguna idea como puedo resolver esto?
Los carteles a los que me refiero dicen esto:

NetworkManager: <info> Desactivating device eth1.
NetworkManager: <info> SUP: sending command 'DISABLE_NETWORK0'.

Antes de instalar el ntfs-config funcionaba todo perfecto.

---

### Post by Tosh78 on 2008-03-08
Bueno, ya lo logre solucionar con algo que encontre en otro foro por un problema diferente.
Lo posteo por si a alguien le sirve.
Primero: cuando arrana Grub, apretar ESC.
Elegir Kernel y apretar E
Elegir Kernel boot y apretar E
al final de la linea escribir acpi=force y darle ENTER
apretar B

Si funciona, para que eso que agregamos se cargue cada vez que iniciamos Ubuntu, hacemos lo siguiente:
Al abrir la consola tipeamos sudo gedit /boot/grub/menu.lst
nos va a pedir la password, la ponemos y continuamos.
Una vez adentro del archivo buscamos la linea que comienza con # defoptions y agregamos al final acpi=force.
Le damos grabar y cerramos.
Supuestamente, para que nos tome el cambio en ese momento tenemos que hacer un reload con sudo update-grub pero a mi no me funciono. La proxima vez que inicie, ahi si funciono todo a la perfeccion.

---

