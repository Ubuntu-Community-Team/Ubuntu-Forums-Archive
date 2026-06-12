---
title: "No se inicia modo grafico, queda en terminal"
date: 2007-08-24
forum: Argentina Team
---

### Post by djthree on 2007-08-24
Hola,

Tuve un problema en el cual no se inciaba el modo gráfico para poder loguearse en el sistema, solo quedaba la ventana de texto asi:

```
username@ubuntu:~$
```

buscando en internet encontré un buen tutorial para solucionar problemas de este tipo, bien concreto y facil de entender:

[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

(esta en ingles pero se entiende fácil)

Lo dejo acá, para los que tengan el mismo problema lo solucionen facilmente.

Saludos!

---

### Post by por100pre1 on 2007-08-24
Mi sugerencia para todos los usuarios aqui es prevenir antes que tener que remediar.

Si tu instalacion de Ubuntu se ve correctamente haz una copia de respaldo de xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_respaldo
```

Para usar el respaldo:

```
sudo cp /etc/X11/xorg.conf_respaldo /etc/X11/xorg.conf
```

---

### Post by djthree on 2007-08-24
Si lo hubiera sabido antes!!!
Gracias!!

---

