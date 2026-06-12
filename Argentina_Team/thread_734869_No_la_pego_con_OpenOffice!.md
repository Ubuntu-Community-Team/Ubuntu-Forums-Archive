---
title: "No la pego con OpenOffice!"
date: 2008-03-25
forum: Argentina Team
---

### Post by h9005 on 2008-03-25
Lo instalé en mi ubuntu studio, pero se colgaba apenas intentaba guardar. Lo instalé y desinstalé. Nada. Lo desinstalé desde los repositorios. Tuve que descargar de vuelta el paquete. Se instaló en inglés (le entiendo pero me queda más cómodo español, además a la máquina no la uso yo solo). Pero sigue colgandose al guardar, y también al imprimir en red con una impresora en una maq con winxp. Como instalo la versión en español de vuelta?

---

### Post by Vecktor on 2008-03-25
Para ponerlo en español tenes que ir a Sistema-> Administración-> Soporte de Idiomas mientras estas conectado a Internet, y teniendo marcado español en la lista de idiomas. Te va a preguntar si queres bajar los paquetes en español para todos tus programas.

Los otros problemas no sabría respondertelos, ya que no tengo experiencia con ellos.

---

### Post by faktorqm on 2008-03-25
Primero hago 

```
aptitude search openoffice
```

y entre la lista de resultados aparece:

openoffice.org2-l10n-es

Paquete en español para openoffice.org 2

entonces hago

```
sudo apt-get install openoffice.org2-l10n-es
```

y listo! Salu2!

---

### Post by h9005 on 2008-03-25
Gracias voy a chequearlo.

---

