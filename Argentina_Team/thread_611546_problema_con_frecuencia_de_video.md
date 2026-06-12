---
title: "problema con frecuencia de video"
date: 2007-11-13
forum: Argentina Team
---

### Post by Skavenger on 2007-11-13
buscando encontre muchos posts donde hablan de editar el archivo /etc/X11/xorg.conf para solucionar este problema, pero no dicen como hacerlo exactamente u.u

el tema es que en windows xp me permitia seleccionar hasta una frecuencia de 85hz, pero aca en ubuntu solo me deja hasta 66hz y me esta rompiendo los ojos mal -.-

la resolucion que uso es 1600*1200 con un monitor flatron ez t910b y una geforce 5200 128mb

si windows me permite usar una frecuencia mas alta, supongo que aca tbn deberia permitirme, solo que no se como solucionar esto =P

espero me puedan ayudar

gracias!

---

### Post by vk-cdg on 2007-11-13
Editá el archivo xorg.conf y al lado de la resolución de pantalla que estás usando ponele la frecuencia de refresco deseada.
Por ejemplo 1600*1200@85

Antes no te olvides de hacer un backup de tu xorg.

---

### Post by sajnox on 2007-11-13
A mi me paso lo mismo con mi monitor y reconfigurando el xorg automaticamente me lo detecto sin problemas

1) Backup del xorg

```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.back
```

2) Reconfigurar el xorg automaticamente

```
 sudo dpkg-reconfigure xserver-xorg
```

ctrl + alt + backspace y reinicias las X, si no funciona y queres volver a lo que tenias

```
 sudo mv /etc/X11/xorg.back /etc/X11/xorg.conf
```

Y volves a reiniciar las X ctrl + alt + backspace

Contanos si funciona

Saludos

---

### Post by Mafber on 2007-11-13
Hola Skavenger!! Te cuento que a mi en frecuencia me dice 50 hz pero cuando me fijo en la información que me da el monitor esta trabajando en 85hz. Suerte!!!

---

