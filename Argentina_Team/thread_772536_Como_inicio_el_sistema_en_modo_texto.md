---
title: "Como inicio el sistema en modo texto?"
date: 2008-04-28
forum: Argentina Team
---

### Post by mrchelo2002 on 2008-04-28
Hola que tal. Otra vez aquí preguntando.

Cuando comienza a cargar el sistema, aparece la imagen de Ubuntu y la barra de progreso de carga. Tengo un problema que nose cual es pero en ese momento el monitor muestra un cartelito indicando que la señal de video esta en una frecuencia extraña, y se mantiene hasta el momento en que aparece el escritorio.

Lo que yo quisiera hacer es que en vez de mostrar esa pantalla con la barrita, me muestre en modo texto todas las cosas que esta cargando.
¿Cómo se puede hacer?

Muchas gracias.
Chelo.

---

### Post by Mauro22 on 2008-04-28
Cuando estas en el GRUB selecciona la opcion de Ubuntu y apreta la 'e' para editar.

Busca la palabra splash y cambiala por no-splash

despues dale a la tecla 'b' para bootear.


Si te andubo bien, vas a tener que hacer los cambios en el archivo /boot/grub/menu.list para que queden para siempre.

:guitar:

---

### Post by mrchelo2002 on 2008-04-28
Gracias Mauro22, anduvo perfecto!!.
Saludos

Chelo

---

