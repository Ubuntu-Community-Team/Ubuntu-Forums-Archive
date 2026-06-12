---
title: "Firefox no me redimensiona"
date: 2007-09-06
forum: Argentina Team
---

### Post by niko_3100 on 2007-09-06
Bueno gente hace un par de horas note que el firefox que me descargue desde [www.firefox.com](www.firefox.com) la version 2.7 creo no me redimensiona las paginas de internet a 1280x800. Esto es muy malo ya que pr eso las letras de las paginas se ven chiquititas y juntas y son muy dificiles de leer, lo peor que el mismo firefox en xp (la version windows) si me redimensiona y me adpata las pantallas a 1280x800 y puedo verlas lo mas bien con letra grande y comodo, a alguien mas le paso'? Probe reinstalando el firefox y nada, que podra ser? algun atributo que le tengo que modificar a mano? o algo medio raro para configurarlo? Muchas gracias.

---

### Post by niko_3100 on 2007-09-06
Bueno gente lo soluciones me baje del repositorio un theme para el ubuntu se ve que los iconos por defecto del firefox me achicaban la imagen mostrada en la pantalla poruqe me agrandaba las barras propias del firefox, ese era el problema.

---

### Post by por100pre1 on 2007-09-06
Prueba renombrando tu perfil de usuario:

```
mv /.mozilla/firefox /.mozilla/firefox_respaldo
```

y reinicia Firefox a ver si la ultima version daño tu perfil. Si esto no funciona ponlo todo en su lugar.

```
mv /.mozilla/firefox_respaldo /.mozilla/firefox
```

---

