---
title: "y donde está el Grub?..."
date: 2007-10-31
forum: Argentina Team
---

### Post by atari130xe on 2007-10-31
Esta mañana instalé via Synaptic Xubuntu-desktop en Ubuntu 7.10 y cuando reinicio la maquina, entró directamente a ubuntu sin aparecer el menú Grub donde tmb tengo en la primera particion al XP, alguien tiene una idea de que pudo haber pasado? al menos como tener nuevamente el Grub con todas las opciones, gracias!

---

### Post by avik on 2007-10-31
Lo siento, no hablo español muy bien, pero ¿qué dice tu /boot/grub/menu.lst?

```
cat /boot/grub/menu.lst
```

---

### Post by sajnox on 2007-10-31
En primer lugar segui el post anterior, fijate que hay en tu grub, si no sabes, postea el contenido para que te podamos dar una mano, sino podes seguir [esta]("http://nand-magazine.net/2006/07/30/recupera-el-grub-que-te-ha-quitado-windows/") guia.

Saludos,

---

### Post by Timbis on 2007-10-31
proba con el super grub disk... es super de verdad
sino proba volviendolo a instalar, hay un par de tutos por ahi.

---

### Post by atari130xe on 2007-11-01
Solucionado: edite el menu list agregue las entradas que tenia y ahora funciona el grub.

---

