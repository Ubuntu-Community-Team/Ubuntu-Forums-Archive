---
title: "[SOLVED] Kubuntu arranca con pantalla negra"
date: 2008-01-09
forum: Argentina Team
---

### Post by aregnando on 2008-01-09
Hola a todos, bueno finalmente instalé Kubuntu en mi máquina luego de probar varios live CD y ya que esta distro es la que más me gustó, me decidí. La instalación corrió perfecta, dejé mi anterior SO en una partición de 40 Gb. e instalé Kubuntu en una partición nueva de otros 40 Gb. hasta acá todo Ok. Luego arranqué Kubuntu y todo anduvo muy bien, pude activar los controladores restringidos para mi placa de video (Nvidia FX 5200) sin problema.
Al apagar la máquina y tratar de arrancar Kubuntu me apareció el Grub, luego el logo de Kubuntu con la franja azul y de ahí en mas todo negro.
Busqué algunas soluciones en Google pero aún no he dado con la respuesta adecuada aí que si alguien me puede tirar una soga va a ser más que bienvenida ya que estoy ansioso por usar mi Kubuntu.
Gracias a todos.

---

### Post by faktorqm on 2008-01-10
Bueno, es raro la verdad, pero vamos a ver que podemos hacer. Para empezar, podes probar de entrar en safe mode desde el grub. si asi sigue sin entrar, con el grub edita la linea del kernel que arranca y en una parte que dice "splash" pone "nosplash" para ver cual es el error. Si vos ves que te arranca pero no te muestra nada, y supuestamente queda en la pantalla donde pones user y pass, pero vos no la ves, apretas CTRL + ALT + F3 y te da una consola (siempre suponiendo ke arranca bien) ahi metes usuario, contraseña, y para probar, yo empezaria por poner el driver en vesa a ver si es eso o es otra cosa. eso lo haces con "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.con_backup" y luego "sudo nano /etc/X11/xorg.conf" y en la seccion driver pones "vesa" o "nv". grabas y cuando salis pones "sudo /etc/init.d/gdm restart" y te fijas si te muestra la pantalla de logueo. Sino postea a ver cual de todas las soluciones usaste y cual fue el resultado. Salu2!

---

### Post by hernan blau on 2008-01-10
Lo que no me quedó claro es si te arranca o no. Luego de ponerse negro esperá 5 minutos y contanos si finalmente arranca. Suerte

---

### Post by aregnando on 2008-01-14
Hola, creo que ya se lo que pasó,Luego de instalar Kubuntu puse para actualizar y entre estas actualizaciones había un incremento de versión que falló en descargar, luego de eso vino la falla mencionada de arranque con pantalla negra.
Reinstalé el sistema y obvié este paso y por suerte estoy usando en este momento mi nuevo SO.
Muchas gracias faktorqm y hernan blau por su ayuda.

---

