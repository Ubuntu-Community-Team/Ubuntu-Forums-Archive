---
title: "Sidebar tipo VIsta"
date: 2007-11-10
forum: Argentina Team
---

### Post by matlnx on 2007-11-10
Buenas tardes, mi nombre es Matias, y hace relativamente poco que estoy en linux. Instale en mi pc nuevo ubuntu 7.04 (que luego actualice a 7.10) y realmente cada dia estoy mas conforme. :)

La pregunta que queria hacerles es si me podian comentar de donde puedo bajar la Sidebar tipo Vista para mi Ubuntu 7.10.

Estuve buscando por internet y todavia no di con el lugar indicado, asi que pense que este debiera ser el mejor, ya que es de esta distro donde voy a instalarlo.

Bueno espero que puedan ayudarme, y desde ya muchas gracias.
Atte
Matias

---

### Post by sajnox on 2007-11-10
En [www.gnome-look.org](www.gnome-look.org) tenes todas esas cositas lindas

Saludos,

---

### Post by facundocorradini on 2007-11-10
[COLOR="Silver"](más alla del enojo que me dá leer "tipo vista" siendo algo que primero aparecieron en Mac OS y luego en GNU/Linux)[/COLOR]

 Creo que lo que estás buscando son los screenlets para compiz-fusion

sitio oficial: [http://www.screenlets.org](http://www.screenlets.org)

COMOS en español:

[http://www.hachemuda.com/2007/05/04/mi-nuevo-escritorio-con-screenlets-los-widgets-para-beryl/](http://www.hachemuda.com/2007/05/04/mi-nuevo-escritorio-con-screenlets-los-widgets-para-beryl/)

espero que te sirvan. 

saludos

---

### Post by santiagoward2000 on 2007-11-10
Hola matlnx!
Como para completar un poco lo que dijeron sajnox y facundo, acá te dejo un link con el Screenlet que buscás.

> **facundocorradini said:**
> [COLOR="Silver"](más alla del enojo que me dá leer "tipo vista" siendo algo que primero aparecieron en Mac OS y luego en GNU/Linux)[/COLOR]

Y... es verdad, pero bueno, en [www.gnome-look.org](www.gnome-look.org) figura como > Sidebar Screenlet (Vista'ish look). Estamos en el horno!!

---

### Post by rretamar on 2007-11-10
Si usas Kubuntu (o si pensás probarlo alguna vez :) ) tenés el software Superkaramba, todo un dulce para los ojos.

KDE 4 lo va a reemplazar por "Plasma" pero manteniendo compatibilidad hacia atrás.

Saludetes !

---

### Post by matlnx on 2007-11-11
Bueno desde ya muchas gracias por los datos, les comento que ya estan funcionando los screenlets famosos :D.

Les comento lo que hice, asi si alguien en un futuro tiene un problema tiene una guia paso apaso de como hacerlo ;)

([http://matlnx.blogspot.com](http://matlnx.blogspot.com)) Screenlets (sidebar) en Compiz (Ubuntu 7.10 Gusty Gibson)

Al fin, y luego de la ayuda de la gente del foro de Ubuntu-ar[1] (Gracias sajnox, facundocorradini, santiagoward2000 y rretamar) pude agregar a mi Ubuntu los famosos screenlets. 
Los screenlets son programas que corren en el escriotio (como la sidebar de window$ Vista, que es una copia de la de macOS de hace un tiempo) y que permiten obtener informacion (como ser clima, hora, etc) en tiempo real entre tantas otras cosas.

Para comenzar con la instalacion[2] se deben agregar los repositorios de screenlets de la siguiente manera:

#nano /etc/apt/sources.list

y agrego las siguientes lineas al final

#Repositorios de Screenlets
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets

Luego haciendo control+x nos va a perdir si deseamos guardar las modificaciones, oprimimor Y (yes) y luego enter para sobreescribir el mismo archivo.

Una vez que agregamos esto, vamos agregaremos el PGP Key correspondiente para que cuando hagamos un apt-get update (o "sudo apt-get update") no nos salga el error. Esto se hace mediante el comando:

wget [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg) -O- | sudo apt-key add - && sudo apt-get update

Y luego instalamos los screenlets:

apt-get install screenlets

Una vez que finalizamos sin problemas, vamos al menu Sistema -> Preferencias -> Screenlets y vamos seleccionando los que mas nos gusten.

ACLARACION: Es muy probable que cuando reinicien sus PCs los screenlets no inicien junto con la misma automaticamente, y que les aparezca un mensaje de error "Unable to connect or launch daemon. Some values may be displayed". En internet encontre la solucion, que consta de dos partes:

La primera ejecutar en una terminal[3]

# chmod 755 ~/.config/Screenlets/. -R

Y la segunda agregar en Menu Sistema -> Preferencias -> Sesiones un nuevo iniciocon el comando python /usr/local/share/screenlets-manager/screenlets-daemon.py [3]. Esto permite iniciar todos los screenlets que cuando los agregamos, habilitamos la opci{on de “automatically start at login”.

[1] [http://ubuntu-ar.org/](http://ubuntu-ar.org/)
[2] [http://www.screenlets.org/index.php/FAQ#Installation](http://www.screenlets.org/index.php/FAQ#Installation)
[3] [http://nemoelpiratilla.wordpress.com/2007/09/14/how-to-solucionar-fallo-al-iniciar-screenlets-en-linux/](http://nemoelpiratilla.wordpress.com/2007/09/14/how-to-solucionar-fallo-al-iniciar-screenlets-en-linux/)

---

