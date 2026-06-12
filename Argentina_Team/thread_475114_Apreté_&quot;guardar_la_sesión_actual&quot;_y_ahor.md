---
title: "Apreté &quot;guardar la sesión actual&quot; y ahora nada inicia."
date: 2007-06-15
forum: Argentina Team
---

### Post by valucha on 2007-06-15
[COLOR="DarkOrchid"]Tuve un problema con Beryl, que se me iniciaba en modo "metacity" y tratando de arreglarlo puse en "sistema>preferencias>sesiones" la opción de "guardar la sesión actual"...
Y ahora el tema es que cuando inicio, 1ero se me queda la splash screen congelada hasta que le hago click encima.... y encima, no me inicia NADA...
pero al rato, pasando n determinado tiempo (2 o 3 minutos) se me inicia TODO!...
por más que ya lo haya iniciado manualmente.


Probé borrando la carpeta .config, que estña en el home donde se guarda el "autostart" pero no hubo caso,m no se reseteó eso.

tienen idea=?
gracias!
[/COLOR]

---

### Post by lavaramano on 2007-06-16
no.
fijate que en .config se guardan otras configuraciones ademas de las de gnome.
para configs de gnome solamente tenes:
> .gconf/ .gnome2_private/ .gconfd/ .gnome/ .gnome2/

fijate en /usr/share/gnome/ los archivos default.session y default.wm o por alguno de esos dirs.

o la solucion tinga(?):  
> dpkg-reconfigure -a 

---

### Post by valucha on 2007-06-17
> dpkg-reconfigure -a
[COLOR="DarkOrchid"]¿para qué sería esto? poner todo desde 0?[/COLOR]

---

### Post by lavaramano on 2007-06-19
reconfiguras todos los paquetes.
no te los desconfigura, ni te borra la configuracion que tenias antes.

al menos a mi nunca me paso que rompa todo.
asi solucione miles de errores rompeb*las, como iniciar el sistema y que gdm crashee.

---

### Post by valucha on 2007-06-21
[COLOR="DarkOrchid"]Ok, sinceramente reinstalé...era más rápido que tratar de solucionarlo.
Sí, ya sé, así no aprendo nada, pero ahroa tengo muchas pruebas.
Perdíon por la molestia y gracias por el comentario y la explicación [/COLOR]

---

### Post by lavaramano on 2007-06-22
hubieras borrado / reinstalado el gnome :P

---

