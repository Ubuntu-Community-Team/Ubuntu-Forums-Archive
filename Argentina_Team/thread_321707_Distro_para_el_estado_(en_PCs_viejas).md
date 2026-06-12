---
title: "Distro para el estado (en PCs viejas)"
date: 2006-12-19
forum: Argentina Team
---

### Post by Hex_Mandos on 2006-12-19
Hoy me di una vuelta por el concejo. Para los que no saben, soy una especie de asesor ad-honorem de una concejal en el partido de Vicente López, y estoy tratando de convencerla de que presente un proyecto para migrar todas las máquinas de la administración municipal a software libre. Lo de convencer no lo digo porque sea una power user de Windows ni nada parecido, sino porque no tiene mucha idea del tema. Hoy justo no estaba en su despacho, y la PC se estaba usando bastante (hay una máquina para 5 personas en una oficinita de 10m2...), cosa que resetearla para mostrar un LiveCD en funcionamiento era imposible. Igualmente en un momento en que estuvo libre me metí en el panel de control, y me di cuenta de que hay un problemita: las máquinas son Pentium II con 128 megas de ram, así que los cds de Ubuntu y Kubuntu (de Shipit, para parecer mas serio) que tenía encima me los iba a tener que tragar, junto con la vergüenza de tratar de promocionar un SO que no andaba en esa maquina.

Igualmente, fui preparado: ayer armé un miniCD de DSL (Damn Small Linux, pesa sólo 50 megas) que andaría bárbaro en esas máquinas, pero me parece que para el target al que apunto no va a ser lo mejor. A mi Fluxbox me sirve como escritorio, pero a gente que no tiene mucha idea le va a parecer un poco rústico. Evidentemente no me interesa que los concejales usen Beryl, pero preferiría mostrarles algo que verdaderamente pueda competir con Windows. Alguien tiene idea de otra distro fácil y liviana para ese nivel de hardware? Funcionará Xubuntu? Ubuntu Lite (con icewm) parece muertísimo...

Si alguien me puede recomendar una distro liviana, fácil, y medianamente vistosa, gracias.

---

### Post by elgatogordo on 2006-12-19
> **Hex_Mandos said:**
> Hoy me di una vuelta por el concejo. Para los que no saben, soy una especie de asesor ad-honorem de una concejal en el partido de Vicente López, y estoy tratando de convencerla de que presente un proyecto para migrar todas las máquinas de la administración municipal a software libre. Lo de convencer no lo digo porque sea una power user de Windows ni nada parecido, sino porque no tiene mucha idea del tema. Hoy justo no estaba en su despacho, y la PC se estaba usando bastante (hay una máquina para 5 personas en una oficinita de 10m2...), cosa que resetearla para mostrar un LiveCD en funcionamiento era imposible. Igualmente en un momento en que estuvo libre me metí en el panel de control, y me di cuenta de que hay un problemita: las máquinas son Pentium II con 128 megas de ram, así que los cds de Ubuntu y Kubuntu (de Shipit, para parecer mas serio) que tenía encima me los iba a tener que tragar, junto con la vergüenza de tratar de promocionar un SO que no andaba en esa maquina.

Igualmente, fui preparado: ayer armé un miniCD de DSL (Damn Small Linux, pesa sólo 50 megas) que andaría bárbaro en esas máquinas, pero me parece que para el target al que apunto no va a ser lo mejor. A mi Fluxbox me sirve como escritorio, pero a gente que no tiene mucha idea le va a parecer un poco rústico. Evidentemente no me interesa que los concejales usen Beryl, pero preferiría mostrarles algo que verdaderamente pueda competir con Windows. Alguien tiene idea de otra distro fácil y liviana para ese nivel de hardware? Funcionará Xubuntu? Ubuntu Lite (con icewm) parece muertísimo...

Si alguien me puede recomendar una distro liviana, fácil, y medianamente vistosa, gracias.

fijate en [www.distrowatch.com](www.distrowatch.com)

---

### Post by Hex_Mandos on 2006-12-19
Estuve mirando Distrowatch, pero las distros que ubico son en general mas pesadas que lo que necesito (o, en el caso de DSL, mas básicas).

Recién probé instalar xubuntu-desktop y icewm. Xfce me gustó bastante, no creo que haya diferencia con Gnome para los usuarios a los que estoy apuntnado. Aparentemente, Xubuntu debería funcionar en la máquina que hoy estuve mirando, así que voy a preparar un LiveCD para probarlo un día de estos. Igual, si alguien conoce una opción mejor, chiflen.

