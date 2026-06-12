---
title: "Problema con Webcam"
date: 2008-01-20
forum: Argentina Team
---

### Post by sebamarca on 2008-01-20
Hace como un año que vengo tratando de conseguir una distro linux para migrar la computadora de mi casa. No la encontraba hasta que encontre Ubuntu. Desde el primer momento reconoció la mayoria de mi hardware aunque con un poco de lentitud. Así que me decidi a probar Xubuntu 7.10.. perfecto, todo barbaro, hasta me puedo conectar a Arnet sin problemas, cosa que no puedo hacer desde XP porque no consigo los drivers para mi placa de red.

la pc es un Duron 1400 con placa pcchips m825 toda integrada....
el problema que tengo es que no puedo hacer andar la webcam... mettro WC350.

probe instalanco el driver spca5xx desde synaptic, pero no puedo encontrar el driver cuando ejecuto modprobe spca5xx. 

Me gustaria me ayudaran o me dijeran si tengo que compilar el driver desde la fuente ....
Desde ya Muchas gracias..

---

### Post by User21 on 2008-01-21
Lo mas seguro es que hayas instalado el paquete **gspca-source** o **spca5xx-source**. Solo has descargado el codigo fuente. Es necesario que compiles desde alli. 

 De todas formas, si eres nuevo, hay una forma MUY FACIL de tener andando tu cam e instalar los drivers: se llama EASYCAM, puedes ver algo de info [aqui]("https://help.ubuntu.com/community/EasyCam"). (en ingles)
Te va a pedir [añadir repositorios]("http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_repositorios_externos") a los origenes de software.  

SI NO PUEDES CON ELLO, avisanos.

---

