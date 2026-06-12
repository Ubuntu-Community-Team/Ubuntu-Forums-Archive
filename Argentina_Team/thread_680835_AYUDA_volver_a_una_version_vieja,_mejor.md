---
title: "AYUDA volver a una version vieja, mejor"
date: 2008-01-28
forum: Argentina Team
---

### Post by niko_3100 on 2008-01-28
Gente tengo un problemita instale hace unas semanas el emesene, y hoy me actualizo a una version nueva, la cosa es que no em deja conectar me aparece una ventanita llena de errores entonces mi pregunta es como volver a la version vieja que tenia y me andaba bien. En el synaptics no me deja elegir la opcion "force version" :( por ahi en la terminal le especifico el comando y me lo toma pero no se cual es jeje!!

---

### Post by nemodot on 2008-01-28
Intentaste desinstalando el emesene desde el synaptic y luego bajarte el paquete desde la pagina de [www.emesene.org](www.emesene.org) ?

---

### Post by niko_3100 on 2008-01-28
desintale desde el synaptcis pero no hay ningun paquete .deb en la pagina de emesene.

---

### Post by anka on 2008-01-28
Esta en el apartado "otros paquetes":

Te lo traduzco:

Debian/Ubuntu APT repository

Añades emesene a la lista de repositores: 
sudo gedit /etc/apt/sources.list

Pegas esto en el fondo de la lista: 
deb [http://apt.emesene.org/](http://apt.emesene.org/) ./
deb-src [http://apt.emesene.org/](http://apt.emesene.org/) ./

Actualizas los repositores: 
sudo apt-get update

Ahora, instala emesene: 
sudo apt-get install emesene

Nada mas, espero que te ayude.

---

### Post by lordpuppet on 2008-01-28
Es claro que ya tenia la sources list de emesene.org. Yo las acabo de añadir y me saltaron las actualizaciones, aunque me funcionó bien despues de instalarlas.

Prueba instalarlas desde el synaptic habiendo desinstalado anteriormente.

---

### Post by User21 on 2008-01-29
Yo tambien recibi las actualizaciones de emesene, y si bien es claro que tiene VAAARIOS BUGS, con solo cerrar el cuadro de dialogo vuelvo a la charla. De todas formas, en breve seguramente recibiremos otra actualizacion (quiero creer) subsanandos los nuevos bugs. De todas formas, puedes bajarte versiones anteriores y ejecutarlos desde su carpeta, sin necesidad de perder la nueva version, y la posibilidad de volver a usarlo con normalidad. 
Por otro lado, no encuentro donde reportar los bugs, jejeje... Yo quiero colaborar!

---

### Post by niko_3100 on 2008-01-29
Claro yo en el synaptics eligo force version per no me la marca no se porque, en que parte del sistema de archivos estan los programas viejos.?

---

### Post by anka on 2008-01-29
Creo que te referiras a los paquetes ya instalados, o que alguna vez lo estubieron, van a parar a /var/cache/apt/archives. Ahi estan todos los .deb que instalaste en algun momento.

De paso, ya que veo que tengo un monton de porquerias ahi, apt-get autoclean, elimina los paquetes que ya no estan instalados, y apt-get clean, los elimina directamente a todos (exactamente lo opuesto a lo que vos queres :P).

Suerte!

---

### Post by niko_3100 on 2008-01-29
aaahh buenisimo eso esta perfecto, no entiendo el apt-get clean si entendi el autoclean pero el clean que es lo que hace de diferente? eliminia todos los que no estan instalados???

---

### Post by anka on 2008-01-29
Ponele que vos instalas "pepito", el .deb queda en ese directorio. Ahora, te cansas de "pepito" y lo desisntalas, el .deb sigue ahi, cosa que si te arrepentis de desinstalar "pepito", el paquete lo va a buscar en el directorio local y no en internet, haciendolo mucho mas rapido.

Aca viene el uso practico de autoclean y clean. El primero solo borra paquetes que no esten instalados, liberando espacio que ocupan paquetes que, en la mayoria de los casos, no vas a volver a instalar (si borras pepito por algo es, pero el paquete sigue ahi, si no pensas instalarlo de nuevo o queres liberar espacio, autoclean y chau .deb, la proxima lo baja de internet).

El clean es mas drastico, borra los .deb de aplicaciones instaladas o que ya fueron desistalados. Si hay que reinstalar, lo baja de internet.

Espero que te ayude, suerte!

---

### Post by niko_3100 on 2008-01-29
Entonces se podria decir que clean borra los .deb del sistema para volver a instalarlos y el autoclean borra paquetes .deb que no estan en uso.

---

