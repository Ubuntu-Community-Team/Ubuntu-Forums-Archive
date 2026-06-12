---
title: "Imposible squirrelmail en español"
date: 2007-05-14
forum: Argentina Team
---

### Post by marcelinux on 2007-05-14
Tengo instalado Squirrel 1.4.9 en Ubuntu 7.04, y no logro que muestre las páginas en español, ni siquira siguiendo los pasos de la página de Squirrel, alguien tuvo la suerte de hacerlo? muchas gracias

---

### Post by ubnuturero on 2007-05-17
Ya que instalaste  squirrelmail-locales

sudo  locale-gen  es_ES

configura  tu squirrelmail  con 
sudo /etc/squirrelmail/conf.pl

y en el lenguaje selecciona  es_ES
reinicia el apache y listo

---

