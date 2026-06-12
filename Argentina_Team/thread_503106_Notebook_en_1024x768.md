---
title: "Notebook en 1024x768"
date: 2007-07-17
forum: Argentina Team
---

### Post by jorgito on 2007-07-17
Hola a todos!

Como un monton mas de gente me encontre con que luego de la instalacion con el Live CD del 7.04 la pantalla de la Olibook 820 queda en 1024x768 y no en 1280x800 como deberia.
Ya intente usar 
sudo dpkg-reconfigure xserver-xorg
Los modos en el archivo xorg parecen estar bien pero la cosa sigue igual.

Por otro lado vi que se podia instalar un paquete que se llama 915resolution, pero la verdad me parece un parche....
No hay forma de hacer las cosas mas prolijamente? Algun driver mas nuevo o algo asi?

Saludos y desde ya muchas gracias!

---

### Post by gepatino on 2007-07-17
justamente el paquete 915resolution soluciona ese tipo de problemas, si tenes una placa intel.

me parece que el problema estaba en un bug de la bios o algo asi... puede ser que sea un parche o no, dependiendo de como lo veas, pero soluciona el problema.

---

### Post by jorgito on 2007-07-18
Gracias gpatino!

A lo que me referia era que el 915resolution es un parche en el sentido que solo modifica el BIOS del video temporalmente, como una cosa mas corriendo junto con el driver medio defectuoso.
Efectivamente encontre que existe un driver mas nuevo y lo instale haciendo 
sudo apt-get install xserver-xorg-video-intel
Solo con esto y reiniciando quedo arreglado.

Gracias de nuevo y saludos!

---

### Post by jpmorelli on 2007-07-18
Posteanos tu xorg.conf, seguramente podemos darte una mano. Yo muchas veces tuve que poner la resolución que quería a la fuerza en la parte donde se listan. 

Ejemplo: 

SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection

a todos los depth le agregas adelante de todo el "1280x1024"
Suerte !

---

### Post by jorgito on 2007-07-19
Gracias jmorelli, 

Como decia, ya habia visto que los "1280x800" estaban todos agregados pero no pasaba nada.
Me resistí a instalar el 915resolution y lo tenía como ultima opción, será que soy de la epoca en la que habia que andar viendo como le ganabas 2 kilobyte al DOS para correr alguna cosa, pero no me gusta dejar algo instalado que no hace nada salvo en el arranque.

De todos modos, el tema de la pantalla creo que esta arreglado. Ahora tendré que ver si anda todo el resto de las cosas, DVD, WiFi, etc. y seguramente apararecerá algo. Como beta tester la tengo a mi mujer, que a fuerza de no saber siquiera que sistema operativo usa,  prueba de todo. 

Saludos y gracias de nuevo!

---

