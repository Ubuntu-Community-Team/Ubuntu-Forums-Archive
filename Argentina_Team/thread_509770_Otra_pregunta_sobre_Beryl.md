---
title: "Otra pregunta sobre Beryl"
date: 2007-07-25
forum: Argentina Team
---

### Post by Darth Trix on 2007-07-25
Se que todos están cansados del infinito circulo de preguntas sobre Beryl (es más yo soy uno de ellos) pero la verdad es un chiche lindo y se merece todas las vueltas que hay que dar, también se que mi pregunta es un poco básica y que para estos momentos tendría que ser capaz de resolverlo  solo pero no se me ocurre como así que aquí les va: ¿alguien tiene idea como hacer que el Beryl arranque de entrada cuando se carga KDE?

---

### Post by kowal on 2007-07-26
La manera más sencilla de ejecutar aplicaciones al inicio de KDE es copiar un acceso directo o un simple script en bash que ejecute **beryl-manager** en **~/.kde/Autostart**. 

Algo así:

```
cd ~/.kde/Autostart
```

```
sudo nano beryl-script.sh
```

Y le ponés:

```
#! /bin/sh
beryl-manager &

```

Grabás con Control+O y salís con Control+X.
Y le dás permisos para ejecutarse:

```
sudo chmod +x beryl-script.sh
```

---

