---
title: "Amarok funcionando mal"
date: 2007-06-21
forum: Argentina Team
---

### Post by DuckMan on 2007-06-21
No se porque, creo que desde que tengo feisty, el amarok no funciona para nada bien, tarda mucho en cargar, cuando quiero ingresar canciones a la playlist se queda agregandolas pero nunca lo logra, y tengo q cerrarlo..

no se tilda, pero funciona terrible. tengo que aclarar que uso gnome, pero no deberia tener nada q ver.. borre la carpeta .amarok de la carpeta home, lo re instale, no se q mas borrar o hacer

si alguien me tira una pista le agradecere (?)

---

### Post by DuckMan on 2007-06-21
disculpen la auto respuesta tan rapida, pero bueno, lo solucione:

el amarok no viene con soporte mp3 por defecto, entonces cargaba tantas canciones a la playlist que se colgaba y no me decia nada.

para agregarle el soporte:

sudo aptitude install libxine-extracodecs gstreamer0.8-mad

---

