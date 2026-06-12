---
title: "script??"
date: 2007-03-15
forum: Argentina Team
---

### Post by tzulberti on 2007-03-15
Hola. Lo que quiero hacer es lo siguiente: tengo cerca de 40 imagenes sacada por una maquina de foto, y las quiero bajar en peso (pesan cerca de 2.5mb cada una) y tamaño (son de 1600x1024). Hay alguna forma de hacer algun script para que me haga eso automatico?

Saludos,
TZ

---

### Post by lavaramano on 2007-03-16
primero bajate al imagemagick

> sudo aptitude install imagemagick

despues de eso, haces un archivito bash (imagenes.sh, por ej) le das permisos de ejecucion (chmod 755 o chmod +x)

el codigo:
> 
#!/bin/bash
for f in `ls`; do convert $f -resize 640x480 $f; done


obviamente al script lo metes en el directorio donde estan las imgs

btw, aca este chabon pone un par de ejemplos mas : 
[http://www.userlinux.net/1008_bash_tip_operaciones_con_imagenes](http://www.userlinux.net/1008_bash_tip_operaciones_con_imagenes) (de ahi saque al script, pero lo modifique un toque)

aca tenes mas info sobre el convert
[http://linux.about.com/od/commands/l/blcmdl1_convert.htm](http://linux.about.com/od/commands/l/blcmdl1_convert.htm)

saludos

---

### Post by tzulberti on 2007-03-16
Muchisimas gracias por la data....

---

