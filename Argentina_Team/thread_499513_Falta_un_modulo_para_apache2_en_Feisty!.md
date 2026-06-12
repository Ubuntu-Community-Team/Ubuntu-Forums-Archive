---
title: "Falta un modulo para apache2 en Feisty!"
date: 2007-07-12
forum: Argentina Team
---

### Post by camellito on 2007-07-12
Hola amigos, pues eso. Extrañamente falta el modulo module_security en Feisty. Acabo de preguntar en el foro en Ingles pero no he tenido suerte. 

Este es el post: [http://ubuntuforums.org/showthread.php?t=499373](http://ubuntuforums.org/showthread.php?t=499373)

Alguien ha podido hacerlo funcionar o conseguir algun deb para feisty?

Gracias.

---

### Post by beuno on 2007-07-12
Ese modulo ni siquiera esta en Debian, asi que asumo que hay algun problema significante con el.

Hay .debs para Debian que quizas te funcionen en: [http://ftp.debian-unofficial.org/debian/pool/main/liba/libapache-mod-security/](http://ftp.debian-unofficial.org/debian/pool/main/liba/libapache-mod-security/)

---

### Post by camellito on 2007-07-12
Gracias por contestar beuno, el problema es que el "**config**" de apache2 en debian es el **httpd.conf** y en feisty el **apache2.conf**... de modo que termino con un lio mas grande que una casa a la hora de intentar compilar el modulo manualmente. Que raro que nadie haya preguntado esto antes, no?

---

