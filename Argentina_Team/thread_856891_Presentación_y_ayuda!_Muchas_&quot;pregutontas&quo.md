---
title: "Presentación y ayuda! Muchas &quot;pregutontas&quot;"
date: 2008-07-11
forum: Argentina Team
---

### Post by tuliobalcaldi on 2008-07-11
Hola! Buenas noches. Primeramente me presento: mi nombre es Tulio y estoy haciendo mi segunda incursión a Linux, pero la primera en serio :) después de dos semanas de leer, leer y leer, me decidí a instalar Ubuntu 8.04 en mi máquina.
He pasado por todo lo que Microsoft ha hecho casi: MS-DOS 5.0 en adelante, Win95, Win98, Win Millenium, Win 2000, Win XP y Vista (en este momento estoy escribiendo con una de las maqs de casa, con XP) y decidí pasarme a una nueva alternativa y dejarme de cracks y demás cosas raras :P
Hace un tiempito ya me compre una notebook, la cual vino "pelada de sistema operativo de serie" (vino con un FreeDOS, si es tal el nombre) y me decidí a instalar Ubuntu. Lo instalé perfectamente! No hay ningun drama en la instalación por suerte, quedó todo perfecto :)
Ahora tengo algunas dudas fundamentales:
Cómo instalo la placa wi-fi? es una Intel PRO/Wireless 4965 AGN Network Connection. Estuve buscando y encontre esta guia: [http://www.guia-ubuntu.org/index.php?title=Instalar_driver_de_tarjetas_WIFI_con_Ndiswrapper#Instalar_driver_wifi](http://www.guia-ubuntu.org/index.php?title=Instalar_driver_de_tarjetas_WIFI_con_Ndiswrapper#Instalar_driver_wifi)
pero la verdad es que me dice que no encuentra el "ndiswrapper".
Por otra parte quise instalar una aplicación (wi-fi radar) y se instaló perfectamente, peeeero cuando lo quiero abrir me salta una ventanita con la siguiente leyenda: "no se pudo lanzar el elemento del menú - ha ocurrido un error al ejecutar el prceso hijo <<su-to-root>> (no existe el fichero o directorio).

Como verán, soy un novato total en este sistema, para el uso que le doy a la pc cumple mis expectativas y lo que he probado va perfecto! Pero con esto me mato, je. La máquina es una Dell Latitude D630.

Saludos y disculpen!
Tulio
[/LIST]

---

### Post by Mauro22 on 2008-07-12
Ndiswrapper se encuentra en los repositorios de Ubuntu, asi como tambien un interfaz grafica para la instalacion de placas wifi

1) Abrir la terminal

2) escribir: sudo synpatic

3) Buscar: ndiswrapper e instalarlo

4) Optativo: podes instalar el paquete ndisgtk que es la parte grafica de ndiswrapper.

5) Seguir con la guia que tenes ahi.



El punto 1 2 y 3, es lo mismo que dice en la guia:

```
sudo aptitude install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9
```

que no se porque no se te instalo

---

### Post by tuliobalcaldi on 2008-07-12
Mauro: mil gracias por tu ayuda! Te comento: entré a synaptic sin dramas, y me aparece así como se ve en la imagen:
[IMG]http://www.mxzonasur.com.ar/pantallazo.png[/IMG]

Por otro lado, intenté isntalar ndisgtk via synaptic y no pude la verdad; use el buscador y aparece, pero no se como se instalan directamente las ocsas la verdad, tampoco se donde ponerlas (las pongo en el "escritorio" -no se si se llama asi en linux-)
Tambien recurri a la ayuda para saber si tengo isntalada la placa inalambrica que trae la maquina y me sale esto (via comandos en terminal, puse "sudo lshw -C network"):

tulio@tulio-laptop:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:26:2f:ff
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5755m-v3.29 latency=0 link=no module=tg3 multicast=yes port=twisted pair




Cuando pongo "sudo aptitude install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9" me sale esto:

tulio@tulio-laptop:~$ sudo aptitude install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "ndiswrapper-common"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "ndiswrapper-utils-1.9"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "ndiswrapper-common"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "ndiswrapper-utils-1.9"
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
tulio@tulio-laptop:~$ 

Esas son las dudas que tengo ahora, despues tengo algunas mas, espero ir aprendiendo de a poco! Soy bastante queso, pero estamos para aprender.
Muchas gracias!
Tulio

