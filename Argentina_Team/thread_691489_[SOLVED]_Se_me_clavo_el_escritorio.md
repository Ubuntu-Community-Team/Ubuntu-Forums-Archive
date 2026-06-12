---
title: "[SOLVED] Se me clavo el escritorio"
date: 2008-02-08
forum: Argentina Team
---

### Post by h9005 on 2008-02-08
No  me inicia el xserver, entro a ubuntu studio pero en modo consola, como hago! Estoy desesperdado, soy tan vulnerable a su amor!

---

### Post by juanman on 2008-02-08
Yo diria acuestate, levantate, no podés seguir asi oh noo...
:guitar:

Naa escribi en consola: sudo dpkg-reconfigure xserver-xorg y dale a aceptar (con el tab te marca el aceptar) a todo (controla q el driver sea el de tu grafica)


Preguntá cualquier duda...

---

### Post by nemodot on 2008-02-08
y si haces startx que error te manda?

---

### Post by h9005 on 2008-02-09
Despues de todo lo que acepto el escritorio no incia, y aparece el siguiente msj: xserver-xorg postinst warning overwriting posibilitiesy dice algo del backup.

---

### Post by juanman on 2008-02-09
Eso esta bien... Proba haciendo un sudo startx o un sudo /etc/init.d/gdm restart y si no inicia te va a mostrar el log con el error... Pasanos esa info por aca...
Q hiciste antes de q pase eso? Estas usando los drivers privativos de nvidia o ati?
Como solucion temporal proba haciendo un sudo dpkg-reconfigure xserver-xorg y elegi como driver al vesa... Eso deberia andar pero sin aceleracion grafica y con una baja resolucion (lo q seria un "modo a prueba de fallos")

---

### Post by h9005 on 2008-02-11
Hola finalmente pude resolverlo. Seguí los pasos que me dijeron, luego de que me tira el error de escritorio, inicio sesión, detengo el funcionamineto del escritorio (por las dudas, para que no genere conflicto, corro la reconfiguracion, una vez finalizada ejecuto el escritorio. Una vez dentro del escritorio, desinstalo desde envy el controlador nvidia, reinicio y listo. ¿Como le ponemos resuelto?

---

### Post by Mauro22 on 2008-02-11
Felicitaciones.



Para marcar como solved:


Justo arriba del primer post (el tuyo) del lado derecho hay tres links:

 		
 	
	 		[Thread Tools]("http://ubuntuforums.org/showthread.php?t=691489&nojs=1#goto_threadtools") 		 [IMG]http://ubuntuforums.org/images/uf/misc/menu_open.gif[/IMG] 	 	 		 			[Search this Thread]("http://ubuntuforums.org/showthread.php?t=691489&nojs=1#goto_threadsearch") 			 [IMG]http://ubuntuforums.org/images/uf/misc/menu_open.gif[/IMG] 		 	 	 	 	 		[Display Modes]("http://ubuntuforums.org/showthread.php?t=691489&nojs=1#goto_displaymodes") 		 [IMG]http://ubuntuforums.org/images/uf/misc/menu_open.gif[/IMG]

Haces clic en el primero, Thread Tools y luego en Mark As Solved!


Saludos!

---

### Post by h9005 on 2008-02-24
Ya sé que está resuelto, pero despues de actualizar el sistema se clavó de vuelta.:confused:

---

### Post by rojojuan on 2008-02-25
Volviste a instalar los drivers de Nvidia con Envy?

> **h9005 said:**
> Ya sé que está resuelto, pero despues de actualizar el sistema se clavó de vuelta.:confused:

---

### Post by faktorqm on 2008-02-26
Cada vez que actualices el kernel te va a pasar, eso es gracias a la gente de nvidia que no libera su driver.
Anda a una consola, edita el xorg.conf, ponele vesa en el driver, hace 
sudo /etc/init.d/gdm restart
cuando te levanta corre el envy, reinicia y listo el pollo.

---

