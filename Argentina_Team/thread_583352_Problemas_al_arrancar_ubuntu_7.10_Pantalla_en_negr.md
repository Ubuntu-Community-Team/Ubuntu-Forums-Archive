---
title: "Problemas al arrancar ubuntu 7.10 Pantalla en negro"
date: 2007-10-20
forum: Argentina Team
---

### Post by eduf on 2007-10-20
Buenas, antes que nada quiero decirles que soy nuevo en esto de los SO linux, pero me parece muy interesante, me bajé la última versión de ubuntu la 7.10, anteriormente me había bajado la 7.04, pero con la última tengo un problema, comienza todo bien con el **live cd**, hasta que la barra de progreso llega al final, justo en ese momento la pantalla pasa a quedarse negra y no sale de este estado, siempre está negra, se llega a escuchar la música, pero se no ve nada, con la anterior versión la 7.04 no tengo este problema al arrancar el live cd iba todo bien, les dejo los datos de mi máquina, espero puedan darme una solución.
Monitor: Philips 104s
Placa: Asus A8V
CPU: AMD Athlon(tm) 64 Processor 3200+ Venice s939
Memoria RAM: 2GB
Disco Rígido: Maxtor DiamondMax 10 de 200 GB
Únidad óptica: DVD LG GSA-4167B
PLaca Gráfica: NVIDIA GeForce FX 5500 con 256 MB de ram
Tengo instalado XP SP2

Desde ya muchas gracias.

---

### Post by Hernán-Amaya on 2007-10-20
seguramente es algún problema con la configuración de video, cuando escuches la musica apreta alt+ctrl+F2  te va a aparecer la consola ahí tenés que loguearte con tu usuario y escribi

```

sudo dpkg-reconfigure xserver-xorg

```

después elegí las opciones que tiene tu hard y debería de andar si no es así avisa 

suerte!

---

### Post by eduf on 2007-10-20
Muchas gracias Hernán por tu respuesta, pero veo que cometí un error importante, el tema es que el problema que describí es cuando arranca el live cd, o sea no tengo instalado el SO, igual te comento que hice lo que me recomendaste, pero como dije antes soy nuevo, y necesitaria la sentencia también para regresar al escritorio, desde ya muchas gracias

---

### Post by WanderingKnight on 2007-10-20
> Muchas gracias Hernán por tu respuesta, pero veo que cometí un error importante, el tema es que el problema que describí es cuando arranca el live cd, o sea no tengo instalado el SO, igual te comento que hice lo que me recomendaste, pero como dije antes soy nuevo, y necesitaria la sentencia también para regresar al escritorio, desde ya muchas gracias

Reseteando la maquina deberia volver luego de reconfigurar el xorg. De todas formas, podes intentar:

```
su *nombredeusuario*
startx
```

...y deberia arrancar en tu sesion.

---

### Post by sebadigri on 2007-10-20
Ponete el driver "vesa" 

Hace esto una vez que t teermine de cargar todos desde el CD (y se escuche el sonido de q ya estas en el escritorio)

Apreta: CONTROL + ALT + F2 (o F1)

dps ahi pone el siguiente comando (respetando mayusculas y minusculas): 
"sudo nano /etc/X11/xorg.conf "
Y ahi vas a abrir el archivo "xorg.conf" y empeza a bajar hasta que veas donde ta la placa de video y ahi pone en la parte que dice driver "vesa"
Después pone CONTROL + S, dale Y para grabar el archivo y usa el siguiente comando...

"sudo /etc/init.d/gdm stop"
"sudo /etc/init.d/gdm start" (si te tira FAIL volvelo a usar y t tira OK)

Espera un ratito y te va a parecer un cartel con graficos re feos y ponele que si...y ahi te tendria q arrancar el Gnome Desktop Manager (GDM) con los drivers "vesa" y se tendria que ver bien......

NOTA: Si tenes 2 placas de video o una placa de video dual core fijate de cambiar la parte en el xorg.conf que dice BusID "PCI:4:0:0" o el numero q sea por otro numero..(a mi me pasa eso me toma PCI 4 y el q usa el monitor es el PCI 5)

Saludos

---

### Post by eduf on 2007-10-21
Gracias sebadigri, pero no funcionó, me parece raro que tenga este problema con el live cd y no vea el escritorio, ya que con la versión anterior como dije, andaba perfecto, gracias a todos por sus respuestas

---

### Post by Darth Trix on 2007-10-22
Yo tuve exactamente el mismo plroblema con el LiveCD la final hice un upgrade desde Feisty, anduvo todo sin problemas.

PD: eduf podrias intentar instalando con el alternate LiveCD.

---

### Post by BlackHero on 2007-12-02
Holas tengo una maquina con 4 gb ram y no puedo cargar un live :S je tube que dejarla en 1 gb para que arrancara y despues la reconfigure el kernel para que me tome los 4 gb totales =)

---

### Post by Hei Ku on 2007-12-02
proba arrancando con la opcion ACPI=off
Tambien podes probar con: nolapic noapic

---

