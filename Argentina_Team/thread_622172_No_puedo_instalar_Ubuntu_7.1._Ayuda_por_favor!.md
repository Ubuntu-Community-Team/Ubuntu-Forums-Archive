---
title: "No puedo instalar Ubuntu 7.1. Ayuda por favor!"
date: 2007-11-24
forum: Argentina Team
---

### Post by gteijido on 2007-11-24
Hola. Les cuento que estroy tratando de instalar Ubuntu 7.1 en mi máquina y se cuelga. Booteo con el CD de instalación, elijo intalar o iniciar Ubuntu, aparece el logo de Ubuntu con una barra de progreso por un momento, después empieza la lista de lo que va levantando, a continuación una pantalla negra con el cursor y despuès una pantalla completamente negra y hasta ahí llega.

A alguien le pasò?

Tengo una notebook Compaq505LA con 1,5GB de RAM y una placa de video on-board NVIDIA GeForce Go 6150.

Muchas gracias por cualquier ayuda!

Saludos!

---

### Post by fscodelaro on 2007-11-24
En general si usás el CD alternativo es mucho más robusto. La desventaja es que no vas a poder ver que tal anda Ubuntu antes de instalarlo, tenes que instalarlo de una (el Alternativo no es LiveCd sino un CD de instalacion como el de Windows XP por ejemplo). Pero por lo que contás estás decidido a instalarlo así que no habría problemas. 