---

### Post by Mauro22 on 2008-07-12
Perdoname jejej


Soy medio queso tambien,

Si no podes configurar WiFi con ubuntu significa que no tenes internet o si?

Porque si no tenes internet no podes bajar el ndiswrapper usando apt-get


**Si tenes internet** (en el caso que tengas por cable/modem) hace en la consola:

sudo apt-get update y copia el resultado aca

---

### Post by [P]oli on 2008-07-12
Coincido con Mauro, para instalar los paquetes se conecta a una lista de servidores y descarga los paquetes (en la mayoría de los casos, y creo :P )por eso no podés instalar **ndiswrapper** ;)
Una posible solución sería conectar la laptop a una red cableada, e instalar los paquetes

---

### Post by tuliobalcaldi on 2008-07-13
Buen punto! La verdad que no sabía ese "pequeño detalle" :) en mi caso habia recurrido a bajar las aplicaciones de pagians de internet y copiarlas al "escritorio" pero con otra maquina.
Mañana sacare del reopero el viejo y querido modem adsl usb, porque no esta en mi planes conectar el router a la notebook, me suena a que voy a toquetear algo y no se como armar nuevamente la red bajo windows, soy un queso para redes tambien, je.
Mañana pruebo en un rato libre y les cuento que sucedio con este temita, me tiene intrigado. Igualmente cuando logre bajar estas cosas me ire a un barcito o a una confiteria a probar el wi-fi, je.
Mil gracias!

---

### Post by tuliobalcaldi on 2008-07-13
Una duda más: ¿´cómo me conecto a internet!? estoy intentando bajar las cosas con esta maquina y las copio via pendrive a la otra, pero no se como instalar los archivos y menos donde tengo que ponerlos para que me los detecte el sistema operativo
:(

---

### Post by faktorqm on 2008-07-14
que modem tenes? lo mas facil es darle internet a esa compu y ya. Salu2!

---

### Post by [P]oli on 2008-07-14
> **faktorqm said:**
> que modem tenes? lo mas facil es darle internet a esa compu y ya. Salu2!

Claro, probá conectando el modem directamente a la pc a la que querés instalarle el Wi-Fi, o conectate a una red LAN como cliente (si tenés router). Esta opción seguro funciona ;)

---

### Post by excaliburs on 2008-07-14
si conectas un cable de red del modem a la portatil no es necesario que toques nada para tener internet...el dhcp se encargara de todo.....solo tenes que ir a la esquina inferior derecha del escritorio y seleccionar la red cableada y listo, ya tenes internet....despues de eso instala tranquilo el ndiswrapper que no tiene porque no andar....yo uso el madwifi pero no se si a vos te andara por la placa que tenes....yo tengo wi-fi atheros....
cualquier cosa comenta como te esta llendo con eso
saludos desde Mercedes (B).

---

### Post by excaliburs on 2008-07-14
Perdon....es del router a la portatil!!!!!!!!!!!!!!!!!!
ahora si!

---

### Post by tuliobalcaldi on 2008-07-15
Hoy probe wi-fi y funciono perfectamente! Mil gracias! Y disculpen por las molestias ocasionadas, soy un novato total, ahroa tenog problemas con amsn, je.

Gracias! :D

---

### Post by [P]oli on 2008-07-15
Te felicito, un logro, (Y) (Y) (?

---

### Post by Hernán-Amaya on 2008-07-16
crea otro post con el problema de amsn, ponele en el tag amsn.

---

### Post by hectorivand on 2010-10-16
> **MCWandy said:**
> Yo ya no se a que foro preguntar, nadie contesta. Alguien que pueda ayudar a tener internet? Supuestamente está todo bien pero no entra internet, dice servidor no encontrado.
Es via wifi. Y la versión del Ubuntu es la 10.04
Gracias.:(

Por favor abrí un tema aparte, en la sección de hardware con la siguiente información.:

Tu maquina.
Que placa Wifi tiene
Si es una notebook, el resultado del comando lsusb
si es una placa wifi PC lspci

Saludos
Nacho

---

### Post by guillermolisi on 2010-10-16
Ese post sobre conexion a Internet con WiFi fue movido a [este nuevo thread]("http://ubuntuforums.org/showthread.php?t=1598255").

---

