---
title: "¿Que distro para esta pc?"
date: 2008-03-08
forum: Argentina Team
---

### Post by benzema on 2008-03-08
es la de un amigo que se quiere pasar a linux alguna facil quisiera que sea ubuntu pero le va a andar lento me parece..

amd k6 533 mhz
192 mb ram compartida con video creo que 8 mb le pasa 
y disco de 8 gb me parece o por ahi anda no mucho mas de eso..

Saludos..

---

### Post by Mauro22 on 2008-03-08
Podrias probar con knoppix, es bastante rapida, usa KDE y levanta casi todo el hardware.

---

### Post by guisheca on 2008-03-08
Para compus viejitas yo conozco las siguiente distros:

*[[COLOR="Blue"]Damn small linux[/COLOR]]("http://damnsmalllinux.org/index_es.html") (dsl) ocupa tan solo 50 mb y funciona con máquinas de hasta 16 mb de ram. Ojo, no está enfoncado al usuario novato.
*[[COLOR="Blue"]Puppy linux[/COLOR]]("http://www.puppylinux.com/index.html") otro muy liviano, aunque tampoco es muy amigable
*[[COLOR="Blue"]Fluxbuntu[/COLOR]]("http://fluxbuntu.org/js.html"), es el ubuntu, pero con el manejador de ventanas ultraliviano fluxbox, sin embargo, mas allá de que sea ubuntu, tampoco es demasiado amigable, debido a que fluxbox no es un entorno de escritorio, si no, un manejador de ventanas con una pequeña barra.
*[[COLOR="Blue"]Xubuntu[/COLOR]]("http://www.xubuntu.org/"), sería lo mas cercano a ubuntu sin ser tan pesado, pero no se si va a funcar en la compu que mensionás.

Ojo, ni fluxbuntu ni xubuntu son distros mantenidas por canonical, es decir, no son oficiales, los hacen la comunidad de usuarios.

Estas son las opciones que conozco, espero que te sean de ayuda.
Un saludo

---

### Post by benzema on 2008-03-08
Oigan anduve averiguando y he visto varios posts diciendo que es muy buena esa knoppix,y ke es muy rapida tmb, esta basada en devian no? muy probable que la pruebe.. yo use kubuntu en mi pc pero se me hizo muy lenta y eso que no tengo una pc tan mala es una sempron 3200 overlockeada a 2400 mhz con un 1 gb de ram y geforce 6100 ob board de 256 que vienen de la ram creen que esta knoppix    es una buena alternativa a  kubuntu? o sera igual de veloz? 

Gracias x la pronta respuesta a la 1 pregunta... chiaoo

---

### Post by gmunioz on 2008-03-08
Hola ben...:
Dentro de las distros de Ubuntu, Xubuntu puede funcionar en esa pc, deberías intentar instalar mediante el alternate-cd, es la opción que se encuentra debajo del  boton start download, en la página de descarga.
E instalarla con este procedimiento:
Primero, en el menu de instalación elegir la tercera opcion sistema solo de comandos, es el server, solo texto, esto asegura su instalación sin problemas de memoria o espacio.
Una vez terminada la instalación e iniciado del disco rígido, estarás en consola, solo texto, el linux real, allí deberás ejecutar:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xubuntu-desktop 
startx
Y ya tendrías a ubuntu funcionando con xfce.
Si te resulta lento o pesado, podrías probar instalar fluxbox, que ira seguramente muy rápido.

---

### Post by Mataca on 2008-03-08
Aunque no soy fana de KDE te recomiendo KNOPIX seguro que te anda de 10. y tiene muchas aplicaciones bonitas :) Ademas es una de las mejores distro live-cd lo podes probar a ver como gunciona antes.

Me olvidaba, tambien podes usarlo como live-pendrive (nombre inventado por mi) claro q u pc seguro no tiene USB peeerooo es una buena opcion.

[http://www.knoppix-es.org/](http://www.knoppix-es.org/)

---

### Post by nemodot on 2008-03-08
Si tuviera un AMD K6 lo primero que probaría como referencia es el Xubuntu y si es muy lento o no corre probaría con distribuciones mas livianas como Damn Small Linux.

---

### Post by raul_ on 2008-03-08
Xubuntu = 256 MB RAM min.

Arch Linux, pero para principiantes no lo se. Elive?

Perdon por meu espanhol, yo so portugues :) apenas tentando ajudar

---

### Post by jpmorelli on 2008-03-08
Si no exigís mucho usa el Xubuntu... Cargalo como dijeron más arriba con el Alternate CD, ese te va a permitir cargar el sistema aunque estés por debajo de los 256, te lo aseguro... yo cargué Ubuntu 7.04 en una Pentium 233 MMX con 64Mb !!!
Suerte !

---

### Post by benzema on 2008-03-09
ok gracias por sus respuestas...

---

### Post by pante on 2008-03-09
En mi experiencia, con 128 MB de RAM instalé Xubuntu con el Alternate y funcionaba muy bien. Obviamente cuanta más memoria mejor. Con Linux la velocidad de la CPU no es tan limitante.

Saludos

---

### Post by Mataca on 2008-03-11
Chicos por ahi ya esta solved este tema, pero encontre esto: una tablita con requisitos minimos de muchas distro.

[http://danubuntu.wordpress.com/2008/03/07/tabla-con-los-requisitos-minimos-y-recomendados-de-las-distribuciones-de-linux-mas-comunes/]("http://danubuntu.wordpress.com/2008/03/07/tabla-con-los-requisitos-minimos-y-recomendados-de-las-distribuciones-de-linux-mas-comunes/")

---

