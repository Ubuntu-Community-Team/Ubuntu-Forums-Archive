---
title: "Problema con compiz desde beryl-manager"
date: 2007-02-17
forum: Argentina Team
---

### Post by felipelerena on 2007-02-17
Hoy accidentalemente cambie en el menu de beryl-manager el gestor de ventanas y puse compiz, y se fue todo al garete, se cargó el gestor de ventanas y se puso la pantalla en blanco (NO en negro).
cada vez que reiniciaba X me aparecia eso por que cargaba beryl-manager por defecto.

alguien me habia contado que le paso y yo le di una solucion muy compleja de tocar a mano la configuraciond e las sesiones y etc...

pero como ahora el problema me paso a mi me puse a buscar una solucion en serio, facil y para cualqueir "hijo de vecino", quiera decir lo que quiera decir esa muletilla

la solucion a cuando te pasa eso:
vas a alguna consola (lease ctrl +alt + F1 al 6) y escribis esto:

```
metacity --display :0 --replace
```ahi vuelve todo a la normalidad, volves al display de X y listo, cambias nuevamente a tu gestor de ventanas estable favorito.

---

### Post by bichopro on 2007-02-17
Rambien podias entrar por la sesion de nome segura en gdm...
gracias por la info

---

### Post by felipelerena on 2007-02-18
no, eso no funciona.
es lo primero que probé

---

