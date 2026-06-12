---
title: "help!!! endsl-ar"
date: 2007-06-22
forum: Argentina Team
---

### Post by perezheguy on 2007-06-22
Hola gente salvadora alguien podria darme una mano en la configuracion de mi ethernet endsl-ar, ya que un colaborar me tiro algunas pistas pero lamentablemente no me reconoce la placa de red como modem!!!! es un a placa conexant.
Gracias

---

### Post by fetova on 2007-06-22
Podrias ser mas especifico con lo que te sucede?

Placa, situacion exacta, etc :)

Saludos!

---

### Post by Cripton on 2007-06-22
la placa de red como modem??

no será el modem en la placa de red?

tirá modelos y marcas por lo menos sinó sabés el chip

¿Será este? modem router adsl
ENDSL-A2+R
One Port Ethernet ADSL2+ Router

[http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=1&pid=178#SPECS]("http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=1&pid=178#SPECS")

---

### Post by perezheguy on 2007-06-27
hola gracias por responder!
mi mootherboard es pcchips m925, placa de red onboard, moden ethernet endsl-ar de conexant. reinstale ubuntu ahora anda el tema es que en oportunidades y no se como reestablecer el modem, tengo volver a windows y como este modem se configura desde un acceso de navegador 10.0.0.2 lo vuelvo a configurar y listo.
No hay manera de hacerlo desde ubuntu?
gracias

---

### Post by faktorqm on 2007-06-27
Hola, bueno, si desde windows te anda y desde linux no, no lo toques, el problema esta en tu maquina, no en el modem de internet, ok? Es decir, o bien, no tenes los drivers de la placa de red integrada, o bien tenes todo bien pero no la tenes configurada. 

Ahora bien, segun lo que me contas, en windous entras desde tu navegador a la direccion 10.0.0.2 y te aparece el modem, ingresas una contrasenia (perdon, pero no me anda la enie) seguramente y entras a la configuracion. Entonces por lo que contas supongo que linux no te toma la placa de red. Ahora bien, la placa de red en un pc-chips 925 depende del chipset que tengas. A partir de aca tenes 2 opciones, 

opcion 1: probamos si tenes todo ok la placa de red y configuramos y si anda internet, josha, si no, pasas a la opcion 2.

opcion 2: si la opcion 1) falla por que dice que no existe, averigua el modelo de tu mother y se vera como proceder. si la opcion 1) falla pero EN NINGUN MOMENTO TE DICE QUE NO EXISTE, ENTONCES HAY QUE SEGUIR EN LA OPCION 1 Y DESCARTAR ESTA.


OPCION 1:

1) Anda al windous, inicio -> ejecutar y escribi "cmd" (sin comillas) y despues enter. Te abre una ventana negra. 

No tenes el inicio -> ejecutar? entonces apreta ctrl + alt + supr, luego boton administrador de tareas, vas a archivo -> nueva tarea (ejecutar), escribis"cmd" (sin comillas) y despues enter. Te abre una ventana negra. 

una vez con esa ventana escribis "ipconfig /all" y te van a salir un monton de datos de tu conexion. 
Entre las opciones, te aparece una que se llama "DHCP habilitado". Si dice "SI", salteate la parte que viene aca y pasa directo a "pasando a linux...". SI DICE "NO" hace esto:

COPIA EN UN PAPEL O IMPRIMI LOS SIGUIENTES DATOS:

Direccion IP, Mascara de subred, Puerta de enlace predeterminada, y Servidores DNS.

_Pasando a linux_:

una vez en ubuntu, anda a sistema -> administracion -> red, ingresa la contrasenia, y ahi te muestra lo que tenes hablando mal y pronto.

Te tiene que aparecer un item que diga CONEXION ALAMBRICA, si te aparece, anda a "Si tenias DHCP...", si no te aparece, cerra, y abri un terminal y escribi:

```
sudo ifconfig eth0 up
```

**SI TE TIRA ALGUN ERROR, PASAS A LA OPCION 2, si no te muestra nada, entonces ta todo ok**

Volve a "red" siguiendo lo de arriba y teoricamente te tendria que aparecer, si no te aparece escribi y lo hacemos por terminal y listo. si te aparece, anda al boton propiedades.


_Si tenias DHCP _en modo "SI", PONE "CONFIGURACION AUTOMATICA (DHCP)" y aceptar. y entonces abri el firefox o el navegador que tengas a mano y fijate, deberia funcionar.

Si no tenias DHCP, llena con los datos que habias conseguido antes de la configuracion del windous, ip, mascara y puerta de enlace. dale aceptar y despues anda a la ficha DNS y completa con los datos anteriores. una vez que tenes todo eso, dale cerrar y listo, acabas de poner la misma configuracion de red en linux que tenias antes en windows. Por lo tanto te deberia andar todo ok.


