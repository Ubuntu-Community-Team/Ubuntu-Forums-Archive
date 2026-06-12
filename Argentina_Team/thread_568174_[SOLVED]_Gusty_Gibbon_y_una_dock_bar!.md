---
title: "[SOLVED] Gusty Gibbon y una dock bar!"
date: 2007-10-05
forum: Argentina Team
---

### Post by Mauro22 on 2007-10-05
Alguien de los que esten usando la beta de GG. Conocen alguna dockbar que ande, como AWN??



Salu2 y gracias! :guitar:

---

### Post by nest on 2007-10-05
si, awn me funciona a la perfección.

¿qué error te tira?

---

### Post by Mauro22 on 2007-10-05
AWN te funciono?

Yo la instalè pero no abre.


De donde la sacaste?


Gracias x la rta.!

---

### Post by nest on 2007-10-05
apt-get install avant-window-navigator ?

---

### Post by Mauro22 on 2007-10-05
No me aparecen en los repositorios, ahora salto otra actualizacion. voy a probar cuando termine.


Gracias por la ayuda.

---

### Post by spg76 on 2007-10-05
Awn no está en los repositorios oficiales.
Podés instalarlo dede el repositorio de reocard.
Agregá el siguiente repositorio:
```
deb http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
```
Después:
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
```
Y por último:
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

No está actualizado con lo última versión (tiene la versión bzr78 y  la última es bzr124) pero es la manera más sencilla de instalarlo.
La otra opción es compilar desde Bazaar, que no es muy complicado.
Podés ver más info en [http://awn.danieltiecher.com/](http://awn.danieltiecher.com/)
Saludos.

---

### Post by Mauro22 on 2007-10-05
Gracias, spg76 y nest.


Ahora funciona de maravillas :)

---

