---
title: "Aceleracion Grafica en Mother PCChips M810L"
date: 2007-09-18
forum: Argentina Team
---

### Post by MatoGroso on 2007-09-18
Hola, tengo un problemón con la aceleracion grafica

Me sucede lo siguiente:

Instalé la version 7.04 en mi equipo: mother PCChips M810LR, Athlon XP 1700+, 512MB RAM, HD 30GB, nVidia GeForce 6200 256MB y todo bien, pero donde le exijo un poco de aceleracion grafica no tengo buenos resultados.

Los drivers que instale son nvidia-glx, estan habilitados. hice $ glxinfo | grep direct y me dice que si tengo aceleracion grafica, pero cuando hago $ glxgears se ve la pantallita de los engranajes negra y al rato me da un "core dumped"... todo mal.

Otra es que cada vez que quiero ingresar al sistema, tengo que cambiar de consola y volver a la consola 7 (donde esta X). Si no hago esto no veo el campo para poder loguearme ni nada... el escritorio me queda en blanco.

 Ya no se mas que probar, cambie los drivers, probé distintas configuraciones y nada.

Estará limitado por el mother? tendrá algo la placa de video?

Les dejo un informe que me dió el Everest.

Cualquier ayuda es agradecida!.

-------[ Placa base ]--------------------------------------------------------------------------------------------------

Propiedades de la Placa Base:
Identificación de la Placa Base 62-0913-001131-00101111-071595-SiS730S$M810LR_RELEASE 09/13/2002 S
Nombre de la Placa Base PCChips M810LR

Propiedades del Bus principal:
Tipo de Bus DEC Alpha EV6
Ancho de bus 64 bits
Reloj real 496 MHz (DDR)
Reloj efectivo 992 MHz
Banda pasante 7936 MB/s

Información física sobre la Placa Base:
Sockets/slots CPU 1 Socket 462
Slots de expansión [ TRIAL VERSION ]
Slots RAM 2 SDR DIMM
Dispositivos integrados Audio, Video, LAN
Forma Micro ATX
Chipset de la Placa Base SiS730S
Otras funciones [ TRIAL VERSION ]

--------[ Chipset ]-----------------------------------------------------------------------------------------------------

[ Puente Norte: SiS 730S ]

Propiedades del puente Norte:
Puente Norte SiS 730S
Supported FSB Speeds FSB200
Tipos de memoria soportadas PC100 SDRAM, PC133 SDRAM
Revisión 02

Tiempos de Memoria:
CAS Latency (CL) 3T
RAS To CAS Delay (tRCD) 3T
RAS Precharge (tRP) 3T
RAS Active Time (tRAS) 6T
Row Cycle Time (tRC) 9T
RAS To RAS Delay (tRRD) 2T
Write Recovery Time (tWR) 1T

Slots de memoria:
Slot DRAM nº1 512 MB (PC133 SDRAM)

Controlador gráfico integrado:
Tipo de controlador gráfico SiS 300
Estado del controlador gráfico Desactivado

Controlador AGP:
Versión AGP 2.00
Estado de AGP Activado
Dispositivos AGP nVIDIA GeForce 6200 AGP
Tamaño de la ventana AGP 64 MB
Velocidades AGP soportadas por este sistema 1x, 2x
Velocidad AGP actual 2x
Fast-Write No soportado
Side Band Addressing Soportado, Activado