Para descargar el alternativo tendrías que ir a [http://ubuntu-ar.org/conseguiubuntu/descargar](http://ubuntu-ar.org/conseguiubuntu/descargar) y marcar donde dice "Marca aquí si necesitas el CD "alternate". Este CD no incluye el sistema Live CD, en su lugar utitliza un instalador basado en texto." que está debajo de todo. Las preguntas durante la instalación son las mismas que con el livecd, solo que sin la interfaz gráfica linda.

---

### Post by Hei Ku on 2007-11-24
Primero probaria a hacer andar el LiveCD. Si ese no anda, es probable que tengas problemas al instalar.

Los LiveCD funcionan bien, excepto que tengas poca RAM, que no es tu caso.
Podes probar agregarle opciones al inicio, como noquiet y ACPI=off

---

### Post by xpelaox on 2007-11-24
a mi notebook le paso algo parecido, proba esto: En la pantalla que te aparece al principio para correr el live cd, apreta f6 y escribi : noapic nolapic  y dale enter.

espero que te sirva!

Saludos

---

### Post by gteijido on 2007-11-26
Gracias a todos! Les cuento con agregando

noapic nolapic

a los parámetros de inicio inició perfecto desde el CD e instaló todo salvo una cosa... la red... Alguien tiene idea sobre cómo hacerla funcionar?

Por las dudas les reitero el modelo de la máquina. Es una Compaq f505LA.

Saludos y gracias de nuevo!

---

### Post by pante on 2007-11-27
Hola

¿Qué es noapic y nolapic? ¿Alguien podría explicarlo brevemente?

Saludos

---

### Post by Hernán-Amaya on 2007-11-27
pone que placa de red tenes? es wireless ?

---

### Post by Hei Ku on 2007-11-27
> **pante said:**
> Hola

¿Qué es noapic y nolapic? ¿Alguien podría explicarlo brevemente?

Saludos

Es una forma de acceso al hardware, reemplazo, si no me equivoco, del ACPI. Permite manejar mejor el hardware, pero la forma de implementacion es bastante poco standard y tiene muchos problemas. Recuerdo que hubo hace un tiempo una discusion muy fuerte sobre este tema en la lista de mail del kernel (entre Linus y el mantenedor de este modulo)

Sacado de Wikipedia: [http://es.wikipedia.org/wiki/APIC](http://es.wikipedia.org/wiki/APIC)
Resumen

Hay dos componentes en un sistema Intel APIC, el APIC Local (LAPIC) y el I/O APIC (de entrada/salida). el LAPIC está integrado en cada CPU del sistema y el I/O APIC se usa por el sistema de buses de periféricos. Normalmente hay un I/O APIC para cada bus de periféricos en el sistema. En el diseño del sistema original, los LAPICs y los I/O APIC están conectados por un bus dedicado APIC. Los sistemas más nuevos usan el bus del sistema para comunicación entre todos los componentes APIC.

En sistemas conteniendo una PIC 8259, el 8259 se puede conectar al LAPIC en el BSP (System's bootstrap processor), o en uno de las I/O APIC del sistema

---

### Post by gteijido on 2007-11-27
La máquina tiene dos placas, la wireless y la standard. La wireless que es la que más uso es una "WLAN Broadcom 802.11b/g".

Recién empiezo a tratar de meterme con Linux y estuve recorriendo un poco los menúes y configuraciones que tengo desde la interfaz gráfica y solo encontré lo siguiente:

En la "Configuración de red" tengo 3 ítems:
- Conexión inalámbrica
- Conexión cableada
- Conexión con módem

Entré a las propiedades de las primeras dos y las configuré para DHCP, puse la calve WEP y el ESSID en el primer caso y en el segundo la dejé en DHCP. Además estos 3 ítems tienen un check que no se que significa pero tildé estos primeros 2.

Por otro lado encontré en el menú las "Herramientas de red" que contiene varias solapas. La primera se llama "Dispositivos". Allí dentro hay un combo con 2 ítems. El primero es "Interfaz Ethernet (eth0)". A continuación dentro de la solapa hay un cuadro con "información IP" que está vacío para este dispositivo. Más abajo hay algunos datos. Todos en "0" o "no disponible".

Bueno. Viendo todo esto no estoy seguro de que esté instalada correctamente ninguna de las placas de red. Alguno tiene idea sobre cómo verificarlo? Tampoco conozco cómo ejecutar el equivalente a un "ipconfig" para ver si la máquina tiene IP o no.

Gracias y saludos!

---

### Post by Hei Ku on 2007-11-27
el equivalente es ifconfig. Corre eso y postea el resultado.

Y tambien postea tu archivo /etc/network/interfaces

Ese tiene toda la info de configuracion de las placas de red.

---

### Post by gteijido on 2007-11-27
Hei Ku, te cuento que este tiempo, antes de ver tu último post, estuve recorriendo y encontré el "Gestor de controladores restringidos".

Ahí aparece:

- Controlador para tarjetas gráficas NVIDIA (tarjetas recientes)
y
- Firmware para la familia de chipsets Broadcom 43xx

que son los drivers de video y de la placa wifi.

Ambos están deshabilitados.

Al intentar habilitarlos me tiran los siguientes errores:
[INDENT]
[I]The software source for the package

nvidia-glx-new

is not enabled[/I][/INDENT]

y
[INDENT][I]
The software source for the package

bcm43xx-fwcutter

is not enabled[/I][/INDENT]

respectivamente.

Alguna idea?

---

### Post by Hei Ku on 2007-11-28
Desde synaptic tenes una opcion para habilitar el repositorio de controladores restringidos, creo. Aca los chicos te pueden ayudar mejor porque yo tengo kubuntu y esa es opcion es un poco diferente, pero es algo facil asi que no deberias tener problemas.

---

### Post by gteijido on 2007-11-28
Bueno, buenas noticias!! Entré al Synaptic. Ahí busqué los dos paquetes que mencioné en mi post anterior pero no los encontró. Conecté la máquina a internet con la placa estandard en vez de la wireless. A continuación entré a Configuración > Repositorios de Synaptic. En la solapa "Software Ubuntu" tildé "Controladores privados para dispositivos (restricted)". Una vez que hice eso, bajó varios paquetes de internet. Volví a buscar los paquetes que no había encontrado originalmente y esta vez si los encontró. Hice click en cada uno de ellos por vez y los marqué para instalar. Los instaló automáticamente. Por último fuí nuevamente a Sistema > Administración > Gestor de controladores restringidos y habilité ambos controladores sin problema.

Como resultado, estoy escribiendo este post desde Ubuntu.

Muchísimas gracias a todos por su colaboración!!!

---

### Post by vk-cdg on 2007-11-29
Perdón. no vengo siguiendo el post en detalle!

Pudiste instalar los drivers de la placa inalámbrica y anda todo?
Epa, esto es muy interesante para mas de un amigo que le pasa algo parecido.

---

### Post by gteijido on 2007-11-29
Si, quedó todo funcionando perfectamente.

A continuación les paso un resumen de los problemas que fui encontrando y sus soluciones para que con solo seguirlos les queden todo andando.

Instalé Ubuntu 7.1 desde el LiveCD en una Compaq F505LA que tiene una placa wireless WLAN Broadcom 802.11b/g y una placa de video NVIDIA GeForce Go 6150.

Los pasos que seguí fueron:

- Bootear con el CD
- Seleccionar instalar
- Primer problema: Comienza a cargar el SO, se puede ver el logo de Ubuntu y la barra de progreso. Luego se ve cómo va levantando algunos componentes, luego pantalla en blanco con el cursot y por último se queda en una pantalla completamente en blanco.
- Solución: Reiniciar para que bootee nuevamente el CD y antes de iniciar la instalación presionar F6 y agregar como parámetros al final:
		
		noapic nolapic
		
- Una vez que inicia Ubuntu elegir instalar en el escritorio y seguir los pasos de la instalación.
- Una vez finalizada la instalación conectarse a internet por red fija.
- Ingresar al Synapsis (Configuración > Repositorios de Synaptic).
- Seleccionar la solapa "Software Ubuntu".
- Tildar "Controladores privados para dispositivos (restricted)". Esperar a que termine de bajar varios paquetes de internet.
- Buscar el paquete "nvidia-glx-new".
- Hacer click derecho sobre el paquete y seleccionar "Marcar para instalar". Esperar a que se instale y baje más datos de internet.
- Buscar el paquete "bcm43xx-fwcutter".
- Hacer click derecho sobre el paquete y seleccionar "Marcar para instalar". Esperar a que se instale y baje más datos de internet.
- Ir al gestor de controladores (Sistema > Administración > Gestor de controladores restringidos).
- Hacer click en los check de habilitación del controlador de NVidia y del firmware de Broadcom.

Listo. Lo que quedaría es que cada uno entre en Sistema > Administración > Redes, marque el check para habilitar la red inalámbrica y se configure una red inalámbrica o deje la máquina en modo itinerante.

Espero que sirva.

Saludos y muchas gracias a todos los que colaboraron!

---

### Post by gteijido on 2007-11-29
Si, quedó todo funcionando perfectamente.

A continuación les paso un resumen de los problemas que fui encontrando y sus soluciones para que con solo seguirlos les queden todo andando.

Instalé Ubuntu 7.1 desde el LiveCD en una Compaq F505LA que tiene una placa wireless WLAN Broadcom 802.11b/g y una placa de video NVIDIA GeForce Go 6150.

Los pasos que seguí fueron:

- Bootear con el CD
- Seleccionar instalar
- Primer problema: Comienza a cargar el SO, se puede ver el logo de Ubuntu y la barra de progreso. Luego se ve cómo va levantando algunos componentes, luego pantalla en blanco con el cursot y por último se queda en una pantalla completamente en blanco.
- Solución: Reiniciar para que bootee nuevamente el CD y antes de iniciar la instalación presionar F6 y agregar como parámetros al final:
		
		noapic nolapic
		
- Una vez que inicia Ubuntu elegir instalar en el escritorio y seguir los pasos de la instalación.
- Una vez finalizada la instalación conectarse a internet por red fija.
- Ingresar al Synapsis (Configuración > Repositorios de Synaptic).
- Seleccionar la solapa "Software Ubuntu".
- Tildar "Controladores privados para dispositivos (restricted)". Esperar a que termine de bajar varios paquetes de internet.
- Buscar el paquete "nvidia-glx-new".
- Hacer click derecho sobre el paquete y seleccionar "Marcar para instalar". Esperar a que se instale y baje más datos de internet.
- Buscar el paquete "bcm43xx-fwcutter".
- Hacer click derecho sobre el paquete y seleccionar "Marcar para instalar". Esperar a que se instale y baje más datos de internet.
- Ir al gestor de controladores (Sistema > Administración > Gestor de controladores restringidos).
- Hacer click en los check de habilitación del controlador de NVidia y del firmware de Broadcom.

Listo. Lo que quedaría es que cada uno entre en Sistema > Administración > Redes, marque el check para habilitar la red inalámbrica y se configure una red inalámbrica o deje la máquina en modo itinerante.

Espero que sirva.

Saludos y muchas gracias a todos los que colaboraron!

---

### Post by dropedrobarri on 2008-04-20
Hola a todos: Yo tampoco pude hacer andar el liveCD del UBUNTU 7.10 en mi notebook:
BanghóMov CQ1405CB 
Microprocesador Intel Pentium Dual T2330
Memoria 1Gb. DDR2 667Mhz. 
Disco Rígido SATA 80Gb. 5400RPM 
Lectoragrabadora de DVD 
Chipset Via VN896CE + VT8237A 
Placa de red 10/100, Wireless 802.11b/g 
Peso 2,2Kg. 
Batería 6 celdas
3 X USB 2.0 – One Express Card/54(34) Slot
Modem 56Kbps. MDC v. 92
Lector de Memorias 7 en 1
Pantalla 14" WXGA
Asì que optè por instalar la versión ISO ALTERNATE, se instaló perfectamente, pero cuando lo inicio igual se me tilda!!!!
Así que probé con iniciar a modo prueba de fallos, y tipeè " startx" Y ANDA PERFECTAMENTE EL UBUNTU.
Así que presumo que se trata de algun driver... en eso estoy: Si alguien sabe algo BIEN RECIBIDA LA RESPUESTA!!!!

---

