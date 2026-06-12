---
title: "videos youtuve"
date: 2008-01-12
forum: Argentina Team
---

### Post by andy_91 on 2008-01-12
bueno tengo un problemita con youtube

lo que pasa es que cuando abro un linck hacia un video de youtube tengo que reiniciar?

alguien tuvo el mismo problema?

(aclaracion: se tilda el ordenador)

---

### Post by clasificado on 2008-01-12
Buenas!

Empezemos con lo básico, ¿me contestarias estas preguntas?:
1) ¿Que versión de flash tenés y como la instalaste?
2) ¿Que navegador estás usando?
3) ¿Cual es la versión de tu distribución?
4) ¿Andan otras páginas que necesiten flash?
5) ¿Tenes puesto el compiz fusion o alguno de sus amigos? ¿Probaste apagándolo?
6) "lo que pasa es que cuando abro un linck hacia un video de youtube tengo que reiniciar?" ¿¿eeeehhh?? ¿Es una pregunta, una afirmación o una aclaración? ¿podrias volver a redactarlo?

Clasificado

---

### Post by andy_91 on 2008-01-12
1) ni idea se que una vez me pidio instalar un flash player el firefox y le di que si. lo raro es que me dio a elegir dos el adobe y otro. elegi el otro

2)firefox

3)xubuntu 7.10

4)nose que otras paginas nesesitan flash :P (fotolog y softonic andan y con esas me salio el cartelito)

5):( ni idea de lo que es hace 4 dias que uso linux XD

6)facil se tillda el sistema y tengo que reiniciar no hay mucha historia:

abro youtuve
busco un video
abro el video
se tilda el pc
Reset.

---

### Post by pablo0469 on 2008-01-12
Si te esta saliendo el cartelito que necesitas instalar plugins para ver correctamente esas paginas, creo que tenes mal instalado Flash, y los videos de Youtube estan recontra embebidos con este.

Te aconsejaria que vayas a Sistema -> Administracion -> Gestor de Paquetes Synaptic, y en la opcion "buscar" pongas "flash" (sin comillas), y marques para eliminar un paquete que se llama "flashplugin-nonfree". 

Despues abri una terminal y escrbi:

sudo aptitude purge ~c

Con esto, te va a desinstalar definitivamente ese paquete (y otros que quizas hayas desistalado a medias).

Y despues, instala Flash a mano. Fijate unas paginas atras un post que se llama "Instalar Flash 100% Garantizado", ahi hay un link para hacerlo en pocos pasos (lastima que no se como miercoles se pone el link que te lleve a ese post aca...).

"ubuntu-restricted-extras" suele dar inconvenientes para instalarlo, como fue mi caso.

Saludos y ojala te sirva. Cualquier cosa postea de nuevo.

---

### Post by steve_ignorant on 2008-01-12
buenas... a mi me funciono perfectamente el flash, cuando lo pidio el firefox, solo que baje el adobe... quizas puede ser ese el problema... 

estoy usando el ubuntu 7.06

---

### Post by andy_91 on 2008-01-12
> **steve_ignorant said:**
> buenas... a mi me funciono perfectamente el flash, cuando lo pidio el firefox, solo que baje el adobe... quizas puede ser ese el problema... 
yo baje el otro y anda bien
eso del cartel fue hace unos dias pero bueno hace unos 5 dias que uso linux

---

### Post by pablo0469 on 2008-01-13
Hola, Andy, en tu lugar probaria reinstalando Flash, el unico ingrediente en tu PC que debes tener bien, pues el motor para ver los videos lo dan ellos, es decir, es un sistema propio que vos solo lo ejecutas desde internet, no creo que sea un problema de Ubuntu.

Saludos.

---

### Post by atari130xe on 2008-01-13
Ayer hice una reinstalacion de Ubuntu 7.10 cuando entraba a una pagina que necesitaba Flash me salia el gestor de pluguins "Ubufox" que viene por defecto en Firefox con Ubuntu, le dí a "instalar" y todo bien pero cuando reiniciaba el navegador e intentaba ver el sitio me volvia a salir que necesitaba el plugin. Solucion: abrí el navegador, fui a complementos, deshabilité Ubufox y cerré el navegador, lo volvi a abrir, entré en el sitio que necesita flash y me volvio a salir el cartel de instalacion, le di "instalar plugin" lo descargó, cerré la ventana, la volvi abrir entré en el sitio y todo salió de 10.

---

### Post by vk-cdg on 2008-01-14
Yo tuve hace unos días un problema también con flash.
Cuando hice mi instalación de Ubuntu 7.10, al momento de instalar el flash player elegí el Gnash por ser libre. Todo andaba bien hasta que tuve que mirar ciertas web hechas enteramente en flash. Ahí es donde trulaba y no me habilitaba links que estaban ahí. 
Desisntalé el gnash e instalé el flash de Macromedia. Acá te dejo los pasos que hice yo ayudado por faktorqm

[http://ubuntuforums.org/showthread.php?t=660973](http://ubuntuforums.org/showthread.php?t=660973)

---

### Post by aregnando on 2008-01-28
Hola probá con este tutorial que a mi me resolvió el problema.

[http://jgutierrez.wordpress.com/2008/01/07/problema-con-plugin-de-flash-en-firefox-ubuntu/](http://jgutierrez.wordpress.com/2008/01/07/problema-con-plugin-de-flash-en-firefox-ubuntu/)

---

