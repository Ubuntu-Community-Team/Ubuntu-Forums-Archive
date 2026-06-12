---
title: "[COMO] Obtener id alta en amule con modem huawei SmartAX mt882"
date: 2008-02-05
forum: Argentina Team
---

### Post by guisheca on 2008-02-05
Para todos los que tengan este módem quizás les ocurrió que hay multitud de sitios que muestran como abrir puertos en este módem pero por alguna razón las opciones que dan y las capturas de pantalla están bastante lejos de lo que en verdad son en nuestro caso.

1º para poder entrar en la configuración del módem dicen que tenemos que poner en la barra de direcciones del explorador la dirección ip de nuestro módem que dicen que es 190... bla bla. La dirección ip de el módem huawei smartax mt882 conectado por puerto de red es 10.0.0.2 y por usb es 10.0.0.100 para los usuarios de arnet de argentina.

2º al poner 10.0.0.2 nos abre una página en la cual no se puede cambiar nada es solo información del módem.

Para entrar a las opciones de configuración debemos poner [http://10.0.0.2/admin.html](http://10.0.0.2/admin.html) (o 10.0.0.100 según corresponda) al hacer esto nos pedirá que pongamos un nombre de usuario y una contraseña las cuales por defecto son: **usuario: admin, contraseña: tomenague**. Si este usuario y contraseña no funcionan deberán resetear el módem mediante un pequeño botoncito empotrado detrás del módem, pero CUIDADO que al hacer esto el módem adquiere su configuración de fábrica con lo cual la conección a internet probablemente no funcione y haya que utilizar el cd del kit autoinstalable para restablecer la conección (abrir el cd y hacer click en archivo setup.exe el cual abrirá las opciones de instalación y se deberá elegir &#8220;reinstalar módem&#8221; y seguir todos los pasos, hay que tener el usuario y la contraseña de la conección).

Una ves entrado a las opciones del módem hay que hacer click en la opción basic del menú izquierdo luego nat y luego redirec. Allí hacer click en new y poner lo siguiente:

[IMG]http://i181.photobucket.com/albums/x250/guisheca/ejemplo.jpg[/IMG]

para tcp:

Local address: 10.0.0.3 esto depende de donde esté la placa de red, para mí es 10.0.0.4, porque tengo dos placas de red, la primera es la integrada a la mother (que se quemó en una tormenta, por lo tanto no funciona pero ocupa un lugar en el sistema) y la segunda una que yo añadí

global ip from: no tocar (0.0.0.0)

global ip to: no tocar (0.0.0.0)

Destination Port From: 4662 (o el puerto tcp que ocupen para amule)

Destination Port To: 4662 (o el puerto tcp que ocupen para amule)

Local Port: 4662 (o el puerto tcp que ocupen para amule)

hacer click en submit

después nuevamente click en new pero ahora para udp

Local address: 10.0.0.3 acuerdense de lo que dije antes

global ip from: no tocar (0.0.0.0)

global ip to: no tocar (0.0.0.0)

Destination Port From: 4672 (o el puerto udp que ocupen para amule)

Destination Port To: 4672 (o el puerto udp que ocupen para amule)

Local Port: 4672 (o el puerto udp que ocupen para amule)

hacer click en submit

Luego de hacer esto ya tendremos los puertos abiertos, pero para que nuestro módem recuerde lo que hicimos, y no lo tengamos que hacer cada ves que encendamos el módem vamos a Tools>Save & Reboot, elegimos "save" y le damos a submit.

[IMG]http://i181.photobucket.com/albums/x250/guisheca/ejemplo2.jpg[/IMG]

Listo!! ya tendrán id alta en amule

Agradezco la ayuda desinteresada de Ivan Meyer y ja_gabriel del foro de ubuntu-es que colaboraron con el contenido de este tutorial.

---

### Post by faktorqm on 2008-02-05
OT: Hola a todos! ya volvi de mis desconadas vacaciones en villa gesell.
Bueno, muy bueno el tuto, yo deberia hacer el del zyxel que prometi y me colgue :S
Lo que capaz estaria bueno es cambiar los puertos del emule, por el que trae por defecto esta filtrado en varios lugares, aunque de todas maneras te lo filtran igual, pero capaz por ahi alguna mala configuracion te deja pasar el paquete. yo uso 7000 tcp, 7003 udp y 7010 udp. salu2!

---

