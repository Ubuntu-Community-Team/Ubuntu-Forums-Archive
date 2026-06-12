---
title: "problemita con flash en mozilla firefox"
date: 2007-02-06
forum: Argentina Team
---

### Post by jajajavi on 2007-02-06
antes que nada, les comento que tengo ubuntu dapper en un **amd64**, por lo cual tuve que hacer un par de manejes para poder instalar el plugin para ver flash con firefox. de hecho uso el **swiftfox** que sino me equivoco es como una versión optimizada para amd64 (o algo así). entonces, no sé muy bien cómo conviven el firefox (en español) y el swiftfox (in english). resulta que cada tanto el plugin del flash deja de andar y me aparece el firefox en español. esto me paso hoy cuando creé una cuenta de usuario para mi hermano en esta misma pc. por el momento mi hermano no podrá ver youtube, aunque puede suceder que inicia su sesión y funciona. es extraño, tal vez metafísico... ¿alguien sabe algo?

---

### Post by beuno on 2007-02-06
Cada usuario tiene su propio perfil, con lo cual tiene sus propios settings de firefox.
Debes haber instalado flash en la carpeta de TU home, y tu hermano no la tiene.
Podes copiar la carpeta ~/.mozilla al home de tu hermano y deberia funcionar todo igual.

---

### Post by jajajavi on 2007-02-06
lo hice con [FONT="Courier New"]**gksudo nautilus**[/FONT], arrastrando (y reemplazando) la carpeta en cuestión, pero tanto firefox como swiftfox dejaron de andar...

---

### Post by beuno on 2007-02-06
Eso es porque quedo root como dueño de la carpeta
hace un ```
sudo chown el_usuario_de_tu_hermano .mozilla -R
```
o en el peor de los casos ```
sudo chmod 777 .mozilla -R
```

---

### Post by jajajavi on 2007-02-09
en mi ubuntu conviven el **firefox** (comando: firefox %u) y el **swiftfox** (comando: firefox32), el segundo optimizado para hacer andar el plugin flash en 64bits. quisiera eliminar el primero o bien dejar al swiftfox como predeterminado, ya que no puedo controlar totalmente cuándo se abre uno u otro, por lo que cada vez que inicio checkea actualizaciones y a veces no anda el plugin flash, entonces tengo que cerrar y abrir el swiftfox (clickeando en el ícono correspondiente). ¿es posible eliminar el firefox dejando el swiftfox? en fin, flash es un dolor de huevo'...

---

### Post by cocotu on 2007-02-09
jaja yo baje flash player directamente de adove.com y me funciona de lo mejor con todos los usuarios. Lo que pasa es que tienes que instalalarlo en /usr/local si no me equivoco, de esta manera todos los usuarios tendran derecho a usarlo.

---

