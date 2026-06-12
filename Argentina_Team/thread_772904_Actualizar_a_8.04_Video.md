---
title: "Actualizar a 8.04 Video"
date: 2008-04-28
forum: Argentina Team
---

### Post by rojojuan on 2008-04-28
Todavía estoy usando Gusty y estoy leyendo lo que puedo para actualizar vía Internet.
Sé que tengo que desactivar los repositorios de terceros, pero me surge una duda con los drivers de video.
Mi placa es una Nvidia que tiene instalados los drivers propietarios vía Envy y funciona a la perfección.
Antes de actualizar a HH tengo que desinstalar esos drivers e instalar los que vienen con Gusty o por el contrario no hay problemas al actualizar?
Desde ya gracias.

---

### Post by luks911 on 2008-04-28
Buenas, 
En la página de Envy dicen con un cartel de advertencia que antes de actualizar hay que desinstalar con ```
$ sudo envy --uninstall-all
``` 
Eso fue lo que hice y una vez actualizado el sistema volví a instalar el driver pero sin Envy. No sé qué es lo que sucede si no se desinstala, pero con mi escaso conocimiento imagino que el driver dejará de funcionar por el cambio de kernel.
Saludos

---

### Post by rojojuan on 2008-04-29
> **luks911 said:**
> Buenas, 
En la página de Envy dicen con un cartel de advertencia que antes de actualizar hay que desinstalar con ```
$ sudo envy --uninstall-all
``` 
Eso fue lo que hice y una vez actualizado el sistema volví a instalar el driver pero sin Envy. No sé qué es lo que sucede si no se desinstala, pero con mi escaso conocimiento imagino que el driver dejará de funcionar por el cambio de kernel.
Saludos

Muchas gracias por responder.
Así lo hice, primero con Envy desinstalé los drivers de Nvidia y luego desinstalé el Envy.
Actualicé de Gusty a Heron y todo bien.
Luego instalé EnvyNG y corriéndolo me instaló los últimos drivers de NVidia.
Un problema que tuve cuando quise guardar la configuración de 800x600 el Nvidia X Server (Sistema, Administración) no me lo permitía.
Al final encontré la solución para guardar las resoluciones que quieras.
En consola sudo "nvidia-settings", modificás lo que quieras y despúes lo podés guardar sin problemas.
Mas saludos!

---