---

### Post by spg76 on 2006-12-19
Xubuntu debería funcionar bien. Incluso en la [página oficial]("http://www.xubuntu.org/get") dice que funcionaría con 64 MB RAM, aunque altamente recomendado usar por lo menos 128 MB.
Otra distro que podes probar, ya que decis que no tenes problemas con Fluxbox, es [Fluxbuntu]("http://fluxbuntu.org/"), que es una derivado de Ubuntu aunque no es oficial (igual usa los repositorios de Ubuntu)
Espero que te sirva alguno de estos datos.
Saludos.

---

### Post by Hex_Mandos on 2006-12-19
No, con Fluxbox yo no tengo problemas, es verdad, pero no se lo instalaría a alguien recién salido de Windows sin mucha idea. Me pareció un poco básico y escasamente user-friendly... bárbaro para tener en DSL, pero no para "vender" Linux o la idea de software libre en general.

Supongo que voy a probar con Xubuntu, xfce me pareció bastante bueno. Ahora, instalar el paquete xubuntu-desktop me cambió la pantalla de login por la de Xubuntu... Probé sacando el xfce, reinstalando ubuntu-desktop (todo via aptitude), y nada. Alguien sabe como volver al login de Gnome/Ubuntu? A mi no me jode, pero esta máquina es compartida y se me ocurre que va a descolocar a mi vieja y a mi hermano. Ya bastante raro les parece que cuando carga dice Kubuntu, de cuando instalé KDE, así que no quiero marearlos mas.

EDIT: Ya lo logré, usando un tutorial de psychocats.net.

---

### Post by jpmorelli on 2006-12-19
Vector LInux o Damn Small LInux ?

---

### Post by DuckMan on 2006-12-19
en esas pcs el xubuntu no va como piña? probalo y decinos q tal :O

---

### Post by Hex_Mandos on 2006-12-20
> **jmorelli said:**
> Vector LInux o Damn Small LInux ?

DSL no. A mi me gusta, pero si tuvieras que venderle Linux a alguien que no tiene idea y siempre usó Windows, le darías una distro con Fluxbox como WM? Yo lo probé el otro día y me gustó (hasta me armé un LiveCD tamaño tarjeta) pero no me parece que sea para gente que no sabe. Les va a parecer feo y poco intuitivo, en cambio en Gnome/KDE/Xfce tenés algo asimilable al Menú Inicio y la barra de tareas de Windows.

A Vector no lo había considerado, parece interesante por usar Xfce. Lo que me gusta un poco menos es que sea basado en Slackware (estoy acostumbrado al manejo de paquetes de Debian) y sobre todo que no tenga un LiveCD. Para mostrarles el SO en funcionamiento tendría que instalarlo, y me parece peligroso en una máquina que no es mía. Salvo que me compre una laptop vieja, pero una máquina comparable a esas me costaría algo así como una luca, me imagino.

Así que supongo que por ahora voy a probar con Xubuntu, que es rápido, liviano, y bastante lindo.

---

### Post by jpmorelli on 2006-12-20
> **Hex_Mandos said:**
> 
Así que supongo que por ahora voy a probar con Xubuntu, que es rápido, liviano, y bastante lindo.


Xubuntu esta muy bueno, pero pense que NO querías que sea Xfce ;)

---

### Post by Hex_Mandos on 2006-12-20
No, probé Xfce y me gustó (dije lo contrario? Estoy perdiendo la poca cordura que alguna vez tuve?).

---

### Post by derjames on 2006-12-20
Prueba PuppyLinux, está basado en Debian y al igual que DSL el file .iso es de 50 MB en mi antigua máquina Celeron 400 MHz el desempenio es sobresaliente...

La otra es instalar Ubuntu Server y aniadir el GUI más liviano (FLuxBOx, IceWM, etc...)

saludos

---

### Post by scrooge_74 on 2006-12-20
Para usuarios neofitos lo mejor sería que instales un ubuntu server y utilizar el manejador de  ventanas que sea lo suficientemente amigable para no intimidarlos y que les puedas instalar los reemplazos de los programas de MS que usan.

Si eliminas la excusa de no tengo tal programa es ya un paso y si el entorno gráfico no se ve intimidante es una excusa menos.

Los usuarios normales no saben como configurar cosas así que eso no es excusa para que digan que no.  Una vez trabajé en una empresa pública y eliminé de los windows todos los paneles de configuración y hasta el uso de los floppy para no tener que esta reparando las cagadas de los usuarios.

Suerte con la prédica

---

