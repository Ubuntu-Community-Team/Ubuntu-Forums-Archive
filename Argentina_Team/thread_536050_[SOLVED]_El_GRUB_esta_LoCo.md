---
title: "[SOLVED] El GRUB esta LoCo"
date: 2007-08-27
forum: Argentina Team
---

### Post by leo_rockway on 2007-08-27
Hola gente. A ver si pescan que pasa aca porque esto es muy raro.

Resulta que mi booteo estaba un poco lento (se quedaba como 30 segundos en "reading files needed for boot") y segui esta guia para ver si mejoraba el tiempo: [http://www.guia-ubuntu.org/index.php?title=Inicio_del_sistema](http://www.guia-ubuntu.org/index.php?title=Inicio_del_sistema)

El booteo no mejoro en rendimiento; todo lo contrario, es como dos minutos mas lento ahora despues de haber booteado varias veces (se queda en "Preparing to profile boot sequence...")

ahora, lo raro es que si reedito /boot/grub/menu.lst y saco la palabra profile, la mitad de los demonios no me carga y me tira al login de consola en lugar de cargarme kde. y cuando quiero iniciar kde a mano haciendo "startkde" me tira un error q no llego a ver xq pasa muy rapido. creo q lo que dice es q no puede abrir el display.

lo mas raro es que si hago xinit y luego startkde, kde carga (y el resto de los demonios cargaron tb algunas veces)

la verdad que no se que hacer. quisiera sacar el "profile" pero no se como hacerlo para que todo vuelva a estar como antes.

cualquier ayuda es bienvenida.

saludos y gracias.

---

### Post by faktorqm on 2007-08-27
perdona una cosa, vos usas gutsy? por que el tutorial dice para dapper, tu nick gutsy..... 
aca te dejo el link para reinstalar el grub, que creo que es la opcion mas sana.
sino, primero desinstala grub, desinstala o borra el readahead ese, y luego reinstala. suerte con eso y saludos!!

[http://ubuntu-ar.org/soporte/comos/reinstalar-grub](http://ubuntu-ar.org/soporte/comos/reinstalar-grub)

---

### Post by leo_rockway on 2007-08-27
Hola faktorqm, yo estoy usando Gutsy en este momento y tambien se puede utilizar readahead. El readahead yo lo tenia instalado de versiones anteriores de Kubuntu, no lo instale ahora. Yo no hice un clean install a Gutsy, sino un upgrade. Al momento de leer la guia yo ya tenia readahead instalado, lo unico que hice fue modificar la linea de menu.lst y agregar la palabra profile.

Siguiendo tu consejo reinstale grub (que ahora que me doy cuenta no era realmente necesario porque Grub no era el verdadero problema) y le hice un remove --purge al readahead. Ahora no solo puedo bootear despues de borrar la palabra profile, sino que mi booteo es aun mas rapido que antes de haber hecho todo esto (asi que readahead era el que estaba causando el booteo lento desde un comienzo)

Muchas gracias por tu ayuda.

---

### Post by Hei Ku on 2007-08-27
Una aclaracion, el profile habria que correrlo sin modificar el menu.lst, porque solo hace falta correrlo una sola vez.

Lo que hace el profile es analizar los archivos que se cargan durante el booteo. Como te puede contar cualquier que hizo profiling de un servidor, cuando está activo el sistema es mucho mas lento.

En resumen, hay que correr el profile una sola vez. Para eso basta con reiniciar la maquina, y cuando aparece el menu de grub agregar la opcion de profile. De esa manera se ejecuta esa única vez y la siguiente ya inicia normalmente, y con suerte mucho más rápido.

---

### Post by leo_rockway on 2007-08-27
el problema es que no me dejaba deshabilitarlo despues de hacerlo correr esa unica vez. la siguiente vez que bootee tuve el problema que comente. despues me di cuenta q al volver a agregar profile desde el menu de grub podia volver a bootear pseudo normalmente, pero me tenia que comer todo el profiling de nuevo.

de todas formas desinstalar readahead y olvidarse del profiling soluciono todo.

---

### Post by faktorqm on 2007-08-27
que bueno que lo solucionaste men!! salu2!!

---

