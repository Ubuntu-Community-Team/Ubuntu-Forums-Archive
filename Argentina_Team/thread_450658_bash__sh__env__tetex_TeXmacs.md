---
title: "bash / sh / env / tetex /TeXmacs"
date: 2007-05-21
forum: Argentina Team
---

### Post by jotacebusta on 2007-05-21
Buenas a todos,

He estado intentando instalar TeXmacs 1.6.0.10 en ubuntu 7.04, siguiendo las instrucciones de [http://www.texmacs.org/tmweb/download/rpm.en.html](http://www.texmacs.org/tmweb/download/rpm.en.html). 
Luego de instalar rpm, bajé el archivo TeXmacs-1.0.6.10-1.i386.rpm, y ejecuté  el comando 
sudo rpm -i TeXmacs-1.0.6.10-1.i386.rpm, lo que me da como resultado: 
juanb@juanb-desktopUSFQ:~/Desktop$ sudo rpm -i TeXmacs-1.0.6.10-1.i386.rpm
Password:
error: Failed dependencies:
        tetex is needed by TeXmacs-1.0.6.10-1.i386
        /bin/bash is needed by TeXmacs-1.0.6.10-1.i386
        /bin/sh is needed by TeXmacs-1.0.6.10-1.i386
        /usr/bin/env is needed by TeXmacs-1.0.6.10-1.i386
juanb@juanb-desktopUSFQ:~/Desktop$ 

No entiendo bien qué debo hacer y qué significa este error. Instalé tetex a partir de synaptic, pero parece haber algún problema
juanb@juanb-desktopUSFQ:~/Desktop$ which tetex
juanb@juanb-desktopUSFQ:~/Desktop$ 

En cambio bash, sh y env parecen estar ahí:
juanb@juanb-desktopUSFQ:~/Desktop$ which bash
/bin/bash
juanb@juanb-desktopUSFQ:~/Desktop$ which sh
/bin/sh
juanb@juanb-desktopUSFQ:~/Desktop$ which env
/usr/bin/env
juanb@juanb-desktopUSFQ:~/Desktop$ 

¿Qué debo hacer? 

Por otro lado, la versión de TeXmacs que ubuntu instala es 1.0.6, y según uno de los desarroladores me dijo en el mailing list de TeXmacs, esta versión es muy muy antigua (a pesar de que la numeración no sea tan distinta), y no soporta maxima, que es lo que me interesa... ¿A quién hay que avisarle esto, para que la versión instalada sea la última? De hecho, al tratar de actualizar TeXmacs desde un terminal obtengo un mensaje del estilo:

juanb@juanb-desktopUSFQ:~/Desktop$ sudo apt-get install texmacs
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
texmacs ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

copsa que está en franca contradicción con lo que dicen en la lista, y con el hecho de tener el archivo mencionado al inicio.


gracias


JCB

---

### Post by marianom on 2007-05-21
Deberías utilizar [Alien]("https://help.ubuntu.com/community/RPM/AlienHowto") para pasar el RPM a .deb y facilitarte un poco las cosas.

Proba con ese procedimiento y si tenes otros errores, pasalos que los vemos.

Con respecto al tema de como pedir que mejoren la versión de un programa en particular, sería, entiendo por un bug, en launchpad. Estuve intentando ingresar a lauchpad para darte un link pero me dice que está con error de servidor así que lo vas a tener que ver en un rato.

Saludos.

---

### Post by jotacebusta on 2007-05-23
Gracias marianom por tu ayuda. Instalé el alien, y seguí tus indicaciones, pero lamentablemente no funciona: al hacer doble click en el .deb, obtengo

129552 ficheros y directorios instalados actualmente.)
Desempaquetando texmacs (de .../texmacs_1.0.6.10-2_i386.deb) ...
dpkg: error al procesar /home/jcelena/Desktop/texmacs_1.0.6.10-2_i386.deb (--install):
 intentando sobreescribir `/usr/share/man/man1/fig2ps.1.gz', que está también en el paquete fig2ps
dpkg-deb: el subproceso paste fue terminado por la señal (Tubería rota)

¿qué puedo hacer?

gracias


JCB

---

