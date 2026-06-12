---
title: "Ayuda !! Particion De Ubuntu En Rigido Nuevoooo"
date: 2007-11-10
forum: Argentina Team
---

### Post by leonardo83 on 2007-11-10
Que tal gente, ayer compre un rigido de 80 gb para instalar solmente ubuntu y el otro rigido de 60 para utilizar windows.
Tengo el ubuntu 7.04 asin que corri el live cd, perfecto, elijo instalar y me aparecen las opciones, a la hora de la particion elegi :
guiado - utilizar todo el disco rigido ( en este caso estoy eligiendo mi nuevo rigido) y al final elijo instalar, aparece la barra que carga y se queda en el 5 % y de ahi no pasa.:confused:
Pasan minutos, minutos, horas......y sigue ahi.
El rigido como lo compre lo instale, no le aplique fdisk ni format como haria con un rigido nuevo para windows porque me dijeron que la particion puede ser diferente y si lo particionaba y formateaba y despues queria instalar linux ahi pordia tener problemas.
Por favor ayudenme que hace 2 dias estoy verificando donde podria estar el inconveniente!!  :(
Saludos.

---

### Post by BlackHero on 2007-11-10
Hola amigo como va bueno, el tema es asi provaste dejando el disco nuevo solo como master y desconectando el otro? je =)
en el caso de que hayas hecho eso y no funque, abri el gpaterd y formatealo desde ahi con el livecd es mas seguro =) cualquier cosa avisa =) instalalo asi que despues te enseñamos a configurar el grub para que te carge el windows desde el otro disco =) cyas

---

### Post by leonardo83 on 2007-11-11
Gracias man!!
Igualmente probe de nuevo y pude instalarlo correctamente :)
Pero como no podia ser de otra manera, empezaron los problemas, me permito preguntarlo aqui disculpen por no abrir otro thread pero ahora sucede lo sigueinte: mi pc quedo con cd-rw como master y cd-r como slave, y rigido de windows como master (el cable ide no me permitio otra forma :() y el rigido de ubuntu como slave.
Al empezar la pc aparece el grub que me pide elegir que sistema empezar, perfecto. Arranco windows, uso un poco y elijo apagar, todo ok.
Apago y areanco linux, PRIMERO : tarda mucho en arrancar, mas que con el live cd!, pasan como 3 minutos hasta que desaparece la barrita naranja que carga.Aparece el login, entro, lo uso, eligo apagar la pc, se apaga . SEGUNDO: tarda nuevamente pero aqui viene mi pregunta... no se apaga la pc. Me queda la imagen del logo con la palabra ubuntu y la barrita sin cargar.Pasan 2....5....10....12 minutos y no pasa nada. Tengo que apagarlo manualmente desde el gabinete.
Me pueden ayudar?
Gracias, como ven ya estoy teniendo una serie de complicaciones de bienvenida :(

---

### Post by clasificado on 2007-11-11
Tengo en mente que hay una forma de quitar esas pantallas bonitas para dejar que se vea la consola, que te muestra como se van enciendiendo y apagando los servicios.

Podrias saber cual es el servicio que te causa problemas

Pasa que no recuerdo como se llama el paquete :lolflag:

Clasificado

---

### Post by leonardo83 on 2007-11-11
Volvi si si, apenas termine de escribir esas lineas me puse a investigar y probe unas cosas de una pagina que hora borre :mad: pero si alguien mas tiene ese problema les digo como lo solucione:
 1) entre en sudo nano /etc/modules
al final del fichero escribi apm_power off=1
guardamos y cerramos
2) ejecutamos sudo nano /boot/grub/menu.lst
busque la linea que dice kernel y ademas una seri de numeros y ro quet splash y al final de esto agregue
acpi=off apm=power-off
guarde cambios, reinicie la pc y ahora al apagarla se apaga por completo :):):):)

Gracias a los que contestaron!!

PD : ahora me gustaria saber como hago para conectarme por dial up .........ni idea como se hace.. :confused:

---

### Post by niko_3100 on 2007-11-12
Si en esta linea ro quet splash pones NOsplash (nosplash asi eh) no te aparece la imagen esa de la abrrita y te aparece la consola.

---

### Post by leonardo83 on 2007-11-12
> **niko_3100 said:**
> Si en esta linea ro quet splash pones NOsplash (nosplash asi eh) no te aparece la imagen esa de la abrrita y te aparece la consola.


Vos me decis la barrita del principio ?? :confused:
voy a probarlo a ver que pasa, man.
Pero decime tengo que poner NOsplash o nosplash ???
Me quedo asi como la duda viteh' :(

---

### Post by fscodelaro on 2007-11-12
Leonardo, si querés ver los mensajes solo por una vez o un par de veces no es necesario que modifiques los parametros de booteo, solo necesitas apretar Ctrl - Alt - F1 en cuanto te aparezca el splash de ubuntu. La otra forma de verlos es una vez que ya estas en el escritorio, yendo a Sistema > Administración y buscando el Log Viewer (no te puedo decir exacto el nombre porque ahora estoy en Kubuntu y en inglés pero por ahí anda).

---

