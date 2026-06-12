---
title: "Pantalla Azul"
date: 2007-03-14
forum: Argentina Team
---

### Post by jayflower on 2007-03-14
Resulta que como puse en el post anterior estuve instalando el openchrome y beryl, pero en algun paso algo hice mal porque cuando entro a mi sesion y con el kernel por defecto aparece una pantalla azul!!! y me tira un log de errores enorme. No se como recuperar mi archivo xorg.conf o si se modifico algo en el kernel...porque segui los pasos del wiki de beryl y del wiki de openchrome. Y Perdonen no quiero ser pesada! Nada mas quiero un cubito de regalo el dia de mi cumpleanios. Igual todavia puedo entrar con el modo de recuperacion como root, eso esta bueno.

Gracias.
P.D.: Adjunto el log

---

### Post by divague on 2007-03-14
Trata usando este comando:

$dpkg-reconfigure xserver-xorg

Cuando trates de instalar el driver de tu tarjeta de video o beryl te recomiendo que hagas un backup de tu archivo xorg.conf:

$sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

en caso de que algo slga mal puedes usar el archivo de backup que hiciste

---

### Post by jayflower on 2007-03-14
edite ese archivo... seguramente mi placa no va con XGL. ya le borre el contenido...
/etc/X11/sessions/xgl.desktop

---

### Post by jpmorelli on 2007-03-14
Mejor usá AIGLX, ya viene incluido en el kernel ( ¿ no ? ) y solo hay que instalar un par de cosas y sale andando.
Yo seguí este tutorial y me anduvo bárbaro. Si tenés problemas con los marcos una vez instalado hacete un post que yo también encontré la solución.

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX")

Suerte ! :lolflag:

---

### Post by jayflower on 2007-03-15
si, segui esos pasos pero sigo con el mismo problema cuando quiero entrar a mi kernel... supongo que algo se modifico mal. ya hice un dpkg -reconfigure xserver-org pero solo una vez pude entrar. Y no quiero reinstalar. Lo voy a mirar mas tarde

---

