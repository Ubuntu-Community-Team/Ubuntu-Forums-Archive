---
title: "Como configuro mi resolucion a 1280 x 800 Intel 915 Ubuntu 6.10 ??"
date: 2007-04-04
forum: Argentina Team
---

### Post by luisciank on 2007-04-04
[COLOR="Blue"]Que tal a todos !!

Bueno antes que nada soy nuevo en Linux bueno mas o menos la verdad es que con este problema me eh dedicado a probar una y otra y otra distro de Linux, ahora estoy con Ubuntu 6.10 y persiste mi problema, paso a explicarlo y espero me puedan hechar la mano y pues obvio en cuanto yo pueda ayudar pues tambienlo haré ok...

Haber mi problema es como puedo configurar mi resolucion a 1280 x 800 en mi laptop, que tiene una tarjeta grafica intel 915, por lo que eh indagado pues si la reconoce mi sistema eh intentado algunas cosas como instalar el 915 resolution etc... pero nada de nada, puesto que al querer ponerle la resolucion correcta siempre me pone la 1024 x 768 y no me gusta como se ve.

Datos que les puedan servir, pues ahi les van:

Mi laptop es una Acer TravelMate 3002 WTCi, la tarjeta grafica es Intel 915, el lcd en winsucks es de 1280 x 800 widescreen.

Espero y me puedan ayudar y sobre todo que sea en lenguaje que pueda entender puesto que no se mucho de esto ok, de antemano gracias por su ayuda.

Saludos !![/COLOR]

---

### Post by fetova on 2007-04-04
Ya probaste cambarla en Sistema - Preferencias - Resolucion de la pantalla?

O prueba...

[http://ubuntuforums.org/showthread.php?t=392527](http://ubuntuforums.org/showthread.php?t=392527)

Tal vez te sirva la info

Saludos

---

### Post by felipelerena on 2007-04-04
```
sudo dpkg-reconfigure xserver-xorg 
```y ahi agregas la resolucion

---

### Post by ariel on 2007-04-06
Yo tuve un problema similar con una laptop dell con monitor WGA (1280x1024).
Lo pude solucionar instalando via synaptics el package "915resolution", y rebooteando. Despues de la instalacion, en Systems>Preferences>ScreenResolution me aparecio 1280x1024 como opcion, lo seleccione y listo.

---