OPCION 2) 

Yo busque y encontre estos modelos de pc chips 925:

Motherboard MicroATX para Pentium 4 Socket 478, Con Bus Frontal de 400 MHz, que soporta los siguientes procesadores: Intel Pentium 4 hasta 2 GHz y 2 GB en RAM (Utiliza memoria DDR PC2100 y tambien puede usar DIMM PC133 SDRAM), Chipset VIA P4M266, incluye Controladora de Audio, Controladora de Video 3D AGP, Modem y Red integradas, 2 slots PCI de 32 bits, 1 slot AGP, 1 slot CNR, 3  slots USB, Marca PC CHIPS Modelo 925-LMR

- Motherboard MicroATX para Pentium 4 Socket 478, Con Bus Frontal de 400 MHz, que soporta los siguientes procesadores: Intel Pentium 4 hasta 2 GHz y 2 GB en RAM (Utiliza memoria DDR PC2100 y tambien puede usar DIMM PC133 SDRAM), Chipset VIA P4M266, incluye Controladora de Audio, Controladora de Video 3D AGP, Modem y Red integradas, 2 slots PCI de 32 bits, 1 slot AGP, 1 slot CNR, 3  slots USB 2.0, Marca PC CHIPS Modelo 925-LMR V3.1

- Motherboard microATX para Pentium 4 Socket 478, Con Bus Frontal de 533 MHz, que soporta los siguientes procesadores: Intel Pentium 4 hasta 2.8 GHz y 2 GB en RAM (Utiliza memoria DDR266 y DDR333), Chipset VIA P4M266A/VT8235, Controladora de Video 3D AGP, Sonido, Modem y Red integradas, 2 slots PCI de 32 bits, 1 slot CNR, 1 slot AGP 4X, 6  slots USB 2.0, Marca PC CHIPS Modelo M925ALMU

- Motherboard microATX para Pentium 4 Socket 478, Con Bus Frontal de 533 MHz, que soporta los siguientes procesadores: Intel Pentium 4 hasta 2.66 GHz y 2 GB en RAM (Utiliza memoria DDR333 SDRAM y tambien puede usar DIMM PC133 SDRAM), Chipset VIA P4M266A/VT8235, Controladora de Video 3D AGP, Sonido, Modem y Red integradas, 2 slots PCI de 32 bits, 1 slot CNR, 1 slot AGP 4X, 4 slots USB 2.0, Marca PC CHIPS Modelo M925G

Ahora, me tenes que decir cual es el tuyo, asi te podemos ayudar, de lo contrario, no podemos adivinar, por que cada configuracion es distinta dependiendo del chipset si es que el problema esta en el driver.

Espero que te haya servido de algo. y Espero tu respuesta. salu2!

---

### Post by perezheguy on 2007-06-28
hola Master!!!!
Hice al pie de la letra lo que me dijiste, no estaba dhcp habilitada, copie la informacion todo bien pero nada....
no consigo navegar. dato: cuando pongo en terminal pppoeconf ME DICE QUE NO ESTA INSTALADA, pero al no tener conexion no puedo hacer aptr-get install pppoeconf, como hago ya que probe con un archivo tar y ademas de ser un quilombo (notaras que mucha experiencia en linux no tengo) desde windows que ahi si tengo internet.
Bueno con respecto al motherboard y sus chiches la tercra opcion es mi placa.
Gracias y espero resolver este problema , me encanta ubuntu y no quisiera renunciar a parte gente como vos (que presta ayuda hacen dew este mundo un lugar mejor) Gracias 
claudio

---

### Post by faktorqm on 2007-06-28
Hola! seré curioso, me falto contemplar un caso, el caso de que te ande todo pero en lugar de conectarte desde el modem lo hagas desde el guindous. 

Decime si cuando entras a guindos estas directamente conectado o tenes que ir a algun icono de algo que te conecta. Si le tenes que dar a un icono para conectarte, tambien fijate el modelo y todos los datos de tu modem  de adsl asi te ayudo a configurarlo para que directamente prendas la compu en cualquier sistema operativo y ya tengas salida a internet sin tocar nada.

(si estas mega ansioso, en el cd de instalacion del ubuntu esta ese paquete, y tambien lo podes bajar desde el guindous desde [http://packages.ubuntu.com](http://packages.ubuntu.com) ) Salu2!! :D

---

### Post by perezheguy on 2007-06-29
MASTER faktorqm:p

Justamente te estoy escribiendo ya desde ubuntu .
Simplemente reinstale ubuntu y SOLUCIONADO GRACIAS A TUS INDICACIONES de configuracion de IP.
Todo anda perfecto...


Otra vez GRACIAS
claudio

---

### Post by faktorqm on 2007-06-29
DE NADA!! que bueno que te anduvo. a disfrutar!! :D:D:D

---

