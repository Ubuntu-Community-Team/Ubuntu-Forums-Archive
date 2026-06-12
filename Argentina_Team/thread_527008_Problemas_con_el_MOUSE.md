---
title: "Problemas con el MOUSE"
date: 2007-08-16
forum: Argentina Team
---

### Post by CabezonBA on 2007-08-16
hola gente:). Como podran ver soy nuevito en Linux y mas en ubuntu.
Mi problema es que cuando termina de cargar el CD Live (ubuntu 7.04 - desktop - i356) el mouse no funciona, este está conectado al puerto serie. La maquina tiene un CPU Athlon XP 0.13 1200Mhz. La RAM es de 352M.
Muchas gracias por la ayuda que me puedan dar.
Saludos a todos.

---

### Post by valucha on 2007-08-16
[COLOR="DarkOrchid"]Bienvenido.
Los Live CD's funcionan con 256 de ram. Veo que tenés más de lo suficiente, pero el tema es que si tenes placa on boead que te saca ram sonaste...
Fijate eso primero
Sino, usá el Alternate cd. Que te instala lo mismo pero en modo rtexto (te da a elegir todo igual que el live cd)[/COLOR]

---

### Post by rojojuan on 2007-08-16
Me pasó y luego de lidiar con varias distribuciones de Linux, encontré la forma de solucionarlo.
Tenés que editar el archivo /etc/X11/xorg.conf.
Mandato:
sudo nano /etc/X11/xorg.conf

En las líneas que corresponden al mouse:


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"


Tenés que dejarlo así:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"ttyS1" (o ttyS2). Probá las dos opciones porque depende en qué puerto se encontra el mouse.
	Option		"Protocol"	"Microsoft"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"

Guardar con Control + O y listo.

Por las dudas siempre anotá cómo estaba la configuración antes de modfiicarla por si es necesario volver atrás.

Espero que te sirva. Comentá cómo te fué.

---

### Post by CabezonBA on 2007-08-16
Gracias valucha y rojojuan. Ahora me pongo a ver el tema. Cualquier cosa los molesto nuevamente.
Saludos.

---

### Post by edd12river on 2007-08-16
yo tuve ese problema, si l oestas usando live cd no lo podes arreglar, ya q tenes q reiniciar al pc para guardar los cambios, y como es live cd no se guardan...si ya lo tene sinstalado no tendrias q tener problemas, en live cd ese archivo q dicen q abras aparece en blanco, xq es un archivo q se crea cuando se instala ubuntu...creo... :s

suerte!

---

### Post by rojojuan on 2007-08-16
En un CD live lo edité, creo que era Knoppix. Tenés que rearrancar las X con Control + alt + retroceso.
Andaba bien y lo guardaba en memoria

---

