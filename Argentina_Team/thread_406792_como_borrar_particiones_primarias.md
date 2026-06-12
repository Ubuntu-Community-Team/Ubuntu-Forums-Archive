---
title: "como borrar particiones primarias?"
date: 2007-04-11
forum: Argentina Team
---

### Post by atari130xe on 2007-04-11
tengo 4 particiones primarias en mi HD, y deseo borrar 1 cual seria el procedimiento?

---

### Post by DoubleQuadword on 2007-04-11
Para este tipo de procedimientos existe **gparted** el cual provee gran funcionalidad en lo que respecta a manejo de particiones.

Formas de obtenerlo:

1. Desde Ubuntu:

```
sudo aptitude install gparted
```

2. Desde el LiveCD:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

3. Desde el instalador del mismo Ubuntu.

Recomiendo usar cualquiera de las últimas dos opciones para realizar esta tarea, ya que evita que debas desmontar la partición. (Aunque depende de que te sea más cómodo).

Documentación: [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php) .

Saludos.

---

