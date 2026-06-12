---
title: "Dios salve al Grub del MBR..."
date: 2006-12-04
forum: Argentina Team
---

### Post by jpmorelli on 2006-12-04
Bueno, por más que lo intenté no lo logré y tuve que terminar reinstalando Ubuntu, por suerte tengo particiones separadas para el raíz y la home.
Pero no puedo entender porque no la hacen más fácil.
La onda fué que cambié el disco por uno más grande y obviamente para pasar todo hice un ghost de uno al otro.
Toda la data paso genial pero al bootear, solo aparecía:
GRUB

Obviamente en este punto pueden decirme millones de cosas para hacer, a mi no se me ocurrió nada mejor que usar el CD de XP, entrar en la consola de recuperación y darle al FIXBOOT. Claro, eso solucionó el XP, pero obvio ! el sistema entraba directamente y solo a él !
Ok, por lo menos volvía a respirar, en ese sistema están todas las fotos, a partir de ahi a recuperar el GRUB para el multibooteo nuevamente. Seguí cuanta guía encontré en el foro, en el wiki, incluso bajé y creé el SuperGrubDisk, pero nada, el sistema daba un error de Input/Output cuando me acercaba a algo por lo menos interesante.
Usé el LiveCD de Dapper, el CD de edgy en modo rescate, monté las unidades, corrí el grub-installer , empezando la instalación y usando la opción de manual partition, dejando sin formatear y saltar hasta el paso de instalación del Grub, NADA ! ](*,) 
Por favor, se viene el VISTA y seguramente mucha gente como yo que todavía no puede dejar Microchot va a tener que instalarlo, alguna forma de hacer esto y que funcione ?
No es urgente ya que ya reinstalé y ya tengo todo andando de vuelta, pero para la próxima...
Sory por lo extenso ;)

---

### Post by Nemesis Teufel on 2006-12-04
Bienvenido al club de los "Grublematicos" :-?

---

### Post by DuckMan on 2006-12-05
me sumo

es increible como no solucionan algo tan... basico diria yo

ya es el 2do reinstall q tube q darle al ubuntu, y eso q intente con TODO, me da errores ilogicos

---

### Post by Nemesis Teufel on 2006-12-05
Me parece que no es un problema de Ubuntu.. es una cagada que nos mandamos nosotros..no? :P

offtopic: wii 100 post! :KS

---

### Post by DuckMan on 2006-12-05
depende el caso!

todo es una cagada q nos mandamos en general, pero deberia ser de facil configuracion

te juro q le mande grub, root (hda0) y se negaba

despues en la instalacion adivina donde lo puso.. inentendible

obviamente mientras menos toquemos eso mejor :P

---

### Post by jpmorelli on 2006-12-06
Debería ser algo tan simple como bootear con el CD de Linux y que exista la opción "Restaurar Grub", escanea las particiones y discos, muestra lo que hay, preview del menú de arranque y si te gusta, DONE !
Si ya sé, hacelo vos y listo, no tengo idea como es, pero solo es una sugerencia que creo que dejaría mucho más tranquila a la gente que todavía no puede dejar de una vez por todas el maldito Guindow :evil:

---