Fabricante del chipset:
Nombre de la empresa Silicon Integrated Systems Corporation
Información sobre el producto [http://www.sis.com/products/index.htm#chipsets](http://www.sis.com/products/index.htm#chipsets)
Descargar el controlador [http://www.sis.com/download](http://www.sis.com/download)
Driver Update [http://driveragent.com?ref=59](http://driveragent.com?ref=59)

--------[ BIOS ]--------------------------------------------------------------------------------------------------------

Propiedades de la BIOS:
Tipo de BIOS AMI
Fecha de la BIOS del sistema 09/13/02
Fecha de la BIOS de video 01/19/07

Fabricante de la BIOS:
Nombre de la empresa American Megatrends Inc.
Información sobre el producto [http://www.ami.com/amibios](http://www.ami.com/amibios)
Actualizaciones del BIOS [http://www.esupport.com/biosagent/index.cfm?refererid=40](http://www.esupport.com/biosagent/index.cfm?refererid=40)

Problemas y sugerencias:
Sugerencia Are you looking for a BIOS Upgrade? Contact eSupport Today!
Sugerencia La system BIOS tiene más de 2 años. Actualícela si es necesario.

 

--------[ Dispositivos PCI ]--------------------------------------------------------------------------------------------

[ nVIDIA GeForce 6200 AGP Video Adapter ]

Propiedades del dispositivo:
Descripción del dispositivo nVIDIA GeForce 6200 AGP Video Adapter
Tipo de Bus AGP 4x
Bus / Dispositivo / Función 1 / 0 / 0
Identificador del dispositivo 10DE-0221
N° del Sub-sistema 0000-0000
Clase de dispositivo 0300 (VGA Display Controller)
Revisión A1
Fast Back-to-Back Transactions Soportado, Desactivado

Funcionalidades del dispositivo:
Opera a 66 MHz Soportado
Bus Mastering Activado

Propiedades AGP:
Versión AGP 3.00
Estado de AGP Activado
Velocidades AGP soportadas por este sistema 1x, 2x, 4x
Velocidad AGP actual 2x
Fast-Write Soportado, Desactivado
Side Band Addressing Soportado, Activado

---

### Post by Mauro22 on 2007-09-18
Por lo que tengo entendido, los PC Chips, no son de muy buena calidad y son los mothers mas lentos que he visto.

---

### Post by MatoGroso on 2007-09-18
Si, se que son de los peores, pero que le voy a hacer, es el que tengo... :)

---

### Post by faktorqm on 2007-09-19
Hola, tengo un mother super parecida, (810lmr). Yo primero empezaría a hilar fino sobre el hardware antes que pensar en linux todavia.
Ahi el everest dice que tenes el agp fast write soportado pero desactivado.... eso
estaria bueno que lo actives.
1) fijate si podes overclockear el micro. (asegurate de tener un buen disipador/cooler para que no pase nada, capaz lo levantas a 2000 o 2200mhz)
si te da miedo/panico/verguenza/escalofrios no lo hagas.
2) entra en el bios, y revisa que efectivamente tengas las memorias a 133 con las latencias bien configuradas.
3) revisa el agp aperture size, (deberia ser igual a la memoria de la placa), habilita el agp fast write y si tenes, la combinacion de escritura (no recuerdo el nombre en ingles). asiganale dma e irq, aunke se supone que ya lo deberias tener.

despues en el linux, fijate si el paquete nvidia-glx soporta el hardware que tenes, yo por ejemplo en otra pc tengo una gforce 4 mx 440 y no la soporta, tengo que instalar otra version, la legacy, que cuando la pongo me dice que no tengo el modulo en el kernel. como los quiero.............
en definitva, yo use envy y me soluciono todo, capaz lo que te conviene es borrar cualquier tipo de paquete y volver al driver nv o al vesa o al que mas te guste, y una vez con todo borrado, darle al envy para que te instale el que va.
contame como te fue. salu2!

---

### Post by MatoGroso on 2007-09-19
> **faktorqm said:**
> Hola, tengo un mother super parecida, (810lmr). Yo primero empezaría a hilar fino sobre el hardware antes que pensar en linux todavia.
Ahi el everest dice que tenes el agp fast write soportado pero desactivado.... eso
estaria bueno que lo actives.
1) fijate si podes overclockear el micro. (asegurate de tener un buen disipador/cooler para que no pase nada, capaz lo levantas a 2000 o 2200mhz)
si te da miedo/panico/verguenza/escalofrios no lo hagas.
2) entra en el bios, y revisa que efectivamente tengas las memorias a 133 con las latencias bien configuradas.
3) revisa el agp aperture size, (deberia ser igual a la memoria de la placa), habilita el agp fast write y si tenes, la combinacion de escritura (no recuerdo el nombre en ingles). asiganale dma e irq, aunke se supone que ya lo deberias tener.

despues en el linux, fijate si el paquete nvidia-glx soporta el hardware que tenes, yo por ejemplo en otra pc tengo una gforce 4 mx 440 y no la soporta, tengo que instalar otra version, la legacy, que cuando la pongo me dice que no tengo el modulo en el kernel. como los quiero.............
en definitva, yo use envy y me soluciono todo, capaz lo que te conviene es borrar cualquier tipo de paquete y volver al driver nv o al vesa o al que mas te guste, y una vez con todo borrado, darle al envy para que te instale el que va.
contame como te fue. salu2!

Muchas gracias por la ayuda!
Mi intencion no es overclockear el micro, no creo que sea necesario para poder alcanzar aceleracion grafica.
Respecto a las memorias, estan en 133.
Estoy revisando el manual del mother, que dice que tiene un puerto AGP4x opcional. No se si es que lo trae y no esta configurado o tengo que instalarle una placa extra... estoy en eso.
Ademas no se si actualizando la BIOS me va a reconocer el AGP4X.

Saludos

---

### Post by faktorqm on 2007-09-20
hola, mira, lo del micro es para levantar un poco la performance. obvio que no lo necesitas para la aceleracion grafica!
con lo de la velocidad del agp, lo que dice ahi el everest es es que la mother soporta agp 2x y que la placa de video 4x.
ahora la placa funciona a 2x. 
capaz el everest se equivoco, fijate en el manual de la mother. creo que no podes levantar la velocidad del agp, sé que se puede forzar para ir mas rápido, pero no se si duplicar en este caso.
una vez que tenes todo usa el envy y/o instalalo a mano el drv de nvidia. te fijasste si lo soporta ya? (o sea, si lo soporta, el tema es saber que driver!) salu2!

---

### Post by MatoGroso on 2007-09-20
> **faktorqm said:**
> hola, mira, lo del micro es para levantar un poco la performance. obvio que no lo necesitas para la aceleracion grafica!
con lo de la velocidad del agp, lo que dice ahi el everest es es que la mother soporta agp 2x y que la placa de video 4x.
ahora la placa funciona a 2x. 
capaz el everest se equivoco, fijate en el manual de la mother. creo que no podes levantar la velocidad del agp, sé que se puede forzar para ir mas rápido, pero no se si duplicar en este caso.
una vez que tenes todo usa el envy y/o instalalo a mano el drv de nvidia. te fijasste si lo soporta ya? (o sea, si lo soporta, el tema es saber que driver!) salu2!

Lei en el manual del mother que tiene un puerto AGP 4X opcional. No se bien a que se refiere con opcional: si es que lo tengo que agregar al slot o tengo que actualizar la BIOS/cambiar la configuracion.
Con los drivers parece no haber problemas, porque si es sin aceleracion grafica funciona todo bien.

---

### Post by faktorqm on 2007-09-20
mira, no entiendo. proba de levantar el puerto agp a 4x desde el bios y listo, si no te anda resetea el bios y a probar otra cosa.
te explico, la serie 71XX de drivers de nvidia, soportan ciertas placas, la serie 96XX otro tanto, y el ultimo, el 100 y algo soportan todas las nuevas. entra a nvidia y fijate que driver debe ir para tu placa, si la serie 71, la serie 96 o los ultimos. salu2!!

---

